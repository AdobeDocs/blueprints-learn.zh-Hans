---
title: Experience Platform 和应用程序护栏
description: 护栏定义了对 Adobe Experience Platform 和应用程序中组件和服务的性能期望和影响
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 2ff576ccb4ac3f9e2bdb690b6e9242d674214c33
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 15%

---

# 护栏

护栏是建议的阈值，可为Adobe Experience Platform和应用程序中的数据、观察到的延迟和系统使用情况提供指导。 护栏反映了系统限制和性能期望，可优化客户架构和用例性能，并有助于避免错误或意外结果。 护栏不是服务级别协议，服务级别协议记录在以下链接的产品描述和客户许可协议中。 护栏旨在为特定客户用例的架构解决方案提供指导，以确保稳定性和执行。

有关应用程序和功能的特定服务级别协议的信息，请参阅 [应用程序和功能描述](#application-feature-descriptions) 部分。

请注意，对于任何具有严格延迟或数量要求的客户用例，Adobe建议与您的Adobe客户团队和实施合作伙伴一起详细审查您的用例。 在某些情况下，建议在用例的生产启动之前测试和观察给定用例实施，以观察和了解预期行为 — 由于每个客户实施具有不同的作用因素，包括数据摄取的性质和频率、正在构建的区段规则的细节以及各种激活渠道和负载 — 每个用例实施将具有不同的观察性能。 因此，最好预先建立和测试预期性能，以确保根据用例的延迟和性能要求获得适当的架构和实施。


## Adobe Experience Platform 和应用程序的护栏参考文档

以下页面提供了有关Adobe Experience Platform功能、服务和应用程序的护栏的信息：

**Experience Platform应用程序**

* [Real-Time CDP护栏概述](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Customer Journey Analytics受众共享护栏](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Customer Journey Analytics数据摄取护栏](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer护栏](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Experience Platform服务**

* [数据摄入护栏](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [边缘网络 API 护栏](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [实时客户个人资料和分段护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* [身份护栏](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=zh-Hans)
* [查询服务护栏](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=zh-Hans)
* [目标激活护栏](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=zh-Hans)

## 端到端延迟图 {#end-to-end-latency}

### 观察到Experience Platform边缘网络和集线器主要延迟 {#edge-hub-latencies}

下图描述了在Experience Platform和应用程序上构建用例时要注意的主要边缘和中心观察延迟。

![Experience Platform边缘网络和集线器主要观察到的延迟。](/help/blueprints/experience-platform/deployment/assets/aep_edge_hub_latency.svg "观察到Experience Platform边缘网络和集线器主要延迟"){width="1000" zoomable="yes"}

### 数据摄入 {#data-ingestion}

下图显示预期的数据摄取延迟值： [流式摄取](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) 和 [批量摄取](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=zh-Hans) 将数据引入Real-Time CDP时。 单击图像可查看高分辨率版本。

![摄取数据高级可视化概述。](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "数据摄取高级可视化概述和延迟值"){width="1000" zoomable="yes"}

### 分段 {#segmentation}

下图显示了使用中的受众时的预期滞后时间值 [Real-Time CDP分段服务](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hans). 单击图像可查看高分辨率版本。

![分段高级视觉概述。](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "分段高级视觉概述和延迟值"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform和边缘网络 {#adobe-edge-latency}

下图显示了利用边缘网络时的预期滞后时间值 — 例如，利用RTCDP受众访问 [Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=zh-Hans). 单击图像可查看高分辨率版本。

![Adobe Edge网络和Experience Platform高级可视化概述。](/help/blueprints/experience-platform/deployment/assets/RTCDP_Edge_guardrails.svg "将受众导出到Adobe Target高级视觉概述和延迟"){width="1000" zoomable="yes"}

### Customer Journey Analytics   {#customer-journey-analytics}

下图显示了使用时的预期滞后时间值 [Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en). 单击图像可查看高分辨率版本。

![使用Customer Journey Analytics高级视觉概述。](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "使用Customer Journey Analytics高级视觉概述和延迟值"){width="1000" zoomable="yes"}

### Journey Optimizer   {#journey-optimizer}

下图显示了使用时的预期滞后时间值 [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en). 单击图像可查看高分辨率版本。

![使用Adobe Journey Optimizer高级可视化概述。](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "使用Adobe Journey Optimizer高级可视化概述和延迟值"){width="1000" zoomable="yes"}

## 应用程序和功能描述 {#application-feature-descriptions}

有关特定于功能的服务级别协议的信息，请参阅下面的产品说明：

* [Experience Platform Collection Enterprise](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-experience-platform-collection-enterprise.html)
* [Real-time Customer Data Platform](https://helpx.adobe.com/cn/legal/product-descriptions/real-time-customer-data-platform.html)
* [B2B 客户数据平台](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-experience-platform-b2b.html)
* [Experience Platform Activation](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-experience-platform0.html)
* [Experience Platform 智能](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [智能服务](https://helpx.adobe.com/cn/legal/product-descriptions/intelligent-services.html)
* [Data Distiller](https://helpx.adobe.com/cn/legal/product-descriptions/data-distiller.html)
* [Customer Journey Analytics](https://helpx.adobe.com/cn/legal/product-descriptions/customer-journey-analytics.html)
* [Journey Optimizer](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)
* [Journey Orchestration](https://helpx.adobe.com/cn/legal/product-descriptions/journey-orchestration.html)
* [Offer Decisioning](https://helpx.adobe.com/cn/legal/product-descriptions/offer-decisioning-app-service.html)
