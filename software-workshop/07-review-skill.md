# Review Skill — PR 代码审查

> 面向预合入（pre-landing）的代码审查。分析当前分支的 diff，发现测试无法捕获的结构性问题。
> 7 位专家子审查员并行分析：api-contract, data-migration, maintainability, performance, red-team, security, testing。

---

## 触发词

- code review
- PR review
- pre-landing review
- diff review

---

## 专家子审查员

| 专家 | 聚焦领域 | 说明文件 |
|------|---------|---------|
| **api-contract** | API 契约审查 | 检查 API 端点签名、参数类型、响应格式是否与已有契约一致 |
| **data-migration** | 数据迁移安全 | 检查数据迁移脚本的安全性和正确性 |
| **maintainability** | 代码可维护性 | 检查复杂度、命名、模块结构、重复代码 |
| **performance** | 性能审查 | 检查性能敏感路径、资源使用、算法复杂度 |
| **red-team** | 红队攻击视角 | 从攻击者角度寻找可利用的弱点 |
| **security** | 安全深度审查 | 安全漏洞深度分析 |
| **testing** | 测试覆盖审查 | 审查变更对应的测试覆盖是否充分 |

---

## 工作流

### 1. Check branch
验证当前分支和基准分支。

### 2. Get the diff
```bash
git diff <base-branch>
```

### 3. Critical pass
检查清单中的 CRITICAL 和 INFORMATIONAL 问题。

### 4. Specialist dispatch
检测 diff 涉及的栈/范围，选择相关专家并行分发，合并发现结果并基于指纹去重。

### 5. Fix-first review
分类为 `AUTO-FIX` 和 `ASK` 两项：
- AUTO-FIX 项：自动修复
- ASK 项：批量提问

### 6. TODOS cross-reference
检查发现是否与现有 TODOS 相关联。

### 7. Documentation staleness
标记可能因本次 diff 而过时的文档。

### 8. Output
结构化审查输出。

---

## 输出格式

每个发现包含：

```yaml
Severity: CRITICAL / WARNING / INFO
Confidence: 0-10
Fingerprint: <去重唯一标识>
File: <文件路径:行号范围>
Description: <问题描述>
Recommended fix: <推荐修复>
```

---

## 使用方式

在代码审查场景中，主理人将 `review` skill 分配给 `gstack-product-reviewer`，product-reviewer 会在审查时自动调用本 skill 及 7 位子审查员。

---

> 本 Skill 定义源自 GStack 软件工坊插件 `skills/review/SKILL.md`
