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
