---
name: diagrams-generator
description: Generate professional diagrams including cloud architecture, data charts, academic figures, and more. Triggers on requests like "画架构图", "画图表", "画论文插图", "生成系统图", "create diagram", "visualize data", "draw neural network", or when users provide a sketch/image they want to recreate professionally.
---

# Diagrams Generator

Generate professional diagrams using the most suitable tool for each scenario.

## 工具选择矩阵

| 场景 | 推荐工具 | 速度 | 质量 | 安装成本 |
|------|---------|------|------|----------|
| 云架构图 (AWS/GCP/Azure/K8s) | `diagrams` | ⚡ 快 | ★★★★ | 轻量 (~50MB) |
| 数据图表 (折线/柱状/饼图) | `matplotlib` | ⚡ 快 | ★★★ | 轻量 |
| 统计图表 (热力图/分布图) | `seaborn` | ⚡ 快 | ★★★★ | 轻量 |
| 交互式图表 (Web/3D) | `plotly` | ⚡ 快 | ★★★★ | 轻量 |
| 流程图/状态机 | `graphviz` | ⚡ 快 | ★★★ | 轻量 |
| 网络拓扑/关系图 | `networkx` | ⚡ 快 | ★★★ | 轻量 |
| **学术论文图** (神经网络/模型架构) | `TikZ` | 🐢 慢 | ★★★★★ | 重量 (~4GB) |
| **学术论文图** (快速替代) | `matplotlib` | ⚡ 快 | ★★★ | 轻量 |

## Prerequisites (按需安装)

### 基础工具 (大多数场景)
```bash
# Graphviz (diagrams 依赖)
brew install graphviz  # macOS
apt-get install graphviz  # Linux

# Python 库
pip install diagrams matplotlib seaborn plotly networkx
```

### TikZ/LaTeX (学术论文级图表 - 可选)
```bash
# macOS - 完整安装 (~4GB, 10-15分钟)
brew install --cask mactex

# macOS - 轻量安装 (~500MB)
brew install --cask basictex
sudo tlmgr install tikz-cd pgfplots standalone

# Linux
apt-get install texlive-full  # 完整版
# 或
apt-get install texlive-base texlive-pictures texlive-latex-extra  # 轻量版
```

## Workflow

### Phase 1: Requirement Understanding & Tool Recommendation (MANDATORY)

**⚠️ CRITICAL: You MUST complete ALL steps in Phase 1 and receive explicit user confirmation BEFORE proceeding to Phase 2. DO NOT skip this phase or generate code without confirmation.**

1. **Receive input**: User provides text description and/or reference image

2. **Identify Scenario**: 根据用户描述中的关键词，识别场景类型：
   
   | 检测关键词 | 场景判断 |
   |-----------|---------|
   | 架构/系统/微服务/AWS/GCP/K8s | → 云架构图 |
   | 数据/趋势/统计/柱状/折线/饼图 | → 数据图表 |
   | 交互/动态/Web/仪表板 | → 交互图表 |
   | 热力图/分布/相关性 | → 统计图表 |
   | 流程/状态机/决策树 | → 流程图 |
   | 网络/拓扑/节点/关系 | → 关系图 |
   | 论文/学术/神经网络/模型架构 | → 学术图 |

3. **Analyze and extract**:
   - Components (services, databases, users, layers, etc.)
   - Groupings/Clusters (VPC, regions, logical groups, network layers)
   - Connections and data flows
   - Labels and annotations

