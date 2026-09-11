---
title: 验证已摄取的事件
description: 确认某个订单发运事件已摄取到配置文件中，并符合预期受众的条件。
doc-type: article
solution: Experience Platform
exl-id: c04397dd-8b5c-48a8-82b5-78188b8374f1
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# 验证已摄取的事件

## 学习目标

确认该事件已成功引入Adobe Experience Platform。

## 验证配置文件中的事件

1. 转到您的&#x200B;**个人资料**&#x200B;并查找您的个人资料，以查看该事件已摄取到个人资料中。  以秒为单位显示。
   - **身份命名空间** -> `email`
   - **标识值** -> `henry.creel@emailsim.io`
2. 单击&#x200B;**事件**&#x200B;选项卡。 查找`orders.shipped`事件。

![orders.shipped事件显示在配置文件的“事件”选项卡上](assets/validate-event-ingested-orders-shipped-event.png)

>[!WARNING]
>
>您是否收到任何&#x200B;**message.feedback**&#x200B;事件。  这些规则来自历程，通常表示失败或排除。  单击这些图标并查看`reason`。
>
>您可能会在生产中遇到的一些示例可能是：
>
>- EmailNoAddressFoundInProfile（您尝试向没有电子邮件的用户档案发送电子邮件）
>- EmailNoConsent (您尝试向同意设置为no的用户档案发送电子邮件。



3. 验证配置文件是否符合&#x200B;**受众**&#x200B;的条件（可能需要几分钟）。
   - 任何活动Edge（15分钟内）
   - 任何事件流（15分钟内）

![配置文件符合任何活动Edge和任何活动流受众的条件](assets/validate-event-ingested-profile-qualified-audiences.png)



## 尝试使用您自己的电子邮件

现在您已验证配置文件已登录，请使用自己的电子邮件发送一些订单发运事件。

1. 返回Postman，查找&#x200B;**发货订单事件**
2. 单击&#x200B;**正文**&#x200B;并将&#x200B;**电子邮件地址**&#x200B;更改为您的电子邮件地址。

![在Postman请求正文中更改的电子邮件地址](assets/validate-event-ingested-change-email-in-postman-body.png)

3. **保存**&#x200B;并点击&#x200B;**发送**。
4. 返回步骤1-3并使用您的电子邮件地址进行验证。

## 回顾

事件会显示在配置文件存储中，并且配置文件现在是正在查找该事件的受众的一部分。
