---
hold: true
title: 对象复制映射
description: 为产品阵列配置对象副本映射，然后在默认副本之上添加和删除字段级覆盖。
doc-type: article
solution: Experience Platform
exl-id: 762d0e19-ed1c-4f4d-91ec-a962bd6277a7
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---


# 对象复制映射

在此部分中，您将添加对象副本映射并创建一些覆盖。

## 直通映射

通过单击“新建字段类型”添加以下包含&#x200B;**products\[\*]**&#x200B;和&#x200B;**products\[\*].productID**&#x200B;的直通映射，并在此处为每行添加新字段。 由于ML推荐，某些可能已存在。

| Source列 | XDM列 |
| ----------------------- | ------------------------- |
| orderStatus | 事件类型 |
| lastOrderStatusUpdate | 时间戳 |
| 产品\[\*] | productListItems\ |
| 产品\[\*].productID | productListItems\[\*].SKU |

>[!NOTE]
>
>请注意，**products\[\*]**&#x200B;正在对象字段之间执行1-1字段映射，并且显式字段映射&#x200B;**products\[\*].productID**&#x200B;正在覆盖默认副本。

>[!NOTE]
>
>除&#x200B;**productListItems\[\*].\_id**&#x200B;外，**products\[\*].productID**&#x200B;还映射到&#x200B;**productListItems\[\*].SKU**。 这是单个输入字段映射到XDM架构中的多个输出字段的示例。 按原样保留映射。

1. 保留映射&#x200B;**products\[\*].price**&#x200B;到&#x200B;**productListItems\[\*].priceTotal**

## 在特定字段上添加覆盖

1. 覆盖对象副本映射的方式
   1. 将&#x200B;**products\[\*].make**&#x200B;映射到&#x200B;**productListItems\[\*].\_devbc.make**
   2. 将&#x200B;**products\[\*].model**&#x200B;映射到&#x200B;**productListItems\[\*].\_devbc.model**

## 删除某些字段上的覆盖

1. 请注意，已自动填充&#x200B;**productListItems.currencyCode**&#x200B;和&#x200B;**productListItems.quantity**。
1. 删除&#x200B;**productListItems\[\*].quantity**&#x200B;和&#x200B;**productListItems\[\*].currencyCode**&#x200B;映射。
1. 覆盖不会发生，并且对象副本会接管传递字段。


## 对象副本映射、覆盖和删除的摘要

| Source列 | XDM列 | 操作 |
| -------------------------- | ----------------------------------- | -------------------------------------- |
| 产品\[\*] | productListItems\ | `Add` |
| 产品\[\*].productID | productListItems\[\*].SKU | `Add` |
| 产品\[\*].productID | productListItems\[\*].\_id | `No change` |
| products\[\*].make | productListItems\[\*].\_devbc.make | `Change` |
| products\[\*].model | productListItems\[\*].\_devbc.model | `Change` |
| products\[\*].price | productListItems\[\*].priceTotal | `No change` |
| products\[\*].quantity | 产品列表项目\[\*].quantity | `Remove` |
| products\[\*].currencyCode | productListItems\[\*].currencyCode | `Remove` |

## 验证映射

有2组映射需要验证。 删除2个映射后，您总共应具有6个映射。



![添加对象副本覆盖后productListItems的结果映射](assets/object-copy-mappings-resultant-mappings-for-productlistitems.png "ProductListItems\[*]的结果映射应如下所示")

![对象复制覆盖后productListItems的结果映射的第二个视图](assets/object-copy-mappings-resultant-mappings-for-productlistitems--2.png)