4. **⚠️ MANDATORY OUTPUT - 输出以下结构化内容**:

   **你必须按照以下格式输出，缺一不可：**
   
   ---
   
   **4.1 架构理解** - Natural language summary of the architecture
   
   **4.2 组件清单** - List all identified components by layer
   
   **4.3 连接关系** - Describe all connections and data flows
   
   **4.4 Mermaid 预览** - Provide Mermaid diagram code for quick visual preview
   
   **4.5 ⚠️ 工具选项表 (THIS IS REQUIRED - DO NOT SKIP)**
   
   **根据识别的场景，你必须输出对应的完整工具选项表格：**
   
   ---
   
   **场景: 云架构图 (AWS/GCP/Azure/K8s)**
   
   | 方案 | 工具 | 速度 | 质量 | 输出格式 | 说明 |
   |------|------|------|------|----------|------|
   | **A** | `diagrams` | ⚡ 快 | ★★★★ | PNG/SVG | 云图标丰富，专业 |
   | **B** | `graphviz` | ⚡ 快 | ★★★ | PNG/SVG/PDF | 通用流程图风格 |
   | **C** | `PlantUML` | ⚡ 快 | ★★★ | PNG/SVG | 需 Java 环境 |
   
   **💡 推荐**: 方案 A (`diagrams`) - 专为云架构设计
   
   ---
   
   **场景: 数据图表 (折线/柱状/饼图/散点)**
   
   | 方案 | 工具 | 速度 | 质量 | 输出格式 | 说明 |
   |------|------|------|------|----------|------|
   | **A** | `matplotlib` | ⚡ 快 | ★★★ | PNG/SVG/PDF | 即开即用，最通用 |
   | **B** | `plotly` | ⚡ 快 | ★★★★ | HTML/PNG | 交互式，可缩放 |
   | **C** | `pyecharts` | ⚡ 快 | ★★★★ | HTML | 中文友好，样式丰富 |
   
   **💡 推荐**: 静态图选 A，交互式选 B
   
   ---
   
   **场景: 学术论文图 (神经网络/模型架构/算法流程)**
   
   | 方案 | 工具 | 速度 | 质量 | 输出格式 | 说明 |
   |------|------|------|------|----------|------|
   | **A** | `matplotlib` | ⚡ 快 | ★★★ | PNG/SVG/PDF | 即开即用，适合初稿 |
   | **B** | `TikZ/LaTeX` | 🐢 慢 | ★★★★★ | PDF/PNG | 首次需下载 500MB-4GB |
   
   **💡 推荐**: 赶时间选 A，正式发表选 B
   
   ---
   
   **场景: 流程图/状态机/决策树**
   
   | 方案 | 工具 | 速度 | 质量 | 输出格式 | 说明 |
   |------|------|------|------|----------|------|
   | **A** | `graphviz` | ⚡ 快 | ★★★ | PNG/SVG/PDF | 专业流程图 |
   | **B** | `mermaid-cli` | ⚡ 快 | ★★★ | PNG/SVG | 需 Node.js 环境 |
   | **C** | `PlantUML` | ⚡ 快 | ★★★ | PNG/SVG | 需 Java 环境 |
   
   **💡 推荐**: 方案 A (`graphviz`) - 无额外依赖
   
   ---
   
   **场景: 网络拓扑/关系图/知识图谱**
   
   | 方案 | 工具 | 速度 | 质量 | 输出格式 | 说明 |
   |------|------|------|------|----------|------|
   | **A** | `networkx` + `matplotlib` | ⚡ 快 | ★★★ | PNG/SVG | 静态图，轻量 |
   | **B** | `pyvis` | ⚡ 快 | ★★★★ | HTML | 交互式，可拖拽 |
   | **C** | `graphviz` | ⚡ 快 | ★★★ | PNG/SVG/PDF | 层次布局清晰 |
   
   **💡 推荐**: 静态选 A，交互式选 B
   
   ---
   
   **场景: 统计图表 (热力图/分布图/相关性矩阵)**
   
   | 方案 | 工具 | 速度 | 质量 | 输出格式 | 说明 |
   |------|------|------|------|----------|------|
   | **A** | `seaborn` | ⚡ 快 | ★★★★ | PNG/SVG/PDF | 统计图专用 |
   | **B** | `matplotlib` | ⚡ 快 | ★★★ | PNG/SVG/PDF | 更灵活，需手动配置 |
   | **C** | `plotly` | ⚡ 快 | ★★★★ | HTML/PNG | 交互式热力图 |
   
   **💡 推荐**: 方案 A (`seaborn`) - 统计可视化首选
   
   ---

5. **MANDATORY CONFIRMATION** - 你必须询问用户确认：
   - 架构理解是否正确？
   - 组件/连接是否需要增减？
   - **请选择工具方案: [A] / [B] / [C]？（或使用推荐方案）**
   - **⚠️ DO NOT proceed to Phase 2 until user explicitly confirms AND chooses a tool**

**Required output format (MUST follow this structure):**

```markdown
## 1. 架构理解

我理解你需要的架构图包含以下内容：[简要描述]

## 2. 组件清单

- **用户层**: Business Analyst, Developer
- **应用层**: Cloud Run (wiki-interface, evaluator)
- **数据层**: Redis (Memorystore), Cloud SQL

## 3. 连接关系

- User → wiki-interface → evaluator
- evaluator → Redis (缓存)

## 4. Mermaid 预览

```mermaid
graph LR
    User --> wiki[wiki-interface]
    wiki --> eval[evaluator]
    eval --> Redis
```

## 5. ⚠️ 工具选项表

**检测到场景**: 云架构图

| 方案 | 工具 | 速度 | 质量 | 输出格式 | 说明 |
|------|------|------|------|----------|------|
| **A** | `diagrams` | ⚡ 快 | ★★★★ | PNG/SVG | 云图标丰富，专业 |
| **B** | `graphviz` | ⚡ 快 | ★★★ | PNG/SVG/PDF | 通用流程图风格 |
| **C** | `PlantUML` | ⚡ 快 | ★★★ | PNG/SVG | 需 Java 环境 |

**💡 推荐**: 方案 A (`diagrams`) - 专为云架构设计，图标更专业

---

## 请确认

1. 架构理解是否正确？组件是否需要增减？
2. 连接关系是否准确？
3. 布局方向偏好（左右 LR / 上下 TB）？
4. **请选择工具方案: [A] / [B] / [C]？（直接回复字母，或回复"用推荐"）**

确认后我将生成专业的架构图。
```

