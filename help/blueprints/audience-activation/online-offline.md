---
title: 使用线上和线下数据激活 Blueprint
description: 线上/线下受众激活。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
source-git-commit: 53ef83cbaa9dde0793e379c0044f449cfca078ab
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 79%

---

# 使用线上和线下数据激活 Blueprint

将线下属性和事件（如线下订单、交易、CRM 或忠诚度数据）与线上行为结合使用，实现线上定位和个性化。

将受众激活到基于用户档案的已知目的地（如电子邮件提供商、社交网络和广告目的地）。

[使用 Experience Cloud 应用程序的受众和用户档案激活 Blueprint](platform-and-applications.md) 中提供了更多详细信息，该 Blueprint 特定于 Experience Platform 和 Experience Cloud 应用程序之间的集成。

## 用例

* 受众定位，针对社交和广告目的地上的已知受众。
* 具有线上和线下属性的线上个性化。
* 激活已知渠道（如电子邮件和短信）的受众。

## 应用程序

* Adobe Experience Platform    
* [!UICONTROL Real-time Customer Data Platform]

## 架构

### 使用线上和线下数据以及目的地激活

<img src="assets/online_offline_activation.svg" alt="线上/线下受众激活 Blueprint 的参考架构" style="width:80%; border:1px solid #4a4a4a" />
<br>

## 护栏

[请参阅“受众和用户档案激活概述”页上的护栏概述。](overview.md)

## 实施步骤

1. 为要摄入的数据[创建架构。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 为要摄入的数据[创建数据集。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)
1. 在架构上[配置正确的身份和身份命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)，以确保摄入的数据可以拼接到统一的用户档案中。
1. [为用户档案启用架构和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。
1. [将数据摄入](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans) Experience Platform。
1. 在 Experience Platform 和 Audience Manager 之间[设置 [!UICONTROL Real-time Customer Data Platform] 区段共享](https://www.adobe.com/go/audiences)，以便将 Experience Platform 中定义的受众共享给 Audience Manager。
1. 在 Experience Platform 中[创建区段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hans)。系统自动确定以批次还是流式评估区段。
1. [配置目的地](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=zh-Hans)，以共享用户档案属性和受众成员资格到所需目的地。

## 实施注意事项

* 要将用户档案数据共享到目的地，您需要在目的地有效负荷中包含目的地使用的特定身份值。任何目标目的地必需的身份都必须被摄入 Platform，并配置为[!UICONTROL 实时客户档案]的身份。

### 从 Real-time Customer Data Platform 共享受众到 Audience Manager

* 无论是在批处理中还是流传输中发生的区段评估，一旦区段评估完成并写入实时客户档案，RT-CDP 中的受众成员资格就会以流传输方式共享到 Audience Manager。如果符合条件的用户档案包含相关用户档案设备的区域路由信息，则 RTCDP 的受众成员资格将在关联的 Audience Manager Edge 上以流传输方式判断资格。如果将区域路由信息应用于过去14天内具有时间戳的用户档案，则会在流Audience Manager边缘中评估该信息。 如果RTCDP中的用户档案不包含区域路由信息或区域路由信息大于14天，则会将用户档案成员资格发送到Audience Manager中心位置，以便进行批量评估和激活。 符合边缘激活资格的配置文件将在RTCDP区段鉴别后的几分钟内激活，不符合边缘激活资格的配置文件将在Audience Manager中心获得资格，并且可能有12-24小时的处理时间。

* 可以收集存储了Audience Manager配置文件的Edge的区域路由信息，以便从Audience Manager、访客ID服务、Analytics、Launch或直接从Web SDK作为单独的配置文件记录类数据集，并使用“数据捕获区域信息”XDM字段组进行Experience Platform。

* 对于从 Experience Platform 共享受众到 Audience Manager 的激活方案，会自动共享以下身份：IDFA、GAID、AdCloud、Google、ECID、EMAIL_LC_SHA256。当前，不共享客户命名空间。

当所需目的地身份包括在[!UICONTROL 实时客户档案]中时，或者在[!UICONTROL 实时客户档案]中的身份可以与在 Audience Manager 中链接的所需目的地身份相关时，可以通过 Audience Manager 目的地共享来自 Experience Platform 的受众。

## 相关文档

* [[!UICONTROL Real-time Customer Data Platform] 产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/real-time-customer-data-platform.html)
* [用户档案和分段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* [分段文档](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans)
* [目的地文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hans)

## 相关视频和教程

* [[!UICONTROL Real-time Customer Data Platform] 概述](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hans)
* [[!UICONTROL Real-time Customer Data Platform] 演示](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hans)
* [创建区段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
