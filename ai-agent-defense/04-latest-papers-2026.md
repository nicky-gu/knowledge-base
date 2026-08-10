# AI Agent 安全最新研究论文清单（2025-2026）

> 检索时间：2026-08-10
> 来源：arXiv API 系统检索 + GitHub 高星仓库
> 筛选标准：有实测数据/开源代码/权威机构出品优先
> 已有的论文（ADR 2605.17380、Hou et al. 2503.23278、MCPXKIT 2508.12538、MCP Safety Audit 2504.03767）不再重复

---

## 一、MCP 协议安全实测与分析

### 1. Exposed by Design: A Dynamic Security Assessment of Internet-Facing MCP Servers at Scale
- **arXiv**: 2608.00150 | 2026-07-31
- **作者**: Nicolás Padilla 等
- **核心**: **首次对公网 21,000+ 个 MCP 服务器做动态行为安全评估**，覆盖 11 个数据源的被动发现 + 主动探测
- **价值**: 目前最大规模的 MCP 生态实测，直接回答"公网上有多少 MCP server 是危险的"

### 2. Registry Descriptions Go Stale Unevenly: An 89-Day Measurement of MCP Drift
- **arXiv**: 2608.00997 | 2026-08-02
- **作者**: Gautam Bharti
- **核心**: **89 天追踪 MCP 注册表描述漂移**——你审计时的 server 描述，89 天后有多少还准确？结论：漂移不均匀，基于描述的审计严重低覆盖
- **价值**: 揭示了 MCP 安全审计的时间维度盲区——静态快照式审计不可靠

### 3. Hybrid Analysis for Secure MCP Tool Use in LLM Agents
- **arXiv**: 2607.25297 | 2026-07-28
- **作者**: Ping He, Yuexiang Xie, Yaliang Li, **Shouling Ji**（浙江大学安全团队）
- **核心**: 混合分析方案——静态分析 MCP 工具源码 + 动态监控 Agent 调用行为，双重检测恶意工具
- **价值**: 和 Uber ADR 的"源码分析 MCP"思路一致，但来自学术界的独立验证

### 4. Hardware Keystores for AI Agent Signing Workflows: A Zero-Trust MCP Enhancement
- **arXiv**: 2608.06130 | 2026-08-06
- **核心**: 用硬件密钥库（HSM/TPM）给 AI Agent 的 MCP 操作签名——零信任模型
- **价值**: 把 Agent 操作的不可否认性提到硬件级别，适合高合规要求场景

---

## 二、Agent 运行时安全与监控

### 5. Securing Agentic AI: From Per-Action Checks to Trajectory Assurance
- **arXiv**: 2608.01558 | 2026-08-03
- **作者**: Alireza Lotfi, Imtiaz Karim, **Elisa Bertino**（普渡大学安全大佬）
- **核心**: **从"逐操作检查"升级到"轨迹级保障"**——Agent 的安全性不只取决于单个操作，而取决于整条执行轨迹
- **价值**: 和你之前读的《断言点与依赖点》完全呼应——单个操作合法不代表整条链合法

### 6. DreamGuard: Efficient Runtime Guardrail via Risk-Aware World Model
- **arXiv**: 2608.05695 | 2026-08-06
- **作者**: Wenhao Lin 等
- **核心**: 用"世界模型"预测 Agent 操作的后果风险，在执行前评估——轻量级运行时护栏
- **价值**: 比纯 LLM 裁判便宜（不需要每次调 API），用预测模型替代

### 7. Online Monitoring and Corrective Steering of Programming Agents
- **arXiv**: 2608.06701 | 2026-08-07
- **作者**: Shuyang Liu 等
- **核心**: **在线监控编程 Agent（如修复 GitHub Issue），发现偏差时主动纠正**——不只是检测，还能实时纠偏
- **价值**: 和 Numbat 的 hook 阻断是互补路线——Numbat 阻断后让用户重来，这篇做的是自动修正

### 8. A Few Neurons Reveal When LLMs Misuse Tools: Sparse Detection
- **arXiv**: 2608.00218 | 2026-07-31
- **作者**: Yutong Ke 等
- **核心**: **发现 LLM 内部少量 MLP 神经元就能判断工具是否被误用**——三种失效：无效参数、不必要调用、遗漏调用
- **价值**: 白盒检测路线——不开 LLM API，直接看模型内部激活值就能发现问题

### 9. Safety Invariants for Agents Orchestrating Irreversible State Transitions
- **arXiv**: 2608.00783 | 2026-08-01
- **作者**: Zhaoming Yin
- **核心**: **四维形式化框架确保 Agent 不执行不可逆危险操作**（转账、写持久存储、驱动硬件）——在区块链公开账本上验证
- **价值**: 形式化安全验证，适合金融/工业控制场景

---

## 三、Agent 红队与攻防演练

### 10. Securing the AI Agent: A Unified Framework for Multi-Layer Agent Red Teaming (AI-Infra-Guard)
- **arXiv**: 2606.31227 | 2026-06-30
- **作者**: Yong Yang 等
- **核心**: **开源多层 Agent 红队框架 AI-Infra-Guard**——覆盖模型服务、Agent 平台、MCP 生态、语言模型本身四个层面
- **代码**: 开源（腾讯雀实验室出品，arXiv 引用了 Tencent/AI-Infra-Guard）
- **价值**: 直接可用于企业内部红队演练

### 11. OpenART: Scaling Agent Red Teaming via Open-Ended Environment Evolution
- **arXiv**: 2608.00677 | 2026-08-01
- **作者**: Yunhao Chen 等
- **核心**: **开放式环境进化的 Agent 红队**——和 Uber ADR Explorer 思路类似（进化算法自动生成攻击），但开放环境
- **价值**: ADR Explorer 没开源，这个是开源替代品

