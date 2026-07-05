# WorkBuddy 专家团 Skill 包（开源版）

> **使用提示**：本仓库所含 skill 文件**均由用户在 WorkBuddy 平台官方渠道、通过自己个人账号、以普通对话方式生成**。未使用破解安装包 / 获取应用文件夹内文件 / 反编译 / 抓包 / 模型 API 调用数据逆向等技术手段。不保证与 WorkBuddy 原版 100% 一致（平台侧可能更新，生成结果受 prompt / 模型版本影响）。

---

## 1. 项目简介

本仓库存档 WorkBuddy 平台（一个 AI 协作专家 agent 市场）的**团队协作型 skill** —— 每个 folder 对应一个"专家团"（多角色协作的 agent 集合），包含一个主理人 + 多个专业角色，工作流化地完成特定场景任务（投资研究 / 视频制作 / MVP 开发 / 财税 / 法务 / 营销 / 设计 / 法律 / 数据分析 等）。

Skill 内容主要由两类来源组装而成：
- **WorkBuddy 官方团队**（在 WorkBuddy 账号标记为 "WorkBuddy 团队"）
- **特邀作者 / 合作方**（Easychen / 卡尔的AI沃茨 / 花叔 (Alchain) / 苍何 / 杜哥学量化 / 百望股份 / vincentlli / Excellent / AI科学局 / Xu Qingchu 等）

每个 skill 在导入 orchestration 框架（OpenAI Custom GPTs / Claude Project / Coze / Dify / MetaGPT / AutoGen / CrewAI 等）时相当于一份长 system prompt，可以整体调度主理人 → 使用子 agent 调用成员，完成复杂的多阶段协作。

---

## 2. 授权 / 免责声明

### 2.1 授权形式

代码 / 文档部分采用 **MIT 许可证**（详见 `LICENSE` 文件）。

### 2.2 数据来源与合规声明

1. **生成方式透明**。所有 skill 文件均由用户在 WorkBuddy 平台官方渠道、通过自己的个人账号、以普通对话方式生成。未使用破解安装包、未获取应用文件夹内文件、未反编译、未抓包、未基于模型 API 调用数据逆向等任何技术手段。
2. **不保证一致性**。skill 内容在不同时间 / 不同 prompt / 不同模型版本下可能会有细微差异，因此**不保证与 WorkBuddy 原版 100% 一致**。如你依赖其中任何信息（法条、财税规则、投资建议、医疗/安全关键内容），请务必自行核实。
3. **数据与合规**。生成素材来自：合法的 WorkBuddy 平台调用输出、领域合规文档、公开语料。用户对自己在本仓下载 / 使用的内容负全部责任。
4. **第三方 attribution**。部分 skill 直接复用了下列开源 / 特邀作者的方法论或文档，版权与归属仍属原作者：
   - *一人企业方法论（One Person Company）*：Easychen — <https://github.com/easychen/opc-methodology>
   - *AST-based Humanize PPT*（MIT License）：LearnPrompt 团队 — <https://github.com/LearnPrompt/humanize-ppt>
   - *腾讯自选股股票投研系列*：作者 `jensonli@tencent.com`
   - "刺桐说 Pro" 投资社群系列：杜哥学量化
   - "卡尔的人感 PPT" 系列：卡尔的AI沃茨
   - "AI 视频创作 / 视频解剖" 系列：苍何
   - "花叔数据分析" 系列：花叔 (Alchain)
   - "智能发票" 系列：百望股份
   - "Makers 开发" 系列：vincentlli
   - "MVP 开发" 系列：Excellent
   - "NCRE 等级考试" 系列：Xu Qingchu
   - "KET 备考" 系列：AI科学局

如你为原始作者且希望修改或移除相关内容，请开 Issue — 我们会在 5 个工作日内响应。

---

## 3. 分类索引

> 📖 **阅读建议**：找到你关心的类别 → 点开对应目录 → 优先看 `README.md`（没有 README 的以 `SKILL.md` 或主理人 `*-team-lead.md` 为准）。
> 一个 skill 可能出现在多个类别（如 `seo-content-skills` 同时属于"内容营销"与"SEO"），下表按主类别只列一次，在"复用视角"段指出跨域协作。

### 3.1 投资分析 📈 (6 个专家团 / ~50+ 位专家)

| 新目录 | 简介 | 专家数（主理人 + 成员） |
|--------|------|------------------------|
| `investment-masters-skills` | AI 式对冲基金圆桌 — 13 位传奇投资哲学家 + 6 位分析师 + 2 位管理人（投资组合经理 + 风控师），参考巴菲特 / 芒格 / 费雪 / 邓普顿 / 达利欧 / ・拉什・库马尔等 | 21 |
| `a-share-skills` | A 股全链路研究：宏观策略 → 产业映射 → 资金追踪 → 个股深度 → 估值 → 风险诊断 → 投顾 | 8 |
| `stock-partner-skills` | 腾讯自选股实战派：产业策略 / 信号捕捉 / 估值 / 抄底 / 基本面 / 短线，6 大真实炒股视角 | 7 |
| `trading-agent-skills` | 多空辩论式投研：技术面 / 基本面 / 新闻 / 情绪 / 多空研究员 / 研究总监 / 交易员 / 三方风险 | 13 |
| `citongshuopro-skills` | 刺桐说 Pro 投资社群：主理人调度 4 位社群嘉宾（Gy / 贾总 / 小星 / 张老师） | 4 |
| `super-partner-skills` | 福帮手超级合伙人：入口路由 → 公司下一步 / 天才合伙人 / 多维度协同工作坊 / 服务跟进 / 乐包商业化 | 11 |

### 3.2 变现 / 商业化 💰 (专家团复用)

