---
title: 联机/脱机Audience Activation蓝图
description: 线上/线下 Audience Activation。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: da21d1796eb9a2c9c0f087d82606874ca55bd4ea
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 74%

---

# 联机/脱机Audience Activation蓝图

将线下属性和事件（如线下订单、交易、CRM 或忠诚度数据）与线上行为结合使用，实现线上定位和个性化。

将受众激活到基于用户档案的已知目的地（如电子邮件提供商、社交网络和广告目的地）。

## 用例

* 受众定位，针对社交和广告目的地上的已知受众。
* 具有线上和线下属性的线上个性化。
* 激活已知渠道（如电子邮件和短信）的受众。

## 应用程序

* Adobe Experience Platform
* [!UICONTROL 实时客户数据平台]

## 架构

### 具有目标的联机/脱机Audience Activation

<img src="assets/online_offline_activation.svg" alt="联机/脱机Audience Activation蓝图的参考体系结构" style="border:1px solid #4a4a4a" />
<br>

### 使用Experience Cloud应用程序进行在线/离线Audience Activation

<img src="assets/activation+apps.svg" alt="使用Experience Cloud应用程序的联机/脱机Audience Activation蓝图的参考体系结构" style="border:1px solid #4a4a4a" />

## 护栏

请参阅“受众和用户档案激活概述”页上概述的护栏 — [ LINK](overview.md)

## 实施步骤

1. 在 Experience Platform 中配置架构和数据集。
1. 在架构上配置正确的身份和身份命名空间，以确保摄入的数据可以拼接到统一的用户档案中。
1. 为用户档案启用架构和数据集。
1. 将数据引入 Platform。
1. 设置[!UICONTROL 实时客户数据平台]在Experience Platform和Audience Manager之间共享区段，以便在Experience Platform中定义的受众共享给Audience Manager。
1. 在 Experience Platform 中创作区段，以批次或流方式评估。系统自动确定以批次还是流式评估区段。
1. 配置目的地，以共享用户档案属性和受众成员到所需目的地。

## 实施注意事项

* 要将用户档案数据共享到目的地，您需要在目的地有效负荷中包含目的地使用的特定身份值。对于目标目标，任何必需的标识都必须被引入平台，并配置为[!UICONTROL 实时客户用户档案]的标识。

* 对于从 Experience Platform 到 Audience Manager 共享受众的激活情况，[!UICONTROL 实时客户档案]中包含的所有身份都共享给 Audience Manager。当所需目的地身份包括在[!UICONTROL 实时客户档案]中时，或者在[!UICONTROL 实时客户档案]中的身份可以与在 Audience Manager 中链接的所需目的地身份相关时，可以通过 Audience Manager 目的地共享来自 Experience Platform 的受众。

## 相关文档

* [实时客户数据平台产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/real-time-customer-data-platform.html)
* [用户档案和细分指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* [分段文档](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans)
* [目的地文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hans)

## 相关视频和教程

* [实时客户数据平台概述](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hans)
* [[!UICONTROL 实时客户数据平台演示]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hans)
* [创建区段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hans)
