---
title: Journey Optimizer 与 Adobe Campaign Blueprint
description: 演示如何将 Adobe Journey Optimizer 与 Adobe Campaign 结合使用，通过 Campaign 中的实时消息传送服务器在本地发送消息
solution: Journey Optimizer, Campaign, Campaign v8, Campaign Classic v7, Campaign Standard
exl-id: 076446a9-dfb9-464c-a04f-6864b8cb7b48
source-git-commit: 6901596cbb661ffa8cf57c6ae958db1978bf1520
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Journey Optimizer 与 Adobe Campaign

演示如何将 Adobe Journey Optimizer 与 Adobe Campaign 结合使用，通过 Campaign 中的实时消息传送服务器在本地发送消息。

<br>

## 架构

<img src="assets/ajo-campaign-architecture.svg" alt="参考架构 Journey Optimizer Blueprint" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>可以同时使用 Journey Optimizer 和 Campaign 来彼此独立地发送消息，但需要考虑一些技术注意事项。如果您希望遵循此路线，请与售前企业架构师沟通，以确保您了解支持实施所需的条件。

<br>

## 先决条件

### Adobe Experience Platform

* 必须在系统中配置架构和数据集，然后才能配置 Journey Optimizer 数据源
* 对于基于体验事件类的架构，当您希望触发的事件不是基于规则的事件时，请添加“编排事件 ID 字段组”
* 对于基于个人用户档案类的架构，添加“用户档案测试详细信息”字段组，以便能够加载测试用户档案以与 Journey Optimizer 一起使用
* Journey Optimizer 和 Campaign 配置在同一 IMS 组织中

### Campaign v7/v8 或 Campaign Standard

* 实时消息传送服务（即消息中心）的执行实例必须由 Adobe 托管云服务托管
* 所有消息创作均在 Campaign 实例本身内完成

<br>

## 护栏

[Journey Optimizer 护栏产品链接](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=zh-Hans)

### 其他 Journey Optimizer 护栏

* 现在可通过 API 设置封顶，以确保目标系统不会因饱和而达到故障点。这意味着超过上限的消息会被彻底丢弃，永不发送。不支持限流。
   * 最大连接数：目标可处理的 http/s 连接的最大数
   * 最大调用数：periodInMs 参数中要进行的最大调用数
   * periodInMs：时间（以毫秒为单位）
* 区段成员资格发起的历程可以两种模式运行：
   * 批次区段（每 24 小时刷新一次）
   * 流传输区段（&lt;5 分钟资格）
* 批次区段 - 需要确保您了解合格用户的每日流量，并确保目标系统能够处理每个历程以及所有历程中的突发吞吐量
* 流式区段 - 需要确保可以处理用户档案资格的初始突发量，以及每个历程和所有历程的每日合格流传输流量
* 不支持的决策管理
* 不支持业务事件
* 出站集成到第三方系统
   * 不支持单个静态 IP，因为我们的基础架构是多租户的（必须允许列出所有数据中心 IP）
   * 自定义操作仅支持 POST 和 PUT 方法
   * 身份验证支持：令牌 |密码 | OAuth2
* 无法打包 Adobe Experience Platform 或 Journey Optimizer 的各个组件，并在各个沙盒之间移动它们。必须在新环境中重新实施

<br>

### Campaign集成

有关与特定版本的Adobe Campaign和Adobe Journey Optimizer集成的指导，请参阅每个Adobe Campaign版本的相应指南。

* [Adobe Journey Optimizer和Campaign v7](ajo-and-campaign-v7.md)
* [Adobe Journey Optimizer和Campaign v8](ajo-and-campaign-v8.md)