---
title: 联机/脱机Web个性化方案
description: 将Web个性化与电子邮件和其他已知的匿名渠道个性化同步。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
translation-type: tm+mt
source-git-commit: 9b6c220a515c5abae22b58fe33558d7d2fed375d
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 0%

---



# 联机/脱机Web个性化方案

将Web个性化与电子邮件和其他已知的匿名渠道个性化同步。

## 用例

* 登陆页优化
* 行为和线下用户档案定位
* 除了离线洞察（如交易、忠诚度和CRM数据）以及建模的洞察之外，还基于以前的产品/内容视图、产品/内容关联、环境属性、第三方受众数据和人口统计信息进行个性化

## 应用程序

* 实时客户数据平台
* Adobe Target
* Adobe Audience Manager（可选）：添加第三方受众数据、基于协作的设备图形、在Adobe Analytics中显示平台区段的功能以及在Platform中显示Adobe Analytics区段的功能
* Adobe Analytics（可选）：添加了根据历史行为数据构建细分和从Adobe Analytics数据细粒度细分的能力

## 架构

<img src="assets/onoff.svg" alt="联机/脱机Web个性化方案的参考架构" style="border:1px solid #4a4a4a" />

## 瓜德雷尔

* 从Experience Platform到Audience Manager共享的细分在细分实现后的几分钟内即可共享 — 无论是通过流评估还是批评估方法。 AEP与AAM之间初始区段配置同步约4小时，AEP区段成员关系才能在AAM用户档案中开始实现。 进入AAM用户档案后，AEP区段成员资格即可通过Adobe Target实现相同的页面个性化。
* 请注意，对于在AEP和AAM之间4小时区段配置同步内发生的区段实现，这些区段实现将作为“现有”区段在后续批区段作业上实现到AAM中。
* 从AEP中进行批量区段共享 — 每天一次或通过API手动启动。 一旦实现这些区段会员资格，它们将在几分钟内共享到AAM，并可在目标中实现同一/下一页个性化。
* 流分段在~p95 5min内实现。 进行这些细分实现后，它们将在几分钟内共享到AAM，并可在目标中实现同一/下一页个性化。
* 默认情况下，区段共享服务允许每个Adobe Analytics报表包最多共享75个受众。 如果客户拥有Audience Manager许可证，则对Adobe Analytics与Adobe Target或Audience Manager与Adobe Target之间可共享的受众数量不设限制。

## 实施先决条件

| 应用程序/服务 | 所需的库 | 附注 |
|---|---|---|
| Adobe Target | 平台Web SDK*、at.js 0.9.1+或mbox.js 61+ | 首选at.js，因为mbox.js不再在开发中。 |
| Adobe Audience Manager（可选） | 平台Web SDK*或dil.js 5.0+ |  |
| Adobe Analytics（可选） | 平台Web SDK*或AppMeasurement.js 1.6.4+ | Adobe Analytics跟踪必须使用区域数据收集(RDC)。 |
| Experience CloudID服务 | 平台Web SDK*或VisitorAPI.js 2.0+ | （建议）使用Experience Platform Launch部署ID服务，以确保在调用任何应用程序之前设置ID |
| Experience Platform Mobile SDK（可选） | 适用于iOS和Android™的4.11或更高版本 |  |
| Experience Platform Web SDK | 1.0，当前Experience Platform SDK版本具有[尚未支持Experience Cloud应用程序](https://github.com/adobe/alloy/projects/5)的各种用例 |  |


## 实施步骤

1. [为您的Web或](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) 移动应用程序实施Adobe目标
1. [实施Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html) （可选）
1. [实施Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html)  （可选）
1. [实施Experience Platform和实时客户用户档案](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html)
1. 实施[Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html)或[Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
   >[!NOTE]
   >
   >每个应用程序都必须使用Experience CloudID，并且必须是同一Experience Cloud组织的一部分，以允许应用程序之间共享受众。
1. [请求设置以在Experience Platform和Adobe Target之间共享受众(共享受众)](https://www.adobe.com/go/audiences)

## 实现数据流图

Web/Mobile个性化蓝图可以使用传统的特定于应用程序的SDK（例如，AppMeasurement.js）或使用Platform Web SDK/Mobile SDK和Edge Network来实现。

### 平台Web/移动SDK和Edge Approach

<img src="assets/websdkflow.svg" alt="平台Web SDK/Mobile SDK和Edge Network Approach的参考架构" style="border:1px solid #4a4a4a" />

### 应用程序特定的SDK方法

<img src="assets/appsdkflow.png" alt="特定于应用程序的SDK方法的参考架构" style="border:1px solid #4a4a4a" />

## 相关文档

* [Experience Platform细分共享与Audience Manager和其他Experience Cloud解决方案](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html)
* [Experience Platform细分概述](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html)
* [流细分](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Experience Platform区段生成器概述](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html)
* [Audience Manager源连接器](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html)
* [Adobe Analytics通过AAM进行细分共享](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* [Experience Platform Web SDK文档](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Experience CloudID服务文档](https://experienceleague.adobe.com/docs/id-service/using/home.html)
* [Experience Platform Launch文档](https://experienceleague.adobe.com/docs/launch/using/home.html)

## 相关博客帖子

* [使用Adobe Experience Platform实时客户用户档案的Web个性化蓝图](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [构建最佳在线体验：利用查询服务丰富统一用户档案](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
* [将Adobe Experience Platform决策引擎与AEM网站集成](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [Adobe Experience Platform的Identity Service — 如何解决客户身份难题](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [Adobe Experience Platform预测受众如何改善个性化体验](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [Adobe Experience Platform Web SDK for 受众 Management](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [通过“客户零”用户档案实施Adobe Experience Platform实时客户项目](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [Adobe Experience Platform如何通过Journey Orchestration服务和移动消息供应商帮助客户实时个性化其移动消息](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [分段（秒）：Adobe Experience Platform如何让实时客户用户档案成为现实](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
* [构建最佳在线体验：利用查询服务丰富统一用户档案](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)


