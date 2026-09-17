---
title: Edge激活
description: 了解Edge、流和批量激活速度的差异，并预览用于创建边缘区段和配置事件转发的实验室步骤。
doc-type: overview-page
solution: Experience Platform
exl-id: 9ecadff9-3838-4cd4-93b1-7c23a232f84c
source-git-commit: 8b3391d41cd4a3ea6cb52d5167e627b7f6bd2c6e
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%
---

# Edge激活

## 激活速度回顾

Adobe具有三种激活速度，可满足不同的需求：

1. Edge
1. 流
1. 批次

我们将介绍如何使用Adobe Edge与事件转发、Edge Audiences和Edge Personalization一起激活。 然后，我们将展示如何使用从中心到Edge和外部目标的流式目标。

>[!IMPORTANT]
>
>在启动本实验之前，请先完成[Postman设置](../../setup.md)。 您还需要访问[webhook.site](https://webhook.site/)以捕获发送到外部目标的事件。

>[!NOTE]
>
>本实验不涉及批量激活。 批量激活可以按不同的时间间隔计划，并且由于时间安排，很难在实验室环境中展示而无需至少3-24小时。



## 实验室将涵盖的内容

- 创建Edge区段
- 配置事件转发
- 在Edge活动中发送
- 此触发器
  - 符合条件的Edge区段
  - Edge上的事件转发以发送到webhook
