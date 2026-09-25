---
title: Adobe Customer Journey Analytics与Adobe Journey Optimizer集成
description: 用于分析Adobe Customer Journey Analytics中的Adobe Journey Optimizer活动和历程见解以及发布受众以供历程执行的架构。
solution: Customer Journey Analytics, Journey Optimizer, Experience Platform
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%
---
# Adobe Customer Journey Analytics与Adobe Journey Optimizer集成

此架构显示了Adobe Journey Optimizer交付和交互数据如何通过Adobe Experience Platform流入Customer Journey Analytics以进行活动和历程分析。 在Customer Journey Analytics中创建的受众可以通过Real-Time CDP发布，以便在Journey Optimizer执行中使用。

## Campaign和历程分析架构

该架构将Journey Optimizer交付和交互数据与Experience Platform和Customer Journey Analytics连接起来，用于报表、分析和创建受众。

![Adobe Customer Journey Analytics和Adobe Journey Optimizer集成架构](assets/cja_ajo_integration.png){width="1000" zoomable="yes"}

## 主要数据流和集成点

- Journey Optimizer投放、交互和效果数据共享到Experience Platform数据服务。
- Experience Platform数据通过CJA连接引入Customer Journey Analytics。
- Customer Journey Analytics数据视图和分析提供campaign和journey insight。
- 在Customer Journey Analytics中创作的受众将发布到Real-Time CDP。
- Real-Time CDP受众可用于Journey Optimizer历程执行和个性化。

## 支持的用例模式

- [Customer Analytics和insight生成](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) — 分析跨渠道的营销活动和历程行为。
- [事件触发的消息传递](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) — 使用客户和历程信号支持编排的消息传递。

## 进一步阅读

- [Journey Optimizer报表](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/reporting/reports/sharing-overview)
- [Customer Journey Analytics概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-overview/cja-overview)
- [发布Customer Journey Analytics受众](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/audiences/publish)