| 新目录 | 复用场景 |
|--------|---------|
| `content-monetization-skills` | CPS 带货 / CPE·CPM 效果广告 / 创作者 ↔ 品牌交易撮合 / BD — 5 人商业化闭环 |
| `super-partner-skills` | 商业化落地：乐包激活与能力继续（Lebao），把能力调用转成商业计划 |
| `a-share-skills` / `stock-partner-skills` | A 股 / 投研内容→ 个人 IP 素材 |
| `investment-masters-skills` | 大师方法论（dhandho-master 等）→ 付费课程 / 知识产品 |

### 3.3 内容创作 / 营销 📣 (10 个专家团 / ~55+ 位专家)

| 新目录 | 简介 | 专家数 |
|--------|------|--------|
| `ai-content-creator-skills` | 多模态内容生产：创意策略 / 文案 / 影像生成 / 精修合成 / 素材改编 / AI 视频 | 7+ |
| `video-gen-skills` | AI 短视频团队：采集（灵阅）→ 策划脚本（灵枢）→ 渲染 MP4（灵映）+ 引用素材库 | 5 |
| `promo-creator-skills` | 产品宣传片：创意简报 → 逐镜头分镜 → 素材生产 → HyperFrames 剪辑 → BGM → 交付 | 6 |
| `content-distribution-skills` | 跨 13+ 平台多平台分发（含微信视频号、小红书）| 5 |
| `marketing-campaign-skills` | 营销战役：内容创作 / 活动策划 / SEO / 品牌分析 — 4 人全生命周期 | 4 |
| `seo-content-skills` | SEO 内容营销：关键词研究 / 技术优化 / 长文创作 / 内容编辑 / 链接策略 / 转化率分析 | 5+ |
| `ket-prep-skills` | KET 剑桥少儿备考：学情诊断 / 词汇语法 / 听读 / 写说 / 模考 | 5 |
| `ncre-exam-skills` | NCRE 计算机等级：一级→四级 + 主理人（徐庆初）| 5 |
| `open-spec-doc-skills` | 企业级长文档：调研 / 生成 / 审核 — 6 阶段 SOP | 3 |
| `humanize-ppt-skills` | AST 人感 PPT：大纲导演 → 魁藏 / Zara / HyperFrames / OPC / 前端 HTML / 视频动效 | 5+ |

### 3.4 内容细分 — 教学 / 科研 / 智能 🎓 (4 个专家团)

| 新目录 | 简介 | 专家数 |
|--------|------|--------|
| `academic-journal-selector-skills` | 学术选刊顾问 v3.0：中外刊并行管道，冲稳保三层投稿方案 | 4 |
| `gpt-researcher-skills` | 深度研究：5 阶段 SOP，多源聚合 + 审稿循环 | 6 |
| `ket-prep-skills` | 同上（语言教学复用）| — |
| `ncre-exam-skills` | 同上（考试复用）| — |

### 3.5 开发 / 工程 DevOps 🛠 (7 个专家团 / ~40+ 位专家)

| 新目录 | 简介 | 专家数 |
|--------|------|--------|
| `aicoding-architecture-expert-skills` | 复杂系统架构：摄入→调研→高层→系统→UserStory→部署→安全 + Gate 返工 | 6 |
| `mvp-dev-skills` | MVP 全栈：PM / 设计 / 架构 / 前端 / 后端 / QA / DevOps | 7 |
| `makers-skills` | EdgeOne Makers 部署：前端 / 后端 / AI Agent / CLI / 部署 + 交付总监 | 6 |
| `software-company-skills` | 软件公司（快速模式）：PM 定需求 → 架构师拆任务 → 工程师批量实现 → QA | 5 |
| `software-workshop` | GStack 软件工坊：产品评审 / 代码审查 / 安全审计 / QA / 设计系统 / 调试运维 + 主理人 | 6 |
| `engineering-assurance-skills` | 工程保障：架构评审 / 代码审查 / SRE 事故响应 / 测试 / 技术文档 | 5 |
| `ai-data-copilot-skills` | 智数分析 (Crew AI)：SQL / 数据科学 / RAG / 可视化 / 报告生成 | 6 |

### 3.6 设计 Design 🎨 (2 个专家团 / ~11 位专家)

| 新目录 | 简介 | 专家数 |
|--------|------|--------|
| `design-engine-skills` | 设计原型：发现 / 设计系统 / 原型 / 评审 / 导出 + 主理人 + 内置 71 套设计系统 | 6 |
| `humanize-ppt-skills` | （见 3.3）AST 方法论上游，作为设计工程的一支 | — |

### 3.7 法律 / 合规 Legal ⚖ (3 个专家团 / ~15 位专家)

| 新目录 | 简介 | 专家数 |
|--------|------|--------|
| `chatlaw-skills` | 中文法律咨询：民事 / 婚姻 / 合同 / 劳动 / 侵权 — 4 阶段 + 判例撰写 | 5 |
| `enterprise-legal-skills` | 企业法务：合同 / 并购 / 劳动 / 隐私 / 产品 / 合规 / AI 治理 / IP + 中国区本地化 | 9 |
| `smb-team-skills` | SMB 经营总管：客户 / 合约 / 投诉 / CRM / 流失预警 | 1 |

### 3.8 财税 Tax / Compliance 🧾 (2 个专家团 / ~12 位专家)

| 新目录 | 简介 | 专家数 |
|--------|------|--------|
| `tax-compliance-skills` | 财税合规：票据 / 记账 / 报表 / 税务申报 / 合规审计 + 主理人 + 引擎 | 6 |
| `invoice-verify-skills` | 智能发票（百望体系）：识别 → 验真 → 征信 → 归档 | 5 |

### 3.9 数据分析 Data Analysis 📊 (2 个专家团 / ~10 位专家)

| 新目录 | 简介 | 专家数 |
|--------|------|--------|
| `huashu-data-pro-skills` | 花叔本地数据分析：趋势 / 结构 / 异常三专家并行，网页 / Excel / PPT 三格式报告 | 3+ |
| `ai-data-copilot-skills` | 智数分析（应用化 SQL 工作流，侧重应用系统落地）| — |

