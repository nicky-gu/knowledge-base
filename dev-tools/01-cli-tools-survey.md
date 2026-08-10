# 软件开发基础组件 / CLI 工具生态调研清单

> 聚焦于"安装在本机、通过命令行操作"的开发者基础组件，不包括 IDE、GUI 工具、SaaS 平台。

---

## 1. 代码托管平台 CLI

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **GitHub CLI (gh)** | GitHub 官方 CLI，操作 PR/Issue/Actions/Release 等 | ✅ MIT | https://cli.github.com/ |
| **GitLab CLI (glab)** | GitLab 官方 CLI，操作 MR/Issue/Pipeline 等 | ✅ MIT | https://gitlab.com/gitlab-org/cli |
| **Bitbucket CLI (bb)** | Atlassian 官方 CLI，支持 Bitbucket Cloud（也覆盖 Jira/Confluence） | ❌ 闭源（免费使用） | https://developer.atlassian.com/platform/atlassian-cli/ |
| **Gitea CLI (tea)** | Gitea 官方 CLI，操作仓库/Issue/PR 等 | ✅ MIT | https://gitea.com/gitea/tea |
| **Forgejo CLI** | Forgejo 自带 CLI 子命令（forgejo admin/auth/cron 等），兼容 Gitea tea | ✅ MIT | https://codeberg.org/forgejo/forgejo |
| **GitHub Hub (deprecated)** | GitHub 早期 CLI，已被 gh 替代 | ✅ MIT | https://github.com/github/hub |

---

## 2. 容器与编排

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **Docker CLI** | Docker 容器引擎官方命令行，build/run/push/compose | ✅ Apache-2.0 | https://docs.docker.com/engine/reference/commandline/cli/ |
| **Podman** | 无守护进程、无 root 的容器引擎，CLI 兼容 Docker | ✅ Apache-2.0 | https://podman.io/ |
| **Buildah** | 脚本化构建 OCI 容器镜像（Podman 同生态） | ✅ Apache-2.0 | https://buildah.io/ |
| **Skopeo** | 跨 registry 复制/检查/签名容器镜像 | ✅ Apache-2.0 | https://github.com/containers/skopeo |
| **kubectl** | Kubernetes 集群官方 CLI | ✅ Apache-2.0 | https://kubernetes.io/docs/reference/kubectl/ |
| **Helm** | Kubernetes 包管理器（chart 部署） | ✅ Apache-2.0 | https://helm.sh/ |
| **K9s** | 终端 UI 的 Kubernetes 集群管理工具 | ✅ Apache-2.0 | https://k9scli.io/ |
| **kubectx / kubens** | 快速切换 kubectl context 和 namespace | ✅ Apache-2.0 | https://github.com/ahmetb/kubectx |
| **ctr** | containerd 底层 CLI，调试容器运行时 | ✌️ Apache-2.0（containerd） | https://github.com/containerd/containerd |
| **crictl** | CRI 兼容容器运行时调试 CLI（Kubelet 层） | ✅ Apache-2.0 | https://github.com/kubernetes-sigs/cri-tools |
| **nerdctl** | containerd 的 Docker 兼容 CLI | ✅ Apache-2.0 | https://github.com/containerd/nerdctl |
| **kind** | 用 Docker 运行本地 Kubernetes 集群 | ✅ Apache-2.0 | https://kind.sigs.k8s.io/ |
| **k3d** | 在 Docker 中运行 k3s 轻量集群 | ✅ MIT | https://k3d.io/ |
| **minikube** | 本地单节点 Kubernetes 集群 | ✅ Apache-2.0 | https://minikube.sigs.k8s.io/ |
| **ArgoCD CLI** | GitOps 持续交付控制器命令行 | ✅ Apache-2.0 | https://argo-cd.readthedocs.io/ |
| **istioctl** | Istio 服务网格 CLI | ✅ Apache-2.0 | https://istio.io/latest/docs/ops/diagnostic-tools/istioctl/ |
| **Docker Compose** | 多容器编排（compose CLI 现已内置于 docker） | ✅ Apache-2.0 | https://docs.docker.com/compose/ |
| **lazydocker** | 终端 TUI 的 Docker/Podman 管理工具 | ✅ MIT | https://github.com/jesseduffield/lazydocker |

---

