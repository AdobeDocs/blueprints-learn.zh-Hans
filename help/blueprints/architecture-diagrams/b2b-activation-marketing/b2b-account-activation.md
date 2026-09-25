---
title: Advertising和文件目标的B2B帐户激活
description: 使用基于帐户的参与来创建帐户受众，并将这些受众激活到广告目标和云存储。
solution: Real-Time Customer Data Platform
exl-id: 578c0019-6133-4508-ae9d-8a8a463376f0
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 1%
---

# B2B帐户激活到广告目标和文件目标

通过基于帐户的参与，B2B营销人员可以在&#x200B;**Real-Time Customer Data Platform B2B edition**&#x200B;中创建帐户受众（公司列表），并将这些帐户受众激活到广告目标（如LinkedIn Matched Audiences、Bombora和Demandbase）以及云存储目标。 这些客户受众可用于定位、销售推广和下游分析。

## 用例

通过使用基于帐户的参与，营销人员可以解锁三个关键用例：

- **填补购买团队的空白：**&#x200B;营销人员可以在尚未与CMO或CIO角色建立联系的客户上做广告。 首先，他们可以在没有联系人且标题为“CMO”或“CIO”的情况下构建客户受众，然后在LinkedIn匹配的受众或其他支持的广告目标上激活受众。 在目标位置，他们随后可以发起一场营销活动，针对具有“CMO”或“CIO”职称的受众和特定人员，以联系这些新联系人并突出显示他们产品的优势。
- **向现有客户公司的其他部门追加销售或交叉销售：**&#x200B;营销人员可以构建一个客户受众，该受众在3到9个月前购买了产品X，但还没有拥有产品Y。然后，他们可以激活此帐户受众，通过LinkedIn匹配受众、其他广告平台或用于销售和营销推广的云存储导出，向此目标受众重点展示产品Y的好处。
- **使用竞争产品的目标公司：**&#x200B;营销人员可以向客户推销以取代竞争对手的产品，即使这些客户没有任何联系人。 他们可以基于显示竞争对手产品所有权或使用情况的合作伙伴或意图数据创建帐户受众，然后通过LinkedIn匹配受众或其他支持的广告目标激活以从目标帐户获取联系人以供扩展。

## 应用程序

- Real-Time Customer Data Platform B2B edition
- （可选）Customer Journey Analytics B2B edition

## 集成模式

此Blueprint的典型集成模式包括：

- RTCDP B2B edition→的&#x200B;**B2B参与和CRM源→帐户受众→目标**

  B2B参与和CRM系统（如Marketo Engage、Salesforce和Microsoft Dynamics）使用标准B2B架构和关系将潜在客户/联系人、客户和机会发送到&#x200B;**Real-Time CDP B2B edition**。 帐户受众基于此统一的B2B数据模型构建，并激活到广告和文件目标。

- **RTCDP B2B edition→的B2B意图和事件源→帐户受众→目标**

  B2B意图和事件源（如Bombrora Intent和Demandbase Intent）将意图和参与事件发送到Experience Platform。 这些数据集被映射到标准B2B架构，允许营销人员构建帐户受众（例如，涌向竞争对手主题的帐户）并将它们激活到广告和云存储目标。 在支持的情况下，随后可以向广告合作伙伴（例如Bombora和Demandbase）激活帐户受众。

## 架构

![B2B帐户激活Blueprint的参考架构](assets/b2b-account-activation.png){width="1000" zoomable="yes"}

## 帐户受众目标

- **LinkedIn匹配的受众**
- **庞博拉**
- **Demandbase**
- **云存储目标**
  - Azure数据湖存储Gen2
  - 数据进入区域
  - SFTP
  - Azure Blob
  - AWS S3

有关支持帐户受众的最新目标列表，请参阅目标文档。

## 护栏

设计和激活帐户受众时，请参阅以下护栏：

- [Real-Time Customer Data Platform B2B edition的护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [帐户受众](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [激活帐户受众](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
- [个人资料和分段护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)
- [流式分段资格标准更新](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/eligibility-criteria-update)

## Real-Time Customer Data Platform B2B edition的实施步骤、帐户受众的创建和激活

- 有关Real-Time Customer Data Platform B2B edition的实施步骤，请参阅文档：[Real-Time Customer Data Platform B2B edition快速入门](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial?lang=en)。
- 有关帐户受众创建步骤，请参阅[帐户受众](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/account-audiences?lang=en)文档。
- 有关帐户受众激活步骤，请参阅[激活帐户受众](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)文档：

  - [LinkedIn匹配受众目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en#required-mappings)的必需映射。

## 实施注意事项

LinkedIn匹配的受众具有最低受众规模要求（例如，300个匹配的成员）。 如果激活到LinkedIn匹配受众的帐户受众不符合此要求，则您可能需要在启动营销活动之前扩大受众定义以增加可匹配的受众规模。

## 相关文档

- [B2B Audience和Profile Activation Blueprint](b2b-audience-profile-activation.md) — 父Blueprint同时涵盖人员级别和帐户级别的B2B激活。
- [Real-Time Customer Data Platform的B2B edition](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview?lang=en)
- [创建和激活帐户受众 — 教程视频](https://experienceleague.adobe.com/zh-hans/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data?lang=en)
- [创建帐户受众](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [激活帐户受众](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
- [Adobe Experience Platform - LinkedIn目标连接器](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/social/linkedin?lang=en)
- [Real-Time CDP B2B edition中的架构](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/rtcdp/schemas/b2b)
- [架构升级到Real-Time CDP B2B edition](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade)
- [目标护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/guardrails)