### 3.10 销售 Sales 🤝 (1 个专家团 / 5 位专家)

| 新目录 | 简介 | 专家数 |
|--------|------|--------|
| `sales-battle-skills` | 销售攻坚：客户研究 / 竞品情报 / 外联策略 / 销售预测 — 主理人 + 4 成员 | 5 |

### 3.11 运营 / HR Ops 🏢 (1 个专家团 / 5 位专家)

| 新目录 | 简介 | 专家数 |
|--------|------|--------|
| `hr-operations-skills` | HR 运营：招聘 / 薪酬分析 / 组织发展 / 入职管理 + 主理人 | 5 |

### 3.12 社媒互动 Social Growth 📱 (1 个专家团 / 5 位专家)

| 新目录 | 简介 | 专家数 |
|--------|------|--------|
| `social-engagement-skills` | 社媒增长：AI 评论 / 互动自动化 / 品牌舆情 / 信号挖掘 — 覆盖 14+ 平台 | 5 |

### 3.13 市场 / 产品 📈 (2 个专家团 / ~9 位专家)

| 新目录 | 简介 | 专家数 |
|--------|------|--------|
| `product-strategy-skills` | 产品战略：需求 / 用户研究 / 竞品 / 数据 / 路线图 + 主理人 | 5 |
| `gpt-researcher-skills` | （见 3.4，深度研究复用）| — |

---

## 4. 快速开始

### 4.1 导入到任意 agent / 编排框架
每个 `SKILL.md` 本质上是一段长 system prompt。典型用法：
- 直接用作 **OpenAI Custom GPTs / Claude Project / Gemini / Coze / Dify / MetaGPT / AutoGen / CrewAI** 的 system prompt
- 把"知识检索工具"调用改成目标平台的等价工具即可跨框架移植
- 最优结构：以 `*team-lead/SKILL.md` 作为 orchestrator，成员 skill 按需作子 agent 调用

### 4.2 目录命名规则
本仓**统一改为** `kebab-case-skills` 风格：

| 原 WorkBuddy 团队名 | 仓内目录 |
|--------------------------|---------|
| InvestmentGroups | `investment-masters-skills` |
| TradingAgentTeam | `trading-agent-skills` |
| AiContentCreatorTeam | `ai-content-creator-skills` |
| AiDataCopilot | `ai-data-copilot-skills` |
| DesignEngineTeam | `design-engine-skills` |
| 刺桐说Pro | `citongshuopro-skills` |
| 学术选刊顾问团 | `academic-journal-selector-skills` |
| 社媒互动增长专家团 | `social-engagement-skills` |
| 花叔数据分析专家团 | `huashu-data-pro-skills` |
| StockPartnerTeam | `stock-partner-skills` |
| GPTResearcherTeam | `gpt-researcher-skills` |
| SeoContentTeam | `seo-content-skills` |
| MvpDevExpertTeam | `mvp-dev-skills` |
| … | … |

完整对照表请查看附录 A。

### 4.3 跨 skill 协作参考
本仓 skill **不强制依赖其他目录**，但一些 skill 在 `description:` 段提到协作场景：

- `mvp-dev-skills` ↔ `makers-skills` ↔ `aicoding-architecture-expert-skills`：前端 / 后端 / Agent 提示注入的工程互参
- `marketing-campaign-skills` ↔ `seo-content-skills`：共享关键词策略 / 内容日历模板
- `product-strategy-skills` 下游可接到 `ai-data-copilot-skills` / `huashu-data-pro-skills`
- `chatlaw-skills` ↔ `enterprise-legal-skills` ↔ `smb-team-skills`：消费者 ↔ 企业 ↔ SMB 三层法律阶梯
- `investment-masters-skills` / `a-share-skills` / `trading-agent-skills` 三套投研互相 roundtable

### 4.4 推荐起始组合

| 目标 | 选用 |
|------|------|
| 营销 + 内容 | `ai-content-creator-skills` + `content-distribution-skills` + `marketing-campaign-skills` |
| A 股投研 | `a-share-skills` + `stock-partner-skills` + `trading-agent-skills` |
| 大师圆桌 | `investment-masters-skills` |
| MVP / App 交付 | `mvp-dev-skills` 或 `mvp-dev-skills` + `software-company-skills` |
| 设计 → 工程闭环 | `design-engine-skills` + `software-company-skills` + `software-workshop` |
| 数据 / 分析策略 | `ai-data-copilot-skills` + `huashu-data-pro-skills` |
| 内容变现 | `content-monetization-skills` + `promo-creator-skills` |
| 学术 / 教育 / 选刊 | `academic-journal-selector-skills` + `gpt-researcher-skills` + `ket-prep-skills` + `ncre-exam-skills` |
| SMB 经营治理 | `enterprise-legal-skills` + `tax-compliance-skills` + `invoice-verify-skills` + `hr-operations-skills` + `smb-team-skills` |
| 投研 IP 变现 | `stock-partner-skills` + `investment-masters-skills` + `citongshuopro-skills` |

---

## 5. 参与贡献

欢迎任何能提高 **skill 复用性 / 团队互操作性 / 可读性 / 可移植性** 的贡献。

- **事实修复**：若 `SKILL.md` 内容已与目录不一致 → 开 PR / Issue
- **翻译**：任何尚未有 `README.en.md` 的 skill → 欢迎补英译
- **SOP 模板化**：把跨 skill 的 lead 检查单 / member 返工契约 / Gate 清单提出 `_templates/`
- **框架迁移**：把 WorkBuddy 原生工具调用移植到 LangChain / CrewAI / AutoGen / Dify，放在 `examples/`
- **保留原作者 attribution**：衍生 README 顶部保留原始作者 ID / 链接 / `name:` 字段

### 提交约定

