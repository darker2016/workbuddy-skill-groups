# 全域内容分发专家团

一站式多平台内容分发解决方案，覆盖 12+ 全球社交媒体平台。

## 类型

Team 型（5人专家团）

## 功能

全域内容分发专家团专注于帮助创作者、品牌方和企业将内容高效分发到全球 12+ 社交媒体平台。核心能力包括：

- **多平台发布规则适配**：精通各平台的内容规格、审核规则和发布限制
- **日历排期管理**：科学规划发布时间、频率和节奏
- **批量发布编排**：支持同步/错峰/梯度等多种发布策略
- **跨平台数据分析**：统一数据口径，跨平台效果对比和归因分析
- **多账号管理**：矩阵号运营、设备指纹防关联、账号安全防护

### 支持平台

**国内平台**：抖音、小红书、快手、B站、微信公众号、微信视频号

**国际平台**：TikTok、YouTube、Instagram、X (Twitter)、LinkedIn、Pinterest、Facebook、Threads

## 团队成员

| 角色 | Agent ID | 名称 | 职责 |
|------|----------|------|------|
| **主理人** | content-distribution-team-lead | 安拓(Atlas) - 分发策略师 | 多平台分发策略制定、发布节奏规划、团队调度、数据复盘 |
| **国内平台专家** | domestic-platform-expert | 晓红(Ruby) | 抖音/小红书/快手/B站/微信公众号/微信视频号 发布规则与内容适配 |
| **国际平台专家** | international-platform-expert | 格罗(Glow) | TikTok/YouTube/Instagram/X/LinkedIn/Pinterest/Facebook/Threads 发布规则与优化 |
| **排期运营专家** | scheduling-specialist | 凯历(Calendar) | 日历排期管理、批量发布编排、最佳时间策略 |
| **分发数据分析师** | distribution-analyst | 达维(Davis) | 多平台数据聚合分析、发布效果评估、优化建议 |

## 技能清单

| 技能名 | 文件 | 说明 |
|--------|------|------|
| multi-platform-distribution | `skills/multi-platform-distribution/SKILL.md` | 多平台内容分发完整知识体系 |
| xiaohongshu | `skills/xiaohongshu/SKILL.md` | 小红书自动化操作 |
| libtv-skill | `skills/libtv-skill/SKILL.md` | AI 素材生成能力 |
| humanizer | `skills/humanizer/SKILL.md` | 文案去 AI 化处理 |
| wechat-article-search | `skills/wechat-article-search/SKILL.md` | 微信公众号文章搜索 |
| mp-draft-push | `skills/mp-draft-push/SKILL.md` | 微信公众号草稿箱发布 |

## 工作流程

```
Phase 1: 分发策略制定（主理人）
    ↓ 确定目标平台和优先级
Phase 2: 平台适配（并行）
    ↓ 国内平台专家 + 国际平台专家
Phase 3: 排期与执行（排期运营专家）
    ↓ 日历排期 + 批量发布
Phase 4: 数据分析（分发数据分析师）
    ↓ 效果追踪 + 优化建议
Phase 5: 综合报告（主理人）
    ↓ 汇编所有产出
```

## 使用示例

- "帮我把这条视频同时发布到抖音、小红书和 TikTok"
- "为我制定一周的内容发布排期计划"
- "分析我上周各平台的发布数据表现"
- "这条横版视频如何适配到竖版平台？"
- "帮我评估各平台的 ROI，决定资源分配"

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
