# 设计原型专家团 · SKILL.md 文档集

完整覆盖设计原型团队 **6 个角色** 的标准工作流程和协作规范，保存于 `design-engine-skills/` 目录。

## 文件结构

```
design-engine-skills/
├── design-engine-team-lead/       # 主理人画统筹 · 流程编排
│   └── SKILL.md
├── discovery-analyst/             # 需求发现分析师 · 许明需
│   └── SKILL.md
├── design-system-expert/          # 设计系统专家 · 彩格调
│   └── SKILL.md
├── prototype-builder/             # 原型构建师 · 筑原型
│   └── SKILL.md
├── critique-reviewer/             # 质量审查官 · 严过审
│   └── SKILL.md
└── export-specialist/             # 导出交付专家 · 交付达
    └── SKILL.md
```

## 角色职责一览

| 文件 | 角色 | 核心产出 |
|------|------|----------|
| `design-engine-team-lead` | 主理人 | 编排 SOP 流程，中转各阶段产出 |
| `discovery-analyst` | 许明需 | 结构化需求摘要（五要素） |
| `design-system-expert` | 彩格调 | 设计系统推荐 + 设计令牌文档 |
| `prototype-builder` | 筑原型 | HTML/CSS 原型代码 |
| `critique-reviewer` | 严过审 | 5 维评审报告 + Anti-Slop 检测 |
| `export-specialist` | 交付达 | 最终交付文件（HTML/PDF/PPTX） |

## 标准工作流

```
Phase 1 ── discovery-analyst → 需求摘要
Phase 2 ── design-system-expert → 设计令牌
Phase 3 ── prototype-builder → HTML/CSS 原型
Phase 4 ── critique-reviewer → 评审报告（可循环修正 2 轮）
Phase 5 ── export-specialist → 最终导出文件
Phase 6 ── 主理人汇总交付
```

## 配套知识库 Skill（已存在）

设计原型团队还依赖以下已有 Skill 知识库：
- `design-systems` — 71 套品牌级设计系统
- `prototype-templates` — 9 种原型模板结构定义
- `quality-review` — 5 维度评审框架详情

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