## 3. CI/CD

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **act** | 在本地运行 GitHub Actions 工作流 | ✅ MIT | https://github.com/nektos/act |
| **GitLab CI CLI** | glab 内置 `glab ci` 子命令触发/查看 pipeline | ✅ MIT | https://gitlab.com/gitlab-org/cli |
| **Jenkins CLI (jenkins-cli)** | Jenkins 官方 CLI（java -jar jenkins-cli.jar），触发任务/管理插件 | ✅ MIT | https://www.jenkins.io/doc/book/managing/cli/ |
| **CircleCI CLI** | CircleCI 本地验证/运行 config，orb 打包 | ✅ MIT | https://github.com/CircleCI-Public/circleci-cli |
| **Drone CLI** | Drone CI 命令行，管理 repo/secret/执行本地构建 | ✅ Apache-2.0 | https://docs.drone.io/cli/ |
| **Tekton CLI (tkn)** | Tekton Pipelines CLI | ✅ Apache-2.0 | https://github.com/tektoncd/cli |
| **GitHub Actions runner** | 自托管 runner 控制器（actions-runner） | ✅ MIT | https://github.com/actions/runner |
| **Woodpecker CLI** | Woodpecker CI（Drone 社区分支）的 CLI | ✅ Apache-2.0 | https://woodpecker-ci.org/ |
| ** dagger (Dagger CLI)** | 可编程的 CI/CD 引擎，用代码定义 pipeline | ✅ Apache-2.0 | https://dagger.io/ |

---

## 4. 包管理器

### 语言生态

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **npm** | Node.js 默认包管理器 | ✅ Artistic-2.0 | https://docs.npmjs.com/cli/ |
| **pnpm** | 高性能、磁盘节省的 Node 包管理器 | ✅ MIT | https://pnpm.io/ |
| **yarn (Berry)** | Node 包管理器（Plug'n'Play） | ✅ BSD-2-Clause | https://yarnpkg.com/ |
| **bun** | 全功能 JS 运行时+包管理器+打包器 | ✅ MIT | https://bun.sh/ |
| **deno** | 安全的 JS/TS 运行时，内置包管理 | ✅ MIT | https://deno.land/ |
| **pip** | Python 默认包安装器 | ✅ MIT | https://pip.pypa.io/ |
| **uv** | Astral 出品的超快 Python 包/项目管理器（Rust 实现） | ✅ Apache-2.0 / MIT | https://docs.astral.sh/uv/ |
| **poetry** | Python 依赖管理与打包 | ✅ MIT | https://python-poetry.org/ |
| **pipx** | 全局安装 Python CLI 应用（隔离虚拟环境） | ✅ MIT | https://pipx.pypa.io/ |
| **conda / mamba** | 跨语言科学计算包管理器（mamba 为 C++ 加速版） | ✅ BSD-3-Clause | https://docs.conda.io/ |
| **rye** | Armin Ronacher 的 Rust 实现的 Python 工具链管理器（已并入 uv） | ✅ MIT | https://rye.astral.sh/ |
| **cargo** | Rust 官方包管理器与构建工具 | ✅ MIT / Apache-2.0 | https://doc.rust-lang.org/cargo/ |
| **go (go mod)** | Go 官方模块管理与构建 | ✅ BSD-3-Clause | https://go.dev/ref/mod |
| **maven** | Java 项目构建与依赖管理 | ✅ Apache-2.0 | https://maven.apache.org/ |
| **gradle** | JVM 生态灵活构建系统 | ✅ Apache-2.0 | https://gradle.org/ |
| **sbt** | Scala 构建工具 | ✌️ Apache-2.0 | https://www.scala-sbt.org/ |
| **nuget** | .NET 包管理器 CLI | ✅ Apache-2.0 | https://learn.microsoft.com/nuget/ |
| **dotnet** | .NET SDK CLI（build/test/pack/add） | ✌️ MIT | https://learn.microsoft.com/dotnet/core/tools/ |
| **gem / bundler** | Ruby 包管理器与依赖锁定 | ✌️ MIT / Ruby | https://bundler.io/ |
| **composer** | PHP 依赖管理器 | ✌️ MIT | https://getcomposer.org/ |
| **swift package manager** | Swift 官方包管理器 | ✌️ Apache-2.0 | https://swift.org/package-manager/ |
| **mix** | Elixir 构建工具与包管理器 | ✌️ Apache-2.0 | https://hexdocs.pm/mix/ |
| **rebar3** | Erlang 构建工具 | ✌️ Apache-2.0 | https://www.rebar3.org/ |