### 12. StealthBench: Measuring Operational Stealth in Autonomous Offensive-Security Agents
- **arXiv**: 2607.26314 | 2026-07-28
- **核心**: **测量攻击型 Agent 的隐蔽性**——不只是能不能攻击，还要测能不能不被检测到
- **价值**: 反过来用——测你的检测方案能不能抓到隐蔽攻击

---

## 四、Agent 攻击新手法

### 13. LoginTrap: Phishing-Style Indirect Prompt Injection against Web Agents
- **arXiv**: 2608.04741 | 2026-08-05
- **核心**: **针对 Web Agent 的钓鱼式间接提示注入**——攻击登录认证边界，Agent 代替用户登录时被劫持
- **价值**: 新攻击面——Agent 的认证场景是新的攻击向量

### 14. MAFIA: Query-Only Memory Attacks against Audited LLM Agents
- **arXiv**: 2608.03844 | 2026-08-04
- **核心**: **仅通过查询就能污染 Agent 的记忆**——不需要直接写入记忆，通过巧妙的查询触发 Agent 自主写入错误信息
- **价值**: 记忆投毒的新变种——绕过记忆审计机制

### 15. Adversarial Attacks in Multi-Agent LLM Pipelines
- **arXiv**: 2608.00718 | 2026-08-01
- **核心**: **多 Agent 管线中的对抗传播**——一个 Agent 被污染后，恶意内容如何沿管线传播到其他 Agent
- **价值**: 多 Agent 系统的"感染模型"——OWASP T13 的学术实证

### 16. Agent Against Agent: Automatic Prompt Injection Detection
- **arXiv**: 2608.05108 | 2026-08-05
- **核心**: **用 Agent 检测 Agent 的提示注入**——和 ADR 的"LLM 审 LLM"思路一致，但专注于注入检测

---

## 五、Agent 安全基准测试

### 17. StepJack: Benchmarking Computer-Use Agent Safety Against Multi-Step Threats
- **arXiv**: 2608.06477 | 2026-08-06
- **核心**: **计算机使用 Agent（如 Claude Computer Use）的多步威胁基准**——测 Agent 在多步操作中的安全性

### 18. WeClawArena: Auditable Sandbox for Cross-User Agent Collaboration and Security
- **arXiv**: 2608.03499 | 2026-08-04
- **核心**: **跨用户 Agent 协作的可审计沙箱**——当多个用户的 Agent 互相交互时，安全怎么测？

### 19. HarnessSafe: Evaluating Safety Across Persistent Carriers in Agent Harnesses
- **arXiv**: 2608.06984 | 2026-08-07
- **核心**: **评估 Agent 持久化载体的安全性**——记忆、技能、工具、共享产物在跨任务/跨会话时的安全风险

---

## 六、企业级 Agent 权限与治理

### 20. Dynamic Capability Scoping for Enterprise AI Agents
- **arXiv**: 2607.22445 | 2026-07-24
- **核心**: **动态权限范围管理**——不再给 Agent 静态全权限，而是按任务动态授予最小权限
- **价值**: OWASP LLM06 Excessive Agency 的技术解法——三源权限架构 + 合成数据集

### 21. Recursive Governance: Graph-Theoretic Framework for Risk Propagation in Agentic AI
- **arXiv**: 2607.23916 | 2026-07-27
- **核心**: **图论框架追踪 Agent 系统中的风险传播和漂移检测**——金融行业视角
- **价值**: 金融合规场景——传统模型风险管理（MRM）在 Agent 时代失效的应对

### 22. NiyamAI: Intent-Bound AI Agent with Cryptographically Verifiable Guardrails
- **arXiv**: 2608.07167 | 2026-08-07
- **核心**: **意图绑定的 Agent + 密码学可验证护栏**——Agent 的每个操作都必须能密码证明它符合用户原始意图
- **价值**: 和我之前深度解读里提的"默认拒绝+显式授权"模型最接近的学术实现

---

## 七、重要综述

### 23. The Attack and Defense Landscape of Agentic AI: A Comprehensive Survey
- **arXiv**: 2603.11088 | 2026-03
- **作者**: Kim, Liu, ..., **Wenbo Guo, Dawn Song**（UC Berkeley 安全团队）
- **核心**: **Agent AI 攻防全景综述**——Dawn Song 是安全领域顶级学者

### 24. Towards Trustworthy Agentic AI: Survey of Safety, Robustness, Privacy, and System Security
- **arXiv**: 2605.23989 | 2026-05
- **作者**: Qi, Li, ..., **King, Xu**
- **核心**: 可信 Agent AI 的四大维度（安全/鲁棒/隐私/系统安全）全景综述

### 25. Systematization of Knowledge: Security and Safety in MCP Ecosystem
- **arXiv**: 2512.08290 | 2025-12
- **核心**: MCP 生态安全知识系统化（SoK）——MCP 安全的标准学术参考

---

## 按你的使用场景推荐

| 你要干什么 | 优先读哪几篇 |
|-----------|------------|
| **了解 MCP 生态真实威胁面** | #1（21K 实测）、#2（漂移追踪）、#3（混合分析） |
| **设计运行时防护** | #5（轨迹保障）、#6（世界模型护栏）、#7（在线纠偏）、#8（神经元检测） |
| **做红队演练** | #10（AI-Infra-Guard 开源）、#11（OpenART 开源）、#12（隐蔽性测试） |
| **关注新攻击手法** | #13（Web Agent 钓鱼）、#14（记忆投毒）、#15（多 Agent 传播） |
| **企业权限/合规治理** | #20（动态权限）、#21（金融治理）、#22（密码学护栏） |
| **全面了解领域** | #23（Berkeley 综述）、#24（可信 Agent 综述）、#25（MCP SoK） |
