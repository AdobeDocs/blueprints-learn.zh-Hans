---
title: 触发式消息和 Adobe Experience Platform Blueprint
description: 使用 Adobe Experience Platform 作为流式传输数据、客户档案和分段的中心枢纽，执行触发的消息和体验。
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 584007cc71e00729732c67a97546e2c21aed3f87
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 100%

---

# 触发式消息和 Adobe Experience Platform Blueprint

使用 Adobe Experience Platform 作为流式传输数据、客户档案和分段的中心枢纽，执行触发的消息和体验。

## 用例

* 触发式消息
* 注册确认
* 放弃购物车和应用程序表单
* 位置触发式消息

## 架构

<img src="assets/triggered.svg" alt="触发式消息和 Adobe Experience Platform Blueprint 的参考架构" style="border:1px solid #4a4a4a" />

## 集成模式

* Adobe Experience Platform -> Journey Orchestration

## 先决条件

* Adobe Experience Platform
* Journey Orchestration

## 护栏

### Journey Orchestration

* 请参阅[有关限制的更多详情](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=zh-Hans#starting-with-journeys)链接
* 可通过 API 设置封顶，以确保目的地系统不会因饱和而达到故障点。封顶意味着超过上限的消息会被彻底丢弃，永不发送。仍不支持限流。
   * 最大连接数：目的地可处理的 http/s 连接的最大数
   * 最大调用数：periodInMs 参数中要进行的最大调用数
   * periodInMs：时间（以毫秒为单位）
* 区段成员资格发起的历程可以两种模式运行：
   * 批次区段（每 24 小时刷新一次）
   * 流式区段（&lt;5 分钟资格）
* 批次区段：确保您了解符合资格的用户的每日流量，并确保目的地系统能够处理每个历程以及所有历程中的突发吞吐量
* 流式区段：确保可以处理用户档案资格的初始突发量，以及每个历程和所有历程符合资格的每日流传输流量
* 最终目的地必须支持 REST API 和 JSON 有效负载
* 当前不支持 Offer Decisioning
* 请参阅 [Experience Platform 的用户档案和数据摄入护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)

### Adobe Campaign Standard

* 吞吐量仅支持 14 tps（每小时 50k）
* 不支持区段成员资格发起的历程
* Journey Orchestration 支持打开/点击事务性消息的反应事件。
* 事务性消息日志当前未本地同步到 Experience Platform，需要手动配置。建议最多每四小时导出一次日志。


## 实施步骤

### Adobe Experience Platform

#### 架构/数据集

1. 根据客户提供的数据在 Experience Platform 中[配置单个用户档案、体验事件和多实体架构。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html?lang=zh-Hans)
1. 为 broadLog、trackingLog、无法投放的地址和用户档案首选项创建 Adobe Campaign 架构（可选）。
1. 为要摄入的数据在 Experience Platform 中[创建数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)。
1. 在 Experience Platform 中为数据集[添加数据使用标签](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hans)以便进行治理。
1. [创建对目的地实施治理的策略。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hans)

#### 用户档案/身份

1. [创建任何客户特定的命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)。
1. [向架构添加身份](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [为用户档案启用架构和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。
1. 为[!UICONTROL 实时客户档案]的不同视图[设置合并策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hans)（可选）。
1. 为 Adobe Campaign 使用创建区段。

#### 源/目的地

1. 使用流 API 和源连接器[将数据摄入到 Experience Platform 中](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans)。1. 配置[!DNL Azure] Blob 存储目的地以便与 Adobe Campaign 一起使用。

#### 移动应用程序部署

1. 为 Adobe Campaign Classic 实施 Adobe Campaign SDK 或为 Adobe Campaign Standard 实施 Experience Platform SDK。如果存在 Experience Platform Launch，建议将 Adobe Campaign Classic 或 Adobe Campaign Standard 扩展与 Experience Platform SDK 一起使用。


### Journey Orchestration

1. 用于启动客户历程的流传输数据必须首先在 Journey Orchestration 中配置，才能获得编排 ID。然后，此编排 ID 将被提供给开发人员以在摄入时使用。
1. 配置外部数据源。
1. 配置自定义操作。

### Adobe Campaign Standard

1. 使用适当的个性化设置配置消息模板。
1. 配置导出工作流导出事务性消息日志。建议最多每四小时运行一次。


## 相关文档

* [Adobe Experience Platform 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Journey Orchestration 文档](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=zh-Hans)
* [Adobe Campaign Classic 文档](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hans)
* [Adobe Campaign Standard 文档](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hans)
* [Experience Platform Launch 文档](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hans)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
