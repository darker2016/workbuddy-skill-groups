# QA Skill — QA 测试

> 系统化 Web 应用测试：Test → Fix → Verify 循环。三种强度等级：Quick、Standard、Exhaustive。
> 含 issue 分类学和报告模板两个引用文件。

---

## 触发词

- QA test
- test the app
- find bugs
- smoke test
- regression test

---

## 测试模式

| 模式 | 说明 |
|------|------|
| **Quick** | 30 秒冒烟测试 |
| **Standard** | 系统性探索，5-10 个问题 |
| **Exhaustive** | 深度测试，全面覆盖 |
| **Regression** | 对比 baseline 回归测试 |
| **Diff-aware** | 从分支 diff 自动检测受影响页面 |

---

## 引用资源

| 文件 | 用途 |
|------|------|
| `references/issue-taxonomy.md` | Issue 分类学：Bug 类型分类 |
| `templates/qa-report-template.md` | 结构化 QA 报告模板 |

---

## 工作流

### 1. Initialize
解析 URL、等级、模式、范围。

### 2. Authenticate
处理登录/认证（如需要）。

### 3. Orient
映射应用结构，检测框架。

### 4. Explore
逐页清单检查：
- 视觉扫描
- 交互元素点击
- 表单测试
- 导航检查
- 状态检查（空态/加载态/错误态/溢出态）
- 控制台错误
- 响应式适配

### 5. Document
两层证据：交互式 Bug vs 静态 Bug。

### 6. Triage
按严重度排序，根据等级决定修复哪些。

### 7. Fix Loop
定位源码 → 最小修复 → 每个修复单个提交 → 重新测试 → 分类。

### 8. Final QA
重新运行 QA，计算最终健康评分。

### 9. Report
结构化报告。

---

## 输出

- 健康评分（0-100）
- 问题列表（含严重度、复现步骤、证据）
- Before/After 对比
- 发布就绪度评估

---

## Issue 分类学（摘要）

详见 `10-qa-issue-taxonomy.md`

### 严重度分级

| 级别 | 定义 | 举例 |
|------|------|------|
| **Critical** | 阻塞核心工作流、数据丢失、应用崩溃 |
| **High** | 主要功能不可用，无替代方案 |
| **Medium** | 功能可用但有明显问题，有替代方案 |
| **Low** | 轻微外观或修饰问题 |

### 分类

| 类别 | 包含 |
|------|------|
| Visual/UI | 布局断裂、图片缺失、z-index 错误、字体/颜色不一致 |
| Functional | 链接断裂、按钮无效、表单验证问题、状态不持久 |
| UX | 导航混乱、加载指示器缺失、错误消息不清晰 |
| Content | 拼写错误、文本过时、占位文本遗留 |
| Performance | 页面加载慢、滚动卡顿、布局偏移 |
| Console/Errors | JS 异常、网络请求失败、弃用警告 |
| Accessibility | 缺少 alt 文本、表单无标签、键盘导航损坏 |

---

> 本 Skill 定义源自 GStack 软件工坊插件 `skills/qa/SKILL.md`
