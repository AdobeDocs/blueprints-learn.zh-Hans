---
title: Real-Time CDP 与 Adobe Campaign v8 集成模式
description: 显示如何将 Adobe Experience Platform 及其实时客户档案和集中化分段工具与 Adobe Campaign v8 结合使用来提供个性化对话。
solution: Real-Time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
source-git-commit: a1f3aef5b508575019bd651b9706efc7d6db5306
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 72%

---

# 具有Adobe[!DNL Campaign] v8集成模式的[!DNL Real-Time CDP]

展示Adobe[!DNL Experience Platform]及其Real-time Customer Profile和集中式分段工具如何与Adobe Campaign一起使用，以提供个性化的对话。

## 应用程序

* Adobe [!DNL Experience Platform Real-Time CDP]
* Adobe[!DNL Campaign] v8

## 架构

<img src="assets/rtcdp-campaignv8-architecture.svg" alt="批次消息和 Adobe Experience Platform 集成模式的参考架构" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 先决条件

* 对于 Experience Cloud，必须为客户配置有效的 IMS 组织
* 建议将Adobe Experience Platform和[!DNL Campaign]配置为使用同一个登录URL的IMS组织
* 客户必须配置[!DNL Campaign]的V8实例
* 客户必须符合条件并有权访问 RTCDP、源、目标。
* Adobe[!DNL Campaign]产品上下文必须存在
<br>

## 实施步骤

请参阅以下文档，了解如何配置到 Adobe Experience Platform 的 Campaign v8 源连接器和到 Campaign v8 的 Real-time Customer Data Platform 目标连接器。
[Campaign 和 AEP 连接器](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=zh-Hans)

## 护栏

### Adobe Campaign

* 请参阅 Campaign 源连接器文档 - [Campaign 源连接器](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=zh-Hans)
* 仅支持 Adobe Campaign 单个组织单位部署


### Experience Platform Real-time Customer Data Platform 区段共享

* 请参阅 RTCDP Campaign 目标连接器 - [RTCDP Campaign 连接](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=zh-Hans)

* 请参阅 AEP 的用户档案和数据摄入护栏 - [链接](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
