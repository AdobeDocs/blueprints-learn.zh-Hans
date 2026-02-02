---
title: 适用于Web和移动Personalization的实时Edge配置文件访问
description: 在边缘位置[!UICONTROL 实时客户个人资料]访问，以提供实时Web和移动个性化的上下文。
solution: Real-Time Customer Data Platform, Data Collection
kt: 719
source-git-commit: 2fad3a8a9210d703130f251b0bd7cc4c0b7cbd32
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 6%

---

# 适用于Web和移动Personalization的实时Edge配置文件访问

适用于Web和移动Personalization蓝图的实时Edge配置文件访问显示了Web和移动应用程序如何访问Adobe Experience Platform边缘的[!UICONTROL 实时客户配置文件]，以实现高吞吐量、低延迟的个性化。

应用程序可在边缘以毫秒延迟访问实时配置文件属性和受众。 作为属性存储在配置文件中的属性、受众成员资格和模型驱动功能可以跨Web和移动渠道实时访问以进行同一页面和下一页面个性化。

利用此功能，您可以根据实时客户档案在网站和移动应用程序上提供高度个性化的体验，包括从实时行为派生的受众、引入实时客户档案的属性以及计算的见解。

>[!NOTE]
>
>Edge配置文件访问专为高吞吐量、低延迟用例而设计，例如Web/移动入站个性化和实时Offer Decisioning。 对于吞吐量较低的情况（如代理辅助支持或销售交互），中心配置文件查找API更合适。 查看支持和销售方案的[实时配置文件访问Blueprint](customer-activity.md)，了解基于中心的配置文件访问。

## 应用程序

* Real-time Customer Data Platform  
* Adobe Experience Platform数据收集(Web SDK/移动SDK)
* Edge Network服务器API

## 用例

* 在Web和移动渠道上实时个性化已知客户体验
* 基于实时配置文件属性和受众的同页和下一页个性化
* 基于客户个人资料的内容和选件个性化，包括实时行为数据、属性和计算的见解
* 与个性化引擎、内容管理系统和外部应用程序集成，用于实时决策
* 使用实时用户档案上下文进行测试和内容优化

## 先决条件

如果您希望使用流数据实时更新用户档案，此Blueprint需要使用以下数据收集方法之一。 无需直接向Edge配置文件收集数据，即可实时访问Edge配置文件；可将数据收集到中心并投影到Edge配置文件。 请注意，收集到中心并随后预计到Edge的数据会增加延迟。

* 如果要从您的网站收集数据，请使用[Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)。
* 如果要从移动应用程序收集数据，请使用[Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/)。
* 如果您未使用Web SDK或Mobile SDK，或者正在实现更直接的服务器到服务器连接，请使用[Edge Network服务器API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hans)。

>[!IMPORTANT]
>
>在实施边缘个性化之前，请阅读有关如何[将受众数据激活到边缘个性化目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)的指南。 本指南将指导您跨多个Experience Platform组件完成相同页面和下一页面个性化用例所需的配置步骤。

## 架构图

<img src="assets/real-time-edge-lookup.svg" alt="适用于Web和移动Personalization的Edge配置文件访问参考架构" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## 护栏

