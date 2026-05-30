---
title: Offer Decisioning
description: 了解如何使用集中式决策逻辑跨渠道为用户档案选择下一个最佳选件或内容。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 8fd511b3-0200-41bf-aff1-e3f2a00a578e
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1640'
ht-degree: 5%

---

# Offer Decisioning

本指南介绍Offer Decisioning用例模式，该模式使用[!DNL Adobe Journey Optimizer] (AJO) Decisioning和[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)实施集中式优惠选择逻辑，从而跨渠道为每个客户配置文件确定下一个最佳优惠。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

此模式将“显示内容”决策与“显示位置”渠道逻辑分离，从而实现跨电子邮件、Web、移动应用程序和任何其他接触点的一致且优化的优惠选择。 AJO Decisioning管理整个优惠生命周期：优惠创建和目录管理、资格规则（谁可以查看每个优惠）、排名策略（如何在合格优惠中进行选择）、投放位置（优惠出现的位置）和决策策略（将所有内容捆绑在一起）。

## 用例模式

此部分介绍Offer Decisioning的执行计划和模式定义。

**Offer Decisioning**

使用集中式决策逻辑跨渠道为用户档案选择下一个最佳优惠或内容。

**执行计划：**&#x200B;受众评估>优惠资格>排名策略>决策执行>交付>报告

## 用例概述

组织经常需要在交互时向每位客户提供最相关的选件、促销或激励。 无论互动发生在电子邮件促销活动中、网站主页上、移动应用程序中，还是多步历程中的决策点，挑战都是一样的：根据客户身份、客户资格以及最有可能带来预期结果的选件，从可用选项目录中选择最佳选件。

Offer Decisioning通过在AJO的决策管理引擎中集中所有优惠选择逻辑来解决此问题。 决策引擎不会将优惠分配硬编码到单独的促销活动或渠道中，而是评估每个用户档案的属性、受众成员资格和上下文信号，以实时确定最佳优惠。 这种集中化可确保同一客户获得一致且经过优化的优惠，无论他们通过哪个渠道开展业务。

此模式与已知访客的Web/应用程序个性化模式在范围上有所不同 — offer decisioning与渠道无关，并且是集中式的，而已知访客个性化侧重于数字表面个性化。 它与目录模型中的行为推荐不同 — 当符合条件的项目集受业务规则、资格限制或监管要求（促销、金融产品、激励）制约时，可使用Offer Decisioning。 当项目集很大、不断变化并且选择由行为相似性或亲和度信号（产品目录、内容库）驱动时，使用行为推荐。

## 主要业务目标

此用例模式支持以下业务目标。

**[提供个性化的客户体验](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
根据个人偏好、行为和生命周期阶段定制内容、选件和消息。
**KPI：**&#x200B;参与度、转化率、客户满意度(CSAT)

**[推动交叉销售和追加销售收入](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
根据行为和购买历史，向现有客户推广补充性和优质产品或服务。
**KPI：**&#x200B;追加销售/交叉销售%，增量收入，客户存留期值

**[提高客户忠诚度和存留期值](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
通过忠诚度计划、奖励和个性化参与，深化客户关系并最大化长期价值。
**KPI：**&#x200B;客户存留期值、留存率、追加销售/交叉销售%

## 战术用例示例

以下场景说明了如何在实践中应用Offer Decisioning。

- 电子邮件促销活动中的下一个最佳优惠 — 在发送时为每个收件人选择最相关的促销活动
- 网站上的实时促销横幅 — 决策功能根据访客的配置文件在页面加载时选择选件
- 以最佳方式刺激用户生命周期阶段的个性化应用程序内卡
- 跨渠道优惠一致性 — 相同的决策逻辑提供电子邮件、Web和推送服务，以便客户看到统一的优惠体验
- 基于客户价值层的动态优惠券或折扣选择（例如，高价值客户会获得优质优惠）
- 基于当前订阅级别的产品升级或追加销售选件选择
- 基于层级和活动历史的忠诚度奖励优惠个性化

## 关键绩效指标

以下KPI有助于衡量Offer Decisioning实施的有效性。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 优惠接受率 | 导致点击、赎回或转化的已交付优惠的百分比 | 优惠点击次数或赎回/投放的优惠总数 |
| 选件选择分发 | 在所有决策中选定的每个优惠的比例 | 每个优惠的计数/呈现的决策总数 |
| 回退率 | 没有符合条件的个性化优惠且已提供回退的决策百分比 | 后备展示次数/决策总数 |
| 转化率 | 完成所需操作（购买、注册、赎回）的优惠接收者百分比 | 转化/优惠展示次数 |
| 增量收入 | 与对照组或后备优惠相比，归属于决策选定优惠的收入 | 来自个性化优惠的收入 — 来自后备/控制的收入 |
| 跨渠道一致性分数 | 在定义的窗口内跨多个渠道接收相同选件的用户档案的百分比 | 一致的优惠/多渠道展示次数总计 |
| 优惠点进率 | 导致点击的优惠展示次数百分比 | 优惠点击次数/优惠展示次数 |

## 应用程序

在此用例模式中使用以下Adobe应用程序。

- **[!DNL Adobe Journey Optimizer] (AJO)** — 用于优惠创建、资格规则、排名策略、投放位置和决策策略的决策管理引擎；用于优惠投放的渠道配置和消息创作；营销活动和历程执行
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 优惠资格区段的受众评估；资格和排名中使用的配置文件数据和计算属性
- **[!DNL Adobe Experience Platform] (AEP)** — 支持AJO和RT-CDP的统一配置文件存储、身份解析和数据基础

## 相关文档

以下资源提供了有关此用例模式中使用的组件的其他详细信息。

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

### 选件交付

- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [使用Edge Decisioning API提供优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [使用Decisioning API提供优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/decisioning-api)

### 渠道配置

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [电子邮件表面设置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### 消息创作和个性化

- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 营销活动和历程

- [开始使用营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [历程入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### 内容试验

- [内容体验入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### 受众和分段

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### 个人资料和身份

- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Customer AI概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### 数据建模和收集

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

### 报告和分析

- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### 数据治理和生命周期

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### 护栏

- [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### 教程

- [决策管理API快速入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/getting-started)
