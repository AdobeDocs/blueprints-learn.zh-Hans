---
title: Journey Optimizer - 触发式消息和 Adobe Experience Platform Blueprint
description: 使用 Adobe Experience Platform 作为流式传输数据、客户档案和分段的中心枢纽，执行触发的消息和体验。
solution: Experience Platform, Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 2ead62f94e761cd9453be284a9fde3c5803879eb
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 41%

---

# Journey Optimizer

Adobe Journey Optimizer 是专门为营销团队打造的系统，可实时响应客户行为并在其所处场景中与之交流。数据管理功能已迁移至 Adobe Experience Platform，以便营销团队能够专注于自己最擅长的工作：创造世界一流的客户历程和个性化的对话。此 Blueprint 概述了该应用程序的技术功能，并深入介绍了组成 Adobe Journey Optimizer 的各种架构组件。

<br>

## 用例

* 触发式消息
* 欢迎和注册确认
* 放弃购物车和申请表
* 位置触发式消息
* 体育场内体验
* 旅游和酒店在抵达前和入住期间的体验

<br>

## 架构

<img src="assets/ajo-architecture.svg" alt="参考架构Journey Optimizer Blueprint" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Blueprint方案

| 场景 | 描述 | 功能 |
| :-- | :--- | :--- |
| [第三方消息传送](3rd-party-messaging.md) | 演示如何将Adobe Journey Optimizer与第三方消息传递系统结合使用来编排和发送个性化通信 | 在客户与您的品牌或公司进行互动时，立即向客户提供1:1的个性化通信<br><br>注意事项：<br><ul><li>第三方系统必须支持用于身份验证的承载令牌</li><li>由于多租户架构，不支持静态IP</li><li>当涉及每秒API调用数时，请注意第三方系统存在的体系结构限制。  客户可能需要从第三方供应商购买额外的卷，以支持来自Journey Optimizer的卷</li><li>不支持消息或负载中的Offer decisioning</li></ul> |

<br>

## 集成模式

| 集成 | 描述 | 功能 |
| :-- | :--- | :--- |
| [Journey Optimizer与Adobe Campaign](ajo-and-campaign.md) | 显示如何使用Adobe Journey Optimizer利用实时客户资料编排1:1体验，并利用本机Adobe Campaign事务型消息传递系统来发送消息 | 利用Journey Optimizer的实时客户资料和强大的功能，在时刻体验中进行编排，同时利用Adobe Campaign的本机实时消息传送功能进行最后一英里通信<br><br>注意事项：<br><ul><li>Campaign应用程序必须位于v7内部版本>21.1或v8上</li><li>消息传送吞吐量</li><ul><li>Campaign v7 — 每小时最多5万</li><li>Campaign v8 — 每小时最多100万</li><li>Campaign Standard — 每小时最多5万</li></ul><li>不执行限制，因此用例需要企业架构师的技术审查</li><li>不支持在Campaign发送的消息中利用Offer decisioning</li></ul> |

<br>

## 先决条件

Adobe Experience Platform

* 必须在系统中配置架构和数据集，然后才能配置Journey Optimizer数据源
* 对于基于体验事件类的架构，当您希望触发的事件不是基于规则的事件时，请添加“编排事件ID字段组”
* 对于基于个人用户档案类的架构，添加“用户档案测试详细信息”字段组，以便能够加载测试用户档案以与Journey Optimizer一起使用

电子邮件

* 必须准备好用于消息发送的子域
* 子域可以完全委派给Adobe（推荐），或者CNAME可以用于指向特定于Adobe的DNS服务器（自定义）
* 每个子域都需要Google TXT记录，以确保良好的可交付性

移动推送

* 客户必须拥有构建应用程序的移动开发人员
* Adobe Experience Platform Mobile SDK

<br>

## 护栏

[Journey Optimizer护栏产品链接](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=zh-Hans)

请注意上述链接中未列出的这些内容：

* 批次区段 - 需要确保您了解合格用户的每日流量，并确保目标系统能够处理每个历程以及所有历程中的突发吞吐量
* 流式区段 - 需要确保可以处理用户档案资格的初始突发量，以及每个历程和所有历程的每日合格流传输流量
* 本地支持仅在消息中Offer decisioning（无自定义操作）
* 支持的消息类型：
   * 电子邮件
   * 推送 (FCM / APNS)
   * 自定义操作（通过Rest API）
* 出站集成到第三方系统
   * 不支持单个静态IP，因为我们的基础架构是多租户(必须允许列表所有数据中心IP)
   * 自定义操作仅支持POST和PUT方法
   * 通过用户/通过或授权令牌进行身份验证
* 无法在各种沙箱之间打包和移动Adobe Experience Platform或Journey Optimizer的各个组件。 必须在新环境中重新实施

### 数据摄入护栏

<img src="assets/aep-data-ingestion-details-latency.svg" alt="参考架构Journey Optimizer Blueprint" style="width:80%; border:1px solid #4a4a4a" />

<br>

### 激活护栏

<img src="assets/ajo-activation-details-latency.svg" alt="参考架构Journey Optimizer Blueprint" style="width:80%; border:1px solid #4a4a4a" />

<br>

## 实施步骤

### Adobe Experience Platform

#### 模式/数据集

1. 根据客户提供的数据在 Experience Platform 中[配置单个用户档案、体验事件和多实体模式。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 为要摄入的数据在 Experience Platform 中[创建数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)。
1. 在 Experience Platform 中为数据集[添加数据使用标签](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hans)以便进行治理。
1. [创建对目标实施治理的策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hans)。

#### 用户档案/身份

1. [创建任何客户特定的命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)。
1. [向模式添加身份](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [为用户档案启用架构和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。
1. 为[!UICONTROL 实时客户档案]的不同视图[设置合并策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hans)（可选）。
1. 为历程使用创建区段。

#### 源/目标

1. 使用流传输 API 和源连接器[将数据摄入 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans)

### Journey Optimizer

1. 配置您的Experience Platform数据源并确定哪些字段应作为profile的一部分缓存。必须先在Journey Optimizer中配置用于启动客户旅程的流数据，才能获取编排ID。 然后，此编排ID将提供给开发人员以与摄取结合使用
1. 配置外部数据源。
1. 配置自定义操作。

### 移动推送配置

1. 实施Experience PlatformMobile SDK以收集推送令牌和登录信息，以关联到已知的客户配置文件
1. 利用Adobe标记并创建具有以下扩展的移动资产：
1. Adobe Journey Optimizer
1. Adobe Experience Platform Edge Network
1. 身份 （边缘网络）
1. 移动核心
1. 确保您拥有专用数据流，用于移动设备应用程序部署与Web部署
1. 有关更多信息，请参阅 [Adobe Journey Optimizer Mobile指南](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)


## 相关文档

* [Experience Platform文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Experience Platform 标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
* [Journey Optimizer 文档](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hans)
* [Journey Optimizer产品描述](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
