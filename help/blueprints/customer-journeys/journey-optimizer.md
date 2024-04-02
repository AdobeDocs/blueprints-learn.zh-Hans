---
title: '"[!DNL Journey Optimizer]  — 触发的消息处理和Adobe Experience Platform Blueprint”'
description: 使用 Adobe Experience Platform 作为流式传输数据、客户档案和分段的中心枢纽，执行触发的消息和体验。
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: a1f3aef5b508575019bd651b9706efc7d6db5306
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 53%

---

# [!DNL Journey Optimizer] 蓝图

Adobe [!DNL Journey Optimizer] 是一个专门构建的系统，营销团队可以实时对客户行为做出反应，并在客户所在的位置满足他们的要求。 数据管理功能已移至Adobe [!DNL Experience Platform] 让营销团队专注于他们擅长的事：打造世界一流的客户历程和个性化的对话。

此Blueprint概述了应用程序的技术功能，并深入研究了构成这些功能的各种架构组件 [!DNL Journey Optimizer].

## 用例

* 触发式消息
* 欢迎和注册确认
* 放弃购物车和申请表
* 位置触发式消息
* 体育场内体验
* 旅游与酒店行业在抵达前和入住期间的体验

## 架构

<img src="assets/ajo-architecture.svg" alt="参考架构 Journey Optimizer Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Blueprint 场景

| 场景 | 描述 | 功能 |
| :-- | :--- | :--- |
| [第三方消息传递](3rd-party-messaging.md) | 演示如何Adobe [!DNL Journey Optimizer] 可与第三方消息传递系统一起使用，以编排和发送个性化通信 | 在客户与您的品牌或公司进行互动时，向客户提供一对一的即时个性化通信<br><br>注意事项：<br><ul><li>第三方系统必须支持用于身份验证的持有者令牌</li><li>由于是多租户架构，不支持静态 IP</li><li>当涉及每秒 API 调用数时，请注意第三方系统存在的架构性限制。客户可能需要从第三方供应商购买额外的卷，以支持来自的卷 [!DNL Journey Optimizer]</li><li>消息或有效负载中不支持决策管理</li></ul> |

<br>

## 集成模式

| 集成 | 描述 | 功能 |
| :-- | :--- | :--- |
| [[!DNL Journey Optimizer] 使用Adobe Campaign](ajo-and-campaign.md) | 显示如何使用Adobe [!DNL Journey Optimizer] 利用实时客户档案编排1:1体验，并利用本机Adobe Campaign事务性消息传递系统发送消息 | 利用的实时客户配置文件和功能 [!DNL Journey Optimizer] 在时刻体验中进行编排，同时利用Adobe Campaign的本机实时消息传送功能进行最后一英里通信<br><br>注意事项：<br><ul><li>Campaign 应用程序必须为 v7 版本 21.1 以上或 v8</li><li>消息传递吞吐量</li><ul><li>Campaign v7 - 多达每小时 5 万</li><li>Campaign v8 - 多达每小时 100 万</li><li>Campaign Standard - 多达每小时 5 万</li></ul><li>未执行限流，因此用例需要企业架构师的技术审查</li><li>不支持在 Campaign 发送的消息中利用决策管理</li></ul> |

<br>

## 先决条件

Adobe [!DNL Experience Platform]：

* 必须先在系统中配置架构和数据集，然后才能进行配置 [!DNL Journey Optimizer] 数据源
* 对于基于体验事件类的架构，当您希望触发的事件不是基于规则的事件时，请添加“编排事件 ID 字段组”
* 对于基于单个用户档案类的架构，请添加“用户档案测试详细信息”字段组，以便能够加载测试用户档案以供使用 [!DNL Journey Optimizer]

电子邮件：

* 必须准备好用于消息发送的子域
* 子域可以完全委派给 Adobe（推荐），或者 CNAME 可以用于指向特定于 Adobe 的 DNS 服务器（自定义）
* 每个子域都需要 Google TXT 记录，以确保良好的传送性

移动推送：

* 客户必须拥有构建应用程序的移动开发人员
* Adobe Experience Platform Mobile SDK

## 护栏

[[!DNL Journey Optimizer] 护栏产品链接](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html)

[护栏和端到端延迟指导](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## 相关文档

* [[!DNL Experience Platform] 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
* [[!DNL Experience Platform] 标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
* [[!DNL Experience Platform Mobile SDK] 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
* [[!DNL Journey Optimizer] 文档](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hans)
* [[!DNL Journey Optimizer] 产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)
