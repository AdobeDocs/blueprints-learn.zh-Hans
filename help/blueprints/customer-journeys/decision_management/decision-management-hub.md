---
title: 中心决策管理 Blueprint
description: 跨渠道向消费者投放个性化优惠，包括自助终端、座席协助体验、电子邮件以及其他推拨投放。
solution: Experience Platform, Journey Optimizer
exl-id: 5a386e18-bbac-4216-a35f-0a5016785e4a
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 80%

---

# 中心决策管理 Blueprint

要了解有关决策管理的更多信息，请参阅[此处](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=zh-Hans)的产品文档和[此处](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=zh-Hans)的决策管理概述

Adobe 决策管理是作为 Adobe Journey Optimizer 的一部分提供的服务。此 Blueprint 概述了该应用程序的用例和技术功能，并深入介绍了构成决策管理的各种架构组件和注意事项。

Journey Optimizer 用于跨所有接触点在适当的时间为客户提供最佳优惠和体验。决策管理通过集中的营销优惠库和决策引擎轻松实现个性化，该引擎可将规则和约束应用于 Adobe Experience Platform 创建的丰富实时用户档案，以帮助您在适当的时间向客户发送适当的优惠。

决策管理可以通过两种方式进行部署。第一种是通过 Adobe Experience Platform 中心，即采用中央数据中心架构。对于“中心”方法，执行、个性化和投放优惠的延迟在 500 毫秒以上。因此，中心架构最适合不需要亚秒级延迟的客户体验，例如，为自助终端、呼叫中心中的座席协助体验或者个人交互提供的优惠决策。插入到电子邮件和推拨营销活动中的优惠同样由中心方法提供支持。

第二种方法是通过Experience [!DNL [!DNL Edge Network]]，它是一种分布在全球的地理位置的基础架构，可提供快速的次秒和毫秒体验。 由最靠近消费者地理位置的边缘基础架构执行最终消费者体验，可最大程度地减少延迟。边缘决策管理旨在提供实时客户体验，例如 Web 或移动集客个性化请求。

此 Blueprint 将介绍中心决策管理的具体细节。

要了解有关边缘决策管理的更多信息，请参阅[边缘决策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-edge.html?lang=zh-Hans) Blueprint。

## 中心决策管理用例

* 个人资料上下文延迟不严格的流用例 — 延迟为15分钟或更高。
* 自助终端和店内体验中的个性化优惠。
* 通过座席辅助体验提供的个性化优惠，例如用于呼叫中心或销售互动。
* 电子邮件、短信、移动推送通知或其他推拨交互中包含的优惠。
* 向外部 ESP 和消息递送系统提供优惠以供投放。
* 跨渠道历程执行 - 通过 Adobe Journey Optimizer 提供跨 Web、移动设备、电子邮件和其他交互渠道的一致性。

>[!IMPORTANT]
>
>适用于需要访问用户档案以获取其他信息和上下文的优惠和历程用例。 请务必考虑将数据摄取到中心服务器上关联的延迟，以确保在决策时可用。 如果上下文正在流式传输或摄取到配置文件中，并且优惠或历程必须在优惠决策后的数秒或数分钟内提供该上下文，则最好通过Edge上的决策管理提供这些方案。

## 架构

<img src="../assets/offers_hub.svg" alt="边缘决策管理参考架构 Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## 护栏

* 有关 Journey Optimizer 护栏，请参阅以下 [Journey Optimizer 护栏](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=zh-Hans)。
* 有关决策管理护栏，请参阅以下[决策管理产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/offer-decisioning-app-service.html).

[护栏和端到端延迟指导](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html)

## 实施模式

* 通过直接与 [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/offers-e2e.html?lang=zh-Hans) 集成，在电子邮件、短信和推拨渠道中实施。
* 对于基于服务器 API 的决策管理实施，请利用[决策 API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/decisioning-vs-edge-apis.html?lang=zh-Hans)。
* 要实施基于批次的决策，以便将优惠批量投放到消息投放应用程序，请使用[批量决策 API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/batch-decisioning-api.html?lang=zh-Hans)。
* 对于基于边缘的实时体验，请按照[边缘决策管理 Blueprint](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-edge.html?lang=zh-Hans) 中的说明使用 Web/Mobile SDK 或 Edge Decisioning API。

## 相关文档

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=zh-Hans)
* [Adobe Journey Optimizer 决策管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=zh-Hans)
* [Adobe Journey Optimizer 产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe 决策管理产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/offer-decisioning-app-service.html)
