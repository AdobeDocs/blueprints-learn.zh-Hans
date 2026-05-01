---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---
# Blueprint评估规则

此规则适用于“架构图和Blueprint”部分下的每个文档
/[TOC.md](../help/blueprints/TOC.md)（第76-133行），以建议是否应将每个Blueprint变为
**用例模式**、**架构图**、二者(**Split**)或标记为
**复制现有模式的**。

应用此规则的输出为[blueprint-audit.md](blueprint-audit.md)。

## 定义

- **用例模式** — 描述特定业务或技术目标和
概述实现这一目标可采取的实施办法和考虑因素。
规范形状： `.claude/skills/use-case-pattern-builder/references/pattern-template.md`。
- **架构图** — 表示系统功能的可视化图表
集成和数据流。 最简单的叙述，图表是人造物品。
规范示例： [platform-data-flow.md](../help/blueprints/experience-platform/platform-data-flow.md)。

## 得分

每个Blueprint都是端到端读取的，并根据8个二进制信号进行评分。 每个信号都有
+1表示模式分数或关系图分数。

### 模式信号（每个= +1模式）

1. **业务目标框架** — 框架收入、保留、收购、潜在客户拓展、成本
减少、客户体验或类似业务成果。
2. **KPI或成功量度** — 明确指定量度、转化率、匹配率、ROI或
类似的结果衡量标准。
3. **多个实施选项或成熟度层** — 提供选项A/选项B，基本与
高级或类似的替代方案，供读者选择。
4. **先决条件或准备工作清单** — 列出在实施之前必须实施的项目。
5. **叙述性实施步骤> ~30行** — 实质性的实施方法指导，而不是
只是个简单的概述。

### 图表信号（每个= +1图表）

&#x200B;6. **架构/数据流映像存在** — `.svg`、`.png`或`.jpg`显示系统拓扑，
数据流或集成箭头。
&#x200B;7. **系统到系统集成拓扑、部署形状或护栏** — 说明如何
组件连接，数据存留的地方、部署模型（边缘与中心）或容量限制。
&#x200B;8. **受众是解决方案架构师** — 框架使用部署、SDK、edge、hub或类似项
面向架构师的术语而不是面向营销人员的框架(营销活动、历程、
受众)。

## 推荐逻辑

首先应用覆盖规则。 如果没有触发覆盖，则从得分获取推荐。

### 覆盖规则（最高优先级）

1. **文件名为`overview.md`**，→推荐= `Navigation`。 被排除在迁移之外；
页面是TOC样式的登陆页面，在子文件结算后将对其进行修订。
2. **`help/blueprints/use-case-patterns/`**&#x200B;中已存在对等模式→
推荐= `Duplicate`。 迁移操作是将Blueprint简化为纯粹的
架构图并向现有模式添加“查看用例模式”交叉链接。
在`duplicate_of`列中记录现有的模式路径。
3. **文件在`experience-platform/`中，没有业务目标信号(#1)**→默认为
   `Diagram`，不考虑其他得分。 此文件夹是体系结构概述层。

### 基于分数的推荐（不触发覆盖时）

| 模式得分 | 关系图分数 | 推荐 | 推理 |
| --- | --- | --- | --- |
| ≥ 3 | ≤ 1 | `Pattern` | 强模式信号、弱图信号→向模式迁移。 |
| ≤ 1 | ≥ 2 | `Diagram` | 弱图案信号，主视觉/拓扑聚焦→保持为图。 |
| ≥ 3 | ≥ 2 | `Split` | 将丰富的模式内容和有意义的图→抽取模式，将原始模式简化为图、交叉链接。 |
| 2 | 2 | `Split` | 以中等强度打平分→。 |
| 2 | ≤ 1 | `Pattern` | 模式倾斜，没有重要的图表值。 |
| ≤ 1 | ≤ 1 | `Diagram` | 总体精简 — 可能是现有的最低体系结构页面。 |

## 如何应用评分标准

对于范围内的每个Blueprint Markdown文件：

1. 端到端地读取完整文件。
2. 标记八个信号中的每一个存在/不存在。
3. 按顺序应用覆盖规则。 如果触发，则为推荐。
4. 否则，计算模式得分和图表得分并查找推荐。
5. 对于`Pattern`和`Split`推荐，建议：
   - `proposed_pattern_category` — 其中之一：
     `audience-building-activation`, `personalization`, `campaign-management-orchestration`,
     `analysis`、`conversational-experience`或标记为`(new) <name>`的新类别。
   - `proposed_pattern_title` — 遵循现有模式的面向操作的简短标题
命名样式。
6. 对于`Diagram`和`Split`推荐，建议：
   - `proposed_diagram_title` — 通常将现有标题修剪为业务框架。
7. 通过将Blueprint的作用域与现有模式目录进行比较，捕获发现的任何重复项
在`duplicate_of`中。
8. 在`notes`中记录未完成的问题、值得保留的独特技术内容或迁移风险。

## 现有用例模式目录（用于重复检测）

| 类别 | 模式 |
| --- | --- |
| audience-building-activation | audience-activation-to-destinations， audience-collaboration-segment-match， b2b-audience-activation，事件转发 |
| 个性化 | anonymous-visitor-web-personalization， known-visitor-web-app-personalization， offer-decisioning，行为推荐 |
| campaign-management-orchestration | 批量出站消息激活、事件触发消息传递、多步协调历程、跨渠道历程与决策、基于购买群组的营销 |
| 分析 | customer-analytics-insight-generation， b2b-analytics |
| 对话体验 | 品牌礼宾对话体验 |
