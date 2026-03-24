---
title: Customer Analytics和Insight生成
description: 了解如何构建跨渠道分析工作区、计算指标和仪表板，以进行行为和性能分析。
solution: Customer Journey Analytics, Experience Platform
exl-id: 235a4eb0-91ae-4030-b90e-7eda08c67ae1
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '8947'
ht-degree: 1%

---

# Customer Analytics和insight生成

本指南为客户分析和insight生成提供了完整的实施参考。 它介绍了如何将[!DNL Adobe Experience Platform]数据集连接到[!DNL Customer Journey Analytics]、配置数据视图、构建自由格式分析工作区、创建计算指标、发布功能板和移动记分卡，以及选择性地将CJA定义的受众发布回[!DNL Adobe Experience Platform]以供激活。

它面向需要了解所有可行的实施路径、它们之间的权衡以及每个阶段所需的配置决策的解决方案架构师、营销技术人员和实施工程师。

与分类法中其他侧重于激活和参与（发送消息、个性化内容、激活受众）的模式不同，此模式侧重于了解 — 分析客户行为、衡量营销活动效果、识别趋势，并生成为战略和优化决策提供信息的见解。 它是最常见的组合模式和与几乎每种激活或个性化模式配对。

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

## 用例模式

**客户分析和insight生成**

构建跨渠道分析工作区、计算指标和仪表板，以了解客户行为和营销活动效果。

**函数链：**&#x200B;数据连接>数据视图配置> Workspace Analysis >计算指标创建>功能板发布

