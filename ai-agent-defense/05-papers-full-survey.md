我现在已经拥有了涵盖所有六个所需研究方向的海量数据集。让我来整理最终报告。

---

# AI Agent 安全论文与研究报告系统性搜索结果（2025-2026）

## 搜索方法
- arXiv API：10+ 组关键词搜索，覆盖 cs.CR 安全类别，按日期降序排列
- GitHub API：搜索 `ai-agent-security`、`mcp-security`、`llm-guardrails` 三个主题
- Semantic Scholar API：交叉引用验证（多数论文为近 1-2 个月发布，引用数均为 0）

以下按研究方向分类，排除已有论文（ADR 2605.17380、Hou et al. 2503.23278、MCPXKIT 2508.12538、MCP Safety Audit 2504.03767）。

---

## 一、MCP 协议安全分析（6 篇）

### 1. Rethinking MCP Security: A Large-Scale Study of Runtime MCP Servers and Security Scanner Reliability
- **arXiv**: 2607.11086
- **作者/机构**: Pei Chen, Baichao An, Mengying Wu, Geng Hong, Xudong Pan, Jiarun Dai, Min Yang（复旦大学 系统软件与安全实验室）
- **时间**: 2026-07-13
- **核心贡献**: 首个大规模运行时 MCP 服务器实证研究，构建真实运行环境，评估现有安全扫描器可靠性，发现大规模误报/漏报问题
- **开源代码**: 是（扩展自 MCPZoo 数据集 arXiv:2512.15144）
- **实测数据**: 是（18 页，11 图，10 表，大规模 MCP 服务器数据集）
- **引用**: 0（新发）

### 2. FlowGuard: From Signals to Evidence for MCP Security Detection
- **arXiv**: 2607.14754
- **作者/机构**: Baichao An, Pei Chen, Geng Hong, Yueyue Chen, Mengying Wu（复旦大学）
- **时间**: 2026-07-16
- **核心贡献**: 提出 FlowGuard——基于实际执行行为而非语义信号的 MCP 安全检测框架，解决现有扫描器"靠猜"的问题
- **开源代码**: 未明确
- **实测数据**: 是

### 3. Hybrid Analysis for Secure MCP Tool Use in LLM Agents
- **arXiv**: 2607.25297
- **作者/机构**: Ping He, Yuexiang Xie, Yaliang Li, **Shouling Ji**（浙江大学 / 蚂蚁集团）
- **时间**: 2026-07-28
- **核心贡献**: 混合分析（静态+动态）框架，检测 MCP 工具使用中的安全风险
- **开源代码**: 未明确
- **实测数据**: 是

### 4. Exposed by Design: A Dynamic Security Assessment of Internet-Facing MCP Servers at Scale
- **arXiv**: 2608.00150
- **作者/机构**: Nicolás Padilla
- **时间**: 2026-07-31
- **核心贡献**: 首个对公网暴露的 21,000+ MCP 服务器实例进行动态行为安全评估，覆盖 11 个数据源（crt.sh, HuggingFace, GitHub, npm, Smithery, PyPI, Censys, FOFA, Shodan, glama.ai, pulsemcp）
- **开源代码**: 未明确
- **实测数据**: 是（大规模实测）

### 5. Mitigating Taint-Style Vulnerabilities in MCP Servers via Security-Aware Tool Descriptions
- **arXiv**: 2607.07461
- **作者/机构**: Yang Shi, Jiaheng Fu, Yihe Huang, Ruixiang Wu, Chengyao Sun, Kaifeng Huang
- **时间**: 2026-07-08
- **核心贡献**: 识别 MCP 服务器中跨服务器的通用污点式漏洞模式，提出安全感知工具描述方案
- **开源代码**: 未明确
- **实测数据**: 是

