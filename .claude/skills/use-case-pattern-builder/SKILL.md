---
name: use-case-pattern-builder
description: 为Adobe Experience Platform Blueprint存储库创建新的用例模式内容指南。 在添加新用例模式、创建实施指导内容或用户提及向Blueprint站点添加模式时，请使用此技能。 处理完整的工作流程：收集模式信息，生成具有正确模板结构的Markdown文件，并更新所有交叉引用页面(TOC.md、overview.md)。
source-git-commit: ed8928687806b619e95d8d320478d27c13722a80
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 0%

---


# 用例模式生成器

此技能可指导Adobe Experience Platform Blueprint存储库创建新的用例模式。 它处理整个工作流：从用户那里收集模式信息，生成具有正确模板结构的Markdown内容文件，并更新所有交叉引用页面，以便发现新模式。

开始之前，请阅读以下参考文件，以了解完整的模板结构和要更新的页面核对清单：

- `references/pattern-template.md` — 带占位符值的完整Markdown模板
- `references/pages-to-update.md` — 添加模式时必须更新的页面清单

## 第1阶段：信息收集

在生成任何文件之前询问用户以收集所有必需的信息。 询问以下问题，并且在提供每个项目或明确延迟提供每个项目之前，不要继续生成内容。

### 所需信息

1. **模式名称** — 易于用户识别的标题（例如，“事件触发的消息传递”）。

2. **类别** — 刚好是以下之一：
   - `audience-building-activation`
   - `personalization`
   - `campaign-management-orchestration`
   - `analysis`
   - `conversational-experience`

3. **主要功能描述** — 描述此模式的用途的单个句子（用于概述表和frontmatter描述）。

4. **核心Adobe解决方案** — Adobe产品是此模式的中心。 根据需要从Journey Optimizer、Real-Time Customer Data Platform、Experience Platform、Customer Journey Analytics、Brand Concierge、Journey Optimizer B2B edition、Real-Time CDP B2B edition或其他中进行选择。

5. **函数链步骤** — 描述模式执行流的3-6个顺序阶段，以`>`分隔。 示例：“Event Ingestion > Event Entry > Condition Evaluation > 历程投放>报告”。

6. **支持的业务目标** — 来自`/help/blueprints/business-objectives/`下的现有集的一个或多个业务目标。 每个名称都应包括目标名称、类别子文件夹和文件名。 在生成内容之前，请验证引用的文件是否存在。

7. **战术用例示例** — 6-10个项目符号场景，描述如何在不同业务环境中应用此模式。 每个模板都应该有一个粗体方案名称，后跟一个说明。

8. **KPI** — 包含三列的表：KPI（名称）、描述（度量值）、度量（公式或方法）。

9. **实施选项** — 2-4个实施选项。 对于每个选项，收集：
   - 选项名称
   - 最适合（何时使用此选项）
   - 工作原理（2-4段）
   - 关键注意事项（项目符号列表）
   - 优势（项目符号列表）
   - 限制（项目符号列表）
   - Experience League链接（指向相关文档的URL）

### 可选，但推荐

- 用例概述段落（3-5段；如果未提供，则从其他信息中草稿）
- 应用程序列表，其中包含每个Adobe应用程序的角色描述
- 基础函数表（函数、状态、必须就地的内容、Experience League引用）
- 支持函数表（“函数”、“状态”、“为何重要”、“Experience League参考”）
- 应用程序函数表（每个应用程序一个，具有函数、实施阶段和说明）
- 先决条件核对清单

如果用户不提供可选项目，则根据模式类别、解决方案和功能链生成合理的默认值。

## 阶段2：内容生成

在以下路径生成模式Markdown文件：

```
/help/blueprints/use-case-patterns/{category}/{kebab-case-pattern-name}.md
```

文件名必须使用从模式名称派生的kebab大小写。 例如，“事件触发的消息传递”变为`event-triggered-messaging.md`。

