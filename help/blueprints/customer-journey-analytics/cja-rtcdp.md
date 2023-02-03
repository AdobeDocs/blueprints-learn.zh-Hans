---
title: Customer Journey AnalyticsReal-time Customer Data Platform Blueprint
description: 在 Customer Journey Analytics 中统一并分析整个客户历程中的数据和客户行为，将受众从 CJA 发布到 RTCDP
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
source-git-commit: 8355a36a235d847a6faf2398f3fadbed28ccac37
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 89%

---

# Customer Journey AnalyticsReal-time Customer Data Platform Blueprint

创建在 Customer Journey Analytics (CJA) 中识别的受众并将其发布到 Adobe Experience Platform 中的实时客户档案，以用于客户定位和个性化。非常适用于使用历史数据创建受众，或通过 Customer Journey Analytics 中的精细筛选和计算字段得出更细化的受众。

## Customer Journey Analytics 受众发布指南

有关从Customer Journey Analytics到Real-time Customer Data Platform的受众发布的实施和配置的指导，请参阅以下文档。 [文档](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=zh-Hans)

## Customer Journey Analytics 的架构 Blueprint

![架构图](assets/CJA_RTCDP.svg)

## Customer Journey Analytics 护栏图 Blueprint

* 有关详细的护栏和端到端延迟，请参阅[部署护栏文档](../experience-platform/deployment/guardrails.md)

![护栏图](../experience-platform/assets/CJA_guardrails.svg)

## 常见问题

* 如果 CJA 发送的 RTCDP 中不存在相应的用户档案，是会创建新用户档案，还是仅从 CJA 为已存在的用户档案记录受众？是，将创建新用户档案。因此，如果 RTCDP 实施仅面向已知客户，则应编写 CJA 受众规则以仅筛选具有已知身份的用户档案。这将确保在不需要时，RTCDP 用户档案计数不会因匿名用户档案而增加。

* CJA 将受众数据作为管道事件发送，还是作为同样会发送到数据湖的平面文件发送？CJA 受众通过管道流传输到 RTCDP 用户档案服务，但数据也作为数据集存储在数据湖中。

* CJA 会发送哪些标识？CJA 会发送在 CJA 配置期间已配置为“人员 ID”的标识。

* 将什么设置为主标识？用户在将 CJA 设置为主“人员”ID 时选择的任何标识。

* 标识服务是否也会处理 CJA 消息？例如，CJA 是否可以通过受众共享向用户档案标识图添加标识？不能，标识服务不处理 CJA 消息。

## 相关博客帖子

* [[!DNL Blueprint for Multi-Channel Orchestration in Adobe Experience Platform]](https://medium.com/adobetech/blueprint-for-multi-channel-orchestration-in-adobe-experience-platform-c68317e94184)
* [[!DNL Leveraging External Data Platforms in Adobe Experience Platform Journey Orchestration]](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17)
* [[!DNL Event-Based Triggering on Adobe Experience Platform Orchestration Service using Apache Airflow]](https://medium.com/adobetech/event-based-triggering-on-adobe-experience-platform-orchestration-service-using-apache-airflow-8607b28251f1)
* [[!DNL Adobe Campaign Classic Integration with Journey Orchestration]](https://medium.com/adobetech/adobe-campaign-classic-integration-with-journey-orchestration-ae577653281)
* [[!DNL Demonstrating the Power of Adobe's New Journey Orchestration Service to Build Personalized Omnichannel Experiences in Real-Time]](https://medium.com/adobetech/demonstrating-the-power-of-adobes-new-journey-orchestration-service-to-build-personalized-aa60d88cd34)
* [[!DNL Journey Orchestration in an Omnichannel World]](https://medium.com/adobetech/journey-orchestration-in-an-omnichannel-world-3a2d32d556d9)
