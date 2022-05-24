---
title: offer decisioning概述
description: 跨客户历程提供个性化优惠。
solution: Experience Platform, Journey Optimizer
exl-id: f6271802-faab-4ffc-92d6-4c4d7d423ed4
source-git-commit: 7dcbf86b362350312a86445bbe7a020f5ccd1752
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 48%

---

# Journey Optimizer -Offer decisioning概述

要了解有关决策管理的更多信息，请参阅[此处](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=zh-Hans)的产品文档

Adobe 决策管理是作为 Adobe Journey Optimizer 的一部分提供的服务。此 Blueprint 概述了该应用程序的用例和技术功能，并深入介绍了构成 Offer Decisioning 的各种架构组件和注意事项。

Journey Optimizer用于在适当的时间跨所有接触点为客户提供最佳选件和体验。 offer decisioning通过集中的营销选件库和决策引擎(该引擎可将规则和约束应用于Adobe Experience Platform创建的丰富实时用户档案，以帮助您在适当的时间向客户发送正确的选件)，从而轻松实现个性化。

决策管理功能包含两个主要组件：

* 集中式选件库，您可以在其中创建和管理构成选件的不同元素，并定义其规则和约束。
* 选件决策引擎可利用Adobe Experience Platform数据和实时客户配置文件，以及选件库，以选择要将选件交付到的正确时间、客户和渠道。

<img src="../assets/offers_overview.png" alt="Offer Decisioning" style="width:100%; border:1px solid #4a4a4a" />

决策管理可以通过以下两种方式之一进行部署：边缘或通过集线器。 每种方法都具有一组用于操作服务的特定接口和协议，如下面各自引用的蓝图中所述。 决策管理文档中还提供了其他详细信息 [此处](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery-api/decisioning-vs-edge-apis.html).

## 中心上的决策管理

第一种是通过 Adobe Experience Platform 中心，即采用中央数据中心架构。对于“中心”方法，执行、个性化和投放优惠的延迟在 500 毫秒以上。因此，中心架构最适合不需要亚秒级延迟的客户体验，例如，为自助终端、呼叫中心中的座席协助体验或者个人交互提供的优惠决策。插入到电子邮件、短信消息或推送通知和其他出站促销活动中的选件也由中心方法提供支持。 要了解有关中心决策管理的更多信息，请参阅[中心决策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-hub.html?lang=zh-Hans) Blueprint。

* 选件资格可针对完整的实时客户资料（包括所有属性和体验事件）进行操作

### 中心上的决策管理用例

* 自助终端和店内体验中的个性化优惠。
* 通过座席辅助体验提供的个性化优惠，例如用于呼叫中心或销售互动。
* 电子邮件、短信或其他推拨交互中包含的优惠。
* 跨渠道历程执行 - 通过 Adobe Journey Optimizer 提供跨 Web、移动设备、电子邮件和其他交互渠道的一致性。

### 关于中心技术考虑事项的决策管理

* 每秒请求数= 2000。
* 响应的延迟小于500毫秒。
* 访问完整的实时客户用户档案，包括受众成员资格、属性和体验事件。

## 边缘决策管理

第二种方法是通过 Experience Edge 网络，它是分布在全球各地的基础架构，可提供快速的亚秒级和毫秒级体验。由最靠近消费者地理位置的边缘基础架构执行最终消费者体验，可最大程度地减少延迟。边缘决策管理旨在提供实时客户体验，例如 Web或移动集客个性化请求。要了解有关边缘决策管理的更多信息，请参阅[边缘决策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-edge.html?lang=zh-Hans) Blueprint。

### 边缘决策管理用例

* 通过Web或移动设备入站体验进行在线个性化。
* 跨渠道历程执行 - 通过 Adobe Journey Optimizer 提供跨 Web、移动设备、电子邮件和其他交互渠道的一致性。

### 边缘技术考虑事项的决策管理

* 每秒请求数= 5000。
* 响应的延迟少于250毫秒。
* 访问边缘实时配置文件。 配置文件中只有边缘预测受众和配置文件属性可用。
* 如果首次体验中需要个性化，则中心将是理想的选择，因为完整的用户档案可用。 边缘配置文件必须首次从集线器同步到边缘体验。 因此，从边缘网站获得的首个体验将不包含以前上传到中心的配置文件数据。

## 相关文档

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=zh-Hans)
* [Adobe Journey Optimizer 决策管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Adobe Journey Optimizer 产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe Offer Decisioning 产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/offer-decisioning-app-service.html)