### 系统级

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **Homebrew (brew)** | macOS/Linux 非官方包管理器 | ✌️ BSD-2-Clause | https://brew.sh/ |
| **apt / apt-get** | Debian/Ubuntu 包管理器 | ✌️ GPL | https://wiki.debian.org/Apt |
| **dnf / yum** | RHEL/Fedora 系包管理器 | ✌️ GPL-2.0 | https://dnf.readthedocs.io/ |
| **pacman** | Arch Linux 包管理器 | ✌️ GPL-2.0 | https://archlinux.org/pacman/ |
| **zypper** | openSUSE 包管理器 | ✌️ GPL-2.0 | https://en.opensuse.org/Portal:Zypper |
| **nix** | 声明式、可复现的包管理与系统配置 | ✌️ LGPL-2.1 | https://nixos.org/ |
| **snap** | Canonical 的容器化软件包 | ✌️ GPL-3.0 | https://snapcraft.io/ |
| **flatpak** | Linux 桌面应用沙箱分发 | ✌️ LGPL-2.1 | https://flatpak.org/ |
| **winget** | Windows 官方包管理器 | ❌ 闭源（免费） | https://learn.microsoft.com/windows/package-manager/winget/ |
| **scoop** | Windows 命令行安装器（便携式） | ✌️ MIT | https://scoop.sh/ |
| **chocolatey** | Windows 包管理器 | ✌️ Apache-2.0 | https://chocolatey.org/ |

### 版本管理器

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **asdf** | 多语言版本管理器（插件式） | ✌️ MIT | https://asdf-vm.com/ |
| **mise (rtx)** | asdf 兼容的超快版本管理器（Rust） | ✌️ MIT | https://mise.jdx.dev/ |
| **nvm** | Node.js 版本管理器 | ✌️ MIT | https://github.com/nvm-sh/nvm |
| **fnm** | Rust 实现的快速 Node 版本管理器 | ✌️ GPL-3.0 | https://github.com/Schniz/fnm |
| **pyenv** | Python 版本管理器 | ✌️ MIT | https://github.com/pyenv/pyenv |
| **rbenv** | Ruby 版本管理器 | ✌️ MIT | https://github.com/rbenv/rbenv |
| **rustup** | Rust 工具链版本管理器 | ✌️ MIT / Apache-2.0 | https://rustup.rs/ |
| **gvm / goenv** | Go 版本管理器 | ✌️ MIT | https://github.com/go-nv/goenv |
| **sdkman** | JVM 生态多版本管理（Java/Kotlin/Gradle 等） | ✌️ Apache-2.0 | https://sdkman.io/ |

---

## 5. 基础设施即代码 (IaC)

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **Terraform** | HashiCorp 的多云 IaC 工具（HCL） | ✅ MPL-2.0（曾改 BSL，已回退 OSS） | https://www.terraform.io/ |
| **OpenTofu** | Terraform 开源分支（Linux 基金会） | ✅ MPL-2.0 | https://opentofu.org/ |
| **Pulumi** | 用通用编程语言（TS/Python/Go）写 IaC | ✅ Apache-2.0 | https://www.pulumi.com/ |
| **Ansible** | Red Hat 的 agentless 配置管理（YAML） | ✅ GPL-3.0 | https://www.ansible.com/ |
| **AWS CloudFormation** | AWS 原生 IaC 服务（通过 aws cloudformation CLI 操作） | ❌ 闭源 | https://aws.amazon.com/cloudformation/ |
| **AWS CDK** | 用代码生成 CloudFormation 模板 | ✅ Apache-2.0 | https://aws.amazon.com/cdk/ |
| **Chef (knife)** | 基础设施自动化（Ruby DSL），knife 为 CLI | ✅ Apache-2.0 | https://docs.chef.io/workstation/knife/ |
| **Puppet (puppet)** | 声明式配置管理 | ✌️ Apache-2.0 | https://www.puppet.com/ |
| **Salt (salt)** | 事件驱动的远程执行与配置管理 | ✌️ Apache-2.0 | https://saltproject.io/ |
| **Crossplane** | Kubernetes-native 控制面 IaC（通过 kubectl） | ✌️ Apache-2.0 | https://www.crossplane.io/ |
| **Terragrunt** | Terraform 的 DRY 工具（减少重复代码） | ✌️ MIT | https://terragrunt.gruntwork.io/ |
| **Atlantis** | Terraform Pull Request 自动化（通过 Webhook） | ✌️ Apache-2.0 | https://www.runatlantis.io/ |
| **Vagrant** | 本地开发虚拟机管理（Vagrantfile） | ✌️ MIT | https://www.vagrantup.com/ |
| **Packer** | HashiCorp 的机器镜像构建工具 | ✌️ MPL-2.0 | https://www.packer.io/ |

---

