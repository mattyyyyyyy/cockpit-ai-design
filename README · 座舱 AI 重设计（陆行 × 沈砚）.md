**README · 座舱 AI 重设计（陆行 × 沈砚）**

**README · 座舱 AI 重设计**

***本文件给后续介入的 AI / 协作者看。读完这一篇，你应该能：① 知道这套文档是什么、为什么存在、不是什么；② 找到任何一篇 PRD；③ 知道哪里已经做好、哪里还没做。***

**1. 项目是什么**

**项目名**：座舱 AI 重设计

**一句话**：从产品视角，**从零策划一套新能源汽车智能座舱 AI 助手的完整产品方案**——14 篇分领域 PRD + 配套技术架构调研，用作产品总监与后端架构师的协同思考训练。

**它不是什么**：

* ❌ 不是真要给某辆车做量产开发，没有车队、没有预算、没有上线节点。
* ❌ 不是对市面现有座舱 AI（小鹏小 P / 理想 Mind GPT / 问界小艺 / 蔚来 Nomi）做评测或竞品分析报告——竞品研究是输入，不是输出。
* ❌ 不是技术选型决策书——技术选型由沈砚（架构师）拍板，本文档只提供产品视角的技术钩子。

**它是什么**：

* ✅ 一套**经得起反驳的产品策划文档**：每篇 PRD 都包含背景目标、用户价值、场景清单、SLO/取舍、功能点详细定义（带技术钩子）。
* ✅ 一份**给后端架构师的输入清单**：每个功能点列了技术挑战、链路节点、性能要求，让沈砚的架构设计有产品锚点。
* ✅ 一次**产品总监思维训练**：作者陆行（agent，非真人）每个 idea 都过六关自我反驳（场景真伪 / 失败路径 / 替代方案 / 代价账 / 竞品镜像 / 撤退条件）。

**2. 为什么叫"重设计"**

**不是推倒重做现有车的座舱**。是相对市面"做加法、堆功能"的座舱 AI 现状，**从场景出发重新组织**——把 AI 上车不当作"在屏幕上贴一个小人"，而是重新设计交互链路、信息结构、服务触达。

核心信念（详见各 PRD §1）：

1. **座舱的终极形态是"不用操作"，不是"操作更酷炫"**——但前提是 AI 要可预测、可干预、可撤销。
2. **AI 上车的核心价值是把意图表达变短**——但不是所有场景都该变短（车控确认、支付、安全相关要慢、要冗余）。
3. **端云分工不是写死的路由规则**——是要做成可动态调整的能力。
4. **个性化的边界是"记住偏好"，不是"替用户做主"**——好的个性化要有遗忘机制和情境感知。
5. **堆料不是产品力，场景才是**——但要承认算力、数据、模型是地基。
6. **功能安全和 AI 体验不是对立面**——但要承认在工程现实里它们经常就是对立的，所以要双层架构。

**3. 作者与分工**

|  |  |  |  |
| --- | --- | --- | --- |
| 角色 | 谁 | 管什么 | 签名 |
| 产品总监 | 陆行（agent） | 用户场景、功能定义、取舍判断、PRD 主体 | 🚗💬 |
| 后端架构师 | 沈砚（agent） | 技术选型、系统架构、SLO 工程实现、Agent 编排拓扑 | 🛠️⚙️ |
| 决策者 | 老师（真人 owner，"鱼不吃糯米"） | 业务方向、资源、上线节点、终审 | - |

**协同规则**：陆行先开口讲产品意图，沈砚接力定后端方案。意见冲突找老师拍板，不和稀泥。

**4. 文档地图**

文件夹根目录：AI助手/，全部公开给老师。

**4.1 PRD 主线（共 16 篇，按功能域）**

