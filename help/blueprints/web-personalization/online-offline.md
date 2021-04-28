---
title: 联机/脱机Web个性化蓝图
description: 将 Web 个性化与电子邮件和其他已知和匿名渠道的个性化同步。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
translation-type: tm+mt
source-git-commit: 9a52c5f9513e39b31956aaa0f30cad1426b63a95
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 在线/离线Web/移动个性化蓝图

将 Web 个性化与电子邮件和其他已知和匿名渠道的个性化同步。

## 用例

* 登陆页优化
* 行为和线下用户档案定位
* 除线下洞察（如交易、预订、CRM 和忠诚度数据）和模型洞察以外，还基于以前的产品/内容视图、产品/内容关联、环境属性、第三方受众数据和人口统计的个性化

## 应用程序

* [!UICONTROL 实时客户数据平台]
* Adobe Target
* Adobe Audience Manager（可选）：添加了第三方受众数据，基于合作社的设备图，在 Adobe Analytics 中显示 Platform 区段功能以及在 Platform 中显示 Adobe Analytics 区段的功能
* Adobe Analytics（可选）：添加了根据历史行为数据和来自 Adobe Analytics 数据的精细分段来构建区段的功能

## 架构

<img src="assets/onoff.svg" alt="在线/离线Web个性化蓝图的参考体系结构" style="border:1px solid #4a4a4a" />

## 护栏

### 细分评估和激活的保证

| 分段类型 | 频率 | 吞吐量 | 延迟（区段评估） | 延迟(区段激活) |
|---|---|---|---|---|
| 边缘分割 | 边缘分割目前处于测试阶段，允许在Experience Platform Edge Network上评估有效的实时分割，以便通过Adobe Target和Adobe Journey Optimizer实时、同一页面决策。 |  | ~100毫秒 | 可立即在Adobe Target中进行个性化，在Edge用户档案中进行用户档案查找，并通过基于Cookie的目标进行激活。 |
| 流传输区段 | 每次将新的流事件或记录引入实时客户用户档案，且区段定义是有效的流区段。 <br>有关流细分 [标准](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans) 的指导，请参阅细分文档 | 每秒最多1500事件。 | ~ p95 &lt;5分钟 | 完成这些细分实现后，它们将在几分钟内共享给Audience Manager和受众共享服务，并可在Adobe Target中实现同一/下一页个性化。 |
| 增量细分 | 自上次增量或批量细分评估以来，每小时一次新数据被引入实时客户用户档案。 |  |  | 在实现这些区段会员资格后，几分钟内即可将它们共享给Audience Manager和受众共享服务，并可在Adobe Target中实现同一/下一页个性化。 |
| 批分段 | 每天根据预定的系统集计划进行一次，或通过API手动启动的点对点。 |  | 每个作业大约1小时，存储容量高达10 TB，每个作业2小时，存储容量为10 TB到100 TB，用户档案存储容量为10 TB。 批区段作业绩效取决于数量用户档案、用户档案大小和要评估的区段数。 | 在实现这些区段会员资格后，几分钟内即可将它们共享给Audience Manager和受众共享服务，并可在Adobe Target中实现同一/下一页个性化。 |

### 跨应用程序受众共享的护栏


| 受众共享集成模式 | 详细信息 | 频率 | 吞吐量 | 延迟（区段评估） | 延迟(区段激活) |
|---|---|---|---|---|---|
| 实时客户数据平台到Audience Manager |  | 取决于分段类型 — 请参阅上面的分段护栏表。 | 取决于分段类型 — 请参阅上面的分段护栏表。 | 取决于分段类型 — 请参阅上面的分段护栏表。 | 在完成细分评估后几分钟内。<br>在实时受众平台和Audience Manager之间进行初始客户配置同步大约需要4小时。<br>在4小时内实现的任何受众会员资格将作为“现有”受众会员资格写入后续批分段作业的Audience Manager。 |
| Adobe Analytics到Audience Manager | 默认情况下，每个Adobe Analytics报表包最多可共享75个受众。 如果使用Audience Manager许可证，则对Adobe Analytics与Adobe Target或Adobe Audience Manager与Adobe Target之间可共享的受众数量没有限制。 |  |  |  |  |
| Adobe Analytics到实时客户数据平台 | 当前不可用。 |  |  |  |  |

