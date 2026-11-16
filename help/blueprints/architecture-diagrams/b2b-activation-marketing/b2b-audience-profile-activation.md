---
title: B2B Audience和Profile Activation
description: 通过Real-Time Customer Data Platform B2B edition提供基于帐户和基于人员的受众，以便在各个渠道和目标中激活。
solution: Real-Time Customer Data Platform
product_v2:
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
source-git-commit: ea991411ae0339bb4a1a36ac994fa76097d37307
workflow-type: tm+mt
source-wordcount: '1745'
ht-degree: 4%
---

# B2B Audience和Profile Activation

使用&#x200B;**Real-Time Customer Data Platform B2B edition**&#x200B;将帐户、商机和人员数据整合到统一的B2B配置文件中，然后在目标（如LinkedIn、Marketo Engage和云存储）中激活人员受众和帐户受众。 此Blueprint介绍了如何设计B2B架构、构建多实体受众，以及导出这些受众以供跨多个渠道和目标激活，以及用于在&#x200B;**Journey Optimizer B2B Edition**&#x200B;和&#x200B;**Customer Journey Analytics B2B edition**&#x200B;等应用程序中的编排和分析。

## 用例

- 创建人员受众，根据B2B数据（包括客户、机会和商机）跨渠道进行定位和个性化。
- 通过使用&#x200B;**区段数**&#x200B;方法，创建将帐户和机会级别属性与人员级别行为结合的多实体受众（例如“过去3天内访问定价页面并且是行业Y中帐户第X阶段机会决策者的人员”）。
- 将人员受众激活到受支持的Experience Platform目标以实现定位和个性化，将客户受众激活到受支持的广告和云存储目标以实现定位、销售外联和分析。 目标支持因受众类型而异；有关帐户激活的信息，请参阅[帐户受众目标](#account-audience-destinations)。

### 基于帐户的用例

- **填补购买团队的空缺：**&#x200B;构建客户受众，其中没有联系人担任CMO或CIO等职位。 将其激活到LinkedIn匹配的受众或其他支持的广告目标，然后使用目标的工作标题定位来联系这些角色中的新联系人。
- **向现有客户的其他部门追加销售或交叉销售：**&#x200B;构建一个客户受众，该受众在3到9个月前购买了产品X，但尚未拥有产品Y。将其激活到支持的广告目标或将其导出到云存储以便进行销售和营销推广。
- **使用竞争产品的目标公司：**&#x200B;使用合作伙伴或意图数据识别使用竞争对手产品的帐户，即使没有已知联系人。 将帐户受众激活到支持的广告目标以联系这些公司的联系人。

## 应用程序

- Real-Time Customer Data Platform B2B edition
- （可选） **Customer Journey Analytics B2B edition**
- （可选） **Journey Optimizer B2B Edition**

## 集成模式

此Blueprint的典型B2B集成模式包括：

- **B2B参与和CRM源RTCDP B2B →目标**

  B2B参与和CRM系统（如Marketo Engage、Salesforce和Microsoft Dynamics）使用标准B2B架构和关系将潜在客户/联系人、客户和机会发送到&#x200B;**Real-Time CDP B2B edition**。 从该位置，人员受众将激活到支持的目标，包括：

  - Marketo Engage
  - LinkedIn/LinkedIn匹配的受众
  - Google客户匹配和DV360
  - 交易台
  - Amazon Ads
  - Trade Desk CRM、Criteo、Bing和其他广告平台
  - 云存储目标，例如Amazon S3、ADLS和Snowflake，用于下游使用

  帐户受众使用相同的统一B2B数据模型，并单独激活到[帐户受众目标](#account-audience-destinations)下列出的受支持的广告和文件目标。

- **B2B意图和事件源RTCDP B2B →受众→目标**

  B2B意图和事件源（如Bombora Intent、Demandbase Intent、PathFactory和RainFocus）将流意图和参与事件置于RTCDP B2B中。 这些事件映射到标准B2B架构，并用于构建可激活到广告和营销目标的人员和帐户受众。 例如，将显示竞争对手主题意图的帐户激活到受支持的帐户目标，如Bombora和Demandbase。

可使用各种B2B数据源将客户、潜在客户、商机和人员数据映射到使用标准&#x200B;**B2B架构和关系**&#x200B;的Real-Time Customer Data Platform的B2B edition。

## 架构

![B2B Audience和Profile Activation Blueprint的参考架构](assets/b2b-audience-profile-activation.png){width="1000" zoomable="yes"}

## 帐户受众目标

可以将帐户受众激活到以下广告和云存储目标：

- LinkedIn匹配的受众
- 庞博拉
- Demandbase
- Azure数据湖存储Gen2
- 数据进入区域
- SFTP
- Azure Blob
- AWS S3

请参阅[激活帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)，了解最新支持的目标和所需的映射。 集成模式中列出的人员 — 受众目标不一定支持帐户受众。

## 护栏

在设计B2B受众和配置文件时，请参阅以下护栏和资格文档：

- [Real-Time Customer Data Platform B2B edition的护栏](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [激活帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
- [Real-Time CDP B2B edition的分段用例](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/segmentation/b2b)
- [个人资料和分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [流式分段资格标准更新](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/eligibility-criteria-update)

### 多实例和IMS组织支持

以下概述了对于映射 Experience Platform 和 Marketo Engage 实例所支持的模式。

#### Marketo作为Experience Platform的数据源

- 支持将多个Marketo Engage实例移植到一个Experience Platform实例。
- 不支持一个 Marketo Engage 实例到多个 Experience Platform 实例。
- 支持一个 Marketo Engage 实例到一个 Experience Platform 实例和多个沙箱。

#### Marketo作为Experience Platform的目标

- 支持将Experience Platform扩展到许多Marketo Engage实例。
- 支持将多个Experience Platform实例合并到一个Marketo Engage实例。

#### Experience Platform配置文件和分段护栏

请在此处查看Experience Platform配置文件和分段护栏： [配置文件和分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)。

包含B2B实体（如帐户、潜在客户或商机）的区段依赖于多实体关系，并在&#x200B;**批次**&#x200B;中进行评估。 相反，对于仅限于不包含B2B实体的人员和事件的受众，支持&#x200B;**流式分段**。 对于近实时B2B激活场景，请考虑使用批量评估的B2B受众作为支持的流受众或边缘受众的输入。

#### Experience Platform - Marketo Engage Source Connector

- 请参阅文档[此处](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)。

#### Experience Platform - Marketo目标连接器

- 请参阅文档[此处](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage-connection)。

#### 目标护栏

- 请参阅目标文档，了解有关每个目标的特定指导： [目标护栏](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)。
- 对于广告目标，如Facebook、Google Customer Match &amp; DV360、Microsoft Bing、The Trade Desk、Amazon Ads、Bombora、Demandbase等，请确保您在架构和身份策略（电子邮件、移动广告ID、地址字段、帐户ID）中选择的标识符与这些目标的映射功能和支持的身份保持一致。

## 实施步骤

有关如何实施和配置Real-Time Customer Data Platform的B2B edition的指导，请参阅Real-Time CDP B2B edition文档： [Real-Time Customer Data Platform的B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)。

两种实施模式是通用的：

- 将Marketo Engage（及其连接的CRM）中的B2B数据和配置文件摄取到RTCDP B2B edition。
- 使用相关的源连接器将B2B数据直接从CRM或其他B2B系统摄取到RTCDP B2B edition中。

在RTCDP B2B架构升级过程中，现已为B2B实体弃用以前使用的一些模式。 有关更详细的详细信息，请参阅详细文档[此处](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade)。

有关帐户受众创建和激活的信息，请参阅：

- [创建帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences?lang=en)。
- [激活帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)。
- LinkedIn匹配受众的[必需映射](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en#required-mappings)。

## 实施注意事项

关于 Blueprint 的主要注意事项和配置的指导。

- **CRM与Marketo的集成和不与**&#x200B;的集成

  - 如果实施使用Marketo Engage作为源，并且Marketo Engage已连接到CRM，则同步到Marketo的CRM数据（例如，潜在客户/联系人、帐户、机会）将通过RTCDP源连接器流入Marketo B2B edition。
  - 如果有未通过Marketo传递的其他CRM表或属性（例如，自定义对象或其他字段），请使用CRM源连接器将CRM源直接连接到Experience Platform，并将这些表映射到标准B2B架构和关系。
  - 同时设计CRM + Marketo摄取，以避免RTCDP B2B中B2B实体的表示重复或冲突，并确保所有B2B实体符合标准架构。

- **LinkedIn匹配的受众最小受众大小**

  LinkedIn匹配的受众具有最低受众规模要求（例如，300个匹配的成员）。 如果激活的帐户受众不符合要求，请先扩大受众定义以增加可匹配的受众规模，然后再启动营销活动。 有关当前要求，请参阅[LinkedIn目标文档](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin?lang=en)。

## 相关文档

- [Real-Time Customer Data Platform的B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
- [Real-Time Customer Data Platform B2B edition快速入门](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial?lang=en)
- [创建和激活帐户受众教程](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data?lang=en)
- [创建帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [激活帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
- [LinkedIn目标连接器](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin?lang=en)
- [Real-Time Customer Data Platform B2B edition的护栏](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [Real-Time Customer Data Platform B2B edition中的架构](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [架构升级到Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade)
- [Adobe Experience Platform](https://experienceleague.adobe.com/en/docs/experience-platform)
- [Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home)
- [Adobe Experience Platform - Marketo Source Connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Adobe Experience Platform - Marketo目标连接器](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-platform-segment-to-a-marketo-static-list)
- [目标护栏](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
