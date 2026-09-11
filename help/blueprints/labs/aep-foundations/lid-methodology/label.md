---
title: 标签
description: 作为LID方法的一部分，将关系型数据仓库表标记为XDM Individual Profile、Experience Event或Lookup类。
doc-type: article
solution: Experience Platform
exl-id: 332ead7a-ca6e-4e30-bb35-8419c060c596
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# 标签

## 讲座

在本视频中，您将了解如何使用Connection 5G ERD作为示例，将关系表标记为XDM Individual Profile (P)、Experience Event (E)或Lookup (L)。

>[!VIDEO](https://video.tv.adobe.com/v/3459087/?quality=12&learn=on)



## 实验室详细信息

使用适用于单个配置文件、体验事件和查找表的相应XDM类标签，为Connection 5G数据仓库ERD和流式传输ERD中的表添加标签。

执行实验时，请牢记以下事项：

- **个人资料（特征） -**&#x200B;唯一描述个人特征（如姓名、电子邮件、地址、偏好设置等）
- **体验事件（行为） -**&#x200B;描述人员与品牌/公司的交互和接触点（例如，网页访问、购买、呼叫中心交互、应用程序提交等）
- **查找（支持） —**&#x200B;提供其他上下文信息以支持个人资料或体验事件



## 步骤1. 为XDM各个配置文件表设置标签

1. 确定在客户数据仓库ERD和客户流ERD中代表个人的所有源表。
1. 使用“**P**”标记每个表，表示它是XDM个人资料类的一部分

>[!NOTE]
>
>仅标记唯一表示个人特征的表



## 步骤2. 为XDM体验事件表设置标签

1. 识别在Connection 5G数据仓库ERD和流式传输ERD中表示个人行为的所有源表。
1. 使用“**E**”标记每个表，表示它是XDM Experience Event类的一部分。

>[!NOTE]
>
>仅标记唯一表示个人行为的表



## 步骤3. 标记XDM支持表

1. 识别所有源表，这些表表示查找数据并直接与您在Connection 5G数据仓库ERD和流式传输ERD中标记的&#x200B;**&quot;P&quot;**&#x200B;或&#x200B;**&quot;E&quot;**&#x200B;表相关。
1. 使用&#x200B;**&quot;L&quot;**&#x200B;标记每个表，表明它是非人员自定义XDM类的一部分。

>[!NOTE]
>
>查找表只能与标记为“P”或“E”的表有1个联接级别或“跃点”



## 审核

以下视频回顾了Connection 5G仓库和流ERD的正确标签，解释了为什么客户帐户、订单和账单表被按原样标记。

>[!VIDEO](https://video.tv.adobe.com/v/3459081/?quality=12&learn=on)
