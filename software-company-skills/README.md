# 软件开发团队 Skill 文档 — 交付概览

## 生成内容

完整复刻了系统提示词中定义的软件开发团队，生成 **5 个 Skill MD 文档**：

| 角色 | 文件名 | 核心职责 |
|------|--------|----------|
| 🎯 **主理人（齐活林）** | `software-team-lead/SKILL.md` | 协调整个工作流，判断路由（快速模式/BugFix/标准SOP），分派成员，中转信息，执行质量门禁 |
| 📋 **产品经理（许清楚）** | `software-product-manager/SKILL.md` | 撰写 PRD（简单/完整两种模式），用户故事，需求优先级（P0/P1/P2），UI 设计参考 |
| 🏗️ **架构师（高见远）** | `software-architect/SKILL.md` | 技术选型，系统架构设计，文件结构，数据结构/接口，时序图，任务分解（含依赖关系） |
| 💻 **工程师（寇豆码）** | `software-engineer/SKILL.md` | 批量编写全量代码，全局一致性审查（IS_PASS: YES/NO），代码质量守则 |
| ✅ **QA工程师（严过关）** | `software-qa-engineer/SKILL.md` | 编写测试用例，智能路由判定（Engineer/QA/NoOne），最多 2 轮测试，回归验证 |

## 文件结构

```
software-company-skills/
├── overview.md                                 # 本文件
├── software-team-lead/
│   └── SKILL.md                                # 主理人技能
├── software-product-manager/
│   └── SKILL.md                                # 产品经理技能
├── software-architect/
│   └── SKILL.md                                # 架构师技能
├── software-engineer/
│   └── SKILL.md                                # 工程师技能
└── software-qa-engineer/
    └── SKILL.md                                # QA工程师技能
```

## 文档特色

- **贴近系统提示词源码**：核心流程、工作流路由（快速模式/BugFix/标准SOP）、团队协作铁律均忠实复现
- **可直接安装为 WorkBuddy Skill**：每个文档均包含标准 frontmatter（`name`、`description`、`agent_created: true`）
- **输出模板即用**：每个角色都内置了完整的 Markdown 输出模板（PRD 模板、架构设计模板、审查报告模板、测试报告模板）
- **中英双语 Agent ID 支持**：使用 `software-` 前缀的规范命名，与系统提示词中的 Agent ID 一致

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
