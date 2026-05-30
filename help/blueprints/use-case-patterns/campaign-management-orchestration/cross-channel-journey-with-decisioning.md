---
title: 使用Decisioning进行跨渠道历程
description: 了解如何结合实时决策来编排多步历程以选择最佳渠道、内容或选件。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: eabdd91f-bb7d-4de3-adb5-5940d3ca4a78
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1983'
ht-degree: 5%

---

# 使用决策的跨渠道历程

本指南介绍具有决策功能的跨渠道历程用例模式，该模式使用[!DNL Adobe Journey Optimizer]和[!DNL Adobe Real-Time Customer Data Platform]编排多步骤、多渠道历程，在一个或多个历程节点纳入实时决策。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

具有决策的跨渠道历程是[!DNL Adobe Experience Platform]生态系统中最复杂的活动编排模式。 通过结合实时决策（使用[!DNL AJO]决策评估用户档案的当前上下文，并在历程画布内的一个或多个决策点动态选择最佳渠道、内容或选件），该功能扩展了多步骤编排的历程。

## 用例模式

**具有决策的跨渠道历程**

编排多步骤、多渠道历程，该历程在一个或多个节点结合了实时决策以选择最佳渠道、内容或选件。

**执行计划：**&#x200B;受众评估>历程执行>决策节点>渠道选择>消息投放>报告

## 用例概述

组织越来越需要提供自适应、个性化的客户历程，这些历程会动态响应每个人的实时上下文，而不是遵循固定的预定顺序。 客户的首选渠道、参与历史记录、忠诚度级别、预测的存留期值以及当前产品兴趣都将在每个接触点制定下一个最佳操作。

包含决策的跨渠道历程通过结合两个强大的[!DNL AJO]功能来满足此需求：历程编排（管理多步骤流程、计时、条件和渠道交付）和决策（评估资格规则、应用排名策略并在每个决策点选择最佳优惠或内容变体）。

此模式适用于以下情况：

- 历程必须动态适应每个用户档案的实时状态，而不是遵循固定渠道或内容序列
- 多个选件、内容变体或渠道是一个或多个历程节点的候选项目，应根据配置文件上下文选择最佳选项
- 需要人工智能辅助或基于公式的排名，以优化历程中的选件选择
- 公司希望将渠道选择逻辑和选件管理整合到一个集中的决策框架中，而不是维护复杂的分支逻辑

目标受众包括营销人员，他们管理生命周期计划、忠诚度历程、回馈序列和入门流程，在这些流程中，大规模个性化需要在每个接触点进行自动决策。

>[!NOTE]
>如果您的历程不需要在单个节点进行动态决策，例如，固定序列培养或入门计划，请参阅[多步编排历程](multi-step-orchestrated-journey.md)。 该模式可更轻松地配置，并且不需要AJO Decisioning。

## 主要业务目标

此用例模式支持以下业务目标。

