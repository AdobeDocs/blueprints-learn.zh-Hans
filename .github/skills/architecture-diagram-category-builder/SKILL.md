---
name: architecture-diagram-category-builder
description: 在Adobe Experience Platform Blueprint存储库的架构图和Blueprint下指导创建全新的顶级类别（子部分）。 如果建议的架构图不适合任何现有类别（架构概述、受众和配置文件激活、B2B激活和营销、客户分析、客户历程），并且需要一个新的架构图，请使用此技能。 处理完整的工作流：确认新类别实际上已得到保证，强制执行文件夹/锚点命名约定，创建文件夹结构和overview.md登陆页面，添加TOC.md子部分，以及更新体系结构图登陆页面卡片网格。 要将页面添加到*existing*类别，请改用architecture-diagram-page-builder。
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 0%
---

# 架构图类别生成器

该技能可指导在`/help/blueprints/TOC.md`中的`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`下创建新的顶级类别。 类别是类似于`customer-insights/`或`b2b-activation-marketing/`的文件夹 — 一组相关的架构图页面，具有自己的`overview.md`登陆页面和自己的TOC子部分。

**这是一项罕见的操作。** 今天有五个类别。 仅当真正的新架构内容域不适合任何现有域时，才应添加第六个元素，这不应作为避免在现有类别下组织页面的快捷方式。

## 开始前需要读取

- `./references/naming-conventions.md` — 文件夹/锚点/标签命名规则及其重要原因。 请仔细阅读，它是命名类别时必须遵循的单一真实来源。
- `./references/category-overview-template.md` — 新类别的`overview.md`所需的确切结构。
- 如果您还没有这样的技能，也跳过`../architecture-diagram-page-builder/SKILL.md` — 一旦该类别存在，将使用该技能添加该类别中的各个页面，而不是使用本技能。

## 阶段1：确认实际需要新类别

执行任何其他操作之前，请向用户列出五个现有类别及其范围：

| 类别 | 文件夹 | 范围 |
| --- | --- | --- |
| 架构概述 | `architecture-overviews/` | 顶级Experience Cloud/Experience Platform架构、护栏、部署SDK |
| 受众和用户档案激活 | `audience-profile-activation/` | 通过Real-Time CDP、Audience Manager构建和激活受众/配置文件 |
| B2B激活和营销 | `b2b-activation-marketing/` | 基于帐户的激活、购买组历程、Marketo/Workfront |
| 客户洞察 | `customer-insights/` | Customer Journey Analytics及其集成 |
| 客户历程 | `customer-journeys/` | Journey Optimizer，决策管理， Campaign v7/v8 |

要求用户确认建议的内容不符合其中任何条件。 如果它非常合适（例如，新的B2B图、新的个性化图），请重定向到该现有类别的`architecture-diagram-page-builder`，而不是创建新类别。 只有在用户确认真正的新类别有保证时，才进入阶段2。

## 阶段2：收集类别信息

使用问题表单收集以下内容（第一轮）：

1. **类别标签** — 完整、人类可读的目录标签（例如“Commerce架构”，而不是缩写）。 现在2-3个建议的短语加上“其他”。
2. **单句描述** — 对于`overview.md`前件和登录页卡而言，此类别涵盖的内容。
3. **主Adobe解决方案** — 用于frontmatter `solution`字段。
4. **初始页面** — 用户是否已有1个以上的页面可放入此类别中，还是只是为以后要遵循的页面搭建基架？

使用`./references/naming-conventions.md`中的概要规则从类别标签派生文件夹名称和锚点（小写，放置`&`，连字符，无缩写）。 向用户显示派生的文件夹/锚点，并在继续操作之前进行确认 — 这是一项以后修复成本高昂的详细信息。

## 阶段3：创建文件夹结构

```
help/blueprints/architecture-diagrams/{new-folder}/
help/blueprints/architecture-diagrams/{new-folder}/assets/
help/blueprints/architecture-diagrams/{new-folder}/overview.md
```