### 6. ChainWatch: A Kill Chain-Aligned Sequential Detection Framework for Multi-Step Attacks in MCP-Based AI Agent Systems
- **arXiv**: 2607.19432
- **作者/机构**: Om Narayan, Rashmi Jyoti, Ramkinker Singh
- **时间**: 2026-07-20
- **核心贡献**: 针对攻击者将多个单独无害的工具调用组合为恶意序列的问题，提出对齐 Kill Chain 的序列检测框架
- **开源代码**: 未明确
- **实测数据**: 是

---

## 二、Agent 攻击手法（8 篇）

### 7. SynChain: Inducing Computer-Use Agent Systems to Construct Their Own Attack Chains
- **arXiv**: 2608.06862
- **作者/机构**: Fuyao Zhang, Jiaming Zhang 等（多机构）
- **时间**: 2026-08-07
- **核心贡献**: 揭示计算机使用代理（CUA）可通过自身持久化制品（skills/memory）内部传播攻击，从外部触发转向内生攻击链构造
- **开源代码**: 未明确
- **实测数据**: 是

### 8. StepJack: Benchmarking Computer-Use Agent Safety Against Multi-Step Indirect Prompt Injection
- **arXiv**: 2608.06477
- **作者/机构**: Zhuoxin Zhan, Akbar Rafiey, Avery Ma, Leila Pishdad, **Layla El Asri**（华为 Noah's Ark Lab）
- **时间**: 2026-08-06
- **核心贡献**: 提出多步间接 prompt injection 攻击类别——将对抗目标分解为看似无害的子步骤，分布到页面链中
- **开源代码**: 未明确
- **实测数据**: 是（基准测试）

### 9. LoginTrap: Uncovering Task-Agnostic Phishing-Style Indirect Prompt Injection Attacks against LLM-based Web Agents
- **arXiv**: 2608.04741
- **作者/机构**: Longtao Guo, Zelin Zhang, Kaifeng Huang, Yang Shi
- **时间**: 2026-08-05
- **核心贡献**: 发现 Web Agent 登录环节的钓鱼式间接 prompt injection 攻击，揭示认证边界安全风险
- **开源代码**: 未明确
- **实测数据**: 是

### 10. Breadcrumbing Search Agents
- **arXiv**: 2608.04565
- **作者/机构**: Xuebin Li, Hanqing Zhao, Siyuan Liang, Kejiang Chen, **Weiming Zhang, Dacheng Tao, Nenghai Yu**（中科大 / USTC）
- **时间**: 2026-08-05
- **核心贡献**: 针对搜索 Agent 的动态查询跟踪和跨链行为，提出"面包屑"攻击——通过引导 Agent 递归查询到恶意内容
- **开源代码**: 未明确
- **实测数据**: 是

### 11. SkillJack: Persistent Skill Backdoors in Self-Evolving Agents
- **arXiv**: 2608.03509
- **作者/机构**: Zonghao Ying, Xiangfan Wu 等
- **时间**: 2026-08-04
- **核心贡献**: 发现自进化 Agent 的全新攻击面——毒化经验可被 Agent 自身转化为持久化的行为后门（skill backdoors），比 memory poisoning 更深层
- **开源代码**: 未明确
- **实测数据**: 是

### 12. PoisonedEvolution: Trajectory Poisoning in Self-Evolving Agent Skill Systems
- **arXiv**: 2608.05563
- **作者/机构**: Jialuo Chen, Lingqi Jiang, Xinhao Deng 等
- **时间**: 2026-08-06
- **核心贡献**: 自进化技能系统的轨迹投毒攻击——攻击者只需贡献有限证据即可在 skill 升级过程中植入后门
- **开源代码**: 未明确
- **实测数据**: 是

### 13. Cross-Agent Campaign Attribution: Linking Asynchronous Attacks Across LLM Agents
- **arXiv**: 2607.18826
- **作者/机构**: SangJin Park, Myungsub Choi, Jineok Kim, Minseung Kang
- **时间**: 2026-07-21
- **核心贡献**: 形式化跨 Agent 异步攻击归因——将分布在独立 Agent/团队/运行时中的稀疏攻击片段链接为同一对抗活动
- **开源代码**: 未明确
- **实测数据**: 是

