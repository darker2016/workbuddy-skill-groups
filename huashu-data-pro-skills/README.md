# 花叔数据分析专家团 · 完整技能包

> 面向「一人公司 / 超级个体」的三视角并行数据分析专家团。

## 包结构

```
huashu-data-pro/
├── README.md                         ← 本文件：团队总览
├── huashu-data-pro-team-lead/
│   └── SKILL.md                      ← 主理人技能：调度与合成
├── trend-analyst/
│   └── SKILL.md                      ← 趋势分析师技能
├── structure-analyst/
│   └── SKILL.md                      ← 结构分析师技能
└── anomaly-analyst/
    └── SKILL.md                      ← 异常侦察员技能
```

## 团队角色

| Agent | Skill 文件 | 职责 |
|-------|-----------|------|
| **主理人 (team-lead)** | `huashu-data-pro-team-lead/SKILL.md` | 听清问题 → 建立团队 → 并行调度 → 等待回传 → 合成报告 → 三格式交付 |
| **趋势分析师 (trend-analyst)** | `trend-analyst/SKILL.md` | 时间序列分析：增长曲线、拐点、季节性、环比/同比 |
| **结构分析师 (structure-analyst)** | `structure-analyst/SKILL.md` | 占比拆解：帕累托分析、因子贡献度、多表交叉、维度对比 |
| **异常侦察员 (anomaly-analyst)** | `anomaly-analyst/SKILL.md` | 异常检测：3σ 离群点、IQR 异常值、突变检测、缺失值、重复记录 |

## 标准工作流

```
用户提出数据分析需求
       ↓
Step 1: 主理人确认三件事（数据是什么 / 关心什么 / 给谁看）
       ↓
Step 2: TeamCreate 建立团队
       ↓
Step 3: 数据摸底（读文件、识别工作表、抽样）
       ↓
Step 4: AgentTool 并行调度 3 位成员（trend + structure + anomaly）
       ↓
Step 5: 等待 3 位成员通过 SendMessage 回传结构化发现
       ↓
Step 6: 主理人合成报告（整体洞察 → 趋势 → 结构 → 异常 → 行动建议）
       ↓
Step 7: 三格式交付（HTML + XLSX + PPTX）
```

## 输出产物

| 格式 | 用途 |
|------|------|
| **HTML** | 交互式报告，适合自己看细节 |
| **XLSX** | 含数据透视表，适合给财务复核 |
| **PPTX** | 幻灯片格式，适合直接拉去开会 |

默认三种全出。用户也可以指定只出某一种或两种。

## 协作铁律

1. ✅ TeamCreate 必须由主理人执行
2. ✅ 成员独立输出，主理人不得代写
3. ✅ 先建团队 → 再调度 → 再等待 → 再合成，步骤不可跳过
4. ✅ 成员不能直接与用户对话
5. ✅ 主理人不能把自己作为成员调度
6. ✅ 等待全部成员回传后再合成，除非某成员超时/失败

## 核心理念

> **三个视角同时看一份数据，永远比一个视角反复看好。**
>
> 数据分析的难点从来不是「看到一个数」，而是「看到一个数之后能不能从多个视角同时解读」。
> 花叔数据分析专家团就是把这件原本需要一整个数据团队才能做的事，搬到一台笔记本里。

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
