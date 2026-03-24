---
title: B2B分析
description: 了解如何在跨渠道客户历程分析中包含B2B帐户级别信息。
solution: Customer Journey Analytics, Real-Time Customer Data Platform
exl-id: 9d576e5c-cbd2-4c60-a6b0-88f8b8b963b4
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7528'
ht-degree: 1%

---

# B2B分析

本指南为使用[!DNL Customer Journey Analytics] ([!DNL CJA]) B2B edition和[!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition的B2B帐户级别分析提供全面的实施参考。 它专为需要将B2B帐户级别信息纳入跨渠道客户历程分析的解决方案架构师、营销技术人员和实施工程师而设计。

它涵盖了以帐户为中心的分析的所有可行方法，从扁平的帐户结构到复杂的全球帐户层次结构，并提供了关于何时选择每个选项的指导。 该计划涉及B2B数据连接、帐户数据视图配置、工作区分析和功能板发布。

B2B Analytics通过基于帐户的连接、特定于B2B的容器（帐户、全球帐户、机会、购买小组）和帐户级别的报告扩展了标准[!DNL CJA]功能。 此功能使组织能够在客户级别分析营销和销售参与度、跟踪商机进展、衡量购买组完整性，以及将收入归因于在较长的B2B销售周期内的营销接触点。

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

## 用例模式

**B2B分析**

在跨渠道客户历程分析中包含B2B帐户级别信息。

**函数链：** B2B数据连接>帐户数据视图配置> Workspace Analysis >功能板发布

## 应用程序

以下应用程序用于实现此用例模式。

- **[!DNL Customer Journey Analytics]B2B edition** — 提供基于帐户的连接、特定于B2B的数据视图容器、帐户级别的工作区分析、购买组分析、机会分析、B2B分段和带有扩展回顾窗口的B2B归因
- **[!DNL Real-Time CDP]B2B edition** — 提供B2B数据基础，包括帐户配置文件统一、B2B身份解析、B2B架构类（Account、Opportunity、购买组）以及用于摄取B2B参与数据的[!DNL Marketo Engage]集成

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本函数 | 状态 | 必须准备好的内容 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 必填 | 沙盒配置了[!DNL CJA]个B2B edition和[!DNL RT-CDP]个B2B edition权限。 为有权访问[!DNL CJA]和B2B数据模型的数据工程师、分析师和营销运营用户设置的角色。 | [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home) |
| 数据建模和准备 | 必填 | 使用B2B类配置的B2B XDM架构：XDM业务帐户、XDM业务机会、XDM业务帐户人员关系、XDM业务机会人员关系和XDM业务营销列表成员。 必须定义客户属性、商机阶段和购买组角色的字段组。 为配置文件创建和启用数据集。 | [XDM系统概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/home)，[B2B edition架构](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/rtcdp/schemas/b2b) |
| 数据源和收集 | 必填 | B2B数据源已连接，通常通过[!DNL Marketo Engage]源连接器或[!DNL Salesforce] CRM源连接器连接。 客户记录、机会记录、人员 — 客户关系和行为参与事件必须流入AEP数据集。[!DNL Web SDK] 或[!DNL Marketo]集成必须通过帐户关联捕获行为事件。 | [源概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/home)，[Marketo Engage连接器](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| 身份和配置文件配置 | 必填 | B2B身份解析配置为解析人员与帐户的关系。 必须关联帐户ID、人员ID （[!DNL Marketo]潜在客户ID或CRM联系人ID）和跨设备身份（ECID、电子邮件）。 身份图必须支持B2B数据模型中固有的多对多人员到帐户映射。 | [身份服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home)，[B2B身份解析](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/rtcdp/schemas/b2b) |
| 受众定义和分段 | 假设就位 | 如果将B2B区段从[!DNL CJA]发布回AEP以进行激活，则帐户级别的受众定义应该可用。 对于仅限Analytics的用例，这不是严格的先决条件，但建议对基于区段的分析执行此操作。 | [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么它很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | 帐户配置文件上的计算属性（例如，总参与度分数、上次活动后间隔天数、机会计数）丰富了[!DNL CJA]中可用于帐户级别分析的分析维度。 | [计算属性概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/overview) |
| 数据生命周期管理 | 推荐 | B2B数据集，尤其是来自[!DNL Marketo Engage]的行为事件数据，可能会快速增长。 数据集过期策略可帮助管理存储并确保遵守数据保留要求。 | [高级数据生命周期管理](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-lifecycle/home) |
| 数据使用标签和执行 | 推荐 | B2B数据通常包含敏感的业务信息（合同价值、竞争情报）。 数据使用标签和治理策略可确保在Analytics和激活工作流中正确使用此数据。 | [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home) |
| 监视和可观察性 | 推荐 | B2B源连接器([!DNL Marketo]， [!DNL Salesforce])需要监视摄取运行状况。 [!DNL CJA]中的连接运行状况监视可确保分析的数据刷新。 引入失败的警报规则可防止功能板过时。 | [可观察性分析概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/home) |
| 报告和分析 | 已包含 | 这种模式本身就是一种分析模式。 该功能本身作为核心功能链包含在内，可提供报告和分析功能。 | [CJA概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-overview/cja-overview) |

## 应用程序功能

此计划从“应用程序功能目录”中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Customer Journey Analytics] B2B edition

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 基于帐户的连接 | 阶段1：B2B数据连接 | 使用帐户或全局帐户作为组织级别分析的主要标识符来配置连接 |
| B2B数据视图配置 | 阶段2：帐户数据视图配置 | 使用特定于B2B的容器（帐户、全球帐户、机会、购买组）以及标准人员、会话和事件容器定义数据视图 |
| 帐户级别的Workspace分析 | 阶段3：Workspace分析 | 使用帐户级别的维度、量度和B2B容器构建自由格式分析，以实现组织级别的历程分析 |
| 购买群组分析 | 阶段3：Workspace分析 | 通过购买决策流程分析购买组构成、参与和进度 |
| 机会分析 | 阶段3：Workspace分析 | 跟踪销售机会在funnel各阶段的进展，并与营销参与数据关联 |
| B2B分段 | 阶段3：Workspace分析 | 使用B2B容器创建区段，以进行过滤的帐户级别分析 |
| B2B归因 | 阶段3：Workspace分析 | 将归因模型与B2B销售周期分析的延长13个月的帐户回顾窗口结合使用 |
| 计算指标创建 | 阶段3：Workspace分析 | 定义B2B KPI的计算指标，如帐户参与率、购买组完整性和管道影响 |
| 功能板和记分卡发布 | 第4阶段：功能板发布 | 为营销和销售领导力创建和共享功能板和移动记分卡 |
| 受众发布 | 第4阶段：功能板发布 | 将[!DNL CJA]定义的基于帐户的受众发布回AEP以供下游激活 |

### [!DNL Customer Journey Analytics] — 标准函数

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 数据连接 | 阶段1：B2B数据连接 | 将AEP B2B数据集绑定到[!DNL CJA]连接以进行跨渠道分析 |
| 数据视图配置 | 阶段2：帐户数据视图配置 | 在B2B数据视图中配置标准维度、量度、归因和持久性设置 |
| Workspace Analysis | 阶段3：Workspace分析 | 使用表、流失、流量、同类群组和归因可视化图表构建自由格式分析 |
| 引导式分析 | 阶段3：Workspace分析 | 在帐户级别使用引导式工作流进行funnel、趋势和维系率分析 |

### [!DNL Real-Time CDP] B2B edition

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 帐户个人资料统一 | 先决条件(F2/F4) | 使用专门的XDM B2B架构类将跨源B2B数据整合到统一的帐户配置文件中 |
| B2B身份解析 | 先决条件(F4) | 解决支持多级帐户层次结构和多对多映射的人员到帐户关系 |
| [!DNL Marketo Engage]集成 | 先决条件(F3) | 通过本机B2B源连接器从[!DNL Marketo Engage]中摄取行为参与数据和帐户/潜在客户记录 |

## 先决条件

在实施开始之前，必须准备好以下项目。

- [ ] [!DNL CJA] B2B edition许可证处于活动状态并已为组织配置
- [ ] [!DNL RT-CDP] B2B edition许可证已激活，并配置了B2B架构和帐户配置文件
- [ 已定义]个B2B XDM架构（帐户、机会、帐户人员关系、机会人员关系、营销列表成员）
- [ ] [!DNL Marketo Engage]和/或CRM源连接器已配置并主动摄取数据
- [ ]帐户级别的行为事件数据（Web访问、电子邮件交互、表单提交）通过帐户关联流入AEP
- [ ]在身份图中建立了人员与帐户的关系
- [ ]至少有30天的历史B2B参与数据可用于有意义的分析
- [ ]利益相关者已同意购买组角色定义和解决方案兴趣映射
- [ ] [!DNL CJA]用户帐户已为B2B edition功能配置了适当的产品配置文件
- [ ]目标KPI和报告要求已由营销和销售领导定义

## 实施选项

以下部分介绍了实施此用例模式的不同方法。

### 选项A：以帐户为中心的分析

**最适合于：**&#x200B;希望通过帐户的镜头分析所有参与和管道数据的组织。 此方法使用帐户容器作为主要分析单位，自上而下查看帐户在购买历程中的进度。

**工作方式：**

将帐户作为主标识符来配置[!DNL CJA] B2B连接。 所有行为事件、商机和购买群组数据都会汇总到帐户级别。 数据视图使用帐户作为最高级别容器，其中嵌套了“人员”、“会话”和“事件”。 这将启用诸如“有多少客户访问了定价页面，然后在30天内创建了一个销售机会？”这样的分析。

以客户为中心的分析为B2B组织提供了最自然的视图，其中客户是购买单位。 行业、公司规模、帐户层和帐户所有者等维度可用于划分参与模式和管道量度。 归因在帐户级别应用，具有13个月的回溯时段，可适应较长的B2B销售周期。

**关键注意事项：**

- 需要在身份图中进行干净的帐户到人员映射
- 所有人员级别的活动必须归属于一个帐户
- 无法与帐户关联的匿名Web流量将不会显示在帐户级别分析中

**优点：**

- 提供整个购买历程的真实帐户级别视图
- 启用基于帐户的归因，使其与B2B收入的生成方式相匹配
- 支持将购买组和机会分析作为帐户中的嵌套容器
- 使Analytics与基于帐户的营销(ABM)策略保持一致

**限制：**

- 需要强大的人员到帐户身份解析
- 从分析中排除匿名或不匹配的参与数据
- 配置比以人员为中心的分析更复杂

**Experience League：**

- [CJA B2B edition概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [B2B edition架构](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/rtcdp/schemas/b2b)

### 选项B：以全球帐户为中心的分析

**最适合于：**&#x200B;具有复杂帐户层次结构的企业组织，其中母公司具有多个子公司帐户。 此方法使用“全局帐户”作为主要标识符，将所有子公司帐户活动累计至母公司组织层。

**工作方式：**

使用全局帐户而不是帐户将[!DNL CJA] B2B连接配置为主标识符。 这将汇总其父组织下所有子公司帐户的参与数据。 例如，如果“Acme Corp”在地区内设有子公司“Acme EMEA”和“Acme APAC”，则全球客户连接会将来自所有三个实体的所有业务整合到一个分析视图中。

数据视图包括全局帐户作为顶级容器，帐户、人员、会话和事件作为嵌套容器。 这样，您就可以在同一工作区项目中的全局帐户层和子帐户层进行分析。 归因回顾窗口适用于全球帐户级别，捕获整个公司层次结构中的所有接触点。

**关键注意事项：**

- 需要在B2B数据模型中定义父子关系的帐户层次结构数据
- 必须填充全局帐户ID，并在所有帐户记录中保持准确
- 子帐户必须正确映射到其父帐户

**优点：**

- 跨复杂的企业帐户结构提供整合的可见性
- 当单个企业客户有多个帐户记录时，防止进行零散的分析
- 在单个全球账户中实现地区子公司之间的比较
- 支持企业级管道和收入报告

**限制：**

- 需要准确的帐户层次结构数据，而许多组织都难以维护这些数据
- 仅在全球级别查看时，可能会模糊子级别模式
- 建立和维护层次结构关系的额外数据建模工作

**Experience League：**

- [CJA B2B edition概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### 选项C：混合人员+帐户分析

**最适合：**&#x200B;从基于人员的分析过渡到基于帐户的分析的组织，或者同时需要人员级别和帐户级别视图的组织。 此方法通过相同的连接创建两个数据视图 — 一个以人员为中心，一个以客户为中心。

**工作方式：**

配置包含所有B2B数据集（事件、帐户、商机、购买组、人员 — 帐户关系）的单个[!DNL CJA] B2B连接。 然后，创建两个数据视图：一个使用人员作为主容器（与标准[!DNL CJA]类似），另一个使用帐户作为主容器。 分析人员可以根据所询问的问题在数据视图之间切换。

以人员为中心的数据视图提供传统的个人级别历程分析（例如，“成为机会的潜在客户的转化路径是什么？”），而以客户为中心的数据视图提供组织级别的分析（例如，“哪些客户的参与到管道的转化率最高？”）。 两个视图使用相同的底层数据，从而确保一致性。

**关键注意事项：**

- 需要两个数据视图，它们具有潜在的不同维度和量度配置
- 分析人员需要培训如何使用每个视图
- 可能需要为每个数据视图单独创建计算指标

**优点：**

- 提供在人员和帐户级别分析数据的灵活性
- 对于习惯于人员级别分析的团队来说，采用方法更简单
- 启用人员级别和帐户级别量度之间的比较
- 支持基于潜在客户和基于客户的营销策略

**限制：**

- 两个要维护和保持同步的数据视图
- 对于分析人员来说，在要使用哪个视图上可能会感到困惑
- 计算指标和过滤器可能需要跨视图进行复制

**Experience League：**

- [创建或编辑数据视图](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [数据视图概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/data-views)

### 选项比较

| 标准 | 选项A：以客户为中心 | 选项B：以全球客户为中心 | 选项C：混合型人员+帐户 |
| --- | --- | --- | --- |
| 最适合 | 具有平面帐户结构的标准B2B | 具有父子层次结构的企业 | 转变企业或双重需求 |
| 复杂性 | 中 | 高 | Medium — 高 |
| 数据要求 | 帐户 — 人员映射 | 帐户层次结构+映射 | 帐户 — 人员映射 |
| 归因范围 | 帐户级别（13个月的回溯） | 全球帐户级别（13个月回顾） | 人员和帐户级别 |
| 匿名数据 | 从帐户视图中排除 | 从全局视图中排除 | 包含在人员视图中，从帐户视图中排除 |
| 需要 | [!DNL RT-CDP] B2B edition，[!DNL CJA] B2B edition | [!DNL RT-CDP] B2B edition，[!DNL CJA] B2B edition，层次结构数据 | [!DNL RT-CDP] B2B edition，[!DNL CJA] B2B edition |
| 维护工作 | 单个数据视图 | 单个数据视图 | 两个数据视图 |

### 选择正确的选项

- **如果贵组织具有扁平的帐户结构（无父子层次结构），并且您的ABM策略在个人帐户级别运行，并且您希望获得帐户级别分析的最简单路径，请选择选项A**。
- **如果目标帐户是跨地区或跨部门拥有子公司帐户的大型企业，并且需要在公司母公司层合并报告，请选择选项B**。 此选项需要高质量的帐户层次结构数据。
- **如果您的组织正在从基于潜在客户的营销过渡为基于帐户的营销，您的分析人员需要人员级别的funnel分析和帐户级别的参与度分析，或者您同时拥有B2B和B2C业务线，请选择选项C**。

## 实施阶段

以下阶段概述了建议的实施顺序。

### 阶段1：B2B数据连接

**应用程序函数：** [!DNL CJA] B2B：基于帐户的连接，[!DNL CJA]：数据连接

配置将AEP B2B数据集绑定到[!DNL CJA]以供分析的[!DNL CJA]连接。 此连接定义哪些数据集流入[!DNL CJA]，主要标识符类型（帐户或全局帐户），以及如何摄取历史数据和流式数据。 该连接是所有后续分析的基础。

#### 决策：主要标识符类型

确定连接应使用帐户ID还是全局帐户ID作为主标识符。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 帐户 ID | 平面帐户结构，无父子层次结构 | 设置更简单；每个帐户都独立分析。 面向中小型企业的B2B最常见的选择。 |
| 全局帐户ID | 具有子公司层次结构的企业帐户 | 需要层次结构数据；聚合父项下的所有子公司。 最适合企业ABM计划。 |

#### 决策：数据集选择和类型指定

确定应包含哪些B2B数据集以及如何键入每个数据集。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 事件数据集（行为） | 始终包括 | Web交互、电子邮件事件、表单提交、内容下载。 必须具有时间戳字段。 这些是参与信号。 |
| 帐户记录数据集（个人资料） | 始终包括 | 帐户属性，如行业、大小、层、所有者。 为帐户分析提供维上下文。 |
| Opportunity数据集（查找/配置文件） | 包括用于管道分析 | 机会阶段、值、结束日期。 管道和收入归因分析需要。 |
| 购买群组数据集（查找/个人资料） | 包括用于购买群组分析 | 购买团体角色、参与度分数、完整性。 购买组组合分析所需。 |
| 人员 — 帐户关系数据集（查找） | 始终包括 | 将人员映射到帐户。 对于将人员级别事件与帐户级别分析关联起来至关重要。 |
| 营销活动/项目数据集（查找） | 包括用于归因 | 营销活动元数据、项目类型、渠道。 启用营销活动影响分析。 |

#### 决策：回填范围

确定应将多少历史数据导入连接。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 所有现有数据 | B2B销售周期很长（6-18个月），您需要完整的历史记录 | 建议用于B2B。 对于大型数据集，回填可能需要几天时间，但它提供了完整的归因数据。 |
| 自定义日期范围（过去2-3年） | 数据质量下降到一定程度后 | 在完整性与数据质量之间取得平衡。 当CRM数据具有历史不一致时很常见。 |
| 无回填 | 仅测试或开发 | 只有新数据流入。 不适用于生产B2B分析。 |

#### 配置B2B数据连接

**UI导航：** [!DNL Customer Journey Analytics] >连接>创建新连接

关键配置详细信息：

- 选择包含B2B数据集的AEP沙盒
- 设置产能计划的平均每日事件数
- 添加每个数据集并指定其类型（事件、查找或档案）
- 配置人员ID字段以使用帐户ID或全局帐户ID进行B2B连接
- 为需要近乎实时更新的数据集启用流式传输
- 为历史回填启用“导入所有现有数据”

**选项差异的位置：**

选项A （以帐户为中心）的&#x200B;**：**
将主要标识符设置为帐户ID。 添加帐户记录、商机、购买群和人员 — 帐户关系数据集。 使用“帐户ID”字段配置人员级别事件数据集，以进行跨数据集联接。

选项B （以全局帐户为中心）的&#x200B;**：**
将主要标识符设置为全局帐户ID。 确保帐户层次结构数据包含全局帐户ID字段。 所有数据集必须包含或可连接到全局帐户ID，才能进行正确汇总。

选项C （混合）的&#x200B;**：**
创建与所有B2B数据集的单个连接。 使用帐户ID作为主标识符。 将在第2阶段通过在同一连接上使用不同的数据视图配置来创建以人员为中心的视图。

**Experience League文档：**

- [连接概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-connections/overview)
- [创建或编辑连接](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-connections/create-connection)
- [管理连接](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-connections/manage-connections)
- [CJA B2B edition概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### 阶段2：帐户数据视图配置

**应用程序函数：** [!DNL CJA] B2B： B2B数据视图配置，[!DNL CJA]：数据视图配置

配置定义连接数据在分析中如何显示的数据视图。 对于B2B分析，这包括配置特定于B2B的容器（帐户、商机、购买组），将B2B架构字段映射到维度和量度，使用适合于B2B的回顾窗口设置归因模型，以及为B2B业务逻辑创建派生字段。

#### 决策：容器配置

确定应该启用哪些B2B容器以及如何命名它们。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 帐户+人员+会话+事件 | 不购买分组或机会分析的标准B2B | 最简单的B2B容器层次结构。 帐户是顶级容器。 |
| 客户+机会+人员+会话+事件 | 需要管道和收入分析 | 将机会添加为容器级别，以实现机会范围的分析。 |
| 客户+购买组+机会+人员+会话+事件 | 包括购买群体构成的完整B2B分析 | 最全面。 支持在B2B数据模型的每个级别进行分析。 |
| 全局帐户+帐户+人员+会话+事件 | 全局帐户层次结构分析 | 添加全局帐户作为帐户之上的最高级别容器。 |

#### 决策：B2B量度的归因模型

确定转化量度默认使用的归因模型。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 线性归因（13个月的回溯） | 将相同点数分配给B2B历程中的所有接触点 | 最适合了解营销活动的全部组合。 B2B的建议起点。 |
| U形归因（13个月的回顾） | 强调首次接触和最后接触，将点数分给中间接触 | 突出显示商机创建和机会转化时刻。 在需求生成分析中很常见。 |
| 时间衰减（13个月的回顾） | 较新的接触点应获得更多点数 | 当参与回访间隔是销售就绪性的重要信号时的最佳选择。 |
| 最后接触 | 转换前的最终接触点的简单报告 | 易于理解，但低估了早期营销的价值。 仅用于快速操作报告。 |

#### 决定：B2B的会话定义

确定应如何为B2B参与定义会话。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 30分钟超时（默认） | 标准网站分析会话行为 | Web参与分析标准。 可能会分割较长的内容使用会话。 |
| 扩展超时（60-120分钟） | B2B用户参与更长的研究会议 | B2B购买者通常会花费很长的时间来审查技术内容、定价和文档。 |
| 基于事件的新会话 | 特定事件应始终启动新会话 | 当营销活动点进或演示请求应始终开始新的分析会话时使用。 |

#### 配置帐户数据视图

**UI导航：** [!DNL Customer Journey Analytics] >数据视图>创建新数据视图

关键配置详细信息：

- 选择在第1阶段中创建的连接
- 为组织配置合适的时区和日历类型
- 将容器重命名为与B2B相关的术语（例如，帐户/参与/接触点）
- 将B2B架构字段映射到维度：帐户名称、帐户ID、行业、公司规模、帐户层、帐户所有者、机会阶段、机会值、购买组角色、解决方案兴趣
- 映射参与量度：事件（发生次数）、人员、会话、页面查看、表单提交、电子邮件打开、电子邮件点击次数
- 配置关键维度的持久性（例如，帐户行业在帐户级别持续存在）
- 将归因设置为线性归因，并将13个月的回溯设置为转化量度的默认归因
- 为营销渠道分类、参与度评分层和机会阶段分组创建派生字段

**选项差异的位置：**

选项A （以帐户为中心）的&#x200B;**：**
将帐户用作顶级容器来配置单个数据视图。 如果需要管道和购买组分析，则包括“机会”和“购买组”容器。

选项B （以全局帐户为中心）的&#x200B;**：**
将全局帐户配置为顶级容器。 包括帐户作为子容器，以启用全局分析和子容器分析。

选项C （混合）的&#x200B;**：**
从同一连接创建两个数据视图。 数据视图1使用人员作为主容器（标准[!DNL CJA]行为）。 数据视图2使用帐户作为具有B2B容器的主容器。 将相同的量度映射到两个视图（如果适用）。

**Experience League文档：**

- [数据视图概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/data-views)
- [创建或编辑数据视图](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [组件设置概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [持久性设置](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [归因设置](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [派生字段](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [会话设置](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/session-settings)

### 第3阶段：Workspace分析

**应用程序功能：** [!DNL CJA] B2B：帐户级别的Workspace Analysis，购买群组分析， Opportunity Analysis， B2B分段， B2B归因，[!DNL CJA]： Workspace Analysis，计算指标创建，引导式分析

构建可提供KPI中定义的分析见解的工作区项目。 此阶段包括使用B2B维度和量度构建自由格式表、创建B2B KPI的计算量度、配置特定于B2B的可视化图表（帐户级别流量、商机funnel、购买团体参与）、使用B2B容器创建过滤器/区段以及应用B2B归因模型。

#### 决策： Analysis Workspace结构

确定应如何组织工作区项目。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 具有多个面板的单个综合项目 | 小团队，所有利益相关者查看相同的报告 | 更易于维护。 使用面板分隔主题（参与、管道、归因）。 每个项目最多40个面板。 |
| 按受众划分多个重点项目 | 不同的利益相关者需要不同的观点 | 营销获得参与度/归因。 销售人员获取管道/帐户运行状况。 操作可获取数据质量。 更多的维护，但更有针对性。 |
| 具有引导式分析的基于模板的项目 | 面向非专家用户的自助式分析 | 对funnel和趋势视图使用引导式分析。 另存为模板，以供进行可重复的分析。 最适合广泛采用。 |

#### 决策：B2B计算指标

确定B2B KPI所需的计算量度。

| 量度 | 公式 | 创建时间 |
| --- | --- | --- |
| 帐户参与率 | （帐户事件总数/帐户总数） | 始终 — 核心B2B量度 |
| 购买组完整性% | （已填写的角色/所需角色）* 100 | 在购买组分析时 |
| 客户到业务机会的转换 | 具有商机/参与客户的客户 | 需要管道分析时 |
| 管道影响% | 受影响的管道值/总管道值 | 当需要营销归因时 |
| 每个联系人的平均参与度 | 每个帐户的事件/独特访客 | 需要客户渗透分析时 |
| 按角色显示的内容参与度 | 按购买组角色过滤的事件 | 需要针对B2B进行内容优化时 |

#### 决定：B2B过滤器/区段范围

确定应在哪个容器级别创建过滤器。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 帐户级别筛选器 | 按帐户匹配标准（例如，企业帐户、特定行业）划分范围的分析 | 包括合格客户的所有活动。 最常见于B2B。 |
| 机会级别的过滤器 | 范围限定于特定机会类型或阶段的分析 | 包括与合格商机相关的所有事件。 |
| 购买群组级别过滤器 | 范围限定于特定购买组状态的分析 | 包括来自符合购买资格条件的购买小组的人员的事件。 |
| 人员级别过滤器 | 范围限定为符合条件的个人（例如，特定角色、标题）的分析 | 标准过滤器行为。 在B2B上下文中分析个人参与时使用。 |

#### 构建工作区分析

**UI导航：** [!DNL Customer Journey Analytics] > Workspace >项目>创建项目

关键配置详细信息：

- 选择在阶段2中创建的B2B数据视图
- 使用按参与量度划分的帐户级别维度（帐户名称、行业、层）构建自由格式表
- 创建机会funnel可视化图表，显示各个阶段的机会进展
- 构建购买组组合表，其中显示每个角色的角色填充率和参与度
- 配置B2B归因面板，将归因模型（线性、U形、时间衰减）与13个月的回溯进行比较
- 创建显示购买历程通用路径的帐户流可视化图表
- 构建同类群组表以分析一段时间内的帐户保留和重新参与
- 应用B2B筛选器以按客户层、行业或参与级别进行区段分析
- 为重要事件（营销活动发布、产品版本、定价变化）创建注释

**Experience League文档：**

- [Workspace概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/home)
- [创建项目](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [自由格式表](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [“归因”面板](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [流量可视化](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [流失可视化](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [同类群组表](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [过滤器概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [计算量度概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [创建计算量度](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [批注概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/annotations/overview)
- [指导分析概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/guided-analysis/overview)
- [划分维度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

### 第4阶段：功能板发布

**应用程序功能：** [!DNL CJA]：功能板和记分卡发布，[!DNL CJA]：受众发布

创建可共享的功能板和移动记分卡，为利益相关者提供B2B分析见解。 此阶段还包括将[!DNL CJA]定义的B2B受众发布回AEP，以便在下游用例（如B2B受众激活）中进行激活。

#### 决策：功能板交付方法

确定应如何向利益相关者提供B2B分析见解。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| Workspace项目（桌面） | 需要交互式探索的分析人员和营销操作 | 完全交互、向下钻取、筛选器切换。 需要[!DNL CJA]访问权限。 |
| 移动记分卡 | 需要一览KPI的管理人员和销售领导 | 带有趋势线的汇总数字。 可通过[!DNL Adobe Analytics]功能板应用程序访问。 交互性有限。 |
| 已计划PDF/CSV导出 | 没有[!DNL CJA]访问权限的利益相关者需要定期更新 | 按计划自动交付。 无交互性。 最适合每周/每月执行摘要。 |
| 以上全部 | 具有多种利益相关者需求的大型组织 | 最大范围。 维护工作量更大。 推荐用于成熟的B2B分析程序。 |

#### 决定：从[!DNL CJA]发布受众

确定是否应将B2B区段发布回AEP以进行激活。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 发布基于帐户的受众 | Analytics分析应该有助于定位和抑制 | 通过[!DNL RT-CDP]启用激活[!DNL CJA]定义的区段（例如，“没有开放机会的高度参与的帐户”）。 刷新节奏：每周4小时。 |
| 不发布 | Analytics仅适用于报表，不适用于激活 | 更简单的配置。 在[!DNL RT-CDP]中单独处理激活。 |

#### 发布功能板和受众

**UI导航：** [!DNL Customer Journey Analytics] >项目>共享（适用于Workspace），项目>创建>移动记分卡（适用于记分卡），组件>受众>发布（适用于受众发布）

关键配置详细信息：

- 使用关键B2B KPI（总参与帐户、管道值、购买团体完整性）的概要数字构建执行仪表板
- 为趋势指标配置比较时段（月同比、季度同比）
- 创建移动记分卡，并为帐户参与、管道运行状况和归因量度创建图块
- 添加过滤器让管理人员按地区、行业或客户层切换视图
- 为每周执行报告配置计划项目交付
- 对于受众发布：选择B2B过滤器，配置身份命名空间（帐户ID），并设置刷新节奏

**Experience League文档：**

- [创建移动记分卡](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [共享项目](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [计划项目](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [配置和策划记分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics功能板 — 执行指南](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [受众概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [创建并发布受众](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-components/audiences/publish)

## 实施注意事项

以下部分涵盖在实施过程中要牢记的护栏、常见隐患、最佳实践和权衡取舍决定。

### 护栏和限制

- [!DNL CJA]连接只能包含来自一个AEP沙盒的数据集 — [CJA护栏](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-admin/guardrails)
- 每个数据视图最多5,000个维度和5,000个量度
- 每个数据视图最多100个派生字段
- B2B归因支持帐户级别分析的最长13个月的回溯时段
- 所有沙盒中每个[!DNL CJA]客户最多有75个已发布受众
- 受众发布的最低刷新节奏为每4小时
- 从AEP到[!DNL CJA]的流延迟通常在90分钟之内
- 自由格式表支持深度多达10个维度细分
- 移动记分卡支持每个记分卡最多16个磁贴
- Workspace项目每个项目最多支持40个面板
- 回填大型B2B数据集（数十亿条记录）可能需要几天才能完成

### 常见陷阱

- **不完整的人员到帐户映射：**&#x200B;如果人员级别事件无法与帐户关联，则这些事件将不会显示在帐户级别分析中。 确保所有事件数据集都包含一个可与帐户ID连接的字段，该字段可直接连接或通过人员 — 帐户关系查找数据集连接。 审核缺少帐户关联的事件百分比，然后再构建分析。
- **数据集类型指定不正确：** B2B查找数据集（商机、购买群、人员 — 帐户关系）必须在[!DNL CJA]连接中正确指定为查找或配置文件类型。 将查找数据集错误键入为事件数据集将产生错误结果，因为[!DNL CJA]将尝试将每个记录视为带有时间戳的事件。
- **归因时段对于B2B太短：**&#x200B;使用默认的30天归因时段将错过通常跨越6-18个月的B2B历程中的早期接触点。 始终为B2B归因量度配置13个月的回溯时段。
- **错误地混合了帐户级别和人员级别的量度：**&#x200B;在帐户级别分析中计算“人员”可能会产生误导。 确保在相应的容器级别定义计算指标。 “帐户参与率”应使用帐户级别的事件，除以帐户，而不是人员。
- **过时的购买群组数据：**&#x200B;购买群组组合和角色分配会随着时间的推移而发生变化。 如果未定期刷新购买组数据集，则完整性量度将不准确。 确保源系统（[!DNL Marketo Engage]或[!DNL AJO] B2B edition）正在积极同步购买组数据。
- **重载单个工作区项目：** B2B分析跨越参与、管道、归因和购买群组。 尝试将所有内容放在一个项目中会导致加载缓慢和导航混乱。 使用多个重点项目或标签明确的面板。

### 最佳实践

- 即使您计划稍后使用选项B（全球帐户），也从选项A（以帐户为中心）开始。 以客户为中心的分析更加简单，并在增加层次结构复杂性之前验证您的数据模型。
- 创建一个专用的“B2B数据质量”工作区项目，以跟踪与帐户关联的事件百分比、孤立帐户的数量以及购买组完整性量度。 每周运行一次以及早发现数据问题。
- 使用派生字段根据帐户级别事件计数创建参与度评分层（高/Medium/低）。 这简化了分析，并使功能板对于非技术利益相关者更易于操作。
- 在配置B2B归因时，请从线性归因作为基线开始，然后与U形和时间衰减模型进行比较。 模型之间的差异通常会揭示营销组合是注重知名度活动还是转化活动。
- 发布“B2B执行摘要”移动记分卡，其中不超过8个磁贴，涵盖对领导层最重要的各项KPI。 重点突出 — 执行记分卡应该能回答“我们表现如何？” 而不是“为什么？”
- 在关键事件（产品发布、重大促销活动发布、定价变化、销售流程变化）中添加批注，以提供数据趋势的上下文。 B2B数据通常显示了在没有事件上下文的情况下无法解释的尖峰和低谷。
- 从[!DNL CJA]发布B2B受众时，请对标准激活区段使用每日刷新，对时间敏感的区段仅使用4小时刷新。 频繁刷新会消耗处理资源。

### 权衡决定

>[!NOTE]
>应根据贵组织的特定要求和限制来评估以下权衡取舍决策。

**数据完整性与分析准确性**

在帐户分析中包含所有人员级别的事件（即使帐户关联较弱的事件）可提高数据完整性，但如果帐户映射不可靠，则可能会降低分析准确性。

- **包含所有活动支持：**&#x200B;全面的参与度量、更高的帐户参与分数、更广的可见性
- **排除不匹配的事件优先：**&#x200B;准确的帐户级别量度、可信的归因、可靠的管道关联
- **建议：**&#x200B;从帐户级别分析中排除不匹配的事件，但将这些事件包含在单独的人员级别数据视图（选项C）中，以了解全貌。 优先改善作为并行工作流的帐户关联数据质量。

**B2B归因回顾窗口长度**

更长的回顾时间范围（13个月）会捕获更多接触点，但可能包括不再与当前购买决策相关的营销活动。

- **更长的回溯（13个月）优惠：**&#x200B;捕获完整的B2B历程，计入认知阶段活动，适应较长的销售周期
- **更短的回顾（6个月）优惠：**&#x200B;专注于最近的参与，减少旧接触点的噪音，更好地反映当前的购买意图
- **推荐：**&#x200B;对于销售周期长（12个月以上）的企业帐户使用13个月的回溯。 对于周期较短的中端市场客户，请使用6个月的回顾。 为每个要比较的窗口创建单独的计算量度。

**单个综合数据视图与多个重点数据视图**

一个包含所有B2B容器和维度的数据视图维护起来更简单，但可能会让分析师不知所措，感到非常复杂。 多个重点数据视图（参与度、管道、归因）更易于使用，但更难以维护。

- **单个视图支持：**&#x200B;一致性、易于维护、单个项目中的跨域分析
- **多个视图优先：**&#x200B;分析人员简单、加载时间更快、针对每个用例量身定制的组件列表
- **推荐：**&#x200B;从单个综合数据视图开始。 如果分析师报告难以找到正确的维度和量度，请在拆分到多个视图之前，在同一个视图中创建策划的组件组。 使用工作区模板引导分析人员了解正确的组件。

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
- [源概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/home)
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
