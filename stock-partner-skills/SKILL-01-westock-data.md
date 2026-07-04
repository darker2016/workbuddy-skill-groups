---
name: westock-data
description: 腾讯自选股数据查询技能 — 查询A股、港股、美股个股/指数/ETF的详细数据，包括实时行情、K线、财务报表、资金流向、技术指标、机构评级、新闻公告等
---

# WeStock Data — 腾讯自选股数据查询技能

> **作用**：查询个股详情 — "查某只股票的行情/K线/财务/资金等数据"、"查宏观经济数据"、"查板块/概念成份股"等
> **数据源**：腾讯自选股行情数据接口 | **支持市场**：A股（沪深/科创/北交所）、港股、美股

---

## 一、工具分工

| 工具 | 职责 |
|------|------|
| **westock-data**（本技能） | 查询个股详情 — 行情/K线/财务/资金/风险/新闻/公告/研报/板块成份股/宏观经济等 |
| **westock-tool** | 筛选/选股 — 条件选股/策略选股/标签选股 |
| **westock-portfolio** | 用户自选股管理（需 APIKEY） |

**⚠️ 概念股查询路径**：`westock-data sector --search 华为` → `sector <代码>`（属于数据查询，非选股）

---

## 二、已知限制

| 限制项 | 说明 |
|--------|------|
| 风险事件 | 仅支持A股（sh/sz/bj），港股美股不支持 `risk` 命令 |
| 龙虎榜 | 仅支持A股 |
| 大宗交易/融资融券 | 仅支持沪深市场（sh/sz） |
| 筹码成本 | 仅支持沪深京A股（sh/sz/bj） |
| 股东结构 | 仅支持A股和港股 |
| 货币单位 | 港股返回港元/美元，美股返回美元，禁止使用人民币符号 |
| `search`/`minute` | 不支持批量查询 |

---

## 三、股票代码格式

| 市场 | 格式 | 示例 |
|------|------|------|
| 沪市/科创板 | sh + 6位数字 | `sh600000`、`sh688981` |
| 深市 | sz + 6位数字 | `sz000001` |
| 北交所 | bj + 6位数字 | `bj430047` |
| 港股 | hk + 5位数字 | `hk00700` |
| 港股指数 | hk + 指数代码 | `hkHSI`(恒生) |
| 美股 | us + 代码 | `usAAPL` |
| 美股指数 | us. + 指数代码 | `us.IXIC`(纳斯达克) |

---

## 四、核心命令速查

### 4.1 基础查询

```bash
# 股票搜索
westock-data search 腾讯控股              # 默认搜索股票
westock-data search 华夏 --fund           # 搜索基金/ETF
westock-data search 银行 --sector         # 搜索板块（仅名称+代码，不含成份股）

# 实时行情（支持个股/指数/板块/ETF 批量查询）
westock-data quote sh600000
westock-data quote sh600000,sz000001,hk00700

# 股票评分
westock-data score sh600519               # 评分及周/月/季变动

# K线（支持多周期：day/week/month/season/year）
westock-data kline hk00700 --period week --limit 10
westock-data kline sz000001 --period day --limit 60 --fq qfq

# 分时
westock-data minute sh600000              # 1日分时
westock-data minute sh600000 --days 5     # 5日分时

# 财务报表
westock-data finance sh600000 --num 4     # 完整财报，最近4期
westock-data finance sh600000 --type lrb --num 8  # 利润表8期
```

### 4.2 资金与交易分析

```bash
# 资金流向
westock-data hkfund hk00700              # 港股资金
westock-data asfund sh600000             # A股资金
westock-data usfund usAAPL               # 美股卖空

# 龙虎榜（仅A股）
westock-data lhb                         # 全市场龙虎榜
westock-data lhb --tab jg,yzb            # 机构+游资榜

# 大宗交易 / 融资融券（仅沪深）
westock-data blocktrade sz000001
westock-data margintrade sz000001

# 公司回购（A股/港股）
westock-data buyback hk01810

# 风险事件（⚠️ 仅A股）
westock-data risk sh600000               # 全部风险事件
westock-data risk sz000001 --types pledge,unlock  # 质押+解禁
```

### 4.3 新闻与研究

```bash
# 新闻列表（--type: 0=公告,1=研报,2=新闻,3=全部）
westock-data news sh600000 --limit 20 --type 2

# 市场资讯
westock-data marketnews hs               # 沪深市场资讯
westock-data marketnews hk               # 港股市场资讯

# 机构评级 / 一致预期
westock-data rating sh600519
westock-data consensus sh600519

# 研报 / 公告
westock-data report sh600000
westock-data notice sh600000
```

### 4.4 技术指标

```bash
westock-data technical sh600000                           # 全部指标
westock-data technical sh600000 --group macd,rsi          # 特定分组
westock-data technical sh600000 --group all --date 2026-03-01  # 指定日期
```

### 4.5 板块与指数

```bash
# 板块成份股（两步法）
westock-data sector --search 华为                        # 步骤1：搜索板块代码
westock-data sector style_pt01801517                     # 步骤2：查成份股

# 板块排行
westock-data sector --rank interval_chg_rank_sw1 --sort chg5Days

# 指数成份股
westock-data index sh000300                              # 沪深300成份股
```

### 4.6 平台特色数据

```bash
westock-data hot stock                   # 热搜股票
westock-data watchlist rank              # 热门股单
westock-data ipo hs                      # 沪深新股
westock-data dehydrated                  # 脱水研报
westock-data calendar                    # 投资日历
```

### 4.7 宏观经济

```bash
westock-data macro --list                                # 列出所有指标
westock-data macro gdp --year 2025                       # GDP查询
westock-data macro core_indicatros_cur --date 2026-03-31 # 最新核心指标
westock-data macro pmi --start 2024 --end 2025           # PMI区间趋势
```

---

## 五、通用参数

| 参数 | 说明 | 适用命令 |
|------|------|----------|
| `--date` | 指定日期 `YYYY-MM-DD` | 资金流向、技术指标等 |
| `--start`/`--end` | 区间查询 | 资金流向、技术指标、K线等 |
| `--limit` | 返回数量限制 | 大部分查询命令 |
| `--num` | 返回期数 | finance（财务报表） |
| `--days` | 分时天数 | minute |

---

## 六、常用指数代码

| 指数 | 代码 |
|------|------|
| 上证指数 | `sh000001` |
| 深证成指 | `sz399001` |
| 创业板指 | `sz399006` |
| 恒生指数 | `hkHSI` |
| 纳斯达克 | `us.IXIC` |
| 标普500 | `us.INX` |

---

## 七、使用规范

- ✅ 使用 CLI 命令查询数据，输出 Markdown 表格
- ❌ 不创建临时脚本文件，不写独立分析脚本
- ⚠️ 港股/美股货币单位不可用人民币符号
- ⚠️ `search --sector` 只返回板块列表，不返回成份股

---

> ⚠️ **重要声明**：本技能仅提供客观市场数据的查询与展示服务，所有返回数据均来源于公开市场信息，不含任何主观分析、投资评级或交易建议。数据可能存在延迟，请以交易所官方数据为准。