## 6. 云平台 CLI

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **AWS CLI (aws)** | Amazon Web Services 官方 CLI | ✌️ Apache-2.0 | https://aws.amazon.com/cli/ |
| **Azure CLI (az)** | Microsoft Azure 官方 CLI | ✌️ MIT | https://learn.microsoft.com/cli/azure/ |
| **Google Cloud CLI (gcloud)** | Google Cloud Platform 官方 CLI | ❌ 闭源（免费） | https://cloud.google.com/sdk/gcloud |
| **腾讯云 CLI (tccli)** | 腾讯云 API 3.0 官方 CLI | ✌️ Apache-2.0 | https://github.com/TencentCloud/tencentcloud-cli |
| **阿里云 CLI (aliyun)** | 阿里云官方 CLI | ✌️ Apache-2.0 | https://github.com/aliyun/aliyun-cli |
| **华为云 CLI (hcloud)** | 华为云 CLI 3.0（基于开源 aoc） | ✌️ Apache-2.0 | https://github.com/huaweicloud/huaweicloud-cli |
| **京东云 CLI (jdcloud)** | 京东云官方 CLI | ✌️ Apache-2.0 | https://docs.jdcloud.com/cn/cli/product-overview |
| **Cloudflare Wrangler** | Cloudflare Workers/Pages 开发与部署 CLI | ✌️ MIT / Apache-2.0 | https://developers.cloudflare.com/workers/wrangler/ |
| **DigitalOcean CLI (doctl)** | DigitalOcean 官方 CLI | ✌️ Apache-2.0 | https://github.com/digitalocean/doctl |
| **Linode/Akamai CLI (linode-cli)** | Akamai（原 Linode）云计算 CLI | ✌️ BSD-3-Clause | https://github.com/linode/linode-cli |
| **Vultr CLI (vultr-cli)** | Vultr 云平台 CLI | ✌️ Apache-2.0 | https://github.com/vultr/vultr-cli |
| **Hetzner CLI (hcloud)** | Hetzner Cloud 官方 CLI | ✌️ MIT | https://github.com/hetznercloud/cli |
| **Scaleway CLI (scw)** | Scaleway 官方 CLI | ✌️ BSD-3-Clause | https://github.com/scaleway/scaleway-cli |
| **Fly.io CLI (flyctl)** | Fly.io 边缘应用部署 CLI | ✌️ Apache-2.0 | https://fly.io/docs/hands-on/install-flyctl/ |
| **Render CLI** | Render.com PaaS 部署 CLI | ✌️ MIT | https://render.com/docs/cli |
| **Vercel CLI** | Vercel 前端托管/Serverless 部署 CLI | ✌️ Apache-2.0 | https://vercel.com/docs/cli |
| **Netlify CLI** | Netlify 静态站点/Serverless CLI | ✌️ MIT | https://docs.netlify.com/cli/get-started/ |
| **Railway CLI** | Railway.app 部署 CLI | ✌️ MIT | https://docs.railway.app/develop/cli |
| **Supabase CLI** | Supabase 后端开发 CLI（DB/Auth/Edge Functions） | ✌️ Apache-2.0 | https://supabase.com/docs/guides/cli |
| **Firebase CLI** | Google Firebase 项目 CLI | ✌️ MIT | https://firebase.google.com/docs/cli |
| **Heroku CLI** | Heroku PaaS 部署 CLI | ✌️ ISC / MIT | https://devcenter.heroku.com/articles/heroku-cli |
| **OpenStack CLI (openstack)** | OpenStack 云管理统一 CLI | ✌️ Apache-2.0 | https://docs.openstack.org/python-openstackclient/ |
| **Rancher CLI (rancher)** | Rancher 多集群 K8s 管理 CLI | ✌️ Apache-2.0 | https://ranchermanager.docs.rancher.com/reference-guides/cli-with-rancher |
| **OCI CLI (oci)** | Oracle Cloud Infrastructure CLI | ✌️ Apache-2.0 / UPL | https://docs.oracle.com/en-us/iaas/Content/API/Concepts/cliconcepts.htm |

---

## 7. 开发效率工具

### 文本 / 数据处理

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **jq** | 轻量级命令行 JSON 处理器 | ✌️ MIT | https://jqlang.github.io/jq/ |
| **yq** | YAML 处理器（类似 jq，也支持 JSON/XML/TOML/CSV） | ✌️ MIT | https://github.com/mikefarah/yq |
| **dasel** | 通用数据格式选择/修改（JSON/YAML/TOML/XML/CSV） | ✌️ MIT | https://github.com/TomWright/dasel |
| **gron** | 将 JSON 展平为可 grep 的文本 | ✌️ MIT | https://github.com/tomnomnom/gron |
| **xsv** | 快速 CSV 索引/切片/拼接（Rust） | ✌️ MIT / Unlicense | https://github.com/BurntSushi/xsv |
| **csvkit** | CSV 实用工具集（Python） | ✌️ MIT | https://github.com/wireservice/csvkit |
| ** miller (mlr)** | 类 awk 的 CSV/TSV/JSON/Lines 数据处理 | ✌️ MIT | https://miller.readthedocs.io/ |
| **htmlq** | 类 jq 的 HTML 处理器（基于 Go） | ✌️ MIT | https://github.com/mgdm/htmlq |
| **fq** | 类 jq 的二进制格式查看器（jq + binary） | ✌️ BSD-3-Clause | https://github.com/wader/fq |