**[提供个性化的客户体验](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
根据个人偏好、行为和生命周期阶段定制内容、选件和消息。
**KPI：**&#x200B;参与度、转化率、客户满意度(CSAT)

**[提高客户忠诚度和存留期值](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
通过忠诚度计划、奖励和个性化参与，深化客户关系并最大化长期价值。
**KPI：**&#x200B;客户存留期值、留存率、追加销售/交叉销售%

**[提高客户保留率](../../business-objectives/customer-experience/improve-customer-retention.md)**
透过价值导向型经验及持续培养关系，让现有客户持续参与及不断更新。
**KPI：**&#x200B;维系、客户存留期值、参与度

**[推动交叉销售和追加销售收入](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
根据行为和购买历史，向现有客户推广补充性和优质产品或服务。
**KPI：**&#x200B;追加销售/交叉销售%，增量收入，客户存留期值

## 战术用例示例

以下场景说明了如何将具有决策的跨渠道历程应用于实践。

- **自适应回送历程** — 多步骤历程，决策根据每个用户档案的参与历史记录选择渠道（电子邮件、推送或短信），并根据预测的生命周期值动态选择最佳激励优惠
- **下一个最佳行动生命周期历程** — 决策功能决定了在客户生命周期的每个阶段传达什么内容，可从入门内容、交叉销售优惠、忠诚度奖励或维系奖励中进行选择
- **通过动态内容选择进行个性化入门** — 新的客户入门历程，其中每个接触点都使用决策功能选择最相关的产品教育内容、提示或激活优惠
- **具有个性化奖励的跨渠道忠诚度计划历程** — 忠诚度会员在决策功能根据层级、购买历史记录和类别亲和度选择个性化奖励优惠的历程中前进
- **动态重新参与渠道和激励优化** — 休眠客户重新参与，其中动态选择外联渠道和激励以最大化响应概率
- **包含人工智能排名内容推荐的客户生命周期培养** — 人工智能排名决策在每个接触点选择最相关的内容或产品推荐的持续培养历程

## 关键绩效指标

使用以下KPI衡量此用例模式的有效性。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 历程完成率 | 完成完整历程的用户档案的百分比 | 历程报表：已完成/已输入 |
| 优惠接受率 | 参与（已点击、已兑换）的决策选定优惠的百分比 | 决策报告：优惠点击次数/优惠展示次数 |
| 渠道参与率 | 历程中使用的每个渠道的打开率和点击率 | 历程报告中的每渠道投放量度 |
| 转化率 | 完成目标转化操作的历程参与者的百分比 | 历程退出事件跟踪或CJA funnel analysis |
| 后备优惠率 | 返回后备优惠而不是个性化优惠的决策请求百分比 | 决策报告：回退选择/选择总数 |
| 客户存留期值影响 | 历程参与者与对照组的CLV更改 | CJA同类群组分析以及保持型比较 |
| 交叉销售/追加销售收入 | 归因于决策所选优惠的增量收入 | 对优惠驱动型转化的CJA归因分析 |
| 决策排名效果 | AI排名选件与随机/基于优先级的选择之间的性能差异 | A/B比较排名策略的实验 |

## 应用程序

以下应用程序用于实现此用例模式。

- **[!DNL Adobe Journey Optimizer]([!DNL AJO])** —历程编排（多步骤画布设计、进入条件、等待、条件、退出条件）、跨渠道消息创作、渠道表面配置、冲突和优先级管理
- **[!DNL Adobe Journey Optimizer]决策** — 优惠和内容项目管理、资格规则、排名策略（优先级、公式、AI）、决策策略、投放、后备优惠
- **[!DNL Adobe Real-Time Customer Data Platform]([!DNL RT-CDP])** — 历程进入和优惠资格区段的受众评估，具有计算属性和倾向分数的配置文件扩充，同意和治理实施
- **[!DNL Adobe Experience Platform]([!DNL AEP])** — 实时客户配置文件存储、跨渠道解析身份服务、数据建模和引入基础结构

## 相关文档

以下资源提供了有关此用例模式中所用功能的更多详细信息。

### 历程编排

- [历程入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [创建历程](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [历程属性](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [读取受众活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [受众鉴定事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [条件活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在历程中添加消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [退出标准](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [历程条目管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [测试您的历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [发布历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### 决策管理

- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [创建投放位置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [创建决策规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [创建个性化优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [创建后备产品建议](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [创建集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [创建集合限定符](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [创建决策](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### 渠道配置

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [创建 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP预热计划](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [电子邮件表面设置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 消息创作和个性化

- [创建电子邮件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 冲突、优先级和频率管理

- [冲突和优先级管理概述](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [优先级分数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [识别潜在冲突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [历程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### 受众和分段

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [受众构成](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language参考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 报告和分析

- [历程实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### 个人资料和身份

- [Real-time Customer Profile概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Customer AI概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### 数据治理和同意

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [管理禁止列表](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 护栏

- [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity服务护栏](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