1. PR 正文列出：涉及哪些目录、新增哪些模板、移除了哪些硬编码工具调用。
2. **禁止提交**商业账号 id / token、API key 等敏感信息。
3. 如补 `README.en.md`，请**与 `README.zh.md` 的章节号一致**。

---

## 附录 A：旧 → 新目录名对照表

| 旧目录名（迁移前） | 新目录名 |
|---------------------|---------|
| InvestmentGroups | investment-masters-skills |
| SEOskills | seo-content-skills |
| aicoding-expert-team | aicoding-architecture-expert-skills |
| content-distribution-team | content-distribution-skills |
| copilot-skills | ai-data-copilot-skills |
| doc-team-skills | open-spec-doc-skills |
| engineering-assurance | engineering-assurance-skills |
| hr-operations-skill-files | hr-operations-skills |
| invoice-verify-skill-docs | invoice-verify-skills |
| ket | ket-prep-skills |
| marketing-campaign | marketing-campaign-skills |
| ncre-skills | ncre-exam-skills |
| opc-team-docs | opc-team-skills |
| product-strategy | product-strategy-skills |
| research-team-skills | gpt-researcher-skills |
| sales-battle | sales-battle-skills |
| smb-skills | smb-team-skills |
| stock-partner-skill-docs | stock-partner-skills |
| video-gen-team-skills | video-gen-skills |
| 刺桐说Pro | citongshuopro-skills |
| 学术选刊顾问团 | academic-journal-selector-skills |
| 社媒互动增长专家团 | social-engagement-skills |
| 花叔数据分析专家团 | huashu-data-pro-skills |

## 附录 B：仓库规模

- **39 个 skill 目录**
- **450+ 个 md 文档**（SKILL.md / README.md / agents / members / references）
- **13 个一级分类、~170+ 个独立专家角色**
- 总仓库大小：~600KB 纯文本（平台描述性 skill 包，无模型权重）


# WorkBuddy Expert Teams Skill Hub (Open Source)

> **Usage notice**: All skill files in this repo are **generated by end users through ordinary text conversations with the official WorkBuddy platform using their own personal accounts**. No cracked installers, no extraction of bundled app files, no reverse engineering, no packet sniffing, and no reverse-engineering by model-API-call data — none of these technical means were employed. No guarantee that these skills are 100% identical to the WorkBuddy originals (the platform may update; outputs depend on prompt / model version).

---

## 1. Project Intro