### 搜索 / 查找

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **ripgrep (rg)** | 超快递归搜索（替代 grep，Rust 实现） | ✌️ MIT / Unlicense | https://github.com/BurntSushi/ripgrep |
| **fd (fd-find)** | 简单快速的 find 替代品（Rust） | ✌️ MIT / Apache-2.0 | https://github.com/sharkdp/fd |
| **fzf** | 通用命令行模糊查找器 | ✌️ MIT | https://github.com/junegunn/fzf |
| **ag (the_silver_searcher)** | 快速代码搜索（C 实现，ack 替代） | ✌️ Apache-2.0 | https://github.com/ggreer/the_silver_searcher |
| **ack** | 为程序员优化的 grep（Perl） | ✌️ Artistic-2.0 | https://beyondgrep.com/ |
| **navi** | 交互式 cheatsheet 工具（基于 fzf） | ✌️ Apache-2.0 | https://github.com/denisidoro/navi |

### 查看 / 浏览

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **bat** | 带语法高亮和 Git 集成的 cat 克隆（Rust） | ✅ MIT / Apache-2.0 | https://github.com/sharkdp/bat |
| **eza** | exa 的社区维护分支，现代 ls 替代品（Rust） | ✅ MIT | https://github.com/eza-community/eza |
| **delta (git-delta)** | 为 diff/blame/grep 提供语法高亮的分页器 | ✅ MIT | https://github.com/dandavison/delta |
| **glow** | 终端 Markdown 渲染器（Go） | ✅ MIT | https://github.com/charmbracelet/glow |
| **mdcat** | 终端 Markdown 渲染器（Rust，支持图片） | ✅ MPL-2.0 | https://github.com/swsnr/mdcat |
| **tig** | 终端文本模式 Git 仓库浏览器 | ✅ GPL-2.0 | https://github.com/jonas/tig |
| **broot** | 交互式目录树浏览与导航 | ✅ MIT | https://dystroy.org/broot/ |
| **vifm / ranger / yazi** | 终端文件管理器（yazi 为 Rust 超快版） | ✅ GPL / MIT | https://yazi-rs.github.io/ |

### Shell / 终端增强

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **tmux** | 终端多路复用器（会话/窗口/面板管理） | ✅ ISC | https://github.com/tmux/tmux |
| **screen** | GNU 终端多路复用器（经典） | ✅ GPL-3.0 | https://www.gnu.org/software/screen/ |
| **zellij** | 现代 Rust 终端多路复用器 | ✅ MIT | https://zellij.dev/ |
| **starship** | 跨 shell 的可定制提示符（Rust） | ✅ ISC | https://starship.rs/ |
| **powerlevel10k** | Zsh 主题，极速提示符 | ✅ MIT | https://github.com/romkatv/powerlevel10k |
| **oh-my-zsh** | Zsh 配置管理框架 | ✅ MIT | https://ohmyz.sh/ |
| **zsh / fish** | 更强大的现代 shell | ✅ MIT / BSD-2-Clause | https://www.zsh.org/ / https://fishshell.com/ |
| **atuin** | 用 SQLite 加密的 shell 历史搜索 | ✅ MIT | https://atuin.sh/ |
| **mcfly** | 智能Shell 历史搜索（神经网络排序） | ✅ MIT | https://github.com/cantino/mcfly |
| **zoxide** | 更聪明的 cd 命令（学习频率排序） | ✅ MIT | https://github.com/ajeetdsouza/zoxide |
| **autojump / z** | 基于频率的目录跳转 | ✅ GPL-3.0 | https://github.com/wting/autojump |
| **direnv** | 根据目录自动加载/卸载环境变量 | ✅ MIT | https://direnv.net/ |
| **mise** | 前述多语言版本管理器，也做 env/tasks 管理 | ✅ MIT | https://mise.jdx.dev/ |
| **fig / Amazon Q** | 终端自动补全与 AI 助手（原 Fig，已被 AWS 收购） | ❌ 闭源（免费） | https://aws.amazon.com/q/developer/ |
| **tmuxinator / zellij sessions** | 声明式管理 tmux/zellij 会话 | ✅ MIT | https://github.com/tmuxinator/tmuxinator |

### 项目脚手架

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **cookiecutter** | Python 项目模板生成器 | ✅ BSD-3-Clause | https://github.com/cookiecutter/cookiecutter |
| **cruft** | cookiecutter 的持续更新工具 | ✅ MIT | https://github.com/cruft/cruft |
| **yeoman (yo)** | Web 生态项目脚手架生成器 | ✅ BSD-2-Clause | https://yeoman.io/ |
| **plop** | 微型脚手架工具（Node.js） | ✅ MIT | https://plopjs.com/ |
| **giter8 (g8)** | Scala/Java 项目模板 | ✅ Apache-2.0 | https://www.foundweekends.org/giter8/ |
| **create-react-app / degit** | 前端项目脚手架/仓库克隆 | ✅ MIT | https://github.com/Rich-Harris/degit |

