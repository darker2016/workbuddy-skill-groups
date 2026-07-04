---
name: makers-cli
description: >-
  Makers 开发专家团 CLI 命令参考 Skill — EdgeOne CLI 全部命令速查、
  非交互 flag、环境变量管理、本地预览、build。
  触发词：CLI 命令、edgeone 命令、命令行参考、makers dev、
  makers build、makers deploy、env set、env ls。
metadata:
  author: edgeone-makers
  version: "1.0.0"
---

# EdgeOne Makers CLI 命令参考

## 安装

```bash
npm install -g edgeone
```

验证：`edgeone -v`（需要 >= 1.6.7）

## 环境变量

任何 `edgeone` 命令前设置：
```bash
export PAGES_SOURCE=skills
```
或内联：`PAGES_SOURCE=skills edgeone makers dev`

## 命令速查

| 命令 | 说明 | 非交互必备 flag |
|------|------|----------------|
| `edgeone makers dev` | 启动本地 dev server（agent runtime + 前端） | `--skip-env-sync` + `--name <project>` |
| `edgeone makers build` | 构建 agents + 前端到 `.edgeone/` | — |
| `edgeone makers deploy` | 构建并部署到 EdgeOne Makers | `--json` |
| `edgeone makers deploy -n <name>` | 作为新项目部署 | `--json` |
| `edgeone makers deploy -t <token>` | 用 API token 部署 | `--json` |
| `edgeone makers deploy -e preview` | 部署到预览环境 | `--json` |
| `edgeone makers link` | 关联本地项目到远端 | `--name <project>` |
| `edgeone makers env pull` | 拉取远端 env 到本地 `.env` | `--skip-env-sync` |
| `edgeone makers env set <K> <V>` | 设置远端环境变量 | — |
| `edgeone makers env ls` | 列出远端环境变量 | — |
| `edgeone makers env rm <KEY>` | 删除远端环境变量 | — |
| `edgeone login` | 浏览器登录 | `--site <china\|global>` |
| `edgeone login --token <t>` | Token 登录 | — |
| `edgeone whoami` | 检查登录状态 | — |

## 非交互 flag 汇总

| flag | 适用命令 | 说明 |
|------|---------|------|
| `--name <project>` | dev, deploy, link | 跳过交互式项目选择 |
| `--skip-env-sync` | dev, env pull | 跳过"是否拉取远端 env"确认 |
| `--json` | deploy | 机器可读 JSON 输出 |
| `-t <token>` | deploy | 跳过登录（Token 方式） |
| `-e preview` | deploy | 部署到预览环境 |

> ⛔ **最容易遗漏**：`edgeone makers dev` 必须带 `--skip-env-sync`，否则交互 prompt 卡死。

## 常用工作流

### 首次设置
```bash
npm install -g edgeone
edgeone login --site china --local
edgeone makers dev --name my-project --skip-env-sync
```

### 部署
```bash
edgeone makers deploy -n my-project -t <token> --json
```

### 设置环境变量
```bash
edgeone makers env set WSA_API_KEY "your-key"
edgeone makers env set SUPABASE_URL "https://xxx.supabase.co"
edgeone makers env ls
```

## 开发注意事项

### package.json dev script 陷阱

**NEVER** 设置 `"dev": "edgeone makers dev"`——CLI 启动时会读 `scripts.dev`，如果就是它自己会递归，导致前端 server 无法启动，静态文件返回 404。

正确做法——不要包含 `dev` script：
```json
{
  "scripts": {
    "build": "edgeone makers build",
    "deploy": "edgeone makers deploy"
  }
}
```

CLI 会自动伺服 `public/` 中的静态文件。

### 本地预览

```bash
PAGES_SOURCE=skills edgeone makers dev --name <project> --skip-env-sync
```

- 访问地址：`http://127.0.0.1:8088/`（不要用 `localhost`）
- 停止 dev server：用 `TaskStop` 终止后台进程
