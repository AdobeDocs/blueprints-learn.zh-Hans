---
title: 支持和销售方案的实时配置文件访问
description: '[!UICONTROL 实时用户档案]查询可提供座席协助支持和销售的背景信息。'
solution: Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c
source-git-commit: 88a15765c0a998d49c19d9853ad0c44d6e3bfaa1
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 65%

---

# 支持和销售方案的实时配置文件访问

支持和销售方案的实时配置文件访问蓝图显示了外部应用程序如何访问Adobe Experience Platform的[!UICONTROL 实时客户配置文件]。

外部应用程序可以使用 API GET 请求来访问用户档案。然后，存储在用户档案中的属性、事件、区段成员和模型驱动功能就可以用于这些外部非 Adobe 应用程序。

利用此功能，您可以在客户呼叫您的呼叫中心时显示丰富的背景信息。例如，支持座席可以了解客户的存留期值、客户流失倾向或营销活动接触情况。销售座席还可以受益于更多的背景信息和有关客户的洞察。

>[!NOTE]
>
>中心上的配置文件查找不适用于高吞吐量、低延迟的用例，如Web/移动入站个性化。 中心上的配置文件查找适用于延迟较低的情形，如代理辅助支持或销售互动。 对于低延迟、高吞吐量场景（如Web/移动个性化或实时优惠决策），应利用Edge用户档案。 Edge配置文件允许通过Real-time Customer Data Platform的[自定义Personalization连接](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/personalization/custom-personalization)进行实时访问。

## 用例

* 为座席支持的交互（如支持和销售体验）提供更深入的消费者背景信息。通过对 Experience Platform 用户档案的查找，座席可以接收更多有关消费者的背景信息，例如最近购买、活动交互、倾向、受众成员，以及存储在实时客户档案中的其他属性和洞察。

## 架构

<img src="assets/customer_activity_hub.svg" alt="客户活动中心 Blueprint 的参考架构" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## 护栏

* [[!UICONTROL 实时客户档案]数据的护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)

## 实施步骤

1. 为要摄入的数据[创建架构。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&lang=zh-Hans)
1. 为要摄入的数据[创建数据集。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)
1. 在架构上[配置正确的身份和身份命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)，以确保摄入的数据可以拼接到统一的用户档案中。
1. [为用户档案启用架构和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。
1. [将数据摄入](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&lang=zh-Hans) Experience Platform。
1. [设置合并策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hans)。
1. 使用[实体API查找配置文件属性](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=zh-Hans)。

## 相关文档

* [Adobe Experience Platform Activation 激活产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-experience-platform0.html)
* [[!UICONTROL 实时客户档案]文档](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=zh-Hans)
* [用户档案护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* [用户档案查找 API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