---

## 8. 代码质量与安全

### Linter / 格式化

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **ESLint** | JavaScript/TypeScript linter | ✅ MIT | https://eslint.org/ |
| **Prettier** | 多语言代码格式化器（JS/CSS/MD 等） | ✅ MIT | https://prettier.io/ |
| **gofmt / gofmt** | Go 官方代码格式化 | ✅ BSD-3-Clause | https://pkg.go.dev/cmd/gofmt |
| **rustfmt / clippy** | Rust 官方格式化与 lint | ✅ MIT / Apache-2.0 | https://rust-lang.github.io/rustfmt-clippy/ |
| **black** | Python 代码格式化（无争议格式） | ✅ MIT | https://github.com/psf/black |
| **ruff** | 超快 Python linter/formatter（Rust，替代 flake8/isort 等） | ✅ MIT | https://docs.astral.sh/ruff/ |
| **mypy** | Python 静态类型检查器 | ✅ MIT | https://mypy-lang.org/ |
| **pylint** | Python 代码分析 linter | ✅ GPL-2.0 | https://pylint.readthedocs.io/ |
| **flake8** | Python 风格检查（pycodestyle+pyflakes） | ✅ MIT | https://flake8.pycqa.org/ |
| **isort** | Python import 排序 | ✅ MIT | https://pycqa.github.io/isort/ |
| **ShellCheck** | Shell 脚本静态分析与 lint | ✅ GPL-3.0 | https://www.shellcheck.net/ |
| **shfmt** | Shell 脚本格式化 | ✅ BSD-3-Clause | https://github.com/mvdan/sh |
| **Hadolint** | Dockerfile linter | ✅ GPL-3.0 | https://github.com/hadolint/hadolint |
| **markdownlint** | Markdown 格式 lint | ✅ MIT | https://github.com/DavidAnson/markdownlint |
| **yamllint** | YAML 格式与语法 lint | ✅ GPL-3.0 | https://yamllint.readthedocs.io/ |
| **tflint** | Terraform lint（AWS/Azure/GCP 规则） | ✅ MPL-2.0 | https://github.com/terraform-linters/tflint |
| **checkov / tfsec** | IaC 安全扫描（Terraform/CloudFormation/K8s） | ✅ Apache-2.0 / MIT | https://www.checkov.io/ |
| **golangci-lint** | Go 聚合 linter（集成数十种 Go lint） | ✅ GPL-3.0 | https://golangci-lint.run/ |
| **staticcheck** | Go 静态分析工具 | ✅ MIT | https://staticcheck.io/ |
| **Revive** | Go linter（golint 继任者） | ✅ MIT | https://github.com/mgechev/revive |
| **Spotbugs** | Java 静态分析（FindBugs 继任） | ✅ LGPL-2.1 | https://spotbugs.github.io/ |
| **Checkstyle** | Java 代码规范检查 | ✅ LGPL-2.1 | https://checkstyle.org/ |
| **PMD** | 多语言（Java/JS/Apex）静态分析 | ✅ BSD-2-Clause | https://pmd.github.io/ |
| **PHP_CodeSniffer** | PHP 编码标准检测 | ✅ BSD-3-Clause | https://github.com/squizlabs/PHP_CodeSniffer |
| **PHPStan** | PHP 静态分析 | ✅ MIT | https://phpstan.org/ |
| **RuboCop** | Ruby linter/formatter | ✅ MIT | https://rubocop.org/ |
| **Credo** | Elixir 静态代码分析 | ✅ MIT | https://github.com/rrrene/credo |
| **Deno lint / deno fmt** | Deno 内置 JS/TS lint 与格式化 | ✅ MIT | https://deno.land/ |

