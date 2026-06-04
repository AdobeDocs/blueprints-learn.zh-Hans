---
name: architecture-diagram-page-builder
description: 指导为Adobe Experience Platform Blueprint存储库创建新的架构图页面。 在添加新的顶级体系结构图、集成体系结构页面或应用程序体系结构概述时，请使用此技能。 架构页面涵盖顶级AEP和应用程序架构以及主要集成点 — 而不是深入用例（用例模式生成器中的用例）。 处理整个工作流：收集页面信息，生成Markdown文件，将其放在正确的主题文件夹中，以及更新TOC.md。
source-git-commit: 4d236750286c28a8b8eb53a5bdec0645cc0e3e91
workflow-type: tm+mt
source-wordcount: '1556'
ht-degree: 1%

---


# 架构图页面生成器

此技能可指导您为Adobe Experience Platform Blueprint存储库创建新的架构图页面。 架构图页面提供了AEP和Adobe应用程序如何组合、它们之间的主要数据流以及作者在设计解决方案时需要注意的集成点的顶级可视化参考。

## 范围

架构图页面是&#x200B;**焦点、引用样式页面**，通常为40-100行Markdown，其中包含：

- 一个或多个体系结构图，其中简要说明了每个图的用途
- 链接到架构支持的用例模式（架构页面不复制该内容）
- 简要列出了主要数据流和集成点，并说明了它们
- Experience League链接，以便进一步了解应用程序域

它们&#x200B;**不是**&#x200B;用于深入用例内容的位置。 KPI、业务目标、战术用例示例、功能和角色叙述属于用例模式页面 — 通过`use-case-pattern-builder`技能生成。 有关完整护栏，请参阅`references/scope-guardrails.md`。

## 开始前需要读取

请阅读以下模板和规则的参考文件：

- `references/diagram-template.md` — 带占位符值的完整Markdown模板
- `references/toc-placement.md` — TOC.md的子部分映射表和条目格式
- `references/scope-guardrails.md` — 属于体系结构页面与用例模式页面上的内容的规则

## 第1阶段：信息收集

**使用表单，而不是线性面试。** 通过以逻辑批处理轮次呈现`AskUserQuestion`表单来收集所有必需的信息，而不是一次询问一个问题。 这使用户体验保持快速和可快速浏览。

### AskUserQuestion约束

- 每个`AskUserQuestion`调用最多&#x200B;**4个问题**。
- 每个问题最多&#x200B;**4个选项**。
- 如果一个问题有4个以上合理的选项，请将其拆分为两个调用（例如，询问前4个选项，然后在第5个选项中输入“是”/“否”）。
- 对于应用多个答案的问题（解决方案、模式、数据流），请使用`multiSelect: true`。

### 第1轮 — 核心页面信息（一个AskUserQuestion调用，最多4个问题）

请以单个表单请求以下所有内容：

1. **页面标题** — 显示2-3个建议变体，这些变体派生自用户已告诉您的内容，另外还有“其他”转义剖面线。
2. **主题文件夹** — 将5个有效的文件夹作为选项显示；根据用户的输入推荐最有可能的文件夹。
3. **Adobe解决方案** — 多选；根据页面主题建议最可能的候选人。
4. **图表计数** — 页面将包含多少图表(1 / 2 / 3 / 4+)。

### 第2轮 — 图表详细信息（一个AskUserQuestion调用，最多4个问题）

以一个形式询问每个图表的图像文件名和页面用途：

- 对于每个图表（单个表单轮中最多为2个），请将&#x200B;**图像文件名**&#x200B;作为问题来询问，其中包含2-3个建议文件名（派生自页面标题）以及“其他”选项。
- 以2-3建议短语加上“其他”的问题形式询问&#x200B;**页面目的**（1-2句描述）。
- 询问是否需要&#x200B;**`>[!MORELIKETHIS]`标注**（是/否）。 如果为“是”，则收集URL并在跟进消息中链接文本。