## 实施模式

Web/移动个性化蓝图可以通过以下方法实现，如下所述。

1. 使用[!UICONTROL Platform Web SDK]或[!UICONTROL Platform Mobile SDK]和[!UICONTROL Edge Network]。
1. 使用传统的特定于应用程序的SDK（例如，AppMeasurement.js）

### 1.平台Web/移动SDK和Edge Approach

<img src="assets/websdkflow.svg" alt="[!UICONTROL Platform Web SDK]或[!UICONTROL Platform Mobile SDK]和[!UICONTROL Edge Network]方法的参考架构" style="border:1px solid #4a4a4a" />

### 2.特定于应用程序的SDK方法

<img src="assets/appsdkflow.png" alt="特定于应用程序的 SDK 方法的参考架构" style="border:1px solid #4a4a4a" />

## 实施先决条件

| 应用程序/服务 | 所需的库 | 备注 |
|---|---|---|
| Adobe Target | [!UICONTROL 平台Web] SDK*、at.js 0.9.1+或mbox.js 61+ | 首选 at.js，因为 mbox.js 将不再开发。 |
| Adobe Audience Manager（可选） | [!UICONTROL 平台Web SDK]*或dil.js 5.0+ |  |
| Adobe Analytics（可选） | [!UICONTROL 平台Web SDK]*或AppMeasurement.js 1.6.4+ | Adobe Analytics 跟踪必须使用区域数据收集 (RDC)。 |
| Experience Cloud ID 服务 | [!UICONTROL 平台Web SDK]*或VisitorAPI.js 2.0+ | （推荐）使用 Experience Platform Launch 部署 ID 服务，以确保在任何应用程序调用之前已设置 ID。 |
| Experience Platform Mobile SDK（可选） | 适用于 Android™ 和 iOS 的 4.11 或更高版本 |  |
| Experience Platform Web SDK | 1.0，当前 Experience Platform SDK 版本具有[尚未支持 Experience Cloud 应用程序的各种用例](https://github.com/adobe/alloy/projects/5) |  |


## 实施步骤

1. 为您的 Web 或移动应用程序[实施 Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=zh-Hans)
1. [实施 Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=zh-Hans)（可选）
1. [实施 Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=zh-Hans)（可选）
1. [[!UICONTROL 实施 Experience Platform 和实时客户档案]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=zh-Hans)
1. 实施 [Experience Cloud Identity 服务](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=zh-Hans)或者 [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hans)
   >[!NOTE]
   >
   >每个应用程序都必须使用 Experience Cloud ID，并且必须是同一 Experience Cloud 组织的一部分，以允许应用程序之间共享受众。
1. [请求预配 Experience Platform 和 Adobe Target 之间的受众共享（共享的受众）](https://www.adobe.com/go/audiences)

## 相关文档

* [与 Audience Manager 和其他 Experience Cloud 解决方案共享 Experience Platform 区段](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=zh-Hans)
* [Experience Platform 区段概述](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hans)
* [流传输区段](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Experience Platform 区段生成器概述](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html?lang=zh-Hans)
* [Audience Manager 源连接器](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=zh-Hans)
* [Adobe Analytics细分共享(通过Adobe Audience Manager)](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=zh-Hans)
* [Experience Platform Web SDK 文档](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Experience Cloud ID 服务文档](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=zh-Hans)
* [Experience Platform Launch 文档](https://experienceleague.adobe.com/docs/launch/using/home.html?lang=zh-Hans)

## 相关博客帖子

* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
* [[!DNL Integrating Adobe Experience Platform Decisioning Engine with AEM Websites]](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [[!DNL Adobe Experience Platform’s Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL How Adobe Experience Platform Can Help Customers Personalize Their Mobile Messaging in Real-Time with Journey Orchestration Service and a Mobile Messaging Vendor]](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
