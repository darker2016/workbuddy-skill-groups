# academic-journal-selector-skills（学术选刊顾问团 v3.0）

> **来源**：本 skill 由用户在 WorkBuddy 平台官方渠道、通过自己个人账号、以普通对话方式生成。
> 未使用破解安装包 / 获取应用文件夹内文件 / 反编译 / 抓包 / 模型 API 调用数据逆向等技术手段。
> 不保证与 WorkBuddy 原版 100% 一致（平台侧可能更新，生成结果受 prompt / 模型版本影响）。

## 描述

并行双管道架构的选刊专家团，中文刊和外文刊独立匹配 + 安全检测，输出冲稳保三层投稿建议。

## 团队成员

| ID | 角色 | 名称(若文件中有) |
|----|------|-----------------|
| `academic-journal-selector-team-lead/SKILL.md` | **(主理人)** | academic-journal-selector-team-lead |
| `cn-pipeline-matcher/SKILL.md` | 成员 | cn-pipeline-matcher |
| `cn-pipeline-scout/SKILL.md` | 成员 | cn-pipeline-scout |
| `en-pipeline-matcher/SKILL.md` | 成员 | en-pipeline-matcher |
| `en-pipeline-scout/SKILL.md` | 成员 | en-pipeline-scout |
| `paper-reviewer/SKILL.md` | 成员 | paper-reviewer |
## 工作流阶段

双管道（CN / EN）→ 学科匹配 → 情报检索 → 安全检测 → 冲稳保方案。

## 使用

把 `academic-journal-selector-team-lead/SKILL.md` 作为主理人的系统提示加载。本仓"主理人文件"为 `academic-journal-selector-team-lead/SKILL.md`。

## 目录结构

```
academic-journal-selector-team-lead/
cn-pipeline-matcher/
cn-pipeline-scout/
en-pipeline-matcher/
en-pipeline-scout/
paper-reviewer/
```
