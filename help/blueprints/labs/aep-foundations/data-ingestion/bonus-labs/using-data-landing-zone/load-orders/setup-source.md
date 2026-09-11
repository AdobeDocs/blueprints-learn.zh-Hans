---
title: 设置源
description: 将历史订单JSON文件上传到数据登陆区，并配置针对订单架构的新数据流。
doc-type: article
solution: Experience Platform
exl-id: 046d50ad-687e-4cdb-a8b1-3c55ab39b68e
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# 设置源

## 上传样本文件

您需要通过Azure Storage Explorer将示例数据文件上传到您的数据登陆区，以便您可以在实验中使用它。  为此，请执行以下操作：

1. 下载[示例文件](../../../sample-files.md)
1. 将&#x200B;**Lab\_Historical\_Orders.json**&#x200B;文件拖放和/或上传到您从上面保存的数据登录区。



上传后，屏幕应类似于下面的屏幕快照。

上载到数据登陆区域的![Lab_Historical_Orders.json文件](assets/setup-source-lab-historical-orders-json-uploaded-to-dlz.png "上载到DLZ的Lab_Historical_Orders.json")

## 导航到源

1. 转到Adobe Experience Platform并导航到： **源** -> **目录** -> **云存储**
1. 单击数据登录区域的&#x200B;**设置** / **添加数据**

![导航到源>目录>云存储以设置数据登陆区域](assets/setup-source-navigate-to-data-landing-zone-source.png "源 — 数据登陆区域")

>[!NOTE]
>
>如果您已经从上一个批量摄取实验室设置了连接，则会看到&#x200B;**添加数据**&#x200B;作为默认操作



## 预览文件

1. 选择&#x200B;**Lab\_Historical\_Orders.json**&#x200B;文件并预览其内容
1. 单击屏幕右上角的&#x200B;**下一步**&#x200B;以继续下一步

![选择并预览Lab_Historical_Orders.json文件内容](assets/setup-source-select-and-preview-lab-historical-orders.png "选择并预览Lab_Historical_Orders.json文件")

## 设置数据流

1. 在数据流详细信息屏幕中，选择&#x200B;**新建数据集**
1. 将输出数据集命名为&#x200B;**订单 — YourNameHere**
1. 选择架构名称&#x200B;**dep： Orders**
1. 打开&#x200B;**配置文件数据集**&#x200B;切换框
（如果未打开此功能，则配置文件存储区将无法监视是否有新数据进入此数据集，因此不会将此数据摄取到配置文件中）
1. 打开&#x200B;**启用部分摄取**
（如果不打开此功能，则当其中一个记录出错时，摄取可能会失败）
1. 将数据流名称设置为&#x200B;**Orders - Backfill - YourNameHere**
1. 打开所有警报&#x200B;**源数据流启动/成功/失败**

为“订单”数据集配置的![数据流详细信息屏幕](assets/setup-source-dataflow-details-for-orders.png "订单的数据流详细信息")

>[!CAUTION]
>
>请确保为配置文件和部分摄取启用了&#x200B;**您的数据集**。

单击屏幕右上角的&#x200B;**下一步**&#x200B;以继续下一步
