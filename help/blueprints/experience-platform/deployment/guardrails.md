---
title: Experience Platform 和应用程序护栏
description: 护栏定义了对 Adobe Experience Platform 和应用程序中组件和服务的性能期望和影响
solution: Experience Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: a5d127c2a9e18ebbf25012475b9f474c07575362
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 10%

---


# 护栏

护栏反映了系统限制、预期延迟和性能期望，可优化客户架构和用例性能，并有助于确保稳定性、避免错误或意外结果。

## 护栏类型

| 护栏类型 | 描述 |
|---|---|
| 性能护栏（软限制） | 性能护栏是与用例范围相关的使用限制，并概述了正常条件下的预期性能。 如果超过此值，您可能会遇到性能下降和延迟问题。 性能护栏记录在Experience League文档中，位于每个解决方案的护栏部分下，如下所述。 |
| 静态限制（硬限制） | 这些是系统强制的限制，不能超过。 静态限制通常在客户合同和[产品描述](https://helpx.adobe.com/cn/legal/product-descriptions.html)中约定并列出。 |

>[!NOTE]
>
> 护栏不是用来作为服务级别协议的，而是用于指导最佳配置和预期的系统行为。 任何属于系统或合同限制或服务级别协议的护栏都将在客户合同和产品描述中具体说明。 如果您有兴趣了解自定义限制，请联系您的客户关怀代表。

>[!NOTE]
>
> 对于具有严格延迟或性能需求的用例，Adobe建议与您的Adobe客户团队和实施合作伙伴讨论详细信息。 每个客户设置可能会因数据摄取模式、用户档案计数和丰富度、区段规则和激活渠道而异。 因此，架构和测试用例以优化其性能并充分了解预期性能特征非常重要。

## Adobe Experience Platform 和应用程序的护栏参考文档

以下页面提供了有关Adobe Experience Platform功能、服务和应用程序的护栏的信息：

**Experience Platform应用程序**

* [Real-Time CDP护栏概述](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html?lang=zh-Hans)
* [Customer Journey Analytics受众共享护栏](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=zh-Hans#latency)
* [Customer Journey Analytics的数据摄取护栏](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=zh-Hans#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer护栏](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=zh-Hans)

**Experience Platform服务**

* [数据摄入护栏](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html?lang=zh-Hans)
* [[!DNL Edge Network] API护栏](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html?lang=zh-Hans)
* [实时客户个人资料和分段护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* [身份护栏](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=zh-Hans)
* [查询服务护栏](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=zh-Hans)
* [目标激活护栏](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=zh-Hans)

## 端到端延迟图 {#end-to-end-latency}

### Experience PlatformEdge Network和中心主要观察到的延迟 {#edge-hub-latencies}

下图描述了在Experience Platform和应用程序上构建用例时要注意的主要边缘和中心观察延迟。

![Experience Platform[!DNL Edge Network]和中心主观察到的延迟。](/help/blueprints/experience-platform/deployment/assets/aep_edge_hub_latency_v1.svg "Experience PlatformEdge Network和中心主观测延迟"){width="1000" zoomable="yes"}

### 数据摄入 {#data-ingestion}

下图显示了将数据引入Real-Time CDP时通过[流式引入](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html?lang=zh-Hans)和[批量引入](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=zh-Hans)进行的预期数据引入延迟值。 单击图像可查看高分辨率版本。

![数据摄取高级可视化概述。](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "数据摄取高级可视化概览和延迟值"){width="1000" zoomable="yes"}

### 分段 {#segmentation}

下图显示了在[Real-Time CDP分段服务](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hans)中使用受众时的预期滞后时间值。 单击图像可查看高分辨率版本。

![分段高级视觉概述。](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "分段高级视觉概述和延迟值"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform和[!DNL Edge Network] {#adobe-edge-latency}

下图显示了在利用[!DNL Edge Network]时的预期延迟值 — 例如，在[Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=zh-Hans)中利用RTCDP受众。 单击图像可查看高分辨率版本。

![Adobe Edge网络和Experience Platform高级可视化概述。](/help/blueprints/experience-platform/deployment/assets/RTCDP_Edge_guardrails.svg "将受众导出到Adobe Target高级视觉概述和延迟"){width="1000" zoomable="yes"}

### Customer Journey Analytics   {#customer-journey-analytics}

下图显示了使用[Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=zh-Hans)时的预期滞后时间值。 单击图像可查看高分辨率版本。

![使用Customer Journey Analytics高级视觉概述。](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "使用Customer Journey Analytics高级视觉概览和延迟值"){width="1000" zoomable="yes"}

### Journey Optimizer   {#journey-optimizer}

下图显示了使用[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=zh-Hans)时的预期滞后时间值。 单击图像可查看高分辨率版本。

![使用Adobe Journey Optimizer高级可视化概述。](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "使用Adobe Journey Optimizer高级可视化概览和延迟值"){width="1000" zoomable="yes"}