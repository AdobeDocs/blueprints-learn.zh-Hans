---
title: 多沙盒事件转发数据收集 Blueprint
description: 使用事件转发将 [!DNL Experience Platform]  (AEP) SDK收集的数据流式传输到多个沙盒
solution: Data Collection
kt: 7202
exl-id: c24a47fe-b3da-4170-9416-74d2b6a18f32
source-git-commit: 72eb4e2ff276279a2fc88ead0b17d77cc8e99b97
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 60%

---

# 多沙盒事件转发数据收集Blueprint

多沙盒事件转发数据收集Blueprint显示了如何将使用Adobe[!DNL Experience Platform] Web和Mobile SDK收集的数据配置为收集单个事件并转发到多个[!DNL Experience Platform] (AEP)沙盒。 此 Blueprint 是使用“Adobe 标记”的事件转发功能的特定用例。

除了使用事件转发功能复制事件之外，您还可以添加、过滤或处理原始收集的数据，以满足其他沙箱的要求。例如，沙盒 A 需要接收所有事件数据元素，而沙盒 B 只应接收非 PII 数据。

事件转发使用单独的标记属性，该属性包含满足您的数据要求所需的数据元素、规则和扩展。 对于传入的事件，您的事件转发属性可以在转发之前收集数据并根据需要进行管理。

您的目标沙盒需要配置HTTP流端点，以供事件转发HTTPS扩展使用。

## 用例

* 全局数据报告 - 使用多个沙箱来隔离操作环境，以及需要将数据收集整合到一个沙箱中时，用于跨沙盒报告。事件转发到报表沙盒允许每个沙盒操作环境在收集数据时将数据实时发送到报告沙盒
* 根据每个沙盒操作环境的不同数据规则，跨沙盒管理数据收集。需要过滤敏感数据（如医疗保健和金融服务）的此类操作环境

## 应用程序

* Adobe[!DNL Experience Platform]数据收集

## 架构

<img src="assets/multi-Sandbox-Data-Collection.svg" alt="多沙盒事件转发的参考架构" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

1. 标记作者既定义了标记属性，又定义了事件转发属性。在这里，作者定义了用于管理数据收集的数据元素、规则和操作。 请记住，标记属性代码在客户端上运行，并由 CDN 主机分发。[!UICONTROL 事件转发属性]代码在Adobe[!DNL Edge Server]上运行。

1. 在客户端上收集的数据将发送到[!DNL Edge Network]。 客户还可以选择首先将数据发送到自己的服务器，作为服务器端收集的一种方法。 Web SDK 可以提供服务器到服务器收集功能。但是，这确实需要不同的编程模型来实施。请参阅下面的文档&#x200B;**[!DNL Edge Network]服务器API概述**

1. 平台[!DNL Edge Network]接收数据收集负载，并协调到所需系统（如Target和Analytics）的数据流。

1. 事件转发属性数据元素用于访问到达有效负载的事件数据。在转发之前，还可以根据需要使用规则来处理事件数据。例如，将数据格式化为流传输数据摄入所需的 XDM

1. 事件转发提供了 HTTPS 扩展，该扩展允许将事件数据转发到 HTTPS 端点。

1. 沙盒 2 配置了接收转发事件的流传输端点。

## 相关文档

* [事件转发文档](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=zh-Hans)
* [事件转发视频](https://experienceleague.adobe.com/docs/launch-learn/tutorials/server-side/overview.html?lang=zh-Hans)
* Web SDK 教程的[事件转发课程](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/event-forwarding/setup-event-forwarding.html?lang=zh-Hans)
* [[!DNL Experience Platform] Web SDK概述](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hans)
* [[!DNL Edge Network] 服务器API概述](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hans)

## 相关博客帖子

* [使用Adobe [!DNL Experience Platform] Web SDK和 [!DNL Edge Network]](https://medium.com/adobetech/boosting-website-performance-with-adobe-experience-platform-web-sdk-and-edge-network-329fcf70fdf9)提升网站性能
* [使用Adobe [!DNL Experience Platform] Web SDK和 [!DNL Edge Network]](https://medium.com/adobetech/solving-implementation-pain-points-with-adobe-experience-platform-web-sdk-and-edge-network-880b635e6819)解决实现难点
* 用于Adobe管理的[受众 [!DNL Experience Platform] Web SDK](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [Adobe [!DNL Experience Platform] Web SDK - Adobe Target](https://medium.com/adobetech/adobe-experience-platform-web-sdk-adobe-target-9b9f621d271)
* Adobe Analytics的[Adobe [!DNL Experience Platform] Web SDK迁移方案](https://medium.com/adobetech/adobe-experience-platform-web-sdk-migration-scenarios-for-adobe-analytics-91c255ec82b0)
* [将您的Adobe [!DNL Experience Platform] 服务与Adobe [!DNL Experience Platform] Web SDK](https://medium.com/adobetech/unify-your-adobe-experience-platform-services-with-adobe-experience-platform-web-sdk-75cf6851a9fc)统一起来
* 使用Adobe [!DNL Experience Platform] Mobile SDK和Launch[加速您的移动应用程序开发](https://medium.com/adobetech/accelerate-your-mobile-application-development-with-adobe-experience-platform-mobile-sdk-and-launch-ed023536d611)
* [使用 Adobe Experience Platform Web SDK 简化客户工作流程](https://medium.com/adobetech/simplifying-customer-workflows-with-adobe-experience-platform-web-sdk-4e54fe134f4a)
