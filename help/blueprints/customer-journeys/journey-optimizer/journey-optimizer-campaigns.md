---
title: '[!DNL Journey Optimizer] — 营销活动编排'
description: 允许营销人员跨出站消息传递渠道协调基于受众的计划多步营销通信。
solution: Journey Optimizer
source-git-commit: 0a3ebcbc6029df46bd988cb8f15ecf838f80c3c9
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 2%

---

# [!DNL Journey Optimizer] — 营销活动编排Blueprint

AJO Campaign Orchestration允许营销人员跨出站渠道（如电子邮件、短信、推送和直邮）设计和执行基于受众的计划多步通信。 AJO历程使用实时客户资料中的实时数据对单个客户行为做出反应，与之不同的是，营销活动采用协调的营销方式，按计划时间间隔定位受众。 营销活动和历程结合起来提供了互补的方法 — 营销活动推动品牌参与策略，而历程提供个性化、响应式体验。

<br>

## 架构

<img src="images/ajo-campaigns-architecture.svg" alt="参考架构Adobe Journey Optimizer Campaign编排Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

### 消息执行架构

<img src="images/ajo-campaigns-message-sending-architecture.png" alt="参考架构Adobe Journey Optimizer Campaign编排Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

### 关系存储 — 数据摄取延迟

<img src="images/ajo-campaigns-data-ingestion-architecture.png" alt="参考架构Adobe Journey Optimizer Campaign编排Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 历程的体系结构注意事项

- **数据架构**： AJO Campaign Orchestration在下面使用关系数据库进行受众构建和编排
- **受众门户集成**：与实时客户配置文件中的受众门户本机集成，以便在构建营销活动时从现有受众读取并将新受众保存到
- **按需受众创建**：为紧急营销用例立即构建、评估和执行受众
- **实时客户个人资料集成：**&#x200B;同意和通信历史事实来源；支持个性化的“瘦身个人资料”设计
- **多实体消息发送：**&#x200B;能够在一次投放中为每个用户档案发送多条消息（例如，为每个预订向客户电子邮件地址发送一条消息）
- **多实体分段**：开始从关系存储中的任何实体（即产品、库存、计划等）构建受众

<br>

## 护栏

[协调的营销活动产品链接](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/guardrails)

[护栏和端到端延迟指导](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails)

<br>

## 相关文档

- [[!DNL Journey Optimizer] 协调的营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/orchestrated-campaigns-landing-page.html)
- [[!DNL Experience Platform] 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
- [[!DNL Experience Platform] 标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
- [[!DNL Experience Platform Mobile SDK] 文档](https://experienceleague.adobe.com/docs/mobile.html)
- [[!DNL Journey Optimizer] 文档](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html)
- [[!DNL Journey Optimizer] 产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)