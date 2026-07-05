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

---

## 普通用户（非开发者）怎么用

> 提示：本 skill 的 `*.md` 文件本质是一段长 system prompt。  
> 你不需要部署、不需要写代码，**打开任意一个免费 AI 对话产品粘贴即可**。

### 国内免费产品（推荐）

| App | 操作方式 | 何时用 |
|-----|---------|--------|
| **豆包** | 创建「智能体」→ 把 `SKILL.md` 全文填入「系统提示词」 | 营销/内容/办公 |
| **DeepSeek** | 在对话开头或「系统消息」粘贴 `SKILL.md` | 投研/文档/代码 |
| **Kimi** | 同上（支持超长 system prompt） | 长文档/法律 |
| **通义千问 / 文心一言 / 腾讯元宝** | 创建智能体 / 直接粘贴 | 通用 |

### 海外免费产品

| App | 操作方式 | 何时用 |
|-----|---------|--------|
| **ChatGPT 免费版** | 对话最前面粘贴 `SKILL.md` | 通用 |
| **Google Gemini** | 用 Custom Instructions 或"system:"前缀粘贴 | 通用/办公 |
| **Claude.ai** | Project → System Prompt → 粘贴 | 写作/政策/法律 |
| **HuggingChat** | 同上 | 通用 |
| **Poe** | Bot 设置 → System Prompt | 通用 |

### ⚠️ 重要提示：复杂任务效果会弱于在 WorkBuddy 上使用

如果你是在 **WorkBuddy 平台之外**使用这些 expert skills，请对效果保持合理预期：

- **多角色并行被压扁**。WorkBuddy 里每个成员是「独立调度的 agent」；在 free app 里只能把所有成员规则压进同一对话上下文，长事务容易丢失上下文。
- **工具调用不存在**。许多 skill 依赖的 WorkBuddy tool calls（知识检索 / 私有数据源）在 free app 里不可用，skill 会"降级"为纯 prompt。
- **跨会话记忆与 RAG 缺失**。WorkBuddy 维持会话级记忆；其他 app 单对话做不到多阶段共享上下文。
- **角色一致性在长事务里漂移**。轮数多时模型容易"忘记自己是第几阶段"。

**建议** 用于一次性、短流程、单主理人为主的场景；  
**不建议** 用于"13 位哲学家并行投研"、"6 阶段 MVP 开发"、"依赖 WorkBuddy 实时私有数据"的任务。

**最佳实践**：先只把**主理人的 `SKILL.md`** 用作 system prompt；在任务中把成员 input / output 作为示例插入，效果最稳定。对于严肃或需要精准结论的任务，请直接在 WorkBuddy 里使用这些 skills。
