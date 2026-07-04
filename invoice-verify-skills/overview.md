# 智能发票专家团 Skill 文档集 - 生成完毕

## 做了什么

基于现有 `invoice-verify-workbuddy` 专家包，生成了完整的智能发票专家团 SKILL.md 文档集，保存到本地 `invoice-verify-skill-docs/` 目录。

### 生成的文档清单（共 12 个文件）

**核心 Skill 文件（1 个）**：
1. `SKILL.md` — 完整业务规范，涵盖场景分拣、发票识别与采集、四要素直通验真、文件夹批量处理、验真与抵扣判断、风险洞察、报告输出等完整工作流程

**Agent 定义文件（5 个）**：
2. `agents/invoice-verify-team-lead.md` — 百晓通（首席专家）：团队编排、调度、汇总
3. `agents/invoice-sorter.md` — 百晓甄（多模态识别专家）：场景分拣、缺失字段追问
4. `agents/invoice-verifier.md` — 百晓燕（发票查验专家）：OCR识别、字段标准化、验真、抵扣判断
5. `agents/counterparty-risk-analyst.md` — 百晓信（商业信用专家）：灰名单、欠税、重大违法风险查询
6. `agents/archivist.md` — 百晓慧（企业票夹）：报告整合、最终输出

**参考文件（6 个）**：
7. `references/ocr_to_verify_type_mapping.md` — 发票名称→验真参数决策表
8. `references/invoice_types.md` — 文件格式清单、四要素定义、旅客运输抵扣规则
9. `references/mcp_calls.md` — MCP 工具注册表、调用示例
10. `references/error_handling.md` — 错误码矩阵、重试策略、去重规则
11. `references/report_templates.md` — 报告 Markdown 模板、字段映射表
12. `references/risk_rules.md` — 风险等级分类、综合评级逻辑

### 关键设计

- 主 SKILL.md 定义了完整的 5 步工作流（分拣→识别→验真→风险→归档）
- 每个 agent 有明确的职责边界、交接协议和结果回传格式
- 参考文件按单一职责原则拆分，6 个文件各管一块（决策/格式/调用/错误/模板/评级）
