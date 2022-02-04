---
title: Journey Optimizer与Adobe Campaign Blueprint
description: 演示如何将Adobe Journey Optimizer与Adobe Campaign结合使用，通过Campaign中的实时消息传送服务器本地发送消息
solution: Experience Platform, Journey Optimizer, Campaign v8, Campaign Classic v7, Campaign Standard
hidefromtoc: true
source-git-commit: a86df4a1b2de38bcb244a6afe1cea87adc7e26fa
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 25%

---

# Journey Optimizer与Adobe Campaign

演示如何将Adobe Journey Optimizer与Adobe Campaign结合使用，通过Campaign中的实时消息传送服务器本地发送消息。

<br>

## 架构

<img src="assets/ajo-campaign-architecture.svg" alt="参考架构Journey Optimizer Blueprint" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>可以同时使用Journey Optimizer和Campaign来彼此独立地发送消息，但有些技术考虑事项需要考虑。 如果您希望遵循此路线，请与售前企业架构师合作，确保您了解支持实施所需的内容。

<br>

## 先决条件

### Adobe Experience Platform

* 必须在系统中配置架构和数据集，然后才能配置Journey Optimizer数据源
* 对于基于体验事件类的架构，当您希望触发的事件不是基于规则的事件时，请添加“编排事件ID字段组”
* 对于基于个人用户档案类的架构，添加“用户档案测试详细信息”字段组，以便能够加载测试用户档案以与Journey Optimizer一起使用
* Journey Optimizer和Campaign在同一IMS组织中进行配置

### Campaign v7/v8或Campaign Standard

* 实时消息传送服务（即消息中心）的执行实例必须由Adobe管理的Cloud Services托管
* 所有消息创作均在Campaign实例本身内完成

<br>

## 护栏

[Journey Optimizer护栏产品链接](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=zh-Hans)

### 其他Journey Optimizer护栏

* 现在可通过API设置上限，以确保目标系统未饱和到故障点。 这意味着超过上限的消息将被完全丢弃，并且从不发送。 不支持限制。
   * 最大连接数 — 目标可处理的http/s连接数上限
   * 最大调用计数 — periodInMs参数中要发起的最大调用数
   * periodInMs — 时间（以毫秒为单位）
* 区段成员资格发起的历程可以两种模式运行：
   * 批量区段（每24小时刷新一次）
   * 流区段（&lt;5分钟鉴别）
* 批次区段 - 需要确保您了解合格用户的每日流量，并确保目标系统能够处理每个历程以及所有历程中的突发吞吐量
* 流式区段 - 需要确保可以处理用户档案资格的初始突发量，以及每个历程和所有历程的每日合格流传输流量
* offer decisioning不受支持
* 不支持业务事件
* 出站集成到第三方系统
   * 不支持单个静态IP，因为我们的基础架构是多租户(必须允许列表所有数据中心IP)
   * 自定义操作仅支持POST和PUT方法
   * 身份验证支持：令牌 |密码 | OAuth2
* 无法在各种沙箱之间打包和移动Adobe Experience Platform或Journey Optimizer的各个组件。 必须在新环境中重新实施

<br>

### Campaign(v7/v8)

* 消息中心的执行实例必须由Adobe管理的Cloud Services托管
* 必须位于v7内部版本>21.1或v8上
* 消息传送吞吐量
   * AC(v7)每小时5万
   * AC(v8)每小时最多1M（基于软件包）
* AC(v7)仅支持事件启动历程的
   * 未启动区段或区段成员资格的历程
   * 不支持读取受众和基于业务事件的历程，因为它可以发送到执行实例的批量
* AC(v7)或AC(v8)都不支持消息中的Offer decisioning
* 对Campaign的出站API调用没有限制
* 事务性消息日志未本地同步到AEP。 需要咨询团队的精力。 建议最多每4小时导出日志

<br>

### Campaign Standard

* 吞吐量支持14个tp（每小时5万）
* 仅支持事件启动的历程
   * 未启动区段或区段成员资格的历程
   * 不支持读取受众和基于业务事件的历程，因为它可以发送到执行实例的批量
* 从发送到Campaign Standard的事务型消息中打开并单击活动将在Journey Optimizer历程画布中以“重新操作事件”的形式本地显示
* 事务性消息日志不会本地同步回Experience Platform。 需要咨询团队的精力。 建议最多每4小时导出日志

<br>

## 实施步骤

### Adobe Experience Platform

#### 模式/数据集

1. 根据客户提供的数据在 Experience Platform 中[配置单个用户档案、体验事件和多实体模式。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 为Adobe Campaign broadLog、trackingLog和不可交付地址表创建基于体验事件类的架构（可选）。
1. 为要摄入的数据在 Experience Platform 中[创建数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)。
1. 在 Experience Platform 中为数据集[添加数据使用标签](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hans)以便进行治理。
1. [创建对目标实施治理的策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hans)。

#### 用户档案/身份

1. [创建任何客户特定的命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)。
1. [向模式添加身份](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [为用户档案启用模式和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。
1. 为[!UICONTROL 实时客户档案]的不同视图[设置合并策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hans)（可选）。
1. 为历程使用创建区段。

#### 源/目标

1. 使用流传输 API 和源连接器[将数据摄入 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans)

### Journey Optimizer

1. 配置Experience Platform数据源并确定哪些字段应作为profile的一部分缓存。必须先在Journey Optimizer中配置用于启动客户旅程的流数据，才能获取编排ID。 然后，此编排ID将提供给开发人员以与摄取结合使用
1. 配置外部数据源
1. 为Campaign实例配置自定义操作

### Campaign v7/v8或Campaign Standard

* 消息模板需要配置相应的个性化上下文
* 导出工作流需要配置为将事务性消息传递日志导出回Experience Platform。 建议最多每4小时运行一次

### 移动推送配置（可选）

1. 实施Experience PlatformMobile SDK以收集推送令牌和登录信息，以关联到已知的客户配置文件
1. 利用Adobe标记并创建具有以下扩展的移动资产：
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Adobe Experience Platform Edge Network
   * 身份 （边缘网络）
   * 移动核心
1. 确保您拥有专用数据流，用于移动设备应用程序部署与Web部署
1. 有关更多信息，请参阅 [Adobe Journey Optimizer Mobile指南](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

   >[!IMPORTANT]
   >如果希望通过Journey Optimizer发送实时通信，并通过Campaign发送批量推送通知，则可能需要在Journey Optimizer和Campaign中收集移动令牌。 Campaign v8要求专门使用Campaign SDK来捕获推送令牌。

<br>

## 相关文档

* [Experience Platform文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Experience Platform 标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
* [Journey Optimizer 文档](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hans)
* [Journey Optimizer产品描述](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Campaign v8文档](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=en)
* [Campaign v7文档](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hans)
* [Campaign Standard 文档](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hans)