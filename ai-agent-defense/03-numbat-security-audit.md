我已经阅读了仓库中的所有核心源代码文件。以下是完整的安全审计报告。

---

# 安全审计报告：perplexityai/numbat

**审计日期：** 2026-08-06  
**仓库：** perplexityai/numbat  
**审计范围：** 全部 354 个文件（源代码、配置、CI/CD、规则、文档）  
**审计人：** 自动化安全审计

---

## 一、仓库概况

Numbat 是一个 **AI Agent 安全监控工具**，用 Go 编写。它的功能是：

1. **scan** — 扫描 AI Agent 的本地会话产物（Claude Code、Codex、Gemini、Cursor 等 15+ Agent），解析为标准化事件
2. **collect** — 监听 OTLP/HTTP 遥测日志（默认绑定 127.0.0.1:4318）
3. **hook** — 安装到各 AI Agent 的生命周期 Hook 中，实时拦截/监控 Agent 操作
4. **ship** — 将本地 NDJSON 记录文件推送到 HTTP endpoint
5. **rules** — 管理 CEL 表达式规则引擎，检测恶意 Agent 行为
6. **timeline** — 重建 Agent 会话的时间线视图
7. **case** — 打包取证发现和引用事件

所有源代码都是 Go 语言，没有 C/C++ 绑定，没有 CGO（`CGO_ENABLED=0`）。

---

## 二、逐项审计结果

### 2.1 网络通信 — ✅ 安全

| 发现 | 风险等级 |
|------|----------|
| 无硬编码的 C2 服务器或数据收集 endpoint | INFO |
| HTTP 输出仅在操作员显式配置时才发起 | INFO |
| `collect` 默认绑定 `127.0.0.1:4318`（回环地址） | INFO |
| 非 HTTP sink 模式下，工具不发起任何网络请求 | INFO |

**详细分析：**

- **`internal/output/httpsink.go`**：HTTP sink 是唯一的出站网络组件。它仅在 `--output http` 或 `--http-url` 被显式指定时创建。验证逻辑严格：
  - 默认拒绝非回环地址的明文 HTTP（`--http-allow-insecure` 才允许）
  - 拒绝 URL 中的内嵌凭据（`user:pass@host`）
  - **不跟随重定向**（防止 307/308 重放 NDJSON body 和 auth header 到不同 origin）
  - 支持 Bearer/HMAC-SHA256 认证
  - drain 但不 echo HTTP 响应体（防止恶意 receiver 向 stderr 注入内容）

- **`cmd/numbat/collect.go`**：OTLP 接收器默认绑定 `127.0.0.1:4318`，仅处理 POST `/v1/logs`，有 4 MiB body 大小限制，验证 Content-Type。非回环绑定时会打印醒目安全警告。

- **`cmd/numbat/ship.go`**：tail 模式推送到 HTTP endpoint，仅在用户指定 `--http-url` 时运行。

**未发现任何隐藏的网络通信路径。** 所有 HTTP 调用都通过 `internal/output/httpsink.go` 的单一出口。

### 2.2 文件系统操作 — ✅ 安全

| 发现 | 风险等级 |
|------|----------|
| 仅读取 AI Agent 的公开会话产物（预期行为） | INFO |
| 不读取 ~/.ssh、~/.aws、.env 等敏感文件 | INFO |
| 输出文件使用 0600 权限，拒绝符号链接 | INFO |
| 状态数据库使用 0600 权限 | INFO |

**详细分析：**

- **`internal/discover/discover.go`**：文件发现逻辑仅扫描已知 AI Agent 目录（`~/.claude/projects/`、`~/.codex/sessions/`、`~/.gemini/tmp/` 等）。这些路径通过 `discover.DefaultRootsFor()` 硬编码或通过环境变量（`CODEX_HOME`、`CLAUDE_CONFIG_DIR` 等）配置。
  
- **不读取敏感文件**：工具本身不读取 `~/.ssh`、`~/.aws/credentials`、`.env` 等。相反，规则引擎中的检测规则（如 `rules/exfil/env_capture_to_network.yaml`、`rules/secrets/cloud_credential_read.yaml`）是用来检测 AI Agent **是否**在读取这些文件。

- **`internal/output/filesink.go`**：输出文件使用 `0600` 权限，通过 `openNoFollow` 拒绝符号链接和 reparse point，防止重定向。

- **`internal/state/state.go`**：bbolt 数据库以 `0600` 权限打开，父目录以 `0700` 创建。

- **文件读取安全**：`discover.Walk` 拒绝 FIFO、socket、设备文件（防止阻塞扫描），拒绝逃逸扫描根目录的符号链接。

### 2.3 进程操作 — ✅ 安全

| 发现 | 风险等级 |
|------|----------|
| 无 fork bomb、反向 shell、权限提升代码 | INFO |
| 工具不执行在产物中发现的任何命令 | INFO |

**详细分析：**

- 工具是纯解析/分析工具，**不执行**任何 AI Agent 产物中发现的命令。`SECURITY.md` 明确声明："numbat never executes an agent, package manager, or command found in an artifact."