* [[!UICONTROL 实时客户档案]数据的护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* [Edge Network护栏](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* Edge用户档案具有14天的生存时间(TTL)。 如果用户在Edge上未活动14天，Edge配置文件可能会过期，需要从中心提取，这可能会影响第一页个性化。
* Edge个性化支持对符合Edge分段标准的受众进行实时受众成员资格评估。 此外，通过相应的配置，还可在边缘位置获得来自中心的批量访问和流式访问受众。

## 实施模式

可以使用Real-time Customer Data Platform中的[自定义Personalization连接](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization)目标实现Edge个性化。 此目标支持多种数据收集方法，具体取决于您的用例。

### 模式1：使用Web SDK/Mobile SDK实现基于受众会员资格的个性化

* 将Adobe Experience Platform Web SDK或Mobile SDK与Edge Network结合使用，以实现基于受众成员资格的个性化。
* 这种方法可为基于受众成员资格的边缘个性化提供低延迟和最佳性能。
* 实时边缘分段需要Web/移动SDK实施。
* 仅Web SDK和Mobile SDK **支持基于受众成员资格的个性化**。
* [有关基于Experience Platform的实施，请参阅SDK Web和Mobile SDK Blueprint](../experience-platform/deployment/websdk.md)。
* 对于移动SDK实施，必须在Mobile SDK中安装[Adobe Journey Optimizer - Decisioning扩展](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/)。

### 模式2：使用Edge Network服务器API进行基于属性的个性化（配置文件属性必需）

>[!IMPORTANT]
>
>**基于属性的个性化要求：**&#x200B;如果您要基于配置文件属性（而不仅仅是受众成员资格）进行个性化，则&#x200B;**必须**&#x200B;使用具有经过身份验证的服务器端集成的[Edge Network服务器API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hans)，无论您同时使用Web SDK还是Mobile SDK进行数据收集。

* 支持与第三方个性化引擎和基于CDN的个性化集成。
* 需要&#x200B;**Edge Network服务器API**&#x200B;才能安全检索用于个性化的配置文件属性。
* 您可以添加利用已用于Web或Mobile SDK实施的相同数据流的服务器端集成，以通过Edge Network服务器API检索配置文件属性。
* 对配置文件属性的所有Edge Network服务器API调用都必须在经过身份验证的上下文中进行，以保护敏感数据。
* 此模式同时支持基于受众成员资格的个性化和基于属性的个性化。
* 适用于服务器端个性化用例、基于API的集成和需要配置文件属性访问权限的情景。

## 实施步骤

1. 为要摄入的数据[创建架构。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&lang=zh-Hans)
1. 为要摄入的数据[创建数据集。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)
1. [在架构上配置正确的身份和身份命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)，以确保摄取的数据可以拼合到统一配置文件中。
1. [为用户档案启用架构和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。
1. [将数据摄入](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&lang=zh-Hans) Experience Platform。
1. [设置合并策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hans)以确保正确的身份拼接和配置文件合并。
1. [在Experience Platform数据收集中配置数据流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html#)，并启用目标配置。 数据流确定在对页面的响应中将包含受众的数据收集数据流。
1. 在Web和移动属性上实施[Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)或[移动SDK](https://developer.adobe.com/client-sdks/home/)以进行数据收集。
1. 为需要实时评估的受众配置边缘分段。 [Edge分段文档](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=zh-Hans)。
1. 在目标目录中，设置[自定义Personalization连接](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization)目标：
1. [将受众激活到边缘个性化目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)。 选择要激活到目标的受众。
1. （基于属性的个性化是可选的）如果除了受众成员资格之外，您还需要根据配置文件属性进行个性化，请使用相同的数据流通过经过身份验证的服务器端集成实施[Edge Network服务器API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hans)。 这是&#x200B;**访问配置文件属性所必需的**。
1. 在Web/移动应用程序中实施个性化逻辑以使用导出的受众数据和配置文件属性：
   * 如果使用Adobe Experience Platform中的标记，请使用[发送事件完成功能](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=zh-Hans)来访问具有导出数据的`event.destinations`变量。
   * 如果不使用标记，请使用[命令响应](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html)从Adobe Experience Platform中解析JSON响应并检索受众ID和配置文件属性。

## 实施注意事项

### 身份注意事项

* 将Web SDK或Mobile SDK与Edge Network结合使用时，任何主要身份都可用于边缘个性化。
* 对于使用已知客户数据进行首次登录个性化，个性化请求必须使用与Real-time Customer Data Platform中的已知客户身份匹配的主要身份。 如果主ID设置为ECID或尚未与已知客户个人资料进行拼接的匿名身份，则实现身份拼接将需要时间，这可能会影响个性化历史个人资料数据的可用性。
* 必须先初始化Edge配置文件，然后才能将其用于个性化。 边缘配置文件已过期（14天TTL）的首次访客或回访访客可能会根据有限的配置文件数据体验初始个性化，直到边缘配置文件完全填充为止。

### 基于属性的个性化

>[!IMPORTANT]
>
>配置文件属性可能包含敏感数据。 为了保护此数据，在为基于属性的个性化配置自定义Personalization目标时，您&#x200B;**必须**&#x200B;使用[Edge Network服务器API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hans)。 所有Edge Network服务器API调用都必须在经过身份验证的上下文中进行。

* 对于使用配置文件属性的基于属性的个性化，您必须添加与Edge Network服务器API的服务器端集成，该集成利用您用于Web或Mobile SDK实施的相同数据流。
* 您必须通过自定义Personalization连接目标配置来配置要包含在边缘投影中的配置文件属性。
* **仅Web SDK和Mobile SDK支持基于受众成员资格进行个性化**。 需要&#x200B;**Edge Network服务器API**&#x200B;才能安全检索用于个性化的配置文件属性。
* 如果您没有实施Edge Network服务器API以进行属性访问，则个性化将仅基于受众成员资格。
* 除了受众区段之外，具有属性的自定义Personalization的API响应还包含`attributes`部分。

### 受众注意事项

* 通过中心上的流式或批量分段评估的受众将投影到边缘，并且可用于进行个性化。
* 对于同一页面个性化，将在边缘实时评估符合边缘分段标准的受众。
* 根据受众在实时个性化用例中的使用情况，为边缘评估配置相应的受众。

## 相关文档

### 目标配置

* [自定义Personalization连接](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) — 主要实施指南
* [Personalization目标概述](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/overview)
* [将受众激活到边缘个性化目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)
* [实时查找边缘上的配置文件属性](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-profile-lookup)

### SDK 文档

* [Experience Platform Web SDK 文档](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)
* [Experience Platform Mobile SDK 文档](https://developer.adobe.com/client-sdks/home/)
* [Edge Network服务器API文档](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hans)
* [Experience Platform 标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
* Web SDK中的[命令响应](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html)

### 用户档案和分段文档

* [[!UICONTROL 实时客户档案]文档](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [用户档案护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)

### 教程

* [使用 Real-Time CDP 和 Adobe Target 实现下一次点击的个性化](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html)
* [数据流配置](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html#)
