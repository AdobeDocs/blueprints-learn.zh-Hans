---
user-guide-title: 数字体验 Blueprint
breadcrumb-title: Blueprint
user-guide-description: Blueprint 是可重复实施的产品，用于应对战略和解决既定的业务问题，并包含架构图、技术注意事项和相关文档链接。
product: adobe experience platform
mini-toc-levels: 3
role: Architect, Developer, User
source-git-commit: 62dc3dff69bbf88b025373b4fdc893cc77b73594
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 56%

---


# 数字体验 Blueprint {#architecture}

+ [数字体验Blueprint](/help/blueprints/overview.md)
+ 垂直行业Blueprint{#vertical-blueprints}
   + [概述](/help/blueprints/vertical-blueprints/overview.md)
   + [服装](/help/blueprints/vertical-blueprints/apparel.md)
   + [零售](/help/blueprints/vertical-blueprints/retail.md)
   + [电信业](/help/blueprints/vertical-blueprints/telecommunications.md)
   + [旅游和酒店业](/help/blueprints/vertical-blueprints/travel-hospitality.md)
+ 架构概述 {#architecture-overview}
   + [Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
   + [Experience Platform和应用程序](/help/blueprints/experience-platform/platform-applications.md)
   + [Experience Platform数据流](/help/blueprints/experience-platform/platform-data-flow.md)
   + 部署 {#deployment}
      + [Experience PlatformWeb SDK &amp; [!DNL Edge Network]](/help/blueprints/experience-platform/deployment/websdk.md)
      + [应用程序 SDK](/help/blueprints/experience-platform/deployment/appsdk.md)
      + [护栏](/help/blueprints/experience-platform/deployment/guardrails.md)
+ 受众和用户档案激活 {#audience-activation}
   + [概述](/help/blueprints/audience-activation/overview.md)
   + [匿名受众激活](/help/blueprints/audience-activation/anonymous.md)
   + 已知客户激活 (RTCDP) {#known-customer-audience-activation}
      + [概述](/help/blueprints/audience-activation/known.md)
      + [激活社交和广告渠道](/help/blueprints/audience-activation/advertising-activation.md)
      + [激活文件和企业流目标](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [客户活动中心](/help/blueprints/audience-activation/customer-activity.md)
      + [区段匹配](/help/blueprints/audience-activation/segment-match.md)
   + [使用Experience Cloud应用程序激活](/help/blueprints/audience-activation/platform-and-applications.md)
   + Web 和移动个性化 {#web-personalization}
      + [概述](/help/blueprints/audience-activation/web-personalization/overview.md)
      + [行为个性化 — Target](/help/blueprints//audience-activation/web-personalization/behavioral.md)
      + [已知客户个性化 — Target和RTCDP](/help/blueprints/audience-activation/web-personalization/known-personalization.md)
      + [决策管理](/help/blueprints/audience-activation/web-personalization/decision-management-edge.md)
+ B2B 激活与营销 {#b2b-activation}
   + [概述](/help/blueprints/b2b/overview.md)
   + [B2B激活](/help/blueprints/b2b/b2bactivation.md)
   + Marketo Engage 和 Workfront 集成 Blueprint{#marketo-engage-and-workfront-integration-blueprint}
      + [概述](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md)
      + [摄取和创建](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md)
      + [审阅并批准](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md)
      + [客户成功案例](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md)
+ 内容和Commerce{#content-commerce}
   + [Adobe Commerce和RTCDP](/help/blueprints/content-commerce/commerce/commerce-rtcdp.md)
+ Customer Journey Analytics {#customer-journey-analytics}
   + [概述](/help/blueprints/customer-journey-analytics/overview.md)
   + [将CJA受众共享到RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
   + [CJA 和 Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
+ 客户历程 {#customer-journeys}
   + [概述](/help/blueprints/customer-journeys/overview.md)
   + Journey Optimizer {#journey-optimizer}
      + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer.md)
      + 决策管理 {#decision-management}
         + [概述](/help/blueprints/customer-journeys/decision_management/decision-management-overview.md)
         + [边缘决策管理](/help/blueprints/customer-journeys/decision_management/decision-management-edge.md)
         + [中心决策管理](/help/blueprints/customer-journeys/decision_management/decision-management-hub.md)
      + [Journey Optimizer 与 Adobe Campaign  ](/help/blueprints/customer-journeys/ajo-and-campaign.md)
      + [第三方报文传送](/help/blueprints/customer-journeys/3rd-party-messaging.md)
   + Campaign Standard {#campaign-standard}
      + [[!DNL Campaign Standard]](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hans){target="_blank"}
      + Adobe为 [!DNL Campaign Standard]的[Real-Time CDP](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=zh-Hans){target="_blank"}
   + Campaign v8 {#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8.md)
      + [Adobe为 [!DNL Campaign] v8的Real-Time CDP](/help/blueprints/customer-journeys/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer 与 Adobe Campaign v8](/help/blueprints/customer-journeys/ajo-and-campaign-v8.md)
   + Campaign v7 {#campaign-v7}
      + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7.md)
      + [Adobe为 [!DNL Campaign] v7的Real-Time CDP](/help/blueprints/customer-journeys/rtcdp-and-campaign.md)
      + [Adobe为 [!DNL Campaign] v7的Journey Optimizer](/help/blueprints/customer-journeys/ajo-and-campaign-v7.md)
+ 数据收集、访问和导出 {#data-ingestion}
   + [概述](/help/blueprints/data-ingestion/overview.md)
   + [多沙盒事件转发数据收集](/help/blueprints/data-ingestion/multi-sandbox-event-forwarding.md)
   + [数据准备和引入](/help/blueprints/data-ingestion/ingestion.md)
   + [数据访问和导出](/help/blueprints/data-ingestion/egress.md)
   + [事件转发](/help/blueprints/data-ingestion/server-side-collection.md)
+ 数据分析、智能和 AI/ML {#data-exploration}
   + [概述](/help/blueprints/data-insights/overview.md)
   + [数据分析和智能](/help/blueprints/data-insights/analysis.md)
   + [用于扩充用户档案的自定义数据科学](/help/blueprints/data-insights/data-science.md)
