---
title: Campaign v8 Blueprint、Campaign 和 Platform
description: 了解Campaign v8的蓝图。
solution: Campaign,Campaign v8
exl-id: 89b3a761-9cb3-4e01-8da0-043e634fa61f
source-git-commit: 16b233c7ea9077566ebf12238f0a87beec1c61ce
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 41%

---

# Campaign v8 Blueprint

Adobe Campaign v8 是一款针对电子邮件和直邮等传统营销渠道而构建的新一代活动工具。它提供了强大的 ETL 和数据管理功能，以帮助策划完美的营销活动。其编排引擎提供了丰富的多接触点营销计划，核心重点放在基于批次的驱动的历程。

它还与可扩展的实时消息服务器相配合，使营销团队能够根据来自任何 IT 系统的包含所有内容的有效负载发送预定义消息，以执行密码重置、订单确认、电子收据等操作。

## 用例

* 高度复杂的基于批次的消息传递程序。
* 入门培训和再营销活动.
* 直邮广告、手册和杂志活动
* 简单的事务型消息传递（如密码重置、电子邮件接收、订单确认等）。
* 将Campaign数据集成到Adobe Experience Platform以进行分析和构建用户档案。
* 将 Real-time Customer Data Platform 受众共享到 Campaign

## 架构图

了解有关[Campaign v8部署模型](https://experienceleague.adobe.com/docs/campaign/campaign-v8/config/architecture/architecture.html#ac-deployment){target="_blank"}的更多信息。

### Campaign企业(FFDA)部署

<img src="assets/P4-architecture.png" alt="Campaign v8 Blueprint的参考架构(P4)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

### Campaign v8 FDA部署

<img src="assets/P1-P3-architecture.png" alt="Campaign v8 Blueprint的参考架构(P1-P3)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## 集成模式

| 场景 | 描述 | 功能 |
| :-- | :--- | :--- |
| Adobe为 [!DNL Campaign]](rtcdp-and-campaign-v8.md)的[[!DNL Real-time Customer Data Platform]  | 展示Adobe Experience Platform及其Real-time Customer Profile和集中式分段工具如何与Adobe[!DNL Campaign]一起使用，以提供个性化的对话 | <ul><li>使用云存储文件交换和Adobe[!DNL Campaign]引入工作流从[!DNL Real-Time CDP]共享到Adobe[!DNL Campaign]的用户档案和受众 </li><li>轻松将客户对话中的投放和交互数据从Adobe[!DNL Campaign]共享回[!DNL Real-Time CDP]，以增强实时客户个人资料并提供关于消息传递营销活动的跨渠道报告</li></ul> |
| Adobe为 [!DNL Campaign]](ajo-and-campaign.md)的[[!DNL Journey Optimizer]  | 显示如何使用Adobe Journey Optimizer利用实时客户配置文件编排1:1体验，并利用本机Adobe[!DNL Campaign]事务性消息传递系统发送消息 | 利用[!DNL Journey Optimizer]的实时客户个人资料和强大功能在时刻体验中进行编排，同时利用Adobe[!DNL Campaign]的本机实时消息传送功能进行最后一英里通信<br><br>注意事项：<br><ul><li>可通过实时消息服务器每小时发送最多 100 万条消息<li>没有从[!DNL Journey Optimizer]执行限制，因此请确保由售前企业架构师进行技术审查</li><li>Campaign v8 的有效负载中不支持决策管理</li></ul> |

## 先决条件

此Blueprint存在以下先决条件。

### 应用程序服务器和实时消息服务器

* 需要Adobe[!DNL Campaign]客户端控制台才能交互和使用[!DNL Campaign] v8软件。 它是基于 Windows 的客户端，使用标准 Internet 协议（SOAP、HTTP 等）。确保您的组织中已启用分发、安装和运行软件的必要权限

* IP地址允许列表：
   * 确定所有用户在访问客户端控制台期间利用的IP范围。
   * 标识允许哪些企业系统与Real-time Messaging Server通信，并确保它们具有可以列入允许列表的静态分配IP或范围。
   * 这可以通过 Campaign 控制面板进行设置和控制。
* Sftp密钥管理：
   * 具有可用于 Campaign 提供的 sFTP 的 SSH 公钥。这可以通过 Campaign 控制面板进行设置和控制。

### 电子邮件

* 拥有可用于消息发送的子域。
* 子域可以完全委派给Adobe（推荐），也可以使用CNAME指向特定于Adobe的DNS服务器（自定义）。
* 每个子域都需要Google TXT记录以确保良好的可投放性。

### 移动推送

* 让移动设备开发人员能够部署、配置和构建移动设备应用程序。
* Adobe 仅提供一个 SDK，用于从 FCM (Android) 和 APNS (iOS) 收集必要信息，以将消息负载发送到其服务器。客户有责任对移动应用程序进行编码、部署、管理和调试。

### Web 应用程序（可选）

* 可以为Campaign托管的取消订阅和登陆页面委派额外的子域。
* 强烈建议使用SSL证书。

## 护栏

护栏如下所述。

### 应用程序服务器大小调整

* 存储可以扩展到高达2亿个配置文件，并有可能扩展到高达10亿个配置文件。
* 通过Adobe[!DNL Admin Console]设置并控制用户访问。
* 应通过批处理文件将数据加载到[!DNL Campaign]：
   * API 数据加载支持主要用于管理数据库中的用户档案或简单对象（即创建和更新）。它不适用于加载大量数据或批量操作。
   * 不支持出于自定义应用程序目的使用 API 读取数据
   * 通过 API 加载的数据将在应用程序数据库中进行暂存，然后每小时向云数据库复制一次
* 对API调用的限制适用。 在[Adobe Campaign产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}中了解详情。

### 批次消息服务器大小调整

* 可以扩展至每小时处理多达 2000 万条消息

### 实时消息服务器大小调整

* 每小时最多可发送 100 万条消息
* 默认情况下，配置两个实时消息服务器。能够扩展到最多 8 个实时消息服务器。

### 短信配置

* Campaign 提供与短信提供商集成的功能。提供商由客户采购，并与Campaign集成，用于发送基于短信的消息。
* 通过SMPP协议提供支持。
* 有三 (3) 种不同类型的短信，它们都受 Adobe 支持：
   * SMS MT（已终止移动设备）：Adobe[!DNL Campaign]通过SMPP提供商向移动电话发出的短信。
   * SMS MO（发起移动设备）：由移动设备通过SMPP提供商发送给Adobe[!DNL Campaign]的短信。
   * SMS SR（状态报告）或DR或DLR（投放回执）：移动设备通过SMPP提供商向Adobe[!DNL Campaign]发送的回执，指示已成功接收短信。 Adobe[!DNL Campaign]还可能收到指示无法传递消息的SR，通常包含错误说明。

## 实施步骤

请参阅快速入门指南，以了解[实施 Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html?lang=zh-Hans)

## 相关文档

* [Campaign v8 文档](https://experienceleague.adobe.com/docs/campaign-v8.html)
* [Campaign v8 产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Experience Platform 标记文档](https://experienceleague.adobe.com/docs/launch.html)
* [Experience Platform Mobile SDK 文档](https://experienceleague.adobe.com/docs/mobile.html)
