---
title: Web/移动Personalization概述 — Adobe Target和RTCDP
description: 将 Web 个性化与电子邮件和其他已知和匿名渠道的个性化同步。
landing-page-description: 将 Web 个性化与电子邮件和其他已知和匿名渠道的个性化同步。
short-description: 将 Web 个性化与电子邮件和其他已知和匿名渠道的个性化同步。
solution: Real-Time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 845655a275cdb6d4a9cd397ec7c3515cbf02d321
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 79%

---


# 具有已知客户数据Blueprint的Web/移动Personalization

## 用例

* 使用已知客户数据的线上个性化
* 登陆页优化
* 除线下数据（如交易、预订、CRM 和忠诚度数据）和模型洞察以外，还基于以前的产品/内容视图、产品/内容关联、环境属性和人口统计的个性化
* 使用 Adobe Target 在网站和移动设备应用程序上共享和定位 Real-time Customer Data Platform 中定义的受众。

## 应用程序

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager（可选）：添加第三方受众数据
* Adobe Analytics 或 Customer Journey Analytics（可选）：添加了根据历史客户和行为数据通过细粒度分段构建区段的功能

### 参考文档

* [用于 Real-time Customer Data Platform 的 Adobe Target 连接](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [Edge 数据流配置](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=zh-Hans)
* [与 Audience Manager 和其他 Experience Cloud 解决方案共享 Experience Platform 区段](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=zh-Hans)


## 集成模式

| 集成模式 | 功能 | 先决条件 |
|---|---|---|
| 将 Edge 上的实时区段评估从 Real-time Customer Data Platform 共享到 Target | <ul><li>在 Edge 上实时评估受众以进行同页或下一页个性化。</li><li>此外，任何以流式或批处理方式评估的区段也将投影到[!DNL Edge Network]，以包含在边缘区段评估和个性化中。</li></ul> | <ul><li>必须实施Web/Mobile SDK或[!DNL Edge Network]服务器API</li><li>必须在 Experience Edge 中配置数据流并启用 Target 和 Experience Platform 扩展。</li><li>必须在 Real-time Customer Data Platform 目标中配置 Target 目标。</li><li>与 Target 集成需要与 Experience Platform 实例具有相同的 IMS 组织。</li></ul> |
| 通过 Edge 方案将来自 Real-time Customer Data Platform 的流传输受众和批次受众共享到 Target | <ul><li>通过[!DNL Edge Network]共享从Real-time Customer Data Platform到Target的流受众和批量受众。 实时评估的受众需要Web SDK和[!DNL Edge Network]实施。</li></ul> | <ul><li>将流传输和批次 RTCDP 受众共享到 Target 时，不需要 Web/Mobile SDK 或边缘 API Target 实施，不过实现上述的实时边缘区段评估需要它。</li><li>如果使用 AT.js，则仅支持针对 ECID 身份命名空间的用户档案集成。</li><li>对于 Edge 上的自定义身份命名空间查找，需要部署 WebSDK/Edge API，并且必须在身份映射中将每个身份设置为身份。</li><li>必须在 Real-time Customer Data Platform 目标中配置 Target 目标，仅支持 RTCDP 中的默认生产沙盒。</li><li>与 Target 集成需要与 Experience Platform 实例具有相同的 IMS 组织。</li></ul> |
| 通过受众共享服务方案，将流传输和批次受众从 Real-time Customer Data Platform 共享到 Target 和 Audience Manager | <ul><li>当 Audience Manager 中需要通过第三方数据和受众进行额外扩充时，可以利用此集成模式。</li></ul> | <ul><li>将流传输受众和批次受众共享到 Target 时，不需要 Web/Mobile SDK，不过实现实时 Edge 区段评估需要它。</li><li>如果使用 AT.js，则仅支持针对 ECID 身份命名空间的用户档案集成。</li><li>对于 Edge 上的自定义身份命名空间查找，需要部署 WebSDK/Edge API，并且必须在身份映射中将每个身份设置为身份。</li><li>必须配置通过受众共享服务的受众映射。</li><li>与 Target 集成需要与 Experience Platform 实例具有相同的 IMS 组织。</li><li>只有默认生产沙盒中的受众支持受众共享核心服务。</li></ul> |

## 将流传输和批次受众实时共享到 Adobe Target

架构

<img src="assets/RTCDP+Target.svg" alt="线上/线下 Web 个性化 Blueprint 的参考架构" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

序列详细信息

<img src="assets/RTCDP+Target_flow.svg" alt="线上/线下 Web 个性化 Blueprint 的参考架构" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

概述架构

<img src="assets/personalization_with_apps.svg" alt="线上/线下 Web 个性化 Blueprint 的参考架构" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## 实施模式

通过多种实施方案支持已知客户个性化。

### 带有Web/Mobile SDK或[!DNL Edge Network] API的实施模式1 - [!DNL Edge Network]（推荐方法）

* 将[!DNL Edge Network]与Web/Mobile SDK结合使用。 实时 Edge 分段需要使用 Web/Mobile SDK 或 Edge API 实施方法。
* [有关基于SDK的Experience Platform，请参阅Web和移动SDK Blueprint](../../experience-platform/deployment/websdk.md)。
* 在 Mobile SDK 中使用 [Adobe Journey Optimizer - 决策扩展](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer-decisioning)必须安装在 Mobile SDK 中。
* [有关包含Edge配置文件的基于API的Adobe Target实现，请参阅 [!DNL Edge Network] 服务器API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hans)。

### 实施模式 2 - 特定于应用程序的 SDK

使用传统的特定于应用程序的 SDK（例如，AT.js 和 AppMeasurement.js）。使用此实施方案不支持实时 Edge 区段评估。但是，使用此实施方案支持从 Experience Platform 中心进行流传输和批次受众共享。

[请参阅Adobe Target连接器文档](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection)
[请参阅特定于应用程序的SDK Blueprint](../../experience-platform/deployment/appsdk.md)

## 实施注意事项

身份先决条件

* 在将[!DNL Edge Network]和Web SDK结合使用上述实施模式1时，可以利用任何主要身份。 首次登录个性化要求个性化请求集主标识与Real-time Customer Data Platform中配置文件的主标识匹配。

## 相关文档

### SDK 文档

* [Experience Platform Web SDK 文档](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hans)
* [Experience Platform 标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
* [Experience Cloud ID 服务文档](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=zh-Hans)

### 分段文档

* [Experience Platform 分段概述](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hans)
* [实时分段](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=zh-Hans)
* [流式分段](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans)
* [通过 Adobe Audience Manager 分享 Adobe Analytics 区段](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=zh-Hans)
* [合并策略配置](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=zh-Hans#create-a-merge-policy)

### 教程

* [使用 Real-Time CDP 和 Adobe Target 实现下一次点击的个性化](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=zh-Hans)

### 相关博客帖子

* [Adobe 宣布使用 Adobe Target 和 Real-time Customer Data Platform 实现的同页增强的个性化](https://blog.adobe.com/en/publish/2021/10/05/adobe-announces-same-page-enhanced-personalization-with-adobe-target-real-time-customer-data-platform)
* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Adobe Experience Platform's Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our "Customer Zero" Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
