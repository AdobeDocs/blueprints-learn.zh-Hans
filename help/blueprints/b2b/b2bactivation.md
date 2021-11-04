---
title: B2B激活
description: 通过Real-time Customer Data Platform提供基于帐户的受众以及以用户档案为中心的客户体​验。
solution: Experience Platform, Real-time Customer Data Platform
kt: 9311
exl-id: null
source-git-commit: d811d82418d477372caa9e5b0b67af197275d459
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 5%

---

# B2B受众和配置文件激活

使用与单个客户绑定的帐户、机会和潜在客户信息，创建可操作的b2b用户档案，以改进跨渠道的个性化和定位。

## 用例

* 创建人员受众，以便针对B2B数据（包括帐户、机会和潜在客户）跨渠道进行定位和个性化。
* 将受众激活到任何Experience Platform目标，以便进行定位和个性化。

## 应用程序

* 实时客户数据平台 B2B版

## 集成模式

* B2B数据源(Marketo、Salesforce等) -> Real-time Customer Data Platform B2B Edition ->目标各种B2B数据源可用于将帐户、商机、商机和人员数据映射到Real-time Customer Data Platform B2B Edition。

## 架构

<img src="assets/b2b-activation.svg" alt="B2B激活Blueprint的参考架构" style="border:1px solid #4a4a4a" />
<br>

## 护栏

请注意，仅当将Marketo Engage用作源和/或目标时，与Marketo Engage相关的防护和实施步骤才相关。

### 多实例和IMS组织支持：

以下概述了支持的映射Experience Platform和Marketo Engage实例模式。

#### Marketo作为数据源Experience Platform:

* 支持将多个Marketo Engage实例映射到一个Experience Platform实例。
* 对多个Marketo Engage实例的多个Experience Platform实例不支持。
* 不支持一个Marketo Engage实例到多个Experience Platform实例。
* 支持一个Marketo Engage实例到一个Experience Platform实例和多个沙箱。

#### Marketo作为Experience Platform的目标：

* Experience Platform到多个Marketo Engage实例
* 支持多个Experience Platform实例到一个Marketo Engage实例

#### Experience Platform配置文件和分段护栏：

* 请参阅用户档案和分段护栏以进行Experience Platform- [用户档案和分段准则](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
* B2B区段（包括帐户、潜在客户、商机）使用多实体关系，导致区段评估成为批量。 仅限于人员和事件的区段支持流分段。

#### Experience Platform-Marketo Engage源连接器：

* 历史回填最多可能需要7天才能完成，具体取决于数据量。
* 持续的数据更新和来自Marketo的更改将通过流式API发送到Experience Platform，流式API最长可延迟至用户档案5分钟左右，数据湖大约延迟15分钟，具体取决于流量。

#### Experience Platform- Marketo目标连接器：

* 从Real-time Customer Data Platform到Marketo Engage的流区段共享最多可能需要5分钟。
* 根据Experience Platform分段计划，每天共享一次批量分段。 B2B区段（包括帐户、潜在客户、商机）使用多实体关系，导致区段成为批处理。

#### Marketo Engage护栏：

* 联系人和潜在客户必须直接在Marketo Engage中摄取和定义，以便Real-time Customer Data Platform受众与Marketo Engage联系人和潜在客户进行匹配。

#### 目标护栏

* 有关目标的具体指导，请参阅目标文档。 [目标准则](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en)


## 实施步骤

有关如何实施和配置Real-time Customer Data Platform B2B版的指导，请参阅Real-time Customer Data Platform文档的B2B版。 [B2B版Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)

存在两个可能的实施模式。 既能够从Marketo Engage中摄取B2B数据和用户档案，也能从其他CRM数据源中摄取B2B数据。

## 实施注意事项

关于Blueprint的主要注意事项和配置的指导。

* 与和不与Marketo集成CRM:如果实施将使用Marketo Engage作为源，并且Marketo Engage已连接到CRM，则使用Experience Platform中的Marketo源连接器将CRM数据摄取到Experience Platform。 如果需要摄取其他表，请使用Experience Platform源连接器。 如果实施不使用Marketo Engage作为源，请使用CRM源Experience Platform连接器将CRM源直接连接到AEP。
* 仅Real-time Customer Data PlatformB2B版不建议引入和培养铅。 在此用例中，建议使用商机培养工具(如Marketo Engage)。
* AEP的Marketo Engage目标连接器，可将受众推送到Marketo Engage进行激活，仅推送电子邮件地址和ECID。 如果联系人不存在，则不会创建新潜在客户，因此需要将用户档案和潜在客户数据引入Marketo Engage。

## 相关文档

* [B2B版Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)
* [Adobe Experience Platform    ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [Marketo Engage](https://experienceleague.adobe.com/docs/marketo/using/home.html?lang=en)
* [Adobe Experience Platform - Marketo源连接器](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=zh-Hans)
* [Adobe Experience Platform - Marketo目标连接器](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-cloud-segment-to-a-marketo-static-list.html?lang=en)