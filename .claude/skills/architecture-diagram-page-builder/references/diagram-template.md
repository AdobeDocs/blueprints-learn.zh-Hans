---
source-git-commit: 83e85d946e455cde46001af0a2112637b7fe24cc
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---
# 架构图页面模板

这是架构图页面的完整Markdown模板。 将每`{placeholder}`替换为在技能工作流的阶段1中收集的值。 移除任何不适用的可选部分（例如`>[!MORELIKETHIS]`块） — 不要在生成的文件中保留空占位符。

&#x200B;---

```markdown
---
title: {Page title}
description: {1-2 sentence page purpose, used for search snippets and previews}
solution: {Comma-separated Adobe solutions, e.g. Experience Platform, Journey Optimizer, Customer Journey Analytics}
---
# {Page title}

{Opening paragraph -- 1-2 sentences describing what the diagrams collectively illustrate. Frame the page as a top-level architecture reference, not a use case walkthrough.}

>[!MORELIKETHIS]
>
>[{Related-content link text}]({Related-content URL}).

## {Diagram 1 section title}

{1-2 sentence explanation of what the diagram shows and why it matters.}

<img src="assets/{filename-1}" alt="{Alt text for diagram 1}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## {Diagram 2 section title}

{1-2 sentence explanation.}

<img src="assets/{filename-2}" alt="{Alt text for diagram 2}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Primary data flows and integration points

- {Flow or integration 1 -- e.g., "Real-time event ingestion from [!DNL Web SDK] to [!DNL Edge Network]"}
- {Flow or integration 2 -- e.g., "Profile sync between [!DNL Experience Platform] Hub and Edge"}
- {Flow or integration 3}
- {Flow or integration 4}
- {Flow or integration 5}

## Use case patterns supported

The architecture above supports the following use case patterns:

- [{Pattern 1 name}](/help/blueprints/use-case-patterns/{category}/{pattern-1-file}.md) -- {1-line note on why this architecture enables the pattern}
- [{Pattern 2 name}](/help/blueprints/use-case-patterns/{category}/{pattern-2-file}.md) -- {1-line note}
- [{Pattern 3 name}](/help/blueprints/use-case-patterns/{category}/{pattern-3-file}.md) -- {1-line note}

## Further reading

- [{Article 1 title}]({Experience League URL 1})
- [{Article 2 title}]({Experience League URL 2})
- [{Article 3 title}]({Experience League URL 3})
```

&#x200B;---

## Frontmatter规则

- **必填字段：** `title`，`description`，`solution`。
- **禁止的字段**（发布时自动分配）： `exl-id`，`product_v2`，`feature_v2`，`role_v2`，`topic_v2`，`TQID`，`kt`，`thumbnail`。 请勿将它们包含在新编写的文件中。

## 正文约定

- **一个H1** — 页面标题。 与`title`前件完全匹配。
- **每个关系图一个H2。** 图节中没有H3；请将其保留为1-2句介绍以及图像。
- **`<img>`嵌入** — 需要内联样式和`class="modal-image"`。 它们驱动Experience League模式缩放交互。
- **图像路径** — 始终为`assets/{filename}`（相对于页面的主题文件夹）。 请勿使用绝对路径。
- **Adobe产品名称** — 在正文和项目符号中以`[!DNL ...]`换行。 示例： `[!DNL Real-Time CDP]`，`[!DNL Journey Optimizer]`，`[!DNL Experience Platform]`。
- **用例模式链接** — 始终使用绝对`/help/blueprints/use-case-patterns/{category}/{file}.md`表单，以便该链接从任何可能包含此内容的页面中解析。
- **Experience League链接** — 以`https://experienceleague.adobe.com/zh-hans`开头的绝对URL。 与本地化的变体相比，更喜欢规范文档URL。

## 章节排序

在所有架构页面上保持顺序一致，以便读者可以按预期扫描：

1. Frontmatter
2. H1 +打开段落
3. （可选） `>[!MORELIKETHIS]`标注
4. 每个图表一个H2（按用户指定的顺序）
5. `## Use case patterns supported`
6. `## Primary data flows and integration points`
7. `## Further reading`

## 长度预期

典型的Markdown为40-100行。 如果页面超过150行，则内容可能迁移到用例模式区域 — 重新检查`scope-guardrails.md`并考虑拆分。
