---
title: 购买后兴奋
description: 了解如何构建事件驱动的购买后历程，该历程会从第三方API触发包含动态跟踪详细信息的配送通知电子邮件。
doc-type: overview-page
solution: Experience Platform
exl-id: 570dc378-e7a3-4895-8f14-89d420b6b340
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%
---

# 购买后兴奋

## 先决条件

>[!WARNING]
>
>必须先完成以下实验，然后才能开始本实验

- **Postman安装程序** **—>** [Postman安装](../../postman-setup/postman-installation.md)
- **数据存储 — 操作中的关系存储** **—>** [配置文件目标Dimension](../../data-stores/relational-store-in-action/profile-target-dimension.md)
- **数据存储 — 配置电子邮件渠道 — >** [配置配置文件](../../data-stores/configure-email-channels/configure-for-profile.md)
  *（此步骤最多需要3小时才能完成）*

如果您尚未这样做，请立即完成这些步骤

>[!CAUTION]
>
>本实验需要在沙盒中向Adobe委派子域。 如果您是自学型的，还没有设置，请参阅[设置](../../setup.md)。

## Lab概述

在本视频中，您将了解购买后兴奋的使用案例如何映射到历程，浏览批判性思维问题和用于在订单发货后发送个性化配送通知的架构。

>[!VIDEO](https://video.tv.adobe.com/v/3491146/)

## 学习目标

- 构建以单一事件开始的历程
- 设置和配置自定义操作以调用第三方系统以返回历程中使用的信息
- 通过在事件有效载荷中流式传输来执行历程
- 测试和调试配置文件和历程
- 通过报告和日志验证预期体验
- 在简单的电子邮件中设置个性化设置，并查看其操作情况



## 用例描述

客户下达订单时，您需要发送包含订单详细信息的确认消息。  发送订单后，您需要触发第二条消息，其中包含从第三方API动态检索的跟踪信息。

**键标注：**

- 初始订单确认通常作为事务型消息实施，因为客户在下订单后不希望等待确认。
- 订单配送通知也可以使用事务型消息传递来实施，但它可以在历程中构建，允许自定义操作检索配送信息并增强客户通信。

>[!NOTE]
>
>在本实验中，您仅构建“已发运订单”消息并跳过“订单确认”消息。