使用`./references/category-overview-template.md`生成`overview.md`。 如果用户已准备好初始页面，请立即将其列在表中（使用`architecture-diagram-page-builder`自己生成这些页面文件 — 该技能仅创建类别基架及其概述页面，而不创建单个图页面）。 如果尚未存在页面，则表可能为空或省略，直到添加了第一页 — 请将此情况告知用户而非创建占位符行。

`assets/`文件夹在创建时可能为空；由于该文件夹存在，因此添加到该类别的第一个关系图页面可以放置其图像。

## 阶段4：添加TOC.md子部分

将新类别作为`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`下的顶级条目插入，该条目位于最后一个现有类别之后，除非用户另外指定：

```
  + {Category Label}{#{folder-slug}}
    + [Overview](/help/blueprints/architecture-diagrams/{new-folder}/overview.md)
    + [{Page title}](/help/blueprints/architecture-diagrams/{new-folder}/{filename}.md)
```

规则：

- 2空格缩进作为类别标题，与其他五个标题匹配。
- 锚点`{#{folder-slug}}`必须完全等于文件夹名称（请参阅naming-conventions.md）。
- `+ [Overview]`始终是任何内容页面之前的第一个条目，具有4个空格缩进。
- 保留所有其他TOC.md条目的现有顺序和内容 — 仅插入、从不重新排序或重写不相关的部分。

## 阶段5：更新体系结构图和Blueprint登录页

在`<table style="table-layout:fixed; width:100%;">`网格中，向`help/blueprints/architecture-diagrams/overview.md`添加一张新信息卡，该网格与其他五张信息卡相同。 新卡：

- 链接到`{new-folder}/overview.md`。
- 使用`{new-folder}/assets/`中的代表性图表缩略图（如果尚不存在图表，则使用中性占位符注释 — 将此标记给用户而不是发明图像路径）。
- 使用与现有卡片（`width:100%; height:160px; object-fit:contain; background-color:#ffffff; border:1px solid #d3d3d3; padding:10px; box-sizing:border-box;`在图像上，`min-height:100px;`在文本div上）完全相同的内联样式块。

**重新计算网格布局。** 现有的五张卡片会填充一个3列的网格（两行，一个尾随空单元格）。 添加第六张卡片会完全填充该空单元格 — 无需更改布局。 如果这是第7、8等类别，请用新信息卡添加新`<tr>`，并用空白`<td style="width:33%; ...;"></td>`元素填充该行中剩余的任何空单元格，以便该行不会呈现Ragged。

## 第6阶段：验证

确认并向用户报告：

1. **命名一致性** — 文件夹名称、目录锚点和类别标签概要相同（根据naming-conventions.md）。
2. **overview.md结构** — 与`category-overview-template.md`匹配（引入+两列`Diagram | Description`表，表中没有嵌入的图像或嵌套列表）。
3. **TOC.md位置** — “架构图和Blueprint”下的新子部分，`+ [Overview]`是第一个，缩进正确，没有其他条目被更改。
4. **登陆页信息卡** — 添加到正确的网格位置，使用标准信息卡样式，链接到新`overview.md`。
5. **重定向** — 如果此类别合并或重命名以前存在于其他位置的内容（很少用于全新的类别，但请检查），请按照以前体系结构图重命名时使用的现有`source,dest`格式将条目添加到`redirects.csv`。

先修复所有验证问题，然后再考虑任务完成。

## 注释

- 如果用户以后重命名类别（标签、文件夹或锚点），则它属于重命名操作，而不是新类别操作 — 请遵循新名称的naming-conventions.md规则，更新每个内部链接（TOC.md、两个概览页面、同级相对链接、技能文档）并添加重定向条目。 与先前在此存储库中处理类别重命名的方式相同：先处理文件夹`git mv`，然后在存储库范围搜索和替换旧路径表单，决不要进行可能与不相关的外部URL冲突的全局字符串替换盲操作（例如`experienceleague.adobe.com/docs/experience-platform/...`产品文档链接）。
- 保持此技能与`architecture-diagram-page-builder`同步：如果`architecture-diagram-page-builder`的`references/toc-placement.md`中的子部分映射表尚未列出新类别，则也将其添加。
