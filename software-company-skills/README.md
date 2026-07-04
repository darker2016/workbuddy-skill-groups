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
