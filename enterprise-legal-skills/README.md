# 企业法务专家团 · SKILL.md 文档集

本目录包含了企业法务专家团（Enterprise Legal Team）完整的 SKILL.md 文档，覆盖主理人、8 位专业成员以及 2 个中国法务本地化工具包。

## 目录结构

```
enterprise-legal-skills/
├── README.md                                    # 本索引文件
│
├── enterprise-legal-lead/
│   └── SKILL.md                                 # 主理人（法衡中）— 团队编排与工作流定义
│
├── members/
│   ├── commercial-contracts-counsel/
│   │   └── SKILL.md                            # 商业合同法律顾问
│   ├── corporate-ma-counsel/
│   │   └── SKILL.md                            # 公司并购法律顾问
│   ├── employment-law-counsel/
│   │   └── SKILL.md                            # 劳动法律顾问
│   ├── privacy-data-counsel/
│   │   └── SKILL.md                            # 隐私数据法律顾问
│   ├── product-legal-counsel/
│   │   └── SKILL.md                            # 产品法律顾问
│   ├── regulatory-compliance-counsel/
│   │   └── SKILL.md                            # 监管合规法律顾问
│   ├── ai-governance-counsel/
│   │   └── SKILL.md                            # AI 治理法律顾问
│   └── ip-portfolio-counsel/
│       └── SKILL.md                            # 知识产权法律顾问
│
└── toolkits/
    ├── china-legal-research/
    │   └── SKILL.md                            # 中国法条与案例检索
    └── china-compliance-toolkit/
        └── SKILL.md                            # 中国企业法务本地化工具包
```

## 文档清单（共 11 份 SKILL.md）

| # | 文档 | 角色 | 说明 |
|---|------|------|------|
| 1 | `enterprise-legal-lead/SKILL.md` | 主理人（法衡中） | 团队编排、4 种预设 Workflow、协作铁律 |
| 2 | `members/commercial-contracts-counsel/SKILL.md` | 商业合同 | 供应商协议/NDA/SaaS MSA 审查 |
| 3 | `members/corporate-ma-counsel/SKILL.md` | 公司并购 | M&A 尽调、交割清单、董事会决议 |
| 4 | `members/employment-law-counsel/SKILL.md` | 劳动法 | 招聘/解雇审查、劳动争议估算 |
| 5 | `members/privacy-data-counsel/SKILL.md` | 隐私数据 | PIA、DPA、PIPL 合规、权利请求 |
| 6 | `members/product-legal-counsel/SKILL.md` | 产品法务 | 产品发布、营销声明、功能风险评估 |
| 7 | `members/regulatory-compliance-counsel/SKILL.md` | 监管合规 | 法规监控、政策差异分析、合规缺口 |
| 8 | `members/ai-governance-counsel/SKILL.md` | AI 治理 | AI 用例分类、影响评估、供应商 AI 条款 |
| 9 | `members/ip-portfolio-counsel/SKILL.md` | 知识产权 | 商标、FTO、OSS 合规、IP 条款 |
| 10 | `toolkits/china-legal-research/SKILL.md` | 中国法检索 | 法条/案例/企业风险检索 |
| 11 | `toolkits/china-compliance-toolkit/SKILL.md` | 中国合规工具包 | 合同/PIPL/税务/劳动合规资源 |

## 工作流对应关系

| Workflow | 触发场景 | 参与成员 |
|----------|---------|---------|
| A: AI 供应商审查 | AI 供应商、SaaS AI 工具 | 商业合同 + 隐私 + AI 治理 + IP |
| B: 产品发布审查 | 产品上线、营销声明 | 产品法务 + 隐私 + AI 治理 + 监管 + IP |
| C: M&A 尽调 | 收购、数据室、交割清单 | 公司并购 + 商业合同 + 劳动 + IP + 隐私 |
| D: 用工调查 | 解雇、内部调查、人员分类 | 劳动法 + 隐私 + 监管 + 商业合同 |

---

> 本文档集系企业法务专家团（Enterprise Legal Team）的完整 Skill 定义，供 WorkBuddy 平台使用。

---

## 普通用户（非开发者）怎么用

> 提示：本 skill 的 `*.md` 文件本质是一段长 system prompt。  
> 你不需要部署、不需要写代码，**打开任意一个免费 AI 对话产品粘贴即可**。

### 国内免费产品（推荐）

| App | 操作方式 | 何时用 |
|-----|---------|--------|
| **豆包** | 创建「智能体」→ 把 `SKILL.md` 全文填入「系统提示词」 | 营销/内容/办公 |
| **DeepSeek** | 在对话开头或「系统消息」粘贴 `SKILL.md` | 投研/文档/代码 |
| **Kimi** | 同上（支持超长 system prompt） | 长文档/法律 |
| **通义千问 / 文心一言 / 腾讯元宝** | 创建智能体 / 直接粘贴 | 通用 |

### 海外免费产品

| App | 操作方式 | 何时用 |
|-----|---------|--------|
| **ChatGPT 免费版** | 对话最前面粘贴 `SKILL.md` | 通用 |
| **Google Gemini** | 用 Custom Instructions 或"system:"前缀粘贴 | 通用/办公 |
| **Claude.ai** | Project → System Prompt → 粘贴 | 写作/政策/法律 |
| **HuggingChat** | 同上 | 通用 |
| **Poe** | Bot 设置 → System Prompt | 通用 |

### ⚠️ 重要提示：复杂任务效果会弱于在 WorkBuddy 上使用

如果你是在 **WorkBuddy 平台之外**使用这些 expert skills，请对效果保持合理预期：

- **多角色并行被压扁**。WorkBuddy 里每个成员是「独立调度的 agent」；在 free app 里只能把所有成员规则压进同一对话上下文，长事务容易丢失上下文。
- **工具调用不存在**。许多 skill 依赖的 WorkBuddy tool calls（知识检索 / 私有数据源）在 free app 里不可用，skill 会"降级"为纯 prompt。
- **跨会话记忆与 RAG 缺失**。WorkBuddy 维持会话级记忆；其他 app 单对话做不到多阶段共享上下文。
- **角色一致性在长事务里漂移**。轮数多时模型容易"忘记自己是第几阶段"。

**建议** 用于一次性、短流程、单主理人为主的场景；  
**不建议** 用于"13 位哲学家并行投研"、"6 阶段 MVP 开发"、"依赖 WorkBuddy 实时私有数据"的任务。

**最佳实践**：先只把**主理人的 `SKILL.md`** 用作 system prompt；在任务中把成员 input / output 作为示例插入，效果最稳定。对于严肃或需要精准结论的任务，请直接在 WorkBuddy 里使用这些 skills。