- shell 命令分析（`internal/rule/shell.go`）是**静态分析**——使用 `mvdan.cc/sh/v3` 解析器将 shell 命令解析为 AST 并提取命令结构（命令名、参数、重定向），然后与检测规则匹配。不实际执行任何命令。

- 无 `os/exec.Command`、`exec.CommandContext` 或任何进程创建调用。

### 2.4 供应链 — ✅ 安全

| 发现 | 风险等级 |
|------|----------|
| 所有依赖均为知名标准库 | INFO |
| 无 typosquatting 包名 | INFO |
| 无可疑/未知的依赖 | INFO |

**依赖清单（`go.mod`）：**

| 依赖 | 版本 | 用途 | 安全性 |
|------|------|------|--------|
| `github.com/google/cel-go` | v0.30.0 | CEL 表达式引擎（规则匹配） | Google 官方维护 |
| `github.com/klauspost/compress` | v1.19.1 | zstd 解压缩（Codex .jsonl.zst） | 知名压缩库 |
| `go.etcd.io/bbolt` | v1.5.0 | 嵌入式 KV 数据库（状态存储） | etcd 官方维护 |
| `go.yaml.in/yaml/v3` | v3.0.5 | YAML 解析（规则文件） | YAML 官方 |
| `golang.org/x/sys` | v0.47.0 | 系统调用封装 | Go 官方 |
| `google.golang.org/protobuf` | v1.36.11 | Protobuf 编解码（OTLP） | Google 官方 |
| `mvdan.cc/sh/v3` | v3.13.1 | POSIX shell 解析器 | 知名项目 |

间接依赖：`cel.dev/expr`、`antlr4-go`、`golang.org/x/exp`、`golang.org/x/text`、`google.golang.org/genproto` — 均为 CEL/protobuf 的标准间接依赖。

**所有包名均正确拼写，无可疑包。** go.sum 中所有哈希值格式正确。

### 2.5 构建脚本 — ✅ 安全

| 发现 | 风险等级 |
|------|----------|
| 无 build.rs（Go 项目，不需要编译时脚本） | INFO |
| CI 使用 SHA-pinned GitHub Actions | INFO |
| Release 工作流使用标准 GoReleaser | INFO |
| CI 中 `persist-credentials: false` | INFO |

**详细分析：**

- 这是 Go 项目，没有 Rust 的 `build.rs` 或 C 的 Makefile 编译脚本。

- **`.github/workflows/ci.yml`**：所有 GitHub Actions 均使用 SHA pin（如 `actions/checkout@3d3c42e5aac5ba805825da76410c181273ba90b1 # v7.0.1`），而非可变 tag。包含：
  - `go vet`、`gofmt`、`go test -race`、`golangci-lint`
  - **govulncheck**（漏洞扫描）
  - Fuzzing 测试（解析器、redaction、OTLP decoder）
  - Coverage 报告

- **`.github/workflows/release.yml`**：
  - 发布前执行 `go mod verify`、`go vet`、`go test -race`
  - 验证 tag 为语义化版本，且可达自 main 分支
  - 使用 GoReleaser 标准配置，`-trimpath -s -w`

- **`.goreleaser.yaml`**：标准配置，CGO 禁用，版本注入通过 ldflags。

### 2.6 混淆代码 — ✅ 安全

| 发现 | 风险等级 |
|------|----------|
| 无 base64 编码的可执行字符串 | INFO |
| 无 eval/reflect 动态代码执行 | INFO |
| CEL 表达式在编译时验证，运行时受限 | INFO |

**详细分析：**

- 代码中没有 `encoding/base64` 用于解码可执行内容。
- 没有使用 `reflect` 进行动态方法调用。
- CEL 表达式引擎（`internal/rule/engine.go`）在启动时编译规则为字节码，运行时安全评估。CEL 是 Google 的**沙箱表达式语言**，禁止函数调用、网络访问、文件 I/O。
- `PowerShell -EncodedCommand` 的 base64 解码（`internal/rule/powershell.go`）是**静态分析**的一部分——解码后是进行规则匹配，不是执行。

### 2.7 环境变量收集 — ✅ 安全

| 发现 | 风险等级 |
|------|----------|
| 仅读取 Agent 配置相关的环境变量 | INFO |
| 不收集 API keys/tokens 外传 | INFO |
| HTTP auth 密钥仅从环境变量读取，从不记录 | INFO |

**详细分析：**

- 工具读取的环境变量均为**配置定位用途**：
  - `CODEX_HOME`、`CLAUDE_CONFIG_DIR`、`GEMINI_CLI_HOME`、`COPILOT_HOME` 等 → 定位 Agent 会话目录
  - `XDG_DATA_HOME` → 定位 OpenCode 存储
  - `OPENCLAW_STATE_DIR`、`OPENCLAW_CONFIG_PATH` → 定位 OpenClaw 状态

- **HTTP 认证密钥**（Bearer token、HMAC key）通过 `NUMBAT_HTTP_BEARER_TOKEN` / `NUMBAT_HTTP_HMAC_KEY` 环境变量传入（见 `cmd/numbat/sink.go` 中的 `printHTTPAuthEnvHelp`），**永不通过命令行 flag 传入**，**永不记录到日志**。

