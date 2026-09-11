---
title: 发送事件
description: 使用Postman将模拟的Order Shipped事件直接流式传输到中心以触发历程，而不是将其发送到Edge。
doc-type: article
solution: Experience Platform
exl-id: a0f75f5a-e3b3-42a2-8547-f075a7661a22
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---


# 发送事件

## 学习目标

使用Postman发送模拟Order Shipped事件以触发历程

## 流式传输到中心与Edge

之前，我们向Edge发送了一个事件。  在某些用例中，我们可能有一个后端系统，它想要在事件中流式传输，但不需要将其发送到Edge。  本实验说明如何通过&#x200B;**将订单发送事件流式传输到集线器**（也称为服务器到服务器，例如Commerce Server到AEP，表示已发送订单）。

## 验证事件不在配置文件中

1. 转到您的&#x200B;**配置文件**&#x200B;并查找配置文件。
   - **身份命名空间** -> `email`
   - **标识值** -> `henry.creel@emailsim.io`
1. 单击&#x200B;**事件**&#x200B;选项卡。
   - 应该有&#x200B;**no** `orders.shipped`个事件

## 修改API请求

要创建API请求，您需要在API请求正文中填写以下部分。

首先，收集以下值：

### 查找帐户流端点

1. 导航到左边栏中的&#x200B;**源**，然后单击顶部导航中的&#x200B;**帐户**
1. 搜索&#x200B;**dep： HTTP API \[raw]**，突出显示该行并复制&#x200B;**流端点**&#x200B;的值并将其保存到以后可以引用的位置

![dep： HTTP API [原始]帐户行使用流式端点值高亮显示](assets/send-an-event-streaming-endpoint-account-row.png "dep： HTTP API \[原始]")


### 查找数据流ID

1. 单击&#x200B;**dep： HTTP API \[raw]**
1. 查找&#x200B;**dep： Orders (stream)**&#x200B;的记录，单击数据流链接
1. 在右边栏中，复制&#x200B;**数据流ID**&#x200B;值并将其保存到以后可引用的位置

> [!WARNING]
>
>单击行上的空格。  不要单击蓝色链接！

右侧边栏中显示的![数据流ID值](assets/send-an-event-dataflow-id-in-right-rail.png "Web数据流和数据集ID")



### 打开Postman

在计算机上启动Postman并导航到以下API调用：

- **Postman左侧边栏** —> `Collections`
- **收藏集** —> `AJO Bootcamp (Labs)`
- **文件夹** —> `Profile & Journey Labs`
- **API请求** —> `Ship Order Event`

位于Postman集合中的![订单事件请求](assets/send-an-event-open-ship-order-event-postman.png)



### 创建最终API请求

1. 将您在上一步中保存的值复制到下面高亮显示的位置。
1. 单击&#x200B;**Headers**&#x200B;并粘贴这些值（删除任何尾随空格）：
   - **红色** —> `Streaming Endpoint URL`
   - **绿色** —> `Dataflow ID`
     - 值类似于GUID（不以http开头）

> [!CAUTION]
>
>尚未执行！

![已将流端点URL和数据流ID粘贴到Postman标头](assets/send-an-event-paste-headers-in-postman.png)

## 执行API

1. 单击&#x200B;**保存**&#x200B;按钮以保存API调用
1. 单击&#x200B;**发送**&#x200B;按钮执行您的请求

成功的调用应导致以下响应……

发送Web事件后![成功响应](assets/send-an-event-successful-web-event-send.png)

## 回顾

已成功将“发运订单”事件发送到平台
