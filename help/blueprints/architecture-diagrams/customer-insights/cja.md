---
title: Customer Journey Analytics与实时客户数据平台
description: 在 Customer Journey Analytics 中统一并分析整个客户历程中的数据和客户行为，将受众从 CJA 发布到 RTCDP
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
TQID: https://experienceleague.adobe.com/gbNXsco0cQIcn5O83ofB-rb0PF65v7kaTZ7mTngqHks
product_v2:
  - id: e98b7246-966c-4318-9e95-cad2f7a17dc7
    internal-label: Customer Journey Analytics
feature_v2:
  - id: ce577701-5b9e-4fe4-8fa3-4eedea976da4
    internal-label: Components
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 8%
---

# Adobe Customer Journey Analytics

Adobe Customer Journey Analytics将客户交互数据从Adobe Experience Platform和其他来源统一到基于历程的分析服务中。 此架构提供了跨渠道分析、B2B CJA派生以及将CJA受众发布到Real-Time CDP的核心参考。

## Customer Journey Analytics架构

此图显示了客户交互数据流入Customer Journey Analytics的核心流程，用于连接、数据视图、分析和受众创建。

![Adobe Customer Journey Analytics核心架构](assets/cja.png){width="1000" zoomable="yes"}

## 架构派生

- B2B Customer Journey Analytics扩展了核心架构，添加了帐户、商机、购买组和人员维度，以便进行基于帐户的分析。
- CJA受众共享会将从Customer Journey Analytics创建的受众发布到Real-Time CDP，以供激活和下游旅程执行。

## 主要数据流和集成点

- 客户交互数据从Web、移动、商务、CRM和其他来源收集到Adobe Experience Platform中。
- 在Customer Journey Analytics连接中选择Experience Platform数据集。
- 数据视图公开用于跨渠道分析的量度、维度和计算字段。
- Customer Journey Analytics受众可发布到Real-Time CDP以供激活。
- Customer Journey Analytics分析可以通过专门的集成架构与Journey Optimizer结合使用。

## 支持的用例模式

- [B2B分析](/help/blueprints/use-case-patterns/b2b/account-analytics.md) — 分析具有B2B维度的帐户、机会和人员级别历程。
- [客户分析和insight生成](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) — 分析跨渠道行为并生成历程见解。

## 进一步阅读

- [Customer Journey Analytics概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Customer Journey Analytics连接](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [发布Customer Journey Analytics受众](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
