# 财税合规专家团 - 完整 SKILL.md 文档包

> 生成日期：2026-07-04
> 文档版本：v1.0
> 团队规模：6 人（1 位主理人 + 5 位专业成员 + 1 个知识引擎）

---

## 文档结构总览

```
tax-compliance-skills/
├── README.md                          ← 本文档（包索引）
├── tax-compliance-team-lead/
│   └── SKILL.md                       ← 主理人 钱合规
├── invoice-processor/
│   └── SKILL.md                       ← 发票处理专员 李票务
├── voucher-accountant/
│   └── SKILL.md                       ← 记账专员 张记账
├── financial-reporter/
│   └── SKILL.md                       ← 报表分析专员 王报表
├── tax-filing-specialist/
│   └── SKILL.md                       ← 纳税申报专员 孙申报
├── compliance-auditor/
│   └── SKILL.md                       ← 合规审计专员 赵审计
└── tax-compliance-engine/
    └── SKILL.md                       ← 财税合规知识引擎
```

## 团队角色对照

| 角色 | Agent ID | 职责定位 | 核心能力 |
|------|----------|---------|---------|
| 钱合规（主理人） | tax-compliance-team-lead | 编排调度、汇总报告 | 团队管理、流程编排、报告汇编 |
| 李票务 | invoice-processor | 发票处理 | OCR识别、验真、分类、查重 |
| 张记账 | voucher-accountant | 记账核算 | 科目表、凭证、账簿、结账 |
| 王报表 | financial-reporter | 报表分析 | 三表编制、比率分析、趋势分析 |
| 孙申报 | tax-filing-specialist | 税务申报 | 各税种计算、优惠匹配、申报表 |
| 赵审计 | compliance-auditor | 合规审计 | 会计/税务/发票合规检查、风险评估 |

## SOP 流程

```
发票处理 → 记账核算 → 报表分析 → 税务申报 → 合规审计 → 综合报告
 李票务      张记账      王报表      孙申报      赵审计      钱合规
```

## 适用范围

- 月度/季度/年度财税合规检查
- 企业税务筹划与优化建议
- 发票批量处理与归档
- 财务报表编制与分析
- 纳税申报预演与核对
- 税务稽查应对准备
- 新企业建账与科目表设置

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
