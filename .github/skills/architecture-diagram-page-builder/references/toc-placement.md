---
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%
---
# TOC.md放置引用

技能生成新的架构图页面时，必须向`/help/blueprints/TOC.md`添加一个条目，以便该页面可在站点导航中找到。 本文档准确地定义该条目的位置和方式。

## 父分区

所有架构图页面都位于TOC.md中的顶级`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`部分下。 在该部分中，多个子部分按主题对页面进行分组。

这些子部分的文件夹名称、目录锚点以及目录标签必须遵循`../../architecture-diagram-category-builder/references/naming-conventions.md`中的命名规则 — 如果需要新类别，请查看该文件（针对该类别使用`architecture-diagram-category-builder`技能，而非该类别）。

## 子区域映射

选取与新页面的主题文件夹匹配的子部分：

| 主题文件夹 | TOC子节标题 |
| --- | --- |
| `architecture-diagrams/architecture-overviews/` | `+ Architecture overviews{#architecture-overviews}` |
| `architecture-diagrams/audience-profile-activation/` | `+ Audience & Profile Activation{#audience-profile-activation}` |
| `architecture-diagrams/b2b-activation-marketing/` | `+ B2B activation & marketing{#b2b-activation-marketing}` |
| `architecture-diagrams/customer-insights/` | `+ Customer Insights{#customer-insights}` |
| `architecture-diagrams/customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

如果用户提议的主题文件夹不在此表格中，则将其视为新的顶级子部分并暂停 — 要求用户确认是否创建它。 请勿静默创建新子节。

## 条目格式

```
    + [{Page title}](/help/blueprints/{topic-folder}/{filename}.md)
```

规则：

- **缩进：**&#x200B;正好四个空格，然后`+ `。 目录解析器取决于此；制表符或不同的间距将中断导航。
- **链接文本：**&#x200B;页面标题，与`title`前件完全匹配。 仅当同一子部分中的现有同级使用`[!DNL ...]`时，才使用它 — 与本地惯例匹配。
- **链接目标：**&#x200B;以`/help/blueprints/`开头的绝对路径。 始终包含`.md`扩展。
- **位置：**&#x200B;将附加到匹配子部分的最后一个条目，除非用户指定了其他位置。 保留所有同级条目的现有顺序。

## 嵌套子部分

`+ Architecture overviews{#architecture-overviews}`没有嵌套分组 — `architecture-diagrams/architecture-overviews/`下的所有页面（包括SDK部署页面，如`websdk.md`、`appsdk.md`）都位于相同的四空格缩进级别。 其他子节（`Audience & Profile Activation`、`B2B activation & marketing`等） 仍可能包含嵌套分组 — 在放置条目之前检查部分。 如果存在嵌套分组并且新页面属于该分组，请缩进两个额外的空格；否则，将该条目置于子部分的顶级。

## 已用示例

### 示例1 — 顶级AEP页面

- 主题文件夹： `architecture-diagrams/architecture-overviews/`
- 文件名： `mix-modeler-integration.md`
- 页面标题： `Adobe Mix Modeler integration with Experience Platform`

条目：

```
    + [Adobe Mix Modeler integration with Experience Platform](/help/blueprints/architecture-diagrams/architecture-overviews/mix-modeler-integration.md)
```

放置在`+ Architecture overviews{#architecture-overviews}`下。

### 示例2 — AJO历程架构

- 主题文件夹： `architecture-diagrams/customer-journeys/`
- 文件名： `cross-channel-journey-architecture.md`
- 页面标题： `Cross-channel journey architecture`

条目：

```
    + [Cross-channel journey architecture](/help/blueprints/architecture-diagrams/customer-journeys/cross-channel-journey-architecture.md)
```

放置在`+ Customer journeys{#customer-journeys}`下。

### 示例3 — SDK部署页面

- 主题文件夹： `architecture-diagrams/architecture-overviews/`
- 文件名： `mobile-sdk-architecture.md`
- 页面标题： `Mobile SDK deployment architecture`

登入（与其他“架构”概览页面相同的四空格缩进）：

```
    + [Mobile SDK deployment architecture](/help/blueprints/architecture-diagrams/architecture-overviews/mobile-sdk-architecture.md)
```

放置在`+ Architecture overviews{#architecture-overviews}`下。

## 验证

编辑TOC.md后，重新读取受影响的子部分并确认：

1. 新条目只使用四个缩进空间（如果嵌套在特定子部分的分组，例如`Audience & Profile Activation`的RTCDP分组，则使用六个）。
2. 链接目标与磁盘上的文件路径匹配 — 包括`.md`扩展名。
3. 该条目被分组到正确的子部分中 — 不浮动在子部分之间。
4. 没有对现有条目进行重新排序或修改。
