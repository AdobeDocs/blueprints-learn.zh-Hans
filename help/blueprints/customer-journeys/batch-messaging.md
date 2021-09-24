---
title: 批次消息和 Adobe Experience Platform Blueprint
description: 使用 Adobe Experience Platform 作为客户档案和分段的中心，执行计划消息和批次消息活动。
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
source-git-commit: 3c950cebaa25901ae50433775c510ed834d8bcd5
workflow-type: ht
source-wordcount: '637'
ht-degree: 100%

---

# 批次消息和 Adobe Experience Platform Blueprint

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

<img src="assets/aepbatch.svg" alt="批次消息和 Adobe Experience Platform Blueprint 的参考架构" style="border:1px solid #4a4a4a" />

## 护栏

* 仅支持 Adobe Campaign 单个组织单位部署
* Adobe Campaign 是所有主要用户档案的真相来源，这意味着用户档案必须存在于 Adobe Campaign 中，而新用户档案不应基于 Experience Platform 区段创建。
* 通过 Experience Platform 实现的区段成员对于批次（每天 1 次）和流传输（约 5 分钟）都是潜在的

**[!UICONTROL 实时客户数据平台]区段共享到 Adobe Campaign：**

* 建议 20 区段限额
* 激活限于每 24 小时
* 仅合并可用于激活的架构属性（不支持阵列/映射/体验事件）。
* 建议每个区段不超过 20 个属性
* 所有具有“已实现”区段成员的用户档案每个区段有一个文件，或者如果已在文件中将区段成员作为属性添加，则包含“已实现”和“已退出”用户档案
* 支持增量或完整的区段导出
* 不支持文件加密
* Adobe Campaign 导出工作流最多每 4 小时运行一次
* 请参阅 [Experience Platform 的用户档案和数据摄入护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)

## 实施步骤

### Adobe Experience Platform

#### 架构/数据集

1. 根据客户提供的数据在 Experience Platform 中[配置单个用户档案、体验事件和多实体架构。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 为 broadLog、trackingLog、无法投放的地址和用户档案偏好设置创建 Adobe Campaign 模式（可选）。
1. 为要摄入的数据在 Experience Platform 中[创建数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)。
1. 在 Experience Platform 中为数据集[添加数据使用标签](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hans)以便进行治理。
1. [创建对目的地实施治理的策略。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hans)

#### 用户档案/身份

1. [创建任何客户特定的命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)。
1. [向模式添加身份](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)。
1. [为用户档案启用模式和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。
1. 为[!UICONTROL 实时客户档案]的不同视图[设置合并策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hans)（可选）。
1. 为 Adobe Campaign 使用创建区段。

#### 源/目的地

1. 使用流传输 API 和源连接器[将数据摄入 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans)
1. 配置 [!DNL Azure] blob 存储目的地以与 Adobe Campaign 一起使用。

#### 移动应用程序部署

1. 为 Adobe Campaign Classic 实施 Adobe Campaign SDK 或为 Adobe Campaign Standard 实施 Experience Platform SDK。如果存在 Experience Platform Launch，建议将 Adobe Campaign Classic 或 Adobe Campaign Standard 扩展与 Experience Platform SDK 一起使用。

#### Adobe Campaign

1. 为用户档案、查找数据和相关投放个性化数据配置架构。

>[!IMPORTANT]
>
>此时了解用户档案和事件数据在 Experience Platform 中包含哪些数据模型至关重要，这样您就能了解 Adobe Campaign 中需要哪些数据。

#### 导入工作流

1. 将简化的用户档案数据加载并摄入 Adobe Campaign sFTP。
1. 将业务安排和消息个性化数据加载和摄入到 Adobe Campaign sFTP 中。
1. 通过工作流从 [!DNL Azure] blob 摄入 Experience Platform 区段。

#### 导出工作流

1. 每四小时通过工作流将 Adobe Campaign 日志发送回 Experience Platform（broadLog、trackingLog、无法投放的地址）。
1. 每四小时通过咨询构建的工作流将用户档案首选项发送回 Experience Platform（可选）。


## 相关文档

* [Adobe Experience Platform 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Campaign Classic 文档](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hans)
* [Campaign Standard 文档](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hans)
* [Experience Platform Launch 文档](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hans)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