### 安全扫描

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **Trivy** | 容器镜像/文件系统/git/IaC 漏洞扫描 | ✅ Apache-2.0 | https://aquasecurity.github.io/trivy/ |
| **Grype** | 容器镜像和文件系统漏洞扫描（Anchore） | ✅ Apache-2.0 | https://github.com/anchore/grype |
| **Syft** | SBOM（软件物料清单）生成 | ✅ Apache-2.0 | https://github.com/anchore/syft |
| **Snyk CLI** | 依赖漏洞扫描与修复（多语言） | ❌ 闭源（免费版） | https://docs.snyk.io/snyk-cli |
| **OWASP Dependency-Check** | 依赖 CVE 检测 | ✅ Apache-2.0 | https://owasp.org/www-project-dependency-check/ |
| **Semgrep** | 基于模式匹配的代码安全扫描（多语言 SAST） | ✅ LGPL-2.1 | https://semgrep.dev/ |
| **SonarQube CLI (sonar-scanner)** | 代码质量与安全扫描器（送至 SonarQube 服务端） | ✅ LGPL-3.0 | https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/scanners/sonarscanner/ |
| **Bandit** | Python 安全问题 linter | ✅ Apache-2.0 | https://github.com/PyCQA/bandit |
| **Gosec** | Go 安全代码扫描 | ✅ Apache-2.0 | https://github.com/securego/gosec |
| **Brakeman** | Ruby on Rails 静态安全扫描 | ✅ MIT | https://brakemanscanner.org/ |
| **go-vuln (govulncheck)** | Go 官方漏洞检测 | ✅ BSD-3-Clause | https://pkg.go.dev/golang.org/x/vuln/cmd/govulncheck |
| **npm audit / pip-audit / cargo audit** | 语言级依赖漏洞检查 | ✅ 各种 | https://docs.npmjs.com/cli/audit |
| **Cosign (sigstore)** | 容器镜像签名与验证 | ✅ Apache-2.0 | https://github.com/sigstore/cosign |
| **gitleaks** | Git 仓库密钥/凭证泄漏扫描 | ✅ MIT | https://github.com/gitleaks/gitleaks |
| **truffleHog** | 深度凭证/密钥搜索 | ✅ GPL-2.0 | https://github.com/trufflesecurity/trufflehog |
| **kube-bench** | Kubernetes CIS Benchmark 检查 | ✅ Apache-2.0 | https://github.com/aquasecurity/kube-bench |
| **kube-hunter** | Kubernetes 集群主动渗透测试 | ✅ Apache-2.0 | https://github.com/aquasecurity/kube-hunter |
| **Dive** | Docker 镜像层分析工具 | ✅ MIT | https://github.com/wagoodman/dive |
| **Claire** | 容器漏洞扫描（CoreOS，较早期） | ✅ Apache-2.0 | https://github.com/quay/clair |

---

## 9. API 调试

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **curl** | 最广泛使用的命令行 HTTP 客户端 | ✅ MIT/curl | https://curl.se/ |
| **HTTPie** | 人性化 HTTP 客户端（语法直观） | ✅ BSD-3-Clause | https://httpie.io/ |
| **jq** | JSON 响应处理与提取（见效率工具） | ✅ MIT | https://jqlang.github.io/jq/ |
| **Newman** | Postman 集合的命令行运行器 | ✅ Apache-2.0 | https://github.com/postmanlabs/newman |
| **grpcurl** | gRPC 服务调试（类似 curl） | ✅ MIT | https://github.com/fullstorydev/grpcurl |
| **grpcui** | gRPC 交互式 Web UI（基于 grpcurl） | ✅ MIT | https://github.com/fullstorydev/grpcui |
| **buf** | Protobuf API 管理 + gRPC 客户端 | ✅ Apache-2.0 | https://buf.build/ |
| **evans** | 更通用的 gRPC 客户端（交互式 REPL） | ✅ MIT | https://github.com/ktr0731/evans |
| **websocat** | 命令行 WebSocket 客户端（类 curl） | ✅ MIT | https://github.com/vi/websocat |
| **wscat** | WebSocket 命令行客户端（Node.js） | ✅ Apache-2.0 | https://github.com/websockets/wscat |
| **step / openssl s_client** | TLS/SSL 调试 | ✅ Apache-2.0 / Apache | https://smallstep.com/docs/step-cli/ |
| **xh** | Rust 实现的 HTTPie 替代品（更快） | ✅ MIT | https://github.com/ducaale/xh |
| **curlie** | curl 前端 + HTTPie 语法 | ✅ MIT | https://github.com/rs/curlie |
| **vegeta** | HTTP 负载测试工具（Go） | ✅ MIT | https://github.com/tsenart/vegeta |
| **hey** | HTTP 压测工具（Go） | ✅ MIT | https://github.com/rakyll/hey |
| **k6** | Grafana 的现代负载测试工具 | ✅ AGPL-3.0 | https://k6.io/ |
| **ab (Apache Bench)** | 经典 HTTP 基准测试 | ✅ Apache-2.0 | https://httpd.apache.org/docs/current/programs/ab.html |
| **wrk** | 现代 HTTP 基准测试（C，多线程） | ✅ Apache-2.0 | https://github.com/wg/wrk |
| **postman CLI** | Postman 新一代命令行（CI 友好） | ❌ 闭源（免费） | https://www.postman.com/product/cli/ |
| **hurl** | 纯文本定义的 HTTP 请求运行（Rust） | ✅ Apache-2.0 | https://hurl.dev/ |
| **cidr / mitmproxy (mitmdump)** | 命令行 HTTP 代理抓包 | ✅ MIT | https://mitmproxy.org/ |

