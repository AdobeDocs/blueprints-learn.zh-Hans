---
title: Campaign v8 Blueprint
description: Adobe Campaign v8是新一代活动工具，专为电子邮件和直邮等传统营销渠道构建。 它提供了强大的ETL和数据管理功能，以帮助策划和策划完美的营销活动。 其编排引擎提供丰富的多接触点营销计划，其核心重点是基于批处理的驱动历程。  它还与可扩展的实时消息传送服务器相配对，该服务器使营销团队能够根据来自任何IT系统的包含所有内容的有效负载发送预定义的消息，以便进行密码重置、订单确认、电子收据等操作。
solution: Campaign v8
hidefromtoc: true
exl-id: f754d099-6842-4759-8e27-6a06d5d8c2e9
source-git-commit: 13f750c0ff820ab01ed4fc615aba864bc2dc7b75
workflow-type: tm+mt
source-wordcount: '1084'
ht-degree: 3%

---

# Campaign v8 Blueprint

Adobe Campaign v8是新一代活动工具，专为电子邮件和直邮等传统营销渠道构建。 它提供了强大的ETL和数据管理功能，以帮助策划和策划完美的营销活动。 其编排引擎提供丰富的多接触点营销计划，其核心重点是基于批处理的驱动历程。  它还与可扩展的实时消息传送服务器相配对，该服务器使营销团队能够根据来自任何IT系统的包含所有内容的有效负载发送预定义的消息，以便进行密码重置、订单确认、电子收据等操作。

<br>

## 用例

* 高度复杂的基于批处理的消息传递程序
* 入门培训和再营销活动
* 直邮广告、手册和杂志活动
* 简单事务型消息传递（即密码重置、电子邮件接收、订单确认等）

<br>

## 架构

<img src="assets/campaign-v8-architecture.svg" alt="Campaign v8 Blueprint的参考架构" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Blueprint方案

| 场景 | 描述 | 功能 |
| :-- | :--- | :--- |
| [Journey Optimizer与Adobe Campaign](ajo-and-campaign.md) | 显示如何使用Adobe Journey Optimizer利用实时客户资料编排1:1体验，并利用本机Adobe Campaign事务型消息传递系统来发送消息 | 利用Journey Optimizer的实时客户资料和强大的功能，在时刻体验中进行编排，同时利用Adobe Campaign的本机实时消息传送功能进行最后一英里通信<br><br>注意事项：<br><ul><li>可通过实时消息服务器每小时发送最多100万条消息<li>不会从Journey Optimizer执行限制，因此请确保售前企业架构师进行技术审查</li><li>offer decisioning在有效负载到Campaign v8中不受支持</li></ul> |

<br>

## 先决条件


### 应用程序服务器和实时消息服务器

* 需要Adobe Campaign客户端控制台才能与Campaign v8软件进行交互和使用。 它是基于Windows的客户端，使用标准Internet协议（SOAP、HTTP等）。 确保您的组织中已启用分发、安装和运行软件的必要权限

* IP地址允许列表
   * 识别所有用户在访问客户端控制台期间将利用的IP范围
   * 确定允许哪些企业系统与实时消息服务器进行通信，并确保它们具有静态分配的IP或范围，您可以允许列表
   * 可以通过Campaign控制面板设置和控制该设置
* sFTP密钥管理
   * 具有可用于Campaign提供的sFTP的SSH公钥。 这可以通过Campaign控制面板进行设置和控制。

### 电子邮件

* 准备好子域以用于消息发送
* 子域可以完全委派给Adobe（推荐），或者CNAME可以用于指向特定于Adobe的DNS服务器（自定义）
* 每个子域都需要Google TXT记录，以确保良好的可交付性

### 移动推送

* 让移动设备开发人员可以部署、配置和构建移动设备应用程序
* Adobe仅提供一个SDK，用于从FCM(Android)和APNS(iOS)收集必要信息，以将消息负载发送到其服务器。 客户有责任对移动设备应用程序进行编码、部署、管理和调试

### Web应用程序（可选）

* 可以为托管的Campaign取消订阅和登陆页面委派其他子域
* 强烈建议使用SSL证书

<br>

## 护栏

### 应用程序服务器大小调整

* 存储容量可缩放到2亿个配置文件，并且有可能扩展到1B个配置文件
* 通过Adobe Admin Console设置和控制用户访问权限
* 数据加载到Campaign的操作应通过批处理文件完成
   * API数据加载支持主要用于管理数据库中的配置文件或简单对象（即创建和更新）。 它不适用于加载大量数据或批量操作。
   * 不支持出于自定义应用程序目的使用API读取数据
   * 通过API加载的数据将在应用程序数据库中进行暂存，然后每小时复制一次到云数据库
* API调用按比例限制为每秒15次或每天15万次

### 批量消息传送服务器大小调整

* 可以扩展以每小时处理多达2000万条消息

### 实时消息服务器大小调整

* 每小时最多可发送100万条消息
* 默认情况下，仅配置一(1)个实时消息服务器。 这是为了确保与服务器的任何通信都通过会话令牌完成，该令牌将在24小时后过期
* 您可以选择部署多达八(8)台实时消息传送服务器，但身份验证则仅支持用户/通过
* 推荐的方法始终是尽可能利用一个实时消息服务器来利用基于会话令牌的身份验证

### 短信配置

* Campaign提供与短信提供商集成的功能。 提供商由客户采购，并与营销活动集成，用于发送基于短信的消息
* 支持通过SMPP协议实现
* 有三(3)种不同类型的短信，所有Adobe都可以支持：
   * 短信MT（已终止移动设备）：由Adobe Campaign通过SMPP提供商向移动电话发出的短信。
   * SMS MO（来自移动设备）：由移动设备通过SMPP提供商发送到Adobe Campaign的短信。
   * 短信SR（状态报告）、DR或DLR（投放收据）：移动设备通过SMPP提供商发送到Adobe Campaign的回执，指示短信已成功接收。 Adobe Campaign可能还会收到指示无法发送消息的SR，通常包含错误描述。

### 移动推送配置

* Campaign v8仅支持Campaign SDK。 联系Adobe客户关怀以获取访问权限
* 请按照 [Campaign SDK文档](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=en) 了解如何安装和配置SDK

   >[!IMPORTANT]
   >其他Experience Cloud应用程序将需要使用Experience PlatformMobile SDK进行数据收集。 这是不同的SDK，需要在Campaign SDK的一侧安装

<br>

## 实施步骤

请参阅入门指南，以了解 [实施Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html?lang=en)


## 相关文档

* [Campaign v8文档](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=en)
* [Campaign v8产品说明](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Experience Platform 标记文档](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hans)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
