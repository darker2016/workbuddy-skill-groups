# 视频创作团队技能文档包 — 已完成

基于 VideoGenTeam 专家定义生成的完整技能文档，共 **5 份主文档 + 3 份参考资料**。

## 文档清单

### 主文档（5 份）

| 编号 | 文件名 | 对应角色 | 核心内容 |
|------|--------|---------|---------|
| 00 | `team-playbook.md` | 全团队 | 完整 SOP、角色分工、调度机制、质检规范、环境依赖 |
| 01 | `video-team-lead-skill.md` | 主理人/凌导 | 团队创建、成员调度、任务编排、质检、交付流程 |
| 02 | `ling-reader-collector-skill.md` | 灵阅/采集员 | feedgrab+multi-search 工具链、采集策略、输出模板 |
| 03 | `ling-planner-scriptwriter-skill.md` | 灵枢/策划师 | 选题评估、脚本写作、分镜设计、JSON 制作包规范 |
| 04 | `ling-producer-renderer-skill.md` | 灵映/制作师 | edge-tts/HyperFrames 渲染链、字幕、质检、排错 |

### 参考资料（3 份）

| 文件名 | 说明 |
|--------|------|
| `references/output-template.md` | 采集报告输出格式模板 |
| `references/hyperframes-html-spec.md` | HyperFrames HTML 结构规范 |
| `references/style-backgrounds.md` | 视频风格背景模板与 CSS |

## 存放位置

```
/Users/darker/WorkBuddy/2026-07-04-19-15-22/video-gen-team-skills/
├── 00-team-playbook.md
├── 01-video-team-lead-skill.md
├── 02-ling-reader-collector-skill.md
├── 03-ling-planner-scriptwriter-skill.md
├── 04-ling-producer-renderer-skill.md
└── references/
    ├── output-template.md
    ├── hyperframes-html-spec.md
    └── style-backgrounds.md
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