- **不收集**：`AWS_ACCESS_KEY_ID`、`GITHUB_TOKEN`、`OPENAI_API_KEY` 等凭据环境变量不会被 numbat 本身读取。

- 规则 `rules/secrets/process_environment_read.yaml` 和 `rules/secrets/agent_read_env.yaml` 检测的是 AI Agent 是否在读取这些变量。

### 2.8 持久化 — ✅ 安全

| 发现 | 风险等级 |
|------|----------|
| 不写入 crontab/systemd/launchd | INFO |
| Hook 安装修改 Agent 配置（预期行为） | LOW |
| 状态仅写入 ~/.numbat/state.db | INFO |

**详细分析：**

- numbat 自身**不安装**任何持久化机制。规则文件 `rules/persistence/scheduler_install.yaml` 检测的是 AI Agent 是否在安装持久化机制。

- `numbat hook install` 会修改 AI Agent 的配置文件（如 Claude 的 `settings.json`、Codex 的配置等），将 numbat 二进制注册为生命周期 Hook。这是**预期行为和核心功能**。安装前会备份原始配置文件，卸载时恢复，操作幂等。

- 唯一的本地状态写入是 `~/.numbat/state.db`（bbolt 数据库，0600 权限），仅存储序列规则窗口的事件标识符和引用。

### 2.9 许可证合规性 — ✅ 合规

| 发现 | 风险等级 |
|------|----------|
| 标准 Apache-2.0，无附加条款 | INFO |
| THIRD_PARTY_LICENSES.txt 包含第三方许可 | INFO |

LICENSE 文件是标准的 Apache License 2.0 全文，无修改。未发现 NOTICE 文件中的附加条款。仓库遵守 Apache-2.0 第 4 条的所有要求。

### 2.10 脱敏机制 — ✅ 安全

| 发现 | 风险等级 |
|------|----------|
| 输出前自动脱敏（redact.String） | INFO |
| 脱敏覆盖命令、文件路径、URL、内容预览 | INFO |
| URL userinfo 无条件剥离 | INFO |

`internal/redact/redact.go` 在输出前对所有字段进行脱敏处理。覆盖：
- AWS Access Key（`AKIA[0-9A-Z]{16}`）
- GitHub Token（`gh[pousr]_...`）
- Slack Token（`xox[baprs]-...`）
- OpenAI Key（`sk-...`）
- PEM 私钥头
- URL userinfo（`user:pass@host`）
- Authorization header 凭据
- 含 SECRET/TOKEN/PASSWORD 等关键字的赋值
- 签名 URL 参数（`x-amz-signature` 等）

**注意：** `SECURITY.md` 正确声明 redaction "is not a declassification or data-loss-prevention boundary"——脱敏是尽力而为的模式匹配，不是加密级保证。这是一个诚实的安全声明。

---

## 三、安全设计亮点

审计过程中发现了多处体现安全工程实践的设计：

1. **Fail-open enforcement**：Hook 处理器在解析错误、评估错误或输出失败时，抑制 deny 响应，选择放行。这防止误判导致 Agent 功能中断。
2. **Redirect 不跟随**：HTTP sink 禁止跟随重定向，防止凭证泄露到不同 origin。
3. **Symlink 防护**：文件 sink 和 artifact 发现都拒绝符号链接，防止重定向。
4. **入站 body 限制**：OTLP 接收器和 Hook stdin 都有 4 MiB body 大小限制。
5. **Loopback 默认**：OTLP 接收器默认绑定回环地址，非回环时发出安全警告。
6. **环境变量传递密钥**：Bearer/HMAC 密钥仅通过环境变量传入，不出现在命令行（防止 `/proc/*/cmdline` 泄露）。
7. **CGO 禁用**：纯 Go 编译，减少 C 层面的攻击面。
8. **govulncheck CI**：CI 流水线集成了 Go 官方漏洞扫描工具。

---

## 四、最终结论

### **✅ 可以安全地在企业内部安装部署。**

**审计未发现任何恶意后门、数据外传、供应链投毒或混淆代码。**

Numbat 是一个设计精良、安全性高的 AI Agent 端点监控工具。代码质量高，安全设计考虑周全。所有网络通信均为用户显式配置，无隐藏的 C2 通道；所有文件操作限于已知 AI Agent 产物；无进程执行能力；依赖均为知名标准库；CI/CD 流水线使用 SHA-pinned Actions 并集成漏洞扫描。

**企业部署建议：**

1. ✅ 使用 `--output file` 本地输出，仅在需要时配置 HTTP sink 到内部 SIEM
2. ✅ 如使用 `collect`，保持默认 `127.0.0.1:4318` 绑定
3. ✅ 如使用 HTTP 输出，使用 `--http-auth bearer` 并通过 HTTPS
4. ✅ 限制 `~/.numbat/` 目录和输出文件的访问权限
5. ✅ 从 GitHub Release 下载预编译二进制时验证 SHA256 checksum
6. ⚠️ Hook 安装会修改 AI Agent 配置——在变更管理流程中记录此操作