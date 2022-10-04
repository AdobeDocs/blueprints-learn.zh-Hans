---
title: Real-Time CDP与Adobe Campaign v8集成模式
description: 显示如何将Adobe Experience Platform及其实时客户资料和集中化分段工具与Adobe Campaign v8结合使用来进行个性化对话。
solution: Real-time Customer Data Platform, Campaign
source-git-commit: f8116387105cf1fe0adfc148562529d62ca90cfc
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 45%

---

# Real-Time CDP与Adobe Campaign v8集成模式

显示如何将 Adobe Experience Platform 及其实时客户档案和集中化分段工具与 Adobe Campaign 结合使用来提供个性化对话。

<br>

## 应用程序

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v8

<br>

## 架构

<img src="assets/rtcdp-campaignv8-architecture.svg" alt="批次消息和 Adobe Experience Platform 集成模式的参考架构" style="width:100%; border:1px solid #4a4a4a" />

<br>

## 先决条件

* 对于 Experience Cloud，必须为客户配置有效的 IMS 组织
* 建议在同一IMS组织中配置Adobe Experience Platform和Campaign，以实现单次登录URL
* 必须为客户配置V8 Campaign实例
* 客户必须符合条件并有权访问RTCDP、源、目标。
* 必须存在Adobe Campaign产品上下文

<br>

## 实施步骤

请参阅以下文档，了解如何配置到Adobe Experience Platform的Campaign v8源连接器和到Campaign v8的Real-time Customer Data Platform目标连接器。
[Campaign和AEP连接器](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=en)

## 护栏

### Adobe Campaign

* 请参阅Campaign源连接器文档 —  [Campaign源连接器](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=en)
* 仅支持 Adobe Campaign 单个组织单位部署
* Adobe Campaign 是所有主要用户档案的真相来源，这意味着用户档案必须存在于 Adobe Campaign 中，而新用户档案不应基于 Experience Platform 区段创建。


### Experience PlatformReal-time Customer Data Platform区段共享

* 请参阅RTCDP Campaign目标连接器 —  [RTCDP Campaign连接](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html)
* 建议 50 区段限额
* 请注意，对于批处理（每天1次）和流式处理（约5分钟），以及基于区段评估计划，AEP中的区段成员身份实现都有延迟。
* 激活延迟最少3小时
* 仅合并可用于激活的架构属性（不支持阵列/映射/体验事件）
* 建议每个区段不超过 20 个属性
* 所有具有“已实现”区段成员的用户档案每个区段有一个文件，或者如果已在文件中将区段成员作为属性添加，则包含“已实现”和“已退出”用户档案
* 支持增量和完整的区段导出
* 不支持文件加密
* 请参阅AEP的配置文件和数据摄取防护 —  [链接](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)