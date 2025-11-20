---
title: Real-time Customer Data Platform 和 Adobe Target
description: 将 RTCDP 轮廓和受众与 Adobe Target 集成。
landing-page-description: 将 RTCDP 轮廓和受众与 Adobe Target 集成。
short-description: 将 RTCDP 轮廓和受众与 Adobe Target 集成。
solution: Real-Time Customer Data Platform, Target, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: b634e14af3ea60e0f4cc9e84a0ef896df293a8c7
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 32%

---


# Real-time Customer Data Platform与Adobe Target集成

## 用例

* 使用已知客户数据的线上个性化
* 登陆页优化
* 除线下数据（如交易、预订、CRM 和忠诚度数据）和模型洞察以外，还基于以前的产品/内容视图、产品/内容关联、环境属性和人口统计的个性化
* 使用Adobe Target在网站和移动应用程序上共享和定位在Real-time Customer Data Platform中定义的受众

## 应用程序

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target

### 参考文档

* [用于 Real-time Customer Data Platform 的 Adobe Target 连接](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [Edge 数据流配置](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=zh-Hans)

## 集成模式

| 集成模式 | 功能 | 先决条件 |
|--------------------|------------|---------------|
| **对从Real-time Customer Data Platform共享到Target的Edge进行实时区段评估** |  — 在Edge上实时评估受众以个性化同一页面或下一页面。 <br> — 以流式或批处理方式评估的任何区段也将投影到Edge Network，以包含在边缘区段评估和个性化中。 |  — 必须实施Web/Mobile SDK或Edge Network服务器API。 <br> — 必须在Experience Edge中配置启用了Target和Experience Platform扩展的数据流。 <br> — 必须在Real-time Customer Data Platform目标中配置目标目标。 <br>- 与 Target 集成需要与 Experience Platform 实例具有相同的 IMS 组织。 |
| **通过Edge方法从Real-time Customer Data Platform流式传输和批量共享受众到Target** | - 通过 Edge 网络将来自 Real-time Customer Data Platform 的流传输受众和批次受众共享到 Target。<br> — 实时评估的受众需要Web SDK和Edge Network实施。 |  — 将流和批量RTCDP受众共享到Target不需要Target的Web/Mobile SDK或Edge API实施，但需要启用实时边缘区段评估。 <br>- 如果使用 AT.js，则仅支持针对 ECID 身份命名空间的用户档案集成。<br> — 对于Edge上的自定义身份命名空间查找，需要Web SDK/Edge API部署，并且必须在身份映射中将每个身份设置为身份。 <br> — 必须在Real-time Customer Data Platform目标中配置目标目标，仅支持RTCDP中的默认生产沙盒。 <br>- 与 Target 集成需要与 Experience Platform 实例具有相同的 IMS 组织。 |
| **通过受众共享服务方法从Real-time Customer Data Platform流式传输和批量共享受众到Target和Audience Manager** |  — 当需要从Audience Manager中的第三方数据和受众进行额外扩充时，可以利用此集成模式。 |  — 将流式受众和批量受众共享到Target不需要Web/Mobile SDK，但是要启用实时边缘区段评估则需要Web/Mobile 。 <br>- 如果使用 AT.js，则仅支持针对 ECID 身份命名空间的用户档案集成。<br> — 对于Edge上的自定义身份命名空间查找，需要Web SDK/Edge API部署，并且必须在身份映射中将每个身份设置为身份。 <br> — 必须配置通过受众共享服务的受众投影。 <br> — 与Target集成需要与Experience Platform实例相同的IMS组织。 <br> — 仅默认生产沙盒中的受众支持受众共享核心服务。 |

## 将流传输和批次受众实时共享到 Adobe Target

架构

![在线/离线Web Personalization Blueprint的参考架构](assets/RTCDP+Target.svg)

序列详细信息

![在线/离线Web Personalization Blueprint的参考架构](assets/RTCDP+Target_flow.svg)

概述架构

![在线/离线Web Personalization Blueprint的参考架构](assets/personalization_with_apps.svg)

## 实施模式

通过多种实施方案支持已知客户个性化。

### 带有Web/移动SDK或[!DNL Edge Network] API的实施模式1 - [!DNL Edge Network]（推荐方法）

* 在Web/移动SDK中使用[!DNL Edge Network]。 实时 Edge 分段需要使用 Web/Mobile SDK 或 Edge API 实施方法。
* [有关基于Experience Platform的实施，请参阅SDK Web和移动SDK Blueprint](../experience-platform/deployment/websdk.md)。
* 要在Mobile SDK中使用，必须安装[Adobe Journey Optimizer - Decisioning扩展](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/)。
* [有关包含Edge配置文件的基于API的Adobe Target实现，请参阅 [!DNL Edge Network] 服务器API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hans)。

### 实施模式 2 - 特定于应用程序的 SDK

使用传统的特定于应用程序的 SDK（例如，AT.js 和 AppMeasurement.js）。使用此实施方案不支持实时 Edge 区段评估。但是，使用此实施方案支持从 Experience Platform 中心进行流传输和批次受众共享。

[请参阅Adobe Target连接器文档](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection)
[请参阅特定于应用程序的SDK Blueprint](../experience-platform/deployment/appsdk.md)

## 实施注意事项

* 在将[!DNL Edge Network]和Web SDK结合使用上述实现模式1时，可以利用任何主要身份。
* 首次使用先前摄取到RTCDP中的已知客户数据进行登录个性化，要求个性化请求具有与Real-time Customer Data Platform中的已知客户身份图匹配的主要身份。 如果主ID设置为ECID或尚未与已知客户个人资料进行拼合的身份，则在Edge上实现身份拼合以及边缘个性化包含之前摄取的已知客户数据需要几分钟时间。
* Edge用户档案当前具有14天TTL。 因此，如果用户未在边缘登录或处于活动状态14天，则边缘上的配置文件可能会过期，因此边缘必须从中心获取配置文件才能使用历史配置文件视图进行个性化，包括先前摄取的配置文件属性和区段，这将会导致个性化，即后续页面查看与首次登录时发生的配置文件的历史视图。

## 相关文档

### SDK 文档

* [Experience Platform Web SDK 文档](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hans)
* [Experience Platform 标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
* [Experience Cloud ID 服务文档](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=zh-Hans)

### 分段文档

* [Experience Platform 分段概述](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hans)
* [实时分段](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=zh-Hans)
* [流式分段](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans)
* [通过 Adobe Audience Manager 分享 Adobe Analytics 区段](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=zh-Hans)
* [合并策略配置](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=zh-Hans#create-a-merge-policy)

### 教程

* [使用 Real-Time CDP 和 Adobe Target 实现下一次点击的个性化](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=zh-Hans)
