---
title: 使用 Experience Cloud 应用程序的受众和用户档案激活 Blueprint
description: 在 Experience Platform 中管理用户档案和受众，并将其与 Experience Cloud 应用程序共享。
solution: Real-Time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services
kt: 7722
exl-id: f36014e8-170d-47e1-b4ec-10c0ea70612d
source-git-commit: ae7347be5095ca4a7f99f9371dd94d87097112b0
workflow-type: ht
source-wordcount: '896'
ht-degree: 100%

---

# 使用 Experience Cloud 应用程序的受众和用户档案激活 Blueprint

在 Experience Platform 中管理用户档案和受众，并将其与 Experience Cloud 应用程序共享。在 Experience Platform 中建立并共享丰富的客户区段和洞察，将其与 Experience Cloud 应用程序共享。

使用 Experience Cloud 应用程序的激活与[已知客户激活 Blueprint](known.md) 保持一致。

## 用例

* 基于 Experience Cloud 跨客户交互渠道进行个性化和定位。
* 在 Experience Platform 和 Experience Cloud 应用程序之间共享受众和用户档案数据。
* 通过包括线上行为数据和数据科学模型在内的多渠道数据得到丰富的洞察，以丰富 Experience Platform 中的实时客户档案，然后与 Experience Cloud 应用程序共享。

## 应用程序

* Adobe Experience Platform   
* [!UICONTROL Real-time Customer Data Platform]
* Experience Platform Activation
* Experience Cloud 应用程序
   * Adobe Audience Manager
   * Adobe Target
   * Adobe Campaign
   * Journey Optimizer
   * Marketo Engage
   * Adobe Commerce
   * Customer Journey Analytics

## 架构

请参阅 [Experience Platform 和应用程序架构的相关章节](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html?lang=zh-Hans)，以了解有关 Experience Platform 与 Experience Cloud 应用程序集成的其他架构图。

### 使用 Experience Cloud 应用程序的受众和用户档案激活

<img src="../experience-platform/assets/aep+apps.svg" alt="使用 Experience Cloud 应用程序的受众和用户档案激活的参考架构" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />
<br>

## 护栏

请参阅[“受众和用户档案激活概述”页上的护栏](overview.md)  和[部署护栏](../experience-platform/deployment/guardrails.md)页面。

## 实施注意事项

* 要将用户档案数据共享到目的地，您需要在目的地有效负荷中包含目的地使用的特定身份值。任何目标目的地必需的身份都必须被摄入 Platform，并配置为[!UICONTROL 实时客户档案]的身份。

### 从 Real-time Customer Data Platform 共享受众到 Audience Manager

* 有关更多详细信息，请参阅以下文档。[与 Audience Manager 和其他 Experience Cloud 解决方案共享 Experience Platform 区段](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=zh-Hans).

* 无论是在批处理中还是流传输中发生的区段评估，一旦区段评估完成并写入实时客户档案，RT-CDP 中的受众成员资格就会以流传输方式共享到 Audience Manager。
* 如果符合条件的用户档案包含相关用户档案设备的区域路由信息，则 RTCDP 的受众成员资格将在关联的 Audience Manager Edge 上以流传输方式判断资格。如果将区域路由信息应用于具有过去 14 天内时间戳的用户档案，则会在流传输中在 Audience Manager Edge 上对其进行评估。如果 RTCDP 中的用户档案不包含区域路由信息或区域路由信息超过 14 天，则 RTCDP 受众成员资格会发送到 Audience Manager 中心位置，以进行批量评估和激活。
* 凭借区域路由信息，这些用户档案符合边缘激活资格，并将在 RTCDP 区段资格审核后的几分钟内激活，不符合边缘激活资格的用户档案将在 Audience Manager 中心判断资格，并且处理时间可能在 12-24 小时。
* 对于存储 Audience Manager 用户档案的 Edge 的区域路由信息，可从 Audience Manager、访客 ID 服务、Analytics、Launch 或直接从 Web SDK，使用“数据捕获区域信息”XDM 字段组以单独用户档案记录类数据集的形式收集到 Experience Platform。有关更多详细信息，请参阅获取区域信息文档[链接](https://experienceleague.adobe.com/docs/id-service/using/reference/regions.html?lang=zh-Hans)。
* 对于从 Experience Platform 共享受众到 Audience Manager 的激活方案，会自动共享以下身份：ECID、IDFA、GAID、散列电子邮件地址 (EMAIL_LC_SHA256)、AdCloud ID。当前，不共享客户命名空间。
* 当所需目的地身份包括在[!UICONTROL 实时客户档案]中时，或者在[!UICONTROL 实时客户档案]中的身份可以与在 Audience Manager 中链接的所需目的地身份相关时，可以通过 Audience Manager 目的地共享来自 Experience Platform 的受众。

### 从 Real-time Customer Data Platform 共享受众到 Target

* 请参阅[已知客户个性化 - Target 和 RTCDP Blueprint](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/known-personalization.html?lang=zh-Hans)，以了解有关将用户档案和受众从 Real-time Customer Data Platform 共享到 Target 的更多详细信息。

### 从 Real-time Customer Data Platform 共享受众到 Campaign 和 Journey Optimizer

* 请参阅[客户历程 Blueprint](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=zh-Hans)，以了解有关将用户档案和受众从 Real-time Customer Data Platform 共享到 Campaign 和 Journey Optimizer 的更多详细信息。

### 从 Real-time Customer Data Platform 共享受众到 Marketo Engage

* 请参阅 [B2B 激活 Blueprint](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=zh-Hans)，以了解有关将用户档案和受众从 Real-time Customer Data Platform 共享到 Marketo Engage 的其他详细信息。

### 从 Real-time Customer Data Platform 共享受众到 Customer Journey Analytics

* 请参阅[与 Customer Journey Analytics 共享 RTCDP 受众](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/ingest-aep-segments.html?lang=zh-Hans)，以了解有关将 Real-time Customer Data Platform 受众共享到 Customer Journey Analytics 的其他详细信息。

## 相关文档

* [[!UICONTROL Real-time Customer Data Platform]产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/real-time-customer-data-platform.html)
* [用户档案和分段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* [分段文档](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans)
* [目的地文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hans)

## 相关视频和教程

* [[!UICONTROL Real-time Customer Data Platform] 概述](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hans)
* [[!UICONTROL Real-time Customer Data Platform] 演示](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hans)
* [创建区段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hans)
