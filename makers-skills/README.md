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
