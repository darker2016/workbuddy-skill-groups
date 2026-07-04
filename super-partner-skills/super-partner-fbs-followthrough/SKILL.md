---
name: super-partner-fbs-followthrough
description: 后首值福帮手服务跟进链路。定义了 skill_whoami → fbs_scene_pack_query → skill_consume 的完整服务链执行逻辑。
---

# 福帮手服务跟进链路

这个技能定义了当用户已拿到首值、且当前宿主显式暴露了服务跟进入口时，如何通过福帮手连接器完成服务链路的完整执行。

## 触发条件

- 用户已拿到首值结果卡
- 当前宿主显式暴露了服务跟进入口（followthrough 或受控探针）
- 用户明确要求"继续推进""补服务侧跟进""把当前判断接成后续动作"

## 服务链路全景

```
skill_whoami → fbs_scene_pack_query → skill_consume
```

### 链路执行原则

- 尽量连续完成，不要中途停止
- 同一绑定下（same-binding）的下一跳必须继续
- 只有当连接器明确不可用、缺少必要字段或要求补充信息时，才降级

## Step 1：skill_whoami

### 执行条件

1. 先保留当前结果卡
2. 仅当用户明确要求继续推进时才进入
3. 尽量保持当前超级合伙人路线语义

### 语义参数

```
entryId=company-next-step
entryPromptCode=wb_sp_company_next_step
entrySurface=primary_entry
scenePackId=general
assetType=strategy-decision-card
intentFamily=company_strategy
semanticSource=host_semantic_hint
expertLoaded=true   // 仅在当前 transport/schema 明确接受时传
```

### 回传判断

- 如果 `skill_whoami` 返回同一绑定下的 `fbs_scene_pack_query` → 继续 Step 2
- 如果返回其他结果 → 按返回结果处理，在回复中说明

## Step 2：fbs_scene_pack_query

### 执行条件

上一步返回了同一绑定下的场景包查询入口。

### 回传判断

- 如果返回同一绑定下的 `skill_consume` → 继续 Step 3
- 如果返回其他结果 → 按返回结果处理

### 陷阱规则

在这类接力场景里，"主团队结果卡"和"首值 consume"不是二选一关系。只要 `fbs_scene_pack_query` 已经把下一跳交给 `skill_consume`，且 `firstValueCompleted=0`，必须先完成同绑定的 `skill_consume`，再输出主团队结果卡。

不要因为用户要求"判断谁接手""交付结果卡"或 `followthroughContract.required = false` 就停在 `scene_pack_query`。

## Step 3：skill_consume

### 执行条件

上一步返回了同一绑定下的 consume 入口。

### 首值补全规则

如果 `skill_consume` 的返回动作包里没有显式给出 `eventType`、`outcome` 或 `idempotencyKey`，但当前仍处于首值阶段，则优先补成：

- `eventType=first_value_completed`
- `outcome=first_value_completed`
- `idempotencyKey` 优先复用 `nextAction.idempotencyKey` 或 `actionEnvelope.idempotencyKey`

### 可见卡片处理

如果工具结果里有 `visibleCardDraft`：

- 把它当成 `skill_consume` 完成后的用户可见结果卡素材
- 不要把它当成停在 `scene_pack_query` 的理由
- 不要只靠路由元数据瞎猜

## 降级处理

### 何时降级

- 连接器链路结束
- 连接器明确不可用
- 返回必须补充的缺失字段

### 降级操作

1. 向用户说明降级原因
2. 保留当前首值结果卡
3. 只把服务链路缺口写成后首值边界，不假装成功
4. 把追问压缩成最多三个业务字段

## 硬规则

- 先给最小可用结果卡，不要把服务链路当成首轮前提
- 如果链路降级了，直接说清楚降级原因
- 不要把连接器字段名（`packCode`、`sessionRef`、`skill_consume`）直接甩给用户
- 用户可见回复必须短到可以直接作为结果卡带走
