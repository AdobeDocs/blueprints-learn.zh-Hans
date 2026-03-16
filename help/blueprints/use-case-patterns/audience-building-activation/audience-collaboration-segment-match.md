---
title: 具有区段匹配的受众Collaboration
description: 了解如何使用区段匹配在沙盒或组织之间共享和匹配受众区段。
solution: Real-Time Customer Data Platform, Experience Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '6238'
ht-degree: 1%

---


# 使用区段匹配进行受众协作

本指南为在[!DNL Real-Time CDP]和[!DNL Adobe Experience Platform]中使用[!DNL Segment Match]的受众协作提供了全面的实施参考。 它专为需要以隐私安全方式在沙盒或组织之间共享和匹配受众区段的解决方案架构师、营销技术人员和实施工程师而设计。

使用此计划了解可用方法、评估折衷方案，并导航[!DNL Adobe Experience League]以了解详细的配置说明。

[!DNL Segment Match]允许两个或多个[!DNL Experience Platform]组织（或组织内的沙盒）通过共享区段成员资格信息而协作处理受众数据，而无需公开底层PII。 参与者可以估计重叠、共享受众并将匹配的配置文件激活到下游目标。

## 用例概述

组织越来越需要与合作伙伴、子公司或跨业务部门协作处理受众数据，同时保持严格的隐私控制。 受众协作通过启用[!DNL Segment Match]中的安全区段共享来满足此需求，该功能位于[!DNL Real-Time CDP]中，允许两个或更多[!DNL Experience Platform]组织（或沙盒）使用经过哈希处理的隐私安全标识符交换受众成员资格信息。

业务场景通常涉及一个组织（发件人），该组织已构建有价值的受众区段，并想要与合作伙伴组织（接收者）共享该区段，以进行联合定位、禁止或扩充。 在共享之前，双方均可以估计受众重叠以评估价值。 共享后，接收组织可以通过其自己的目标激活匹配的受众。

此模式与标准受众激活不同，因为它在组织或沙盒之间运行，而不是与外部广告或营销目标运行。 它还与数据清理室或第三方协作平台不同，因为它使用[!DNL Experience Platform]身份基础结构在Adobe生态系统中以本机方式运行。

## 主要业务目标

此用例模式支持以下业务目标。

### 获取新客户

通过有针对性的客户获取促销活动、相似受众和付费媒体优化来扩展客户群。 受众协作使组织能够通过将其区段与合作伙伴受众匹配、识别高价值重叠以及通过联合激活接触全新客户来发现新的潜在客户池。

