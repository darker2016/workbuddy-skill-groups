# Design HTML Skill — 生产级 HTML/CSS 生成

> 使用 Pretext 框架生成生产级 HTML/CSS。支持从零构建或基于已批准的设计稿。
> 30KB 框架开销，零外部依赖。

---

## 触发词

- design to HTML
- implement design
- generate HTML CSS
- design implementation

---

## 关键特性

- 30KB 框架开销，零外部依赖
- 智能 API 路由：为每种设计类型选择正确的 Pretext 模式
- 自包含输出文件（HTML + CSS 内嵌）
- 移动端响应式布局
- 语义化、干净的标记

---

## Vendor

| 文件 | 说明 |
|------|------|
| `vendor/pretext.js` | Pretext 框架库 |

---

## 工作流

### 1. Input
接收设计上下文（设计稿描述、DESIGN.md 引用、产品评审输出等）。

### 2. Pattern selection
根据设计类型选择合适的 Pretext 模式。

### 3. Generate HTML/CSS
使用 Pretext 框架生成生产级输出。

### 4. Verify
检查输出渲染是否正确，是否符合设计意图。

### 5. Deliver
写入最终 HTML/CSS 文件。

---

## 输出

- 自包含 HTML 文件（CSS 内嵌）
- 移动端响应式布局
- 干净的语义化标记
- 正确应用的 Pretext 框架模式

---

## 使用方式

在以下场景中使用：

| 场景 | 详见 |
|------|------|
| 设计系统预览 | `05-gstack-designer-agent.md` — Design Consultation Phase 5 |
| 设计变体探索 | `05-gstack-designer-agent.md` — Design Shotgun |
| 设计落地实现 | 主理人调度 designer 时，直接引用此 skill |

---

> 本 Skill 定义源自 GStack 软件工坊插件 `skills/design-html/SKILL.md`
