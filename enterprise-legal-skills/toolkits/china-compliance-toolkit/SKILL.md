---
name: china-compliance-toolkit
description: 中国企业法务本地化工具包，整合税务知识、涉税文书模板、合同风险扫描、PIPL 合规、诉讼费估算和精选合规脚本。用于中国境内合同、劳动、隐私、税务和合规工作流。
agent_created: true
---

# 中国企业法务本地化工具包

## 概述

企业法务专家团的中国法务本地化辅助工具包。集成了中国合同审查、PIPL 合规、税务参考、劳动争议计算、条款重述和法律文书骨架等实用资源。

## 集成资源

| 资源 | 用途 | 引用方式 |
|------|------|---------|
| 合同审查 | 入口级中国合同审查流程、劳动/销售合同审查要点 | `references/china-contract-review/` |
| PIPL 合规 | 法律笔记、检查清单、风险评估指南、执法案例、评分脚本 | `references/pipl-compliance/` |
| 法律 AI 助手 | 合同风险模式、条款重述手册、诉讼成本公式、劳动争议场景、文书骨架、隐私与信任规则 | `references/ai-legal-assistant-pro/` |
| 中国税法 | 税率参考、税务合规清单 | `references/china-tax-law/` |
| 法律文书起草 | 税务筹划报告、法律意见书、复议/诉讼文书、合同税务条款模板 | `references/legal-doc-writer/` |

## 可用脚本

| 脚本 | 用途 | 路径 |
|------|------|------|
| `calculate_lawsuit_fee.py` | 诉讼费计算（参考《诉讼费用交纳办法》） | `scripts/ai-legal-assistant/` |
| `contract_review.py` | 合同风险规则扫描 | `scripts/` |
| `labor_contract_check.py` | 劳动合同检查 | `scripts/` |
| `pipl_compliance_check.py` | PIPL 合规检查 | `scripts/` |
| `compliance_risk_matrix.py` | 合规风险矩阵评分 | `scripts/` |
| `pipl-check.py` | PIPL 合规核验 | `scripts/pipl/` |
| `risk-assessment.py` | 个人信息处理活动风险评估 | `scripts/pipl/` |

## 路由指南

| 需求 | 使用指引 |
|------|---------|
| 合同审查与条款重述 | `references/ai-legal-assistant-pro/references/risk-patterns.md` + `clause-redraft-playbook.md` + `contract-type-guides.md` + 精选合同脚本 |
| 劳动/劳动争议 | `labor-dispute-scenarios.md` + `labor-compensation-output-template.md` + `labor_contract_check.py` |
| PIPL/数据合规 | `references/pipl-compliance/` + `scripts/pipl/pipl-check.py` + `scripts/pipl/risk-assessment.py` + `pipl_compliance_check.py` |
| 税务 | `references/china-tax-law/` + `references/legal-doc-writer/` |
| 诉讼成本与文书骨架 | `calculate_lawsuit_fee.py` + `document-skeletons.md` |

## 关于 `risk-assessment.py --activity` 的说明

命令如 `python3 scripts/pipl/risk-assessment.py --activity "用户注册" --data medium --volume medium --format json` 中，`"用户注册"` 仅是待评估的个人信息处理活动名称（用户注册 / 账号注册），并非注册码，不注册用户，也不调用外部服务。该脚本是本地确定性风险评分辅助工具：将数据敏感性、处理规模、目的、第三方参与和安全级别组合成一个初步的 PIPL 风险评分。

## 企业工商信息集成（Qichacha MCP）

如果 WorkBuddy 已启用企查查企业连接器，可调用 `mcp__qcc-company__<tool_name>` 工具。将企查查用作企业数据层，而非法律结论引擎。

有用工具和法务场景：

| 工具 | 法务场景 |
|------|---------|
| `verify_company_accuracy` | 验证公司名称/法定代表人/统一社会信用代码 — 合同对手方准入 |
| `get_company_registration_info` | 登记状态、法定代表人、资本、成立日期、地址 — 合同主体审查 |
| `get_company_profile` | 行业和业务简介 — 产品法务适配和合规上下文 |
| `get_shareholder_info` / `get_actual_controller` / `get_beneficial_owners` | 所有权、控制权、反洗钱、关联方和尽调审查 |
| `get_key_personnel` / `get_branches` / `get_change_records` | 治理结构、分支结构、变更历史检查 |
| `get_financial_data` / `get_listing_info` / `get_annual_reports` | 供应商/客户财务状况、上市公司背景、年度经营审查 |
| `get_external_investments` / `get_contact_info` / `get_tax_invoice_info` | 集团架构、联系/ICP 上下文、开票身份信息 |

若工具不可用，告知用户可在 WorkBuddy 中启用企查查连接器（当前有每日免费额度）。不得凭空编造企业档案、股东、实控人、发票或财务数据。

## 输出规则

保持源工作流的结构，但移除营销语言、无根据的产品声明和空置的占位能力。对于任何法律结论，注明所使用的源材料，并告知用户仍需要持证律师或官方来源核实的内容。
