---
title: Journey Optimizer - 触发式消息和 Adobe Experience Platform Blueprint
description: 使用 Adobe Experience Platform 作为流式传输数据、客户档案和分段的中心枢纽，执行触发的消息和体验。
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 3c950cebaa25901ae50433775c510ed834d8bcd5
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 98%

---

# Journey Optimizer

Adobe Journey Optimizer 是专门为营销团队打造的系统，可实时响应客户行为并在其所处场景中与之交流。数据管理功能已迁移至 Adobe Experience Platform，以便营销团队能够专注于自己最擅长的工作：创造世界一流的客户历程和个性化的对话。此 Blueprint 概述了该应用程序的技术功能，并深入介绍了组成 Adobe Journey Optimizer 的各种架构组件。

## 用例

* 触发式消息
* 注册确认
* 放弃购物车和申请表
* 位置触发式消息

## 架构

<img src="assets/journey-optimizer.png" alt="触发式消息和 Adobe Experience Platform Blueprint 的参考架构" style="border:1px solid #4a4a4a" />

## 集成模式

* Adobe Experience Platform -> Journey Optimizer

## 先决条件

1. 对于 Experience Cloud，必须为客户配置有效的 IMS 组织
1. 移动推送

* 客户必须拥有构建应用程序的移动开发人员
* Adobe Experience Platform Mobile SDK
* 数据收集
   * 移动标记属性
      * 扩展：
         * Adobe Journey Optimizer 扩展
         * Adobe Experience Platform Edge Network
         * 身份
         * 移动核心
         * 用户档案
   * 应用程序配置
   * 数据流
      * 为 Experience Platform 启用
      * 事件数据集 - 用于收集常规移动设备行为
      * 用户档案数据集 - AJO 推送用户档案数据集（必须相同）

## 护栏

* 有关限制的更多详情，请参阅链接
* 批次区段 - 需要确保您了解合格用户的每日流量，并确保目标系统能够处理每个历程以及所有历程中的突发吞吐量
* 流式区段 -需要确保可以处理用户档案资格的初始突发量，以及每个历程和所有历程的每日合格流传输流量
* 用户档案更新活动 - 可以在历程中以本地方式更新实时客户档案。在将更新处理到用户档案存储时，有最多 1 分钟的延迟
* 业务事件 - 基于对 JO 系统的外部调用，可触发基于读取区段的历程
* 本机仅支持消息中的 Offer Decisioning。将来会通过本机操作提供支持
* 支持的渠道：
   * 电子邮件
   * 推送 (FCM / APNS)
   * Rest API 端点
* 每秒处理 5000 个事件，并可水平扩展（受预算限制）
* 完成 A/B 测试需要使用两个投放并使用 QS 或 CJA 确定结果
* Litmus 集成 - 必须拥有 Litmus 帐户才能利用集成

## 实施步骤

### Adobe Experience Platform

#### 模式/数据集

1. 根据客户提供的数据在 Experience Platform 中[配置单个用户档案、体验事件和多实体模式。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 为 broadLog、trackingLog、无法投放的地址和用户档案偏好设置创建 Adobe Campaign 模式（可选）。
1. 为要摄入的数据在 Experience Platform 中[创建数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)。
1. 在 Experience Platform 中为数据集[添加数据使用标签](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hans)以便进行治理。
1. [创建对目标实施治理的策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hans)。

#### 用户档案/身份

1. [创建任何客户特定的命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)。
1. [向模式添加身份](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [为用户档案启用模式和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。
1. 为[!UICONTROL 实时客户档案]的不同视图[设置合并策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hans)（可选）。
1. 为 Adobe Campaign 用途创建区段。

#### 源/目标

1. 使用流 API 和源连接器[将数据摄入到 Experience Platform 中](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans)。1. 配置[!DNL Azure] Blob 存储目标以便与 Adobe Campaign 一起使用。

#### 移动应用程序部署

1. 为 Adobe Campaign Classic 实施 Adobe Campaign SDK 或为 Adobe Campaign Standard 实施 Experience Platform SDK。如果存在 Experience Platform Launch，建议将 Adobe Campaign Classic 或 Adobe Campaign Standard 扩展与 Experience Platform SDK 一起使用。


### Journey Orchestration

1. 用于启动客户历程的流传输数据必须首先在 Journey Optimizer 中配置，才能获得编排 ID。然后，此编排 ID 将被提供给开发人员以在摄入时使用。
1. 配置外部数据源。
1. 配置自定义操作。

## 相关文档

* [Adobe Experience Platform 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Journey Optimizer 文档](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=zh-Hans)
* [Experience Platform Launch 文档](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hans)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
