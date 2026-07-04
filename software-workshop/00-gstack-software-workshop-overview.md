# GStack 软件工坊 — 完整系统概览

> 软件工坊（Software Workshop）是一个 AI 驱动的工程工作流工具包，覆盖从想法到生产的完整软件生命周期。

**版本**: 1.0.0
**类型**: 工程工作流团队（Engineering Workflow Team）
**创建日期**: 2026-07-03

---

## 系统架构

软件工坊由 **1 位主理人 + 5 位专业成员 + 3 个专用 Skill** 组成，采用 "主理人调度 → 专业成员执行 → 主理人汇编" 的协作模式。

```
用户请求
    │
    ▼
┌──────────────────────┐
│  gstack-lead (主理人) │  ← 沽思航 · 软件工坊 CEO
│  判断复杂度 + 路由调度  │
└───────┬──────────────┘
        │
        ├──→ gstack-product-reviewer (产品评审 · 6维度审查 + Autoplan)
        ├──→ gstack-security-officer (安全审计 · OWASP + STRIDE 14阶段)
        ├──→ gstack-qa-lead (质量测试 · QA → Ship → Canary → Deploy)
        ├──→ gstack-designer (设计系统 · 咨询 → 审查 → 变体探索 → HTML落地)
        └──→ gstack-investigator (排障运维 · 调试 → 健康 → Benchmark → Retro)
                │
                ▼
        主理人汇编 → 落盘报告
```

---

## 团队成员一览

| 代号 | 中文名 | 英文名 | 专业领域 |
|------|--------|--------|---------|
| `gstack-lead` | 沽思航 | Gu | 工程工作流编排、团队调度、报告汇编 |
| `gstack-product-reviewer` | 产品官 | Product Reviewer | 产品评审（Office Hours / CEO / Design / Eng / DX / Autoplan） |
| `gstack-security-officer` | 安全卫士 | Security Officer | OWASP Top 10 + STRIDE 威胁建模，14阶段安全审计 |
| `gstack-qa-lead` | 质量门神 | QA & Ship Lead | QA 测试（Quick/Standard/Exhaustive）、Ship 发布、Canary 监控、部署验证 |
| `gstack-designer` | 设计师 | Design Consultant | 设计系统创建、视觉审查、设计变体探索、HTML/CSS 落地 |
| `gstack-investigator` | 排障手 | Investigator | 系统化调试、代码健康评分、性能基准、回顾复盘、知识管理 |

---

## 可用 Skill

| Skill | 用途 | 说明 |
|-------|------|------|
| `review` | PR 代码审查 | 7 位专家子审查员并行分析（安全/SQL/API契约/性能/可维护性/红队/测试） |
| `qa` | QA 测试 | 3 级强度测试（Quick/Standard/Exhaustive），含 issue 分类学和报告模板 |
| `design-html` | 生产级 HTML/CSS | Pretext 框架，30KB 开销，零外部依赖 |

---

## 路由规则

| 用户意图 | 调度成员 |
|---------|---------|
| 产品评审、计划审查、Office Hours、autoplan | `gstack-product-reviewer` |
| 安全审计、威胁建模、OWASP、CSO | `gstack-security-officer` |
| 测试、发布、部署、Canary | `gstack-qa-lead` |
| 设计系统、视觉审查、设计变体 | `gstack-designer` |
| 调试、根因分析、健康检查、回顾 | `gstack-investigator` |
| 代码审查 / PR Review | `gstack-product-reviewer`（含 review skill） |
| QA 测试 + 修复 | `gstack-qa-lead`（含 qa skill） |
| 全流程（plan → code → review → ship） | 多成员顺序协作 |

---

## 协作模式

### 团队协作模式（复杂任务）
1. 主理人创建团队（TeamCreate）
2. 按需调度成员，下发独立任务
3. 消息经主理人中转，成员间不直连
4. 成员独立输出专业结论
5. 主理人汇编 → 落盘为 MD 报告

### 单Agent直调模式（简单/单一成员任务）
- 直接调用目标成员 Agent，无需 TeamCreate
- 主理人传递上下文 → 成员直接输出

---

## 落盘规范

- **存盘位置**: `{workspace}/deliverables/gstack/`
- **文件命名**: `<场景类型>-<主题简称>-<YYYY-MM-DD>.md`
- **必须包含**: TL;DR / 核心结论卡片 / 各成员核心结论 / 行动清单 / 免责声明
- **多成员场景强制落盘**

---

## 文件清单

本软件工坊文档包包含以下文件：

| 文件 | 内容 |
|------|------|
| `00-gstack-software-workshop-overview.md` | 本总览文档 |
| `01-gstack-lead-agent.md` | 主理人 Agent 定义 |
| `02-gstack-product-reviewer-agent.md` | 产品评审 Agent 定义 |
| `03-gstack-security-officer-agent.md` | 安全审计 Agent 定义 |
| `04-gstack-qa-lead-agent.md` | 质量门神 Agent 定义 |
| `05-gstack-designer-agent.md` | 设计顾问 Agent 定义 |
| `06-gstack-investigator-agent.md` | 排障手 Agent 定义 |
| `07-review-skill.md` | PR 代码审查 Skill |
| `08-qa-skill.md` | QA 测试 Skill |
| `09-design-html-skill.md` | 设计 HTML 落地 Skill |
| `10-qa-issue-taxonomy.md` | QA Issue 分类学（引用） |
| `11-qa-report-template.md` | QA 报告模板（引用） |

---

> 本文档由 GStack 软件工坊主理人生成，完整记录了软件工坊的系统定义、团队角色、Skill 规范和协作流程。
