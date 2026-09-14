---
title: 回顾
description: 查看API建模实验室步骤，包括通过JSON修补来创建客户帐户架构、标记身份以及建立查找关系。
doc-type: article
solution: Experience Platform
exl-id: 0279cd68-af7b-43b4-8c6c-d8f8f96f0c0e
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%
---

# 回顾

以下视频概述了如何通过API调用构建架构、身份和关系描述符，并演示了如何使用JSON修补程序修改架构。

>[!VIDEO](https://video.tv.adobe.com/v/3459564/?quality=12&learn=on)

>[!SUCCESS]
>
>恭喜！ 了解其工作方式有助于您从整体上了解系统。



## 已创建客户帐户架构

您由`$ref`创建架构，其中包含Adobe创建的字段组和您自己的自定义创建的字段组（即租户）。 您还`$ref`架构要表示的类（即XDM Individual Profile）

![客户帐户架构通过$ref](assets/recap-customer-account-schema.png "客户帐户架构")引用字段组和类


## 已通过JSON修补客户帐户架构

您使用了JSON修补方法修改客户帐户架构，以向计划对象添加新字段。 为此，您应修补您在[创建自定义字段组](build-schema/create-custom-field-groups.md)中定义的名为`Customer Account Details`的`$ref`自定义字段组，而不是修补架构本身。

![JSON修补程序请求将planDescription字段添加到“客户帐户详细信息”字段组](assets/recap-json-patch-plan-description-field.png "planDescription字段的JSON修补程序")


## 已标记身份字段

要为客户帐户架构中的`_devbc.customerID`和`personalEmail.address`字段创建`Identity Descriptors`，您执行了同一`POST`调用中的两个。

1. `_devbc.customerID`字段已设置为&#x200B;**主要**&#x200B;标识
1. `personalEmail.address`字段&#x200B;**未设置**&#x200B;为主字段

![客户帐户架构显示主要和非主要标识描述符](assets/recap-marked-identity-fields.png "客户帐户架构标识字段")

## 已创建查找关系

最后一步是从XDM ERD on Paper lab中创建客户帐户与计划架构之间的关系。 这要求您在客户帐户架构上同时创建关系描述符（即如何将`Customer Account`架构与`dep: Plan [Lookup]`架构相关联）和引用身份描述符。

![关联描述符和引用标识描述符将客户帐户关联到计划查找架构](assets/recap-relationship-reference-identity-descriptors.png "关联和引用标识描述符")

>[!NOTE]
>
>`referenceIdentity`描述符告知实时客户档案`Customer Account`架构中的哪个字段与哪个身份命名空间匹配。 请记住，定义查找架构时，必须将字段标记为主要标识，并为其分配类型为`non-person`的命名空间。