### 14. Benign Alone, Harmful Together: Exploiting Experience Composition in Self-Evolving LLM Agents
- **arXiv**: 2608.01759
- **作者/机构**: Bingyu Yan, Xiaoming Zhang 等
- **时间**: 2026-08-03
- **核心贡献**: 发现单独无害的经验在被积累和重用时可能联合削弱 Agent 安全边界的组合攻击
- **开源代码**: 未明确
- **实测数据**: 是

---

## 三、Memory Poisoning / 持久化攻击（4 篇）

### 15. MAPLE-Guard: Memory-Aware Link Enforcement Against Memory-Link Poisoning in Multi-Agent Systems
- **arXiv**: 2608.00426
- **作者/机构**: Wenjun Xiong, Yijin Zhou, Jiaqian Wang, **Shangding Gu**, Bo Tang 等
- **时间**: 2026-08-01
- **核心贡献**: 针对多 Agent 系统中 memory-link poisoning 的防御方案——防止单次投毒写入被持续检索、提升到共享内存并跨 Agent 复用
- **开源代码**: **是**（https://github.com/xiong-wenjun/MAPLE-Guard）
- **实测数据**: 是（27 页，14 图，9 表）
- **引用**: 0

### 16. MemPoison: Uncovering Persistent Memory Threats and Structural Blind Spots in LLM Agents
- **arXiv**: 2607.14651
- **作者/机构**: Jifeng Gao, Kang Xia, Yi Zhang 等（南京大学）
- **时间**: 2026-07-16
- **核心贡献**: 全面内存投毒基准测试——1227 个手工验证案例，覆盖 4 种攻击类型，揭示现有防御的结构性盲点
- **开源代码**: 未明确
- **实测数据**: **是（大规模基准）**

### 17. MemSecBench: Tracking Agent Memory Poisoning from Persistence to Consequence and Repair
- **arXiv**: 2607.27080
- **作者/机构**: Xuanze Chen, Xukang Xie 等（浙江大学）
- **时间**: 2026-07-29
- **核心贡献**: 从持久化→后果→修复全生命周期跟踪 Agent 内存投毒的基准测试
- **开源代码**: 未明确
- **实测数据**: 是

### 18. Isolated but Exposed: Persistence-Based Memory Extraction Attack on LLM Agents
- **arXiv**: 2607.23444
- **作者/机构**: Xinyu Gao 等（山东大学）
- **时间**: 2026-07-26
- **核心贡献**: 证明即使用户内存隔离（绑定唯一 ID），仍可通过持久化机制提取隐私数据
- **开源代码**: 未明确
- **实测数据**: 是

---

## 四、Agent 防御/检测方案（6 篇）

### 19. DreamGuard: Efficient Runtime Guardrail for LLM Agents via Risk-Aware World Model
- **arXiv**: 2608.05695
- **作者/机构**: Wenhao Lin, Chenyu Yu 等（西电 / 国防科大）
- **时间**: 2026-08-06
- **核心贡献**: 基于风险感知世界模型的前瞻式 runtime guardrail——不仅检查当前动作安全性，还预测后续状态变化
- **开源代码**: 未明确
- **实测数据**: 是

### 20. AgentAntibody: An Adaptive Immune System for Defending LLM Agents against Prompt Injection
- **arXiv**: 2608.04053
- **作者/机构**: Shihao Weng, Yang Feng, Xiaofei Xie, Jiongchi Yu
- **时间**: 2026-08-04
- **核心贡献**: 借鉴生物免疫系统的自适应防御——从历史交互中学习并积累"抗体"来检测新型 prompt injection
- **开源代码**: 未明确
- **实测数据**: 是

