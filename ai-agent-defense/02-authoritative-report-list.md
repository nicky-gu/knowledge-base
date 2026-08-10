# 2025–2026 权威机构「AI Agent 安全」研究报告/测评报告清单

> 调研时间：2026-08-07。重点覆盖终端侧/企业侧 AI Agent（Claude Code、Cursor、Copilot 等 coding agent）与 MCP 生态。
> 标注说明：【已验证】= 本次调研中实际访问并确认了页面/日期；【待核实】= 调研环境（国内网络，多数国际站点/搜索引擎被反爬封锁）无法直连确认，信息来自既有知识库，引用前请自行点开核对。

---

## 一、标准组织 / 政府机构（合规引用首选）

### 1. NIST（美国国家标准与技术研究院）
| 报告 | 时间 | 链接 | 状态 |
|---|---|---|---|
| AI Risk Management Framework (AI RMF 1.0) + **Generative AI Profile（NIST AI 600-1，生成式AI风险画像）** | RMF 2023-01；GenAI Profile 2024-07 | https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence | 【已验证】免费 |
| **NIST AI 100-2e2025**《Adversarial Machine Learning: A Taxonomy and Terminology of Attacks and Mitigations》（2025 修订版） | 2025 | https://csrc.nist.gov/pubs/ai/100/2/e2025/final | 【已验证】免费 |
| **AI Agent Standards Initiative（AI 智能体标准倡议）** — NIST CAISI 发起，目标是"让自主行动的 AI agent 可安全互操作地被广泛采用" | 宣布 2026-02-17 | https://www.nist.gov/artificial-intelligence/ai-agent-standards-initiative | 【已验证】免费 |
| **CAISI RFI: Securing AI Agent Systems（关于保护 AI Agent 系统的信息征询）** | 2026-01-12 | https://www.nist.gov/news-events/news/2026/01/caisi-issues-request-information-about-securing-ai-agent-systems | 【已验证】 |
| CAISI 技术博客系列：Strengthening AI Agent Hijacking Evaluations（2025-01）、Cheating on AI Agent Evaluations（2025-12）、Insights into AI Agent Security from a Large-Scale Red-Teaming Competition（2026-03） | 2025–2026 | https://www.nist.gov/blogs/caisi-research-blog | 【已验证】免费 |

- 一句话：NIST 尚无一本独立的"Agentic AI 安全标准"，但 2026 年已通过 CAISI 把 agent 安全（劫持评测、标准制定）列为专项工作；AI RMF + GenAI Profile 仍是合规引用基线。
- 权威性：**最高级**——写安全方案/合规文件引用 NIST AI RMF、NIST AI 600-1 是"引用即有效"。

### 2. MITRE ATLAS（AI 威胁矩阵）
- **MITRE ATLAS**（Adversarial Threat Landscape for AI Systems）— 持续更新的 AI 对抗威胁知识库（ATT&CK 的 AI 对应物），近年已加入生成式 AI / 智能体相关技术条目与案例库。截至调研时**未发现独立的 "Agentic AI 专项报告"**，agent 相关威胁以技术/案例条目形式并入矩阵。
- 链接：https://atlas.mitre.org ｜【已验证站点存活，具体条目待核实】免费
- 权威性：**高**——威胁建模、红队方案中引用 ATLAS 技术编号（AML.Txxxx）是行业惯例。

### 3. OWASP GenAI Security Project（对 coding agent/MCP 最对口）
| 报告 | 时间 | 链接 | 状态 |
|---|---|---|---|
| **OWASP Top 10 for LLM Applications（2025 版 / 2026 版）** | 2025 版 2024-11 发布；2026 版 2026-06-01 | https://genai.owasp.org/llm-top-10/ | 【已验证】免费 |
| **Agentic AI – Threats and Mitigations**（威胁建模式参考，Agentic Security Initiative 系列首篇） | 2025-02-17 | https://genai.owasp.org/resource/agentic-ai-threats-and-mitigations/ | 【已验证】免费 |
| **OWASP Top 10 for Agentic Applications（2026）** — 全球同行评审的 agentic AI 关键风险清单 | 2025 底–2026 | https://genai.owasp.org/agentic-security/ | 【已验证】免费 |
| **State of Agentic AI Security and Governance 2.01** | 2026-05-25 | 同上 | 【已验证】免费 |
| **A Practical Guide for Secure MCP Server Development** + 第三方 MCP Server 安全使用 Cheat Sheet | 2026 | 同上 | 【已验证】免费 |
| AI Security Solutions Landscape for Agentic AI（Q2 2026）— agentic AI 安全厂商全景 | 2026 | 同上 | 【已验证】免费 |

