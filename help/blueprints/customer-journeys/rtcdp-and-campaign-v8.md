---
title: Real-Time CDP 与 Adobe Campaign v8 集成模式
description: 显示如何将 Adobe Experience Platform 及其实时客户档案和集中化分段工具与 Adobe Campaign v8 结合使用来提供个性化对话。
solution: Real-Time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
source-git-commit: 5f9384abe7f29ec764428af33c6dd1f0a43f5a89
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 100%

---

# Real-Time CDP 与 Adobe Campaign v8 集成模式

显示如何将 Adobe Experience Platform 及其实时客户档案和集中化分段工具与 Adobe Campaign 结合使用来提供个性化对话。

<br>

## 应用程序

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v8

<br>

## 架构

<img src="assets/rtcdp-campaignv8-architecture.svg" alt="批次消息和 Adobe Experience Platform 集成模式的参考架构" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 先决条件

* 对于 Experience Cloud，必须为客户配置有效的 IMS 组织
* 建议在同一 IMS 组织中配置 Adobe Experience Platform 和 Campaign，以便只有一个登录 URL
* 必须为客户配置 V8 Campaign 实例
* 客户必须符合条件并有权访问 RTCDP、源、目标。
* 必须存在 Adobe Campaign 产品上下文
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
