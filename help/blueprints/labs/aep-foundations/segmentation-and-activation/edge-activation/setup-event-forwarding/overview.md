---
hold: true
title: 设置事件转发
description: 了解事件转发如何使用属性、数据元素、规则和数据流将边缘事件转发到第三方端点。
doc-type: overview-page
solution: Experience Platform
exl-id: da3d1c7f-3642-4de7-a297-fc36d09e7336
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# 设置事件转发

事件转发位于Edge上，允许我们创建一组规则和光转换以将事件发送到任何端点。

在此步骤中，我们将向webhook转发我们发送到Edge的所有活动。 webhook将充当第三方的代理，并让我们能够查看正在发生的情况。

要进行配置，我们将设置：

- 一个属性，包含决定转发内容和转发位置所需的所有扩展、数据元素和规则
  - 数据元素，引用传入事件或根据需要将其解析为多个单独的组件
  - 用于添加任何有关转发内容、转换有效负载以及发送位置的条件的规则
- 一种数据流，可配置将利用它的服务（如事件转发和AEP）
  - 发送到这些数据流的数据随后可以根据配置的服务采取操作（例如，转发事件并将数据发送到数据集）
