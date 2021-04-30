---
title: 受众和用户档案激活到企业目标Blueprint
description: 受众和用户档案激活到企业目标
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: 76fe52d8e83e075f9e7ce6e8596880181b01a7fd
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 39%

---

# 受众和用户档案激活到企业目标Blueprint

从[!UICONTROL 实时客户数据平台]共享用户档案和受众更改以及流式或批量事件到企业数据存储和应用程序。 这些用户档案和受众事件可用于向客户发起销售或支持行动，例如跟踪放弃的应用程序流程或网络研讨会注册，或使用[!UICONTROL 实时客户数据平台]的最新客户属性和智能更新企业应用程序。

## 用例

* 用户档案和受众激活到云存储目标，或用于企业跟踪、存储、分析和激活客户数据和洞察的流目标。

## 应用程序

* Adobe Experience Platform 激活

## 架构

<img src="assets/enterprise_destination_activation.svg" alt="企业激活方案的参考体系结构" style="border:1px solid #4a4a4a" />

## 护栏

请参阅“受众和用户档案激活概述”页上概述的护栏 — [ LINK](overview.md)

## 实施步骤

1. 为要摄取的数据创建模式。
1. 为要摄取的数据创建数据集。
1. 在架构上配置正确的身份和身份命名空间，以确保摄入的数据可以拼接到统一的用户档案中。
1. 启用模式和数据集以进行用户档案处理。
1. 配置任何数据获取源。
1. 在Experience Platform中创作区段，以批量或流形式进行评估。 系统自动确定以批次还是流式评估区段。
1. 配置目的地，以共享用户档案属性和受众成员到所需目的地。

## 相关文档

* [目的地文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hans)
* [云存储目标概述](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [HTTP目标](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [实时客户数据平台产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/real-time-customer-data-platform.html)
* [用户档案和细分指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* [分段文档](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans)

## 相关视频和教程

* [实时客户数据平台概述](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hans)
* [[!UICONTROL 实时客户数据平台演示]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hans)
* [创建区段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hans)
