---
title: Journey Optimizer - 第三方消息传递 blueprint
description: 演示如何将 Adobe Journey Optimizer 与第三方消息传递系统结合使用来编排和发送个性化通信。
solution: Journey Optimizer
exl-id: 3a14fc06-6d9c-4cd8-bc5c-f38e253d53ce
source-git-commit: 5110ee2a7a079945475055cbcfdabf7cdcaa0ab5
workflow-type: ht
source-wordcount: '823'
ht-degree: 100%

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

其他 Journey Optimizer 护栏：

* 现在可通过 API 设置封顶，以确保目标系统不会因饱和而达到故障点。这意味着超过上限的消息会被彻底丢弃，永不发送。不支持限流。
   * 最大连接数：目标可处理的 http/s 连接的最大数
   * 最大调用数：periodInMs 参数中要进行的最大调用数
   * periodInMs：时间（以毫秒为单位）
* 区段成员资格发起的历程可以两种模式运行：
   * 批次区段（每 24 小时刷新一次）
   * 流传输区段（&lt;5 分钟资格）
* 批次区段 - 需要确保您了解合格用户的每日流量，并确保目标系统能够处理每个历程以及所有历程中的突发吞吐量
* 流式区段 - 需要确保可以处理用户档案资格的初始突发量，以及每个历程和所有历程的每日合格流传输流量
* 不支持的决策管理
* 到第三方系统的出站集成
   * 不支持单个静态 IP，因为我们的基础架构是多租户的（必须允许列出所有数据中心 IP）
   * 自定义操作仅支持 POST 和 PUT 方法
   * 身份验证支持：令牌 | 密码 | OAuth2
* 无法打包 Adobe Experience Platform 或 Journey Optimizer 的各个组件，并在各个沙盒之间移动它们。必须在新环境中重新实施

<br>

第三方消息传递系统

* 需要了解系统可支持哪些负载进行事务 API 调用
   * 每秒允许的调用数
   * 连接数
* 需要了解进行 API 调用所需的身份验证
   * 身份验证类型：令牌 | 密码 | 通过 Journey Optimizer 支持 OAuth2
   * 身份验证缓存持续时间：令牌有效时间有多长？
* 如果仅支持批次摄入，则需要流传输到云存储引擎，如 Amazon Kinesis 或 Azure Event Grid 1st
   * 这些云存储引擎的数据可以经过批处理并传输到第三方
   * 客户或第三方将负责提供所需的任何中间件

<br>

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
   * 身份       （边缘网络）
   * 移动核心
1. 确保您拥有专用数据流，用于移动应用程序部署与 Web 部署
1. 有关更多信息，请参阅 [Adobe Journey Optimizer 移动指南](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

<br>

## 相关文档

* [Experience Platform 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Experience Platform 标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
* [Journey Optimizer 文档](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hans)
* [Journey Optimizer 产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)
