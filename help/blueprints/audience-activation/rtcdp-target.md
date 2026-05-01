---
title: 已知客户Personalization与Target
description: 将 RTCDP 轮廓和受众与 Adobe Target 集成。
landing-page-description: 将 RTCDP 轮廓和受众与 Adobe Target 集成。
short-description: 将 RTCDP 轮廓和受众与 Adobe Target 集成。
solution: Real-Time Customer Data Platform, Target, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
TQID: https://experienceleague.adobe.com/1ti2SqfAFOgnKbaJ70xwGI-xHDE1WXJ7-oTStcJJy1E
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2:
  - id: a37e4ecd-c740-426a-addf-cb1b483c5c5a
  - id: adee20bd-51f4-461d-b9db-d215f8756eeb
  - id: ba929a52-9339-4154-9487-317dc875a3c7
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
subfeature_v2:
  - id: cbd4a8d8-97a6-4ac9-b8d6-b6c1f28d3342
  - id: cdd3e38b-fec2-4f39-8b10-83ddaab1ac16
  - id: d1823595-9241-4128-8a33-e4ac3bf08773
  - id: ee602049-8a18-43df-9299-a689a025a371
  - id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 735
ht-degree: 37%

---

# 已知客户Personalization与Target

>[!TIP]
>此Blueprint还作为Personalization下的[用例模式](/help/blueprints/use-case-patterns/personalization/audience-sharing-with-target.md)提供。

## 用例

* 使用已知客户数据的线上个性化
* 登陆页优化
* 除线下数据（如交易、预订、CRM 和忠诚度数据）和模型洞察以外，还基于以前的产品/内容视图、产品/内容关联、环境属性和人口统计的个性化
* 使用Adobe Target在网站和移动应用程序上共享和定位在Real-time Customer Data Platform中定义的受众

## 应用程序

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target

### 参考文档

* [实时客户数据平台的Adobe Target连接](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [Edge数据流配置](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=zh-Hans)

## 集成模式

| 集成模式 | 功能 | 先决条件 |
|--------------------|------------|---------------|
| **对从Real-time Customer Data Platform共享到Target的Edge进行实时区段评估** |  — 在Edge上实时评估受众以个性化同一页面或下一页面。 <br> — 以流式或批处理方式评估的任何区段也将投影到Edge Network，以包含在边缘区段评估和个性化中。 |  — 必须实施Web/Mobile SDK或Edge Network服务器API。 <br> — 必须在Experience Edge中配置启用了Target和Experience Platform扩展的数据流。 <br> — 必须在Real-time Customer Data Platform目标中配置目标目标。 <br>- 与 Target 集成需要与 Experience Platform 实例具有相同的 IMS 组织。 |
| **通过Edge方法从Real-time Customer Data Platform流式传输和批量共享受众到Target** | - 通过 Edge 网络将来自 Real-time Customer Data Platform 的流传输受众和批次受众共享到 Target。 <br> — 实时评估的受众需要Web SDK和Edge Network实施。 |  — 将流和批量RTCDP受众共享到Target不需要Target的Web/Mobile SDK或Edge API实施，但需要启用实时边缘区段评估。 <br>- 如果使用 AT.js，则仅支持针对 ECID 身份命名空间的用户档案集成。 <br> — 对于Edge上的自定义身份命名空间查找，需要Web SDK/Edge API部署，并且必须在身份映射中将每个身份设置为身份。 <br> — 必须在Real-time Customer Data Platform目标中配置目标目标，仅支持RTCDP中的默认生产沙盒。 <br>- 与 Target 集成需要与 Experience Platform 实例具有相同的 IMS 组织。 |
| **通过受众共享服务方法从Real-time Customer Data Platform流式传输和批量共享受众到Target和Audience Manager** |  — 当需要从Audience Manager中的第三方数据和受众进行额外扩充时，可以利用此集成模式。 |  — 将流式受众和批量受众共享到Target不需要Web/Mobile SDK，但是要启用实时边缘区段评估则需要Web/Mobile 。 <br>- 如果使用 AT.js，则仅支持针对 ECID 身份命名空间的用户档案集成。 <br> — 对于Edge上的自定义身份命名空间查找，需要Web SDK/Edge API部署，并且必须在身份映射中将每个身份设置为身份。 <br> — 必须配置通过受众共享服务的受众投影。 <br>- 与 Target 集成需要与 Experience Platform 实例具有相同的 IMS 组织。 <br> — 仅默认生产沙盒中的受众支持受众共享核心服务。 |

## 将流传输和批次受众实时共享到 Adobe Target

架构

![在线/离线Web Personalization Blueprint的参考架构](assets/RTCDP+Target.svg)

序列详细信息

![在线/离线Web Personalization Blueprint的参考架构](assets/RTCDP+Target_flow.svg)

概述架构

![在线/离线Web Personalization Blueprint的参考架构](assets/personalization_with_apps.svg)

## 相关文档

### SDK 文档

* [Experience Platform Web SDK文档](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hans)
* [Experience Platform标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
* [Experience Cloud ID服务文档](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=zh-Hans)

### 分段文档

* [Experience Platform分段概述](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hans)
* [实时分段](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=zh-Hans)
* [流式客户细分](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans)
* [通过Adobe Audience Manager共享Adobe Analytics区段](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=zh-Hans)
* [合并策略配置](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=zh-Hans#create-a-merge-policy)

### 教程

* [使用Real-Time CDP和Adobe Target进行下一次点击个性化](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=zh-Hans)
