---
title: Campaign v7 Blueprint
description: Adobe Campaign v7是一款针对电子邮件和直邮等传统营销渠道而构建的活动工具。 它提供了强大的ETL和数据管理功能，以帮助策划和策划完美的营销活动。 其编排引擎提供丰富的多接触点营销计划，其核心重点是基于批处理的驱动历程。  它还与实时消息服务器相配合，使营销团队能够根据来自任何IT系统的包含所有内容的有效负载发送预定义消息，以执行密码重置、订单确认、电子收据等操作。
solution: Campaign Classic v7
exl-id: 71c808f5-59e6-4f49-a6ba-581ed508bc04
source-git-commit: 0c072465c2cac954631fe3a8dbdcef280ee397ab
workflow-type: tm+mt
source-wordcount: '1193'
ht-degree: 3%

---

# Campaign v7 Blueprint

Adobe Campaign v7是一款针对电子邮件和直邮等传统营销渠道而构建的活动工具。 它提供了强大的ETL和数据管理功能，以帮助策划和策划完美的营销活动。 其编排引擎提供丰富的多接触点营销计划，其核心重点是基于批处理的驱动历程。  它还与实时消息服务器相配合，使营销团队能够根据来自任何IT系统的包含所有内容的有效负载发送预定义消息，以执行密码重置、订单确认、电子收据等操作。

<br>

## 用例

* 基于批处理的消息传递程序
* 入门培训和再营销活动
* 直邮广告、手册和杂志活动
* 低流量的简单事务型消息传递（即密码重置、电子邮件接收、订单确认等）

<br>

## 架构

<img src="assets/campaign-v7-architecture.svg" alt="Campaign v7 Blueprint的参考架构" style="width:100%; border:1px solid #4a4a4a" />

<br>

## 集成模式

| 场景 | 描述 | 功能 |
| :-- | :--- | :--- |
| [Journey Optimizer与Adobe Campaign](ajo-and-campaign.md) | 显示如何使用Adobe Journey Optimizer利用实时客户资料编排1:1体验，并利用本机Adobe Campaign事务型消息传递系统来发送消息 | 利用Journey Optimizer的实时客户资料和强大的功能，在时刻体验中进行编排，同时利用Adobe Campaign的本机实时消息传送功能进行最后一英里通信<br><br>注意事项：<br><ul><li>可通过实时消息服务器每小时发送最多5万条消息<li>不会从Journey Optimizer执行限制，因此请确保售前企业架构师进行技术审查</li><li>offer decisioning在负载到Campaign v7实时消息服务器中不受支持</li></ul> |
| [Real-Time CDP与Adobe Campaign](rtcdp-and-campaign.md) | 展示如何将Adobe Experience Platform的Real-Time CDP及其集中分段工具与Adobe Campaign结合使用来提供个性化对话 | <ul><li>使用云存储文件交换和Adobe Campaign摄取工作流，将受众从Real-Time CDP共享到Adobe Campaign </li><li>轻松地将客户对话中的投放和交互数据共享回Adobe Campaign的Real-time CDP，以增强实时客户资料并提供有关消息传送促销活动的跨渠道报告</li></ul> |

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

* 存储可扩展到1亿个配置文件
* 通过Adobe Admin Console（推荐）或在应用程序本身本地设置和控制用户访问权限
* 数据加载到Campaign的操作应通过批处理文件完成
   * API数据加载支持主要用于管理数据库中的配置文件或简单对象（即创建和更新）。 它不适用于加载大量数据或批量操作。
   * 不支持出于自定义应用程序目的使用API读取数据
* API调用按比例限制为每秒15次或每天15万次

### 批量消息传送服务器大小调整

* 可以扩展以每小时处理多达250万条消息

### 实时消息服务器大小调整

* 每小时最多可发送5万条消息
* 默认情况下，配置两个实时消息服务器。 能够扩展到最多8个实时报文传送服务器。

### 短信配置

* Campaign提供与短信提供商集成的功能。 提供商由客户采购，并与营销活动集成，用于发送基于短信的消息
* 支持通过SMPP协议实现
* 有三(3)种不同类型的短信，所有Adobe都可以支持：
   * 短信MT（已终止移动设备）：由Adobe Campaign通过SMPP提供商向移动电话发出的短信。
   * SMS MO（来自移动设备）：由移动设备通过SMPP提供商发送到Adobe Campaign的短信。
   * 短信SR（状态报告）、DR或DLR（投放收据）：移动设备通过SMPP提供商发送到Adobe Campaign的回执，指示短信已成功接收。 Adobe Campaign可能还会收到指示无法发送消息的SR，通常包含错误描述。

### 移动推送配置

* 用于与移动设备集成推送通知的两种受支持的方法：
   * Experience PlatformMobile SDK（推荐）
   * Campaign Mobile SDK
* Experience PlatformMobile SDK路由：
   * 利用Adobe标记和Campaign Classic扩展来设置您与Experience PlatformMobile SDK的集成
   * 需要了解Adobe标记和数据收集的工作知识
   * 需要在Android和iOS中具有推送通知的移动设备开发经验来部署SDK，与FCM(Android)和APNS(iOS)集成以获取推送令牌，将应用程序配置为接收推送通知并处理推送交互
* Campaign Mobile SDK
   * 联系Adobe客户关怀以获取访问权限
   * 请按照 [Campaign SDK文档](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=en) 了解如何安装和配置SDK

   >[!IMPORTANT]
   >如果您部署Campaign SDK并正在使用其他Experience Cloud应用程序，则需要使用Experience PlatformMobile SDK进行数据收集。 这是不同的SDK，需要在Campaign SDK的一侧安装

<br>

## 实施步骤

请参阅 [入门指南](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/about-adobe-campaign-classic.html?lang=en) 实施Adobe Campaign v7


## 相关文档

* [Campaign v7文档](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hans)
* [Campaign v7产品说明](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Experience Platform 标记文档](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hans)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
