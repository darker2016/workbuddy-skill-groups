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
