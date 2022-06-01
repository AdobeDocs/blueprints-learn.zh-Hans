---
title: Journey Optimizer 与 Adobe Campaign Blueprint
description: 演示如何将 Adobe Journey Optimizer 与 Adobe Campaign 结合使用，通过 Campaign 中的实时消息传送服务器在本地发送消息
solution: Journey Optimizer, Campaign, Campaign v8, Campaign Classic v7, Campaign Standard
exl-id: 076446a9-dfb9-464c-a04f-6864b8cb7b48
source-git-commit: 37fa3bc00175a4636766564f0b8fb847fa8a951e
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 98%

---

# Journey Optimizer 与 Adobe Campaign

演示如何将 Adobe Journey Optimizer 与 Adobe Campaign 结合使用，通过 Campaign 中的实时消息传送服务器在本地发送消息。

<br>

## 架构

<img src="assets/ajo-campaign-architecture.svg" alt="参考架构 Journey Optimizer Blueprint" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>可以同时使用 Journey Optimizer 和 Campaign 来彼此独立地发送消息，但需要考虑一些技术注意事项。如果您希望遵循此路线，请与售前企业架构师沟通，以确保您了解支持实施所需的条件。

<br>

## 先决条件

### Adobe Experience Platform

* 必须在系统中配置架构和数据集，然后才能配置 Journey Optimizer 数据源
* 对于基于体验事件类的架构，当您希望触发的事件不是基于规则的事件时，请添加“编排事件 ID 字段组”
* 对于基于个人用户档案类的架构，添加“用户档案测试详细信息”字段组，以便能够加载测试用户档案以与 Journey Optimizer 一起使用
* Journey Optimizer 和 Campaign 配置在同一 IMS 组织中

### Campaign v7/v8 或 Campaign Standard

* 实时消息传送服务（即消息中心）的执行实例必须由 Adobe 托管云服务托管
* 所有消息创作均在 Campaign 实例本身内完成

<br>

## 护栏

[Journey Optimizer 护栏产品链接](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=zh-Hans)

### 其他 Journey Optimizer 护栏

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
* 不支持业务事件
* 出站集成到第三方系统
   * 不支持单个静态 IP，因为我们的基础架构是多租户的（必须允许列出所有数据中心 IP）
   * 自定义操作仅支持 POST 和 PUT 方法
   * 身份验证支持：令牌 |密码 | OAuth2
* 无法打包 Adobe Experience Platform 或 Journey Optimizer 的各个组件，并在各个沙箱之间移动它们。必须在新环境中重新实施

<br>

### Campaign (v7/v8)

* 消息中心的执行实例必须由 Adobe 托管云服务托管
* 需要 v7 版本 21.1 以上或 v8
* 消息传递吞吐量
   * AC (v7) 每小时 5 万
   * AC (v8) 多达每小时 100 万（基于软件包）
* AC (v7) 仅支持事件启动历程
   * 无启动了区段或区段成员资格的历程
   * 鉴于它可以发送到执行实例的数量，不支持基于读取受众和业务事件的历程
* AC(v7)或AC(v8)均不支持消息中的决策管理
* 对 Campaign 的出站 API 调用没有限流
* 事务性消息日志未本地同步到 AEP。需要咨询团队的精力。建议最多每 4 小时导出一次日志

<br>

### Campaign Standard

* 吞吐量支持 14 tps（每小时 5 万）
* 仅支持事件启动历程
   * 无启动了区段或区段成员资格的历程
   * 鉴于它可以发送到执行实例的数量，不支持基于读取受众和业务事件的历程
* 在发送到 Campaign Standard 的事务型消息中打开并单击活动时，将在 Journey Optimizer 历程画布中作为“重新操作事件”本地显示
* 事务性消息日志不会本地同步回 Experience Platform。需要咨询团队的精力。建议最多每 4 小时导出一次日志

<br>

## 实施步骤

### Adobe Experience Platform

#### 模式/数据集

1. 根据客户提供的数据在 Experience Platform 中[配置单个用户档案、体验事件和多实体模式。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 为 Adobe Campaign broadLog、trackingLog 和无法投放地址表创建基于体验事件类的架构（可选）。
1. 为要摄入的数据在 Experience Platform 中[创建数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)。
1. 在 Experience Platform 中为数据集[添加数据使用标签](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hans)以便进行治理。
1. [创建对目标实施治理的策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hans)。

#### 用户档案/身份

1. [创建任何客户特定的命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)。
1. [向模式添加身份](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [为用户档案启用架构和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。
1. 为[!UICONTROL 实时客户档案]的不同视图[设置合并策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hans)（可选）。
1. 创建区段以用于 Journey。

#### 源/目标

1. 使用流传输 API 和源连接器[将数据摄入 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans)

### Journey Optimizer

1. 配置 Experience Platform 数据源并确定哪些字段应作为用户档案的一部分缓存。必须先在 Journey Optimizer 中配置用于启动客户历程的流数据，才能获取编排 ID。然后，此编排 ID 将被提供给开发人员以在摄入时使用。
1. 配置外部数据源
1. 为 Campaign 实例配置自定义操作

### Campaign v7/v8 或 Campaign Standard

* 需要使用相应的个性化上下文配置消息模板
* 导出工作流需要配置为将事务性消息传递日志导出并发回 Experience Platform。建议最多每 4 小时运行一次

### 移动推送配置（可选）

1. 实施 Experience Platform Mobile SDK 以收集推送令牌和登录信息，从而关联回已知的客户用户档案
1. 利用 Adobe 标记并创建具有以下扩展的移动资产：
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Adobe Experience Platform Edge Network
   * 身份 （边缘网络）
   * 移动核心
1. 确保您拥有专用数据流，用于移动应用程序部署与 Web 部署
1. 有关更多信息，请参阅 [Adobe Journey Optimizer 移动指南](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

   >[!IMPORTANT]
   >如果希望通过 Journey Optimizer 发送实时通信，并通过 Campaign 发送批量推送通知，则可能需要在 Journey Optimizer 和 Campaign 中收集移动令牌。Campaign v8 要求专门使用 Campaign SDK 来捕获推送令牌。

<br>

## 相关文档

* [Experience Platform 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Experience Platform 标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
* [Journey Optimizer 文档](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hans)
* [Journey Optimizer 产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)
* [Campaign v8 文档](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=zh-Hans)
* [Campaign v7 文档](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hans)
* [Campaign Standard 文档](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hans)