- 权威性：**企业应用安全场景"引用即有效"**（与 OWASP Top 10 同级别的行业默认基线）；MCP 安全两份指南是当前最对口的公开权威实践。

### 4. ENISA（欧盟）
- **Multilayer Framework for Good Cybersecurity Practices for AI**（2023-06，窗口外但仍是 EU 官方基线）https://www.enisa.europa.eu/publications/multilayer-framework-for-good-cybersecurity-practices-for-ai 【已验证】免费
- ENISA Threat Landscape 年度报告持续覆盖 AI 威胁；**2025–2026 年 agentic 专项报告未能验证**【待核实】。
- 权威性：欧盟合规（NIS2、AI Act 配套）场景引用有效。

### 5. 英国 AISI（AI Security Institute）与国际 AI 安全报告
| 报告 | 时间 | 链接 | 状态 |
|---|---|---|---|
| **International AI Safety Report 2025 / 2026**（Yoshua Bengio 牵头、30+ 国家支持、100+ 专家撰写，含 agent 能力/风险章节） | 2025-01 / 2026-02-03 | https://internationalaisafetyreport.org | 【已验证】免费 |
| **AISI Frontier AI Trends Report (2025)** | 2025-12-18 | https://www.aisi.gov.uk/publications | 【已验证】免费 |
| **How are AI agents used? Evidence from 177,000 MCP tools**（MCP 生态实测） | 2026-03-26 | 同上 | 【已验证】免费 |
| Measuring AI Agents' Progress on Multi-Step Cyber Attack Scenarios | 2026-03-16 | 同上 | 【已验证】免费 |
| Breaking agent backbones: Evaluating the security of backbone LLMs in AI agents | 2025-10 | 同上 | 【已验证】免费 |

- 权威性：政府间背书，政策/合规引用有效；AISI 的 MCP 实测论文对"MCP 生态安全现状"论证非常直接。

### 6. CISA / NSA（美国）联合指南
- **AI Data Security: Best Practices for Securing Data Used to Train & Operate AI Systems**（CISA+NSA+FBI 及澳新英伙伴联合发布，2025-05）https://www.cisa.gov/resources-tools/resources/ai-data-security 【页面存在但被反爬，待核实】免费
- 另：Deploying AI Systems Securely（2024-04 联合指南）仍是基线。权威性：美国关基/政府承包商场景引用有效。

### 7. 中国（调研环境无法访问国内站点验证，以下均需核实）
- **全国网络安全标准化技术委员会（TC260）《人工智能安全治理框架》1.0（2024-09）/ 2.0（2025-09）** — 国内 AI 安全治理的权威框架文件【待核实，建议在 tc260.org.cn 核对】
- **中国信通院（CAICT）**：2025 年起发布多份智能体/大模型安全相关报告与评测（如《智能体发展报告》、大模型安全基准评测等），泰尔实验室亦开展 AI 终端/智能体安全测评【待核实，www.caict.ac.cn「白皮书」栏目】
- 权威性：国内合规场景（等保、关基、行业监管汇报）引用 TC260/信通院文件有效性最高；但具体报告名与链接请务必核实后再引用。

---

## 二、权威咨询/测评机构（付费墙为主，采购场景引用多）

| 机构 | 报告/资产 | 时间 | 链接 | 免费? |
|---|---|---|---|---|
| Gartner | **Top Strategic Technology Trends 2025：Agentic AI 列首位** | 2024-10 | gartner.com/en/newsroom 【待核实】 | 摘要免费 |
| Gartner | **Predicts Over 40% of Agentic AI Projects Will Be Canceled by End of 2027**（新闻稿） | 2025-06-25 | https://www.gartner.com/en/newsroom/press-releases/2025-06-25-gartner-predicts-over-40-percent-of-agentic-ai-projects-will-be-canceled-by-end-of-2027 【链接模式已确认，内容待核实】 | 新闻稿免费 |
| Gartner | **AI TRiSM（AI 信任、风险与安全管理）** 系列研究 + "How to Secure and Govern AI Agents" 类报告 | 2025–2026 | gartner.com（付费墙）【待核实】 | 付费 |
| Forrester | AI Security Solutions Landscape / Wave（AI 安全厂商测评） | 2025–2026 | forrester.com（付费墙）【待核实，具体标题/季度请核实】 | 付费 |
| IDC / Frost & Sullivan | AI 安全/治理市场份额与预测报告 | 2025–2026 | 付费墙【待核实】 | 付费 |

