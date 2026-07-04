---
name: makers-deploy
description: >-
  Makers 开发专家团部署 Skill — 将前端/全栈项目部署到 EdgeOne Makers。
  包含 CLI 安装、登录鉴权、一键部署、JSON 输出解析、URL 铁律。
  触发词：部署、发布、上线、发版、deploy、publish、go live、
  重新部署、deploy to EdgeOne。
  当执行 edgeone makers deploy 命令时必须加载此 skill。
metadata:
  author: edgeone-makers
  version: "2.1.0"
---

# EdgeOne Makers 部署 Skill

将任何项目部署到 **EdgeOne Makers**。

## ⛔ 铁律（不可跳过）

1. **CLI 版本 >= `1.6.7`**——低于此版本在非交互环境会卡住
2. **绝不截断部署 URL**——完整 URL 含鉴权查询参数，省略导致 401
3. **非交互环境用 `--json`**——输出单行机器可读 JSON
4. **部署地址必须醒目展示**——放在回复最前面，用大标题 + 代码块
5. **部署前先问站点选择**——China / Global
6. **桌面环境用浏览器登录，无头环境用 Token 登录**

---

## 环境准备

在任何 `edgeone` 命令之前设置：
```bash
export PAGES_SOURCE=skills
```

### 检测步骤

```bash
# 1. CLI 版本检测
edgeone -v    # 必须 >= 1.6.7

# 2. 登录状态检测（CLI >= 1.6.7 会快速失败，不会卡住）
edgeone whoami

# 3. 项目关联检测
cat .edgeone/project.json 2>/dev/null && echo "LINKED" || echo "NOT LINKED"
```

### 决策表

| CLI 版本 | 登录状态 | 操作 |
|----------|---------|------|
| 未安装或 < 1.6.7 | — | → 安装 CLI |
| >= 1.6.7 ✓ | 已登录或 token 存在 | → 部署 |
| >= 1.6.7 ✓ | 未登录，桌面环境 | → 浏览器登录 |
| >= 1.6.7 ✓ | 未登录，无头环境 | → 让用户提供 token |

---

## 安装 CLI

```bash
npm install -g edgeone@latest
edgeone -v    # 验证 >= 1.6.7
```

## 登录

### 浏览器登录（推荐）
```bash
# 先询问用户选择站点
edgeone login --site china --local    # 国内站
edgeone login --site global --local   # 国际站
```

### Token 登录（降级方案）
```bash
edgeone login --token <token> --local
```

Token 获取方式：
- **国内站**：https://console.cloud.tencent.com/edgeone/pages?tab=settings
- **国际站**：https://console.intl.cloud.tencent.com/edgeone/pages?tab=settings

---

## 部署命令

### Web 项目（无 `agents/` 目录）
```bash
# 已链接项目
edgeone makers deploy -t <token> --json

# 新项目
edgeone makers deploy -n <project-name> -t <token> --json

# 预览环境
edgeone makers deploy -n <project-name> -t <token> --json -e preview
```

### Agent 项目（有 `agents/` 目录）
```bash
# edgeone makers deploy 自动执行 build + 部署
edgeone makers deploy -n <project-name> -t <token> --json

# 预览环境
edgeone makers deploy -n <project-name> -t <token> --json -e preview
```

**部署命令必须前台同步执行**（不加 `run_in_background`）。部署通常 1-3 分钟。

---

## 解析部署输出

成功时 stdout 最后一行是 JSON：
```json
{"status":"success","url":"https://xxx.edgeone.cool?eo_token=...","projectId":"pages-xxx","deploymentId":"dp-xxx","consoleUrl":"https://..."}
```

失败时：
```json
{"status":"error","error":"<message>"}
```

## URL 铁律

**🌐 线上地址：`https://xxx.edgeone.cool?eo_token=xxx&eo_time=xxx`**

- 绝不截断 URL 的查询参数（`eo_token`、`eo_time`）
- 告知用户该 URL 含时效性鉴权参数，分享链接可能失效
- 如需长期公开访问，请在控制台绑定自定义域名

## 错误处理

| 错误 | 解决方案 |
|------|----------|
| `command not found: edgeone` | `npm install -g edgeone@latest` |
| CLI 版本 < 1.6.7 | 重新安装 `npm install -g edgeone@latest` |
| 浏览器无法打开 | 切换到 token 登录 |
| "not authenticated" | 运行登录或提供 token |
| 部署卡在 "Deploying..." | CLI >= 1.6.7 非 TTY 会发心跳，未卡住；用 `--json` |
| Token 认证错误 | Token 可能过期，去控制台重新生成 |
| 项目名冲突 | 用 `-n` 换一个名字 |
| 项目配额超限 | 到控制台清理不再需要的旧项目 |
