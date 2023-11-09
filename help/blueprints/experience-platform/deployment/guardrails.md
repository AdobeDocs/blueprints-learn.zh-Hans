---
title: Experience Platform 和应用程序护栏
description: 护栏定义了对 Adobe Experience Platform 和应用程序中组件和服务的性能期望和影响
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 4379f372241248ea6c70c766f13a182783fcac0c
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 64%

---

# 护栏

护栏是建议的阈值，可为Adobe Experience Platform和应用程序中的数据使用和系统使用提供指导。 护栏反映了系统限制和性能期望，可优化客户架构和用例性能，并有助于避免错误或意外结果。 护栏不是用来作为服务级别协议的。

有关应用程序和功能的特定服务级别协议的信息，请参阅 [应用程序和功能描述](#application-feature-descriptions) 部分。


## Adobe Experience Platform 和应用程序的护栏参考文档

以下页面提供了有关Adobe Experience Platform功能、服务和应用程序的护栏的信息：

**Experience Platform应用程序**

* [Real-Time CDP护栏概述](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Customer Journey Analytics受众共享护栏](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=zh-Hans#latency)
* [Customer Journey Analytics数据摄取护栏](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=zh-Hans#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer护栏](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=zh-Hans)

**Experience Platform服务**

* [数据摄入护栏](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html?lang=zh-Hans)
* [边缘网络 API 护栏](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html?lang=zh-Hans)
* [实时客户档案护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* [身份护栏](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=zh-Hans)
* [查询服务护栏](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=zh-Hans)
* [目标激活护栏](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=zh-Hans)



## 端到端延迟图

### 数据摄入

<img src="assets/aep_data_flow_guardrails.svg" alt="Experience Platform 数据流" style="border:1px solid #4a4a4a" width="85%" />

<br>

### 分段

<img src="assets/segmentation_guardrails.svg" alt="Experience Platform 分段护栏" style="border:1px solid #4a4a4a" width="85%" />

<br>

### Real-time Customer Data Platform 和 Adobe Target

<img src="assets/RTCDP_Target_guardrails.svg" alt="RTCDP 和 Target 护栏" style="border:1px solid #4a4a4a" width="85%" />

<br>

### Customer Journey Analytics

<img src="assets/CJA_guardrails.svg" alt="CJA 护栏" style="border:1px solid #4a4a4a" width="85%" />

<br>

### Journey Optimizer

<img src="assets/AJO_guardrails.svg" alt="参考架构 Journey Optimizer Blueprint" style="width:85%; border:1px solid #4a4a4a" />

<br>

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
