---
source-git-commit: e0ecfa4d74b8fcc0bbaf35d44c33c725a1b1a539
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%
---
# 类别overview.md模板

`help/blueprints/architecture-diagrams/`下的每个类别文件夹都需要一个看起来像其他五个类别文件夹的`overview.md`。 请使用此确切的结构。

## Frontmatter

```yaml
---
title: {Category Label}
description: {One-sentence summary of what this category covers.}
solution: {Primary Adobe solution(s), comma-separated}
doc-type: overview-page
---
```

不要在新页面上包含`exl-id`、`product_v2`、`feature_v2`、`role_v2`、`topic_v2`、`TQID`、`kt`或`thumbnail` — 发布管道会自动填充这些内容。

## 正文

```markdown
# {Category Label}

{1-3 paragraph intro describing what this category of diagrams covers and why it matters.}

| Diagram | Description |
| --- | --- |
| [{Page title}]({filename}.md) | {One-sentence description of the page} |
| [{Page title}]({filename}.md) | {One-sentence description of the page} |
```

规则：

- 按页面在TOC.md中的显示顺序列出该类别中的每个页面。
- 链接目标是相对的文件名（无`/help/blueprints/...`前缀），因为概述与其同级页面一起存在。
- 描述是一句句子，如果读起来像标签，则不需要后置句点。
- 如果类别具有自然的子分组（例如，客户历程下的“已弃用的图表”），请以相同格式添加一个`## {Sub-group name}`标题，后跟其自己的两列表 — 请勿在表中混合使用图表缩略图或额外的列。
- 请勿在此表中嵌入`<img>`关系图缩略图。 将其保留为两列：`Diagram` （链接）和`Description` （文本）。 缩略图属于单个内容页面，而不是类别概述。
- 不要在表单元格中使用嵌套的`<ul><li>` HTML。 仅限纯文本。

## 示例（客户分析）

```markdown
---
title: Customer Insights
description: Unify and analyze data and customer behaviors from across the customer journey
solution: Customer Journey Analytics
doc-type: overview-page
---
# Customer Insights

Customer Journey Analytics shows how brands can unify customer data and behavior from various interaction channels and sources to create a journey-based view of all customer interactions.

| Diagram | Description |
| --- | --- |
| [Adobe Customer Journey Analytics](cja.md) | Core Customer Journey Analytics architecture, including B2B and audience-sharing derivations |
| [Adobe Customer Journey Analytics & Adobe Journey Optimizer integration](cja-ajo-integration.md) | Campaign and journey insights integration between Customer Journey Analytics and Journey Optimizer |
```