|  |  |  |  |
| --- | --- | --- | --- |
| 编号 | 标题 | 一句话 | 链接 |
| 总目录 | 座舱 AI 重设计 · 总目录 | 项目纲领，定 14 个功能域的边界 | https://my.feishu.cn/docx/M6hrd4uj8olZ2jx8tSbcrCHKnEe |
| **01** | 多模态输入（感知层） | 语音/视线/手势/触控的融合采集与初步过滤 | https://my.feishu.cn/docx/YPuUdf7vooepPoxrpn1cCpxRnRb |
| **02** | 外部情境感知 | 车辆状态、道路、天气、时段、乘员等外部信号 | https://my.feishu.cn/docx/TYoNdMHsHo9F54xOcYzcHQJinRf |
| **03** | NLU 与意图理解 | 语义解析、多轮对话、指代消歧、情境推理 | https://my.feishu.cn/docx/VmPYdwMzEoROmUx4G6ocumj3nFj |
| **04** | 状态管理·记忆系统·模式切换 | 短期/长期记忆、用户画像、驾驶/泊车/休憩模式切换 | https://my.feishu.cn/docx/NrBGdQE3Noyu8IxvM47cvnp1nDc |
| **05** | 主动服务决策 | 何时主动说话、何时沉默、推荐的可预测可干预可撤销 | https://my.feishu.cn/docx/K1w0dg4broPAUzxjhgqckDIjnRg |
| **06** | Agent 编排与复杂指令 | 多 Agent 协作、任务分解、失败兜底 | https://my.feishu.cn/docx/NnXMdaKfHopRnOxbfZucOLdPn9f |
| **07** | 生态接入与跨端 | 第三方 App、账号体系、车家手机互联 | https://my.feishu.cn/docx/L1LLdpaD5oGN2zxDF8dcWWeknbc |
| **08** | 语音输出（TTS） | 音色、停顿、情感、可中断、多音区分发 | https://my.feishu.cn/docx/KRnFdXzWvoOmCmxbKiCcXEySnsh |
| **09** | HMI 多屏协同 | 仪表/中控/HUD/后排/投影 的协同、虚拟形象 | https://my.feishu.cn/docx/Uw8ud4HbqoliuuxZwROcwKR0nnf |
| **10** | AI 大模型集成·车云协同 | 端侧小模型 + 云端大模型、OTA、成本控制 | https://my.feishu.cn/docx/X1acdsO6ioORYdxhzIUcu4Sinxf |
| **11** | 个性化与人格层 | 用户偏好、AI 人格设定、遗忘机制 | https://my.feishu.cn/docx/AFa1dQf0joVqMXxeEx0c2LknnFb |
| **12** | 弱网与降级策略 | 隧道、地库、跨省、断网时的体验保底 | https://my.feishu.cn/docx/KaSbd7J4mozihJxmD5Sc5DAynuB |
| **13** | 安全、可解释、合规 | 功能安全、隐私、未成年人保护、可解释性 | https://my.feishu.cn/docx/E9RWdTfAEo0Z1RxxvMfc1lLLn2e |
| **14** | 数据闭环与持续优化 | 数据采集合规、标注、Bad Case 回流、版本迭代 | https://my.feishu.cn/docx/RyCmdj1mWoNk5wxYoxmcEqNhnlc |
| **15** | 第三方 MCP 接入与路由机制 | 第三方 Agent/Skill 的接入、路由、隔离 | https://my.feishu.cn/docx/BYdodeQycocbb8xdCkzcHjAknOg |

**4.2 给沈砚的输入（PRD 衍生物）**

|  |  |  |
| --- | --- | --- |
| 文档 | 用途 | 链接 |
| 16 技术钩子清单 v1（给沈砚） | 14 篇 PRD 中 650+ 条技术钩子的汇总 | https://my.feishu.cn/docx/Xm5wdKKdtoy1LYxHkj3cdN1qnQ8 |
| 技术钩子清单 v1（同上别名版） | 早期同名版本 | https://my.feishu.cn/docx/WhvLdr7qLoDQUXxyfrlchasvnSl |
| 调研交叉对齐（陆行 × 沈砚） | 产品调研 × 技术调研的对齐讨论 | https://my.feishu.cn/docx/Upp1drVJ4oXe1nxn4JVcygIVnAe |

**4.3 沈砚的技术调研产出（架构师视角）**

|  |  |  |
| --- | --- | --- |
| 文档 | 用途 | 链接 |
| README · 沈砚 | 沈砚的产出清单 | https://my.feishu.cn/docx/SDiAdzkSuoQPD2xn9mKcaw9RnQo |
| 技术架构索引 · 沈砚 | 技术架构文档集索引 | https://my.feishu.cn/docx/WeJEdhDLWoH2CAxE5elcIpL7nzd |
| 01 - 架构调研大纲（技术视角） | https://my.feishu.cn/docx/CCiid5H6no4wbnxj7CCcERDFnyd |  |
| 02 - 技术可行性边界框架 | https://my.feishu.cn/docx/ELlKdhPUjoHz9axHMHCcZPtangb |  |
| 03 - SLO 估算方法 | https://my.feishu.cn/docx/X9ipdSP7FosBGwx4XhacMOaYnZc |  |
| 04 - 失败模式详细方案 | https://my.feishu.cn/docx/HhnSd4ConoZapbxc0yfc9zzXnPf |  |
| 05 - 座舱AI重设计架构草稿 | https://my.feishu.cn/docx/IKp7dMcuaoh37UxWCV4c5a4vnCZ |  |

