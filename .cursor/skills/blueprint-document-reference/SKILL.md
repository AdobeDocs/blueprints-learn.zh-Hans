---
name: blueprint-document-reference
description: 有关创建和编辑Adobe Digital Experience Blueprint文档的参考。 在创建新Blueprint、添加Blueprint页面，或用户询问Blueprint结构、区域、模板或引用Adobe Experience League时使用。
source-git-commit: dfa21942ecf2a1db06df6f6cc945f5572811ca93
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 1%

---


# Blueprint文档引用

在此存储库中创建或编辑Blueprint文档时使用此技能。 Blueprint是可重复的实施，用于解决已确定的业务问题，包括架构图、技术注意事项以及Adobe Experience League文档链接。

## 何时应用

- 创建新的Blueprint文档或Blueprint概述页面
- 在现有Blueprint中添加或重新构建区域
- 链接或引用Adobe Experience League文档
- 将新内容与Blueprint约定（前件、标题、图表）对齐

## 快速参考

1. **文档目的**： Blueprint提供系统和数据流架构，以显示Adobe Experience Platform和应用程序的集成方式。 它们是视觉和技术性的，而不是营销性的。
2. **节**：使用模板中的标准节；仅在不适用时省略（请参阅[reference.md](reference.md)）。
3. **Experience League**：首选链接到Experience League以获取产品文档、API、护栏和教程。 使用完整的URL；有关URL模式和格式，请参阅[reference.md](reference.md)。
4. **存储库结构**： Blueprint位于`help/blueprints/`下。 添加或移动Blueprint页面时更新`help/blueprints/TOC.md`。

## 文档模板

每个Blueprint页面都应遵循此结构。 仅包括适用的部分。

```markdown
---
title: [Short descriptive title]
description: "[One sentence: what this blueprint shows and why it matters.]"
solution: [Product name, e.g. Real-Time Customer Data Platform, Journey Optimizer]
exl-id: [UUID - leave blank if new, this will be auto-generated as part of the Experience League publishing flow]
---
# [H1 - same as title or expanded]

[1–3 paragraphs: what the blueprint covers, key capabilities, and who it’s for.]

## Applications

* [Product 1]
* [Product 2]

## Use cases

* [Use case 1]
* [Use case 2]

## Prerequisites

[Bullets or short paragraphs: required products, config, or setup.]

## Architecture Diagram

<img src="[path to SVG/image]" alt="[Descriptive alt]" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Guardrails

[Link to Experience League guardrails and any blueprint-specific limits.]

## Implementation patterns

[Optional: named patterns with bullets.]

## Implementation steps

1. [Step with link to Experience League where relevant]
2. ...

## Implementation considerations

[Optional: identity, performance, security, etc.]

## Related documentation

[Grouped links to Experience League: product docs, APIs, tutorials.]
```

对于概述页面或中心页面，请使用较短的结构：简介、用例（或选项卡）、架构图像、方案/阵列表、先决条件、护栏、相关文档。 有关示例，请参阅`help/blueprints/`中的现有概述。

## Frontmatter

| 字段 | 必填 | 备注 |
|-------|----------|--------|
| `title` | 是 | 短；按Adobe样式使用`[!DNL Product Name]`作为产品名称 |
| `description` | 是 | 一个句子；用于搜索和卡片 |
| `solution` | 是 | 主要产品(例如Real-Time Customer Data Platform、Journey Optimizer) |
| `exl-id` | 是 | UUID；留空则创建新页面 |
| `doc-type` | 概述 | 将`overview-page`用于主Blueprint概述页面 |
| `kt` | 可选 | 知识库文章ID（如果已链接） |

## 引用Adobe Experience League

- **何时链接**：链接到Experience League，获取产品文档、API引用、护栏、教程和配置步骤。 不要重复冗长的过程；摘要和链接。
- **URL格式**：使用完整的URL。 首选`https://experienceleague.adobe.com/docs/?lang=zh-Hans...`或`https://experienceleague.adobe.com/zh-hans/docs/...`。 对于开发人员文档，`https://developer.adobe.com/...`也有效。
- **链接文本**：使用描述性文本（例如，“[创建架构] (url)”，而不是“单击此处”）。 对于链接文本中的产品名称，请酌情使用`[!DNL Product Name]`。
- **相关文档部分**：使用“相关文档”部分结束Blueprint并按类别对链接进行分组(例如，目标配置、SDK文档、配置文件和分段、教程)。

有关详细的URL模式、链接分组和示例，请参阅[reference.md](reference.md)。

## 提交前清单

- [ ] Frontmatter具有`title`、`description`、`solution`、`exl-id`
- [ ] H1匹配或适当扩展标题
- [ ]架构图显示和替换文本描述性
- [ ]实施步骤链接到Experience League，过程位于此处
- [ ]护栏部分链接到官方的Experience League护栏文档
- [ ]相关文档部分包含相关的Experience League链接
- [ ]个新页面或移动页面反映在`help/blueprints/TOC.md`中

## 其他资源

- 完整模板和部分注释： [reference.md](reference.md)
- 现有Blueprint： `help/blueprints/` （例如`audience-activation/real-time-lookup.md`，`customer-journeys/journey-optimizer/journey-optimizer-overview.md`）
- 目录和导航： `help/blueprints/TOC.md`
