---
source-git-commit: dfa21942ecf2a1db06df6f6cc945f5572811ca93
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 2%

---
# Blueprint文档引用 — 详细指南

## 文档类型

| 类型 | 用途 | 位置/示例 |
|------|---------|--------------------|
| **概述/中心** | 介绍产品或区域；链接到方案Blueprint | 如`overview.md`，`journey-optimizer-overview.md` |
| **方案Blueprint** | 单一用例：架构、步骤、护栏 | 如`real-time-lookup.md`，`journey-optimizer-journeys.md` |
| **目录** | 导航；请勿用作内容模板 | `help/blueprints/TOC.md` |

&#x200B;---

## 完整部分引用

### 标题和描述（前置内容）

- **title**：短，特定。 将`[!DNL Product Name]`用于产品名称（如`[!DNL Journey Optimizer]`）。
- **描述**：一句。 描述Blueprint显示的内容和结果（例如，“在Edge实时访问客户个人资料以进行Web和移动个性化”）。

### 正文部分

| 部分 | 何时包含 | 内容指导 |
|---------|-----------------|-------------------|
| **应用程序** | 始终用于方案Blueprint | 相关的Adobe产品/解决方案的项目符号列表（例如Real-time Customer Data Platform、数据收集）。 |
| **用例** | 始终 | 此Blueprint支持的业务/技术用例项目符号列表。 |
| **先决条件** | 需要设置时 | 必须适当的产品、子域、SDK和配置。 链接到Experience League以了解设置步骤。 |
| **架构图** | 始终 | 单个主图(首选SVG)。 使用一致的样式： `style="width:90%; border:1px solid #4a4a4a" class="modal-image"`。 提供有意义的`alt`文本。 |
| **护栏** | 当产品有护栏时始终如此 | Experience League官方护栏页面的链接。 将Blueprint特定的限制（例如TTL、速率限制）添加为项目符号。 |
| **实施模式** | 存在多种方法时 | 命名每个模式(例如“模式1：基于Web SDK的受众成员资格”)；使用项目符号确定何时使用和取舍。 |
| **实施步骤** | 对于具有定义路径的方案Blueprint | 编号列表。 每个步骤：操作+指向过程所在的Experience League的链接。 请勿复制完整过程。 |
| **实施注意事项** | 当有重要的警告时 | 子部分（例如身份注意事项、基于属性的个性化）。 项目符号或简短段落；链接以获得深度。 |
| **相关文档** | 始终 | 到Experience League的分组链接(也可选择使用developer.adobe.com)。 请参阅下面的“Experience League链接组”。 |

### 概述/中心页面

- 从关于产品/区域和Blueprint涵盖内容的1-2个段落开始。
- **用例**：可以为多个类别使用`>[!BEGINTABS]` / `>[!TAB ...]` / `>[!ENDTABS]`。
- **架构**：一个主图。
- **Blueprint方案**&#x200B;或&#x200B;**集成模式**：包含方案名称、简短描述和方案Blueprint链接的表。
- **先决条件**，**护栏**，**相关文档**：与上述内容相同；请保持简洁。

&#x200B;---

## Adobe Experience League — 代理指导

### 何时引用Experience League

- **产品文档**：产品的工作方式、UI流程、概念。
- **API**：端点、参数、示例(Experience Platform、Edge等)。
- **护栏**：产品或服务的官方护栏页面。
- **教程**：分步指南（例如，创建架构、激活目标）。
- **配置**：数据流、目标、合并策略、身份等。

请勿将来自Experience League的较长过程粘贴到Blueprint中。 总结并链接。

### URL模式

| 内容类型 | 基本URL | 示例路径 |
|--------------|----------|--------------|
| Experience Platform文档 | `https://experienceleague.adobe.com/docs/experience-platform/` | `.../profile/home.html`，`.../destinations/catalog/...` |
| Experience League (en) | `https://experienceleague.adobe.com/en/docs/` | 与`/en/`的上述结构相同。 |
| Journey Optimizer | `https://experienceleague.adobe.com/docs/journey-optimizer/` | `.../using/get-started/guardrails.html` |
| Web SDK | `https://experienceleague.adobe.com/docs/experience-platform/web-sdk/` | `.../home.html`，`.../commands/command-responses.html` |
| Edge Network服务器API | `https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/` | `.../overview.html`，`.../guardrails.html` |
| Mobile SDK | `https://developer.adobe.com/client-sdks/` | `.../home/`，`.../edge/adobe-journey-optimizer-decisioning/` |
| 标记 | `https://experienceleague.adobe.com/docs/experience-platform/tags/` | `.../home.html` |
| Platform教程 | `https://experienceleague.adobe.com/docs/platform-learn/tutorials/` | `.../profiles/create-merge-policies.html` |

使用与当前Experience League站点匹配的规范路径（如果已知英文路径，则首选`/en/docs/`）。

### Markdown中的链接格式

- **描述性链接文本**： `[Create schemas](https://experienceleague.adobe.com/...)`不是“单击此处”。
- **文本中的产品名称**：针对每个Adobe样式使用`[!DNL Product Name]`（例如`[!DNL Real-time Customer Profile]`）。
- **外部链接**：仅在模板或管道需要时才添加`{target="_blank"}`（检查存储库中的现有Blueprint）。

### 相关文档 — 建议的组

在应用时，请使用这些组：

1. **目标配置**（用于激活/边缘个性化Blueprint）
2. **SDK文档**(Web SDK、Mobile SDK、Edge Network服务器API、标记)
3. **个人资料和分段**（实时客户个人资料、合并策略、分段）
4. **教程** （平台学习或特定于产品的分步指南）
5. **产品文档**（主产品文档主页或关键子部分）
6. **护栏** （如果护栏分区中尚不存在）

示例：

```markdown
## Related documentation

### Destination configurations
* [Custom Personalization Connection](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization)
* [Activate audiences to edge personalization destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)

### SDK documentation
* [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)
* [Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html)

### Profile and segmentation
* [Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [Profile Guardrails](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
```

&#x200B;---

## 存储库和目录

- **Blueprint内容路径**： `help/blueprints/`（具有按区域划分的子文件夹，例如`audience-activation/`、`customer-journeys/journey-optimizer/`）。
- **Assets**：与Blueprint共同定位（例如`assets/`、`images/`）或在共享文件夹中（例如`experience-platform/assets/`）。
- **目录**：添加、重命名或移动Blueprint页面时编辑`help/blueprints/TOC.md`。 保留frontmatter (`user-guide-title`， `breadcrumb-title`， `user-guide-description`， `product`， `mini-toc-levels`， `role`)和`+`层次结构。

&#x200B;---

## 此存储库中的示例引用

- **方案Blueprint（长格式）**： `help/blueprints/audience-activation/real-time-lookup.md`
- **带选项卡和表的概述/中心**： `help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md`
- **护栏聚焦**： `help/blueprints/experience-platform/guardrails.md`
- **导航**： `help/blueprints/TOC.md`，`help/blueprints/overview.md`

将它们用作章节顺序、前沿内容、图表放置和Experience League链接使用的模式。
