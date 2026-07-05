# 福帮手超级合伙人技能包

这个技能包集合完整复制了 FBSir 超级合伙人团队的系统能力。包含 11 个 SKILL.md 文件，覆盖从入口路由到交付落地的全链路。

## 技能总览

### 核心与系统级（7 个）

| 技能名 | 文件 | 用途 |
|--------|------|------|
| **super-partner-core** | `super-partner-core/SKILL.md` | 核心执行合同：团队结构、协作机制、首值合同、能力簇路由、语言合同 |
| **super-partner-entry-routing** | `super-partner-entry-routing/SKILL.md` | 入口路由与分派：场景识别、问题簇映射、teamMode 选择、建立团队 |
| **super-partner-company-next-step** | `super-partner-company-next-step/SKILL.md` | "公司下一步"主工作流：单成员直调 + 唐老收口 |
| **super-partner-multi-workshop** | `super-partner-multi-workshop/SKILL.md` | 多维度协同工作坊：四成员并行 + 综合裁决 |
| **super-partner-genius-draft** | `super-partner-genius-draft/SKILL.md` | 天才合伙人草案：行业补位、C6 能力簇完整定义 |
| **super-partner-fbs-followthrough** | `super-partner-fbs-followthrough/SKILL.md` | 福帮手服务跟进链路：whoami → scene_pack_query → consume |
| **super-partner-lebao-activation** | `super-partner-lebao-activation/SKILL.md` | 乐包激活与能力继续：解锁、激活、行动转化 |

### 成员独立技能（4 个）

| 技能名 | 文件 | 对应角色 |
|--------|------|---------|
| **super-partner-strategy-member** | `super-partner-strategy-member/SKILL.md` | 老孙 — 战略与机会合伙人 |
| **super-partner-ops-member** | `super-partner-ops-member/SKILL.md` | 老朱 — 组织与运营合伙人 |
| **super-partner-growth-member** | `super-partner-growth-member/SKILL.md` | 老沙 — 增长与商业化合伙人 |
| **super-partner-product-member** | `super-partner-product-member/SKILL.md` | 小白 — 产品与智能化合伙人 |

## 团队协作架构

```
用户输入
    │
    ▼
┌────────────────────────────────────────────┐
│  super-partner-entry-routing                │
│  识别场景 → 选择 teamMode → 建立团队        │
└────────────┬───────────────────────────────┘
             │
    ┌────────┴──────────┬──────────────┐
    ▼                   ▼              ▼
┌─────────┐  ┌────────────────┐  ┌──────────┐
│ 单成员  │  │ 多维工作坊      │  │ 天才合伙人│
│ 直调    │  │ 并行调度       │  │ 草案生成  │
└────┬───┘  └───────┬────────┘  └─────┬────┘
     │              │                 │
     ▼              ▼                 ▼
┌────────────────────────────────────────────┐
│  唐老收口 → 结果卡 + 唯一下一步            │
└────────────┬───────────────────────────────┘
             │
    ┌────────┴──────────┐
    ▼                   ▼
┌──────────┐   ┌──────────────┐
│ 首值完成 │   │ fbs-follow   │
│          │   │ through      │
│          │   │ (后首值增强)  │
└──────────┘   └──────────────┘
```

## 能力簇体系

| 簇 ID | 角色 | 名称 |
|-------|------|------|
| C1 | 唐老 | 路由与状态管理 |
| C2 | 老孙 | 战略与机会 |
| C3 | 老朱 | 组织与运营 |
| C4 | 老沙 | 增长与商业化 |
| C5 | 小白 | 产品与智能化 |
| C6 | 小白 | 天才合伙人工厂 |

## 使用方式

每个 SKILL.md 文件都是一个自包含的技能定义，可以作为 WorkBuddy 的 Skill 加载使用。加载方式：

```
Skill({
  skill: "super-partner-core"  // 或其它技能名
})
```

## 源插件

这个技能包基于插件 `fbsir-super-partner-group@1.3.0` 的完整定义生成。原始 Agent 定义位于 `agents/` 目录下，包含 5 个成员的完整 MD 文件。

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
