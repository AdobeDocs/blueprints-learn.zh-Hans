---
title: Experience Platform 和应用程序护栏
description: 护栏定义了对 Adobe Experience Platform 和应用程序中组件和服务的性能期望和影响
solution: Experience Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 13%

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
* [Customer Journey Analytics数据摄取护栏](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=zh-Hans#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer护栏](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=zh-Hans)

**Experience Platform服务**

* [数据摄入护栏](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html?lang=zh-Hans)
* [[!DNL Edge Network] API护栏](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html?lang=zh-Hans)
* [实时客户个人资料和分段护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* [身份护栏](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=zh-Hans)
* [查询服务护栏](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=zh-Hans)
* [目标激活护栏](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=zh-Hans)

## 端到端延迟图 {#end-to-end-latency}

### Experience Platform Edge Network和中心主要观察到的延迟 {#edge-hub-latencies}

下图描述了在Experience Platform和应用程序上构建用例时要注意的主要边缘和中心观察延迟。

![Experience Platform [!DNL Edge Network]和中心主观察到的延迟。](/help/blueprints/experience-platform/assets/aep_edge_hub_latency_v1.svg "Experience Platform Edge Network和中心主观测延迟"){width="1000" zoomable="yes"}