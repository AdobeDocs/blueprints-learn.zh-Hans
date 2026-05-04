---
title: Journey Optimizer 与 Adobe Campaign v8 Blueprint
description: 演示如何将 Adobe Journey Optimizer 与 Adobe Campaign 结合使用，通过 Campaign 中的实时消息传送服务器在本地发送消息
solution: Journey Optimizer, Campaign, Campaign v8, Campaign v8 Client Console
version: Campaign v8, Campaign v8 Client Console
exl-id: 447a1b60-f217-4295-a0df-32292c4742b0
TQID: https://experienceleague.adobe.com/EWmi1DKRUqfWUqK0u-pfXkdUlzDc6-HjC0i1QqOocpk
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: d556b755-390a-43f0-be32-a08cf6236126
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
subfeature_v2:
  - id: af7571a6-3ddb-4c1c-abdf-4d4dde592140
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c7d04a2c-412a-4c9d-9d7a-4456eaa5adeb
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: a99add31cc9f485db119ca00426798545e6a7316
workflow-type: tm+mt
source-wordcount: 795
ht-degree: 56%

---

# Journey Optimizer 与 Adobe Campaign v8 Blueprint

演示如何在[!DNL Campaign]中利用Real-time Messaging Server，将Adobe [!DNL Journey Optimizer]与Adobe [!DNL Campaign]一起原生用于发送消息。

## 架构

<img src="images/ajo-campaign-v8-architecture.svg" alt="参考架构 Journey Optimizer Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

>[!IMPORTANT]
>可以同时使用 Journey Optimizer 和 Campaign 来彼此独立地发送消息，但需要考虑一些技术注意事项。 如果您希望遵循此途径，请与售前企业架构师合作，确保您了解支持实施所需的条件

<br>

## 先决条件

查看每个应用程序的以下先决条件。

### Adobe Experience Platform

* 必须在系统中配置架构和数据集，然后才能配置 Journey Optimizer 数据源
* 对于基于体验事件类的架构，当您希望触发的事件不是基于规则的事件时，请添加“Orchestration eventID”字段组
* 对于基于个人资料类的架构，请添加“个人资料测试详细信息”字段组，以便能够加载测试个人资料以用于Journey Optimizer
* Journey Optimizer 和 Campaign 配置在同一 IMS 组织中

### Campaign v8

* Adobe Managed Cloud Services必须托管实时消息服务（即消息中心）的执行实例
* 所有消息创作均在 Campaign 实例本身内完成

## 护栏

* [Journey Optimizer护栏产品限制](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/get-started/guardrails)

* [护栏和端到端延迟指导](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html?lang=zh-Hans)

## 实施步骤

请按照下面描述的每个应用程序的实施内容进行操作。

### Adobe Experience Platform

#### 架构/数据集

1. 根据客户提供的数据在 Experience Platform 中[配置单个用户档案、体验事件和多实体模式。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&lang=zh-Hans)
1. （可选）为Adobe Campaign broadLog、trackingLog和无法投放的地址表创建基于Experience Event类的架构。
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

1. 使用流API和源连接器[将数据摄取到 [!DNL Experience Platform]](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&lang=zh-Hans)。

### Journey Optimizer

1. 配置[!DNL Experience Platform]数据源并确定应缓存哪些字段
1. 用于启动客户历程的流传输数据必须首先在 Journey Optimizer 中配置，才能获得编排 ID。 然后，此编排 ID 将被提供给开发人员以在摄入时使用。
1. 配置外部数据源。
1. 为Campaign实例配置自定义操作。

### Campaign v8

* 需要为消息模板配置适当的个性化上下文。
* 对于[!DNL Campaign]标准：需要配置导出工作流，以将事务性消息传递日志导出回Experience Platform。 建议最多每四小时运行一次。
* 对于[!DNL Campaign] v8.4，可以利用Experience Platform中的Adobe [!DNL Campaign] Managed Services Source Connector将投放和跟踪事件从Campaign同步到Experience Platform中。 有关详细信息，请参阅[Source连接器](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=zh-Hans)文档。

### 移动推送配置（可选）

1. 实施[!DNL Experience Platform] Mobile SDK以收集推送令牌和登录信息以绑定回已知的客户配置文件。
1. 利用 Adobe 标记并创建具有以下扩展的移动资产：
   * Adobe [!DNL Journey Optimizer] | Adobe [!DNL Campaign Classic] | Adobe [!DNL Campaign Standard]
   * Adobe [!DNL Experience Platform] [!DNL Edge Network]
   * [!DNL Edge Network]的身份
   * 移动核心
1. 确保您拥有专用数据流用于移动应用程序部署而不是Web部署。
1. 有关详细信息，请参阅[Adobe Journey Optimizer Mobile指南](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer/push-notification/)。

   >[!IMPORTANT]
   >如果希望通过 Journey Optimizer 发送实时通信，并通过 Campaign 发送批量推送通知，则可能需要在 Journey Optimizer 和 Campaign 中收集移动令牌。 Campaign v8 要求专门使用 Campaign SDK 来捕获推送令牌。

## 相关文档

* [Journey Optimizer文档](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hans)
* [Journey Optimizer产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)
* [Campaign v8文档](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=zh-Hans)