> **节标题和替换文本：**&#x200B;当图像文件名是描述性的（例如，`fac-architecture.svg`、`fac-dataflow.svg`）时，从其中推断H2节标题和替换文本 — 无需询问用户。 使用带标题且人性化的文件名干作为节标题（例如，`Architecture diagram`、`Data flow diagram`）。 仅询问文件名是否模棱两可。

### 第3轮 — 用例模式（扫描后的AskUserQuestion）

在展示此表单之前，**glob`/help/blueprints/use-case-patterns/`**&#x200B;并根据页面标题、目的和解决方案识别3-5个可能的匹配模式。 在建议每个文件之前，先确认每个文件是否存在。

将前4名候选人作为`multiSelect`问题提出。 如果存在强有力的第五个候选人，则对该候选人另外提出一个“是”或“否”的问题。 还可以邀请用户命名您错过的任何模式。

仅包括已确认存在其文件的模式。 别让图案名称产生幻觉。

### 第4轮 — 数据流和Experience League链接（一次AskUserQuestion调用）

**数据流：**&#x200B;建议3-5个预写的数据流项目符号作为`multiSelect`问题（派生自页面主题）。 用户选择适用的项。 将每个选项保留为一个简明的句子。 如果用户需要不在您的列表中的自定义流，他们可以在后续中提供这些流。

**Experience League链接：**&#x200B;在表单之后，显示一个Markdown表，其中包含4-6个建议的链接，以及文章标题、URL和一行原理。 将每个URL标记为&#x200B;**未验证**。 要求用户(a)接受，(b)替换为验证的URL，或(c)添加他们自己的URL。 如果列表很长，请使用包含4个选项的跟进`AskUserQuestion`；否则，接受纯文本确认。

从不创建您尚未获取的URL。 如果不确定，则建议文章标题，并允许用户提供URL。

### 当所有倒圆角都完成时

在生成任何文件之前，确认用户设置的完整信息。 如果仍然缺少任何必需项目或将其标记为“其他”但没有值，请在继续操作之前询问该项目。 请勿制作图、图案或链接。

## 阶段2：范围检查

在生成之前，请重新阅读用户的图表描述、数据流项目符号和任何草稿散文。 应用`references/scope-guardrails.md`中的护栏。

如果计划的内容中出现以下任一内容，请警告用户和选件将该部分重定向到用例模式页面（或从架构页面中修剪它）：

- KPI或度量公式
- 业务目标或业务影响说明
- 战术用例示例（特定的个性化场景、活动示例等）
- 功能（`A > B > C > D`样式）
- 角色驱动的storytelling

如果计划内容停留在体系结构页面范围内（顶层体系结构、系统数据流、集成点、部署拓扑、边缘与中心），请与用户确认并进入阶段3。

## 阶段3：内容生成

在以下位置生成页面：

```
/help/blueprints/{topic-folder}/{kebab-filename}.md
```

使用`references/diagram-template.md`作为源模板。 使用收集的信息填写所有占位符值。 生成的文件必须包括：

1. **YAML frontmatter** — 仅`title`，`description`，`solution`。
   - **不包括`exl-id`** — 发布管道自动分配它。
   - **不包括** `product_v2`、`feature_v2`、`role_v2`、`topic_v2`、`TQID`、`kt`或`thumbnail` — 这些也是自动填充的。

2. **H1标题** — 页面标题。

3. **打开段落** — 从页面目的输入派生出1-2个句子。

4. **可选`>[!MORELIKETHIS]`块** — 仅当用户提供了相关内容链接时。

5. **每个关系图一个H2节** — 按用户提供的顺序。 每个部分包含：
   - 将章节标题用作H2标题
   - 1-2个句子解释图表的用途
   - 使用标准约定嵌入的图像：

     ```html
     <img src="assets/{filename}" alt="{Alt Text}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />
     ```

6. **`## Use case patterns supported`** — 项目符号列表。 每个项目符号：

   ```
   - [{Pattern name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) -- {1-line note on why this architecture enables the pattern}
   ```

7. **`## Primary data flows and integration points`** — 3-7个流/集成项目的项目符号列表。

