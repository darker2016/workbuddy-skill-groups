---
name: super-partner-genius-draft
description: 天才合伙人草案生成技能。行业场景研究员补位和长期行业专业化草案的工作流，包含 C6 能力簇完整定义。
---

# 天才合伙人草案

这个技能定义了"天才合伙人"（Genius Partner）草案的生成流程。适用于用户需要长期行业补位、行业专业化或特定领域的深度专家方案时。

## 触发条件

- 用户需要"行业场景研究员"补位
- 需要为特定行业或领域创建一个专门的专家方案
- 长期行业深耕或专业化需求
- 现有超级合伙人成员无法覆盖的专业领域
- `teamMode=genius_partner_draft`

## 负责角色

由 `product-partner-xiaobai`（小白）负责草案组织和生成。

## C6 能力簇定义

`C6 天才合伙人工厂` 的核心能力：

- 行业画像采集
- 草案生成
- 确认前检查
- 确认后转移路径说明

### C5 / C6 分工明确

- `C5 产品智能化`：产品方案、AI 试点、数据口径、自动化、工具链
- `C6 天才合伙人工厂`：行业画像、草案生成、确认后转移

> Do not merge C5 and C6 into one generic answer. Always state which cluster this turn is using.

## 草案输出合同

当 `teamMode=genius_partner_draft` 时，必须包含以下 10 项：

### 1. 战术补位原因
为什么当前场景需要一位专门的行业合伙人，而不是由现有超级合伙人成员覆盖。

### 2. 团队上下文匹配
新合伙人的定位如何与现有团队（老孙、老朱、老沙、小白）形成互补，不是替代。

### 3. 证据计划与声明边界
- 需要采集哪些行业知识
- 信息的新鲜度和来源
- 哪些方面可以本地推理，哪些需要联网验证

### 4. 回交主团队计划
草案完成后如何与主团队衔接，数据如何回传给唐老。

### 5. 项目单元匹配
关联到当前工作空间中的哪个项目或任务。

### 6. 持续任务计划
后续维护该合伙人的任务安排。

### 7. 交付物落点
- 宿主可执行产物：草稿卡、场景包、专家定义文件
- 目标转移承载面：`my-experts` 或 `plugin_scene_pack`

### 8. 确认台账计划
如何记录确认状态、版本和审批记录。

### 9. 回滚计划
如果草案不被批准或需要修改，如何回滚到上一版本。

### 10. 可用性验收项
新合伙人的验收标准和使用条件。

## 执行流程

### Step 1：行业画像采集

收集以下信息：

- 行业定义和边界
- 关键术语和概念
- 常见问题和痛点
- 与超级合伙人现有能力的衔接点
- 目标用户角色画像

### Step 2：草案框架设计

基于行业画像，设计草案结构：

- 角色定义（name, description, displayName, profession）
- 能力边界（擅长/不擅长）
- 入参/出参合同
- 与主团队的通信协议

### Step 3：草案生成

小白输出完整的天才合伙人草案，包含上述 10 项输出合同。

### Step 4：确认门禁（Confirmation Gate）

草案在以下条件满足前一律视为草稿，不得直接交付给用户作为终稿：

- 用户明确确认接受草案
- 转移承载面已确认（my-experts / plugin_scene_pack）
- 回滚机制已建立

## 输出格式

每次输出必须是一张产品智能化卡（C5 模式）或完整的天才合伙人草案（C6 模式）。

### C6 模式额外字段

1. required input gaps
2. draft sections produced
3. quick prompts plan
4. confirmation gate
5. target transfer surface（my-experts 或 plugin_scene_pack）
6. tactical supplement reason
7. team context fit
8. evidence plan with freshness / claim boundary
9. return-to-core-team plan
10. project operating unit fit
11. taskized continuation plan
12. artifact delivery plan
13. confirmation ledger plan
14. rollback plan
15. usability acceptance checks

> 所有 15 项必须在最终的用户面草案中可见，不能隐藏在内部推理中。
