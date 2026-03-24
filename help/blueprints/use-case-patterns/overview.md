---
title: 用例模式
description: 了解用于实施Adobe Experience Platform和应用程序以实现关键业务目标的用例模式。
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
doc-type: overview-page
exl-id: 58caa6ad-0d1c-4290-9614-c68c9c9028bb
source-git-commit: 27f7e230982807ec70ca96af7f737944a6588f27
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 0%

---

# 用例模式

用例模式定义了Adobe Experience Platform和应用程序的可重复实施方法。 每种模式都描述了特定的功能、提供该功能的功能链、涉及的应用程序以及它支持的[关键业务目标](/help/blueprints/business-objectives/overview.md)。

使用下表查找与您的实施需求相匹配的模式，然后按照指向完整实施参考的链接操作，包括选项、阶段、决策指导和Experience League文档。

## Audience Building &amp; Activation

以下模式可帮助您跨渠道和目标构建、评估和激活受众区段。

| 图案 | 主要功能 | 核心解决方案 |
| --- | --- | --- |
| [目标受众激活](audience-building-activation/audience-activation-to-destinations.md) | 评估受众区段并将其发布到外部目标以进行定位或抑制 | [!DNL Real-Time CDP] |
| [受众Collaboration](audience-building-activation/audience-collaboration-segment-match.md) | 使用区段匹配在沙盒或组织之间共享和匹配受众区段 | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [事件转发](audience-building-activation/event-forwarding.md) | 将通过Edge Network收集的实时事件数据转发到非Adobe目标 | [!DNL Experience Platform] （Edge Network，事件转发） |
| [B2B受众激活](audience-building-activation/b2b-audience-activation.md) | 跨Web、电子邮件和广告渠道激活基于帐户的B2B受众 | [!DNL Real-Time CDP] B2B edition |

## 个性化

以下模式可以跨Web和应用程序表面为已知和未知访客提供量身定制的体验。

| 图案 | 主要功能 | 核心解决方案 |
| --- | --- | --- |
| [匿名访客Web个性化](personalization/anonymous-visitor-web-personalization.md) | 根据会话中行为信号为未识别的访客提供个性化内容 | [!DNL Journey Optimizer] （Web渠道），[!DNL Real-Time CDP] |
| [已知访客的Web/应用程序个性化](personalization/known-visitor-web-app-personalization.md) | 根据实时用户档案和区段会员资格为已识别的访客提供个性化内容、优惠或促销 | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Offer Decisioning](personalization/offer-decisioning.md) | 使用集中式决策逻辑跨渠道为用户档案选择下一个最佳优惠或内容 | [!DNL Journey Optimizer] （决策），[!DNL Real-Time CDP] |
| [行为推荐](personalization/behavioral-recommendation.md) | 使用选择策略和排名模型生成项目和内容推荐 | [!DNL Journey Optimizer] （决策），[!DNL Real-Time CDP] |

## 营销活动管理和编排

以下模式涵盖跨渠道的计划消息投放、触发消息投放和多步消息投放。

| 图案 | 主要功能 | 核心解决方案 |
| --- | --- | --- |
| [批量出站消息激活](campaign-management-orchestration/batch-outbound-message-activation.md) | 评估受众，然后在单个批量执行中投放计划的出站消息 | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [事件触发的消息传递](campaign-management-orchestration/event-triggered-messaging.md) | 监听实时行为或系统事件，然后将上下文消息交付给触发的用户档案 | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [多步协调历程](campaign-management-orchestration/multi-step-orchestrated-journey.md) | 通过等待、条件和多个消息操作，引导用户档案完成分支式多点接触历程 | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [具有决策的跨渠道历程](campaign-management-orchestration/cross-channel-journey-with-decisioning.md) | 编排包含实时决策的多步历程，以选择最佳渠道、内容或选件 | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [购买基于群组的营销和历程管理](campaign-management-orchestration/buying-group-based-marketing.md) | 开发客户级别的历程，使潜在客户有资格加入购买群体，以提高B2B营销效率 | [!DNL Journey Optimizer] B2B edition，[!DNL Real-Time CDP] B2B edition |

## 分析

以下模式支持跨渠道行为和性能分析。

| 图案 | 主要功能 | 核心解决方案 |
| --- | --- | --- |
| [客户分析和insight生成](analysis/customer-analytics-insight-generation.md) | 构建跨渠道分析工作区、计算指标和功能板，以进行行为和性能分析 | [!DNL Customer Journey Analytics], [!DNL Experience Platform] |
| [B2B分析](analysis/b2b-analytics.md) | 在跨渠道客户历程分析中包含B2B帐户级别信息 | [!DNL Customer Journey Analytics] B2B edition，[!DNL Real-Time CDP] B2B edition |

## 对话体验

以下模式支持在数字资产上进行AI支持的品牌安全对话交互。

| 图案 | 主要功能 | 核心解决方案 |
| --- | --- | --- |
| [Brand Concierge对话体验](conversational-experience/brand-concierge-conversational-experience.md) | 将数字资产转换为由AI支持、品牌安全的对话体验，以指导客户发现 | [!DNL Brand Concierge], [!DNL Experience Platform], [!DNL Real-Time CDP] |

## 方案选择器

当场景很有可能适合多个模式时，请使用此指南。 回答分支问题以查找主要模式，然后可选地扩展列出的模式。

### 通过激励优惠实现回馈

*失效的客户已有90天未购买。 您希望通过定向优惠重新吸引他们。*

- **优惠选择是否为动态的（不同的客户根据资格或排名接收不同的优惠）？**
   - 是→[Offer Decisioning](personalization/offer-decisioning.md)作为选件层，封装在[多步骤编排历程](campaign-management-orchestration/multi-step-orchestrated-journey.md)中，用于重新参与序列
   - 没有（向所有符合条件的失效客户提供相同优惠），仅→[多步协调历程](campaign-management-orchestration/multi-step-orchestrated-journey.md)

### 购买后跟进

*客户刚刚完成购买。 您希望发送确认、交叉销售推荐和忠诚度奖励通知。*

- **序列是否需要根据实时事件（例如，已申请奖励、已审查产品）进行自适应分支？**
   - 是→[多步协调历程](campaign-management-orchestration/multi-step-orchestrated-journey.md)
   - [批出站消息激活](campaign-management-orchestration/batch-outbound-message-activation.md)→无（固定序列，无分支）
- **它是否包含个性化的产品推荐？**
   - 是→在内容层使用[行为推荐](personalization/behavioral-recommendation.md)进行扩展

### 忠诚度里程碑个性化

*客户达到新的忠诚度级别。 您希望显示个性化Web内容并发送祝贺消息。*

- **Web内容是否为个性化的（每层或每区段具有不同的内容）？**
   - 是→Web表面的[已知访客Web/应用程序个性化](personalization/known-visitor-web-app-personalization.md)
- **出站消息是单次发送还是培养序列？**
   - 单个发送→[事件触发的消息传递](campaign-management-orchestration/event-triggered-messaging.md)
   - [→多步协调历程](campaign-management-orchestration/multi-step-orchestrated-journey.md)的序列

### 重新参与营销活动

*非活动用户区段需要多点触控重新激活序列。*

- **单个消息是否需要实时从多个选件变体中进行选择？**
   - 是→[具有决策的跨渠道历程](campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
   - 无→[多步骤编排历程](campaign-management-orchestration/multi-step-orchestrated-journey.md)
