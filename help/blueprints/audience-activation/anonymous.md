---
title: 匿名受众激活 Blueprint
description: 了解如何基于匿名和行为客户数据跨网络和广告渠道定位受众。该功能支持跨设备的个性化、一致的实时客户体验。
landing-page-description: 了解如何基于匿名和行为客户数据跨网络和广告渠道定位受众。
solution: Experience Platform, Audience Manager
kt: 7211
thumbnail: null
exl-id: f17599f1-2e75-4cbe-841a-9fd1dae71ada
source-git-commit: 64e7b61c1b4b1d600641fd3299a2b84154873cfb
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 41%

---

# 匿名受众激活 Blueprint

匿名受众激活是一种根据匿名设备和行为数据，通过Web、移动设备和广告渠道，定位和个性化受众的功能。

## 用例

* 在网站、移动设备应用程序或受支持的广告渠道上，对匿名数字受众进行定位和个性化。
* 根据已知设备和行为特征优化登陆页面和预验证体验。
* 利用Audience Manager的第三方数据网络进一步优化和扩展您的受众以进行定位。


## 应用程序

* Audience Manager
* Real-time Customer Data Platform  

利用Audience Manager和Real-time Customer Data Platform，可以提供现场和广告目标的匿名Audience Activation。 请注意，Real-time Customer Data Platform仅支持在 [目标文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en).

Microsoft Bing、Google DV360和TradeDesk是基于匿名设备定位的主要受支持Real-time Customer Data Platform广告目标。 除此之外，Real-time Customer Data Platform还支持在 [目标文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en) 如 [已知客户激活蓝图](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).

## 架构

<img src="assets/anonymous_activation.svg" alt="匿名受众激活 Blueprint 的参考架构" style="width:80%; border:1px solid #4a4a4a" />

<br>

## 实施步骤

1. [实施 Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=zh-Hans#implementation-integration-guides)
1. 将数据收集至 Audience Manager。
1. 配置要在区段定义中使用的信号和特征。
1. 在 Audience Manager 中创建区段。
1. 在 Audience Manager 中配置目的地以共享受众。

有关Real-time Customer Data Platform的实施步骤，请参阅 [已知客户激活蓝图](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).

## 相关文档

* [Audience Manager](https://experienceleague.adobe.com/docs/audience-manager.html?lang=zh-Hans)
* [Experience Cloud[!UICONTROL  受众]](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html?lang=zh-Hans)
* [将 Audience Manager 与 Target 集成](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html?lang=zh-Hans)
* [通过 Audience Manager 分享 Adobe Analytics 区段](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=zh-Hans)
* [已知的客户激活Blueprint](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).
* [Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
