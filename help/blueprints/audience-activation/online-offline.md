---
title: 线上/线下受众激活 Blueprint
description: 线上/线下受众激活。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 2fc1adc04a9ca2184c88970d5ba0785957327f68
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 74%

---

# 线上/线下受众激活 Blueprint

将线下属性和事件（如线下订单、交易、CRM 或忠诚度数据）与线上行为结合使用，实现线上定位和个性化。

将受众激活到基于用户档案的已知目的地（如电子邮件提供商、社交网络和广告目的地）。

“联机/脱机Audience Activation蓝图”与“Experience Cloud应用程序蓝图”的[受众和用户档案激活紧密对齐。 ](platform-and-applications.md)在[受众和用户档案激活中，使用Experience Cloud Applications Blueprint](platform-and-applications.md)提供了更多详细信息   特定于Experience Platform和Experience Cloud应用程序之间的集成。

## 用例

* 受众定位，针对社交和广告目的地上的已知受众。
* 具有线上和线下属性的线上个性化。
* 激活已知渠道（如电子邮件和短信）的受众。

## 应用程序

* Adobe Experience Platform 
* [!UICONTROL 实时客户数据平台]

## 架构

### 具有目标的联机/脱机Audience Activation

<img src="assets/online_offline_activation.svg" alt="线上/线下受众激活 Blueprint 的参考架构" style="border:1px solid #4a4a4a" />
<br>

### 使用Experience Cloud应用程序进行在线/离线Audience Activation

<img src="assets/activation+apps.svg" alt="使用Experience Cloud应用程序的联机/脱机Audience Activation蓝图的参考体系结构" style="border:1px solid #4a4a4a" />

## 护栏

[请参阅“受众和用户档案激活概述”页上概述的护栏。](overview.md)

## 实施步骤

1. [为要摄入的数据创建架构。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html)
1. [为要摄入的数据创建数据集。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html)
1. [在架构上配置正确的身份和身份命名空间，以确保摄入的数据可以拼接到统一的用户档案中。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)
1. [为用户档案启用模式和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html)。
1. [将数据摄入 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
1. [设置在 Experience Platform 和 Audience Manager 之间共享[!UICONTROL 实时客户数据平台]区段，以便将 Experience Platform 中定义的受众共享给 Audience Manager。](https://www.adobe.com/go/audiences)
1. [在Experience Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hans) 中创建细分。系统自动确定以批次还是流式评估区段。
1. [配置目的地，以共享用户档案属性和受众成员资格到所需目的地。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html)

## 实施注意事项

* 要将用户档案数据共享到目的地，您需要在目的地有效负荷中包含目的地使用的特定身份值。任何目标目的地必需的身份都必须被摄入 Platform，并配置为[!UICONTROL 实时客户档案]的身份。

* 对于从 Experience Platform 到 Audience Manager 共享受众的激活情况，[!UICONTROL 实时客户档案]中包含的所有身份都共享给 Audience Manager。当所需目的地身份包括在[!UICONTROL 实时客户档案]中时，或者在[!UICONTROL 实时客户档案]中的身份可以与在 Audience Manager 中链接的所需目的地身份相关时，可以通过 Audience Manager 目的地共享来自 Experience Platform 的受众。

## 相关文档

* [[!UICONTROL 实时客户数据平台]产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/real-time-customer-data-platform.html)
* [用户档案和分段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* [分段文档](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans)
* [目的地文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hans)

## 相关视频和教程

* [[!UICONTROL 实时客户数据平台]概述](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hans)
* [[!UICONTROL 实时客户数据平台]演示](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hans)
* [创建区段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