- 权威性评价：Gartner/Forrester 是**企业采购决策**中引用率最高的（"Gartner 预测 agentic AI…"常出现在董事会汇报里）；但技术细节不如 OWASP/NIST，且核心报告付费。合规场景引用 Gartner 新闻稿（免费）即可。

---

## 三、云安全/安全厂商权威报告

| 机构 | 报告 | 时间 | 链接 | 状态/免费 |
|---|---|---|---|---|
| **Palo Alto Unit 42** | **AI Agents Are Here. So Are the Threats.**（CrewAI/AutoGen 双框架 9 类攻击实测：信息泄露、凭据窃取、工具滥用、RCE） | 2025-05-01 | https://unit42.paloaltonetworks.com/agentic-ai-threats/ | 【已验证】免费 |
| **Microsoft** | **Microsoft Digital Defense Report 2025**（含 AI/agentic AI 威胁章节） | 2025-10 | microsoft.com security-insider（官网路径有变动，搜索 "Microsoft Digital Defense Report 2025"）【待核实】 | 免费 |
| Microsoft | "Securing AI agents" 系列博客（Defender for AI agents、Entra Agent ID 等） | 2025–2026 | microsoft.com/security/blog【待核实】 | 免费 |
| **Google Cloud / Mandiant** | "Google's approach for secure AI agents"（SAIF 框架向 agent 延伸的指引，2025 年中）+ M-Trends 年度报告 AI 章节 | 2025–2026 | cloud.google.com/blog【待核实，本环境 google 域名不可达】 | 免费 |
| **Cloud Security Alliance (CSA)** | Agentic AI 安全工作组/威胁建模出版物（CSA 2025 年启动 agentic AI 安全工作） | 2025–2026 | cloudsecurityalliance.org【待核实，Cloudflare 拦截】 | 免费（注册） |
| **Wiz** | State of AI in the Cloud 年度研究（云环境 AI 采用率/风险实测） | 2025 | wiz.io【待核实，具体 URL 未确认】 | 免费 |
| **HiddenLayer** | **AI Threat Landscape Report（年度）** + How to Secure Coding Agents / How Coding Agents Are Changing Application Risk（专题研究） | 2026 版已出 | https://hiddenlayer.com/innovation-hub/reports-and-guides | 【已验证】免费（注册） |
| **Zenity** | **The Ultimate Guide to Securing Coding Agents**（eBook，专门讲 Claude Code/Copilot 类 coding agent 的企业防护框架） | 2026 | https://zenity.io/resources/ | 【已验证】免费（注册） |
| **Lakera** | MCP/Agentic IDE 零点击 RCE 等专题研究（博客系列，如 "Zero-Click RCE: Exploiting MCP & Agentic IDEs"） | 2025–2026 | https://www.lakera.ai/blog | 【已验证】免费 |
| **IBM** | **Cost of a Data Breach Report 2025/2026**（含 AI 采用、shadow AI、AI 治理缺口与泄露成本关联数据） | 2025-07 / 2026 | https://www.ibm.com/reports/data-breach | 【已验证】免费（注册） |
| **OpenAI** | **A Practical Guide to Building Agents**（含 guardrails/安全章节，企业部署 agent 的官方实践） | 2025-04 | https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf | 【已验证】免费 |
| Anthropic | Claude Code 安全最佳实践（官方文档） | 持续更新 | https://docs.anthropic.com/en/docs/claude-code/security | 【待核实】免费 |
| MIT Technology Review Insights | agentic AI 商业/安全类赞助报告 | 2025–2026 | 【待核实，未确认具体报告】 | — |

- 权威性评价：厂商报告在**威胁情报与实测数据**上引用价值高（Unit 42、HiddenLayer、Lakera 的研究常被媒体/方案引用）；但属商业机构，合规文件里通常作为"佐证"而非"依据"。IBM 泄露成本报告是量化风险叙事的经典引用源。
- 注：任务中提到的 "Invisible AI" 未能定位到对应机构/报告（invisible.co 无此报告），可能是名称记忆偏差，建议用户提供线索。

---

## 四、学术综述（arXiv 2025–2026，高引用优先）

