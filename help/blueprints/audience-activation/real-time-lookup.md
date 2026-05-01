---
title: 适用于Web和移动Personalization的实时Edge配置文件访问
description: 在边缘位置[!UICONTROL 实时客户个人资料]访问，以提供实时Web和移动个性化的上下文。
solution: Real-Time Customer Data Platform, Data Collection
kt: 719
exl-id: 61b81d00-c4bd-41b2-8161-683814947b56
TQID: https://experienceleague.adobe.com/H59c3UBbNCQFs3H0VL5iVDKKZ5D3CFt4ri2RVwNlq7s
product_v2: id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2: id: ba929a52-9339-4154-9487-317dc875a3c7
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: c4147b6e-073b-4d3c-9ab1-d60f2f4434efid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: d3cdead0-685a-4489-9250-4bb709942f66id: e0eb8757-182f-49f3-94a4-1587d16f5094id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 631
ht-degree: 8%

---

# 适用于Web和移动Personalization的实时Edge配置文件访问

>[!TIP]
>此Blueprint还作为Personalization下的[用例模式](/help/blueprints/use-case-patterns/personalization/edge-profile-access.md)提供。

适用于Web和移动Personalization蓝图的实时Edge配置文件访问显示了Web和移动应用程序如何访问Adobe Experience Platform边缘的[!UICONTROL 实时客户配置文件]，以实现高吞吐量、低延迟的个性化。

应用程序可在边缘以毫秒延迟访问实时配置文件属性和受众。 作为属性存储在配置文件中的属性、受众成员资格和模型驱动功能可以跨Web和移动渠道实时访问以进行同一页面和下一页面个性化。

利用此功能，您可以根据实时客户档案在网站和移动应用程序上提供高度个性化的体验，包括从实时行为派生的受众、引入实时客户档案的属性以及计算的见解。

>[!NOTE]
>
>Edge配置文件访问专为高吞吐量、低延迟用例而设计，例如Web/移动入站个性化和实时Offer Decisioning。 对于吞吐量较低的情况（如代理辅助支持或销售交互），中心配置文件查找API更合适。 查看支持和销售方案的[实时配置文件访问Blueprint](customer-activity.md)，了解基于中心的配置文件访问。

## 应用程序

* Real-time Customer Data Platform
* Adobe Experience Platform数据收集（Web SDK/移动SDK）
* Edge Network服务器API

## 用例

* 在Web和移动渠道上实时个性化已知客户体验
* 基于实时配置文件属性和受众的同页和下一页个性化
* 基于客户个人资料的内容和选件个性化，包括实时行为数据、属性和计算的见解
* 与个性化引擎、内容管理系统和外部应用程序集成，用于实时决策
* 使用实时用户档案上下文进行测试和内容优化

## 架构图

<img src="assets/real-time-edge-lookup.svg" alt="适用于Web和移动Personalization的Edge配置文件访问参考架构" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## 护栏

* [[!UICONTROL 实时客户个人资料]数据的护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* [Edge Network护栏](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* Edge用户档案具有14天的生存时间(TTL)。 如果用户在Edge上未活动14天，Edge配置文件可能会过期，需要从中心提取，这可能会影响第一页个性化。
* Edge个性化支持对符合Edge分段标准的受众进行实时受众成员资格评估。 此外，通过相应的配置，还可在边缘位置获得来自中心的批量访问和流式访问受众。

## 相关文档

### 目标配置

* [自定义Personalization连接](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) — 主要实施指南
* [Personalization目标概述](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/overview)
* [激活受众以边缘个性化目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)
* [实时查找边缘上的配置文件属性](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-profile-lookup)

### SDK 文档

* [Experience Platform Web SDK文档](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)
* [Experience Platform Mobile SDK文档](https://developer.adobe.com/client-sdks/home/)
* [Edge Network服务器API文档](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hans)
* [Experience Platform标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
* [Web SDK中的命令响应](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html)

### 用户档案和分段文档

* [[!UICONTROL 实时客户个人资料]文档](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [轮廓护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)

### 教程

* [使用Real-Time CDP和Adobe Target进行下一次点击个性化](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html)
* [数据流配置](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html#)
