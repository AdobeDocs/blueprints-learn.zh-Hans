---
title: 多渠道消息编排蓝图
description: 跨屏幕提供及时的个性化客户体验。
solution: Experience Platform
kt: null
thumbnail: null
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---


# 多渠道消息编排蓝图

多渠道消息编排蓝图显示了各品牌如何通过电子邮件、短信和移动警报等渠道主动与客户互动并与其通信。

业务流程工具可以与其他交互渠道(如入站渠道)集成，通过与其他渠道的决策引擎共享受众状态，实现Web和移动个性化。 各种因素有助于确定要使用的应用程序和部署选项，例如客户交互是基于触发器还是已计划，定位和个性化需要哪些数据，等等。 这些因素导致在构建消息编排功能时出现各种可能的情况和部署选项。

## 场景


| 方案 | 说明 | Experience Cloud应用程序 |
|---|---|---|
| **批处理和交易消息** | <ul><li>创作和执行计划和批处理出站活动</li><li>提供事务性消息</li></ul> | <ul><li>Adobe Campaign Classic和Managed Services</li><li>Adobe Campaign Standard</li></ul> |
| **[批处理消息和Adobe Experience Platform](batch-messaging.md)** | <ul><li>使用Adobe Experience Platform作为客户用户档案和细分的中心，执行计划消息和批量消息活动</li></ul> | <ul><li>实时客户数据平台</li><li>Adobe Campaign Classic、Managed Services或Campaign Standard</li><li>支持的第三方消息传递提供商</li></ul> |
| **[触发式消息和Adobe Experience Platform](triggered-messaging.md)** | <ul><li>使用Adobe Experience Platform作为流数据、客户用户档案和细分的中心枢纽，通过Journey Orchestration进行流旅程安排和消息投放，执行触发式和流式消息传递</li></ul> | <ul><li>Adobe Experience Platform</li><li>Journey Orchestration</li><li>Adobe Campaign或其他第三方应用程序，用于消息投放</li></ul> |
