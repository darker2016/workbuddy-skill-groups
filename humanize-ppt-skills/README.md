# 卡尔的人感 PPT 专家团 — Skill 文档总览

> 生成时间：2026-07-04  
> 总计 **76 个文档文件**，覆盖 5 大 Skill 及其完整参考体系

---

## 目录结构

```
humanize-ppt-skills/
├── overview.md                                   ← 本文档
├── humanize-ppt/          (大纲导演 - AST 生产契约)
│   ├── SKILL.md                                  ← 核心 skill 定义
│   ├── README.md / README.en.md                  ← 项目说明
│   ├── contracts/                                ← 6 份生产契约模板
│   │   ├── deck-brief.template.md
│   │   ├── ast-outline.schema.md
│   │   ├── slide-plan.schema.json
│   │   ├── speaker-intent.template.md
│   │   ├── asset-manifest.template.md
│   │   └── video-slots.schema.json
│   ├── adapters/                                 ← 下游适配器规范
│   │   ├── guizang-bridge-notes.md
│   │   ├── zara-bridge-notes.md
│   │   └── presenter-adapter-spec.md
│   ├── references/
│   │   └── agent-teams-public-preview.md
│   └── *.md (AST-theory, OPC-workflow, agent-teams, presenter-adapter, router-rules, index)
│
├── guizang-ppt-skill/    (电子杂志 × 电子墨水风格 HTML PPT)
│   ├── SKILL.md                                  ← 核心 skill 定义
│   ├── README.md / README.en.md / LICENSE
│   └── references/                               ← 完整参考体系
│       ├── themes.md                             (5 套主题色预设)
│       ├── layouts.md                            (10 种布局骨架)
│       ├── components.md                         (组件手册)
│       ├── checklist.md                          (质量检查清单)
│       ├── image-prompts.md                      (配图提示词)
│       ├── browser-validation-notes.md           (浏览器验证注意事项)
│       └── template-known-issues.md              (模板已知问题)
│
├── frontend-slides/      (风格探索与部署版 HTML Slides)
│   ├── SKILL.md                                  ← 核心 skill 定义
│   ├── STYLE_PRESETS.md                          (12 套视觉预设)
│   ├── viewport-base.css                         (必含响应式 CSS)
│   ├── html-template.md                          (HTML 架构指南)
│   ├── animation-patterns.md                     (动效模式参考)
│   ├── README.md
│   └── scripts/
│       ├── deploy.sh                             (Vercel 部署)
│       ├── export-pdf.sh                         (PDF 导出)
│       └── extract-pptx.py                       (PPT 内容提取)
│
├── html-ppt/             (HTML PPT Studio - 全功能演讲模式)
│   ├── SKILL.md                                  ← 核心 skill 定义
│   ├── README.md / README.zh-CN.md / LICENSE
│   └── references/                               ← 完整参考体系
│       ├── themes.md                             (36 套主题)
│       ├── layouts.md                            (31 种布局)
│       ├── animations.md                         (27 CSS + 20 Canvas 动效)
│       ├── full-decks.md                         (15 个全 deck 模板)
│       ├── presenter-mode.md                     (演讲者模式指南)
│       └── authoring-guide.md                    (完整编写指南)
│
└── remotion-video-toolkit/  (程序化视频生成 - Remotion)
    ├── SKILL.md                                  ← 核心 skill 定义
    ├── _meta.json
    └── rules/                                    ← 29 条规则
        ├── compositions.md / rendering.md / calculate-metadata.md
        ├── animations.md / timing.md / sequencing.md / transitions.md / trimming.md
        ├── text-animations.md / fonts.md / measuring-text.md
        ├── videos.md / audio.md / images.md / gifs.md / assets.md / can-decode.md
        ├── transcribe-captions.md / display-captions.md / import-srt-captions.md
        ├── charts.md
        ├── 3d.md / lottie.md / tailwind.md / measuring-dom-nodes.md
        ├── get-video-duration.md / get-video-dimensions.md / get-audio-duration.md / extract-frames.md
        └── assets/ (示例代码: charts-bar-chart.tsx, text-animations-typewriter.tsx, text-animations-word-highlight.tsx)
```

---

## Skill 协作关系

```
用户原始材料
    │
    ▼
┌─────────────────────────────────────┐
│  humanize-ppt  (大纲导演)            │
│  输出: deck_brief / ast_outline /    │
│        slide_plan / speaker_intent / │
│        asset_manifest / video_slots  │
└──────────────┬──────────────────────┘
               │
    ┌──────────┼──────────┐
    ▼          ▼          ▼
┌────────┐ ┌────────┐ ┌──────────────┐
│guizang │ │frontend│ │remotion-     │
│-ppt-   │ │-slides │ │video-toolkit │
│skill   │ │        │ │ (视频动效)   │
│(中文   │ │(风格   │ │              │
│ 稳定版)│ │ 探索)  │ │              │
└───┬────┘ └───┬────┘ └──────────────┘
    │          │
    └──────────┘
          │
          ▼
    ┌──────────┐
    │ html-ppt │
    │ (演讲者  │
    │  模式)   │
    └──────────┘
```

---

## 文件来源

> 原始位置：`/Users/darker/.workbuddy/plugins/marketplaces/experts/plugins/humanize-ppt-team/skills/*`
> 
> 共 323 个文件（含 HTML 模板、JS 运行时、CSS 主题、PNG 截图等），本目录提取了其中的 **76 个核心文档文件**（.md / .json / .css / .py / .sh）

未包含的文件类型（如需完整包可再生成）：
- HTML 模板文件（template.html, deck.html, showcase 等）
- JS 运行时文件（runtime.js, fx-runtime.js, fx/*.js 等）
- 35 个 CSS 主题文件（html-ppt/assets/themes/*.css）
- 15 个全 deck 模板（html-ppt/templates/full-decks/*/）
- 31 个单页布局模板（html-ppt/templates/single-page/*.html）
- PNG 截图验证文件

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
