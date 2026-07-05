# Makers 开发专家团 - Skill 包

完整复刻 WorkBuddy 中 Makers 开发专家团的 6 个核心 Skill，覆盖从需求分析、开发到部署的全流程。

## 团队成员

| Skill | 角色 | 名称 | 职责 |
|-------|------|------|------|
| `team-lead` | 主理人（交付总监） | 齐上线 (Qi) | 需求分析、技术选型、团队调度、本地预览、部署执行 |
| `frontend` | 前端工程师 | 裴知页 (Pei) | UI 页面、React/Vue/Next.js、静态资源、样式与动画 |
| `backend` | 后端工程师 | 范云申 (Fan) | Edge Functions、Cloud Functions (Node/Go/Python)、Middleware、KV/Blob |
| `agent` | AI Agent 工程师 | 智行远 (Zhi) | AI Agent 端点、5 大 LLM 框架集成、SSE 流式、conversation store |
| `deploy` | 部署 | — | CLI 安装、登录鉴权、一键部署、JSON 输出解析、URL 铁律 |
| `cli` | CLI 命令参考 | — | edgeone 全部命令速查、非交互 flag、环境变量管理 |

## Skill 说明

| 文件 | 用途 |
|------|------|
| `team-lead/SKILL.md` | 主理人编排 Skill — SOP 工作流、团队协作机制、部署流程 |
| `frontend/SKILL.md` | 前端开发 Skill — 框架选型、组件开发、关键约束 |
| `backend/SKILL.md` | 后端开发 Skill — Edge/Cloud Functions、Middleware、存储 |
| `agent/SKILL.md` | AI Agent 开发 Skill — 5 框架、SSE 协议、Store API |
| `deploy/SKILL.md` | 部署 Skill — CLI 安装、登录、部署命令、URL 铁律 |
| `cli/SKILL.md` | CLI 命令参考 Skill — 全部命令速查、非交互 flag |

## 使用方式

将对应 `SKILL.md` 的内容作为系统 prompt 加载到 AI Agent 中，即可获得对应角色的专业能力。

## 数据来源

本套 Skill 文档基于 [edgeone-makers-experts](https://github.com/TencentEdgeOne/edgeone-makers-tools) 插件和工作流程整理，完整保留所有关键约束、SOP 和铁律。

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