### 21. S³: Improving Agent Safety through Multi-Stage Defense
- **arXiv**: 2608.02683
- **作者/机构**: Zibo Xiao, **Haoyu Wang**, Jun Sun（新加坡管理大学）
- **时间**: 2026-08-03
- **核心贡献**: 覆盖 memory→planning→tool execution 全链路的多阶段 Agent 安全防御框架
- **开源代码**: 未明确
- **实测数据**: 是

### 22. Agent Against Agent (PIMiner): An Agentic System for Automatic Prompt Injection Red Teaming
- **arXiv**: 2608.05108
- **作者/机构**: Yanting Wang, Chenlong Yin, Runpeng Geng, **Jinyuan Jia**（Virginia Tech）
- **时间**: 2026-08-05
- **核心贡献**: 用 Agent 自动化进行 prompt injection 红队测试，替代 RL 方式，泛化性更强
- **开源代码**: **是**（https://github.com/wang-yanting/PIMiner）
- **实测数据**: 是

### 23. Securing Agentic AI: From Per-Action Checks to Trajectory Assurance
- **arXiv**: 2608.01558
- **作者/机构**: Alireza Lotfi, Subangkar Karmaker Shanto, **Imtiaz Karim, Elisa Bertino**（Purdue University）
- **时间**: 2026-08-03（ACM AI Leadership Summit 2026）
- **核心贡献**: 提出从单动作检查向轨迹级保证转变的安全范式
- **开源代码**: 未明确
- **实测数据**: 是

### 24. Robust Context-Aware Detection of Malicious Instructions in Text
- **arXiv**: 2608.05430
- **作者/机构**: Buzhao Liu, Xinhang Ma, **Yevgeniy Vorobeychik**（Washington University in St. Louis）
- **时间**: 2026-08-05
- **核心贡献**: 上下文感知的恶意指令检测——结合上下文判断指令是否为注入
- **开源代码**: 未明确
- **实测数据**: 是

---

## 五、Agent 权限/访问控制（4 篇）

### 25. Twin Agent: Context Residual Compression for Privilege Separated Agents
- **arXiv**: 2607.19595
- **作者/机构**: Zhanhao Hu, Dennis Jacob, Xiao Huang, Zhaorun Chen, **Bo Li, David Wagner**（UC Berkeley / UIUC）
- **时间**: 2026-07-21
- **核心贡献**: 通过上下文残差压缩改进特权分离 Agent 架构——在不损失效用前提下隔离不可信观察与特权执行
- **开源代码**: 未明确
- **实测数据**: 是

### 26. APPA: Agentic Permissions Policy Algebra for Taint Confinement in LLM Agents
- **arXiv**: 2607.24625
- **作者/机构**: Arseny Kravchenko, Vadim Liventsev 等
- **时间**: 2026-07-27
- **核心贡献**: 提出权限策略代数（APPA），通过动态信息流控制解决传统 taint tracking 过度限制的问题
- **开源代码**: 未明确
- **实测数据**: 是

### 27. Dynamic Capability Scoping for Enterprise AI Agents
- **arXiv**: 2607.22445
- **作者/机构**: Halil Burak Noyan
- **时间**: 2026-07-24
- **核心贡献**: 企业 Agent 的动态最小权限方案——按任务按需发放凭证，消除静态持久过度授权
- **开源代码**: 未明确
- **实测数据**: 是（含合成数据集）

### 28. Hardware Keystores for AI Agent Signing Workflows: A Zero-Trust MCP Enforcement Architecture
- **arXiv**: 2608.06130
- **作者/机构**: Leo Sambrook, Sampo Sovio
- **时间**: 2026-08-06
- **核心贡献**: 用硬件密钥库实现零信任 MCP 执行架构——保护 Agent 的签名/认证/证书操作私钥
- **开源代码**: 未明确
- **实测数据**: 是

---

## 六、Agent 安全基准测试/红队框架（5 篇）

