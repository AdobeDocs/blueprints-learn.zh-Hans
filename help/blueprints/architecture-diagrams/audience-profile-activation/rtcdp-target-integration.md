---
title: Adobe Real-Time CDP与Adobe Target集成
description: 了解Real-Time Customer Data Platform受众和配置文件上下文如何通过Edge Network与Adobe Target集成。
landing-page-description: 了解Real-Time Customer Data Platform受众和配置文件上下文如何通过Edge Network与Adobe Target集成。
short-description: 了解Real-Time Customer Data Platform受众和配置文件上下文如何通过Edge Network与Adobe Target集成。
solution: Real-Time Customer Data Platform, Target, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
TQID: https://experienceleague.adobe.com/1ti2SqfAFOgnKbaJ70xwGI-xHDE1WXJ7-oTStcJJy1E
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
feature_v2:
  - id: a37e4ecd-c740-426a-addf-cb1b483c5c5a
    internal-label: Segmentation
  - id: adee20bd-51f4-461d-b9db-d215f8756eeb
    internal-label: Audiences
  - id: ba929a52-9339-4154-9487-317dc875a3c7
    internal-label: Use cases
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
subfeature_v2:
  - id: cbd4a8d8-97a6-4ac9-b8d6-b6c1f28d3342
    internal-label: Segments
  - id: cdd3e38b-fec2-4f39-8b10-83ddaab1ac16
    internal-label: B2B
  - id: d1823595-9241-4128-8a33-e4ac3bf08773
    internal-label: Audiences
  - id: ee602049-8a18-43df-9299-a689a025a371
    internal-label: Use cases
  - id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
    internal-label: at.js
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 17%
---
# Adobe Real-Time CDP与Adobe Target集成

此架构显示如何通过Edge Network集成[!DNL Real-Time Customer Data Platform]和[!DNL Adobe Target]。 它可帮助您在边缘的实时受众评估与使用Target共享流受众或批量受众之间进行选择。

## 应用程序

* [!DNL Real-Time Customer Data Platform]
* [!DNL Adobe Target]
* [!DNL Experience Platform] Edge Network
* Experience Platform Web SDK或Edge Network服务器API

## 选择集成方法

### 边缘的实时受众评估

当[!DNL Adobe Target]需要边缘评估的受众和配置文件属性来实现同一页面或下一页面个性化时，请使用此方法。 实施Web SDK或Edge Network Server API并配置启用[!DNL Adobe Target]和[!DNL Experience Platform]服务的数据流。

### 将流和批量受众共享到Target

当在[!DNL Real-Time Customer Data Platform]中评估的受众需要在[!DNL Adobe Target]中可用而没有实时边缘评估时，使用此方法。 在默认生产沙盒中配置[!DNL Adobe Target]目标。 仅实时边缘评估或自定义身份命名空间查找需要Web SDK或Edge Network服务器API实施。

## 架构图

此图显示了数据收集、Edge Network、[!DNL Real-Time Customer Data Platform]和[!DNL Adobe Target]之间的主要集成点。

![Real-Time Customer Data Platform与Adobe Target集成的架构](assets/real_time_cdp_target.png){zoomable="yes"}

## 数据流图

此序列显示客户端请求如何到达Edge Network、评估受众和配置文件上下文、向[!DNL Adobe Target]发送个性化请求并将生成的体验返回给客户端。

用于Real-Time Customer Data Platform与Adobe Target集成的![数据流](assets/real_time_cdp_target_data_flow_detail.png){zoomable="yes"}

## 实施注意事项

* [!DNL Adobe Target]和[!DNL Real-Time Customer Data Platform]必须使用相同的IMS组织。
* [!DNL Adobe Target]目标支持[!DNL Real-Time Customer Data Platform]中的默认生产沙盒。
* 对于边缘位置的自定义身份命名空间查找，请使用Web SDK或Edge Network服务器API，并在身份映射中包含每个身份。
* 如果使用at.js，则配置文件集成仅支持ECID身份命名空间。

## 相关文档

### 配置集成

* [实时客户数据平台的Adobe Target连接](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=zh-Hans)
* [Edge数据流配置](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=zh-Hans)

### 在边缘实施

* [Experience Platform Web SDK文档](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hans)
* [Experience Platform标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
* [Experience Cloud ID服务文档](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=zh-Hans)

### 评估受众

* [Experience Platform分段概述](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hans)
* [实时分段](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=zh-Hans)
* [流式客户细分](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans)
* [合并策略配置](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=zh-Hans#create-a-merge-policy)