### Phase 2: Code Generation & Execution

After user confirms, generate Python code following these rules:

#### Output Configuration
```python
with Diagram(
    "Diagram Name",
    filename="./pic/{subfolder}/{name}",  # Output to pic subdirectory
    outformat=["png", "svg"],              # Both formats
    show=False,                            # Don't auto-open
    direction="LR"                         # Left-to-right by default
):
```

#### Directory Setup
Before execution, ensure output directory exists:
```python
import os
os.makedirs("./pic/{subfolder}", exist_ok=True)
```

#### Code Structure Template
```python
from diagrams import Diagram, Cluster, Edge
# Import nodes based on cloud provider
# from diagrams.gcp.compute import Run, ComputeEngine
# from diagrams.aws.compute import EC2, Lambda
# from diagrams.k8s.compute import Pod, Deployment

import os
output_dir = "./pic/{diagram_name}"
os.makedirs(output_dir, exist_ok=True)

with Diagram(
    "{Diagram Title}",
    filename=f"{output_dir}/{diagram_name}",
    outformat=["png", "svg"],
    show=False,
    direction="LR"
):
    # Define clusters and nodes
    with Cluster("Cluster Name"):
        node1 = ServiceType("Label")
    
    # Define connections
    node1 >> Edge(label="description") >> node2
```

### Phase 3: Save Code & Result Feedback

After execution:
1. **Save the Python source code** to `./pic/{name}/{name}.py` (same folder as generated images)
2. Report generated file paths:
   - `./pic/{name}/{name}.py` (source code)
   - `./pic/{name}/{name}.png`
   - `./pic/{name}/{name}.svg`
3. If errors occur, analyze and fix automatically

## Node Import Reference

See [references/diagrams-api.md](references/diagrams-api.md) for complete node import paths.

### Quick Reference - Common Providers

| Provider | Import Pattern | Example |
|----------|---------------|---------|
| GCP | `diagrams.gcp.{category}` | `from diagrams.gcp.compute import Run` |
| AWS | `diagrams.aws.{category}` | `from diagrams.aws.compute import EC2` |
| Azure | `diagrams.azure.{category}` | `from diagrams.azure.compute import VM` |
| K8s | `diagrams.k8s.{category}` | `from diagrams.k8s.compute import Pod` |
| Generic | `diagrams.generic.{category}` | `from diagrams.generic.compute import Rack` |
| On-Premise | `diagrams.onprem.{category}` | `from diagrams.onprem.database import PostgreSQL` |

### Common Categories
- `compute`: EC2, Run, Pod, VM
- `database`: RDS, SQL, PostgreSQL, Redis
- `network`: ELB, VPC, DNS, CDN
- `storage`: S3, GCS, PersistentDisk
- `analytics`: BigQuery, Dataflow
- `ml`: SageMaker, VertexAI
- `security`: IAM, KMS, WAF
- `client`: User, Users, Client

## 扩展能力：多种 Python 绑图库支持

除了 `diagrams` 库用于架构图，本 Skill 支持根据用户需求动态选择合适的 Python 绘图库：

| 场景 | 推荐库 | 安装命令 | 适用场景 |
|------|--------|----------|----------|
| 云架构图 | `diagrams` | `pip install diagrams` | AWS/GCP/Azure/K8s 架构可视化 |
| 数据可视化 | `matplotlib` | `pip install matplotlib` | 折线图、柱状图、散点图、饼图等 |
| 统计图表 | `seaborn` | `pip install seaborn` | 高级统计图、热力图、分布图 |
| 交互式图表 | `plotly` | `pip install plotly` | 可交互的 Web 图表、3D 图 |
| 流程图/思维导图 | `graphviz` | `pip install graphviz` | 流程图、状态机、决策树 |
| 网络拓扑图 | `networkx` + `matplotlib` | `pip install networkx` | 网络关系图、图论可视化 |
| 甘特图/时序图 | `plotly` / `matplotlib` | - | 项目管理、时间线 |

## Design Best Practices

1. **Use Clusters** for logical grouping (VPC, Region, Service Group)
2. **Direction**: Use `LR` (left-right) for wide diagrams, `TB` (top-bottom) for tall ones
3. **Edge labels**: Add `Edge(label="HTTP")` for connection descriptions
4. **Consistent naming**: Use clear, descriptive labels
5. **Color coding**: Leverage built-in provider colors for visual distinction

## 输出格式指南

| 格式 | 适用场景 | 工具支持 |
|------|---------|---------|
| **PNG** | 通用展示、PPT、网页 | 所有工具 |
| **SVG** | 网页嵌入、可缩放 | matplotlib, diagrams, plotly |
| **PDF** | 论文插图、打印 | TikZ (原生), matplotlib |
| **HTML** | 交互式展示 | plotly |
