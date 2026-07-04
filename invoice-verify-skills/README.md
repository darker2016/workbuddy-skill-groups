# 智能发票专家团 — Skill 文档集

本目录包含智能发票专家团（Intelligent Invoice Expert Team）的完整 SKILL.md 文档，五位 AI 专家接力协作，通过上传发票文件、批量上传表格或指定本地文件夹，完成识别、税局验真、信用核查与归档。

## 团队角色

| 角色 | 专家定位 | 技能文件 | 职责 |
|------|----------|----------|------|
| **百晓通** | 智能发票首席专家 | `agents/invoice-verify-team-lead.md` | 接单、编排、分发与结果汇总 |
| **百晓甄** | 多模态识别专家 | `agents/invoice-sorter.md` | 场景分拣、识别请求类型 |
| **百晓燕** | 发票查验专家 | `agents/invoice-verifier.md` | OCR识别、字段标准化、验真、旅客运输抵扣判断 |
| **百晓信** | 商业信用专家 | `agents/counterparty-risk-analyst.md` | 交易对手灰名单、欠税、重大违法风险查询 |
| **百晓慧** | 企业票夹 | `agents/archivist.md` | 报告整合与最终输出 |

## 目录结构

```
invoice-verify-skill-docs/
├── SKILL.md                          # 核心业务规范（完整工作流）
├── README.md                         # 本说明文件
├── agents/                           # 各角色的 agent 定义文件
│   ├── invoice-verify-team-lead.md   # 百晓通 - 首席专家
│   ├── invoice-sorter.md             # 百晓甄 - 多模态识别专家
│   ├── invoice-verifier.md           # 百晓燕 - 发票查验专家
│   ├── counterparty-risk-analyst.md  # 百晓信 - 商业信用专家
│   └── archivist.md                  # 百晓慧 - 企业票夹
├── references/                       # 业务规则参考文件
│   ├── ocr_to_verify_type_mapping.md # 发票名称→验真参数决策表
│   ├── invoice_types.md              # 文件格式清单、四要素定义、旅客运输抵扣
│   ├── mcp_calls.md                  # MCP 工具注册表与调用示例
│   ├── error_handling.md             # 错误码矩阵、重试策略、去重规则
│   ├── report_templates.md           # 报告 Markdown 模板与字段映射
│   └── risk_rules.md                 # 风险等级分类与综合评级逻辑
└── scripts/                          # Python 脚本占位
```

## 核心工作流

```text
用户输入/上传发票
  → 百晓通识别任务
    → 百晓甄判断输入场景（文件/四要素/文件夹/表格/不完整）
      → 百晓燕上传文件、OCR识别、标准化参数、发起验真
        → 百晓信按销方名称或税号查询商业信用风险
          → 百晓慧整合查验结果和商业信用结果
```

## 关键能力

- **单张发票核验**：支持 jpg/jpeg/png/bmp/pdf/ofd/xml 格式
- **四要素直通验真**：跳过文件识别，直接调用验真接口
- **文件夹批量核验**：支持批量扫描、去重（上限100张）
- **表格批量解析**：支持 xlsx/xls/csv 按列名匹配
- **交易对手风险查询**：灰名单、欠税、重大税收违法三项并行
- **旅客运输抵扣判断**：电子普票+旅客运输服务的自动抵扣计算
- **异常处理降级**：接口不可用时的 WebSearch 降级和人工指引

## 免责声明

以上内容由 AI 基于发票识别、验真和风险查询结果整理生成，仅供业务复核参考，不构成税务建议、入账依据或最终合规结论。发票查验结果以税务机关官方查验平台和企业内部审批流程为准。
