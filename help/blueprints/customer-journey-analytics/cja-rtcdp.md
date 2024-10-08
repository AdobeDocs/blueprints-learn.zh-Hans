---
title: 使用Real-time Customer Data Platform BlueprintCustomer Journey Analytics
description: 在 Customer Journey Analytics 中统一并分析整个客户历程中的数据和客户行为，将受众从 CJA 发布到 RTCDP
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
source-git-commit: 9fe44d93dcc05711c77ce1325b6549bb6c27a860
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 94%

---

# 使用Real-time Customer Data Platform BlueprintCustomer Journey Analytics

创建在 Customer Journey Analytics (CJA) 中识别的受众并将其发布到 Adobe Experience Platform 中的实时客户档案，以用于客户定位和个性化。非常适用于使用历史数据创建受众，或通过 Customer Journey Analytics 中的精细筛选和计算字段得出更细化的受众。

## Customer Journey Analytics 受众发布指南

请参阅以下文档，了解有关从 Customer Journey Analytics 向 Real-time Customer Data Platform 发布受众的实施和配置的指导。[文档](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=zh-Hans)

## Customer Journey Analytics 的架构 Blueprint

![架构图](assets/CJA.svg){zoomable="yes"}

## Customer Journey Analytics 护栏图 Blueprint

* 有关详细的护栏和端到端延迟，请参阅[部署护栏文档](../experience-platform/deployment/guardrails.md)

![护栏图](../experience-platform/deployment/assets/CJA_guardrails.svg){zoomable="yes"}

## 常见问题

* 如果 CJA 发送的 RTCDP 中不存在相应的用户档案，是会创建新用户档案，还是仅从 CJA 为已存在的用户档案记录受众？是，将创建新用户档案。因此，如果 RTCDP 实施仅面向已知客户，则应编写 CJA 受众规则以仅筛选具有已知身份的用户档案。这将确保在不需要时，RTCDP 用户档案计数不会因匿名用户档案而增加。

* CJA 会发送哪些标识？CJA 会发送在 CJA 配置期间已配置为“人员 ID”的标识。

* 将什么设置为主标识？用户在将 CJA 设置为主“人员”ID 时选择的任何标识。

* 标识服务是否也会处理 CJA 消息？例如，CJA 是否可以通过受众共享向用户档案标识图添加标识？不能，标识服务不处理 CJA 消息。