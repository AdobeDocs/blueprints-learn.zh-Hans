---
title: 边缘决策管理 Blueprint
description: 跨渠道向消费者提供个性化优惠，包括实时 Web 体验和移动体验。
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: f6c4a0f39acdc177ac23c4314d2f50f793cbf270
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 68%

---

# Journey Optimizer - Edge Blueprint上的[!DNL Decision Management]

[!DNL Decision Management]是作为[!DNL Journey Optimizer]的一部分提供的服务。 此 Blueprint 概述了该应用程序的用例和技术功能，并深入介绍了构成决策管理的各种架构组件和注意事项。

>[!MORELIKETHIS]
>
>要了解有关[!DNL Decision Management]的更多信息，请参阅[Blueprint概述](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=zh-Hans)或访问[产品文档](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=zh-Hans)。

[!DNL Decision Management]可通过两种方式之一进行部署。 第一个是通过[!DNL Experience Platform]中心，它是一个单一的数据中心架构。 对于“中心”方法，执行、个性化和投放优惠的延迟为一秒左右。因此，中心架构最适合不需要亚秒级延迟的客户体验，例如，为自助终端、呼叫中心中的座席协助体验或者个人交互提供的优惠决策。

第二种方法是通过Experience Platform[!DNL Edge Network]，它是一种分布在全球的地理位置的基础架构，可提供快速的次秒和毫秒体验。 Edge基础架构正在执行的与消费者地理位置最接近的最终消费者体验，旨在最大程度地减少延迟。 Edge上的[!DNL Decision Management]旨在提供实时消费者体验。 这些体验包括 Web 或移动入站个性化请求等体验。

此 Blueprint 将介绍边缘决策管理的具体细节。

要了解有关中心决策管理的更多信息，请参阅[中心决策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-hub.html?lang=zh-Hans) Blueprint。

## 边缘决策管理用例

* 个人资料上下文延迟严格低于15分钟延迟且决策管理执行为亚秒的流使用案例。
* 通过 Web 或移动设备集客体验进行在线个性化。
* 跨渠道历程执行 - 通过 Adobe Journey Optimizer 提供跨 Web、移动设备、电子邮件和其他交互渠道的一致性。

## 架构

<img src="../assets/offers_edge.svg" alt="边缘决策管理参考架构 Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## 集成模式

| 集成 | 描述 |
| :-- | :--- |
| [使用 Adobe Target 进行决策管理](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html?lang=zh-Hans) | 决策管理可以与 Adobe Target 集成，以便将优惠作为 Target 体验进行测试和投放。 |

## 护栏

* 有关 Journey Optimizer 护栏，请参阅以下 [Journey Optimizer 护栏](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=zh-Hans)。

* 有关决策管理护栏，请参阅以下[决策管理产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/offer-decisioning-app-service.html).

[护栏和端到端延迟指导](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html?lang=zh-Hans)

## 相关文档

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=zh-Hans)
* [Adobe Journey Optimizer 决策管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=zh-Hans)
* [Adobe Journey Optimizer 产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe 决策管理产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/offer-decisioning-app-service.html)
