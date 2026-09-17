---
title: 用例 #1 - Acquisition
description: 定义一个客户获取用例，以针对尚未订购或拥有设备的iPhone 14页面访客，并规划受众构建方法。
doc-type: overview-page
solution: Experience Platform
exl-id: a85b1eb1-88f4-41b2-acce-2e34dbe6aff8
source-git-commit: 8b3391d41cd4a3ea6cb52d5167e627b7f6bd2c6e
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%
---

# 用例#1 — 客户获取

## 概述

在本视频中，您将了解如何为iPhone 14客户获取用例构建受众。

>[!VIDEO](https://video.tv.adobe.com/v/3459402/?quality=12&learn=on)



**用例定义**

激活所有访问了iPhone 14产品页面，但iPhone 14订单不存在或没有活动的iPhone 14的用户档案。

>[!IMPORTANT]
>
>在启动本实验之前，请先完成[Postman设置](../../setup.md)。 您还需要访问[webhook.site](https://webhook.site/)以捕获激活的受众数据。



## 分析任务

分析以上内容并记下：

1. 您认为解决此用例需要哪些字段？
1. 评估方法是否需要流式处理？
1. 当受众中使用的事件在不同时间进入时，流会产生什么影响？
1. 我们如何知道“活跃”是什么意思？
1. 您还希望了解哪些其他信息？

**记住**：当我们从业务利益相关者那里获得要求时，他们往往是不完整的，使用其他术语并在不知晓的情况下做出假设。 你的工作就是将所有这些信息公布于众，引导他们找到可以做的事情。



## 方针

对于此用例，我们将它划分为多个受众：

1. iPhone/Pixel不存在订单
1. 无活动的iPhone/像素
1. 已访问iPhone/Pixel并且订单不存在iPhone/Pixel以及没有活动的iPhone/Pixel