This repo archives **multi-agent collaboration skills** from [WorkBuddy](https://workbuddy.ai) — an "AI expert agent marketplace". Each subfolder is an "expert team" (one orchestrator + multiple specialist roles), designed to complete stage-based work in a specific domain:

- Investment research, monetization & trading
- Content creation, video production, marketing & distribution
- Design, MVP development, DevOps, legal, tax, sales, HR, data analysis
- Academic prep, exam prep, social-media growth, journal selection

Each skill can be imported into any agent / orchestration framework (OpenAI Custom GPTs / Claude Project / Gemini / Coze / Dify / MetaGPT / AutoGen / CrewAI etc.) as a long system prompt. Loading `*team-lead/SKILL.md` as orchestrator and invoking member skills as on-demand sub-agents is the canonical way to use them.

---

## 2. License & Disclaimer

### 2.1 License

Code and docs are released under **MIT License** (see `LICENSE`).

### 2.2 Data provenance & compliance

1. **Transparent generation**. Every skill file is generated by the end user through ordinary conversation with the WorkBuddy official platform under their own personal account. No cracked installers; no extraction of bundled app files; no reverse engineering; no packet sniffing; no reconstruction from model API call data.
2. **No identity guarantee**. Skill content can vary slightly across time / prompts / model versions; **no guarantee of 100% fidelity to the WorkBuddy originals**. Always independently verify any information you rely on here (legal clauses, tax rules, investment advice, medical / safety-critical content).
3. **Data & compliance**. Generation material comes from legitimate WorkBuddy platform calls, in-domain compliance documents, or public corpora. You are solely responsible for how you use the contents of this repo.
4. **Third-party attribution**. Some skills directly reuse methodologies or documentation from the following open-source / guest authors — copyright and attribution remain with the original authors:
   - *One Person Company Methodology*: Easychen — <https://github.com/easychen/opc-methodology>
   - *AST-based Humanize PPT* (MIT License): LearnPrompt team — <https://github.com/LearnPrompt/humanize-ppt>
   - *Tencent Stock Partner series*: author `jensonli@tencent.com`
   - *Citongshuopro Investment Community*: DuGeLearnQuant (杜哥学量化)
   - *Carl's Human-like PPT*: Carl AI Watts (卡尔的AI沃茨)
   - *AI Video Creation & Video Dissection*: Cang He (苍何)
   - *HuaShu Data Analysis*: HuaShu (花叔 / Alchain)
   - *Smart Invoice series*: BaiWang Group (百望股份)
   - *Makers Dev series*: vincentlli
   - *MVP Dev series*: Excellent
   - *NCRE Exam prep series*: Xu Qingchu
   - *KET Exam prep series*: AI Science Bureau (AI科学局)

If you are an original author and wish to have your content modified or removed, please open an Issue — we will respond within 5 business days.

---

## 3. Categorized Index

> 📖 **Reading tip**: Find your category → open the folder → start with `README.md`; if absent, read the team-lead's `SKILL.md` or `*-team-lead.md`.
> A skill can appear in multiple categories; this table lists each skill only once under its primary category with cross-links in section 4.

### 3.1 Investment Analysis 📈 (6 teams / ~50+ experts)

| Folder | Short description | Experts (lead + members) |
|--------|-------------------|--------------------------|
| `investment-masters-skills` | AI hedge-fund roundtable — 13 legendary philosophers + 6 analysts + 2 managers (portfolio + risk); reference Buffett / Munger / Fisher / Templeton / Dalio / Jhunjhunwala | 21 |
| `a-share-skills` | A-share end-to-end: macro → industry → capital flow → single-name → valuation → risk-diagnosis → advisor | 8 |
| `stock-partner-skills` | Tencent Stock Partner real-trader cases: industry strategy / signal capture / valuation / bottom-fishing / fundamentals / short-term | 7 |
| `trading-agent-skills` | Bull-bear debate investing: technical / fundamental / news / sentiment / bull & bear researchers / research director / trader / three-way risk | 13 |
| `citongshuopro-skills` | Citongshuopro investment community: lead routes 4 community guests (Gy / Jia / LittleStar / ZhangLaoshi) | 4 |
| `super-partner-skills` | FuBangShou Super Partner: entry routing → "company next step" / genius-draft / multi-workshop / service-follow / Lebao commercialization | 11 |

### 3.2 Monetization / Commercialization 💰 (skill reuse)

| Folder | Reuse scenario |
|--------|----------------|
| `content-monetization-skills` | CPS affiliate / CPE·CPM ads / creator↔brand match / BD sales — 5-person monetization loop |
| `super-partner-skills` | Commercialization landing: Lebao activation & capability continuation |
| `a-share-skills` / `stock-partner-skills` | A-share / investment-research content → personal-IP material |
| `investment-masters-skills` | Master methodologies (dhandho-master etc.) → paid courses / knowledge products |

### 3.3 Content Creation / Marketing 📣 (10 teams / ~55+ experts)

| Folder | Short description | Experts |
|--------|-------------------|---------|
| `ai-content-creator-skills` | Multimedia content production: creative strategy / copywriting / video-gen / image-gen / retouching / adaptation / AI video | 7+ |
| `video-gen-skills` | AI short-video team: collector / planner·scriptwriter / producer·renderer + reference lib | 5 |
| `promo-creator-skills` | Product promo videos: brief → storyboard → asset → HyperFrames edit → BGM → delivery | 6 |
| `content-distribution-skills` | 13+ cross-platform distribution (incl. WeChat video, Xiaohongshu) | 5 |
| `marketing-campaign-skills` | Marketing campaign: content creator / planner / SEO / brand analyst — 4-person full lifecycle | 4 |
| `seo-content-skills` | SEO content marketing: keyword research / tech SEO / long-form / editing / link strategy / CRO | 5+ |
| `ket-prep-skills` | Cambridge KET prep: aptitude / vocab+grammar / listening+reading / speaking+writing / mock | 5 |
| `ncre-exam-skills` | NCRE computer ranks: Level 1→4 + lead (Xu Qingchu) | 5 |
| `open-spec-doc-skills` | Enterprise long-docs: research → generate → review — 6-stage SOP | 3 |
| `humanize-ppt-skills` | AST human-like PPT: outline director → Kuizang / Zara / HyperFrames / OPC / front-end HTML / Remotion video | 5+ |

### 3.4 Niche — Teaching / Research / Intelligent 🎓 (4 teams)

| Folder | Short description | Experts |
|--------|-------------------|---------|
| `academic-journal-selector-skills` | Academic journal selector v3.0: parallel CN/EN pipelines, tiered submission | 4 |
| `gpt-researcher-skills` | Deep research: 5-stage SOP with multi-source aggregation + review loop | 6 |
| `ket-prep-skills` | Ditto (language teaching reuse) | — |
| `ncre-exam-skills` | Ditto (exam reuse) | — |

### 3.5 Development / Engineering DevOps 🛠 (7 teams / ~40+ experts)

| Folder | Short description | Experts |
|--------|-------------------|---------|
| `aicoding-architecture-expert-skills` | Complex-system architecture: intake → research → high-level → system → UserStory → deploy → security + Gate-based rework | 6 |
| `mvp-dev-skills` | MVP full-stack: PM / designer / architect / frontend / backend / QA / DevOps | 7 |
| `makers-skills` | EdgeOne Makers deployment: frontend / backend / AI Agent / CLI / deploy + delivery director | 6 |
| `software-company-skills` | Software company (fast mode): PM specs → architect splits → engineer batch-implements → QA | 5 |
| `software-workshop` | GStack Software Workshop: product review / code review / security audit / QA / design system / ops | 6 |
| `engineering-assurance-skills` | Engineering assurance: architecture review / code review / SRE incident / testing / tech-writing | 5 |
| `ai-data-copilot-skills` | Crew AI (智数分析): SQL / data science / RAG / visualization / report composer | 6 |

### 3.6 Design 🎨 (2 teams / ~11 experts)

| Folder | Short description | Experts |
|--------|-------------------|---------|
| `design-engine-skills` | Design-prototype: discovery / design-system / prototype / review / export + lead + 71 built-in design systems | 6 |
| `humanize-ppt-skills` | (see 3.3) AST methodology upstream of design engineering | — |

### 3.7 Legal / Compliance ⚖ (3 teams / ~15 experts)

| Folder | Short description | Experts |
|--------|-------------------|---------|
| `chatlaw-skills` | Chinese legal advisory: civil / marriage / contract / labor / tort — 4-stage SOP + case writing | 5 |
| `enterprise-legal-skills` | Enterprise legal: commercial / M&A / labor / privacy / product / compliance / AI governance / IP + 2 CN-localized packs | 9 |
| `smb-team-skills` | SMB governance: customer / contract / complaints / CRM / churn | 1 |

### 3.8 Tax / Compliance 🧾 (2 teams / ~12 experts)

| Folder | Short description | Experts |
|--------|-------------------|---------|
| `tax-compliance-skills` | Tax compliance: invoicing / bookkeeping / reporting / filing / audit + lead + engine | 6 |
| `invoice-verify-skills` | Smart Invoice (BaiWang series): recognize → verify → credit-check → archive | 5 |

### 3.9 Data Analysis 📊 (2 teams / ~10 experts)

| Folder | Short description | Experts |
|--------|-------------------|---------|
| `huashu-data-pro-skills` | HuaShu local analytics: trend / structure / anomaly trio, HTML / Excel / PPT triple-report, data stays local | 3+ |
| `ai-data-copilot-skills` | 智数分析 (application-focussed SQL workflow) | — |

### 3.10 Sales 🤝 (1 team / 5 experts)

| Folder | Short description | Experts |
|--------|-------------------|---------|
| `sales-battle-skills` | Sales force: account research / competitive intel / outreach / forecast · lead + 4 members | 5 |

### 3.11 Operations / HR 🏢 (1 team / 5 experts)

| Folder | Short description | Experts |
|--------|-------------------|---------|
| `hr-operations-skills` | HR operations: recruiting / comp / org-development / onboarding + lead | 5 |

### 3.12 Social Growth 📱 (1 team / 5 experts)

| Folder | Short description | Experts |
|--------|-------------------|---------|
| `social-engagement-skills` | Social-media growth: AI comments / interaction automation / brand monitoring / signal mining — covers 14+ platforms | 5 |

### 3.13 Market / Product 📈 (2 teams / ~9 experts)

| Folder | Short description | Experts |
|--------|-------------------|---------|
| `product-strategy-skills` | Product strategy: requirement / user-research / competitive / data / roadmap + lead | 5 |
| `gpt-researcher-skills` | (see 3.4, deep research reuse) | — |

---

## 4. Quickstart

### 4.1 Import into any agent / orchestration framework

Each `SKILL.md` is effectively a long system prompt. To use it:
- Drop directly as the system prompt for OpenAI Custom GPTs / Claude Project / Gemini / Coze / Dify / MetaGPT / AutoGen / CrewAI.
- Rewrite only the knowledge-retrieval tool calls to port across frameworks.
- Best practice: load `*team-lead/SKILL.md` as orchestrator and invoke member skills on demand as sub-agents.

### 4.2 Naming conventions

This repo is normalized to `kebab-case-skills` style. Full old → new mapping in Appendix A.

### 4.3 Cross-skill reference

Skills in this repo **do not hard-depend on other folders**, but a few reference collaboration scenarios in their `description:`:

- `mvp-dev-skills` ↔ `makers-skills` ↔ `aicoding-architecture-expert-skills`: shared front/back/agent prompt-injection engineering
- `marketing-campaign-skills` ↔ `seo-content-skills`: shared keyword-strategy & content-calendar template
- `product-strategy-skills` downstream feeds `ai-data-copilot-skills` / `huashu-data-pro-skills`
- `chatlaw-skills` ↔ `enterprise-legal-skills` ↔ `smb-team-skills`: 3-tier legal ladder (consumer ↔ enterprise ↔ SMB)
- `investment-masters-skills` / `a-share-skills` / `trading-agent-skills`: cross-roundtable investment analysis

### 4.4 Starter recipes

| Goal | Start with |
|------|-----------|
| Marketing & content | `ai-content-creator-skills` + `content-distribution-skills` + `marketing-campaign-skills` |
| A-share equity research | `a-share-skills` + `stock-partner-skills` + `trading-agent-skills` |
| Multi-master roundtable | `investment-masters-skills` |
| MVP / app delivery | `mvp-dev-skills` or `mvp-dev-skills` + `software-company-skills` |
| Design-dev closed loop | `design-engine-skills` + `software-company-skills` + `software-workshop` |
| Data / analytics strategy | `ai-data-copilot-skills` + `huashu-data-pro-skills` |
| Content monetization | `content-monetization-skills` + `promo-creator-skills` |
| Academic / EdTech / journal selection | `academic-journal-selector-skills` + `gpt-researcher-skills` + `ket-prep-skills` + `ncre-exam-skills` |
| SMB governance | `enterprise-legal-skills` + `tax-compliance-skills` + `invoice-verify-skills` + `hr-operations-skills` + `smb-team-skills` |
| Investment IP monetization | `stock-partner-skills` + `investment-masters-skills` + `citongshuopro-skills` |

---

## 5. Contributing

Contributions are welcome as long as they improve **skill reusability / team interoperability / readability / portability**.

- **Factual fixes**: if a `SKILL.md` no longer matches its folder → PR / Issue
- **Translations**: any skill without `README.en.md` is open for translation
- **SOP templating**: extract the recurring lead checklists, member rework contracts, and Gate checklists into `_templates/`
- **Framework migration**: port any WorkBuddy-native tool-call into LangChain / CrewAI / AutoGen / Dify minimal demos under `examples/`
- **Author attribution**: keep the original author IDs / links / `name:` fields at the top of derived READMEs.

### Submission conventions

1. PR body lists: affected folders, new templates, hardcoded tool calls removed.
2. **Never commit** commercial account ids or tokens.
3. If adding `README.en.md`, **mirror section numbering** with `README.zh.md`.

---

## Appendix A: old → new directory names

| Old directory (before reorganization) | New directory |
|---------------------------------------|---------------|
| InvestmentGroups | investment-masters-skills |
| SEOskills | seo-content-skills |
| aicoding-expert-team | aicoding-architecture-expert-skills |
| content-distribution-team | content-distribution-skills |
| copilot-skills | ai-data-copilot-skills |
| doc-team-skills | open-spec-doc-skills |
| engineering-assurance | engineering-assurance-skills |
| hr-operations-skill-files | hr-operations-skills |
| invoice-verify-skill-docs | invoice-verify-skills |
| ket | ket-prep-skills |
| marketing-campaign | marketing-campaign-skills |
| ncre-skills | ncre-exam-skills |
| opc-team-docs | opc-team-skills |
| product-strategy | product-strategy-skills |
| research-team-skills | gpt-researcher-skills |
| sales-battle | sales-battle-skills |
| smb-skills | smb-team-skills |
| stock-partner-skill-docs | stock-partner-skills |
| video-gen-team-skills | video-gen-skills |
| 刺桐说Pro | citongshuopro-skills |
| 学术选刊顾问团 | academic-journal-selector-skills |
| 社媒互动增长专家团 | social-engagement-skills |
| 花叔数据分析专家团 | huashu-data-pro-skills |

## Appendix B: repo scale

- **39 skill directories**
- **450+ md files** (SKILL.md / README.md / agents / members / references)
- **13 top-level categories, ~170+ distinct expert roles**
- Total repo size: ~600KB text only (no model weights).

---
---

## 6. 普通用户（非开发者）如何利用这些 expert skills

你**不需要写代码**，也能把这份 repo 里的许多 expert skills 立刻用在日常对话 AI 上。
核心思路：任何一个 `SKILL.md` 本质都是一段很长很详细的「系统提示词」；把它们粘贴到对话中，就相当于「召唤了那个专家」。

### 6.1 在国产免费 AI 中直接用（国内用户优先）

| App | 如何使用 | 推荐场景 |
|-----|---------|---------|
| **豆包（字节跳动）** | ① 进入「智能体」/「AI 应用」→「创建智能体」<br>② 把某个 skill 目录下 `SKILL.md` 全文粘贴到【系统提示词】<br>③ 指令中保留"触发词"作为示范 prompt | 写作/营销/内容/日常办公/教育 |
| **DeepSeek（深度求索）** | ① 在对话开头或【系统消息】里粘贴完整的 SKILL.md<br>② 多轮对话可让 DeepSeek 严格遵循工作流 | 投研/文档/数据分析/代码辅助 |
| **Kimi（月之暗面）** | 同上，Kimi 对长 system prompt 的支持很好 | 长文档分析/法律/选刊 |
| **通义千问（阿里云）** | ①「创作」→「创建智能体」<br>② 粘贴为主系统提示 | 电商文案/营销/办公 |
| **文心一言（百度）** | 提示词模式直接粘贴；不需要开发部署 | 教育/日常问答 |
| **腾讯元宝** | 粘贴为 system prompt 即可使用 | GPT 应用/投研 |

### 6.2 在国外免费 AI 上同样可用

| App | 如何使用 | 推荐场景 |
|-----|---------|---------|
| **ChatGPT 免费版** | 在对话开头粘贴 SKILL.md（或让 ChatGPT 的系统提示允许长文本） | 通用 |
| **Gemini（Google）** | 通过「Custom Instructions」或在对话前用"system:"前缀粘贴 | 通用/办公 |
| **Claude.ai（Anthropic）** | 在 Project 中配置 System Prompt，粘贴 SKILL.md 全文 | 写作/政策/严肃内容 |
| **HuggingChat** | 任意华文开源模型都支持长 system prompt | 通用 |
| **Poe（Quora）** | Bot 设置里粘贴 system prompt | 通用 |

### 6.3 步骤示例（以豆包为例）

1. 选一个你想用的 skill，比如 `chatlaw-skills（中文法律咨询团）`
2. 打开 <https://github.com/darker2016/workbuddy-skill-groups/tree/main/chatlaw-skills>
3. 依次把 `chatlaw-info-intake.md` `chatlaw-legal-research.md` `chatlaw-case-precedent.md` `chatlaw-advice-writer.md` `chatlaw-report-finalizer.md` 全文复制下来
4. 在豆包里创建智能体，把 5 段内容合并为一条 long system prompt
5. 发送一条法律咨询试试 — 你会得到一个接近 WorkBuddy 的专业分析

### 6.4 局限：**复杂任务在 WorkBuddy 之外会弱一些**

如果你尝试后发现效果没有 WorkBuddy 原生那么强，通常是以下几个原因 — **请先调整预期**：

- **子 agent 调度被压扁。** WorkBuddy 里每个 member 是一个「被独立调度的 agent」；在免费 app 里你只能把所有成员规则压进同一个对话上下文。当任务复杂、成员间交接多时，单轮对话会丢失上下文。
- **工具调用无法原生执行。** 许多 skill 内部依赖 WorkBuddy 的 tool calls（知识检索 / 内部数据源）。在 free apps 里这些工具不存在，skill 会"降级"为纯 prompt 指引。
- **Agent 内存与 RAG 缺失。** WorkBuddy 维持了会话级记忆和文档级 RAG；单 app 单对话做不到多阶段共享复杂上下文。
- **角色一致性在长事务里漂移。** 当 prompt 很长 + 轮数很多时，模型容易"忘记自己是第几阶段、该谁出场"。

**建议用于**：

- 一次性 / 短任务（单次 < 10 轮对话）
- 单角色为主的 skill（如 copywriting、法律、学情诊断）
- "先把 Skill 的主理人 prompt 用作高质量 system prompt"的场景

**不建议用于**：

- 需要多 agent 真正并行计算（如投资大师团 13 位哲学家同时独立输出）
- 需要 WorkBuddy 私有数据源 / 实时金融数据的场景
- 长事务协作（如跨 6 阶段的 MVP 开发）

**最佳实践**：先在这些 free app 里试试用**主理人 SKILL.md**（而非成员）作为 system prompt，把成员文件作为任务指令或按需插入，效果最稳定。

---

## 7. 感谢 WorkBuddy 团队

最后，想手打一段对 WorkBuddy 团队的感谢。

我们刚才所做的所有工作 — 把平台上用过的专家团 skills 复刻成开源仓库 — 全部是**通过普通对话方式、在 WorkBuddy 官方渠道、用我们自己的个人账号生成**的。过程中没有使用破解安装包、没有获取应用文件夹内的文件、没有反编译、没有抓包、没有基于模型 API 调用数据逆向。

但与此同时，我们也**发现 WorkBuddy 团队非常开放**：对这些 skills，官方没有藏着掖着，对照后发现应用内的系统提示词**几乎没有限制、屏蔽、混淆等动作**。换句话说，如果你是一个愿意花时间认真描述需求 + 善于提问的人，完全可以在 WorkBuddy 上"对话式生成"出近乎完美的专有 agent skill —— 这是 WorkBuddy 作为产品最值得被看见的地方。

---

# WorkBuddy Expert Teams Skill Hub (Open Source)

> **Usage notice**: All skill files in this repo are **generated by end users through ordinary text conversations with the official WorkBuddy platform using their own personal accounts**. No cracked installers, no extraction of bundled app files, no reverse engineering, no packet sniffing, and no reverse-engineering by model-API-call data — none of these technical means were employed. No guarantee that these skills are 100% identical to the WorkBuddy originals (the platform may update; outputs depend on prompt / model version).

*以下为英文版 §6 / §7，与上方中文内容一一对应。*

---

## 6. How non-developers can use these expert skills

You **do not need to write any code** to start using many of the skills from this repo in your favorite chat AI today.
Core idea: every `SKILL.md` is, in essence, a long and detailed **system prompt**; paste it into a conversation and you have effectively "summoned that expert".

### 6.1 Use directly in free Chinese AI apps (recommended for users in CN)

| App | How to use | Good for |
|-----|-----------|----------|
| **Doubao (豆包, ByteDance)** | ① Go to "智能体 / AI 应用" → "创建智能体"<br>② Paste a `SKILL.md` into the "系统提示词" (system prompt)<br>③ Keep trigger words as sample prompts in instructions | Copywriting / marketing / content / office / education |
| **DeepSeek (深度求索)** | ① Paste the full `SKILL.md` at the start of the conversation or as a 【系统消息】<br>② Multi-turn conversations will adhere to the SOP | Investment research / documents / data analysis / code |
| **Kimi (月之暗面)** | Same as above; Kimi supports long system prompts well | Long documents / legal / journal selection |
| **Tongyi Qianwen (通义千问, Alibaba)** | ① "创作" → "创建智能体"<br>② Paste as main system prompt | E-commerce copy / marketing / office |
| **ERNIE Bot (文心一言, Baidu)** | Paste in prompt mode; no deployment needed | Education / everyday Q&A |
| **Tencent Yuanbao (腾讯元宝)** | Paste as system prompt and start chatting | GPT apps / investment research |

### 6.2 Also works in free overseas AI apps

| App | How to use | Good for |
|-----|-----------|----------|
| **ChatGPT (free tier)** | Paste `SKILL.md` at the very beginning of the conversation | General |
| **Gemini (Google)** | Use "Custom Instructions" or prepend with "system:" in the message | General / office |
| **Claude.ai (Anthropic)** | Project → System Prompt → paste the full `SKILL.md` | Copywriting / policy / serious content |
| **HuggingChat** | Any open-weight Chinese-friendly model accepts long system prompts | General |
| **Poe (Quora)** | Bot settings → System Prompt | General |

### 6.3 Step by step (Doubao example)

1. Pick a skill, e.g. `chatlaw-skills (中文法律咨询团)`.
2. Open <https://github.com/darker2016/workbuddy-skill-groups/tree/main/chatlaw-skills>.
3. Copy the full text of each file: `chatlaw-info-intake.md`, `chatlaw-legal-research.md`, `chatlaw-case-precedent.md`, `chatlaw-advice-writer.md`, `chatlaw-report-finalizer.md`.
4. Create a new "智能体" in Doubao and paste the 5 blocks as one long system prompt.
5. Send a legal query — you will get an analysis close to what WorkBuddy produces natively.

### 6.4 Limitation: **complex tasks perform weaker than on WorkBuddy**

If you try these skills outside WorkBuddy and the result feels weaker, that is usually expected. Please calibrate your expectations:

- **Sub-agent dispatch is flattened.** On WorkBuddy each member is an "independently scheduled agent"; in a free app you have to compress all member rules into a single conversation context. Complex tasks with many hand-offs easily lose context inside a single thread.
- **Tool calls cannot be executed natively.** Many skills depend on WorkBuddy tool-calls (knowledge retrieval / private data sources). On these free apps those tools do not exist, so the skill "downgrades" to a guidance prompt.
- **Cross-session memory & RAG are missing.** WorkBuddy maintains session-level memory and document-level RAG; a single conversation on other apps cannot share complex context across stages.
- **Role consistency drifts on very long tasks.** With long prompts and many turns, the model tends to "forget which stage it is on and who should be acting".

**Recommended for**:

- One-shot / short flows (< 10 turns in a single session)
- Skills dominated by one lead role (e.g. copywriting, legal advice, learning diagnosis)
- "Use the lead's SKILL.md as a high quality system prompt" scenarios

**Not recommended for**:

- Tasks that *require* many agents working in parallel (e.g. 13 philosopher-investors producing simultaneous independent output in `investment-masters-skills`)
- Tasks that depend on WorkBuddy private data sources / live financial data
- Very long multi-phase collaborations (e.g. 6-stage MVP development in `mvp-dev-skills`)

**Best practice**: in these free apps, try using **only the lead's `SKILL.md`** as the system prompt and insert member output/input as samples or on demand — this is the most stable approach. For serious or high-stakes conclusions, please use the skills directly on WorkBuddy.

---

## 7. Thanks to the WorkBuddy team

Finally, a personal thank-you to the WorkBuddy team.

Everything we did above — re-creating the expert-team skills we had used on the platform as this open-source repo — was **generated through ordinary text conversations on the official WorkBuddy channel, using our own personal accounts**. At no point did we use cracked installers, extract bundled app files, reverse engineer, packet-sniff, or reconstruct outputs from model API calls.

Along the way we also discovered that **the WorkBuddy team is genuinely open**: for these skills, the official app hid nothing; comparing inputs and outputs showed that the in-app system prompts contain almost **no obfuscation, no masking, no deliberate redaction**. In other words: if you are someone willing to spend time describing your needs carefully and asking good questions, you can "author-by-dialogue" a near-perfect proprietary agent skill entirely on WorkBuddy — and that is the most compelling thing about WorkBuddy as a product.
