---
title: Campaign v8 Blueprint、Campaign 和 Platform
description: Adobe Campaign v8 是一款针对电子邮件和直邮等传统营销渠道而构建的新一代活动工具。它提供了强大的 ETL 和数据管理功能，以帮助策划完美的营销活动。其编排引擎提供丰富的多接触点营销计划，其核心重点是基于批次的驱动历程。它还与可扩展的实时消息服务器相配合，使营销团队能够根据来自任何 IT 系统的包含所有内容的有效负载发送预定义消息，以执行密码重置、订单确认、电子收据等操作。
solution: Campaign,Campaign v8
exl-id: 89b3a761-9cb3-4e01-8da0-043e634fa61f
source-git-commit: ac6e27e88854f5a05a7ff7428cd4375b3532f632
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 95%

---

# Campaign v8 Blueprint

Adobe Campaign v8 是一款针对电子邮件和直邮等传统营销渠道而构建的新一代活动工具。它提供了强大的 ETL 和数据管理功能，以帮助策划完美的营销活动。其编排引擎提供丰富的多接触点营销计划，其核心重点是基于批次的驱动历程。它还与可扩展的实时消息服务器相配合，使营销团队能够根据来自任何 IT 系统的包含所有内容的有效负载发送预定义消息，以执行密码重置、订单确认、电子收据等操作。

<br>

## 用例

* 高度复杂的基于批处理的消息传递程序
* 入门培训和再营销活动
* 直邮广告、手册和杂志活动
* 简单事务型消息传递（即密码重置、电子邮件接收、订单确认等）
* 将 Campaign 数据集成到 Adobe Experience Platform 以进行分析和构建用户档案
* 将 Real-time Customer Data Platform 受众共享到 Campaign

<br>

## 架构图

在中了解有关Campaign v8部署模型的更多信息 [此页面](https://experienceleague.adobe.com/docs/campaign/campaign-v8/config/architecture/architecture.html#ac-deployment){target="_blank"}.

### Campaign Enterprise (FFDA)部署

<img src="assets/P4-architecture.png" alt="Campaign v8 Blueprint的参考架构(P4)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />


### Campaign v8 FDA部署

<img src="assets/P1-P3-architecture.png" alt="Campaign v8 Blueprint的参考架构(P1-P3)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 集成模式

| 场景 | 描述 | 功能 |
| :-- | :--- | :--- |
| [Real time Customer Data Platform 与 Adobe Campaign](rtcdp-and-campaign-v8.md) | 显示如何将 Adobe Experience Platform 及其实时客户档案和集中化分段工具与 Adobe Campaign 结合使用来提供个性化对话 | <ul><li>使用云存储文件交换和 Adobe Campaign 摄入工作流，将用户档案和受众从 Real-Time CDP 共享到 Adobe Campaign </li><li>将客户对话中的传送和交互数据轻松共享回 Adobe Campaign 的 Real-Time CDP，以增强实时客户档案并提供有关消息传递营销活动的跨渠道报告</li></ul> |
| [Journey Optimizer 与 Adobe Campaign](ajo-and-campaign.md) | 显示如何使用 Adobe Journey Optimizer 利用实时客户档案编排 1:1 体验，并利用本机 Adobe Campaign 事务型消息传递系统来发送消息 | 利用实时客户档案和 Journey Optimizer 的强大功能编排即刻体验，同时利用 Adobe Campaign 的本机实时消息传递功能进行最后一英里通信<br><br>注意事项：<br><ul><li>可通过实时消息服务器每小时发送最多 100 万条消息<li>不会从 Journey Optimizer 执行限流，因此请确保售前企业架构师进行技术审查</li><li>Campaign v8 的有效负载中不支持决策管理</li></ul> |

<br>

## 先决条件


### 应用程序服务器和实时消息服务器

* 需要 Adobe Campaign 客户端控制台才能使用 Campaign v8 软件并与之交互。它是基于 Windows 的客户端，使用标准 Internet 协议（SOAP、HTTP 等）。确保您的组织中已启用分发、安装和运行软件的必要权限

* IP 地址允许列表
   * 识别所有用户在访问客户端控制台期间将利用的 IP 范围
   * 确定允许哪些企业系统与实时消息服务器进行通信，并确保它们具有您可以允许列出的静态分配的 IP 或范围
   * 可以通过 Campaign 控制面板设置和控制该设置
* sFTP 密钥管理
   * 具有可用于 Campaign 提供的 sFTP 的 SSH 公钥。这可以通过 Campaign 控制面板进行设置和控制。

### 电子邮件

* 准备好子域以用于消息发送
* 子域可以完全委派给 Adobe（推荐），或者 CNAME 可以用于指向特定于 Adobe 的 DNS 服务器（自定义）
* 每个子域都需要 Google TXT 记录，以确保良好的传送性

### 移动推送

* 让移动开发人员可以部署、配置和构建移动应用程序
* Adobe 仅提供一个 SDK，用于从 FCM (Android) 和 APNS (iOS) 收集必要信息，以将消息负载发送到其服务器。客户有责任对移动应用程序进行编码、部署、管理和调试

### Web 应用程序（可选）

* 可以为托管的 Campaign 取消订阅和登陆页面委派其他子域
* 强烈建议使用 SSL 证书

<br>

## 护栏

### 应用程序服务器大小调整

* 存储容量可扩展到 2 亿个用户档案，并且有可能扩展到 10 亿个用户档案
* 通过 Adobe Admin Console 设置和控制用户访问权限
* 数据加载到 Campaign 的操作应通过批次文件完成
   * API 数据加载支持主要用于管理数据库中的用户档案或简单对象（即创建和更新）。它不适用于加载大量数据或批量操作。
   * 不支持出于自定义应用程序目的使用 API 读取数据
   * 通过 API 加载的数据将在应用程序数据库中进行暂存，然后每小时向云数据库复制一次
* 对API调用的限制适用。 在中了解详情 [Adobe Campaign产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

### 批次消息服务器大小调整

* 可以扩展至每小时处理多达 2000 万条消息

### 实时消息服务器大小调整

* 每小时最多可发送 100 万条消息
* 默认情况下，配置两个实时消息服务器。能够扩展到最多 8 个实时消息服务器。

### 短信配置

* Campaign 提供与短信提供商集成的功能。提供商由客户采购，并与营销活动集成，用于发送基于短信的消息
* 支持通过 SMPP 协议实现
* 有三 (3) 种不同类型的短信，它们都受 Adobe 支持：
   * 短信 MT（到达移动设备）：由 Adobe Campaign 通过 SMPP 提供商向移动电话发出的短信。
   * SMS MO（来自移动设备）：由移动设备通过 SMPP 提供商发送到 Adobe Campaign 的短信。
   * 短信 SR（状态报告）、DR 或 DLR（传送收据）：移动设备通过 SMPP 提供商发送到 Adobe Campaign 的回执，指示短信已成功接收。Adobe Campaign 可能还会收到指示无法发送消息的 SR，通常包含错误描述。

## 实施步骤

请参阅快速入门指南，以了解[实施 Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html?lang=zh-Hans)


## 相关文档

* [Campaign v8 文档](https://experienceleague.adobe.com/docs/campaign-v8.html)
* [Campaign v8 产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Experience Platform 标记文档](https://experienceleague.adobe.com/docs/launch.html)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html)