有关组合指导，请参阅[实施选项](#implementation-options)部分。

## 应用程序

在此用例模式中使用以下应用程序。

- **[!DNL Customer Journey Analytics] (CJA)** — 连接、数据视图、工作区分析、引导式分析、计算指标、功能板、受众发布和内容分析
- **[!DNL Adobe Experience Platform] (AEP)** — 为CJA连接提供数据湖、数据集、XDM架构、配置文件和事件数据

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本函数 | 状态 | 必须准备好的内容 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 假设就位 | CJA产品配置文件配置了工作区创建和数据查看访问权限。 AEP数据集可供CJA连接访问。 分配给相应CJA角色的用户。 | [访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | 将连接到CJA的XDM架构和数据集必须存在于AEP中。 架构设计直接影响CJA数据视图中可用的维度和量度。 事件架构需要时间戳字段；查找架构需要关键字段。 | [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| 数据源和收集 | 必填 | 数据必须流入AEP数据集 — 通过Web SDK的Web事件、通过Mobile SDK的应用程序事件、AJO促销活动事件、通过源连接器的CRM数据。 分析的丰富程度取决于所收集数据的广度。 | [源概述](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| 身份和配置文件配置 | 必填 | CJA连接中的人员ID配置决定了如何跨数据集拼合事件。 AEP中的跨设备身份拼接可提高CJA构建完整客户历程的能力。 必须为人员ID字段配置身份命名空间。 | [Identity Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| 受众定义和分段 | 不适用 | CJA在分析上下文中构建自己的过滤器和受众。 RT-CDP受众不是先决条件，但CJA可以通过受众发布将受众发布回AEP（选项C）。 | [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么它很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | AEP计算属性可以丰富连接到CJA的数据集，从而提供额外的维度和指标以供分析（例如，生命周期购买计数、距上次活动间隔天数）。 这些配置文件级聚合在CJA数据视图中可用作维度。 | [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 数据生命周期管理 | 推荐 | 数据集保留策略会影响CJA中可用的历史数据。 分析通常需要长期保留，才能进行年度同期比较和长期趋势分析。 配置数据集TTL以确保足够的历史深度。 | [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 数据使用标签和执行 | 推荐 | 敏感字段上的治理标签可以限制CJA数据视图中显示的内容。 如果CJA连接中包含PII或敏感数据，则数据管理标签可确保合规访问，并防止在共享功能板中未经授权地暴露数据。 | [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| 监视和可观察性 | 推荐 | CJA连接的运行状况和数据刷新情况应受到监控。 为源数据流故障和摄取问题配置警报，以确保数据馈送CJA可靠且最新。 | [可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 报告和分析 | 已包含 | 这是报告和分析实施。 当其他模式的参考计划包含S5时，请将此客户分析和insight生成计划用于Analytics实施。 | [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## 应用程序功能

此计划从应用程序功能目录中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Customer Journey Analytics] (CJA)

下表列出了此模式中使用的CJA应用程序函数。

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 数据连接 | 阶段1：数据连接 | 将AEP数据集绑定到CJA连接以进行跨渠道分析，并配置数据集类型和人员ID以进行跨数据集拼接 |
| 数据视图配置 | 阶段2：数据视图配置 | 定义维度、量度、归因模型、持久性设置、会话参数以及影响分析透视图的派生字段 |
| Workspace Analysis | 阶段3：分析和量度创建 | 使用表、可视化图表、过滤器、注释和维度细分（选项A、B、C）构建自由格式分析项目 |
| 引导式分析 | 阶段3：分析和量度创建 | 将结构化引导式工作流用于funnel、趋势、维系、用户增长和参与频度分析（选项D） |
| 计算指标创建 | 阶段3：分析和量度创建 | 使用公式、过滤器和函数为可重用KPI定义计算量度，如转化率、参与度分数和每次访问收入 |
| 功能板和记分卡发布 | 第4阶段：功能板发布 | 创建和共享交互式仪表板和移动记分卡，用于利益相关者报告 |
| 受众发布 | 阶段5：受众发布（仅限选项C） | 将CJA定义的受众发布回AEP实时客户配置文件以供下游激活 |
| Content Analytics | 阶段3：分析和量度创建 | 分析数字资产中的内容性能趋势、异常和疲劳（当内容分析成为焦点时） |

### [!DNL Adobe Experience Platform] (AEP)

下表列出了此模式中使用的AEP应用程序函数。

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 数据湖和数据集 | 先决条件(F2、F3) | 提供用于CJA连接的源事件、配置文件和查找数据集 |
| 身份服务 | 先决条件(F4) | 在CJA连接中提供用于跨数据集拼合人员ID的标识命名空间配置 |

## 先决条件

在实施此用例模式之前，必须满足以下先决条件。

- [ 已为组织配置]个CJA产品权利
- [ ]个CJA产品配置文件配置了适当的用户访问权限（工作区创建、数据视图访问权限）
- [ ] AEP沙盒包含具有数据流的目标数据集（Web事件、应用程序事件、营销活动数据、CRM记录）
- [ 为具有相应字段组的所有源数据集定义了] XDM架构
- [ ]人员ID字段已识别，并且在将连接的所有数据集上始终可用
- [ 在AEP中为CJA连接拼接中使用的个人ID配置了]身份命名空间
- [ ]利益相关者要求已记录 — 哪些KPI、哪些受众将使用功能板、详细程度如何
- [ ]对于移动记分卡：利益相关者已安装[!DNL Adobe Analytics]功能板移动应用程序
- [ 选项C（受众发布）的]：目标沙盒中已启用AEP实时客户个人资料
- [ 选项D （引导式分析）的]： CJA SKU包含引导式分析功能

## 实施选项

此部分介绍此用例模式可用的实施选项。

### 选项A：促销活动效果分析

**最适合：**&#x200B;衡量和优化促销活动和历程效率 — 电子邮件促销活动功能板、历程funnel分析、渠道绩效比较和营销ROI报告。

**工作方式：**

此选项将AJO营销活动和历程数据集连接到CJA，使用投放和参与指标（发送、投放、打开、点击、退回、取消订阅）配置数据视图，构建营销活动绩效仪表板，并为营销利益相关者发布记分卡。 重点是了解营销活动如何跨渠道和随时间推移而表现。

数据视图配置有特定于营销活动的维度（营销活动名称、历程名称、渠道类型、消息变体）和投放指标。 计算量度是为派生度量创建的，例如打开率、点进率、转化率和每条消息的收入。 功能板使用比较期间提供这些KPI以进行趋势分析。

**关键注意事项：**

- 需要AEP中的AJO营销活动和历程事件数据集
- 归因模型应与组织的活动测量哲学保持一致
- 考虑同时包含AJO原生报表（用于运营投放指标）和CJA（用于跨渠道业务影响）

**优点：**

- 为活动测量和优化而专门构建
- 支持跨营销活动比较和渠道组合分析
- 计算指标在所有营销活动中提供标准化的KPI定义
- 移动记分卡为营销主管提供一目了然的性能

**限制：**

- 仅限于campaign和历程数据；不提供完整的客户历程上下文
- 不包括历程路径、流失或同类群组分析
- 归因的适用范围是促销活动接触点，而不是整个客户历程

**Experience League：**

- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### 选项B：Customer journey Analytics

**最适合：**&#x200B;了解跨Web、应用程序、电子邮件、CRM和离线接触点的跨渠道客户历程 — 流失分析、路径分析、同类群组保留、归因建模和生命周期阶段分析。

**工作方式：**

此选项可连接多个AEP数据集（Web事件、应用程序事件、CRM数据、活动交互、事务记录），以构建客户历程的统一跨渠道视图。 数据视图配置了跨所有渠道的维度和量度。 CJA的流量、流失、同类群组和归因可视化图表用于分析客户如何在历程中移动、客户流失在哪里、不同区段如何保留，以及哪些渠道应该获得转化点数。

这是最全面的分析性选项，可让insight深入了解端到端客户体验。 此外，实施过程也是最复杂的，需要谨慎的人员ID配置以进行跨数据集拼接，并需要深思熟虑的数据视图设计以公开正确的维度和量度。

**关键注意事项：**

- 需要所有连接的数据集均具有一致的人员ID，以便进行准确的跨渠道分析
- AEP中的架构设计直接影响CJA分析的质量和深度
- 连接中的数据集越多，意味着分析越丰富，但回填时间越长
- 归因建模需要明确的转化事件定义

**优点：**

- 实现跨渠道客户历程的可见性
- 全套CJA可视化图表：流量、流失、同类群组、归因、自由格式表
- 支持发现单渠道报表中不可见的见解
- 支持关于客户行为和生命周期的复杂分析问题

**限制：**

- 由于多数据集连接和跨渠道拼接，提高了实施的复杂性
- 需要更多数据视图配置和派生字段的前期规划
- 回填大型多数据集连接可能需要几天时间
- 分析质量取决于底层数据的完整性和一致性

**Experience League：**

- [连接概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [流量可视化](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [流失可视化](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [同类群组表](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [“归因”面板](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)

### 选项C：包含受众发布的Analytics

**最适合：**&#x200B;分析驱动型激活 — 通过CJA分析发现感兴趣的区段，然后将其发布回AEP以通过RT-CDP目标、AJO促销活动或AJO历程进行激活。

**工作方式：**

此选项扩展了选项A或选项B并从CJA发布受众。 分析人员使用跨渠道行为数据和CJA过滤器的全面分析功能在CJA中构建区段，然后将这些受众发布到AEP实时客户档案以供下游激活。 这弥合了insight与操作之间的差距 — 探索性分析期间发现的区段成为可操作的受众，而无需在AEP区段生成器中手动重新创建。

已发布的受众将显示在AEP Audience Portal中，其原始名称为“CJA”，可激活到任何RT-CDP目标，在AJO中用作促销活动目标或用作历程进入条件。

**关键注意事项：**

- 需要在Target沙盒中启用AEP实时客户档案
- CJA连接必须具有可解析为AEP身份命名空间的有效人员ID
- 已发布受众将计入组织的AEP受众权利
- 必须根据激活要求（一次，每4小时，每天，每周）配置刷新频率

**优点：**

- 关闭分析和激活之间的循环
- 使用CJA的跨渠道行为数据实现高价值区段的发现
- 在CJA中定义的受众可以利用AEP区段生成器中不可用的维度和过滤器
- 支持基于分析见解的迭代优化受众标准

**限制：**

- 每个CJA客户最多发布75个受众
- 对于大型数据集，初始受众评估可能需要24小时
- 无法在AEP中编辑CJA发布的受众 — 必须在CJA中进行更改
- 需要基本分析以外的其他身份命名空间和配置文件配置

**Experience League：**

- [受众概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [创建并发布受众](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)

### 选项D：面向产品团队的引导式分析

**最适合：**&#x200B;产品体验分析 — 使用CJA的引导式分析工作流程进行功能采用、用户参与趋势、保留时间分析、funnel转化和发布影响分析，而无需设置复杂的自由格式Workspace项目。

**工作方式：**

此选项使用CJA引导式分析来生成结构化、模板化的insight。 引导式分析提供了预建的分析类型（funnel、趋势、维系、用户增长、参与频率、发布影响、首次使用和时间线），可指导分析师完成结构化的工作流程，以回答特定的产品和体验问题。 它非常适合需要快速而集中的洞察而不需要从头开始构建自由格式项目的产品经理和分析员。

该实施将AEP数据集连接到CJA，使用事件级维度和指标配置数据视图，然后使用引导式分析工作流生成见解。 结果可保存为Workspace项目中的面板，以供进一步自定义。

**关键注意事项：**

- 引导式分析需要包含引导式分析功能的CJA产品权利
- 最适合于产品和体验分析，而不是促销活动效果衡量
- 提供非分析用户更易访问的结构化工作流
- 可与自由格式的Workspace分析结合使用，以便进行更深入的探究

**优点：**

- 降低进入门槛 — 结构化工作流引导用户完成分析
- 专门针对产品体验问题（funnel、维系、增长、影响）而构建
- 加快常见分析问题的使用insight时间
- 保存的分析可以与自由格式分析一起嵌入到Workspace项目中

**限制：**

- 没有自由格式Workspace分析那么灵活
- 仅限于预建的分析类型（funnel、趋势、维系、增长、频率、影响、时间线）
- 区段比较同时支持最多3个区段
- funnel analysis支持最多15个步骤

**Experience League：**

- [指导分析概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [funnel视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [“维系”视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

### 选项比较

下表比较了可用的实施选项。

| 标准 | 选项A：促销活动效果 | 选项B：客户历程 | 选项C：Analytics +激活 | 选项D：引导式分析 |
| --- | --- | --- | --- | --- |
| 最适合 | 营销活动测量和优化 | 跨渠道历程了解 | insight驱动的受众激活 | 产品体验分析 |
| 复杂性 | 低Medium | 高 | 高 | 低 |
| 需要数据集 | AJO营销活动/旅程活动 | 多个跨渠道数据集 | 与A或B相同，外加配置文件标识 | 通过产品交互的事件数据集 |
| 关键可视化图表 | 自由格式表、摘要数字、趋势线 | 流量、流失、队列、归因 | 与A或B相同，外加受众发布 | funnel，趋势，维系，增长 |
| 激活功能 | 否（仅报告） | 否（仅报告） | 是（将受众发布到AEP） | 否（仅报告） |
| 需要受众 | 营销分析员、营销活动经理 | 数据分析师、历程架构师 | 分析员+激活团队 | 产品经理、增长分析师 |
| 使用的CJA函数 | 连接、数据视图、Workspace、计算指标、功能板 | 连接、数据视图、Workspace、计算指标、功能板 | 与A或B相同，外加受众发布 | 连接、数据视图、引导式分析、功能板 |
| 首次insight的时间 | 天 | 周 | 周 | 小时 — 天 |

### 选择正确的选项

请遵循以下指南来选择最符合您需求的实施选项。

- **如果您的主要目标是衡量促销活动效果**，并且您有AJO促销活动数据流入AEP，请从&#x200B;**选项A**&#x200B;开始。它为营销绩效报告提供了最快的价值实现时间。

- **如果您需要了解跨Web、应用程序、电子邮件和离线接触点的完整客户历程**，并且有多个数据集具有一致的人员ID，请选择&#x200B;**选项B**。它提供了最深入的分析能力，但需要在数据视图配置方面进行更多前期投资。

- **如果要通过将CJA发现的区段发布回AEP以在RT-CDP或AJO中激活来根据分析采取行动**，请选择&#x200B;**选项C**。这会扩展选项A或B与受众发布，并且需要AEP实时客户个人资料配置。

- **如果您的团队需要快速的结构化产品洞察**，而不需要复杂的自由格式Workspace项目，并且CJA SKU包含引导式分析，请选择&#x200B;**选项D**。这是回答特定产品体验问题的最快途径。

- **许多组织实施了多个选项**：选项A适用于营销团队营销活动功能板，选项B适用于分析团队的跨渠道分析，而选项D适用于产品团队的自助服务见解。 这些选项共享相同的CJA连接和数据视图基础架构。

## 实施阶段

本节详细介绍了此用例模式的分步实施阶段。

### 阶段1：数据连接

**应用程序函数：** CJA：数据连接

此阶段将配置一个CJA连接，以便将一个或多个AEP数据集绑定到CJA进行分析。 该连接定义哪些数据集流入CJA，如何通过人员ID跨数据集拼合事件，以及如何摄取历史数据和流式数据。 这是AEP的数据湖与CJA之间的基础链接。

#### 决策点

在此阶段必须做出以下决策。

>[!NOTE]
>**决定：选择AEP沙盒**
>
>哪个AEP沙盒包含源数据集？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 生产沙盒 | 生产报表的实时客户数据 | 用于生产功能板和利益相关者报告 |
>| 开发沙盒 | 在生产部署之前测试和迭代 | 用于在提升至生产环境之前进行初始配置和验证 |

>[!NOTE]
>**决策：数据集选择和类型指定**
>
>连接中应包含哪些AEP数据集，应分配哪种类型？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 事件数据集 | 带有时间戳的行为数据（Web交互、应用程序事件、营销活动交互、交易） | 需要时间戳字段；形成大多数分析的核心 |
>| 查找数据集 | 键值参考数据（产品目录、营销活动元数据、存储位置） | 通过共享密钥加入事件数据；仅使用最新状态 |
>| 配置文件数据集 | 人员级别属性（忠诚度级别、生命周期值、CRM属性） | 在人员级别提供扩充；仅使用最新状态 |

>[!NOTE]
>**决定：人员ID配置**
>
>哪个字段用作跨数据集拼接的人员ID？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| CRM ID | 组织具有跨渠道的一致的CRM标识符 | 为已知客户提供最准确的跨渠道拼合 |
>| ECID (Experience Cloud ID) | 主要分析匿名Web/应用程序行为 | 设备范围；不拼合没有标识解析度的设备 |
>| 电子邮件（哈希） | 电子邮件是数据集中的通用标识符 | 在接触点间始终捕获电子邮件时工作正常 |
>| 自定义命名空间 | 组织使用专有标识符 | 必须匹配用于受众发布的AEP标识命名空间（选项C） |

>[!NOTE]
>**决策：回填范围**
>
>应该将多少历史数据导入到连接中？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 所有现有数据 | 进行年度同期比较和长期趋势所需的最大历史深度 | 回填大型数据集（数十亿条记录）可能需要几天才能完成 |
>| 自定义日期范围 | 只有最近的历史是相关的，或者需要考虑存储优化 | 限制可用于分析的历史深度 |
>| 无回填 | 只需要前瞻性分析 | 最快的连接设置；在传入新数据之前，没有可用的历史数据 |

>[!NOTE]
>**决定：流支持**
>
>新数据是否应近乎实时地流入CJA？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 启用流式传输 | 需要近乎实时的报表（摄取AEP后约90分钟内即可获得数据） | 最常用于生产连接；支持及时分析 |
>| 仅批次 | 定期刷新就足够了，无需流式处理 | 配置更简单；数据可在批处理后使用 |

#### 配置数据连接

**UI导航：** CJA >连接>创建新连接

关键配置详细信息：

- 连接名称和描述应遵循组织命名惯例
- 平均每日事件数用于CJA容量规划
- 单个连接中的所有数据集必须来自同一AEP沙盒
- 人员ID字段必须在所有数据集中保持一致，以便进行准确的跨数据集拼合
- 验证人员ID字段是否存在并已填充到每个数据集中，然后再将其添加到连接

**Experience League文档：**

- [连接概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [创建或编辑连接](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [管理连接](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)
- [CJA护栏](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

### 阶段2：数据视图配置

**应用程序函数：** CJA：数据视图配置

此阶段将配置定义连接数据在分析中的显示方式的数据视图。 数据视图确定哪些架构字段作为维度和量度显示、如何归因和保留值、如何定义会话以及哪些派生字段将原始数据转换为分析就绪组件。 对于不同的分析透视，可通过单个连接创建多个数据视图。

#### 决策点

在此阶段必须做出以下决策。

>[!NOTE]
>**决策：容器命名**
>
>容器应使用哪些术语来匹配业务域？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 默认（人员/会话/事件） | 团队可理解标准分析术语 | 适用于大多数实施 |
>| 自定义名称（例如，购物者/访问/互动） | 特定于业务领域的术语可提高用户采用率 | 帮助非技术利益相关者了解分析的范围 |
>| B2B名称（例如，帐户/参与/接触点） | 以帐户级别分析为中心的B2B分析 | 使容器范围与B2B业务概念保持一致 |

>[!NOTE]
>**决定：会话超时**
>
>非活动状态持续时间定义会话边界？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 30分钟（默认） | 标准网站分析会话定义 | 行业标准；与大多数分析基准保持一致 |
>| 15 分钟 | 用户可快速完成任务的短格式内容或事务性站点 | 创建更多会话；可能更好地捕获不同的用户意图 |
>| 60分钟或更长 | 长格式内容、复杂的B2B交互或大量研究的历程 | 减少会话；将扩展的研究捕获为单个会话 |
>| 通过新会话事件进行自定义 | 某些事件（例如，应用程序启动、促销活动点进）应始终启动新会话 | 提供业务逻辑驱动的会话边界 |

>[!NOTE]
>**决策：归因模型默认值**
>
>应将哪个默认归因模型应用于转化量度？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 最近联系（默认） | 点数应转到转化前的最新接触点 | 简单直观；可能低估了意识渠道 |
>| 首次接触 | 了解哪些渠道可推动初始意识和客户获取 | 有助于客户获取分析；忽略培养接触点 |
>| 线性 | 所有接触点应共享相同的点数 | 公平分配；可能稀释关键接触点的影响 |
>| 时间衰减 | 最近的接触点应比遥远的接触点获得更多的点数 | 将回访间隔与历史贡献进行平衡 |
>| U型 | 第一个和最后一个接触点应获得最大点数 | 有助于了解客户获取和结束渠道 |
>| 算法 | 使用CJA的AI模型的数据驱动归因 | 最准确，但需要足够的转化数据量 |

>[!NOTE]
>**决策：派生字段逻辑**
>
>是否需要自定义业务规则将原始数据转换为分析就绪的维度？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 营销渠道分类（案例条件） | 原始跟踪代码需要分类为渠道组 | 最常见的派生字段用例；对于渠道分析至关重要 |
>| 值分段 | 连续值需要分组为多个范围（例如，订单值层） | 简化了对连续量度的分析 |
>| 字段合并 | 多个源字段应合并为一个维度 | 当数据集之间的不同架构路径中存在相同的概念时，此模型非常有用 |
>| 基于正则表达式的提取 | 需要解析结构化值（例如，从营销活动代码中提取营销活动类型） | 功能强大，但需要仔细的正则表达式模式设计 |

#### 配置数据视图

**UI导航：** CJA >数据视图>创建新数据视图

关键配置详细信息：

- 选择在第1阶段创建的父连接
- 配置时区和日历类型以符合报表要求
- 将XDM架构字段映射到具有适当持久性（分配和到期）设置的维度
- 将XDM架构字段映射到具有格式（小数、整数、货币、百分比、时间）和归因设置的量度
- 对维度配置包含/排除规则以过滤掉不相关的值
- 在必要时启用指标去重，以防止重复计数
- 创建用于营销渠道分类、值分段或字段合并的派生字段
- 每个数据视图最多5,000个维度和5,000个量度
- 每个数据视图最多100个派生字段

#### 不同选项的位置

选项A （促销活动效果分析）的&#x200B;**：**

映射特定于促销活动的维度：促销活动名称、历程名称、渠道类型、消息变体、主题行。 映射投放量度：发送、投放、打开、点击、退回、取消订阅。 根据促销活动测量原理配置转化量度的归因。

选项B (Customer Journey Analytics)的&#x200B;**：**

映射跨渠道维度：页面名称、应用程序屏幕、渠道、促销活动、产品、内容类型。 映射所有渠道的参与和转化量度。 配置多个归因模型以进行比较分析。 创建用于渠道分类和历程阶段识别的派生字段。

选项D （引导分析）的&#x200B;**：**

映射与产品体验分析相关的事件级维度和量度：功能名称、用户操作、参与类型。 重点关注定义funnel步骤、维系标准和增长信号的事件。

**Experience League文档：**

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

### 阶段3：分析和量度创建

**应用程序函数：** CJA： Workspace Analysis， CJA：引导式分析， CJA：计算度量创建

此阶段构建分析工作区（自由格式项目或引导式分析）、派生KPI的计算量度、分段分析的过滤器以及关键事件的注释。 这是实现分析价值的地方，即构建可解答业务问题的表格、可视化和量度。

#### 决策点

在此阶段必须做出以下决策。

>[!NOTE]
>**决定：分析方法**
>
>此分析应该使用自由格式的Workspace项目还是引导式分析工作流程？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 自由格式Workspace（选项A、B、C） | 深入探索分析、自定义布局、复杂划分、高级可视化图表 | 最大的灵活性；需要分析人员技能；支持所有可视化类型 |
>| 指导分析（选项D） | 结构化产品洞察，特定问题的快速解答，技术含量较低的用户 | 加快了insight的实施；仅限于预建分析类型；保存到Workspace以供进一步自定义 |
>| 两者 | 组织既需要深入分析，也需要快速的结构化洞察 | 对常见问题使用引导式分析；对Workspace进行深入探讨 |

>[!NOTE]
>**决策：可视化类型**
>
>哪些可视化图表最能传达此用例的见解？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 自由格式表 | 使用维度划分进行详细数据探索 | 大多数分析的基础；支持最多10个划分级别 |
>| 流量可视化 | 了解路径行为（页面流、渠道过渡） | 非常适合历程路径发现；可能复杂且具有高基数 |
>| 流失可视化 | 通过定义的接触点序列测量转化 | 最适合funnel分析；清晰显示每一步的流失情况 |
>| 同类群组表 | 按客户获取同类群组显示一段时间的维系率分析 | 显示不同组的保留情况；对于生命周期分析至关重要 |
>| “归因”面板 | 比较转化量度的归因模型 | 并排模型比较；需要明确的转化事件定义 |
>| 概要数字/变化 | 执行KPI显示与期间比较 | 简洁的量度显示；非常适合仪表板标题 |

>[!NOTE]
>**决定：计算量度公式**
>
>除了基本数据视图量度之外，哪些业务KPI需要计算量度？
>
>| 量度模式 | 公式示例 | 使用时间 |
>| --- | --- | --- |
>| 比率/比率 | 订购/访问 | 转化率、点进率、跳出率 |
>| 已过滤的量度 | 收入（其中渠道=“电子邮件”） | 特定于渠道或特定于区段的衡量标准 |
>| 每项目平均值 | 收入/订单 | 平均订单值，每次访问的收入 |
>| 复合公式 | （收入 — 成本）/收入 | 利润率百分比，ROI计算 |
>| 参与度评分 | 交互的加权总和 | 跨渠道的复合参与度评分 |

#### 配置分析和量度

**UI导航：**

- Workspace： CJA > Workspace >项目>创建项目>空白项目
- 引导式分析： CJA >主页>引导式分析（或Workspace >创建>引导式分析）
- 计算指标： CJA >组件>计算指标>创建
- 过滤器：CJA >组件>过滤器>创建过滤器

关键配置详细信息：

- 选择在第2阶段中创建的数据视图作为项目数据视图
- 为分析设置适当的日期范围和比较时段
- 通过将维度拖到行并将量度拖到列来构建自由格式表
- 添加维度划分以更深层浏览数据（例如，按促销活动、按产品逐页）
- 为特定于受众的分析（人员级别、会话级别或事件级别范围）创建可重用过滤器（区段）
- 添加注释以标记关键业务事件（产品发布、营销活动、事件）
- 设置计算指标格式（小数、百分比、货币、时间）和极性（up表示良好/up表示不良）
- 以查看或编辑权限与CJA用户共享工作区项目

#### 不同选项的位置

选项A （促销活动效果分析）的&#x200B;**：**

使用按投放和参与量度细分的活动维度构建自由格式表。 创建打开率、点进率、转化率、每条消息收入和营销活动ROI的计算指标。 添加趋势可视化图表以跟踪一段时间内的营销活动效果。 比较促销活动变量与区段比较。

选项B (Customer Journey Analytics)的&#x200B;**：**

构建流失可视化图表以确定历程流失点。 创建流量可视化图表以发现跨渠道的导航模式。 构建同类群组表以按客户获取同类群组衡量维系率。 配置归因面板，以比较转化量度的归因模型。 创建历程完成率、跨渠道参与度得分和生命周期阶段转换的计算量度。

选项C （具有受众发布功能的分析）的&#x200B;**：**

从选项A或B构建分析工作区，然后在分析期间标识高值或性能不佳的区段。 创建可捕获这些区段以供在阶段5中发布的CJA过滤器。

选项D （引导分析）的&#x200B;**：**

根据业务问题选择适当的引导式分析类型。 配置关键事件、日期范围、计数方法和区段比较。 将已完成的分析保存为Workspace项目中的面板，以供进一步自定义。

**Experience League文档：**

- [Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [创建项目](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [自由格式表](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [流量可视化](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [流失可视化](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [同类群组表](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [“归因”面板](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [划分维度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [过滤器概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [创建过滤器](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [批注概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [计算量度概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [创建计算量度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [计算量度函数](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [指导分析概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [funnel视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [趋势视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [“维系”视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [活跃增长视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [参与频率视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [发布影响视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/release)
- [Content Analytics](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/content-analytics/content-analytics)

### 第4阶段：功能板发布

**应用程序功能：** CJA：功能板和记分卡发布

此阶段将创建交互式功能板（Workspace项目）和移动记分卡，为利益相关者提供KPI可见性。 功能板通过汇总数字、趋势线、划分和批注提供执行和操作可见性。 移动记分卡通过[!DNL Adobe Analytics]功能板移动应用程序提供一目了然的性能数据。

#### 决策点

在此阶段必须做出以下决策。

>[!NOTE]
>**决策：仪表板类型**
>
>这是桌面Workspace功能板、移动记分卡还是两者？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| Workspace项目（桌面） | 面向分析人员和营销人员的详细交互式功能板 | 全面的可视化功能；支持面板、表格和复杂布局 |
>| 移动记分卡 | 移动设备上面向高管和利益相关者的概览KPI | 限制为16个图块；摘要数字带有趋势迷你图；需要移动设备应用程序 |
>| 两者 | 组织既需要详细分析，也需要执行级别的移动报告 | 单独的工件，但可以共享相同的数据视图和计算指标 |

>[!NOTE]
>**决定：共享模型**
>
>谁应接收仪表板以及如何接收？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 与特定用户共享 | 受众有限，有特定的访问需求 | 最精细的控制；需要单独的用户管理 |
>| 与产品配置文件组共享 | 与组织角色一致的团队级别访问权限 | 高效地在团队内进行分发；通过CJA产品配置文件进行管理 |
>| 计划电子邮件投放 | 未登录CJA的利益相关者周期性PDF/CSV报表 | 自动交付；最大频率为每小时；PDF和CSV格式 |

>[!NOTE]
>**决策：注释可见性**
>
>是否应在功能板趋势线上对关键事件添加注释？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 是 — 创建注释 | 主要营销活动、产品发布、网站事件或季节性事件可能会解释数据趋势 | 批注显示为在线图表和记分卡趋势中的标记；提供数据激增或骤减的上下文 |
>| 否 | 仪表板受众熟悉业务上下文，并且注释会增加杂乱程度 | 更简单的视觉呈现 |

#### 配置仪表板

**UI导航：**

- Workspace功能板： CJA > Workspace >创建项目
- 移动记分卡：CJA >项目>创建>移动记分卡
- 共享：CJA > Workspace >共享>与Workspace用户共享
- 计划提交： CJA > Workspace >共享>计划项目

关键配置详细信息：

- 对于移动记分卡，创建可显示单个量度（具有摘要数字和迷你图趋势）的图块
- 配置默认日期范围和比较时段（例如，最近30天与上一时段或月同期）
- 添加受众范围的过滤器，以便管理员在移动记分卡上切换
- 为周期性PDF或CSV报表配置计划的电子邮件投放
- 每个移动记分卡最多包含16个磁贴；每个Workspace项目最多包含15个面板
- 每个数据视图的注释限制为100个

**Experience League文档：**

- [创建移动记分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [配置和策划记分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics功能板 — 执行指南](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [共享项目](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [计划项目](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [概要数字可视化](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)
- [日期范围](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

### 阶段5：受众发布（仅限选项C）

**应用程序函数：** CJA：受众发布

此阶段将配置CJA受众发布，以将分析发现的区段推送回AEP实时客户档案，以便在RT-CDP目标、AJO促销活动或AJO历程中进行下游激活。

#### 决策点

在此阶段必须做出以下决策。

>[!NOTE]
>**决定：刷新节奏**
>
>受众会员资格的刷新频率如何？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 一次性（快照） | 无需持续刷新的促销活动特定受众 | 没有正在进行的处理；必须重新发布才能进行更新 |
>| 每4小时 | 近乎实时的激活要求 | 处理成本较高；最适合对时间敏感的受众 |
>| 每日 | 标准营销激活节奏 | 新鲜度和成本平衡；最常见选择 |
>| 每周 | 稳定、变化缓慢的受众 | 最小处理；适用于长期区段 |

>[!NOTE]
>**决定：身份命名空间**
>
>CJA应使用哪个身份命名空间进行受众成员解析？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| CRM ID | 组织的主要客户标识符 | 已知客户匹配的最佳准确性 |
>| ECID | 主要基于Web/应用程序的受众 | 设备范围；可能无法解析为所有的配置文件记录 |
>| 电子邮件（哈希） | 电子邮件是激活的常见标识符 | 必须匹配AEP身份配置中使用的命名空间 |
>| 自定义命名空间 | 在整个组织中使用的专有标识符 | 必须在AEP Identity Service中进行配置 |

#### 配置受众发布

**UI导航：** CJA >组件>受众>发布受众

关键配置详细信息：

- 使用CJA过滤器（人员、会话或事件容器范围）定义受众标准
- 选择要发布的数据视图和过滤器
- 配置用于AEP配置文件解析的身份命名空间
- 根据激活需求设置刷新节奏
- 在“CJA受众”列表（“组件”>“受众”>“状态”列）中监控发布状态
- 验证受众是否显示在AEP受众门户中（受众>浏览>按来源“CJA”筛选）
- 每个CJA客户最多发布75个受众（在所有沙盒中）
- 对于大型数据集，初始受众评估可能需要24小时

**Experience League文档：**

- [受众概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [创建并发布受众](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [管理受众](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)
- [受众门户概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-portal)

## 实施注意事项

此部分涵盖此用例模式的护栏、常见隐患、最佳实践和取舍决策。

### 护栏和限制

以下护栏和限制适用于此实施。

- **连接限制：**&#x200B;每个组织的最大连接数受CJA SKU权利限制。 单个连接只能包含来自一个AEP沙盒的数据集。 — [CJA护栏](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)
- **数据视图限制：**&#x200B;每个数据视图最多5,000个维度和5,000个量度。 每个数据视图最多100个派生字段，包含最多5级嵌套函数。
- **Workspace限制：**&#x200B;每个项目最多包含40个面板。 自由格式表支持深度多达10个维度细分。 每个报告请求最多50,000行。
- **记分卡限制：**&#x200B;每个移动记分卡最多有16个磁贴。
- **流延迟：**&#x200B;流数据通常在AEP引入后90分钟内可在CJA中使用。
- **受众发布限制：**&#x200B;每个CJA客户最多发布75个受众。 最低刷新节奏为每4小时。
- **引导式分析限制：** Funnel分析支持最多15个步骤。 区段比较同时支持最多3个区段。

### 常见陷阱

实施此模式时，请注意以下常见问题。

- **数据集之间的人员ID不匹配：**&#x200B;连接中的所有数据集必须使用一致的人员ID字段进行跨数据集分析。 人员ID不匹配会导致客户视图分段，其中同一人员显示为多个人员。 在创建连接之前验证人员ID是否一致。

- **回填耗时意外地长：**&#x200B;包含数十亿条记录的大型数据集可能需要几天的时间才能回填。 在实施时间线内对此进行规划并提前开始回填。 在连接详细信息视图中监控进度。

- **对于大多数维度值显示“未指定”的数据视图：**&#x200B;映射的架构字段可能在源数据中稀疏填充。 在假设发生配置错误之前，请检查源数据集的数据质量。 考虑使用派生字段处理null值。

- **会话计数似乎不正确：**&#x200B;会话超时设置严重影响会话范围的量度。 超短超时会导致更多的会话；超长超时会导致更少的会话。 新会话开始事件也可能意外地分割会话。 根据已知的用户行为模式查看和测试会话设置。

- **归因模型未按预期应用：**&#x200B;归因模型仅适用于量度，不适用于维度。 验证回看窗口是否针对业务周期进行了适当设置。 短回顾窗口可能会错过funnel早期的接触点。

- **返回零或意外值的计算度量：**&#x200B;验证公式中引用的基本度量在目标数据视图中是否包含选定日期范围的数据。 检查比率指标中除以零的情况。 检索量度定义并验证公式结构。

- **受众发布失败（选项C）：** CJA连接必须具有可解析为AEP身份命名空间的有效人员ID。 验证身份命名空间配置以及目标沙盒中是否启用了AEP实时客户配置文件。

### 最佳实践

请遵循这些最佳实践以获得成功的实施。

- **从单个综合连接开始：**&#x200B;创建一个包含所有相关数据集的连接，然后为不同的分析透视图创建多个数据视图。 这样可避免连接激增并简化管理。

- **将派生字段用于营销渠道分类：**&#x200B;不要依赖原始跟踪代码，而应使用Case When逻辑创建派生字段以将流量分类到营销渠道。 这可确保跨所有分析的一致渠道报告。

- **创建量度字典：**&#x200B;记录所有计算量度及其公式、预期用途和预期值范围。 与分析团队共享此词典，以确保跨项目一致的量度使用情况。

- **为受众设计数据视图：**&#x200B;为不同的利益相关者群体创建单独的数据视图 — 一个具有以促销活动为中心的维度和量度的营销数据视图，以及一个具有功能和参与维度的产品数据视图。 这简化了每个用户组的组件列表。

- **在所有内容中添加批注：**&#x200B;为促销活动发布、网站更改、技术事件、季节性以及任何可能说明数据趋势的事件创建批注。 注释可在几个月后查看功能板时提供关键上下文。

- **针对手动计算测试计算指标：**&#x200B;在依赖功能板的计算指标之前，请并排运行包含计算指标及其基本组件的报表。 验证计算值与手动计算是否匹配。

- **策略性地使用筛选器：**&#x200B;为常见的分段模式（按地理位置区分的新区段与回访区段、移动设备区段与桌面区段）创建可重复使用的筛选器。 将它们作为面板级别过滤器应用，而不是将它们嵌入每个自由格式表中。

- **定期监视连接运行状况：**&#x200B;检查连接详细信息视图，了解跳过的记录、失败的批次和流延迟。 连接级别的数据质量问题会影响所有下游分析。

### 权衡决定

在规划实施时，请考虑以下取舍。

>[!NOTE]
>**取舍：分析深度与insight使用时间的比较**
>
>选项B(Customer Journey Analytics)提供最深入的跨渠道分析，但需要在连接配置、数据视图设计和派生字段创建方面进行大量前期投资。 选项D（引导式分析）通过结构化工作流加快实施insight的速度，但提供的分析灵活性较低。
>
>- **选项B支持：**&#x200B;全面了解、复杂的多渠道分析、归因建模、自定义KPI开发
>- **选项D支持：**&#x200B;速度、非分析用户的辅助功能、结构化产品体验问题
>- **推荐：**&#x200B;从选项D开始，以便在并行构建选项B基础架构时即时了解产品。 许多组织为不同的团队同时运行这两者。

>[!NOTE]
>**取舍：回填完整性与连接准备情况**
>
>导入所有历史数据可以为年度同期比较和长期趋势分析提供最大分析深度，但回填大型数据集可能需要几天时间。 将回填限制为最近的时间段可加快连接准备工作，但会限制历史分析。
>
>- **所有数据都更适合：**&#x200B;长期趋势分析、年度同期比较、历史较长同类群组分析
>- **有限的回填支持：**&#x200B;连接准备速度更快，进入第一个仪表板的时间更短，存储优化更有效
>- **推荐：**&#x200B;回填支持策略分析的生产连接的所有数据。 将有限的回填用于开发连接和概念验证实施。

>[!NOTE]
>**取舍：单个综合数据视图与多个重点数据视图**
>
>包含所有维度和指标的单个数据视图提供了一个统一的分析工作区，但使用组件列表可能会使用户不知所措。 多个重点数据视图（每个团队或用例一个）简化了组件体验，但需要维护多个配置。
>
>- **单个数据视图支持：**&#x200B;统一分析、跨域划分、更简单的管理
>- **多个数据视图支持：**&#x200B;清理器组件列表、特定于团队的术语、每个用例的不同会话定义
>- **建议：**&#x200B;从一个主数据视图开始，如果组件列表复杂性成为采用障碍，则创建其他重点数据视图。 所有数据视图都可以引用相同的连接。

>[!NOTE]
>**取舍：实时流摄取与仅批量摄取**
>
>在CJA连接上启用流式处理可提供近乎实时的数据（AEP引入后约90分钟内），但会持续处理更多数据。 仅批量摄取会定期处理数据，并且可能会造成延迟。
>
>- **流式处理优惠：**&#x200B;及时报告、监控活动营销活动、近乎实时的仪表板
>- **仅批处理优势：**&#x200B;配置更简单，处理窗口可预测，足以每周或每月报告
>- **建议：**&#x200B;为生产连接启用流式传输。 与及时数据对主动营销活动监控和操作仪表板的价值相比，增量处理成本最低。

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
- [源概述](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
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
