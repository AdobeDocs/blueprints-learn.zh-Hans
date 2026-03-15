---
user-guide-title: 客户体验编排Blueprint
breadcrumb-title: 蓝图
user-guide-description: Blueprint 是可重复实施的产品，用于应对战略和解决既定的业务问题，并包含架构图、技术注意事项和相关文档链接。
product: adobe experience platform
mini-toc-levels: 3
role: Developer, User
source-git-commit: 1b722db275b3360fc443a67e07c7162909c32d72
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 26%

---


# 客户体验编排Blueprint {#architecture}

+ [客户体验编排Blueprint](/help/blueprints/overview.md)
+ 架构概述{#architecture-overview}
   + [Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
   + [Experience Platform与应用程序](/help/blueprints/experience-platform/platform-applications.md)
   + [Experience Platform数据流](/help/blueprints/experience-platform/platform-data-flow.md)
   + [Experience Platform护栏](/help/blueprints/experience-platform/guardrails.md)
   + 部署{#deployment}
      + [Experience Platform Web SDK &amp; [!DNL Edge Network]](/help/blueprints/experience-platform/deployment/websdk.md)
      + [应用程序 SDK](/help/blueprints/experience-platform/deployment/appsdk.md)
+ 受众和用户档案激活{#audience-activation}
   + [Device Based — 使用Audience Manager进行匿名受众定位](/help/blueprints/audience-activation/audience-manager.md)
   + Real-Time Customer Data Platform (RTCDP) {#known-customer-audience-activation}
      + [Audience Activation到社交和广告目标](/help/blueprints/audience-activation/advertising-activation.md)
      + [将受众和配置文件激活到企业目标Blueprint](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [支持与销售方案的实时配置文件访问](/help/blueprints/audience-activation/customer-activity.md)
      + [用于Web和移动个性化的实时边缘配置文件访问](/help/blueprints/audience-activation/real-time-lookup.md)
      + [使用区段匹配进行受众协作](/help/blueprints/audience-activation/segment-match.md)
      + [使用Target实现已知的客户个性化](/help/blueprints/audience-activation/rtcdp-target.md)
+ B2B激活和营销{#b2b-activation}
   + [概述](/help/blueprints/b2b/overview.md)
   + [B2B激活](/help/blueprints/b2b/b2bactivation.md)
   + [B2B帐户激活](/help/blueprints/b2b/b2b-account-activation.md)
   + [购买基于群组的营销和历程管理](/help/blueprints/b2b/b2b-buying-group-journeys.md)
   + [使用Marketo数据的B2B历程](/help/blueprints/b2b/b2b-journeys-with-marketo.md)
   + [B2B付费媒体控制器](/help/blueprints/b2b/ajo-b2b-paid-media-controller.md)
   + Marketo Engage和Workfront集成Blueprint{#marketo-engage-and-workfront-integration-blueprint}
      + [概述](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md)
      + [摄取和创建](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md)
      + [审阅并批准](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md)
      + [客户成功案例](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md)
+ Customer Journey Analytics{#customer-journey-analytics}
   + [概述](/help/blueprints/customer-journey-analytics/overview.md)
   + [B2B Customer Journey Analytics](/help/blueprints/customer-journey-analytics/b2b-cja.md)
   + [将CJA受众共享到RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
   + [CJA 和 Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
+ 客户历程{#customer-journeys}
   + [概述](/help/blueprints/customer-journeys/overview.md)
   + Journey Optimizer{#journey-optimizer}
      + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md)
      + [AJO历程](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md)
      + [AJO营销活动](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md)
      + [第三方报文传送](/help/blueprints/customer-journeys/journey-optimizer/3rd-party-messaging.md)
   + 决策管理{#decision-management}
      + [概述](/help/blueprints/customer-journeys/decision-management/decision-management-overview.md)
      + [Edge上的决策管理](/help/blueprints/customer-journeys/decision-management/decision-management-edge.md)
      + [中心上的决策管理](/help/blueprints/customer-journeys/decision-management/decision-management-hub.md)
   + Campaign v8{#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8/campaign-v8-overview.md)
      + [Real-Time CDP与Adobe [!DNL Campaign] v8](/help/blueprints/customer-journeys/campaign-v8/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer 与 Adobe Campaign v8](/help/blueprints/customer-journeys/campaign-v8/ajo-and-campaign-v8.md)
   + 已弃用的Blueprint{#deprecated-blueprints}
      + Campaign Standard{#campaign-standard}
         + [[!DNL Campaign Standard]](https://experienceleague.adobe.com/zh-hans/docs/campaign-standard){target="_blank"}
         + [Real-Time CDP与Adobe [!DNL Campaign Standard]](https://experienceleague.adobe.com/zh-hans/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/get-started-sources-destinations)
      + Campaign v7{#campaign-v7}
         + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md)
+ 数据分析、智能和 AI/ML{#data-exploration}
   + [数据分析和智能](/help/blueprints/data-insights/analysis.md)
   + [用于扩充用户档案的自定义数据科学](/help/blueprints/data-insights/data-science.md)