---
title: offer decisioning在边缘
description: 跨渠道（包括实时Web体验和移动体验）向消费者提供个性化优惠。
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: 7f566536c4ff5a6af321d60058ad67c13c28bf64
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 34%

---

# Journey Optimizer — 边缘Offer decisioning

要了解有关决策管理的更多信息，请参阅产品文档 [此处](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html) 和Offer decisioning概述 [此处](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-overview.html)

Adobe决策管理是作为Adobe Journey Optimizer的一部分提供的服务。 此蓝图概述了应用程序的用例和技术功能，并深入介绍了构成Offer decisioning的各种体系结构组件和注意事项。

决策管理可以通过两种方式之一进行部署。 第一种方式是通过Adobe Experience Platform中心，该中心是一个数据中心架构。 在“中心”方法中，会在第二个延迟内执行、个性化和交付选件。 因此，中心架构最适合不需要亚秒延迟的客户体验，例如，为诸如呼叫中心或个人交互中的网亭或代理辅助体验提供的选件决策。

第二种方法是通过Experience Edge Network，它是分布在全球各地的基础架构，可提供快速且在几秒钟以内的体验。 最靠近消费者地理位置的边缘基础架构执行的最终消费者体验，可最大程度地减少延迟。 Edge上的决策管理旨在提供实时的消费者体验。 这些体验包括Web或移动入站个性化请求等体验。

此蓝图将介绍Edge上决策管理的具体细节。

要详细了解中心上的决策管理，请参阅 [中心上的决策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-hub.html) 蓝图。

## 边缘决策管理用例

* 通过Web或移动设备入站体验进行在线个性化。
* 跨渠道历程执行 — 通过Adobe Journey Optimizer提供跨Web、移动设备、电子邮件和其他交互渠道的一致性。

<br>

## 架构

<img src="../assets/offers_edge.svg" alt="边缘Blueprint上的引用架构Offer decisioning" style="width:100%; border:1px solid #4a4a4a" />

<br>

## 集成模式

| 集成 | 描述 |
| :-- | :--- |
| [offer decisioningAdobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html) | offer decisioning可以与Adobe Target集成，以便选件可以作为Target体验进行测试和交付。 |

## 先决条件

Adobe Experience Platform

* 必须在系统中配置架构和数据集，然后才能配置 Journey Optimizer 数据源
* 对于基于体验事件类的架构，当您希望触发的事件不是基于规则的事件时，请添加“编排事件 ID 字段组”
* 对于基于个人用户档案类的架构，添加“用户档案测试详细信息”字段组，以便能够加载测试用户档案以与 Journey Optimizer 一起使用

<br>

## 护栏

* 有关Journey Optimizer护栏，请参阅以下内容 [Journey Optimizer护栏](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html).
* 有关Offer decisioning护栏，请参阅以下内容 [offer decisioning产品描述](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html).

### 数据摄入护栏

<img src="../assets/aep-data-ingestion-details-latency.svg" alt="参考架构 Journey Optimizer Blueprint" style="width:80%; border:1px solid #4a4a4a" />

<br>

### 激活护栏

<img src="../assets/ajo-activation-details-latency.svg" alt="参考架构 Journey Optimizer Blueprint" style="width:80%; border:1px solid #4a4a4a" />

<br>

## 实施模式

* 使用Web SDK或Mobile SDK在网站和移动应用程序上部署，以实施部署SDK的Offer decisioning。
   * [Web/Mobile SDK蓝图](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/data-ingestion/websdk.html?lang=zh-Hans)
   * [WebSDK](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/offer-decisioning/offer-decisioning-overview.html)
   * [MobileSDK](https://aep-sdks.gitbook.io/docs/)

或

* 对于基于API服务器到服务器的实施，请使用边缘网络服务API将服务器直接实施到服务器Offer decisioning。
   * [边缘网络服务器API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/deliver-offers.html)

<br>

## 实施步骤

### Adobe Experience Platform

#### 模式/数据集

1. 根据客户提供的数据在 Experience Platform 中[配置单个用户档案、体验事件和多实体模式。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 为要摄入的数据在 Experience Platform 中[创建数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)。
1. 在 Experience Platform 中为数据集[添加数据使用标签](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hans)以便进行治理。
1. [创建对目标实施治理的策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hans)。

#### 用户档案/身份

1. [创建任何客户特定的命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)。
1. [向模式添加身份](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [为用户档案启用架构和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。
1. 为[!UICONTROL 实时客户档案]的不同视图[设置合并策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hans)（可选）。
1. 创建区段以用于 Journey。

#### 源/目标

1. 使用流传输 API 和源连接器[将数据摄入 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans)

## 相关文档

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Adobe Journey Optimizer决策管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Adobe Journey Optimizer产品描述](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [AdobeOffer decisioning产品说明](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)