---

## 10. 版本控制增强

| 工具 | 一句话定位 | 开源 | 官方链接 |
|------|-----------|------|---------|
| **Git** | 分布式版本控制系统（核心） | ✅ GPL-2.0 | https://git-scm.com/ |
| **lazygit** | 终端 TUI 的 Git 操作（简单且强大） | ✅ MIT | https://github.com/jesseduffield/lazygit |
| **tig** | 终端 Git 历史浏览器（文本模式） | ✅ GPL-2.0 | https://github.com/jonas/tig |
| **git-delta (delta)** | diff/blame 高亮分页器（见效率工具） | ✅ MIT | https://github.com/dandavison/delta |
| **gh (GitHub CLI)** | GitHub 平台 CLI（见代码托管平台） | ✅ MIT | https://cli.github.com/ |
| **git-extras** | Git 工具集扩展（60+ 子命令） | ✅ MIT | https://github.com/tj/git-extras |
| **git-flow** | Vincent Driessen 的 Git 分支模型工具 | ✅ BSD-2-Clause | https://github.com/nvie/gitflow |
| **git-lfs** | Git 大文件存储 | ✅ MIT | https://git-lfs.com/ |
| **git-filter-repo** | 快速重写 Git 历史（filter-branch 替代） | ✅ GPL-2.0 | https://github.com/newren/git-filter-repo |
| **git-cliff** | 从 conventional commits 生成 Changelog | ✅ GPL-3.0 | https://git-cliff.org/ |
| **commitizen (cz)** | 交互式规范 commit 消息工具 | ✅ MIT | https://github.com/commitizen/cz-cli |
| **commitlint** | commit 消息格式检查 | ✅ MIT | https://commitlint.js.org/ |
| **husky** | Git hooks 管理（Node.js） | ✅ MIT | https://typicode.github.io/husky/ |
| **pre-commit** | 多语言 pre-commit hooks 管理框架 | ✅ MIT | https://pre-commit.com/ |
| **lefthook** | 快速 Git hooks 管理器（Go，并行执行） | ✅ MIT | https://github.com/evilmartians/lefthook/ |
| **semantic-release** | 全自动语义化版本发布 | ✅ MIT | https://github.com/semantic-release/semantic-release |
| **standard-version** | conventional-changelog 自动版本（已废弃，推荐 release-please） | ✅ ISC | https://github.com/conventional-changelog/standard-version |
| **release-please** | Google 的自动版本/release PR 工具 | ✅ Apache-2.0 | https://github.com/googleapis/release-please |
| **changeloguru** | 从 conventional commits 生成 changelog（Go） | ✅ MIT | https://github.com/changeloguru/changeloguru |
| **bfg-repo-cleaner** | 从 Git 历史中删除大文件/敏感数据 | ✅ GPL-3.0 | https://github.com/rtyley/bfg-repo-cleaner |
| **forgit** | fzf + git 交互式操作 | ✅ MIT | https://github.com/wfxr/forgit |
| **gitui** | Rust 实现的终端 Git TUI | ✅ MIT | https://github.com/extrawurst/gitui |
| **gitsign** | sigstore 为 git commit 签名（keyless） | ✅ Apache-2.0 | https://github.com/sigstore/gitsign |
| **gh CLI extensions** | gh 的插件扩展机制（社区维护扩展生态） | ✅ MIT | https://cli.github.com/manual/gh_extension |

---

## 附：工具安装快速参考

| 平台 | 包管理器 | 安装示例 |
|------|---------|---------|
| macOS | Homebrew | `brew install gh docker kubectl helm fzf ripgrep fd bat jq yq starship` |
| Linux (Debian/Ubuntu) | apt + 其他 | `apt install git curl jq docker.io kubectl; snap install ...; 或通过官方安装脚本` |
| Linux (Arch) | pacman | `pacman -S github-cli docker kubernetes-helm fzf ripgrep fd bat jq yq starship` |
| Windows | winget / scoop | `winget install GitHub.cli Docker.DockerDesktop Kubernetes.kubectl; scoop install fzf ripgrep fd bat jq yq starship` |
| 跨平台 (Node) | npm | `npm install -g newman httpie commitizen` |
| 跨平台 (Python) | pipx | `pipx install cookiecutter pre-commit` |
| 跨平台 (Rust) | cargo | `cargo install git-delta` |
| 跨平台 (Go) | go install | `go install github.com/jesseduffield/lazygit@latest` |

---

> **说明：** ✅ = 完全开源（OSI 批准许可证）；❌ = 闭源/专有（可能免费使用）。本清单聚焦于安装在本地终端、通过命令行交互的开发者工具，不含 IDE 插件、GUI 应用或纯 SaaS 平台。