| 论文 | 作者 | 时间 | 引用数* | 链接 |
|---|---|---|---|---|
| **Model Context Protocol (MCP): Landscape, Security Threats, and Future Research Directions** | Hou, Zhao, Wang, Wang | 2025-03（v3） | **450** | https://arxiv.org/abs/2503.23278 |
| **MCP Safety Audit: LLMs with the Model Context Protocol Allow Major Security Exploits** | Radosevich, Halloran | 2025-04 | **98** | https://arxiv.org/abs/2504.03767 |
| **The Attack and Defense Landscape of Agentic AI: A Comprehensive Survey** | Kim, Liu, …, **Wenbo Guo, Dawn Song** | 2026-03 | 新 | https://arxiv.org/abs/2603.11088 |
| **Systematization of Knowledge: Security and Safety in the Model Context Protocol Ecosystem** | Gaire et al. | 2025-12 | 新 | https://arxiv.org/abs/2512.08290 |
| **Towards Trustworthy Agentic AI: A Comprehensive Survey of Safety, Robustness, Privacy, and System Security** | Qi, Li, …, King, Xu | 2026-05 | 新 | https://arxiv.org/abs/2605.23989 |
| MCP Security Bench (MSB): Benchmarking Attacks Against MCP in LLM Agents | — | 2025-10 | 34 | https://arxiv.org/abs/2510.15994 |
| Beyond the Protocol: Unveiling Attack Vectors in the MCP Ecosystem | — | 2025-06 | — | https://arxiv.org/abs/2506.02040 |
| MCPSecBench: A Systematic Security Benchmark and Playground for MCP | — | 2025-08 | — | https://arxiv.org/abs/2508.13220 |
| A Measurement Study of Model Context Protocol Ecosystem | — | 2025-09 | — | https://arxiv.org/abs/2509.25292 |
| Enterprise-Grade Security for MCP: Frameworks and Mitigation Strategies | — | 2025-04 | — | https://arxiv.org/abs/2504.08623 |
| AI Agents Under Threat: A Survey of Key Security Challenges and Future Pathways | — | 2024-06（持续更新） | — | https://arxiv.org/abs/2406.02630 |

\* Semantic Scholar 引用数（2026-08-07 查询；2025 底后的新论文尚未被收录）。
- 权威性评价：学术论文在合规文件中一般作为"技术佐证"；其中 Hou et al.（450 引）已是 MCP 安全领域的事实标准综述，写 MCP 安全方案时引用最合适。注意用户提到的 "Guo et al. MCP systematic analysis" 更可能是 Kim/Guo/Song 的 2603.11088（agentic AI 攻防全景）或 Gaire et al. 的 SoK（2512.08290）。

---

## 五、结论：企业安全合规场景「引用即有效」清单（按效力排序）

**第一梯队（监管/审计/标准依据）**
1. NIST AI RMF + NIST AI 600-1（GenAI Profile）——合规基线
2. NIST CAISI AI Agent Standards Initiative / Securing AI Agent Systems RFI（2026，agent 专项政策信号）
3. OWASP Top 10 for LLM Applications + **OWASP Top 10 for Agentic Applications** + MCP 安全指南——应用安全事实标准
4. MITRE ATLAS——威胁建模技术引用
5. International AI Safety Report 2025/2026（Bengio，30+ 国背书）——国际政策级
6. TC260《人工智能安全治理框架》/ 信通院报告——国内合规场景（引用前核实版本）

**第二梯队（行业共识/采购汇报）**
7. Gartner 新闻稿（agentic AI 预测、AI TRiSM）、Forrester Landscape/Wave
8. IBM Cost of a Data Breach（AI 风险量化）
9. ENISA / CISA-NSA 联合指南（区域性合规）

**第三梯队（技术佐证/威胁情报）**
10. Unit 42、HiddenLayer、Zenity、Lakera、Microsoft/Google 安全研究
11. arXiv 高引综述（Hou et al. MCP 450 引等）
12. UK AISI 评测报告（MCP 生态实测、agent 网络攻击能力测量）

**与"终端侧 coding agent + MCP 生态"最对口的 6 份（建议优先精读）：**
1. OWASP Top 10 for Agentic Applications + MCP Server 安全开发指南（genai.owasp.org/agentic-security）
2. Zenity《The Ultimate Guide to Securing Coding Agents》
3. HiddenLayer《How to Secure Coding Agents》/ AI Threat Landscape Report
4. Unit 42《AI Agents Are Here. So Are the Threats.》
5. UK AISI《How are AI agents used? Evidence from 177,000 MCP tools》
6. Hou et al.《MCP: Landscape, Security Threats, and Future Research Directions》（arXiv 2503.23278）
