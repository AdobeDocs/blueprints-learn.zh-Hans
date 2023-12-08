---
title: Adobe Commerce - RTCDP Blueprint
description: Adobe Experience Platform与Adobe Commerce集成，以创建客户的单一视图，并在数字店面和各个渠道上智能地个性化体验。
solution: Real-Time Customer Data Platform, Commerce
exl-id: e2fc5e1c-c865-4c24-9b82-861a34aba487
source-git-commit: 8a47b73065a5591673804301c61a73947346813c
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Adobe Commerce和RTCDP

此 [!DNL Data Connection] 扩展可帮助Adobe Commerce客户与Adobe Experience Platform无缝集成，以丰富客户配置文件并在数字店面和其他渠道中个性化体验。

## 已启用技术功能

* 店面数据（客户端，例如添加到购物车、购物车放弃等）收集和发送到任何Adobe Experience Cloud产品中。
* 任何Adobe Experience Cloud产品的后台订单状态
* 可以将后台历史订单发送到Adobe Experience Platform
* 在Adobe Commerce中共享和个性化RTCDP受众

## 先决条件

要使用 [!DNL Data Connection] 扩展上，您必须具备以下条件：

* Adobe Commerce 2.4.4或更高版本
* Adobe ID和组织ID
* Adobe Experience Platform/RTCDP
* [Adobe客户端数据层(ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). 需要ACDL才能收集店面事件数据。

## 载入步骤

### 从Adobe Commerce到Adobe Experience Platform的数据收集

* [安装](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/install.html) 该 [!DNL Data Connection] 扩展。
* [登录](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) Adobe ，并查看以确认您的组织ID。 组织ID是与您配置的Experience Cloud公司关联的ID。 此ID是由24个字符组成的字母数字字符串，其后跟（且必须包括）@AdobeOrg。
* [创建或更新](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/update-xdm.html) 您的XDM架构和特定于商务的字段组。
* [创建数据集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 基于您创建或更新的架构。 此数据集将包含您发送的商务数据。
* [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 并选择包含特定于Commerce的字段组的XDM架构。
* [连接到Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).
* [连接到Adobe Experience Platform](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/connect-data.html).

### 从Adobe Experience Platform连接到Commerce目标以进行受众共享

要连接到Adobe Commerce目标，请执行以下操作：

* 在 [Adobe Experience Platform界面](https://experience.adobe.com/platform/)，转到Destinations > Catalog 。
* 选择个性化。
* 选择要突出显示的Adobe Commerce目标，然后选择设置。
* 请按照 [目标配置教程](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/connect-destination.html).

## 开箱即用数据

* 店面（浏览器/应用程序）事件
* 后台活动
* 历史订单数据

有关支持的事件的完整列表，请参阅 [商务事件](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/event-forwarding/events.html)

## 架构

<img src="../commerce/assets/commerce_rtcdp.png" alt="Adobe Commerce RTCDP架构" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## 相关实施指南

| 指南 | 链接 |
|:----|:----|
| 平台连接器 | [Adobe CommerceExperience Platform连接器概述](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/overview.html) |
| 商务目标 | [RTCDP中的Adobe Commerce连接](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-commerce.html) |
| 边缘个性化 | [激活受众以边缘个性化目标](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html) | |
