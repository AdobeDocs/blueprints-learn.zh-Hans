---
hold: true
title: 初始映射
description: 使用计算字段表达式手动映射Experience Event数据集的必需_id和时间戳字段。
doc-type: article
solution: Experience Platform
exl-id: 4052d104-bf0c-4b2d-a298-8075279aeaf8
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# 初始映射

与上一个练习一样，您将需要验证映射，并且在某些情况下需要对其进行修改。

## 验证ML推荐

1. 在“映射”步骤中，“ML推荐”会自动映射大部分属性。 但是，您也会看到多个错误。 初始屏幕可能与下面类似。

![映射屏幕将_id和时间戳显示为ML](assets/initial-mappings-id-timestamp-unmapped-fields.png "_id不推荐使用的未映射字段，时间戳是ML推荐程序不会为")生成映射的两个字段

>[!NOTE]
>
>由于我们是首次映射Experience Event数据集，请注意，对于Experience Event，默认情况下绝不推荐或映射&#x200B;**\_id**&#x200B;和&#x200B;**timestamp**。 您必须手动确保正确映射这些文件。

## 映射\_id、时间戳和顺序。\_devbc.acqSource字段

1. 要映射&#x200B;**\_id，**&#x200B;请编写以下计算字段表达式并单击“预览”

```none
concat(orderID, "-", lastOrderStatusUpdate)
```

![映射_id的计算字段，准备保存](assets/initial-mappings-calculated-field-for-id-mapping.png "映射_id的计算字段将类似于此。 单击保存以保存计算字段")

![将计算字段映射到_id属性](assets/initial-mappings-map-calculated-field-to-id.png "将计算字段映射到_id")

1. 确保目标架构中的&#x200B;**timestamp**&#x200B;字段映射到以下计算字段：

```none
lastOrderStatusUpdate
```

![时间戳映射的计算字段表达式预览](assets/initial-mappings-expression-preview.png "请编写以下表达式，然后单击“预览”。 请注意，此值区分大小写，必须按此方式完全写入")

![将计算字段表达式“inStore”映射到order._devbc.acqSource](assets/initial-mappings-map-instore-expression-to-acqsource.png)

1. 将计算字段表达式&#x200B;**&quot;inStore&quot;**&#x200B;映射到&#x200B;**order.\_devbc.acqSource**

![写入“inStore”计算字段表达式并单击“预览”](assets/initial-mappings-write-instore-expression-preview.png "写入以下表达式并单击“预览”。 请注意，此值区分大小写，必须按此方式完全写入")

## 处理重复的映射

如果映射屏幕现在抱怨存在诸如&#x200B;**orderStatus**&#x200B;等映射到&#x200B;**order.\_devbc.acqSource，**&#x200B;的重复映射，请单击“ — ”图标以删除该映射。

&#x200B;> [!NOTE]
>
>请记住，多个输入字段无法映射到同一个输出字段，因为这会使映射变得不明确。 但是，一个输入字段可以映射到XDM架构中的多个输出字段。

![映射到订单的orderStatus的映射警告重复。_devbc.acqSource](assets/initial-mappings-duplicate-mapping-warning.png "映射到订单的orderStatus的映射重复。_devbc.acqSource")



![创建计算字段后出现order._devbc.acqSource的重复映射警告](assets/initial-mappings-duplicate-mapping-for-acqsource.png "创建计算字段并已映射到该计算字段后，出现order._devbc.acqSource的重复映射。")
