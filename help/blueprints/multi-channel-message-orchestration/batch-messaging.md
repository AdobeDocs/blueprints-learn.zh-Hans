---
title: 批处理消息和Adobe Experience Platform Blueprint
description: 使用 Adobe Experience Platform 作为客户档案和分段的中心，执行计划消息和批次消息活动。
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
translation-type: tm+mt
source-git-commit: 81df87f850b7ac4be9dce7a3b96d39a3a47685c5
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 48%

---

# 批处理消息和Adobe Experience Platform Blueprint

使用 Adobe Experience Platform 作为客户档案和分段的中心，执行计划消息和批次消息活动。

## 用例

* 计划的电子邮件活动
* 入门培训和再营销活动

## 应用程序

* Adobe Experience Platform
* Adobe Campaign Classic 或 Standard

## 集成模式

* Adobe Experience Platform → Adobe Campaign Classic
* Adobe Experience Platform → Adobe Campaign Standard

## 架构

<img src="assets/aepbatch.svg" alt="批处理消息和Adobe Experience Platform Blueprint的参考架构" style="border:1px solid #4a4a4a" />

## 护栏

* 仅支持Adobe Campaign单个组织单位部署
* Adobe Campaign是所有活动用户档案的真相来源，这意味着用户档案必须存在于Adobe Campaign中，而新用户档案不应基于Experience Platform段创建。
* 通过 Experience Platform 实现的区段成员对于批次（每天 1 次）和流传输（约 5 分钟）都是潜在的

**[!UICONTROL 实时客户数据平] 台细分共享到Adobe Campaign:**

* 建议 20 区段限额
* 激活限于每 24 小时
* 仅合并可用于激活的架构属性（不支持阵列/映射/体验事件）。
* 建议每个区段不超过 20 个属性
* 所有具有“已实现”区段成员的用户档案每个区段有一个文件，或者如果已在文件中将区段成员作为属性添加，则包含“已实现”和“已退出”用户档案
* 支持增量或完整的区段导出
* 不支持文件加密
* Adobe Campaign导出工作流最多每4小时运行一次
* 请参阅 [Experience Platform 的用户档案和数据摄入护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)

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
1. [启用模式和用户档案集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html)。
1. [为实时客](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) 户视图的不 [!UICONTROL 同用户档案设置合] 并策略（可选）。
1. 为Adobe Campaign使用创建区段。

#### 源/目的地

1. [使用流传输 API 和源连接器将数据引入 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
1. 配置[!DNL Azure] blob存储目标以与Adobe Campaign一起使用。

#### 移动应用程序部署

1. 为Adobe Campaign Classic实施Adobe Campaign SDK或为Adobe Campaign Standard实施Experience Platform SDK。 如果存在Experience Platform Launch，建议将Adobe Campaign Classic或Adobe Campaign Standard扩展与Experience Platform SDK一起使用。

#### Adobe Campaign

1. 为用户档案、查找数据和相关投放个性化数据配置架构。

>[!IMPORTANT]
>
>此时了解用户档案和事件数据在Experience Platform中包含哪些数据模型至关重要，这样您就能了解Adobe Campaign中需要哪些数据。

#### 导入工作流

1. 将简化的用户档案数据加载并导入Adobe Campaign sFTP。
1. 将业务安排和消息个性化数据加载和收录到Adobe Campaign sFTP上。
1. 通过工作流从 [!DNL Azure] blob 摄入 Experience Platform 区段。

#### 导出工作流

1. 每四小时通过工作流将Adobe Campaign日志发送回Experience Platform（broadLog、trackingLog、不可交付的地址）。
1. 每四小时通过咨询构建的工作流将用户档案首选项发送回 Experience Platform（可选）。


## 相关文档

* [Adobe Experience Platform 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Campaign Classic 文档](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hans)
* [Campaign Standard 文档](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hans)
* [Experience Platform Launch 文档](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hans)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
