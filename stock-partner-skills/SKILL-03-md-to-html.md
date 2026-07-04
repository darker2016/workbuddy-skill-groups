---
name: md-to-html
description: 圆桌报告 HTML 渲染技能 — 把主理人写的 body 片段套进 shell.html，输出完整可分享的 HTML 报告（含 CSS + 头像 base64 内嵌）
---

# md-to-html — 圆桌报告 HTML 渲染技能

> **作用**：把主理人写的 HTML body 片段套进 `shell.html`，输出最终 `<主题>-圆桌报告.html`（含完整 CSS + 嵌入头像）
> **何时调用**：主理人写完 `<主题>-圆桌报告.md` 后，按 components.md 写 body 片段，调用 `scripts/render.py`

---

## 一、文件清单

| 文件 | 谁读 | 作用 |
|------|------|------|
| `SKILL.md`（本文） | agent | 调用入口 |
| `components.md` | **agent 必读** | 组件 API 手册（class + HTML 模板） |
| `avatar-mapping.md` | **agent 必读** | 中文头衔 ↔ 头像文件名映射 |
| `shell.html` | 仅 render.py | 外壳模板（含全部 CSS） |
| `scripts/render.py` | agent 调用 | 注入器：body 片段 → 完整 HTML |
| `scripts/embed_avatars.py` | render.py 自动调用 | 把头像 png 嵌成 base64 |

---

## 二、工作流（agent 视角）

```
步骤1：读 components.md → 了解7个区块的 class 与 HTML 模板
步骤2：读 avatar-mapping.md → 知道头像 src 写法
步骤3：写 body 片段 <主题>-圆桌报告.body.html
       （含 nav + hero + 4 模块，不含 <head>/<style>/<footer>）
步骤4：跑 render.py 合成最终 HTML
```

### render.py 调用命令

```bash
python3 <SKILL目录>/scripts/render.py \
  deliverables/stock-partner/<YYYY-MM-DD>/<主题>-圆桌报告.body.html \
  deliverables/stock-partner/<YYYY-MM-DD>/<主题>-圆桌报告.html \
  --title="<主题> · 腾讯自选股股票投研圆桌报告" \
  --date=<YYYY-MM-DD>
```

`render.py` 会自动：
- 调 `scripts/embed_avatars.py` 把头像替换成 base64
- 渲染成功后**删除 body 片段文件**（加 `--keep-body` 保留）

---

## 三、Body 片段自检清单

- [ ] `<nav>` 4 个锚点齐：`#conclusion` / `#voices` / `#thinking` / `#watch`
- [ ] `<section class="hero">` 包含 `.kicker` / `<h1>` / `.hero-dek` / `.host`
- [ ] Module 1：`<section id="conclusion">` 含五件套（question/snapshot/headline/actions/vote）
- [ ] Module 2：每位上场成员一张 `.voice-card`，容器 `.voice-stack`
- [ ] Module 3：`#thinking` 内含 3a `.notes-stack` + 3b `.qa-stack`
- [ ] Module 4：`#watch` 内含 4a `.trigger-table` + 4b `.notes-stack`
- [ ] body **不写 `<style>`**、**不写 `<footer>`**、**不写 `<head>`**
- [ ] 涨跌着色对：`.cc-snap-up` / `.up` 红、`.cc-snap-down` / `.down` 绿
- [ ] 头像 src 都是 `avatars/<kebab>.png` 形式（不是绝对路径）

---

## 四、Body 片段的 7 个区块

按出现顺序：

```
1. <nav>                  导航条           固定 4 个锚点
2. .hero                  封面             报告标题 + 副标题 + 主理人署名
3. .conclusion-card       Module 1 · 结论  conclusion-card 组件
4. <section id="voices">  Module 2 · 视角  voice-card × N
5. <section id="thinking"> Module 3 · 思考  notes-stack + qa-stack
6. <section id="watch">   Module 4 · 关注  trigger-table + notes-stack
7. （可选）.passage-card  非标内容兜底      M1-4 装不下时用
```

### 全局规则

- **头像**：所有 `<img src="avatars/<file>.png">` 由 `embed_avatars.py` 自动嵌成 base64
- **涨红跌绿**：`.cc-snap-up` / `.up` 红（涨），`.cc-snap-down` / `.down` 绿（跌）——中国股市习惯
- **强调色**：`.cc-headline` 内关键判断词 `<strong>` 加粗，核心字眼 `<em>` 染红（每段2-3处）
- **不要写 `<style>`**：CSS 全在 shell 里

---

## 五、Q&A 类型标签

| Class | 文字 | 颜色 |
|-------|------|------|
| `.tag-key` | 🔑 关键 | 金 |
| `.tag-confuse` | ⚠️ 易混淆 | 红 |
| `.tag-miss` | 🔍 易疏忽 | 蓝 |
| `.tag-meta` | ⭐ 重要 | 紫 |

---

## 六、排错指南

| 问题 | 可能原因 |
|------|---------|
| render.py 报"shell.html 缺少占位符" | shell.html 被改坏，应有 `{{TITLE}}`/`{{BODY}}`/`{{DATE}}` |
| embed_avatars 警告"头像文件缺失" | src 拼错了或对应 png 不存在，检查 avatar-mapping.md |
| CSS 错位 / 视觉跑偏 | body 片段用了 components.md 之外的 class，或写了自定 `<style>` |

---

## 七、不变量（agent 自检）

- body 片段里**不含** `<!DOCTYPE>` / `<html>` / `<head>` / `<style>` / `<body>` / `<footer>` 标签
- body 片段以 `<nav>` 开头，以最后一个 `</section>` 结尾
- `<img>` 头像 src 全部是 `avatars/<kebab>.png` 形式
- 4 个模块 ID 固定：`#conclusion` / `#voices` / `#thinking` / `#watch`

不满足任一条 = body 不合规，render.py 仍能生成 HTML 但效果会出错。
