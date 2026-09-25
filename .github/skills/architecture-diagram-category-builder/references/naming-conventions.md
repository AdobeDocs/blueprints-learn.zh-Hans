---
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%
---
# 命名约定：架构图和Blueprint

此文档是`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`下的类别命名方式的真实来源。 `architecture-diagram-category-builder`技能（新类别）和`architecture-diagram-page-builder`技能（现有类别中的新页面）都必须遵循这些规则。

## 规则

**文件夹名称= TOC锚点概要=完整TOC标签的kebab大小写。** 所有三个必须完全匹配，无缩写或截断。

| TOC标签 | 锚点 | 文件夹 |
| --- | --- | --- |
| 架构概述 | `#architecture-overviews` | `architecture-overviews/` |
| 受众和用户档案激活 | `#audience-profile-activation` | `audience-profile-activation/` |
| B2B激活和营销 | `#b2b-activation-marketing` | `b2b-activation-marketing/` |
| 客户洞察 | `#customer-insights` | `customer-insights/` |
| 客户历程 | `#customer-journeys` | `customer-journeys/` |

这是所有五个类别（截至2026-09-16年）的目前更正状态。 在此存储库的历史记录中，某些存储库的缩写(`architecture-overview`、`audience-activation`、`b2b-activation`) — 该不一致已修复。 不要为新类别或现有类别重新引入缩写文件夹/锚点名称。

## 为什么这很重要

- **可预测性。** 参与者（人工或代理）应能够从TOC标签猜出文件夹路径（反之亦然），而无需打开TOC.md。
- **安全自动化。** 仅当映射精确且机械化（kebab大小写，无缩写）时，从标签（或路径标签）生成路径的技能和脚本才能可靠工作。
- **重定向卫生。** 每次重命名都需要`redirects.csv`中的新条目。 从一开始保持名称稳定且具有完全描述性可避免重复的重命名流失。

## 如何从标签派生概要

1. 将标签小写。
2. 完全删除`&`并用连字符连接周围的单词（例如`Audience & Profile Activation` -> `audience-profile-activation`）。
3. 将空格替换为连字符。
4. 去除除连字符外的标点符号。
5. 请勿在标签中缩写、截断或丢弃单词（对于“B2B激活和营销”，无`b2b-activation`，请使用`b2b-activation-marketing`）。

## 每个类别所需的资产

直接位于`help/blueprints/architecture-diagrams/`下的每个类别文件夹都必须包含：

1. **`overview.md`** — 类别的登陆页面。 有关所需结构，请参阅`./category-overview-template.md`。 每个类别概览页面看起来必须相同：介绍段落，然后单个`| Diagram | Description |`表列出类别中的每个页面（按目录顺序）。 不要使用嵌套的`<ul><li>`单元格、嵌入的图图像或第三列 — 与现有五个类别完全匹配。
2. **`assets/`** — 图表图像的文件夹，即使在创建时为空也是如此（添加第一个图表后即创建它）。

## TOC.md要求

- 类别的`+ [Overview](/help/blueprints/architecture-diagrams/{folder}/overview.md)`条目始终是类别标题下的&#x200B;**第一个**&#x200B;条目，位于任何内容页面之前。
- 类别标题及其锚点紧靠在`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`下，与其他五个类别处于相同的2空格缩进级别。
- 内容页面缩进4个空格（`+`以四个前导空格为前缀）。 嵌套的子分组（例如Audience &amp; Profile Activation下的RTCDP分组）以6个空格缩进。

## 登陆页面要求

`help/blueprints/architecture-diagrams/overview.md` （顶级架构图和Blueprint登陆页面）的每个类别必须只有一个卡片（按目录顺序）。 每张卡片：

- 链接到类别的`overview.md`（不是内容页面）。
- 使用该类别的`assets/`文件夹中的代表性图表图像作为缩略图，样式为标准卡片CSS （`background-color:#ffffff; border:1px solid #d3d3d3;`加上文件中已存在的共享大小/填充规则）。
- 包括类别名称（粗体/强）以及与类别概述简介相匹配的一句说明。

当类别数是3的倍数时，表将渲染为干净的完整行（3列，`table-layout:fixed`，每个单元格`width:33%`）。 如果不是3的倍数，请在最后一行中为每个缺失的插槽添加一个空的`<td>`（不要使表不整齐/无样式）。