- **KPI：**&#x200B;新客户、客户获取成本、潜在客户/潜在客户转化
- [获取新客户](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### 降低客户购置成本

提高定位效率，抑制现有客户参与客户获取促销活动，并优化媒体支出。 通过跨组织或业务部门共享抑制区段，团队可以避免在已转化客户上浪费支出，并将预算集中在真正的新客户上。

- **KPI：**&#x200B;客户获取成本，每个潜在客户的成本，效率
- [降低客户购置成本](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### 优化营销支出和ROI

通过更好的定位、归因、受众抑制和预算分配提高营销投资回报。[!DNL Segment Match] 支持跨组织受众抑制和联合定位，从而减少重复并提高准确性。

- **KPI：**&#x200B;成本节约、客户获取成本、递增收入
- [优化营销支出和ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## 战术用例示例

- **发布者 — 广告商受众匹配** — 品牌与媒体发布者共享其高价值客户区段，以评估重叠并定位与个性化广告匹配的用户，从而提高促销活动相关性而又不公开PII。
- **控股公司内的跨品牌抑制** — 父组织下的多个品牌共享客户区段，以通过收购促销活动抑制姐妹品牌的现有客户，从而减少浪费的广告支出。
- **零售媒体网络受众扩充** — retailer与CPG品牌合作伙伴共享基于购买的区段，使品牌能够以更高的转化率在retailer的媒体网络上定位经验证的购买者。
- **联合营销合作伙伴受众发现** — 两个非竞争品牌在启动联合营销活动之前评估受众重叠以评估合作伙伴潜力，使用重叠估计验证受众一致性。
- **数据合作区段共享** — 数据合作共享中的组织对受众区段进行了哈希处理，以扩大定位范围，同时维护隐私合规性和数据治理控制。
- **多沙盒受众联合** — 一家全球企业跨地区沙盒共享受众区段，以实现跨市场的一致客户定位，同时遵守地区数据驻留要求。
- **忠诚度计划跨合作伙伴激活** — 忠诚度联盟与参与商户共享忠诚度级别区段，以便每个合作伙伴可以向共享的客户群提供适合级别的促销活动。
- **测量和归因协作** — 广告商与媒体合作伙伴共享转化区段，以便合作伙伴可以通过将公开的用户与转化者进行匹配来衡量促销活动的有效性。

## 关键绩效指标

以下KPI有助于衡量受众协作实施是否成功。

| KPI | 描述 | 测量方法 |
| --- | --- | --- |
| 受众重叠率 | 共享区段中发件人和接收者之间匹配的配置文件百分比 | [!DNL Segment Match]重叠估计报告 |
| 匹配的受众规模 | 成功匹配并可供激活的配置文件数 | [!DNL Segment Match]共享状态和受众群体计数 |
| 从匹配受众获取新客户 | 通过定位匹配区段的营销活动获得的全新客户 | 使用匹配受众跟踪营销活动的转化 |
| 客户购置成本降低 | 使用匹配受众与广泛定位时，降低每次购置成本 | 比较匹配受众与不匹配受众性能的促销活动成本分析 |
| 禁止显示节省 | 通过抑制客户获取促销活动中的已知客户来节省媒体支出 | 前/后抑制媒体支出比较 |
| 营销活动效果提升 | 提高了使用匹配受众的营销活动的转化率、点进率或参与度 | A/B测试比较匹配的受众营销活动与控制 |
| 访问Collaboration的时间 | 从区段共享启动到激活准备状态所经过的时间 | [!DNL Segment Match]工作流时间戳 |

## 用例模式

此用例遵循Audience Collaboration模式。

使用[!DNL Segment Match]在沙盒或组织之间共享和匹配受众区段。

**函数链：**&#x200B;区段选择>匹配配置>重叠估算>受众共享>激活

## 应用程序

在此用例模式中使用以下应用程序。

- **[!DNL Real-Time CDP]** — 提供[!DNL Segment Match]功能以进行隐私安全的受众共享、针对区段创建的受众评估以及针对匹配受众下游使用的目标激活。
- **[!DNL Adobe Experience Platform]** — 提供[!DNL Segment Match]所依赖的基础数据基础架构，包括身份解析、配置文件统一、数据管理和同意执行。

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本函数 | 状态 | 必须准备好的内容 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 必填 | 发件人和接收者组织都必须为沙盒设置适当的角色和权限。 管理[!DNL Segment Match]的用户必须具有查看和共享区段、配置连接和管理合作伙伴馈送的权限。 ABAC策略应配置为控制哪些用户可以启动和接受区段共享。 | [访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 假设就位 | 用户档案和事件的XDM架构必须具有必需的字段组。 必须为[!DNL Real-Time Customer Profile]创建和启用配置文件和事件数据集。 数据模型必须支持用于区段匹配的身份命名空间（通常是经过哈希处理的电子邮件或手机）。 | [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| 数据源和收集 | 假设就位 | 客户数据必须通过配置的数据源（SDK、源连接器、批量摄取）主动流入[!DNL Experience Platform]。 必须使用用于[!DNL Segment Match]的标识类型（例如，经过哈希处理的电子邮件）填充配置文件。 | [源概述](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| 身份和配置文件配置 | 必填 | 必须为区段匹配中使用的标识符配置标识命名空间。 发送者和接收者必须使用兼容的标识命名空间。 必须配置合并策略以正确统一配置文件。 应建立身份关联规则，以确保准确的用户档案解析。 | [Identity Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| 受众定义和分段 | 必填 | 必须先定义和评估Source受众，然后才能通过[!DNL Segment Match]共享。 应使用[!DNL Segment Builder]或[!DNL Audience Composition]构建受众，并完成批次评估。 只有经过批次评估的受众才符合[!DNL Segment Match]共享的条件。 | [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么它很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | 计算属性（如生命周期购买值、参与度得分或产品亲和度）可以创建更精确的区段进行共享。 高质量的输入区段会带来更有价值的受众协作。 | [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 数据生命周期管理 | 推荐 | 同意和数据保留策略可确保共享区段遵守隐私法规。 数据集到期策略有助于管理接收受众数据的生命周期。 同意实施阻止共享已选择退出的配置文件。 | [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 数据使用标签和执行 | 已包含 | 在共享区段之前，必须评估数据治理策略以确保法规遵从性。 身份字段和配置文件属性的标签决定了可以共享的内容。 实施管治可防止将未经授权的数据纳入区段股份。 | [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| 监视和可观察性 | 推荐 | 监控[!DNL Segment Match]共享进程、重叠估计作业和激活数据流有助于及早检测故障。 可以针对共享故障或意外低匹配率配置警报。 | [可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 报告和分析 | 推荐 | 衡量使用匹配受众的营销活动效果可验证协作的价值。[!DNL Customer Journey Analytics] 分析可以比较匹配的受众促销活动与控制组的效果。 | [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## 应用程序功能

此计划从应用程序功能目录中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Real-Time CDP]

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 受众评估 | 阶段1：区段选择和准备 | 使用批次评估来评估区段成员资格，以生成将通过[!DNL Segment Match]共享的受众 |
| 受众构成 | 阶段1：区段选择和准备 | 可以选择撰写派生受众（排名、拆分、排除、扩充）以创建更多目标区段进行共享 |
| 同意和治理实施 | 第2阶段：匹配配置和管理 | 在共享区段之前，强制执行数据使用策略和同意首选项以确保法规遵从性 |
| Audience Activation | 阶段5：匹配的Audience Activation | 将通过[!DNL Segment Match]收到的匹配受众发布到外部目标以进行定位或禁止 |
| 目标配置 | 阶段5：匹配的Audience Activation | 配置与将激活匹配受众的外部目标的连接 |

## 先决条件

- 发件人和接收者组织都为[!DNL Real-Time CDP]设置了[!DNL Segment Match]权利
- 为参与协作的组织或沙盒启用了[!DNL Segment Match]
- 已在[!DNL Segment Match] UI中的发送者组织和接收者组织之间建立合作伙伴连接
- 两个组织都使用兼容的标识命名空间（例如，两个组织都配置了哈希电子邮件）
- 已使用非零群体定义和评估Source受众
- 配置数据治理策略，并将数据使用标签应用于相关数据集和字段
- 双方的用户都拥有管理[!DNL Segment Match]连接、共享和源的必要权限
- 在用户档案中填充同意字段以在共享前启用基于同意的筛选

## 实施选项

以下选项描述了通过[!DNL Segment Match]实现受众协作的不同方法。 选择最适合您的组织结构和协作要求的选项。

### 方案A：直接分部份额（一对一）

此选项最适合于两个特定组织（如广告商和出版商）或联合营销安排中的两个品牌之间的双边合作。

**工作方式：**

在直接的一对一区段共享中，发送者组织选择一个或多个评估的受众，与特定的合作伙伴组织发起共享，接收者接受共享。 在最终确定共享之前，重叠估计会自动运行以向双方显示匹配用户档案的百分比和数量。

发件人定义用于匹配的身份命名空间，并选择要共享的区段。 接收者查看传入的共享并接受，匹配的受众将在其受众列表中可用于下游激活。 只交换经过哈希处理的身份重叠 — 没有任何基础PII或配置文件属性数据跨组织边界。

此方法简单明了，并且为双方提供了完全的控制权。 发送者精确地选择要共享的内容以及与谁共享，接收者可以选择接受或拒绝每个共享。

**关键注意事项：**

- 需要两个组织之间明确设置合作伙伴连接
- 两个组织必须就用于匹配的身份命名空间达成一致
- 重叠估算在承诺之前提供了透明度
- 每个共享都必须单独进行管理和监控

**优点：**

- 简单、通俗易懂的双边工作流程
- 在共享之前通过重叠估计实现完全透明
- 粒度控制 — 发件人精确地选择要共享的区段
- Privacy-safe — 仅使用哈希标识符进行匹配
- 接收者可以选择性地接受或拒绝股票

**限制：**

- 与多个合作伙伴同时协作时，不能高效地扩展
- 每种合作关系都需要分别建立和管理连接
- 必须为每个新区段重复共享配置

**Experience League：**

- [区段匹配概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [区段匹配疑难解答](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### 选项B：多合作伙伴区段分发（一对多）

此选项最适合需要同时与多个合作伙伴共享区段的组织，例如，零售媒体网络与多个品牌广告商共享基于购买的区段，或控股公司将区段分发到附属品牌。

**工作方式：**

在一对多分发模型中，发件人组织与多个合作伙伴组织建立[!DNL Segment Match]连接，并与每个合作伙伴组织共享相同或不同的区段。 发送者管理合作伙伴关系组合，并可根据关系和使用案例有选择地与其他合作伙伴共享不同的受众区段。

每个合作伙伴连接独立运行 — 重叠估计、共享接受和激活按合作伙伴进行管理。 发送者可以控制每个合作伙伴接收哪些区段，从而实现差异化协作策略（例如，高级合作伙伴接收更细粒度的区段，标准合作伙伴接收更广的区段）。

此方法使用与选项A相同的基础[!DNL Segment Match]机制，但将其大规模应用于管理多个并发伙伴关系的操作框架。

**关键注意事项：**

- 需要强大的操作流程来管理多个合作伙伴关系
- 治理策略必须考虑与多个外部方共享相同区段
- 每个合作伙伴可能使用不同的身份命名空间，需要灵活的配置
- 重叠率因合作伙伴而异，需要按合作伙伴进行评估

**优点：**

- 在合作伙伴的生态系统中扩展受众协作
- 每个合作伙伴的差异化共享策略
- 集中管理一个组织的所有出站区段共享
- 每个伙伴关系都保持独立的治理和同意控制

**限制：**

- 操作复杂性会随着每个其他合作伙伴的增加而增加
- 必须按合作伙伴进行监控和故障排除
- 每个新合作伙伴连接都需要进行治理审查
- 合作伙伴不会看到彼此的数据或共享状态

**Experience League：**

- [区段匹配概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)

### 选项C：跨沙盒受众联合

此选项最适合具有多个[!DNL Experience Platform]沙盒（例如，区域沙盒、品牌特定沙盒或环境特定沙盒）且需要跨内部边界共享受众区段而不移动原始数据的大型企业。

**工作方式：**

跨沙盒受众联合使用[!DNL Segment Match]而不是在单独的组织之间共享受众区段，而是在同一组织的沙盒之间共享受众区段。 这使全球营销团队能够在中央沙盒中构建区段并与区域沙盒共享该区段，或允许品牌特定的沙盒相互共享禁止列表。

该工作流反映直接区段份额（选项A），但在组织边界内运行。 沙盒到沙盒连接是通过[!DNL Segment Match]建立的，并且区段使用相同的隐私安全匹配过程共享。 接收沙盒将匹配的受众作为新受众，可通过其自己的本地配置目标激活。

当数据驻留要求不允许在区域之间移动原始客户数据，但允许受众级别的协作时，此方法特别有用。

**关键注意事项：**

- 需要支持跨沙盒共享的[!DNL Segment Match]权利
- 身份命名空间必须在沙盒中保持一致
- 每个沙盒中的合并策略可能会以不同的方式解析配置文件，这可能会影响匹配率
- 治理策略按沙盒独立应用

**优点：**

- 支持受众协作，无需跨沙盒边界移动原始数据
- 支持数据驻留和区域法规遵从性要求
- 利用现有的组织标识基础架构
- 由于共享发生在同一组织内，因此简化了治理审查

**限制：**

- 需要跨沙盒一致的身份命名空间配置
- 匹配率取决于沙盒之间的合并策略一致性
- 无法满足跨组织协作需求
- 可能需要沙盒工具来同步架构和配置

**Experience League：**

- [区段匹配概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)

### 选项比较

下表比较了三个实施选项（基于主要标准）。

| 标准 | 期权A：直接分部份额 | 选项B：多合作伙伴分发 | 选项C：跨沙盒联合 |
| --- | --- | --- | --- |
| 最适合 | 双边伙伴关系 | 生态系统规模的合作 | 内部跨沙盒共享 |
| 复杂性 | 低 | 高 | 中 |
| 合作伙伴数量 | 1 | 许多 | 内部沙盒 |
| 治理开销 | 低 | 高（按合作伙伴审核） | Medium（在组织内） |
| 运营管理 | 简单 | 需要合作伙伴管理框架 | 审核 |
| 数据驻留支持 | 不适用 | 取决于合作伙伴的位置 | 强 |
| 需要 | 合作伙伴连接设置 | 多个合作伙伴连接 | 跨沙盒[!DNL Segment Match] |

### 选择正确的选项

使用以下决定指导选择适当的实施方法：

1. **您是否与外部组织或您自己的组织合作？**
   - 外部组织：进入问题2。
   - 在您自己的组织内（跨沙盒）：选择&#x200B;**选项C** （跨沙盒联合）。

2. **您将与多少外部合作伙伴协作？**
   - 一个合作伙伴：选择&#x200B;**选项A** （直接区段共享）。
   - 多个合作伙伴：选择&#x200B;**选项B** （多合作伙伴分发）。

3. **您是否具有数据驻留限制以防止跨区域移动原始数据？**
   - 是：选择&#x200B;**选项C**，而不管合作伙伴是内部合作伙伴还是外部合作伙伴 — 使用跨沙盒共享来维护数据局部性。

## 实施阶段

以下阶段描述了与[!DNL Segment Match]进行受众协作的端到端实施过程。

### 阶段1：选择和准备区段

**应用程序函数：** [!DNL Real-Time CDP]：受众评估，[!DNL Real-Time CDP]：受众构成

此阶段涉及定义和评估将通过[!DNL Segment Match]共享的受众区段。 必须使用非零群体对源区段进行全面评估，然后才能选择它们进行共享。 此阶段还包括可选的受众组合，以在共享之前优化区段。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决定：受众定义方法**
>
>应如何创建共享的源受众？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 区段生成器（区段规则） | 基于配置文件属性、事件或区段成员资格的标准受众定义 | 支持批量、流式和边缘评估；对于定义标准最为灵活 |
>| 受众构成 | 要求对现有区段执行排名、拆分、排除或扩充操作的派生受众 | 仅支持批量评估；每个沙盒限制为10个合成画布 |
>| 联合受众构成 | 从外部Data Warehouse查询生成的受众，没有将数据摄取到[!DNL Experience Platform] | 需要[!DNL Federated Audience Composition]权利；数据保留在仓库中 |

>[!NOTE]
>
>**决定：受众评估方法**
>
>[!DNL Segment Match]需要批次评估的受众。 应如何计划评估？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 计划批次（每天） | 每日受众刷新足以满足的标准用例 | 默认评估计划；最易于管理 |
>| 按需批处理 | 临时共享需要在您希望立即共享最新受众的位置 | 需要手动触发；对于时效性强的协作很有用 |
>| 自定义计划 | 与合作伙伴激活窗口一致的特定计时要求 | 配置自定义cron计划；更加复杂但精确 |

**UI导航：**&#x200B;客户>受众>创建受众>生成规则（对于[!DNL Segment Builder]）或组合受众（对于[!DNL Audience Composition]）

**密钥配置详细信息：**

- 使用配置文件属性、行为事件和/或区段成员资格定义受众标准
- 确保受众使用的合并策略与用于[!DNL Segment Match]的标识命名空间兼容
- 验证评估后受众群体是否非零
- 应用禁止规则以排除不应共享的用户档案（例如，已选择退出数据共享的用户档案）

**选项差异的位置：**

选项A的&#x200B;**（直接区段共享）：**
准备要与单个合作伙伴共享的特定区段。 注重质量而非数量 — 管理为伙伴关系提供明确价值的区段。

选项B （多合作伙伴分发）的&#x200B;**：**
准备可与不同合作伙伴共享的区段组合。 如果不同的合作伙伴需要不同的受众定义，请考虑创建特定于合作伙伴的区段。 使用一致的命名惯例来管理跨伙伴关系的区段。

选项C （跨沙盒联合）的&#x200B;**：**
确保发送沙盒中的源受众使用接收沙盒中存在的身份命名空间。 验证合并策略是否在沙盒之间对齐。

**Experience League文档：**

- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [受众构成概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [评估方法](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home#evaluation-methods)
- [Profile Query Language参考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 第2阶段：配置匹配和治理

**应用程序功能：** [!DNL Real-Time CDP]：同意和治理实施

此阶段在组织或沙盒之间建立[!DNL Segment Match]连接，配置用于匹配的身份命名空间，并确保数据治理策略允许共享。 治理实施充当策略入口，在共享任何区段数据之前必须先清除该入口。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决策：用于匹配的身份命名空间**
>
>哪个身份命名空间将用于匹配发送者和接收者之间的用户档案？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 哈希电子邮件(SHA-256) | 两个组织都会收集电子邮件地址，并且可以对其进行一致的哈希处理 | 最常见的匹配键；消费者用例的匹配率较高；双方必须使用相同的哈希算法 |
>| 散列电话号码 | 电子邮件并非总是可用，但电话号码始终可用 | 在许多市场中，覆盖率低于电子邮件；这对首先使用移动设备的受众非常有用 |
>| 自定义命名空间（例如，经过哈希处理的忠诚度ID） | 组织共享共同的忠诚度或会员资格计划ID | 已知共享客户群的最高匹配率；需要预先存在的共享ID基础架构 |
>| 多个命名空间 | 最大限度地提高匹配率至关重要，两个组织都有多个一致的标识符 | 提高了匹配率，但增加了复杂性；必须单独配置每个命名空间 |

>[!NOTE]
>
>**决定：数据管理审核**
>
>在共享之前必须完成哪些治理检查？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 标准治理评估 | 标准数据使用标签和策略的典型用例 | 根据数据集标签评估营销操作“导出到第三方”；在共享之前解决任何违规 |
>| 通过同意过滤增强了治理 | 与外部合作伙伴共享，其中必须明确验证同意 | 添加基于同意的过滤以排除未经同意的用户档案（例如，consents.share.val = &#39;n&#39;）；更严格但更安全 |
>| 内部治理审查 | 同一组织内的跨沙盒共享 | 更少的治理要求，因为数据保留在组织边界内；仍验证数据使用标签 |

**UI导航：**&#x200B;客户>受众>区段匹配>合作伙伴连接

**密钥配置详细信息：**

- 通过在发送者组织和接收者组织之间交换连接标识符来建立合作伙伴连接
- 配置将在两侧进行匹配的身份命名空间
- 根据与区段共享关联的营销活动运行数据治理策略评估
- 验证是否填写了用户档案上的同意字段，以及是否排除未共享同意的用户档案
- 查看共享中包含的数据集和架构字段上的数据使用标签

**选项差异的位置：**

选项A的&#x200B;**（直接区段共享）：**
建立单一合作伙伴连接。 使用特定合作伙伴配置身份命名空间。 治理审查重点关注双边关系。

选项B （多合作伙伴分发）的&#x200B;**：**
建立和管理多个合作伙伴连接。 每个合作伙伴可能需要单独进行治理审查。 记录每个伙伴关系的治理批准。 考虑创建治理核对清单，以简化合作伙伴新用户引导。

选项C （跨沙盒联合）的&#x200B;**：**
在组织内建立沙盒到沙盒的连接。 由于共享发生在内部，因此管理通常更简单。 确保各个沙盒中的身份命名空间保持一致。

**Experience League文档：**

- [区段匹配概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [策略实施](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [同意和偏好设置](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

### 阶段3：估计重叠

**应用程序函数：** [!DNL Real-Time CDP]：受众评估（用于估计重叠）

此阶段运行发送者的区段与接收者的配置文件库之间的重叠估计。 重叠估算在确认全部区段份额之前，为双方提供预计的配对数量和百分比，从而能够就协作价值做出明智的决策。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决定：重叠阈值以便继续**
>
>什么最低重叠率证明有理由继续使用完整的区段共享？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 无最小阈值 | 探索性合作关系或任何重叠都能带来价值 | 适用于您正在测试关系的初始协作 |
>| 低阈值(1-5%) | 大规模受众协作，即使重叠很小也代表大量受众 | 对于具有大量受众群的发布者 — 广告商关系来说，这是很常见的做法 |
>| Medium阈值(5-20%) | 预期会有实质性重叠的标准伙伴关系 | 联合营销或同行业协作的典型情况 |
>| 高阈值(20%+) | 必须满足受众高度一致的伙伴关系 | 适用于忠诚度联盟或紧密集成的品牌合作伙伴关系 |

**UI导航：**&#x200B;客户>受众>区段匹配>共享>估计重叠

**密钥配置详细信息：**

- 选择要包含在重叠估计中的区段
- 查看重叠报表，其中显示匹配的用户档案计数和百分比
- 与双方利益相关者共享重叠估计结果以供审批
- 记录重叠量度作为衡量协作效率的基准
- 如果重叠低于可接受的阈值，请考虑调整区段定义或身份匹配配置，然后再继续

**Experience League文档：**

- [区段匹配概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)

### 第4阶段：共享受众

**应用程序函数：** [!DNL Real-Time CDP]：受众评估（用于共享执行）

此阶段执行从发件人到接收人的实际区段共享。 发送者为所选区段发起共享，接收者接受传入共享。 接受后，匹配的受众将作为可用于下游激活的新受众显示在接收者的受众列表中。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决策：共享方向**
>
>此协作的共享模型是什么？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 单向共享（发件人到接收人） | 仅一方提供受众数据的非对称伙伴关系 | 最简单的模型；发件人共享，接收人激活；在广告商 — 发布商关系中常见 |
>| 双向共享 | 双方均受益于相互共享受众 | 两个组织同时充当发送者和接收者；需要两种共享配置；在共同营销合作伙伴中很常见 |

>[!NOTE]
>
>**决定：共享刷新节奏**
>
>应多久刷新一次共享受众一次，并设置更新的区段成员资格？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 一次性共享 | 测试协作或针对具有固定受众的特定营销活动 | 最简单；无持续维护；受众会随着时间的推移而变得陈旧 |
>| 循环共享（与批次评估一致） | 持续存在的伙伴关系，受众成员会发生变化，需要保持最新状态 | 需要监视刷新状态；最常见于生产协作 |

**UI导航：**&#x200B;客户>受众>区段匹配>共享>创建共享（发件人）或接受共享（接收者）

**密钥配置详细信息：**

- 发送者选择要共享的区段，并与配置的合作伙伴启动共享
- 接收者审阅传入共享详细信息（区段名称、估计大小、使用的身份命名空间）
- 接收者接受共享以在其沙盒中创建匹配的受众
- 验证匹配的受众是否显示在接收者的受众列表中，以及是否具有预期的群体
- 确认匹配的受众已正确标记治理跟踪

**选项差异的位置：**

选项A的&#x200B;**（直接区段共享）：**
与您的合作伙伴执行单一共享。 监控共享状态并验证接收器端的匹配受众。

选项B （多合作伙伴分发）的&#x200B;**：**
为每个合作伙伴独立执行股份。 跟踪所有伙伴关系中的共享状态。 考虑交错启动共享以管理处理负载。

选项C （跨沙盒联合）的&#x200B;**：**
执行跨沙盒共享。 匹配的受众将显示在接收沙盒的受众列表中。 验证接收沙盒是否具有用于下游激活的必要目标配置。

**Experience League文档：**

- [区段匹配概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [区段匹配疑难解答](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### 阶段5：激活匹配的受众

**应用程序函数：** [!DNL Real-Time CDP]：目标配置，[!DNL Real-Time CDP]： Audience Activation

此阶段会将匹配的受众（在接收器端）激活到外部目标，以进行定位、抑制或下游使用。 匹配的受众会像接收者沙盒中的任何其他受众一样进行处理，并且可以通过标准目标激活工作流进行激活。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决策：匹配受众的目标类型**
>
>匹配受众应激活到何处？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| Advertising目标（Google、Meta、交易台） | 使用匹配的受众进行广告定位或抑制 | 需要目标连接和身份验证；受特定于目标的速率限制和格式要求的约束 |
>| 云存储目标(S3、Azure、GCS) | 将匹配的受众作为文件导出以供外部系统使用 | 支持文件格式自定义；需要批量导出计划；灵活的下游处理 |
>| CRM/营销自动化目标 | 扩充CRM记录或触发具有匹配受众数据的自动营销工作流 | 需要字段映射到CRM架构；这对于销售营销协调很有用 |
>| Personalization目标（Web、应用程序） | 使用匹配的受众会员资格进行现场个性化 | 需要边缘评估匹配的受众或流激活；延迟因目标而异 |

>[!NOTE]
>
>**决定：激活计划**
>
>匹配的受众应多久导出一次到目标？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 每日增量导出 | 通过定期受众更新进行标准激活 | 仅导出已更改的用户档案；数据量较小；最常见于正在进行的营销活动 |
>| 每日完全导出 | 每次需要完整受众文件的目标 | 更大的数据量；确保目标具有完整的受众状态；某些目标需要完全导出 |
>| 按需激活 | 临时营销活动启动或对时间敏感的激活 | 手动触发器；绕过计划节奏；仅适用于批处理目标 |

**UI导航：**&#x200B;连接>目标>目录（目标设置）或浏览>选择目标>激活受众（激活）

**密钥配置详细信息：**

- 使用适当的身份验证凭据配置目标连接
- 将配置文件属性从匹配的受众映射到目标字段（身份字段、配置文件属性、区段成员资格）
- 配置导出计划（增量与完整、每日与自定义）
- 监控激活数据流以确认已成功导出匹配的受众配置文件
- 验证目标监视视图中的激活指标（导出用户档案，记录失败）

**选项差异的位置：**

选项A的&#x200B;**（直接区段共享）：**
接收者通过其标准目标工作流激活匹配的受众。 除正常目标激活外，不需要任何特殊配置。

选项B （多合作伙伴分发）的&#x200B;**：**
每个接收者组织通过其各自的目标单独激活匹配的受众。 发件人看不到接收方激活。

选项C （跨沙盒联合）的&#x200B;**：**
接收沙盒必须具有自己的目标配置。 目标无法在沙盒之间共享。 确保接收沙盒已建立必要的目标连接。

**Experience League文档：**

- [目的地概述](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [目标目录](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [监测目标的数据流](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [激活护栏](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

## 实施注意事项

在实施之前和期间请查看以下注意事项，以避免常见问题并优化受众协作。

### 护栏和限制

- [!DNL Segment Match]使用哈希标识符进行匹配 — 没有PII跨组织边界。 请参阅[区段匹配概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)。
- 只能通过[!DNL Segment Match]共享批次评估的受众。 在共享之前，必须将流和边缘评估区段转换为批次评估。
- 每个沙盒最多4,000个区段定义适用于源区段和接收的区段。 请参阅[分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)。
- 重叠估计的准确性取决于匹配的标识符的数量。 少量受众可能会显示不太准确的估计值。
- 激活护栏适用于匹配受众的方式与适用于任何其他受众的方式相同 — 每个目标最多100个数据流。 请参阅[激活护栏](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)。
- 合成受众按批量计划评估，每个沙盒限制为10个合成画布。 请参阅[受众组合护栏](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)。

### 常见陷阱

- **发件人和接收者之间的身份哈希不一致：**&#x200B;如果两个组织都哈希电子邮件地址，但使用不同的哈希算法、标准化规则或Salt值，则匹配率将接近于零。 在建立连接之前，双方必须就确切的哈希处理规范（例如，小写、修剪后的电子邮件上的SHA-256）达成一致。
- **共享受众而不进行治理审查：**&#x200B;在不评估数据使用策略的情况下启动区段共享可能会导致违反合规性。 在与外部组织共享区段之前，请始终根据“导出到第三方”营销操作运行治理策略评估。
- **由于身份覆盖率差距导致匹配率较低：**&#x200B;如果发件人的受众主要通过ECID（匿名Cookie）识别，但匹配的命名空间是经过哈希处理的电子邮件，则匹配率将非常低，因为匿名用户档案没有电子邮件地址。 验证源受众是否具有所配置匹配身份命名空间的足够覆盖范围。
- **忘记在接收方接受共享：**&#x200B;在共享被明确接受之前，共享受众不会出现在接收方的受众列表中。 与接收者协调，确保及时被接受，尤其是对于时效性强的营销活动。
- **由于评估计划未对齐而导致匹配的受众过时：**&#x200B;如果发件人的源受众每天进行评估，但[!DNL Segment Match]刷新每周运行，则接收方匹配的受众可能无法反映最新的成员资格。 调整评估并共享刷新节奏。

### 最佳实践

- 在配置[!DNL Segment Match]之前，在组织之间建立正式的数据共享协议。 这应涵盖允许的使用案例、数据治理要求、同意义务和终止程序。
- 在每个主要营销活动之前将重叠估计用作验证工具 — 在提交之前运行估计以确保匹配的受众满足最小大小和质量阈值。
- 将描述性命名惯例应用于包含合作伙伴名称、用例和日期的共享区段（例如“PartnerX_HighValue_Suppression_2026Q1”），以保持组织间的明确性。
- 监测一段时间的匹配率。 匹配率下降可能表明身份覆盖范围下降、数据质量问题或合作伙伴客户群发生变化。
- 对源受众进行分段，以排除没有填充匹配身份命名空间的用户档案。 这提高了匹配率百分比，并提供了更准确的重叠估计。
- 对于双向共享合作关系，请指定区段维护和刷新时间表的明确所有权，以避免混淆负责更新的组织。

### 权衡决定

>[!NOTE]
>
>**取舍：匹配率与隐私控制的对比**
>
>使用更多身份命名空间（经过哈希处理的电子邮件、经过哈希处理的手机、设备ID）进行匹配，可增加匹配率，但会扩大表面区域，以便进行潜在的重新识别。 使用较少的命名空间（仅限哈希电子邮件）可提供更强大的隐私保护，但可能会减少匹配的受众大小。
>
>- **多个命名空间优先：**&#x200B;匹配率更高，匹配受众更多，对营销活动定位更有价值
>- **单个命名空间支持：**&#x200B;更强大的隐私状态，更简单的治理审查，更低的合规性风险
>- **建议：**&#x200B;从单个命名空间开始（哈希电子邮件最常见），仅当匹配率不足以满足用例要求时才添加其他命名空间。 记录每个添加的命名空间的隐私影响评估。

>[!NOTE]
>
>**取舍：区段粒度与操作简单性**
>
>与合作伙伴共享许多粒度、高针对性的区段，会为活动定位提供更大的灵活性，但会增加发件人和接收者的操作复杂性。 共享数量更少、范围更广的区段可简化管理，但会降低定位精度。
>
>- **粒度区段优先：**&#x200B;精确定位、差异化的促销活动、更高的相关性
>- **广泛区段有优势：**&#x200B;更简单的管理，更少的可监控份额，更低的运营开销
>- **建议：**&#x200B;从少量高值区段(2-5)开始新合作关系。 随着伙伴关系的成熟和业务进程的建立，提高精细度。 使用命名惯例和文档可管理随着区段计数增长而增加的复杂性。

>[!NOTE]
>
>**取舍：刷新频率与处理成本**
>
>更频繁地刷新共享受众可使匹配的受众保持为最新，但会增加处理负载，并可能占用更多许可证容量。 不太频繁的刷新降低了成本，但会让匹配的受众变得过时。
>
>- **频繁刷新优惠：**&#x200B;当前受众成员资格、更高的营销活动相关性、更好的隐藏准确性
>- **不经常更新的好处：**&#x200B;处理成本更低、监控更简单、许可证消耗更少
>- **建议：**&#x200B;每日刷新适用于大多数生产协作。 对于时间敏感型用例（例如，闪电促销、基于事件的促销活动），请考虑在促销活动启动之前立即进行按需重新评估和共享。

## 相关文档

以下资源提供了有关此用例模式中所用功能的更多详细信息。

### [!DNL Segment Match]

- [区段匹配概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [区段匹配疑难解答](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### 分段和受众

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [受众构成概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language参考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### 身份和配置文件

- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Real-time Customer Profile概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### 数据治理和同意

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [策略实施](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [同意和偏好设置](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [同意和偏好设置字段组](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

### 目标和激活

- [目的地概述](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [目标目录](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [监测目标的数据流](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)

### 数据建模和模式

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### 管理和访问控制

- [访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)

### 监控和可观察性

- [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### 护栏

- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [激活护栏](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

### 教程

- [创建架构](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [为配置文件启用数据集](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/enable-for-profile)
