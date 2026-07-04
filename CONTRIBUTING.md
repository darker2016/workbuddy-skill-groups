# 如何参与

欢迎任何能提高本仓库 **skill 复用性 / 团队互操作性 / 可读性 / 可移植性** 的贡献。所有贡献将被视为默认遵循 [LICENSE](../LICENSE) 中的 MIT 条款（涉及原始作者 attribution 的部分仍须保留）。

## 贡献类别

### 1. 事实修复

如果你发现某个 skill 的 `SKILL.md` 内容已与团队实际不一致、或与原始 WorkBuddy 描述冲突 → 请开 Pull Request 或 Issue，并说明你预期正确的内容（引用源为佳）。

### 2. 英文翻译

本仓库每个 skill 都配有 `README.md`。部分 skill 暂无英文版 `/README.en.md`，欢迎贡献：

- 请在 skill 目录内写一个同名 `README.en.md`
- **章节号必须** 与 `README.zh.md` 一致（例如中文"## 描述" → 英文"## Description"）
- **保留中文原段落标题的章节编号锚点** (`<a id="...">`)，便于交叉引用

### 3. SOP 模板化

多 skill 共享的"主理人检查单 / member 返工契约 / Gate 清单 / 错误处理约定"，建议提取到根目录 `_templates/` 中。例如：

```
_templates/
├── team-lead-sop.md           # 主理人通用 SOP 模板
├── member-rework-contract.md   # 子 agent 通用返工契约
├── gate-checklist.md           # 阶段 Gate 模板
└── error-handling.md           # 错误恢复模板
```

提取时请在 PR 中列出：来源 skill、适配目标 skill。

### 4. 框架迁移示例

WorkBuddy 原生 skill 里的工具调用不能直接在其它平台跑。你可以提交轻量示例：

```
examples/
├── crewai/
│   └── stock-partner-crewai.ipynb
├── langchain/
│   └── mvp-dev-langchain.py
└── dify/
    └── ket-prep-dify.md
```

示例请满足：**可独立运行**、**不内嵌任何 token / API key**。

### 5. Attribution 与署名维护

衍生 README / 示例 / 翻译时，必须在显著位置保留：

- 原始作者 ID（如 `name: chatlaw-team-lead`）
- 原始作者名（Tk · 林律师 / 花叔 等）
- 原始链接（GitHub 仓库 / WorkBuddy skill 卡片）

**禁止移除、拼写错误或替换原始作者 attribution。**

## 提交约定

1. **PR 正文模板**：列出你影响的 folders、新增的 templates、移除的硬编码 tool-call 等信息。
2. **Branch 命名**：`fix/<skill>-<short>`、`trans/<skill>-en`、`tmpl/<name>`、`ex/<framework>` 之一。
3. **敏感信息**：**禁止提交** 商业账号 id、内部 API token、API key、外部服务的私有凭据。
4. **不得夹带** WorkBuddy 平台的商业付费编排代码（仅公开技能描述 / SOP 允许）。

## 版权与 Liability

贡献即表示你确认：

- 你拥有所提交内容的版权，或相关权利人允许你按 MIT 开源
- 你未曾通过破解、反编译、抓包、逆向等手段获取相关内容
- 你已阅读并同意 LICENSE 中的免责条款

如有任何疑问（例如"我能 fork 这套 skill 做付费产品吗"），请先开 Issue 讨论再开 PR。

## 联系

- Open an Issue → 最快、默认可见
- GitHub Discussion → 适合提议性话题（如"要不要增加 xx 类 skill"）
