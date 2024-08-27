---
title: B2B帐户激活到Advertising目标和文件目标
description: 使用基于帐户的参与来创建受众并通过目标定位受众。
solution: Real-Time Customer Data Platform
source-git-commit: 074edca2f061459935d5f8b5e59e8cbd69b0fe4f
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 5%

---

# B2B帐户激活到广告目标和文件目标

通过基于帐户的参与，B2B营销人员可创建帐户受众（即公司列表），并通过LinkedIn等接受公司列表作为输入或导出到云存储目标的目标位置来定位这些公司，以进行定位和销售推广。

## 用例

通过使用基于帐户的参与，营销人员可以解锁三个关键用例：

* **填补购买团队的空白：**&#x200B;营销人员可以在尚未与CMO或CIO角色建立联系的客户上做广告。 他们可以首先在不接触标题为“CMO”或“CIO”的情况下构建客户受众，然后在LinkedIn上激活受众。 在目标位置LinkedIn内，他们随后可以发起一场营销活动，针对那些拥有“CMO”或“CIO”职称的受众和特定人员，以联系这些新联系人并突出显示他们产品的好处。
* **向现有客户公司的其他部门追加销售或交叉销售：**&#x200B;营销人员可以构建一个客户受众，该受众在3到9个月前购买了产品X，但还没有拥有产品Y。然后，他们可以激活，并向该目标受众突出产品Y的好处。
* **使用竞争产品的目标公司：**&#x200B;营销人员可以向客户推销以取代竞争对手的产品，即使这些客户没有任何联系人。 他们可以基于显示竞争对手产品的所有权或使用情况的合作伙伴数据创建帐户受众，然后通过LinkedIn激活以从目标帐户获取联系人以供扩展。

## 应用程序

* Real-time Customer Data Platform B2B 版

## 集成模式

* B2B 数据源（Marketo、Salesforce 等）-> Real-time Customer Data Platform B2B版本 — >目标。
* 各种B2B数据源可用于将客户、商机、机会和人员数据映射到Real-time Customer Data Platform的B2B版本。

## 架构

![B2B帐户Audience ActivationBlueprint的参考体系结构](assets/b2b-blueprint-account-audience-activation.png)

## 帐户受众目标

* （公司） LinkedIn匹配的受众
* 云存储目标
   * Azure数据湖
   * 数据进入区域
   * SFTP
   * Azure Blob
   * AWS S3

## 护栏

* 每个沙盒最多有50个帐户区段。
* 批次分段评估。
   * 在批量受众运行和配置文件导出作业完成后，每24小时自动评估一次。
   * 不支持边缘、流或临时评估。
* 帐户属性可用于导出。
* 人们的事件。
   * 事件回顾时间最长为30天，不为事件谓词排序。
   * AND/OR受支持(因此您可以说“A和B必须发生”，  但是你不能说“A必须在B之前3天发生”)。
* 对于云存储目标，导出计划支持“区段评估后”选项。
* [B2B配置文件和分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)。

## Real-time Customer Data Platform B2B版本、帐户受众创建和激活的实施步骤

* 有关Real-time Customer Data Platform B2B版本的实施步骤，请参阅[Real-time Customer Data Platform B2B版本快速入门](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)文档。
* 有关帐户受众创建步骤，请参阅[帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences)文档。
* 有关帐户Audience Activation步骤，请参阅[激活帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences)文档。
   * [（公司） LinkedIn所需的映射与受众目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences#required-mappings)匹配。

## 实施注意事项

linkedIn匹配的受众有几项要求，包括最低受众规模为300个匹配的成员。 如果为公司链接的匹配受众目标激活的帐户受众不符合要求，则需要修改受众定义以增加受众规模，从而启动LinkedIn促销活动。

## 相关文档

* [Real-time Customer Data Platform B2B 版](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [创建并激活帐户受众教程视频](https://experienceleague.adobe.com/zh-hans/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data)
* [创建帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences)
* [激活帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences)
* [Adobe Experience Platform - LinkedIn目标连接器](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