8. **`## Further reading`** — Experience League链接的项目符号列表：

   ```
   - [{Article title}]({Experience League URL})
   ```

在正文和项目符号中为Adobe产品名称使用`[!DNL ...]`语法，与现有页面的约定相匹配。

## 第4阶段：交叉引用更新

更新&#x200B;**`/help/blueprints/TOC.md`**&#x200B;以将新页面添加到导航。 这是唯一要更新的交叉引用页面。

读取完整子部分映射表和规则的`references/toc-placement.md`。 摘要：

| 主题文件夹 | TOC子部分 |
| --- | --- |
| `experience-platform/` | `+ Architecture overviews{#architecture-overview}` |
| `experience-platform/deployment/` | `+ Deployment{#deployment}` （架构概述的子部分） |
| `audience-activation/` | `+ Audience & Profile Activation{#audience-activation}` |
| `b2b/` | `+ B2B activation & marketing{#b2b-activation}` |
| `customer-journey-analytics/` | `+ Customer Journey Analytics{#customer-journey-analytics}` |
| `customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

条目格式（4空格缩进+ `+`）：

```
    + [{Page title}](/help/blueprints/{topic-folder}/{filename}.md)
```

除非用户指定不同的位置，否则将新条目附加为匹配子部分中的最后一项。 保留精确的4空间缩进 — TOC解析取决于它。

**在放置之前检查嵌套的子组。** 某些子部分（尤其是`Audience & Profile Activation`）包含嵌套分组（例如，`Real-Time Customer Data Platform (RTCDP) {#known-customer-audience-activation}`）。 在编辑之前，请阅读TOC.md中受影响的子部分。 新的顶级架构页面属于子节的4空格缩进级别 — **而非**&#x200B;位于嵌套子组（使用6空格缩进）内。 将新条目放在最后一个嵌套的子组条目的后面，并放在下一个顶级子节标题之前。

## 阶段5：验证

创建和更新所有文件后，验证以下内容并向用户报告任何故障：

1. **存在图像资源** — 对于每个图，检查`/help/blueprints/{topic-folder}/assets/{filename}`是否存在。 如果缺少&#x200B;**警告**；请勿阻止（用户可能正在与图设计并行创作）。 显示缺少文件的清晰列表，以便用户知道要添加的内容。

2. **用例模式链接** — 文件中的每个模式链接都指向`/help/blueprints/use-case-patterns/`下的现有Markdown文件。 使用`Read`或glob确认每个目标都存在。

3. **Experience League链接** — 抽查`## Further reading`部分中的每个URL是否都以`https://experienceleague.adobe.com/zh-hans`开头。

4. **目录条目位置** — 新条目位于正确的子部分内，使用4空格缩进，并且路径与生成的文件位置完全匹配。

5. **文件命名** — 页面文件名大小写为kebab，与TOC.md中引用的路径匹配。

6. **Frontmatter完整性** — 该页面包括`title`、`description`和`solution`。 它必须&#x200B;**不**&#x200B;包括`exl-id`、`product_v2`、`feature_v2`、`role_v2`、`topic_v2`、`TQID`、`kt`或`thumbnail`。

先修复所有验证问题，然后再考虑任务完成。

## 注释

- 在正文和项目符号中始终使用Adobe产品名称的`[!DNL ...]`语法，遵循现有页面的惯例。
- 体系结构图通常是SVG（对于清晰度和缩放是首选），但PNG对于点阵源图稿是可接受的。
- 需要`<img>`嵌入的内联样式字符串(`border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;`)和`class="modal-image"` — 它们启用Experience League模式缩放交互。
- 如果用户正在为尚不存在的全新主题文件夹创建页面，请警告TOC.md在`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`下需要新的顶级子部分。 将该步骤作为单独的步骤处理，需要用户明确批准。
- 如果架构图详细记录了&#x200B;*单个用例的端到端*（包括KPI、业务目标、功能），则将用户重定向到`use-case-pattern-builder` — 这不是架构页面。
