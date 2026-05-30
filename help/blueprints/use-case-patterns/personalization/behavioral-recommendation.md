---
title: 行为推荐
description: 了解如何使用选择策略和排名模型生成项目和内容推荐。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: db16e773-e0da-46c4-9fa5-d16f04feb46b
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 5%

---

# 行为推荐

本指南介绍了行为推荐用例模式，该模式使用[!DNL Adobe Journey Optimizer] (AJO) Decisioning、[!DNL Real-Time Customer Data Platform] (RT-CDP)和[!DNL Adobe Experience Platform] (AEP)跨Web、移动应用程序和电子邮件渠道提供个性化推荐体验。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

行为推荐使用行为信号（产品查看、购买、内容交互、搜索查询）与AJO Decisioning选择策略和排名模型相结合，生成项目级别或内容级别的推荐。 与offer decisioning（使用资格规则和业务限制来控制一组有限的优惠、促销或激励）不同，此模式适用于不断变化的大型项目目录（产品、文章、视频），其中的选择由行为亲和信号而不是受控制的资格驱动。

## 用例模式

**行为推荐**

使用AJO Decisioning选择策略和排名模型根据行为信号生成项目级或内容级推荐，以提供上下文内容。

**执行计划：**&#x200B;行为信号提取>决策策略评估>推荐交付>报告

## 用例概述

拥有产品目录、内容库或媒体库的组织需要根据每位访客的行为历史记录和会话内活动，向其展示最相关的项目。 无论是主页上的“为您推荐”轮播、产品详细信息页面上的交叉销售小组件，还是电子邮件促销活动中嵌入的产品推荐，基本挑战都是相同的：将每位访客的行为配置文件与目录中最相关的项目相匹配，然后在适当的时候在正确的渠道中提供这些推荐。

此模式通过以下方式解决了该难题：通过[!DNL Web SDK]或[!DNL Mobile SDK]实时摄取行为信号，通过结合项目属性和行为上下文的AJO Decisioning选择策略处理这些信号，以及通过Web、应用程序内或电子邮件渠道交付推荐的项目。 排名模型可以基于公式（例如，按类别亲和度分数排序）或AI排名（例如，个性化推荐模型）。 模式还通过配置回退推荐来处理没有行为历史记录的新访客的冷启动方案。

此模式的目标受众包括电子商务营销团队、内容个性化团队和数字体验团队，这些团队寻求通过由真实用户行为驱动的个性化推荐提高参与度、转化率和平均订单价值。

## 主要业务目标

此用例模式支持以下业务目标。

### [推动交叉销售和追加销售收入](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

根据行为和购买历史，向现有客户推广补充性和优质产品或服务。

**KPI：**&#x200B;追加销售/交叉销售%，增量收入，客户存留期值

### [提高转化率](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

提高完成所需操作（如购买、注册或表单提交）的访客和潜在客户的百分比。

**KPI：**&#x200B;转化率、潜在客户转化、每个潜在客户的成本

### [提供个性化的客户体验](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

根据个人偏好、行为和生命周期阶段定制内容、选件和消息。

**KPI：**&#x200B;参与度、转化率、客户满意度(CSAT)

## 战术用例示例

以下是此模式的常见战术实施：

- 产品详细信息页面上的产品交叉销售小组件（“已购买客户”）
- 基于浏览历史记录的主页上的“为您推荐”轮播
- 媒体网站上基于阅读行为的内容推荐
- “最近查看的项目”与类似项目小部件相结合
- 购买后补充产品推荐
- 通过电子邮件发送基于行为亲和度的产品推荐
- 基于会话内浏览行为的特定于类别的推荐
- 基于行为信号的搜索结果重新排名

## 关键绩效指标

以下KPI有助于衡量行为推荐实施的有效性。

| KPI | 度量方法 |
| --- | --- |
| 推荐点进率(CTR) | 推荐项目的点击次数除以推荐展示次数 |
| 推荐转化率 | 推荐点击量的购买或所需操作数除以推荐总点击量 |
| 受推荐影响的收入 | 来自至少包含一个推荐驱动型产品的订单的总收入 |
| 平均订单值(AOV)提升 | 参与推荐的会话与未参与推荐的会话的AOV增加 |
| 每订单项目数 | 每个订单中涉及推荐的会话的项目数 |
| 推荐范围 | 收到个性化（非后备）推荐的符合条件的页面查看次数或会话的百分比 |
| 冷启动回退率 | 由于行为历史记录不足而由回退逻辑提供的推荐请求百分比 |

## 应用程序

在此用例模式中使用以下应用程序。

- **[!DNL Adobe Journey Optimizer] (AJO)决策** — 选择策略、排名模型、项目目录和决策策略，用于评估行为信号并返回每个访客的最相关项目
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 行为配置文件数据累积、推荐范围的受众评估以及行为亲和度评分的计算属性
- **[!DNL Adobe Experience Platform] (AEP)** — 通过[!DNL Web SDK]和[!DNL Mobile SDK]进行的行为事件摄取，[!DNL Edge Network]正在处理，事件和目录数据的XDM架构管理

## 相关文档

以下资源提供了有关在此模式中使用的技术和功能的更多详细信息。

### 决策管理

- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [创建投放位置](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [创建决策规则](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [创建个性化优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [创建后备产品建议](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [创建集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [创建集合限定符](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [创建决策](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [使用Edge Decisioning API提供优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### 数据收集和Web/移动SDK

- [Web SDK概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/web-sdk/home)
- [安装Web SDK](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/web-sdk/install/overview)
- [移动SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [配置数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/datastreams/configure)
- [Edge Network Server API概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/edge-network-server-api/overview)

### XDM和数据建模

- [XDM系统概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/schema/composition)
- [创建数据集](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/catalog/datasets/create)
- [定义两个架构之间的关系](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/tutorials/relationship-api)

### 身份和配置文件

- [Identity服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [合并策略概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/merge-policies/overview)
- [Real-time Customer Profile概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/home)

### 受众和分段

- [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/edge-segmentation)

### 计算属性和配置文件扩充

- [计算属性概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/overview)
- [计算属性UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/ui)
- [Customer AI概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/intelligent-services/customer-ai/overview)

### 渠道配置

- [电子邮件配置入门](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [设置渠道平面](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### 消息创作和个性化

- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### 报告和分析

- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [CJA概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/home)
- [计算量度概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### 数据治理和生命周期

- [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [高级数据生命周期管理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-lifecycle/home)
- [数据集过期时间](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### 监控和可观察性

- [可观察性分析概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/home)
- [警报概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/alerts/overview)

### 护栏

- [Journey Optimizer护栏](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)
- [摄取护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/ingestion/guardrails)
- [Identity服务护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/guardrails)

### 教程和指南

- [来源概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/home)
- [标记概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/tags/home)
- [同意和偏好设置字段组](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/field-groups/profile/consents)
