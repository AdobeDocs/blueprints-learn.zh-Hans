---
title: 支持和销售方案的实时配置文件访问
description: '[!UICONTROL 实时用户档案]查询可提供座席协助支持和销售的背景信息。'
solution: Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c
TQID: https://experienceleague.adobe.com/Ci9pUbGCLQ9uhlQ9l1na7A2NiI9CpCRMLrUSN6lSOnU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: ba929a52-9339-4154-9487-317dc875a3c7
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
  - id: e5ae22e3-a3b0-46ed-804f-9abf1bbe3e74
  - id: ee602049-8a18-43df-9299-a689a025a371
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 368
ht-degree: 54%

---

# 支持和销售方案的实时配置文件访问

>[!TIP]
>此Blueprint还作为Audience Building &amp; Activation下的[用例模式](/help/blueprints/use-case-patterns/audience-building-activation/real-time-profile-lookup.md)提供。

支持和销售方案的实时配置文件访问蓝图显示了外部应用程序如何访问Adobe Experience Platform的[!UICONTROL 实时客户配置文件]。

外部应用程序可以使用 API GET 请求来访问用户档案。 然后，存储在用户档案中的属性、事件、区段成员和模型驱动功能就可以用于这些外部非 Adobe 应用程序。

利用此功能，您可以在客户呼叫您的呼叫中心时显示丰富的背景信息。 例如，支持座席可以了解客户的存留期值、客户流失倾向或营销活动接触情况。 销售座席还可以受益于更多的背景信息和有关客户的洞察。

>[!NOTE]
>
>中心上的配置文件查找不适用于高吞吐量、低延迟的用例，如Web/移动入站个性化。 中心上的配置文件查找适用于延迟较低的情形，如代理辅助支持或销售互动。 对于低延迟、高吞吐量场景（如Web/移动个性化或实时优惠决策），应利用Edge用户档案。 Edge配置文件允许通过Real-time Customer Data Platform的[自定义Personalization连接](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization)进行实时访问。

## 用例

* 为座席支持的交互（如支持和销售体验）提供更深入的消费者背景信息。 通过对 Experience Platform 用户档案的查找，座席可以接收更多有关消费者的背景信息，例如最近购买、活动交互、倾向、受众成员，以及存储在实时客户档案中的其他属性和洞察。

## 架构

<img src="assets/customer_activity_hub.svg" alt="客户活动中心 Blueprint 的参考架构" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## 护栏

* [[!UICONTROL 实时客户个人资料]数据的护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)

## 相关文档

* [Adobe Experience Platform Activation产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-experience-platform0.html)
* [[!UICONTROL 实时客户个人资料]文档](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=zh-Hans)
* [轮廓护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* [配置文件查找API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
