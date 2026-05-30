---
title: Customer Analytics和Insight生成
description: 了解如何构建跨渠道分析工作区、计算指标和仪表板，以进行行为和性能分析。
solution: Customer Journey Analytics, Experience Platform
exl-id: 235a4eb0-91ae-4030-b90e-7eda08c67ae1
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1717'
ht-degree: 3%

---

# Customer Analytics和insight生成

本指南介绍了Customer Analytics和insight生成用例模式，该模式将[!DNL Adobe Experience Platform]数据集连接到[!DNL Customer Journey Analytics]以构建数据视图、自由格式分析工作区、计算指标、功能板和移动记分卡，并可以选择将CJA定义的受众发布回[!DNL Adobe Experience Platform]以供激活。

它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

与分类法中其他侧重于激活和参与（发送消息、个性化内容、激活受众）的模式不同，此模式侧重于了解 — 分析客户行为、衡量营销活动效果、识别趋势，并生成为战略和优化决策提供信息的见解。

## 用例模式

**客户分析和insight生成**

构建跨渠道分析工作区、计算指标和仪表板，以了解客户行为和营销活动效果。

**执行计划：**&#x200B;数据连接>数据视图配置> Workspace Analysis >功能板发布

## 用例概述

组织需要了解客户如何跨渠道行为、促销活动如何执行、客户在历程中的流失位置、哪些内容引起了共鸣，以及不同区段如何随时间的推移保留。 Customer Analytics和insight生成通过将[!DNL Adobe Experience Platform]中的丰富跨渠道数据连接到[!DNL Customer Journey Analytics]来满足此需求，在此处，分析人员可以构建自由格式工作区、创建自定义量度、配置归因模型和发布仪表板以供利益相关者使用。

该模式面向多个受众：需要深入探索分析的营销分析员、需要绩效仪表板的活动经理、需要参与度和保留洞察的产品经理，以及需要概览KPI记分卡的管理员。 实施方法因主要分析重点（活动效果衡量、跨渠道历程分析、分析驱动的受众激活或引导式产品见解）而异。

## 主要业务目标

此用例模式支持以下业务目标。

**改进分析和报告**

增强报表功能，通过统一的功能板和自助服务工具提供更快、更易于实施的营销见解。

- **KPI：**&#x200B;效率、生产率

有关此业务目标的更多信息，请参阅[改进分析和报告](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)。

**启用数据驱动型决策**

让团队能够使用自助分析、实时客户洞察和AI支持的预测来指导策略。

- **KPI：**&#x200B;效率、生产率

有关此业务目标的详细信息，请参阅[启用数据驱动型决策](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)。

**改进营销归因**

准确衡量营销接触点、渠道和营销活动对转化和收入结果的影响。

- **KPI：**&#x200B;效率，增量收入

有关此业务目标的详细信息，请参阅[改进营销归因](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md)。

**优化营销支出和ROI**

通过了解哪些渠道和营销活动可带来最高回报，优化营销预算分配。

- **KPI：**&#x200B;效率，增量收入

有关此业务目标的更多信息，请参阅[优化营销支出和ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)。

## 战术用例示例

以下是可以使用此模式实施的战术用例示例。

- 营销活动效果仪表板 — 跨电子邮件、短信、推送和付费媒体营销活动的投放量度、参与率、转化和收入归因
- 客户历程流失分析 — 识别客户在购买、注册或载入漏斗中放弃的位置
- 同类群组维系分析 — 衡量不同的客户获取同类群组在周、月和季度中的维系情况
- 渠道归因建模 — 对首次联系、最近联系、线性归因和时间衰减归因进行比较，以了解哪些渠道可促进转化
- 内容性能分析 — 按区段、渠道和生命周期阶段确定最能引起共鸣的内容
- 产品使用和采用率分析 — 跟踪功能采用、参与频率和用户增长趋势
- 客户生命周期阶段分析 — 按生命周期阶段（新、活跃、存在风险、已失效）划分和分析客户
- 营销组合优化仪表板 — 比较渠道投资与收入贡献
- 跨渠道参与度评分和报告 — 从Web、应用程序、电子邮件和活动交互中构建复合参与度分数

## 关键绩效指标

以下KPI可帮助衡量此用例模式是否成功。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 效率 | 缩短insight时间和手动报告工作 | 跟踪分析人员在CJA实施之前和之后构建报表所花费的时间 |
| 工作效率 | 业务用户创建的自助分析数量 | 监控Workspace项目创建和功能板使用情况 |
| 增量收入 | 归因于见解驱动型优化决策的收入 | 衡量基于CJA分析优化的促销活动的收入提升 |
| 转化率 | 关键客户旅程中的Funnel完成率 | 使用CJA流失可视化图表跟踪每个历程步骤的流失率 |
| 参与度 | 跨渠道的客户互动深度和频率 | 在CJA中构建参与度评分的计算指标 |
| 保留 | 已定义时间期的客户退货率 | 使用CJA同类群组分析测量维系率曲线 |

## 应用程序

在此用例模式中使用以下应用程序。

- **[!DNL Customer Journey Analytics] (CJA)** — 连接、数据视图、工作区分析、引导式分析、计算指标、功能板、受众发布和内容分析
- **[!DNL Adobe Experience Platform] (AEP)** — 为CJA连接提供数据湖、数据集、XDM架构、配置文件和事件数据

## 相关文档

以下资源提供了有关此用例模式的其他信息。

### [!DNL Customer Journey Analytics] — 快速入门

- [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA护栏](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

### 连接

- [连接概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [创建或编辑连接](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [管理连接](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)

### 数据视图

- [数据视图概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [创建或编辑数据视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [组件设置概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [持久性设置](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [归因设置](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [格式设置](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [重复量度删除](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [包括/排除值](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [会话设置](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)
- [派生字段](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Workspace &amp; analysis

- [Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [创建项目](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [自由格式表](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [流量可视化](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [流失可视化](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [同类群组表](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [“归因”面板](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [划分维度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [共享项目](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [计划项目](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [导出概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/export/export-cloud)

### 引导式分析

- [指导分析概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [funnel视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [趋势视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [参与频率视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [“维系”视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [活跃增长视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [发布影响视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/release)
- [首次使用影响视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/first-use)
- [时间线视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/streams/timeline)

### 组件

- [过滤器概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [创建过滤器](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [计算量度概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [创建计算量度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [计算量度函数](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [批注概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [日期范围](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)
- [量度组件](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/apply-create-metrics)

### 受众发布

- [受众概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [创建并发布受众](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [管理受众](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)

### 内容分析

- [Content Analytics](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/content-analytics/content-analytics)
- [Content Analytics配置](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/config/configuration)

### 功能板和记分卡

- [创建移动记分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [配置和策划记分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics功能板 — 执行指南](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [概要数字可视化](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)

### AEP基础

- [数据集概述](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/overview)
- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [来源概述](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [受众门户概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-portal)

### AJO报表集成

- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [营销活动电子邮件报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/campaign-global-report-cja-email)
- [历程电子邮件报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/journey-global-report-cja-email)

### 教程和指南

- [架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
