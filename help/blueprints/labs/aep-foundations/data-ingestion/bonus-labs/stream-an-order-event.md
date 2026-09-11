---
title: 流式传输订单事件
description: 练习构建HTTP API流数据流，以发送示例订单事件并将其链接到现有客户个人资料。
doc-type: article
solution: Experience Platform
exl-id: 558c21d1-f9b7-489b-9153-5f10d0b8448a
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# 流式传输订单事件

## 先决条件

1. 您已下载[示例文件](../sample-files.md)并查看名为 — > **Lab\_Single\_Order\_sample.json**&#x200B;的文件
1. 您已成功完成[使用数据登录区](./using-data-landing-zone/overview.md)实验室，并具有要导入的有效映射集

## 挑战

像在上一个实验中所做的那样，执行以下一组任务。

1. 使用HTTP API源连接器创建新帐户
1. 使用新帐户设置数据流，将数据流式传输到您自己的客户订单数据集中
1. 从[使用数据登录区](./using-data-landing-zone/overview.md)实验室重新使用映射集
1. 在Postman中，使用必要的信息填充&#x200B;**创建订单事件**，以便成功流式传输数据并将其附加到您之前创建的客户帐户记录
1. 确认订单已链接到您的个人资料

> [!TIP]
>
>祝你好运，祝愿Adobe Experience Platform诸神与你同在！