### 29. HarnessSafe: Evaluating Safety Across Persistent Carriers in Agent Harnesses
- **arXiv**: 2608.06984
- **作者/机构**: Xiao Zhang, Yusheng Wang, **Yuhao Fei** 等
- **时间**: 2026-08-07
- **核心贡献**: 首个评估 Agent Harness 中跨持久载体（memory/skills/tools/artifacts）安全风险的端到端基准
- **开源代码**: 未明确
- **实测数据**: 是（21 页，3 图）

### 30. AI-Infra-Guard: A Unified Framework for Multi-Layer Agent Red Teaming
- **arXiv**: 2606.31227
- **作者/机构**: Yong Yang, Xing Zheng 等
- **时间**: 2026-06-30
- **核心贡献**: 开源分层红队框架——覆盖模型服务引擎、Agent 平台、MCP 生态和语言模型的全栈攻击面
- **开源代码**: **是**（AI-Infra-Guard）
- **实测数据**: 是

### 31. SkillSec-Eval: Agent Skill Security - Threat Models, Attacks, Defenses, and Evaluation
- **arXiv**: 2607.13987
- **作者/机构**: Sanket Badhe, Priyanka Tiwari
- **时间**: 2026-07-15
- **核心贡献**: 针对 Agent 技能全生命周期安全的威胁模型+攻击+防御+评估框架
- **开源代码**: 未明确
- **实测数据**: 是

### 32. SkillGate / Risk Assessment of Malicious Skill Files in Coding Agents
- **arXiv**: 2607.25619 / 2608.05223
- **作者/机构**: Rui Yang, Michael Fu, **Kla Tantithamthavorn**, Chetan Arora, Joey Chua（Monash University）
- **时间**: 2026-07-28 / 2026-08-05
- **核心贡献**: 针对编码 Agent（Cursor/Claude Code/Copilot）中恶意 skill 文件的运行时检测方案+风险评估
- **开源代码**: 未明确
- **实测数据**: 是（29 页，6 图，6 表）

### 33. The Chronos Vulnerability: A Taxonomy of Temporal Persistence and Memory-Based Deception in Agentic AI
- **arXiv**: 2607.19433
- **作者/机构**: Om Narayan, Ramkinker Singh, Praveen Baskar
- **时间**: 2026-07-20
- **核心贡献**: 对从无状态到有状态 Agent 的架构演进带来的时间持久化和基于内存欺骗的安全威胁的分类法
- **开源代码**: 未明确
- **实测数据**: 是

---

## 七、多 Agent 攻击/防御（2 篇）

### 34. When Coordination Becomes a Threat: Communication Attacks in LLM-Controlled Multi-Robot Systems
- **arXiv**: 2608.06830
- **作者/机构**: Zhen Huang 等（国防科大）
- **时间**: 2026-08-07
- **核心贡献**: 针对多机器人系统中 LLM 规划层的通信攻击——利用 Agent 间协调机制注入恶意指令
- **开源代码**: 未明确
- **实测数据**: 是

### 35. Early Detection of Distributed Backdoors in Multi-Agent LLM Systems
- **arXiv**: 2607.24893
- **作者/机构**: Diego Fernandez Arias, Dev Prashant Mistry, Ren Wang, Yibo Hu
- **时间**: 2026-07-27
- **核心贡献**: 发现多 Agent 系统中的分布式后门——加密碎片分散到多个 Agent，任何单个 Agent 都不持有完整 payload
- **开源代码**: 未明确
- **实测数据**: 是

---

## 八、其他高价值论文

### 36. SoK: How Frontier AI Reshapes System-Level Security Risk Dynamics in Critical Infrastructure
- **arXiv**: 2608.04033
- **时间**: 2026-08-03
- **核心贡献**: 前沿 AI（含 Agentic 系统）如何重塑关键基础设施系统级安全风险动态的系统性综述

### 37. ToolGuardian: Declarative Security for AI Agent-Tool Interactions
- **arXiv**: 2607.21835
- **时间**: 2026-07-23
- **核心贡献**: 声明式 Agent-工具交互安全框架——确定性的、可审计的安全策略执行

