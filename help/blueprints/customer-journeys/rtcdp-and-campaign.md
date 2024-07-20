---
title: Real-Time CDP与 [!DNL Campaign] v7和Campaign Standard集成模式
description: 展示Adobe Experience Platform及其Real-time Customer Profile和集中式分段工具如何与Adobe [!DNL Campaign] 一起使用，以提供个性化的对话。
solution: Real-Time Customer Data Platform, [!DNL Campaign]
exl-id: a15e8304-2763-42fc-9978-11f2482ea8b8
source-git-commit: 258aea64f6ff2f620b1adaa0c9ba4b02b47acce9
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 42%

---

# 具有[!DNL Campaign]集成模式的[!DNL Real-Time Customer Data Platform]

展示Adobe[!DNL Experience Platform]及其Real-time Customer Profile和集中式分段工具如何与Adobe[!DNL Campaign]一起使用，以提供个性化的对话。

## 应用程序

* Adobe [!DNL Experience Platform Real-Time Customer Data Platform]
* Adobe[!DNL Campaign] v7或[!DNL Campaign Standard]

## 架构

<img src="assets/rtcdp-campaign-architecture.svg" alt="批次消息和 Adobe Experience Platform 集成模式的参考架构" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## 先决条件

* 建议在同一IMS组织中设置Experience Platform和[!DNL Campaign]，并使用Adobe Admin Console进行用户访问。 这还能确保客户能够从营销 UI 中利用解决方案切换器

## 护栏

以下部分介绍了此集成的防护。

### Adobe [!DNL Campaign]

* 仅支持Adobe[!DNL Campaign]单个组织单位部署
* Adobe[!DNL Campaign]是所有活动配置文件的真实来源，这意味着配置文件必须存在于Adobe[!DNL Campaign]中，并且不应基于Experience Platform区段创建新配置文件。
* [!DNL Campaign]导出工作流至多每4小时运行一次
* Adobe[!DNL Campaign] broadLog、trackingLog和不可投放地址的XDM架构和数据集不是现成的，必须设计和构建

### Real-time Customer Data Platform区段共享

* 请参阅RTCDP [!DNL Campaign]目标连接器 — [RTCDP营销活动连接](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=zh-Hans)

* 查看 [!DNL Real-Time Customer Profile Data] 和分段](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)的[默认护栏

## 实施步骤

以下各节描述了每个应用程序的实施步骤。

### Adobe Experience Platform  

#### 架构/数据集

1. 根据客户提供的数据在 Experience Platform 中[配置单个用户档案、体验事件和多实体模式。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=zh-Hans)
1. 为broadLog、trackingLog、无法投放的地址和配置文件首选项创建Adobe[!DNL Campaign]架构（可选）。
1. 为要摄入的数据在 Experience Platform 中[创建数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)。
1. 在 Experience Platform 中为数据集[添加数据使用标签](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hans)以便进行治理。
1. [创建对目标实施治理的策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hans)。

#### 用户档案/身份

1. [创建任何客户特定的命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)。
1. [向模式添加身份](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)。
1. [为用户档案启用架构和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。
1. 为[!UICONTROL 实时客户档案]的不同视图[设置合并策略](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hans)（可选）。
1. 为Adobe[!DNL Campaign]使用情况创建区段。

#### 源/目标

1. [Experience Platform和 [!DNL Campaign] 标准源和设计](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=zh-Hans)
1. [Experience Platform和 [!DNL Campaign] v7源和目标](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/aep-sources-destinations/get-started-sources-destinations.html?lang=zh-Hans)
1. 使用流传输 API 和源连接器[将数据摄入 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans)
1. 配置[!DNL Azure] blob存储目标以用于Adobe[!DNL Campaign]。

#### Adobe [!DNL Campaign]

1. 为用户档案、查找数据和相关投放个性化数据配置架构。

>[!IMPORTANT]
>
>此时，了解配置文件和事件数据的Experience Platform中的数据模型非常重要，这样您就可以知道Adobe[!DNL Campaign]中需要哪些数据。

#### 导入工作流

1. 将简化的配置文件数据加载并摄取到Adobe[!DNL Campaign] sFTP。
1. 将编排和消息个性化数据加载并摄取到Adobe[!DNL Campaign] sFTP。
1. 通过工作流从 [!DNL Azure] blob 摄入 Experience Platform 区段。

#### 导出工作流

1. 每四小时通过工作流将Adobe[!DNL Campaign]日志发送回Experience Platform（broadLog、trackingLog、无法投放的地址）。
1. 每四小时通过咨询构建的工作流将用户档案首选项发送回 Experience Platform（可选）。

### 移动推送配置

* 用于与移动设备集成以推送通知的两种受支持的方法：
   * Experience Platform Mobile SDK
   * [!DNL Campaign] Mobile SDK
* Experience Platform Mobile SDK 路径:
   * 利用Adobe标记和[!DNL Campaign Classic]扩展来设置您与Experience PlatformMobile SDK的集成
   * 需要了解 Adobe 标记和数据收集的工作知识
   * 需要具有以下移动设备开发经验：在 Android 和 iOS 中推送通知以部署 SDK，与 FCM (Android) 和 APNS (iOS) 集成来获取推送令牌，将应用程序配置为接收推送通知和处理推送交互
* [!DNL Campaign] Mobile SDK
   * 请参阅[Campaign ClassicSDK文档](https://developer.adobe.com/client-sdks/solution/adobe-campaign-classic/)

>[!IMPORTANT]
>
>如果您部署[!DNL Campaign] SDK并且正在与其他Experience Cloud应用程序一起使用，则将需要使用Experience PlatformMobile SDK进行数据收集。 这将在设备上创建重复的客户端调用。

## 相关文档

* [Adobe [!DNL Experience Platform] 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [[!DNL Campaign Classic] 文档](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hans)
* [[!DNL Campaign Standard] 文档](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hans)
* [[!DNL Experience Platform] Launch文档](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hans)
* [[!DNL Experience Platform] Mobile SDK文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
