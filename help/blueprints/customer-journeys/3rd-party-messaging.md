---
title: Journey Optimizer - 第三方消息传递 blueprint
description: 演示如何将 Adobe Journey Optimizer 与第三方消息传递系统结合使用来编排和发送个性化通信。
solution: Journey Optimizer
exl-id: 3a14fc06-6d9c-4cd8-bc5c-f38e253d53ce
source-git-commit: 60a7785ea0ec4ee83fd9a1e843f0b84fc4cb1150
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 97%

---

# 第三方消息传递 blueprint

演示如何将 Adobe Journey Optimizer 与第三方消息传递系统结合使用来编排和发送个性化通信。

<br>

## 架构

<img src="assets/3rd-party-messaging-architecture.svg" alt="参考架构 Journey Optimizer Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 先决条件

Adobe Experience Platform

* 必须在系统中配置架构和数据集，然后才能配置 Journey Optimizer 数据源
* 对于基于体验事件类的架构，当您希望触发的事件不是基于规则的事件时，请添加“编排事件 ID 字段组”
* 对于基于个人用户档案类的架构，添加“用户档案测试详细信息”字段组，以便能够加载测试用户档案以与 Journey Optimizer 一起使用

第三方消息传递应用程序

* 必须支持 REST API 调用以发送事务负载

<br>

## 护栏

[Journey Optimizer 护栏产品链接](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=zh-Hans)

[护栏和端到端延迟指导](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)


## 实施步骤

### Adobe Experience Platform  

#### 架构/数据集

1. 根据客户提供的数据在 Experience Platform 中[配置单个用户档案、体验事件和多实体模式。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=zh-Hans)
1. 为要摄入的数据在 Experience Platform 中[创建数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)。
1. 在 Experience Platform 中为数据集[添加数据使用标签](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hans)以便进行治理。
1. [创建对目标实施治理的策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hans)。

#### 用户档案/身份

1. [创建任何客户特定的命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)。
1. [向模式添加身份](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)。
1. [为用户档案启用架构和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。
1. 为[!UICONTROL 实时客户档案]的不同视图[设置合并策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hans)（可选）。
1. 创建区段以用于 Journey。

#### 源/目标

1. 使用流传输 API 和源连接器[将数据摄入 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans)

### Journey Optimizer

1. 配置 Experience Platform 数据源并确定哪些字段应作为用户档案的一部分缓存。必须先在 Journey Optimizer 中配置用于启动客户历程的流数据，才能获取编排 ID。然后，此编排 ID 将被提供给开发人员以在摄入时使用。
1. 配置外部数据源
1. 为第三方应用程序配置自定义操作

### 移动推送配置（可选，因为第三方可能会收集令牌）

1. 实施 Experience Platform Mobile SDK 以收集推送令牌和登录信息，从而关联回已知的客户用户档案
1. 利用 Adobe 标记并创建具有以下扩展的移动资产：
   * Adobe Journey Optimizer
   * Adobe Experience Platform Edge 网络
   * 以下对象的身份 [!DNL Edge Network]
   * 移动核心
1. 确保您拥有专用数据流，用于移动应用程序部署与 Web 部署
1. 有关更多信息，请参阅 [Adobe Journey Optimizer 移动指南](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer/)

<br>

## 相关文档

* [Experience Platform 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Experience Platform 标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
* [Journey Optimizer 文档](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hans)
* [Journey Optimizer 产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)
