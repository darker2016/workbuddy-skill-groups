---
name: westock-tool
description: 腾讯自选股选股筛选技能 — 条件选股/策略选股/标签选股，支持自定义表达式筛选、40+预置策略一键选股、70+分类标签快速获取股票列表
---

# WeStock Tool — 腾讯自选股选股筛选技能

> **作用**：提供三种选股方式——条件选股（自定义表达式）、策略选股（40+预置策略）、标签选股（70+分类标签）
> **数据源**：腾讯自选股选股数据接口
> **市场支持**：条件选股（A股、港股、美股）| 策略选股（仅A股）| 标签选股（仅A股）

---

## 一、工具分工

| 工具 | 职责 | 典型场景 |
|------|------|---------|
| **westock-tool**（本技能） | 筛选/选股 | "MACD金叉策略"、"央企有哪些"、"PE<20且ROE>15" |
| **westock-data** | 查询个股详情 | 查行情/K线/财务/板块成份股（概念股查调用 `sector`） |
| **westock-portfolio** | 用户自选股管理 | "查看我的自选股" |

**⚠️ 命令路由原则**：
- `strategy` → 用户提到策略名称（如"MACD金叉"、"早晨之星"）
- `filter --preset` → 预设条件快速筛选（如"低PE股"、"高股息"）
- `label` → 分类标签（如"央企"、"ST股"、"新股"）
- `filter` 表达式 → 自定义条件（如 `PE<20且ROE>15`）
- ❌ 概念股查询用 `westock-data sector`，不是本工具

---

## 二、已知限制

| 限制项 | 说明 |
|--------|------|
| 市场覆盖 | 沪深A股、港股、美股；**不支持北交所** |
| 市值单位差异 | 沪深 `TotalMV` 单位为**元**，港股/美股为**亿元** |
| 港股/美股字段名 | 估值字段名与沪深不同，切勿混用 |
| PE/PB 负值 | 亏损股 PE/PB 为负，筛选时需 `PE_TTM > 0` |
| 预设函数市场 | 港股加 `--market hk`，美股加 `--market us` |
| 策略选股 | `strategy` 命令**仅支持A股** |
| 标签选股 | `label` 命令**仅支持A股** |

---

## 三、条件选股（filter）

### 基本语法

```bash
# 单条件
westock-tool filter "ClosePrice >= 100"

# AND 组合（必须用 intersect）
westock-tool filter "intersect([PE_TTM > 0, PE_TTM < 20, ROETTM > 15])"

# OR 组合
westock-tool filter "union([ChangePCT > 5, Chg5D > 10])"

# 指定排序
westock-tool filter "intersect([PE_TTM > 0, PE_TTM < 15])" --orderby ROETTM:desc

# 港股/美股选股
westock-tool filter "intersect([PeTTM > 0, PeTTM < 10])" --market hk
westock-tool filter "intersect([PeTTM > 0, PeTTM < 30])" --market us
```

### 参数说明

| 参数 | 说明 |
|------|------|
| 表达式 | 选股表达式，支持 `intersect([...])`(AND) 和 `union([...])`(OR) |
| `--date` | `YYYY-MM-DD`，默认今天 |
| `--limit` | 最大返回数量，默认20 |
| `--orderby` | 排序，格式 `字段:asc` 或 `字段:desc` |
| `--market` | `hk`=港股，`us`=美股，不指定默认沪深 |
| `--universe` | 板块代码，限定选股范围 |
| `--preset` | 预设函数快捷方式 |

### 预设选股函数

```bash
westock-tool filter --preset MACDGoldenCross --date 2026-03-24 --limit 30
westock-tool filter --preset LowPE --date 2026-03-12 --limit 20
westock-tool filter --preset HighDividend --market hk
westock-tool filter --list-presets        # 查看所有可用预设
```

---

## 四、策略选股（strategy）

```bash
# 查看所有策略
westock-tool strategy --list

# 单个策略
westock-tool strategy macd_golden

# 多个策略
westock-tool strategy high_dividend,pb_roe --date 2026-04-10

# 日期区间
westock-tool strategy macd_golden --start 2026-04-01 --end 2026-04-10
```

**参数**：`--date` / `--start` + `--end` / `--limit` / `--offset` / `--list`

---

## 五、标签选股（label）

```bash
# 查看所有标签
westock-tool label --list                 # 全部标签
westock-tool label --list 股东属性         # 按分组查看

# 单标签查询
westock-tool label shareholder_central_state

# 多标签查询（分别返回，非交集）
westock-tool label shareholder_central_state,risk_st

# 日期区间
westock-tool label shareholder_central_state --start 2026-04-01 --end 2026-04-10
```

**参数**：`--date` / `--start` + `--end` / `--limit` / `--offset` / `--list`

---

## 六、常用字段速查

| 类别 | 沪深(HS) | 港股(HK) | 美股(US) |
|------|----------|----------|----------|
| 市盈率TTM | PE_TTM | PeTTM | PeTTM |
| 市净率 | PB | PbLF | PbLF |
| 股息率TTM | DividendRatioTTM | DivTTM | DivTTM |
| 收盘价 | ClosePrice | ClosePrice | ClosePrice |
| 涨跌幅 | ChangePCT | ChangePCT | ChangePCT |
| 总市值 | TotalMV (元) | TotalMV (亿元) | TotalMV (亿元) |
| ROE(TTM) | ROETTM | RoeWeighted | ROE |
| 主力净流入 | MainNetFlow | MainNetFlow | - |

**⚠️ 沪深 TotalMV 单位为"元"，港股/美股为"亿元"**
**⚠️ 多条件 AND 必须用 `intersect([...])`，不支持 `&`/`&&`/`AND`**

---

## 七、常见错误

| 错误写法 | 正确写法 |
|---------|---------|
| `PE_TTM < 20 & ROE_TTM > 15` | `intersect([PE_TTM > 0, PE_TTM < 20, ROETTM > 15])` |
| `PE_TTM < 20 AND ROETTM > 15` | `intersect([PE_TTM > 0, PE_TTM < 20, ROETTM > 15])` |

---

## 八、使用规范

- ✅ 使用 CLI 命令执行选股查询，输出 Markdown 表格
- ❌ 不创建临时脚本文件，不写独立分析脚本
- ⚠️ 港股必须 `--market hk`，美股必须 `--market us`
- ⚠️ 筛选 PE/PB 时排除负值
- ⚠️ 沪深 `TotalMV` 单位为"元"，港股/美股为"亿元"

---

> ⚠️ **重要声明**：本技能仅提供客观市场数据的筛选与展示服务，所有返回数据均来源于公开市场信息，不含任何主观分析、投资评级或交易建议。数据可能存在延迟，请以交易所官方数据为准。
