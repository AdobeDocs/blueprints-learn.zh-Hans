---
title: 已知访客Web/应用程序Personalization
description: 了解如何根据实时用户档案和区段会员资格向已识别的访客提供个性化内容、优惠或促销。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 585adc0e-f528-4a09-b931-ef6b45fa8ec8
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1819'
ht-degree: 4%

---

# 已知访客的Web/应用程序个性化

本指南介绍已知访客的Web/应用程序个性化用例模式，该模式使用[!DNL Adobe Journey Optimizer] (AJO)和[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)跨数字表面为已识别的访客提供个性化内容。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

已知访客的Web/应用程序个性化是经过身份验证的数字体验的主要个性化模式。 与仅依赖会话内行为信号的匿名访客个性化不同，此模式利用完整的统一配置文件：历史行为数据、区段成员资格、忠诚度级别、购买历史记录、生命周期阶段、计算属性和倾向分数。 它支持跨网页（通过AJO Web渠道）、移动应用程序内消息和内容卡片的个性化。

## 用例模式

本节介绍核心模式及其执行计划。

**已知访客的Web/应用程序个性化**

跨Web、移动应用程序内和内容卡表面根据实时配置文件和区段成员资格为已识别的访客提供个性化内容、优惠或促销。

**执行计划：**&#x200B;受众评估> Personalization Decisioning >界面/渠道配置>内容交付>展示跟踪>报告

## 用例概述

拥有经过身份验证的数字资产的组织（电子商务网站、银行门户、订阅服务、忠诚度计划、移动应用程序）需要提供个性化体验，以反映每位客户与品牌的关系。 当访客登录或通过身份解析进行识别时，平台可以访问其完整的统一配置文件，并根据其特定属性、行为和偏好提供量身定制的内容。

此模式适用于以下情况：已识别的访客到达Web资产或打开移动应用程序，系统必须根据实时配置文件数据和受众成员资格确定要显示的最佳内容、选件或促销活动。 个性化决策在边缘进行（以毫秒为单位），从而可在没有可察觉延迟的情况下进行每秒内容交付。

该模式支持确定性个性化（其中特定内容映射到特定受众区段）和动态决策（其中AJO Decisioning评估资格规则和排名策略以根据用户档案选择最佳内容）。 它跨越多个数字表面（网页、移动应用程序内消息和内容卡），支持在客户的数字历程中实现一致的个性化。

## 主要业务目标

此用例模式支持以下业务目标。

### 提供个性化的客户体验

根据个人偏好、行为和生命周期阶段定制内容、选件和消息。 有关详细信息，请参阅[提供个性化的客户体验](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)。

**KPI：**&#x200B;参与度、转化率、客户满意度(CSAT)

### 提高网站参与度

通过相关体验，缩短网站停留时间、每次会话显示页面以及与Web内容的交互。 有关详细信息，请参阅[提高网站参与度](../../business-objectives/acquisition-growth/increase-website-engagement.md)。

**KPI：**&#x200B;网页逗留时间、参与度、转化率

### 提高移动应用程序参与度

通过个性化的应用程序内体验，推动每日活动使用情况、功能采用和应用程序内转化。

**KPI：**&#x200B;参与度、维系率、转化率

## 战术用例示例

以下是此模式的常见战术实施：

- 按忠诚度等级或生命周期阶段划分的主页主页主页个性化 — 根据客户是新客户、活跃客户、风险客户还是VIP客户，显示不同的主页横幅
- 基于购买历史记录的产品推荐轮播 — 使用过去的购买数据和产品亲和度得分显示相关的产品建议
- 按客户区段显示的个性化促销横幅 — 显示针对高价值、高风险和新客户区段的不同促销活动
- 基于功能采用的移动用户的应用程序内消息 — 根据用户使用模式指导用户了解未充分利用的功能
- 在帐户仪表板上提供个性化优惠的内容卡 — 根据客户个人资料定制的持续、不允许的优惠
- 基于客户层的个性化定价或折扣显示 — 向忠诚度计划成员显示特定于层的定价或独家折扣
- 基于自有产品的交叉销售推荐小组件 — 根据当前产品组合推荐补充性产品或服务
- 基于兴趣的个性化导航或内容排序 — 根据演示的偏好对内容模块或导航元素重新排序