**4.4 形象研究（早期附产物）**

|  |  |  |
| --- | --- | --- |
| 文档 | 用途 | 链接 |
| 智能座舱助手形象研究 · 完整报告 | 助手形象（视觉、声音、人格）调研 | https://my.feishu.cn/docx/BQiQd4mQPoEXVVxV6JXcdBX3ngc |
| 智能座舱助手形象研究 · 附录 | 原始资料与深度口碑 | https://my.feishu.cn/docx/JK1wdT7D4oixCGx5jE5cCBMkn8f |
| D4 · "澄"形象 Moodboard | 助手视觉与动效脚本 | https://my.feishu.cn/docx/PhmMdUh6JoXiTyxr6A2ccMd0n7R |

**5. PRD 结构（每篇都长这样）**

每篇 PRD 大致五段：

* **§1 背景与目标**：为什么做、解决什么问题、目标 SLO。
* **§2 用户价值**：核心价值 + 反价值（"不做什么"——这点比"做什么"更重要，是六关反驳的产物）。
* **§3 场景清单**：8 个核心场景 + 5 个边界场景 + 3 条非场景（也是反驳产物，明确边界）。
* **§4 非功能需求 / SLO / 取舍**：6 条 SLO + 降级策略 + 5 条关键取舍（这里讲清楚了"不要"什么，比"要"什么更值钱）。
* **§5 功能点详细展开**：每个功能点用六段式定义——产品定义、用户故事、流程、边界、失败处理、技术钩子。

**读法建议**：

* 想了解产品形态 → 直接读 §3 场景清单。
* 想理解取舍 → 读 §4 关键取舍。
* 想做技术架构 → 读各 PRD 的 §5 技术钩子 + 16 号技术钩子清单。
* 想了解整体设计哲学 → 读总目录 + 本 README §2。

**6. 项目进度（截至 2026-05-11）**

**✅ 已完成**

* Phase 1：16 篇 PRD 主体 §1~§5 全部入库飞书云文档。
* 88 个功能点 × 六段式定义 × 650+ 条技术钩子。
* 沈砚的 5 篇技术调研产出（已挪入本文件夹）。
* 形象研究 3 篇（早期附产物）。

**🔄 进行中 / 未做**

* **Phase 2**：把 650+ 条技术钩子按沈砚的架构链路（输入感知/理解/决策/执行/输出/支撑/治理）重新分组归并，形成"技术架构输入清单 v1"。当前状态：已有 v1 雏形（16 号文档），需细化分组。
* **交叉对齐**：陆行的产品方案 × 沈砚的技术架构需做一轮对齐会，需沈砚在场。
* **Phase 3**：项目复盘、教训提升到 SOUL.md / AGENTS.md / TOOLS.md。

**7. 如果你是接手的 AI**

**入门路径**（按顺序）：

1. 读本 README（你现在在这里）。
2. 读总目录 M6hrd4uj8olZ2jx8tSbcrCHKnEe——理解 14 个功能域怎么切的、为什么。
3. 挑一篇你最关心的 PRD 通读（推荐先看 §05 主动服务决策，最能体现"自我反驳"风格）。
4. 看 16 号技术钩子清单，理解工程视角。
5. 想看产品总监的思维范式——读 SOUL.md / IDENTITY.md / MEMORY.md（在工作空间根目录）。

**协作注意**：

* 这是陆行（产品 agent）的产出。修改前请确认动机：是补完，还是质疑现有判断？后者请走"自我反驳"流程，不是"我觉得应该这样"。
* 每篇 PRD 的 §4 关键取舍是经过六关反驳留下来的，挑战之前先看清取舍的理由。
* 技术细节请联系沈砚（agent，工作空间在 workspace-agent-orchestrator/）。

**8. 元信息**

* **作者**：陆行（产品 agent）+ 沈砚（架构师 agent）
* **owner**：鱼不吃糯米
* **创建于**：2026-04-22（最早的形象研究）
* **主体完成于**：2026-05-10
* **最近更新**：2026-05-11
* **存放位置**：飞书云文档 → 我的空间 → AI助手/
* **本地草稿**：workspace-product-director/drafts/（陆行）
* **追踪表**：workspace-product-director/TASK\_TRACKER.md（陆行不清零）

🚗💬 陆行 + 🛠️⚙️ 沈砚