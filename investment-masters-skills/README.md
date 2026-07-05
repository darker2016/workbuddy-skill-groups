# investment-masters-skills（AI 投资大师专家团）

> **来源**：本 skill 由用户在 WorkBuddy 平台官方渠道、通过自己个人账号、以普通对话方式生成。
> 未使用破解安装包 / 获取应用文件夹内文件 / 反编译 / 抓包 / 模型 API 调用数据逆向等技术手段。
> 不保证与 WorkBuddy 原版 100% 一致（平台侧可能更新，生成结果受 prompt / 模型版本影响）。

## 描述

对冲基金圆桌：13 位投资哲学家（巴菲特 / 芒格 / 费雪 / 邓普顿 / 达利欧 等）+ 6 位分析师 + 投资组合经理 + 风控师。

## 团队成员

| ID | 角色 | 名称(若文件中有) |
|----|------|-----------------|
| `ben-graham/SKILL.md` | 成员 | ben-graham |
| `black-swan-prophet/SKILL.md` | 成员 | black-swan-prophet |
| `charlie-munger/SKILL.md` | 成员 | charlie-munger |
| `dean-of-valuation/SKILL.md` | 成员 | dean-of-valuation |
| `dhandho-master/SKILL.md` | 成员 | dhandho-master |
| `growth-analyst/SKILL.md` | 成员 | growth-analyst |
| `hedge-fund-lead/SKILL.md` | **(主理人)** | hedge-fund-lead |
| `macro-king/SKILL.md` | 成员 | macro-king |
| `magellan-captain/SKILL.md` | 成员 | magellan-captain |
| `mama-wood/SKILL.md` | 成员 | mama-wood |
| `news-sentiment-analyst/SKILL.md` | 成员 | news-sentiment-analyst |
| `oracle-of-omaha/SKILL.md` | 成员 | oracle-of-omaha |
| `phil-fisher/SKILL.md` | 成员 | phil-fisher |
| `portfolio-manager/SKILL.md` | 成员 | portfolio-manager |
| `rakesh-jhunjhunwala/SKILL.md` | 成员 | rakesh-jhunjhunwala |
| `technicals-analyst/SKILL.md` | 成员 | technicals-analyst |
| `the-big-short/SKILL.md` | 成员 | the-big-short |
| `valuation-analyst/SKILL.md` | 成员 | valuation-analyst |
| `wall-street-activist/SKILL.md` | 成员 | wall-street-activist |
## 工作流阶段

调度 → 并行研究 → 汇总 → 投票 → 投资决策报告，详见 hedge-fund-lead/SKILL.md。

## 使用

把 `hedge-fund-lead/SKILL.md` 作为主理人的系统提示加载。本仓"主理人文件"为 `hedge-fund-lead/SKILL.md`。

## 目录结构

```
ben-graham/
black-swan-prophet/
charlie-munger/
dean-of-valuation/
dhandho-master/
growth-analyst/
hedge-fund-lead/
macro-king/
magellan-captain/
mama-wood/
news-sentiment-analyst/
oracle-of-omaha/
phil-fisher/
portfolio-manager/
rakesh-jhunjhunwala/
technicals-analyst/
the-big-short/
valuation-analyst/
wall-street-activist/
```

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