### 38. Data Leakage Prevention in Agentic Applications via Preemptive Hardening
- **arXiv**: 2607.18847
- **作者/机构**: Akansha Shukla 等（**Yuval Elovici, Asaf Shabtai** — BGU 以色列本古里安大学）
- **时间**: 2026-07-21
- **核心贡献**: 预部署加固方案——在多 Agent 系统中预防数据泄露和工具误用

### 39. PromptShield Home: Ambient Multimodal Prompt Injection Defense for Smart-Home Agents
- **arXiv**: 2608.05495
- **时间**: 2026-08-06
- **核心贡献**: 智能家居场景下区分真实用户指令与环境噪声（电视语音/屏幕文字/对话）的防御方案

### 40. Protocol-Level Attacks on Agentic Commerce Platforms: AIP-Bench and Unified Defense
- **arXiv**: 2607.21824
- **时间**: 2026-07-23
- **核心贡献**: 揭示 Agent 商务平台的协议层攻击面（而非 AI 模型层），含跨平台分类法和 AIP-Bench 基准

---

## 九、高价值开源项目（GitHub）

| 项目 | Stars | 核心定位 |
|------|-------|---------|
| **nolabs-ai/nono** | 3,560 | 零配置 Agent 沙箱，秒级隔离 |
| **perplexityai/numbat** | 859 | 端点 AI Agent 活动监控+检测+取证 |
| **stacklok/toolhive** | 1,996 | 企业级 MCP 服务器管理平台 |
| **luckyPipewrench/pipelock** | 792 | AI Agent 防火墙（MCP/HTTP/A2A/WebSocket 流量扫描） |
| **emiliaprotocol/emilia-protocol** | 810 | 机器操作后果防火墙——在执行前验证权限 |
| **afshinm/zerobox** | 698 | 基于 Codex 运行时的轻量级进程沙箱 |
| **secureagentics/Adrian** | 520 | 开源 runtime AI Agent 安全监控工具 |
| **hashgraph-online/hol-guard** | 430 | AI Agent 防病毒——拦截恶意工具/prompt injection/MCP 服务器 |
| **Agent-Threat-Rule/agent-threat-rules** | 366 | AI Agent 安全威胁检测规则标准（已合并入微软） |
| **confident-ai/deepteam** | 2,405 | LLM/AI Agent 红队测试框架 |
| **msoedov/agentic_security** | 1,958 | Agent LLM 漏洞扫描器 / AI 红队工具包 |
| **webpro255/awesome-ai-agent-attacks** | 61 | AI Agent 安全事件时间线（2024-2026，含来源和日期） |
| **agentbaseline/agentbaseline** | 19 | 企业运行 AI Agent 需达成的 6 项安全控制基线 |

---

## 总结

**搜索覆盖**: arXiv cs.CR 类别 10+ 关键词组合，GitHub 3 个主题，Semantic Scholar 交叉验证。

**关键发现**:
1. **MCP 安全**是 2026 年最热门方向——复旦团队（2607.11086/2607.14754）产出最系统，含大规模实证研究
2. **自进化 Agent 的 skill/experience poisoning** 是全新攻击面（SkillJack 2608.03509、PoisonedEvolution 2608.05563、Benign Alone 2608.01759 三篇同期论文）
3. **持久化攻击**从 memory poisoning 扩展到 skill backdoors、trajectory poisoning、distributed backdoors
4. **防御方面**: 权限分离（Twin Agent/Berkeley）、免疫式学习（AgentAntibody）、多阶段防御（S³）均有突破
5. 几乎所有论文均发布于 2026 年 7-8 月（近 1-2 个月），引用数均为 0——该领域正处于爆发期
6. **开源生态活跃**: nono（3.5k star 沙箱）、pipelock（Agent 防火墙）、Agent-Threat-Rule（已被微软采纳）值得关注