---
source-git-commit: 83e85d946e455cde46001af0a2112637b7fe24cc
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---
# TOC.md放置引用

技能生成新的架构图页面时，必须向`/help/blueprints/TOC.md`添加一个条目，以便该页面可在站点导航中找到。 本文档准确地定义该条目的位置和方式。

## 父分区

所有架构图页面都位于TOC.md中的顶级`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`部分下。 在该部分中，多个子部分按主题对页面进行分组。

## 子区域映射

选取与新页面的主题文件夹匹配的子部分：

| 主题文件夹 | TOC子节标题 |
| --- | --- |
| `experience-platform/` | `+ Architecture overviews{#architecture-overview}` |
| `experience-platform/deployment/` | `+ Deployment{#deployment}` （嵌套在`Architecture overviews`中的子部分） |
| `audience-activation/` | `+ Audience & Profile Activation{#audience-activation}` |
| `b2b/` | `+ B2B activation & marketing{#b2b-activation}` |
| `customer-journey-analytics/` | `+ Customer Journey Analytics{#customer-journey-analytics}` |
| `customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

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

`+ Architecture overviews{#architecture-overview}`包含用于SDK页面的嵌套`+ Deployment{#deployment}`块。 如果新页面位于`experience-platform/deployment/`下，请将条目放置在`Deployment`内，并包含&#x200B;**6个**&#x200B;缩进空格：

```
      + [{Page title}](/help/blueprints/experience-platform/deployment/{filename}.md)
```

其他子节（`Audience & Profile Activation`、`B2B activation & marketing`等） 可能还包含嵌套分组 — 在放置条目之前检查部分。 如果存在嵌套分组并且新页面属于该分组，请缩进两个额外的空格；否则，将该条目置于子部分的顶级。

## 已用示例

### 示例1 — 顶级AEP页面

- 主题文件夹： `experience-platform/`
- 文件名： `mix-modeler-integration.md`
- 页面标题： `Adobe Mix Modeler integration with Experience Platform`

条目：

```
    + [Adobe Mix Modeler integration with Experience Platform](/help/blueprints/experience-platform/mix-modeler-integration.md)
```

放置在`+ Architecture overviews{#architecture-overview}`下。

### 示例2 — AJO历程架构

- 主题文件夹： `customer-journeys/`
- 文件名： `cross-channel-journey-architecture.md`
- 页面标题： `Cross-channel journey architecture`

条目：

```
    + [Cross-channel journey architecture](/help/blueprints/customer-journeys/cross-channel-journey-architecture.md)
```

放置在`+ Customer journeys{#customer-journeys}`下。

### 示例3 — 部署SDK页面

- 主题文件夹： `experience-platform/deployment/`
- 文件名： `mobile-sdk-architecture.md`
- 页面标题： `Mobile SDK deployment architecture`

输入（请注意六空格缩进）：

```
      + [Mobile SDK deployment architecture](/help/blueprints/experience-platform/deployment/mobile-sdk-architecture.md)
```

放置在`+ Architecture overviews{#architecture-overview}`内的`+ Deployment{#deployment}`下。

## 验证

编辑TOC.md后，重新读取受影响的子部分并确认：

1. 新条目只使用四个缩进空格（如果嵌套在`Deployment`下，则使用六个缩进空格）。
2. 链接目标与磁盘上的文件路径匹配 — 包括`.md`扩展名。
3. 该条目被分组到正确的子部分中 — 不浮动在子部分之间。
4. 没有对现有条目进行重新排序或修改。
