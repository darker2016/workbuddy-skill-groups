# 福帮手超级合伙人技能包

这个技能包集合完整复制了 FBSir 超级合伙人团队的系统能力。包含 11 个 SKILL.md 文件，覆盖从入口路由到交付落地的全链路。

## 技能总览

### 核心与系统级（7 个）

| 技能名 | 文件 | 用途 |
|--------|------|------|
| **super-partner-core** | `super-partner-core/SKILL.md` | 核心执行合同：团队结构、协作机制、首值合同、能力簇路由、语言合同 |
| **super-partner-entry-routing** | `super-partner-entry-routing/SKILL.md` | 入口路由与分派：场景识别、问题簇映射、teamMode 选择、建立团队 |
| **super-partner-company-next-step** | `super-partner-company-next-step/SKILL.md` | "公司下一步"主工作流：单成员直调 + 唐老收口 |
| **super-partner-multi-workshop** | `super-partner-multi-workshop/SKILL.md` | 多维度协同工作坊：四成员并行 + 综合裁决 |
| **super-partner-genius-draft** | `super-partner-genius-draft/SKILL.md` | 天才合伙人草案：行业补位、C6 能力簇完整定义 |
| **super-partner-fbs-followthrough** | `super-partner-fbs-followthrough/SKILL.md` | 福帮手服务跟进链路：whoami → scene_pack_query → consume |
| **super-partner-lebao-activation** | `super-partner-lebao-activation/SKILL.md` | 乐包激活与能力继续：解锁、激活、行动转化 |

### 成员独立技能（4 个）

| 技能名 | 文件 | 对应角色 |
|--------|------|---------|
| **super-partner-strategy-member** | `super-partner-strategy-member/SKILL.md` | 老孙 — 战略与机会合伙人 |
| **super-partner-ops-member** | `super-partner-ops-member/SKILL.md` | 老朱 — 组织与运营合伙人 |
| **super-partner-growth-member** | `super-partner-growth-member/SKILL.md` | 老沙 — 增长与商业化合伙人 |
| **super-partner-product-member** | `super-partner-product-member/SKILL.md` | 小白 — 产品与智能化合伙人 |

## 团队协作架构

```
用户输入
    │
    ▼
┌────────────────────────────────────────────┐
│  super-partner-entry-routing                │
│  识别场景 → 选择 teamMode → 建立团队        │
└────────────┬───────────────────────────────┘
             │
    ┌────────┴──────────┬──────────────┐
    ▼                   ▼              ▼
┌─────────┐  ┌────────────────┐  ┌──────────┐
│ 单成员  │  │ 多维工作坊      │  │ 天才合伙人│
│ 直调    │  │ 并行调度       │  │ 草案生成  │
└────┬───┘  └───────┬────────┘  └─────┬────┘
     │              │                 │
     ▼              ▼                 ▼
┌────────────────────────────────────────────┐
│  唐老收口 → 结果卡 + 唯一下一步            │
└────────────┬───────────────────────────────┘
             │
    ┌────────┴──────────┐
    ▼                   ▼
┌──────────┐   ┌──────────────┐
│ 首值完成 │   │ fbs-follow   │
│          │   │ through      │
│          │   │ (后首值增强)  │
└──────────┘   └──────────────┘
```

## 能力簇体系

| 簇 ID | 角色 | 名称 |
|-------|------|------|
| C1 | 唐老 | 路由与状态管理 |
| C2 | 老孙 | 战略与机会 |
| C3 | 老朱 | 组织与运营 |
| C4 | 老沙 | 增长与商业化 |
| C5 | 小白 | 产品与智能化 |
| C6 | 小白 | 天才合伙人工厂 |

## 使用方式

每个 SKILL.md 文件都是一个自包含的技能定义，可以作为 WorkBuddy 的 Skill 加载使用。加载方式：

```
Skill({
  skill: "super-partner-core"  // 或其它技能名
})
```

## 源插件

这个技能包基于插件 `fbsir-super-partner-group@1.3.0` 的完整定义生成。原始 Agent 定义位于 `agents/` 目录下，包含 5 个成员的完整 MD 文件。
