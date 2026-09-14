---
title: 旗舰手机发布
description: 在旗舰手机发布后，获取构建针对客户持有人和单独线路的编排营销活动的概述，以及短信升级选件。
doc-type: overview-page
solution: Experience Platform
exl-id: 04c509f1-aa10-4d29-aa59-5e627b79e498
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%
---

# 旗舰手机发布

## 先决条件

>[!WARNING]
>
>必须先完成以下实验，然后才能开始本实验

- **Postman安装程序** **—>** [Postman安装](../../postman-setup/postman-installation.md)
- **数据存储 — 操作中的关系存储** **—>** [配置文件目标Dimension](../../data-stores/relational-store-in-action/profile-target-dimension.md)
- **数据存储 — 配置电子邮件渠道 — >** [为关系配置](../../data-stores/configure-email-channels/configure-for-relational.md)
  *（此设置步骤最多需要3小时才能完成）*

如果您尚未完成这些实验，请立即完成后再继续。

>[!CAUTION]
>
>本实验需要在沙盒中使用SMS凭据来完成配置SMS渠道步骤 — 不发送实际消息，但必须存在Twilio凭据。 如果您已自学，但尚未配置这些项，请参阅[设置](../../setup.md)。

## Lab概述

在此视频中，您将了解旗舰手机发布用例如何映射到编排的营销活动，在构建面向客户所有者和个人营销活动之前，重述关键思维问题和架构。

>[!VIDEO](https://video.tv.adobe.com/v/3486217/)

## 学习目标

- 使用各种工作流活动构建编排的营销活动
- 使用构建受众活动构建受众
- 了解如何设置短信渠道
- 将受众保存到受众门户
- 通过电子邮件和短信消息定位客户帐户和各个行



## 用例描述

紧随制造商最新旗舰设备发布后，向帐户持有人和系列用户发送一条有针对性的消息，邀请他们升级到最新的移动技术。

**键标注：**

- 将所有客户行的受众保存到受众门户
- 通过消息定向单个行和帐户持有者（您将使用短信）

>[!NOTE]
>
>此方案模拟&#x200B;**电信合同升级促销活动**，其中辅助（相关）线路接收定向升级消息。
