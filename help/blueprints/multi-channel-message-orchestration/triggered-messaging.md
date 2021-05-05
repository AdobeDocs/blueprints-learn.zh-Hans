---
title: 触发式消息和Adobe Experience Platform Blueprint
description: 使用 Adobe Experience Platform 作为流式传输数据、客户个人资料和细分的中心枢纽，执行触发的消息和体验。
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
translation-type: tm+mt
source-git-commit: 01f70fe432d7be38b71889ae19c0d5fe4cf0f78a
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 68%

---

# 触发式消息和Adobe Experience Platform Blueprint

使用 Adobe Experience Platform 作为流式传输数据、客户个人资料和细分的中心枢纽，执行触发的消息和体验。

## 用例

* 触发式消息
* 注册确认
* 放弃购物车和应用程序表单
* 位置触发式消息

## 架构

<img src="assets/triggered.svg" alt="触发式消息和Adobe Experience Platform蓝图的参考体系结构" style="border:1px solid #4a4a4a" />

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
* 区段成员关系发起的历程可以两种模式运行：
   * 批次区段（每 24 小时刷新一次）
   * 流传输区段（&lt;5 分钟资格）
* 批次区段：确保您了解符合资格的用户的每日流量，并确保目的地系统能够处理每个历程以及所有历程中的突发吞吐量
* 流传输区段：确保可以处理用户档案资格的初始突发量，以及每个历程和所有历程符合资格的每日流传输流量
* 最终目的地必须支持 REST API 和 JSON 有效负载
* 当前不支持 Offer Decisioning
* 请参阅 [Experience Platform 的用户档案和数据摄入护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)

### Adobe Campaign Standard

* 吞吐量仅支持 14tps（每小时 50k）
* 不支持区段成员关系发起的历程
* Journey Orchestration 支持打开/点击事务性消息的反应事件。
* 事务性消息日志当前未本地同步到 Experience Platform，需要手动配置。建议最多每四小时导出一次日志。


## 实施步骤

### Adobe Experience Platform

#### 架构/数据集

1. [根据客户提供的数据在 Experience Platform 中配置单个用户档案、体验事件和多实体架构。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html)
1. 为broadLog、trackingLog、不可交付地址和用户档案首选项创建Adobe Campaign模式（可选）。
1. [在Experience Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) 中创建要摄取的数据。
1. [将Experience Platform中的数](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) 据使用标签添加到数据集以进行管理。
1. [创建对目的地实施治理的策略。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html)

#### 用户档案/身份

1. [创建任何客户特定的命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [向模式添加身份](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [为用户档案启用模式和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html)。
1. [为实时客](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) 户视图的不 [!UICONTROL 同用户档案设置合] 并策略（可选）。
1. 为Adobe Campaign使用创建区段。

#### 源/目的地

1. [使用流API和源](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) 连接器将数据引入Experience Platform。1.配 [!DNL Azure] 置Blob存储目标以与Adobe Campaign一起使用。

#### 移动应用程序部署

1. 为Adobe Campaign Classic实施Adobe Campaign SDK或为Adobe Campaign Standard实施Experience Platform SDK。 如果存在Experience Platform Launch，建议将Adobe Campaign Classic或Adobe Campaign Standard扩展与Experience Platform SDK一起使用。


### Journey Orchestration

1. 用于启动客户历程的流传输数据必须首先在 Journey Orchestration 中配置，才能获得 Orchestration ID。然后，此业务流程 ID 将被提供给开发人员以在摄入时使用。
1. 配置外部数据源。
1. 配置自定义操作。

### Adobe Campaign Standard

1. 使用适当的个性化设置配置消息模板。
1. 配置 导出工作流 导出事务性消息日志。建议最多每四小时运行一次。


## 相关文档

* [Adobe Experience Platform 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Journey Orchestration 文档](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=zh-Hans)
* [Adobe Campaign Classic文档](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hans)
* [Adobe Campaign Standard文档](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hans)
* [Experience Platform Launch 文档](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hans)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
