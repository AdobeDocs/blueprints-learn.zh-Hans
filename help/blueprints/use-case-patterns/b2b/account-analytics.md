---
title: B2B分析
description: 了解如何在跨渠道客户历程分析中包含B2B帐户级别信息。
solution: Customer Journey Analytics, Real-Time Customer Data Platform
exl-id: 9d576e5c-cbd2-4c60-a6b0-88f8b8b963b4
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1811'
ht-degree: 2%

---

# B2B分析

本指南介绍了B2B分析用例模式，该模式使用[!DNL Customer Journey Analytics] ([!DNL CJA])B2B edition和[!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP])B2B edition将B2B帐户级别信息合并到跨渠道客户历程分析中。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

B2B Analytics通过基于帐户的连接、特定于B2B的容器（帐户、全球帐户、机会、购买小组）和帐户级别的报告扩展了标准[!DNL CJA]功能。 此功能使组织能够在客户级别分析营销和销售参与度、跟踪商机进展、衡量购买组完整性，以及将收入归因于在较长的B2B销售周期内的营销接触点。

## 用例模式

**B2B分析**

在跨渠道客户历程分析中包含B2B帐户级别信息。

**执行计划：** B2B数据连接>帐户数据视图配置> Workspace Analysis >功能板发布

## 用例概述

B2B组织面临根本性的分析挑战：其客户不是个人客户，而是由多个利益相关者、购买组和机会组成的帐户。 基于人员的标准分析不能回答诸如“哪些客户最参与？”、“我们的购买小组完成了多少？”或“哪些营销接触点推动了机会进展？”等之类的问题。

B2B Analytics通过利用[!DNL CJA] B2B edition创建以帐户为中心的分析视图（将人员级别的行为数据与帐户、机会和购买群组维度相结合）来解决此问题。[!DNL RT-CDP] B2B edition提供基础帐户配置文件统一和B2B身份解析，以提供Analytics层。 这些解决方案结合起来，使组织能够在客户级别构建跨渠道历程分析，将营销参与与管道进展相关联，并向营销和销售团队提供切实可行的洞察。

目标受众包括B2B营销运营团队、需求挖掘负责人、收入运营分析员和销售负责人，他们需要了解客户级别的参与情况和管道运行状况。

## 主要业务目标

此用例模式支持以下业务目标。

### 改进分析和报告

增强报表功能，通过统一的功能板和自助服务工具提供更快、更易于实施的营销见解。 B2B Analytics使组织能够将来自多个来源的帐户级参与数据整合到单个分析环境中，从而跨渠道了解营销计划如何影响管道和收入。

**KPI：**&#x200B;效率、生产率

[了解有关改进分析和报告的更多信息](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)

### 支持数据驱动型决策

让团队能够使用自助分析、实时客户洞察和AI支持的预测来指导策略。 帐户级别的分析为营销和销售团队提供了确定帐户优先级、优化参与策略以及调整潜在销售机会所需的数据。

**KPI：**&#x200B;效率、生产率

[了解有关支持数据驱动型决策的更多信息](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)

### 改进潜在客户资格鉴定和转化

通过评分、培养和个性化的跟进，提高销售线索质量并加快管道进度。 CJA B2B edition提供了专为B2B销售周期设计的13个月扩展帐户回顾窗口，从而能够在整个帐户历程中实现准确的多接触点归因。

**KPI：**&#x200B;效率，增量收入