## 关键绩效指标

以下KPI有助于衡量此用例模式的有效性。

| KPI | 度量方法 | 基准指南 |
| --- | --- | --- |
| Personalization参与率 | 包含个性化内容元素的点击次数和交互次数除以展示次数 | 个性化内容的表现应优于默认内容20-50% |
| 转化率提升 | 个性化体验与控制/默认体验的转化率 | 目标比非个性化体验提升10-30% |
| 点进率(CTR) | 个性化CTA、优惠和推荐的点击次数除以展示次数 | 按表面（Web、应用程序内、内容卡）和每个区段进行监控 |
| 每次访问的收入 | 归因于具有个性化体验的会话的收入 | 比较个性化与非个性化访客同类群组 |
| 内容卡交互率 | 相对于展示的内容卡点击量和关闭量 | 按卡片类型和受众区段跟踪 |
| 应用程序内消息参与度 | 相对于展示的应用程序内消息交互（CTA点击次数、取消次数） | 跨受众区段和消息类型比较 |
| 页面逗留时间 | 包含个性化内容与默认内容的页面平均逗留时间 | 个性化页面应会显示增加的驻留时间 |
| 优惠接受率 | 导致转化事件的决策选定优惠的百分比 | 跟踪每个选件、每个投放位置和每个排名策略 |

## 应用程序

在此用例模式中使用以下应用程序。

- **[!DNL Adobe Journey Optimizer] (AJO)** — Web渠道配置、应用程序内渠道配置、内容卡渠道配置、决策（优惠选择和排名）、消息创作（个性化内容创建）、营销活动执行、内容试验以及报告
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 受众评估（边缘、流和批处理）、通过Edge Network进行实时配置文件查找、使用计算属性和倾向分数扩充配置文件
- **[!DNL Adobe Experience Platform] (AEP)** — 配置文件存储，身份服务， Web SDK， Mobile SDK，数据流配置，边缘网络交付

## 相关文档

以下资源提供了有关本指南中引用的技术和配置的更多详细信息。

### Web渠道个性化

- [Web渠道入门](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/web/get-started-web)
- [创建Web体验](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/web/create-web)
- [Web渠道配置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### 应用程序内和内容卡渠道

- [应用程序内渠道概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [应用程序内渠道先决条件](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [创建应用程序内消息](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [内容卡渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [内容卡配置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [创建内容卡片](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/content-card/create-content-card)

### 决策管理

- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [创建投放位置](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [创建决策规则](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [创建个性化优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [创建后备产品建议](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [创建集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [创建决策](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Personalization和内容

- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [辅助函数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### 受众和分段

- [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/segment-builder)
- [边缘分段](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/edge-segmentation)
- [流式客户细分](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language参考](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/pql/overview)

### 身份和配置文件

- [Identity服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [身份标识图链接规则](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/identity-linking-logic)
- [配置文件概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/home)
- [合并策略概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/merge-policies/overview)

### 数据收集和SDK

- [Web SDK概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/web-sdk/home)
- [安装Web SDK](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/web-sdk/install/overview)
- [移动SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [配置数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/datastreams/configure)
- [Edge Network Server API概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/edge-network-server-api/overview)

### 营销活动和试验

- [开始使用营销活动](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [内容体验入门](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [内容试验报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### 计算属性和扩充

- [计算属性概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/overview)
- [计算属性UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/ui)
- [Customer AI概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/intelligent-services/customer-ai/overview)

### 报告和分析

- [营销活动实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [CJA概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/home)

### 治理和隐私

- [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [高级数据生命周期管理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-lifecycle/home)

### 护栏

- [Journey Optimizer护栏](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)
- [Identity服务护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/guardrails)
