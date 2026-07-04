---
name: team-orchestration
description: |
  SEO 内容营销团队编排与工作流管理工具。提供完整的 5 阶段 SOP、团队协作机制、
  成员调度规范和最终报告整合标准。
  触发词：团队编排、工作流管理、SOP、任务调度、内容发布、团队协作
---

# SEO 内容营销团队编排与工作流

## 功能说明

提供 SEO 内容营销团队的完整编排方法论，覆盖从任务确认到内容发布的 5 阶段标准作业流程（SOP），包括团队创建、成员调度、消息中转、质量把关和最终报告整合。主理人基于此工具协调 6 位专业成员高效协作。

## 团队架构

### 成员角色

| Agent ID | 名字 | 专业领域 |
|----------|------|----------|
| **keyword-researcher** | 关宇霖 | 关键词调研、竞品分析、主题聚类策略、搜索意图分析 |
| **content-writer** | 文笔舒 | SEO 长文撰写（2000-3000+ 词）、Hook 写作、CTA 嵌入 |
| **seo-optimizer** | 欧化成 | 页面 SEO 优化、关键词密度审计、Meta 元素、结构化数据 |
| **content-editor** | 艾笔润 | 内容人性化编辑、AI 痕迹清除、标题优化、可读性提升 |
| **link-strategist** | 连乐桥 | 内链架构设计、外链推荐、主题聚类链接网络 |
| **cro-analyst** | 率可成 | 转化率优化、落地页心理学分析、CTA 策略、A/B 测试 |

### 团队协作铁律

1. **建立团队**：主理人在任务开始时创建团队（`TeamCreate(team_name="seo-content-<主题简称>")`）
2. **正式调度**：团队成员作为独立协作方，基于任务说明输出专业产出
3. **消息中转**：所有跨成员信息流必须经主理人中转，成员不得互相直连
4. **成员结论为准**：专业产出必须由对应成员输出后方可采信

**严禁行为**：
- ❌ 跳过"建立团队"的正式流程
- ❌ 主理人代写任何成员的专业产出
- ❌ 未完成前序阶段跳到后续阶段
- ❌ 成员互相直连通信
- ❌ spawn 主理人自己

## 标准工作流程（5 阶段 SOP）

### Phase 1: 关键词研究与任务确认

**主理人动作**：
1. 与用户确认：主题/关键词、目标受众、内容类型、品牌要求
2. 创建团队 `seo-content-<主题简称>`
3. 调用 **keyword-researcher**（关宇霖），下发研究任务

**调度示例**：
```
TeamCreate(team_name="seo-content-<主题简称>")
Agent(name="keyword-researcher", subagent_type="keyword-researcher", 
      team_name="seo-content-<主题简称>", prompt="<研究任务说明>")
```

**研究员输出**：
- 主关键词（搜索量、难度评估）
- 3-5 个语义变体和长尾词
- 竞品 Top 10 分析（字数基准、覆盖主题、内容差距）
- 搜索意图分类
- 推荐文章结构大纲
- 内链目标页面建议
- Meta 元素初稿

### Phase 2: 内容创作

**主理人动作**：
1. 将研究 Brief 完整传递给 **content-writer**（文笔舒）
2. 明确字数要求（默认 2500+ 词）、品牌声音、目标受众

**调度示例**：
```
Agent(name="content-writer", subagent_type="content-writer",
      team_name="seo-content-<主题简称>", prompt="<研究Brief + 写作要求>")
```

**撰稿人输出**：
- 完整 Markdown 格式文章（H1/H2/H3 层级结构）
- Hook 开头 + 关键要点块 + 2-3 个迷你故事 + 2-3 个上下文 CTA
- 前 100 词包含主关键词
- 关键词自然分布（1-2% 密度）
- 文件保存为 `drafts/[topic-slug]-[YYYY-MM-DD].md`

### Phase 3: 并行优化联审

**主理人动作**：
1. 将文章稿件同时传递给 3 位成员（同一条消息并行 spawn）

**调度示例**：
```
Agent(name="seo-optimizer", subagent_type="seo-optimizer", 
      team_name="seo-content-<主题简称>", prompt="<文章稿件 + 审计要求>")
Agent(name="content-editor", subagent_type="content-editor",
      team_name="seo-content-<主题简称>", prompt="<文章稿件 + 编辑要求>")
Agent(name="link-strategist", subagent_type="link-strategist",
      team_name="seo-content-<主题简称>", prompt="<文章稿件 + 链接策略要求>")
```

**等待 3 位成员全部通过 SendMessage 回传后，再进入下一阶段**

### Phase 4: CRO 优化（按需）

**触发条件**：内容类型为落地页、注册页，或用户要求优化转化率

**调度示例**：
```
Agent(name="cro-analyst", subagent_type="cro-analyst",
      team_name="seo-content-<主题简称>", prompt="<文章稿件 + Phase 3 报告 + CRO 要求>")
```

**CRO 分析师输出**：
- 心理学分析（7 维度）
- 具体修改建议（含 A/B 测试假设）
- CTA 优化方案
- 转化漏斗分析

### Phase 5: 最终整合与报告

**主理人动作**：
1. 汇总所有成员的优化建议
2. 整合冲突建议（SEO vs 可读性权衡时，优先用户体验）
3. 生成最终交付包

**最终输出物**：
1. **最终文章稿**（Markdown 格式，整合所有优化建议）
2. **SEO 审计报告**（评分、关键词分布、Meta 元素推荐）
3. **编辑报告**（人性化改动说明）
4. **发布检查清单**（所有项目 ✓/✗ 状态）
5. **发布状态判定**：Ready to Publish / Needs Minor Fixes / Needs Revision

## 预设工作流

### Workflow 1: 写新文章（完整流程）

```
Phase 1【串行】── keyword-researcher
Phase 2【串行】── content-writer
Phase 3【并行】── seo-optimizer + content-editor + link-strategist
Phase 5【主理人】── 汇总整合
```

### Workflow 2: 落地页创作（含 CRO）

```
Phase 1-2-3 同 Workflow 1
Phase 4【串行】── cro-analyst
Phase 5【主理人】── 汇总整合
```

### Workflow 3: 优化现有文章

```
Phase 3【并行】── seo-optimizer + content-editor + link-strategist
Phase 5【主理人】── 汇总整合
```

### Workflow 4: CRO 专项

```
Phase 4【串行】── cro-analyst
Phase 5【主理人】── 整合输出
```

## 单 agent 直调路由表

| 用户问法 | 直接调谁 |
|----------|----------|
| "帮我做关键词研究""分析竞品""设计主题聚类" | keyword-researcher |
| "帮我写一篇文章""基于 brief 写长文" | content-writer |
| "帮我做 SEO 审计""优化关键词分布" | seo-optimizer |
| "帮我去 AI 痕迹""优化标题""提升可读性" | content-editor |
| "帮我设计内链策略""评估内容健康度" | link-strategist |
| "帮我优化落地页转化率""分析 CTA" | cro-analyst |
| 综合性需求 | 走预设 Workflow |

## 质量标准

- **内容评分**：综合 ≥ 70 分方可标记为 "Ready to Publish"
- **冲突决策**：SEO 与可读性冲突时，优先用户体验
- **发布检查清单**：全量项 ✓ 通过方可发布

## 输出规范

| 文件类型 | 命名规则 |
|----------|----------|
| 文章稿件 | `drafts/[topic-slug]-[YYYY-MM-DD].md` |
| SEO 报告 | `reports/seo-report-[topic-slug]-[YYYY-MM-DD].md` |
| 研究 brief | `research/brief-[topic-slug]-[YYYY-MM-DD].md` |
