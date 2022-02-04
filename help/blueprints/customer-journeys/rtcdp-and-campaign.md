---
title: Real-Time CDP与Adobe Campaign Blueprint
description: 显示如何将Adobe Experience Platform及其实时客户资料和集中化分段工具与Adobe Campaign结合使用来进行个性化对话。
solution: Experience Platform, Campaign v8, Campaign Classic v7, Campaign Standard
source-git-commit: 1c46cbdfc395de4fc9139966cf869ba1feeceaaa
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 56%

---

# Real-Time CDP与Adobe Campaign Blueprint

显示如何将Adobe Experience Platform及其实时客户资料和集中化分段工具与Adobe Campaign结合使用来进行个性化对话。

<br>

## 应用程序

* Adobe Experience PlatformReal-Time CDP
* Adobe Campaign v7或Campaign Standard

<br>

## 架构

<img src="assets/rtcdp-campaign-architecture.svg" alt="批次消息和 Adobe Experience Platform Blueprint 的参考架构" style="width:100%; border:1px solid #4a4a4a" />

<br>

## 先决条件

* 建议在同一IMS组织中配置Experience Platform和Campaign，并利用Adobe Admin Console进行用户访问。 这还可确保客户能够从营销UI中利用解决方案切换器

<br>

## 护栏

### Adobe Campaign

* 仅支持Adobe Campaign单个组织单位部署
* Adobe Campaign 是所有主要用户档案的真相来源，这意味着用户档案必须存在于 Adobe Campaign 中，而新用户档案不应基于 Experience Platform 区段创建。
* Campaign 导出工作流最多每 4 小时运行一次
* Adobe Campaign broadLog、trackingLogs和不可交付地址的XDM架构和数据集并非开箱即用，必须进行设计和构建

### Experience PlatformCDP区段共享

* 20个区段限额的建议
* 激活时间限制为每24小时
* 只有联合架构属性可用于激活（不支持阵列/映射/体验事件）
* 关于每个区段不超过20个属性的建议
* 所有具有“已实现”区段成员的用户档案每个区段有一个文件，或者如果已在文件中将区段成员作为属性添加，则包含“已实现”和“已退出”用户档案
* 支持增量和完整区段导出
* 不支持文件加密

<br>

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
1. [向模式添加身份](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [为用户档案启用模式和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。
1. 为[!UICONTROL 实时客户档案]的不同视图[设置合并策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hans)（可选）。
1. 为 Adobe Campaign 使用创建区段。

#### 源/目的地

1. 使用流传输 API 和源连接器[将数据摄入 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans)
1. 配置 [!DNL Azure] blob 存储目的地以与 Adobe Campaign 一起使用。

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


### 移动推送配置

* 用于与移动设备集成推送通知的两种受支持的方法：
   * Experience Platform Mobile SDK
   * Campaign Mobile SDK
* Experience PlatformMobile SDK路由：
   * 利用Adobe标记和Campaign Classic扩展来设置您与Experience PlatformMobile SDK的集成
   * 需要了解Adobe标记和数据收集的工作知识
   * 需要在Android和iOS中具有推送通知的移动设备开发经验来部署SDK，与FCM(Android)和APNS(iOS)集成以获取推送令牌，将应用程序配置为接收推送通知并处理推送交互
* Campaign Mobile SDK
   * 请按照 [Campaign SDK文档]（Campaign Mobile SDK请按照此处概述的部署文档进行操作）

   >[!IMPORTANT]
   >如果您部署Campaign SDK并正在使用其他Experience Cloud应用程序，则需要使用Experience PlatformMobile SDK进行数据收集。 这将在设备上创建重复的客户端调用。

## 相关文档

* [Adobe Experience Platform 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Campaign Classic 文档](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hans)
* [Campaign Standard 文档](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hans)
* [Experience Platform Launch 文档](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hans)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
