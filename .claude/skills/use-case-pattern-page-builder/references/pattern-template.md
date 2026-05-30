---
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 48%

---
# 用例模式模板

此文件包含用例模式页面的完整Markdown模板。 在生成新模式时，将所有`{{placeholder}}`值替换为实际内容。

&#x200B;---

## 模板

````markdown
---
title: {{Pattern Title}}
description: {{One-sentence description of what this pattern teaches}}
solution: {{Comma-separated Adobe solutions}}
exl-id: {{generate-uuid-placeholder}}
---
# {{Pattern title}}

This guide provides an overview of {{pattern name}} using {{solutions with [!DNL ...] formatting}}. It is designed for solution architects, marketing technologists, and implementation engineers who need to {{primary capability description}}.

## Use case pattern

**{{Pattern Name}}**

{{One-two sentence description of what the pattern does and enables.}}

**Execution plan:** {{Step 1}} > {{Step 2}} > {{Step 3}} > {{Step 4}} > {{Step 5}}

## Use case overview

{{Paragraph 1: Define the pattern. What does it do? How does it differ from related patterns? Provide a clear, specific definition.}}

{{Paragraph 2: Describe the typical trigger or starting condition. When does this pattern apply? What event, schedule, or condition initiates it?}}

{{Paragraph 3: Describe what the pattern delivers. What is the end result for the customer or business? What channels or touchpoints does it affect?}}

{{Paragraph 4: Clarify scope boundaries. What does this pattern NOT cover? What adjacent patterns handle those needs? Reference other patterns by name if relevant.}}

{{Paragraph 5 (optional): Identify typical stakeholders and teams involved in implementation. Who owns what?}}

## Key business objectives

The following business objectives are supported by this use case pattern.

**[{{Objective Name}}](../../business-objectives/{{category}}/{{objective-file}}.md)**

{{Brief description of how this pattern supports the objective -- 1-2 sentences.}}

| KPIs |
| --- |
| {{KPI1}}, {{KPI2}}, {{KPI3}} |

{{Repeat the above block for each supported business objective.}}

## Example tactical use cases

The following scenarios illustrate how {{pattern name}} can be applied across different business contexts.

- **{{Scenario name}}** -- {{Description of the scenario and how it uses this pattern}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
{{Include 6-10 scenarios total}}

## Key performance indicators

| KPI | Description | Measurement |
| --- | --- | --- |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}

## Related documentation

The following resources provide additional detail on the capabilities used in this pattern. Group the reference links to primary Experience League documents under descriptive subheadings.

### {{Topic group}}

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})

### {{Topic group}}

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})
````

&#x200B;---

## 关于使用此模板的注释

- **YAML frontmatter：** `exl-id`应为占位符UUID（例如，`xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`）。 发布管道分配实际值。
- **节顺序：** `Use case pattern`节紧跟在开始介绍之后，在`Use case overview`之前。 它给读者提供了一个清晰的单行定义和高级执行计划。
- **Adobe产品名称：**&#x200B;在正文和表中始终使用Adobe产品名称的`[!DNL ...]`语法（例如`[!DNL Journey Optimizer]`）。 这是一项阻止翻译产品名称的Experience League约定。
- **业务目标链接：**&#x200B;使用从模式文件到业务目标目录： `../../business-objectives/{{category}}/{{filename}}.md`的相对路径。
- **Kebab-case文件名：**&#x200B;模式文件名必须是派生自模式标题的kebab-case。 示例：“事件触发的消息传递”变为`event-triggered-messaging.md`。
- **执行计划：**&#x200B;使用` > `（空格、大于、空格）作为步骤之间的分隔符。 保留标签恰好`**Execution plan:**`。
- **相关文档：**&#x200B;描述性`###`子标题下的组引用链接（例如，按应用程序或功能区域）。 这些是Experience League对模式中使用的应用程序和功能的引用。
- **架构（可选）：**&#x200B;如果模式从参考架构图中获益，则可以在`Applications`和`Related documentation`之间放置可选`## Architecture`部分。
- **范围：**&#x200B;此模板刻意排除详细的实施部分（基础/支持/应用程序功能、先决条件、实施选项和分阶段实施步骤）。 这些详细信息位于从`Related documentation`链接的Experience League文档中。