使用`references/pattern-template.md`中的模板并使用收集的信息填写所有占位符值。 生成的文件必须包含模板中的每个部分：

1. **YAML frontmatter** — title、description、solution（逗号分隔）、exl-id（生成类似`xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`的UUID占位符 — 发布团队将分配实际占位符）。

2. **打开部分** — `# {Pattern name}`标题，后面是介绍性段落和“使用本指南了解……” 句子。

3. **用例概述** — 3-5个段落，描述模式范围、适用时间、操作和不操作以及典型利益相关者是谁。

4. **关键业务目标** — 每个目标都作为链接标题，带有简要说明和KPI摘要行。

5. **战术用例示例** — 6-10个方案的项目符号列表。

6. **关键绩效指标** — 包含KPI、说明和度量列的表。

7. **用例模式** — 描述段落和函数链。

8. **应用程序** — 具有`[!DNL ...]`格式和描述的Adobe应用程序列表。

9. **基础函数** — 包含列的表：基础函数、状态、必须就地的、Experience League引用。 状态值：必需，假定已就位，不适用。

10. **支持函数** — 带列的表：支持函数、状态、它的重要性原因、Experience League引用。 状态值：推荐、已包含、不适用。

11. **应用程序函数** — 每个应用程序有一个表，该表具有列：函数、实现阶段、描述。

12. **先决条件** — 使用`- [ ]`语法的清单。

13. **实施选项** — 2-4个详细选项，每个选项都具有Best for、工作方式、关键注意事项、优势、限制和Experience League链接。

14. **选项比较** — 末尾的摘要比较表。

## 阶段3：交叉引用更新

生成图案文件后，更新以下文件。 请阅读`references/pages-to-update.md`以了解详细核对清单。

### TOC.md

**文件：** `/help/blueprints/TOC.md`

在正确的类别部分下添加新条目。 类别映射到以下目录部分：

| 类别概要 | 目录章节标题 |
| --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation{#audience-building-activation}` |
| `personalization` | `+ Personalization{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience{#conversational-experience-patterns}` |

条目格式为：

```
    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)
```

在匹配部分的最后一个现有条目之后添加新条目。 保留确切的缩进（`+`前有四个空格）。

### “概述”页面

**文件：** `/help/blueprints/use-case-patterns/overview.md`

向正确的类别表添加新行。 格式为：

```
| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |
```

在匹配类别表中最后一个现有行之后添加新行。

## 第4阶段：验证

创建并更新所有文件后，请验证以下各项：

1. **业务目标链接** — 模式文件中的每个业务目标链接指向`/help/blueprints/business-objectives/`下的现有文件。 使用glob或read确认每个目标文件都存在。

2. **目录条目位置** — 新的目录条目位于正确的类别部分中，并使用正确的缩进和路径格式。

3. **概述表行** — 新的概述行位于正确的类别表中，并且遵循与现有行相同的列格式。

4. **文件命名** — 模式文件名使用kebab大小写，并与TOC.md和overview.md中引用的路径匹配。

5. **Frontmatter完整性** — 模式文件在其YAML frontmatter中包含标题、描述、解决方案和exl-id。

6. **Experience League链接** — 抽查所有Experience League URL是否合理（以`https://experienceleague.adobe.com/zh-hans`开头）。

向用户报告任何验证失败，并在考虑任务完成之前修复它们。

## 注释

- 在表和正文文本中，始终使用用于Adobe产品名称的`[!DNL ...]`语法，遵循现有模式文件的约定。
- frontmatter中的`exl-id`应为占位符UUID。 发布管道分配实际值。
- 如果用户希望一次创建多个模式，请对每个模式重复第2-4阶段，但在第1阶段中收集所有信息。
- 如果需要上述列表中不存在的新类别，请警告用户TOC.md和overview.md需要创建新分区，并作为单独的步骤进行处理。
