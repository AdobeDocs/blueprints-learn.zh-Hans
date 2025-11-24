---
title: '[!DNL Journey Optimizer] - 历程Blueprint'
description: 使用 Adobe Experience Platform 作为流式传输数据、客户档案和分段的中心枢纽，执行触发的消息和体验。
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 3a3988e93dd9e92f4f564bfedfa314e8e2b5d9ba
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 15%

---

# [!DNL Journey Optimizer]蓝图

Adobe [!DNL Journey Optimizer]是基于Adobe Experience Platform构建的云原生应用程序，它支持跨多个渠道实时和计划地编排客户历程。 它支持事件驱动触发器、受众分段和决策服务，以通过电子邮件、短信、推送、Web和应用程序内消息传送提供个性化体验。 它与入站和出站系统集成，允许在整个客户生命周期中统一进行受众状态管理和情境式参与。

此Blueprint概述了应用程序的技术功能，并深入分析了构成[!DNL Journey Optimizer]的各种体系结构组件。

<br>

## 用例

>[!BEGINTABS]
>[!TAB 历程（事件驱动，实时）]

- **放弃恢复：**&#x200B;当用户通过电子邮件、推送或应用程序内放弃购物车、表单或会话时，触发个性化消息。
- **新用户注册：**&#x200B;新用户注册新帐户首选项、相关促销活动或权益后，立即与其接洽
- **事务性消息：**&#x200B;使用事件触发器发送实时确认、警报或更新（例如，已发送订单、密码重置）。
- **上下文定位：**&#x200B;根据用户的信号和位置与其即时通信，以帮助指导和引导其体验
- **上下文追加销售/交叉销售：**&#x200B;根据实时配置文件属性和最近的交互提供个性化优惠。

>[!TAB 营销活动编排（已计划，品牌启动）]

- **促销活动**：针对产品发布、季节性优惠或销售活动启动多步骤、多渠道的促销活动。
- **生命周期营销**：自动执行生日消息、续订提醒或忠诚度里程碑等循环营销活动。
- **基于受众的Funnel推送**：根据业务逻辑或CRM属性将受众细分并推送至结构化营销活动。
- **新闻稿和内容分发**：通过电子邮件和移动设备，为目标受众计划和提供个性化内容。
- **重新参与营销活动**：识别休眠用户，并根据非活动阈值将其重新引入参与流程。

>[!ENDTABS]

<br>

## 架构

<img src="images/ajo-architecture.svg" alt="参考架构Adobe Journey Optimizer Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Blueprint 场景

| 场景 | 描述 |
| :-- | :-- |
| [历程](journey-optimizer-journeys.md) | Adobe Journey Optimizer中的AJO历程是由实时事件或受众区段触发的自动个性化客户体验，允许营销人员跨电子邮件、短信和推送通知等渠道投放相关消息。 |
| [营销活动编排](journey-optimizer-campaigns.md) | AJO Campaign Orchestration使营销人员能够使用实时数据和受众分析来设计和执行个性化的跨渠道营销活动。 它支持动态定位、消息投放和历程逻辑，以优化电子邮件、短信、推送和自定义渠道中的客户参与。 |

<br>

## 集成模式

| 集成 | 描述 | 技术注意事项 |
| :-- | :-- | :-- |
| [第三方消息传递](3rd-party-messaging.md) | 演示Adobe [!DNL Journey Optimizer]如何与第三方消息传递平台集成，以编排和提供个性化的客户通信。 | <ul><li>第三方系统必须支持&#x200B;**持有者令牌身份验证**</li><li>由于多租户架构，不支持&#x200B;**静态IP**。</li><li>了解第三方系统上的&#x200B;**API速率限制**；客户可能需要购买额外容量来处理源自&#x200B;**Adobe Journey Optimizer**&#x200B;的流量。</li><li>消息有效负载或投放逻辑中不支持&#x200B;**决策管理**。</li></ul> |
| 使用Adobe Campaign v8[[!DNL Journey Optimizer] 的](../campaign-v8/ajo-and-campaign-v8.md) | 演示Adobe [!DNL Journey Optimizer]如何与Adobe Campaign v8的事务性消息传递功能集成以执行最终消息传递。 | <ul><li>消息不受限制。 每5分钟最多4,000条消息。</li><li>仅支持事件启动的历程</li><li>Campaign发送的消息不支持决策管理</li></ul> |

<br>

## 先决条件

Adobe [!DNL Experience Platform]：

- 必须先在系统中配置架构和数据集，然后才能配置[!DNL Journey Optimizer]数据源
- 对于基于XDM体验事件类的架构，当您希望触发的事件不是基于规则的事件时，请添加“Orchestration eventID”字段组
- 对于基于XDM个人资料类的架构，请添加“个人资料测试详细信息”字段组，以便能够加载测试个人资料以用于[!DNL Journey Optimizer]

<br>

电子邮件：

- 必须准备好用于消息发送的子域
- 子域可以完全委派给 Adobe（推荐），或者 CNAME 可以用于指向特定于 Adobe 的 DNS 服务器（自定义）
- 每个子域都需要 Google TXT 记录，以确保良好的传送性

<br>

移动推送：

- 客户必须拥有构建应用程序的移动开发人员
- Adobe Experience Platform Mobile SDK

<br>

## 护栏

[[!DNL Journey Optimizer] 护栏产品链接](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[护栏和端到端延迟指导](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html?lang=zh-Hans)

## 相关文档

- [[!DNL Experience Platform] 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
- [[!DNL Experience Platform] 标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
- [[!DNL Experience Platform Mobile SDK] 文档](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hans)
- [[!DNL Journey Optimizer] 文档](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hans)
- [[!DNL Journey Optimizer] 产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)