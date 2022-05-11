---
title: offer decisioning概述
description: 跨客户历程提供个性化优惠。
solution: Experience Platform, Journey Optimizer
source-git-commit: 7f566536c4ff5a6af321d60058ad67c13c28bf64
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 2%

---

# Journey Optimizer -Offer decisioning概述

要了解有关决策管理的更多信息，请参阅产品文档 [此处](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)

Adobe决策管理是作为Adobe Journey Optimizer的一部分提供的服务。 此蓝图概述了应用程序的用例和技术功能，并深入介绍了构成Offer decisioning的各种体系结构组件和注意事项。

Journey Optimizer用于在适当的时间跨所有接触点为客户提供最佳选件和体验。 offer decisioning通过集中的营销选件库和决策引擎(该引擎可将规则和约束应用于Adobe Experience Platform创建的丰富实时用户档案，以帮助您在适当的时间向客户发送正确的选件)，从而轻松实现个性化。

决策管理功能包含两个主要组件：

* 集中式选件库，您可以在其中创建和管理构成选件的不同元素，并定义其规则和约束。
* 选件决策引擎可利用Adobe Experience Platform数据和实时客户配置文件，以及选件库，以选择要将选件交付到的正确时间、客户和渠道。

<img src="../assets/offers_overview.png" alt="offer decisioning" style="width:100%; border:1px solid #4a4a4a" />

决策管理可以通过两种方式之一进行部署。

## 中心上的决策管理

第一个是通过Adobe Experience Platform中心，该中心是一个中央数据中心架构。 在“中心”方法中，可在500毫秒以上的延迟内执行、个性化和交付选件。 因此，中心架构最适合不需要亚秒延迟的客户体验，例如，为诸如呼叫中心或个人交互中的网亭或代理辅助体验提供的选件决策。 插入到电子邮件、短信消息或推送通知和其他出站促销活动中的选件也由中心方法提供支持。 要详细了解中心上的决策管理，请参阅 [中心上的决策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-hub.html?lang=en) 蓝图。

### 中心上的决策管理用例

* 在网亭和商店体验上提供个性化选件。
* 通过座席辅助体验提供的个性化选件，例如呼叫中心或销售行动。
* 电子邮件、短信或其他出站交互中包含的选件。
* 跨渠道历程执行 — 通过Adobe Journey Optimizer提供跨Web、移动设备、电子邮件和其他交互渠道的一致性。

## 边缘决策管理

第二种方法是通过Experience Edge Network，它是分布在全球各地的基础架构，可提供快速且在几秒钟以内的体验。 最靠近消费者地理位置的边缘基础架构执行的最终消费者体验，可最大程度地减少延迟。 Edge上的决策管理旨在提供实时客户体验，例如Web或移动入站个性化请求。 要详细了解Edge上的决策管理，请参阅 [边缘决策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-edge.html?lang=en) 蓝图。

### 边缘决策管理用例

* 通过Web或移动设备入站体验进行在线个性化。
* 跨渠道历程执行 — 通过Adobe Journey Optimizer提供跨Web、移动设备、电子邮件和其他交互渠道的一致性。

## 相关文档

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Adobe Journey Optimizer决策管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Adobe Journey Optimizer产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)
* [AdobeOffer decisioning产品说明](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)