[了解有关改进潜在客户资格和转化的更多信息](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

## 战术用例示例

以下场景说明了如何将此模式应用于实践。

- **帐户参与度评分分析** — 通过帐户在Web、电子邮件、事件和内容交互中的聚合参与度来衡量帐户并进行排名，以确定高意向帐户以进行销售跟进
- **购买群组完整性跟踪** — 分析跨帐户的购买群组构成，以找出角色覆盖范围的差距并优先为未完成的购买群组获得潜在客户
- **机会管道关联** — 将营销参与数据与机会阶段进展关联，以了解哪些营销活动和接触点可推动管道进展
- **多触点B2B归因** — 将具有13个月回顾时间范围的归因模型应用于从首次接触到结束的完整B2B购买历程中的信用营销接触点
- **帐户历程映射** — 通过创建并关闭商机、确定通用路径和摩擦点，将跨渠道帐户历程从最初的认知可视化
- **营销活动对管道的影响** — 衡量特定营销活动对帐户管道创建、机会提升和收入生成的影响
- **购买组参与度进展** — 跟踪购买组参与度分数随时间的变化，并将参与度阈值与机会结果关联
- **基于帐户的内容性能** — 分析哪些内容资产和主题与特定客户群体、行业或购买团体角色产生共鸣
- **销售和营销协调功能板** — 构建共享的功能板，为营销和销售团队提供帐户参与度、管道运行状况和收入归因的统一视图
- **激活的帐户分段** — 根据帐户级别的分析创建B2B区段（例如，“没有开放机会的参与度高的帐户”），并发布这些区段以进行下游激活

## 关键绩效指标

以下KPI可帮助衡量此用例模式是否成功。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 帐户参与度分数 | 汇总帐户中所有联系人的参与量度 | 在帐户级别组合了Web访问、电子邮件交互、事件出勤和内容下载的计算量度 |
| 购买组完整性 | 购买组中所需角色的百分比 | 已填充角色与每个购买组所需角色总数的比率，随时间进行跟踪 |
| 受营销影响的管道 | 营销活动涉及的管道中的收入 | 相关客户联系人在归因窗口中具有营销接触点的机会值 |
| 客户到业务机会的转化率 | 生成合格机会的参与客户的百分比 | 具有机会的客户除以定义期间内的参与客户总数 |
| 平均交易周期长度 | 从首次营销接触到成功关门的时间 | 从第一个已归因接触点到机会关闭日期的平均持续时间 |
| 营销归因收入 | 归因于营销接触点的收入 | 通过归因模型分销的营销接触来赢的机会的收入 |
| 客户覆盖和渗透 | 每个目标帐户的参与联系人数 | 每个帐户具有营销互动的唯一联系人，与已知联系人总数相比 |
| 按购买角色列出的内容参与度 | 按购买团体角色划分的参与量度 | 按购买组内的角色/角色细分的页面查看、下载和逗留时间 |

## 应用程序

以下应用程序用于实现此用例模式。

- **[!DNL Customer Journey Analytics]B2B edition** — 提供基于帐户的连接、特定于B2B的数据视图容器、帐户级别的工作区分析、购买组分析、机会分析、B2B分段和带有扩展回顾窗口的B2B归因
- **[!DNL Real-Time CDP]B2B edition** — 提供B2B数据基础，包括帐户配置文件统一、B2B身份解析、B2B架构类（Account、Opportunity、购买组）以及用于摄取B2B参与数据的[!DNL Marketo Engage]集成

## 相关文档

以下资源提供了实施此用例模式的其他信息。

**[!DNL CJA]B2B edition**

- [CJA B2B edition概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [CJA概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA护栏](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-admin/guardrails)

**连接**

- [连接概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-connections/overview)
- [创建或编辑连接](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-connections/create-connection)
- [管理连接](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-connections/manage-connections)

**数据视图**

- [数据视图概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/data-views)
- [创建或编辑数据视图](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [组件设置概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [持久性设置](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [归因设置](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [格式设置](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [派生字段](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [会话设置](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/session-settings)

**Workspace和分析**

- [Workspace概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/home)
- [创建项目](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [自由格式表](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [流量可视化](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [流失可视化](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [同类群组表](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [“归因”面板](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [共享项目](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [计划项目](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [划分维度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

**组件**

- [过滤器概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [创建过滤器](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [计算量度概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [创建计算量度](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [批注概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/annotations/overview)
- [日期范围](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

**受众**

- [受众概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [创建并发布受众](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/audiences/publish)
- [管理受众](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/audiences/manage)

**功能板和记分卡**

- [创建移动记分卡](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [配置和策划记分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics功能板 — 执行指南](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dashboards/set-up-execs)

**引导式分析**

- [指导分析概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/guided-analysis/overview)
- [funnel视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [趋势视图](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/guided-analysis/trends/usage)
- [“维系”视图](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

**[!DNL RT-CDP]B2B edition**

- [RT-CDP B2B edition概述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#702702)
- [B2B edition架构](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/rtcdp/schemas/b2b)
- [B2B源概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/rtcdp/sources/b2b)

**AEP数据基础**

- [XDM系统概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/home)
- [来源概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/home)
- [Marketo Engage连接器](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Identity服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home)
- [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)

**数据治理和生命周期**

- [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home)
- [高级数据生命周期管理](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-lifecycle/home)

**教程和指南**

- [架构组合基础](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/schema/composition)
- [计算属性概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/overview)
- [可观察性分析概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/home)
