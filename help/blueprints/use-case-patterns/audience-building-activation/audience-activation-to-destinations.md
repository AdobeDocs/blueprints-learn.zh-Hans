---
title: Audience Activation到目标
description: 了解如何使用Adobe Real-Time CDP评估受众区段并将其发布到外部目标以进行定位或抑制。
solution: Real-Time Customer Data Platform, Experience Platform
source-git-commit: b2e496eb521fc3dd3290fccdd9a8203384934b88
workflow-type: tm+mt
source-wordcount: '7005'
ht-degree: 1%

---


# Audience Activation到目标

本指南提供了将受众从Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)激活到外部目标的完整实施参考。 它专为需要评估受众区段并将其发布到广告平台、云存储、CRM系统或数据合作伙伴以进行定位、抑制、相似人群拓展建模或分析扩充的解决方案架构师、营销技术人员和实施工程师而设计。

它提供了所有可行的实施选项，以及权衡分析、决策指导、UI导航路径和Experience League文档参考。

该指南涵盖受众激活的整个生命周期，从定义和评估受众区段（通过配置目标连接和发布受众），到监控激活运行状况并强制实施治理合规性。

## 用例概述

组织需要向外部系统交付受众数据，以便为付费媒体活动提供支持、丰富CRM记录、与合作伙伴共享数据或提供下游分析。 Audience Activation到目标是RT-CDP中的基本激活模式：它评估哪些配置文件符合目标受众的条件，连接到一个或多个外部目标，将配置文件属性映射到目标特定的字段，并发布受众以供下游使用。

每当目标是在正确的时间以正确的格式将受众数据获取到外部系统时，此模式即适用。 它不涉及消息投放、网站个性化或分析。 它是RT-CDP实施的最常见起点，并作为其他模式在其上构建的构建块。

典型的利益相关者包括管理付费媒体的数字营销团队、充实仓库的数据团队、为营销活动准备联系人列表的CRM团队以及确保出站数据流符合治理要求的隐私团队。

## 主要业务目标

此用例模式实现了以下业务目标。

### 获取新客户

通过有针对性的客户获取促销活动、相似受众和付费媒体优化来扩展客户群。

**KPI：**&#x200B;新客户、客户获取成本、潜在客户/潜在客户转化

[了解有关获取新客户的更多信息](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### 降低客户购置成本

提高定位效率，抑制现有客户参与客户获取促销活动，并优化媒体支出。

**KPI：**&#x200B;客户获取成本，每个潜在客户的成本，效率

[了解有关降低客户获取成本的更多信息](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### 优化营销支出和ROI

通过更好的定位、归因、受众抑制和预算分配提高营销投资回报。

**KPI：**&#x200B;成本节约、客户获取成本、递增收入

[了解有关优化营销支出和ROI的更多信息](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## 战术用例示例

- **广告平台受众定位** — 将符合条件的区段推送到付费媒体平台以进行营销活动定位
- **现有客户的付费媒体抑制** — 将已知客户排除在广告平台上的客户获取促销活动之外，以消除浪费的支出
- **相似种子受众** — 将高价值客户区段推送到Facebook、Google Ads或交易台，作为相似人群拓展的种子受众
- **为销售支持进行CRM同步** — 激活高意图或高价值受众，以便销售团队可以优先开展外展活动
- **数据合作伙伴受众共享** — 与数据合作伙伴共享符合条件的受众区段，以进行协作定位或测量
- **用于数据仓库扩充的云存储导出** — 将受众成员资格和配置文件属性导出到Amazon S3、Azure Blob、Google Cloud Storage或SFTP，以用于下游分析
- **重定位受众激活** — 激活未转换为重定位平台的网站访客
- **联系人列表同步到电子邮件服务提供商** — 将受众会员资格推送到第三方电子邮件平台，以便协调外联

## 关键绩效指标

| KPI | 描述 | 测量制导 |
| --- | --- | --- |
| 客户购置成本(CAC) | 通过激活的受众获取新客户的成本 | 归因于激活受众的总媒体支出/新客户 |
| 受众匹配率 | 已成功匹配目标的激活配置文件的百分比 | 在目标匹配的用户档案/从RT-CDP导出的用户档案 |
| 禁止显示节省 | 通过抑制现有客户进行客户获取促销活动来避免媒体支出 | 预计的CPM x抑制的受众规模 |
| 激活交付率 | 成功传送到目标的配置文件百分比 | 源受众中已交付的用户档案/用户档案 |
| 激活时间 | 从受众定义到首次在目标投放所经过的时间 | 从区段创建到首次确认的数据流运行的测量 |
| 受众群体准确性 | 目标处的预期受众大小和实际受众大小之间的匹配情况 | 目标受众规模/RT-CDP受众规模 |

## 用例模式

**Audience Activation到目标** — 评估受众区段并将其发布到外部目标以进行定位或抑制。

**函数链：**&#x200B;受众评估>目标配置> Audience Activation >监视

## 应用程序

- **Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)** — 受众评估、目标管理、受众激活、同意和治理实施
- **Adobe [!DNL Experience Platform] (AEP)** — 配置文件存储，身份服务，分段引擎，数据管理

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本函数 | 状态 | 必须准备好的内容 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 假设就位 | 已配置和活动的RT-CDP沙盒。 分配给实施角色的目标管理和激活权限。 目标平台可用的目标帐户凭据。 | [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)，[访问控制概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | 配置文件架构必须包含将映射到目标字段的属性（例如，电子邮件、电话、哈希标识符、人口统计属性）。 架构必须启用配置文件，数据集才能主动接收数据。 | [XDM系统概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/home)，[架构组合基础](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/schema/composition) |
| 数据源和收集 | 假设就位 | 必须摄取且保持最新，才能为受众评估提供支持的个人资料数据。 批量和/或流式摄取管道可操作。 Web SDK、源连接器或批量摄取，可将数据传递到启用配置文件的数据集。 | [源概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/home)，[Web SDK概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/web-sdk/home) |
| 身份和配置文件配置 | 必填 | 必须配置用于目标匹配的身份命名空间（例如，Facebook自定义受众的哈希电子邮件、Google Ads客户匹配）。 合并策略必须生成具有激活所需所有属性的统一配置文件。 | [身份服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home)，[合并策略概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/merge-policies/overview) |
| 受众定义和分段 | 必填 | 使用区段生成器、受众组合或联合受众组合定义的目标受众。 根据激活延迟需求选择的评估方法（批量、流或边缘）。 此职能在本计划的第一阶段执行。 | [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home)，[区段生成器UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/segment-builder) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么它很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | 生命周期值、参与度得分或倾向得分等计算属性可提高受众精度并提供要映射到目标的扩充属性。 当目标从基于值或基于分数的受众分段中受益时，尤其有用。 | [计算属性概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/overview) |
| 数据生命周期管理 | 推荐 | 数据集和配置文件过期策略可确保数据刷新和合规性。 同意模式配置可确保仅激活同意的用户档案。 在将数据导出到外部系统时，对于法规合规性至关重要。 | [高级数据生命周期管理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-lifecycle/home) |
| 数据使用标签和执行 | 推荐 | 治理标签和策略阻止将受限数据激活到未经授权的目标（例如，将PII激活到广告平台，将敏感区段激活到数据合作伙伴）。 对于激活到外部第三方系统的受众尤为重要。 | [数据管理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home)，[数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview) |
| 监视和可观察性 | 已包含 | 激活监控是功能链（第5阶段）的一部分。 涵盖数据流运行监控、投放状态警报、受众群体跟踪和许可证使用可见性。 | [监视目标数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/dataflows/ui/monitor-destinations)，[警报概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/alerts/overview) |
| 报告和分析 | 推荐 | 通过CJA分析受众激活效果，可以测量激活受众的性能（例如，来自抑制的转化提升、来自相似受众的ROAS）。 | [CJA概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-overview/cja-overview) |

## 应用程序功能

此计划从“应用程序功能目录”中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Real-Time CDP] (RT-CDP)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 受众评估 | 第1阶段：受众评估 | 定义受众规则，并使用批处理、流或边缘评估方法评估区段成员资格 |
| 受众构成 | 第1阶段：受众评估 | （可选）通过针对复杂受众逻辑的扩充、排名、拆分、排除和连接操作来撰写派生受众 |
| 目标配置 | 阶段2：目标配置 | 使用字段映射和计划参数配置与外部目标的已验证连接 |
| Audience Activation | 第3阶段：Audience Activation | 使用属性映射和导出计划将评估的受众发布到已配置的目标 |
| 同意和治理实施 | 第4阶段：治理验证 | 在对外部系统进行受众激活之前和期间，强制执行同意首选项和数据使用策略 |

## 先决条件

- [ ] RT-CDP许可证在受众激活权利下处于活动状态
- [ ] Target沙盒已配置并可由实施团队访问
- [ ]用户角色包括目标管理和受众激活权限
- [ ]每个目标目标的身份验证凭据均可用（OAuth令牌、API密钥、S3访问密钥或服务帐户凭据）
- [ ]配置文件架构包括需要映射到目标字段的所有属性
- [ 已配置目标匹配所需的]身份命名空间（例如，经过哈希处理的电子邮件、电话、设备ID）
- [ ]数据摄取管道正在运行，配置文件正在填充配置文件存储
- [ ]针对正在激活的属性（尤其是外部目标）审查数据管理标签和策略
- [ 如果需要基于同意的筛选，则在配置文件中填充]同意字段

## 实施选项

以下实施选项适用于此用例模式。 查看每个选项和比较表，确定符合要求的最佳方法。

### 选项A：流目标激活

**最适合：**&#x200B;对广告平台或合作伙伴系统进行实时受众会员资格更新 — Facebook自定义受众、Google广告客户匹配、LinkedIn匹配受众、Trade Desk以及类似的基于流API的目标。

**工作方式：**

当配置文件符合或取消符合区段资格时，流式目标激活会近乎实时地将受众成员资格更改传递到目标。 当配置文件属性发生更改或发生导致配置文件进入或退出受众的行为事件时，成员资格更新会在几分钟内流式传输到目标。

此方法需要流式目标连接器（大多数主要广告平台都支持此方法）和流式或边缘受众评估方法。 受众评估会持续监控符合条件的用户档案更改，激活数据流会在发生更新时推送更新。 目标会接收增量成员资格更改，而不是完整受众快照。

流激活是RT-CDP目录中的大多数广告平台目标的默认设置。 目标连接器会自动处理API身份验证、速率限制和重试逻辑。

**关键注意事项：**

- 受众评估必须使用流评估或边缘评估（仅限批次的受众无法实时馈送流目标）
- 并非所有区段表达式都符合流式评估的条件 — 复杂的聚合、多实体查询和某些基于时间的函数需要批处理
- 在大型受众资格事件中，目标合作伙伴API速率限制可能会影响吞吐量
- 配置文件属性更新随成员资格更改一起发送，使目标数据保持最新

**优点：**

- 目标处的近乎实时的受众新鲜度（分钟而非小时）
- 与完整导出相比，增量更新减少了数据传输量
- 自动处理资格和取消资格事件
- 大多数广告平台目标本身支持流式传输

**限制：**

- 需要符合流条件的区段定义（有限的区段功能集）
- 无法控制文件格式或导出结构 — 由目标连接器确定的数据格式
- 无法导出到基于文件的存储目标(S3、Azure Blob、SFTP)
- 目标API速率限制可能会限制大量更改

**Experience League：**

- [将受众激活到流目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [流式目标目录](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/overview)

### 选项B：批量目标激活（文件导出）

**最适合：**&#x200B;将计划受众导出到云存储、数据仓库或使用基于文件的导入的系统 — Amazon S3、Azure Blob存储、Google云存储、SFTP、数据登陆区。

**工作方式：**

批量目标激活会按计划的节奏评估受众，并将结果作为文件（CSV、JSON或Parquet）导出到配置的存储目标。 导出可以包括完整的受众快照或增量更改（自上次导出以来新增的资格和取消资格）。

实施过程涉及使用存储凭据、文件格式首选项（分隔符、压缩、命名约定）和导出计划（每天、每3小时、每6小时等）配置基于文件的目标连接。 每次导出运行都会生成包含受众成员资格和任何映射的配置文件属性的文件。

这种方法支持范围最广的下游用户，因为普遍支持基于文件的数据交换。 它还是云存储和数据仓库扩充用例的唯一选项。

**关键注意事项：**

- 受众评估可以使用任何方法（批处理、流或边缘） — 导出本身按计划运行，而不管
- 文件格式、压缩和命名惯例可根据目标进行配置
- 支持增量导出（仅限更改）和完全导出（完整受众快照）
- 导出计划粒度范围从每3小时到每天

**优点：**

- 完全控制导出文件格式(CSV、JSON、Parquet)、压缩和命名
- 与任何可使用文件的下游系统兼容
- 支持增量导出模式和完全导出模式
- 可以使用任何评估方法导出受众（包括具有复杂分段逻辑的仅批处理区段）
- 支持在常规计划之外运行临时（按需）导出

**限制：**

- 滞后时间内在地会更高 — 受众数据按计划到达目标，而不是实时到达
- 基于文件的导出需要目标系统处理和摄取文件
- 导出文件的目标存储成本
- 与增量流更新相比，每次导出的数据量更大

**Experience League：**

- [将受众激活到批量配置文件导出目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [基于文件的目标目录](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage)

### 选项C：多目标激活

**最适合：**&#x200B;将同一受众同时激活到多个目标 — 例如，将禁止列表推送到所有广告平台，将高价值区段同步到CRM和广告平台，或协调多个媒体合作伙伴的受众访问范围。

**工作方式：**

多目标激活不是单独的技术机制，而是选项A和B的组合，它们跨多个目标连接应用于同一受众。 同一受众被激活到两个或更多目标，每个目标具有自己的连接配置、字段映射和计划。

每个目标连接都独立运行 — 对Facebook的流激活和对S3的批量导出可以同时从同一源受众运行。 字段映射是按目标配置的，因此，可以根据每个目标的要求以及治理策略允许的内容，将不同的属性发送到不同的系统。

这是一种常见的生产模式，适用于跨多个广告平台运营、在媒体激活的同时维护CRM同步，或需要将受众数据分发到运营和分析系统的组织。

**关键注意事项：**

- 每个目标都有独立的字段映射、调度和治理评估
- 每个目标强制实施治理策略 — 不同的目标类型可能允许不同的属性
- 单个受众可同时激活到流式传输和批量目标的混合中
- 添加新目标不需要更改现有激活

**优点：**

- 通过单个受众定义跨所有外部系统的协调受众分布
- 每个目标的独立配置允许优化的映射和计划
- 实施每个目标治理可确保跨不同目标类型的法规遵从性
- 集中受众管理，同时支持分布式激活

**限制：**

- 配置、验证和维护更多目标连接
- 监视复杂性会随着每个目标而增加 — 必须为每个目标跟踪激活失败
- 许可证使用（激活的配置文件）可能按目标计数，具体取决于授权
- 跨多个目标的字段映射维护需要协调

**Experience League：**

- [目的地概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/home)
- [目标目录](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/overview)

### 选项比较

| 标准 | 选项A：流 | 选项B：批处理（文件导出） | 选项C：多目标 |
| --- | --- | --- | --- |
| 最适合 | 实时广告平台定位和抑制 | 数据仓库扩充、基于文件的系统集成 | 协调的跨平台受众分发 |
| 复杂性 | 低 | 中 | 高 |
| 延迟 | 分钟（近乎实时） | 小时（计划） | 每个目标分钟数和小时数的组合 |
| 文件格式控件 | 无（目标确定格式） | 完整（CSV、JSON、Parquet、压缩、命名） | 每个目标 |
| 受众评估 | 需要流式处理或边缘处理 | 任意方法（批处理、流、边缘） | 按目标要求 |
| 需要 | 流目标连接器，符合流条件的区段 | 基于文件的目标连接器，存储凭据 | 多个目标连接器和凭据 |
| 治理 | 单一目的地评估 | 单一目的地评估 | 按目标评估 |

### 选择正确的选项

使用以下决策逻辑选择正确的实施方法：

1. **您需要多少个目标？** 如果您需要将同一受众激活到两个或更多目标，则您将实施选项C（该选项为每个目标包含选项A和B）。 对于每个目标，请回答问题2和3。

2. **目标是否支持流式传输？** 如果目标是广告平台(Facebook、Google Ads、LinkedIn、The Trade Desk)或合作伙伴与流API集成，请为该目标使用选项A。 如果目标是云存储(S3、Azure Blob、GCS、SFTP)或使用文件的系统，请使用选项B。

3. **受众必须多久才能到达目标？** 如果受众成员资格必须在几分钟内反映在目标位置（例如，在活动营销活动期间进行实时抑制），请使用选项A。如果每日或多小时交付足以满足需求（例如，每周数据仓库刷新、CRM批量同步），请使用选项B。

4. **您的受众是否使用复杂的分段逻辑？** 如果受众定义包含多事件聚合、大时间窗口或不符合流式评估条件的函数，请使用选项B（批处理目标）或确保选项A目标也按计划接收批处理评估的受众。

## 实施阶段

实施将遵循这些阶段。 每个阶段都包括配置详细信息、决策点以及指向Experience League文档的链接。

### 第1阶段：受众评估

**应用程序函数：** RT-CDP：受众评估， RT-CDP：受众构成

**您将配置的内容：**&#x200B;定义将激活到目标的目标受众。 这包括指定受众条件（哪些用户档案符合条件）、选择评估方法（成员资格更新的速度）以及验证受众群体。 这是所有激活的起点 — 如果没有已定义和已评估的受众，则没有任何要激活的内容。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决定：受众创建方法**
>
>应如何定义目标受众？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 区段生成器（基于规则） | 使用用户档案属性、行为事件和区段成员资格条件的标准受众定义 | 最灵活的规则定义；支持对符合条件的表达式进行流式处理和边缘评估；非常适用于单条件或中等复杂的受众 |
>| 受众构成 | 受众需要合并、排名、拆分或排除现有受众 | 连续操作的可视画布；结果仅进行批次评估；每个画布最多10个合成块 |
>| 联合受众构成 | 必须根据外部数据仓库中的数据来评估受众标准，而无需将其摄取到AEP中 | 直接查询外部数据库；避免数据重复；需要联合受众组合许可证 |

>[!NOTE]
>
>**决定：评估方法**
>
>配置文件必须以多快的速度进入和退出受众？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 批次 | 不符合流式处理条件的计划营销活动、每日受众刷新或复杂分段逻辑 | 每个作业最多处理2400万个配置文件；支持所有分段功能；按计划（每天默认或自定义cron计划）运行 |
>| 流 | 流式目标激活或事件触发用例所需的实时受众会员资格更改 | 近乎实时（从秒到分钟）；分段函数集有限 — 仅简单事件、属性比较和有限的时间窗口；无多实体查询 |
>| Edge | 边缘站点需要同一页面个性化或即时受众资格 | 毫秒延迟；最严格的规则集 — 仅配置文件属性和简单的区段成员资格检查；主要用于现场个性化（不太常见于目标激活） |

>[!NOTE]
>
>**决定：合并策略**
>
>受众评估应使用哪个合并策略？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 已排序的时间戳（默认） | 大多数用例 — 当配置文件片段冲突时，最近的数据应优先 | 最常见；使用最近更新的属性值 |
>| 数据集优先级 | 无论时间戳如何，特定数据源都应覆盖其他数据源 | 需要定义数据集优先级顺序；在CRM记录系统应始终覆盖Web收集的数据时非常有用 |

**UI导航：**&#x200B;客户>受众>创建受众>生成规则（用于区段生成器）或组合受众（用于受众合成）

**密钥配置详细信息：**

- 根据用例定义受众标准 — 用户档案属性、行为事件、区段成员资格或基于时间的条件
- 应用禁止规则以排除不应激活的用户档案（例如，最近转换的用户档案、全局取消订阅的用户档案）
- 在继续激活之前，验证受众群体大小
- 确认评估方法与阶段2中选择的目标类型一致

**选项差异的位置：**

选项A （流目标激活）的&#x200B;**：**
受众必须使用流评估或边缘评估来提供实时成员资格更新。 验证区段规则表达式是否符合流式评估的条件 — 避免基于时间的聚合函数、多实体查询和`inSegment()`对仅批处理区段的引用。

选项B的&#x200B;**（批处理目标激活）：**
任何评估方法都有效。 批处理评估是最常见的选择，因为导出本身按计划运行。 确认沙盒中存在批次评估计划，或创建一个批次评估计划。

选项C （多目标激活）的&#x200B;**：**
评价方法应适应要求最高的目的地。 如果有任何目标需要流式传输，则受众应使用流式评估。 如果所有目标均为批处理，则进行批量评估即可。

**Experience League文档：**

- [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language参考](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/pql/overview)
- [流式客户细分](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/edge-segmentation)
- [受众构成概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/audience-composition)
- [评估方法](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home#evaluation-methods)


### 阶段2：目标配置

**应用程序函数：** RT-CDP：目标配置

**您将配置的内容：**&#x200B;与将发布受众的外部目标建立经过身份验证的连接。 这包括从目录中选择目标、提供身份验证凭据以及配置特定于目标的参数，例如文件格式、存储位置和导出计划。 每个目标都需要自己的连接配置。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决策：目标类型**
>
>应在何处交付受众？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| Advertising目标（流） | 广告平台（Facebook、Google Ads、LinkedIn、The Trade Desk等）上的定位或禁止显示 | 流连接器；近乎实时的成员资格更新；通过散列电子邮件、电话或设备ID进行身份匹配 |
>| 云存储目标（批量） | 导出到S3、Azure Blob、GCS、SFTP或数据登陆区，以扩充数据仓库 | 基于文件的导出；可配置格式(CSV、JSON、Parquet)；计划的步调 |
>| CRM目标 | 将受众同步到Salesforce、Microsoft Dynamics或HubSpot以实现销售支持 | 通常为流式处理；需要特定于CRM的字段映射；可能需要CRM管理员权限 |
>| 数据合作伙伴目标 | 与测量或定位合作伙伴共享受众数据 | 因合作伙伴而异；审查外部共享数据对治理的影响 |
>| 自定义目标(Destination SDK) | 目标系统在目录中不可用 | 需要使用Destination SDK构建自定义目标；需要投入更大的实施工作 |

>[!NOTE]
>
>**决策：身份验证方法**
>
>目标需要什么凭据？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| OAuth 2.0 | 广告平台和SaaS目标(Facebook、Google、Salesforce) | 需要初始授权流程；令牌自动刷新；最常见于流目标 |
>| 访问密钥/密钥 | 云存储(S3、Azure Blob) | 静态凭据；应计划轮换；适用于基于文件的目标 |
>| 服务帐户/API密钥 | 合作伙伴API和自定义集成 | 需要目标合作伙伴提供凭据 |
>| 连接字符串 | 基于Azure的目标 | 包含所有连接参数的单个字符串 |

>[!NOTE]
>
>**决策：导出类型（仅限批处理目标）**
>
>应如何打包受众数据以供导出？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 增量导出 | 仅自上次导出后的新资格和取消资格 | 文件更小；目标处的处理速度更快；需要目标系统来保持状态 |
>| 完全导出 | 每次运行时完整的受众快照 | 文件更大；目标每次都能获得完整图像；对于执行完整替换的系统，更简单 |

**UI导航：**&#x200B;连接>目标>目录> [选择目标] >配置

**密钥配置详细信息：**

- 浏览目标目录并选择目标目标
- 提供身份验证凭据并测试连接
- 对于批处理目标：配置文件格式(CSV、JSON、Parquet)、压缩、文件命名模板和导出计划
- 对于流目标：连接通常通过OAuth授权流建立
- 在继续激活之前，验证目标连接状态是否显示为“活动”

**选项差异的位置：**

选项A （流目标激活）的&#x200B;**：**
从目录（Advertising或Social类别）中选择流目标。 完成OAuth授权流程。 确认授权后，连接即可激活。

选项B的&#x200B;**（批处理目标激活）：**
从目录（云存储类别）中选择基于文件的目标。 配置存储路径、文件格式、压缩、命名约定和导出计划。 通过验证对存储位置的写入权限来测试连接。

选项C （多目标激活）的&#x200B;**：**
对每个目标重复此阶段。 每个连接都是独立的 — 您可能同时拥有流式传输和批处理目标。 记录每个连接的身份验证和配置以供操作参考。

**Experience League文档：**

- [目标目录](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/overview)
- [目的地概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/home)
- [将受众激活到批量配置文件导出目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [将受众激活到流目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Destination SDK概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/destination-sdk/overview)
- [Destination SDK配置选项](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/destination-sdk/functionality/configuration-options)


### 阶段3：受众激活

**应用程序函数：** RT-CDP： Audience Activation

**您将配置的内容：**&#x200B;通过创建激活数据流，将评估的受众发布到配置的目标。 这涉及选择要激活的受众、将配置文件属性映射到目标字段以及配置导出计划。 激活数据流将源受众连接到目标受众，并管理正在进行的数据交付。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决策：属性映射**
>
>激活中应包含哪些配置文件属性？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 仅标识字段 | 目标只需要匹配用户档案（例如，广告平台中的受众成员资格） | 最小的数据传输；最隐私安全；典型用于广告平台定位和抑制 |
>| 身份和配置文件属性 | 目标需要用于个性化或分段的扩充属性（例如CRM同步、合作伙伴共享） | 传输了更多数据；需要对每个属性进行治理审查；根据目标营销操作检查数据使用标签 |
>| 标识+计算属性 | 目标从派生得分或聚合（例如，生命周期值层、合作伙伴定位的倾向分数）中受益 | 需要配置计算属性；下游系统的高值扩充 |

>[!NOTE]
>
>**决定：导出计划（仅限批处理目标）**
>
>多久导出一次受众数据？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 每日 | 标准刷新节奏；大多数批处理用例 | 使新鲜度与加工成本平衡；最常见的默认值 |
>| 每3-6个小时 | 频率较高的用例，如当天活动优化 | 更频繁的文件生成；目标位置更高的存储和处理负载 |
>| 按需（临时） | 一次性导出或紧急的周期外激活 | 手动触发器绕过计划；对于测试或紧急活动需求非常有用 |

**UI导航：**&#x200B;连接>目标>浏览> [选择目标] >激活受众

**密钥配置详细信息：**

- 选择要激活到目标的一个或多个受众
- 将配置文件属性和标识字段映射到特定于目标的字段
- 对于流目标：确认身份命名空间映射（例如，将电子邮件哈希处理为Facebook的extern_id）
- 对于批处理目标：配置导出计划，选择增量或完全导出模式，并设置第一个导出日期
- 在发布之前，查看激活摘要以确认所有映射和计划

**选项差异的位置：**

选项A （流目标激活）的&#x200B;**：**
选择受众并将身份命名空间映射到目标身份字段。 发布后立即开始激活 — 受众成员资格会将流近乎实时地更改为目标。 无需导出计划；激活是连续的。

选项B的&#x200B;**（批处理目标激活）：**
选择受众、映射配置文件属性并配置导出计划。 在增量导出模式和完全导出模式之间进行选择。 （可选）触发临时导出，以便在常规计划之外立即发送。

选项C （多目标激活）的&#x200B;**：**
对每个目标重复激活工作流。 同一受众可以激活到多个目标，每个目标具有不同的属性映射。 例如，仅将经过哈希处理的电子邮件发送到广告平台，但将人口统计属性发送到CRM。

**Experience League文档：**

- [将受众激活到流目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [将受众激活到批量配置文件导出目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [将按需受众激活到批处理目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [监测目标的数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/dataflows/ui/monitor-destinations)


### 第4阶段：治理验证

**应用程序功能：** RT-CDP：同意和治理实施

**您将配置的内容：**&#x200B;验证在激活之前和激活期间是否正确强制实施治理策略和同意首选项。 此阶段确保受限制的数据（PII、敏感属性）不会发送到未授权的目标，并且不会激活未经有效同意的用户档案。 在激活时自动执行治理，但主动验证可防止阻止的激活和合规性违规。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决定：治理实施方法**
>
>何时应验证公司治理法遵从性？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 主动（预激活） | 建议用于所有实施，尤其是激活到外部第三方系统时 | 在配置字段映射之前查看数据使用标签和策略；防止激活失败并确保从一开始就符合要求 |
>| 反应性（激活时） | 当治理政策已确立并且团队有信心遵守时 | Platform在激活时自动强制实施策略；违规会阻止激活或排除受限制属性；如果不能很好地理解策略，可能会导致意外失败 |

>[!NOTE]
>
>**决定：同意筛选**
>
>同意首选项应该如何影响激活？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 已启用同意执行 | 在激活到依法需要同意的广告或营销目标时，必须填写此项 | 未经有效同意的用户档案(consents.marketing.{channel}.val = &#39;y&#39;)将自动从激活中排除；需要摄取同意数据 |
>| 无同意筛选 | 同意不适用于数据传输的内部使用目标或分析导出 | 仅当数据使用不构成需要同意的营销活动时才适用；请咨询法律/隐私团队 |

**UI导航：**&#x200B;隐私>策略>同意策略（用于同意审查）；数据管理>策略（用于数据使用策略审查）

**密钥配置详细信息：**

- 查看应用于正在激活的数据集和架构字段的数据使用标签
- 验证治理策略对于与目标关联的营销操作（例如，对于广告平台，验证是否为“导出到第三方”）有效
- 确认在用户档案中填充了同意字段，并且为相关渠道启用了同意执行
- 如果检测到策略违规，则通过从目标映射中删除受限字段或选择替代目标来解决此问题

**Experience League文档：**

- [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home)
- [策略实施](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/enforcement/overview)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [同意和偏好设置](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [同意策略实施](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/policies/user-guide)


### 第5阶段：监测和验证

**应用程序功能：**&#x200B;监视和可观察性

**您将配置的内容：**&#x200B;设置激活数据流的持续监控、配置故障警报、验证目标上的受众填充以及跟踪许可证使用情况。 在生产激活中，如果投放失败会直接影响营销活动性能和媒体支出，则监控至关重要。

**密钥配置详细信息：**

- 查看每个活动目标的数据流运行状态，以确认受众已成功交付
- 为目标激活失败、数据流延迟和受众群体异常配置警报
- 跟踪导出的配置文件与每次数据流运行失败的配置文件
- 监测目标（目标报表可用）的受众匹配率
- 审查许可证使用情况以根据授权跟踪激活的配置文件数量

**UI导航：**&#x200B;连接>目标>浏览> [选择目标] >数据流运行（用于激活监视）；警报>警报规则>订阅（用于警报配置）；管理>许可证使用（用于许可证跟踪）

**Experience League文档：**

- [监测目标的数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/dataflows/ui/monitor-destinations)
- [警报概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/alerts/overview)
- [可观察性分析概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/home)
- [许可证用量仪表板](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

## 实施注意事项

在实施之前和过程中，请查看以下注意事项。

### 护栏和限制

- **区段定义限制：**&#x200B;每个沙盒最多4,000个区段定义 — [分段护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)
- **每个目标的数据流：**&#x200B;每个目标连接最多100个数据流 — [目标护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/guardrails)
- **批量导出文件大小：**&#x200B;基于文件的目标具有最大导出文件大小限制；大型受众自动拆分为多个文件
- **流式目标吞吐量：**&#x200B;每个目标合作伙伴都设置了每秒吞吐量限制；可能会限制大量受众更改
- **批量评估容量：**&#x200B;默认情况下，每个区段评估作业最多有2400万个配置文件
- **受众组合：**&#x200B;每个画布最多10个组合块；仅对组合的受众进行批量评估
- **标识图形：**&#x200B;每个图形最多50个标识 — [标识服务护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/guardrails)
- **计算属性：**&#x200B;每个沙盒最多25个计算属性 — [计算属性护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/overview#guardrails)
- **激活护栏概述：** [激活护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/guardrails)

### 常见陷阱

- **具有不合格规则逻辑的流式区段：**&#x200B;定义具有复杂聚合函数或多实体查询的受众并预期流式评估。 这些区段会静默回退到批量评估，从而导致意外延迟。 预防：在定义受众之前，请查看流资格要求。

- **由于同意筛选而导出的配置文件为零：**&#x200B;受众中的所有配置文件都缺少有效的同意值，从而导致在激活时筛选掉整个受众。 预防：验证同意数据摄取是否可操作，以及同意字段是否在激活之前填充。

- **治理策略意外阻止激活：**&#x200B;架构字段上的数据使用标签触发阻止激活的策略违规。 预防：在配置字段映射之前，主动评估治理合规性（阶段4）。 查看从架构继承的标签。

- **目标凭据过期：** OAuth令牌或API密钥过期，导致激活失败，不会立即发出警报。 预防：针对目标激活失败配置警报，并建立凭据轮换计划。

- **不匹配的身份命名空间：**&#x200B;激活映射中配置的身份命名空间与目标所需的不匹配（例如，当目标需要SHA-256哈希电子邮件时发送纯文本电子邮件）。 预防：在配置映射之前，请查看目标文档以了解所需的身份格式。

- **字段映射错误导致导出失败：**&#x200B;将配置文件属性映射到数据类型或格式不兼容的目标字段。 预防：首先在少量受众中测试激活，并在缩放到生产受众之前查看数据流运行详细信息以映射错误。

- **RT-CDP与目标：**&#x200B;由于标识匹配差异、目标去重逻辑或计时，RT-CDP中的受众规模与目标的计数不匹配。 这是预期行为 — 预防：记录每个目标的预期匹配率基准并监控重大偏差。

### 最佳实践

- **从测试受众开始：**&#x200B;在激活生产受众之前，将了解情况的小型测试受众激活到每个新目标。 使用测试受众验证字段映射、身份匹配和投放量度。

- **早期层治理：**&#x200B;在配置目标激活之前，应用数据使用标签并配置治理策略。 这样可防止被阻止的激活，并确保从一开始就符合要求。

- **对批处理目标使用增量导出：**&#x200B;增量导出可减少文件大小，加快目标处的处理速度，并最大限度地降低存储成本。 仅当目标系统需要完全替换受众时，才使用完全导出。

- **标准化命名约定：**&#x200B;在整个组织内为受众、目标连接和数据流建立一致的命名。 在名称（例如“Suppression_ExistingCustomers_Facebook_Streaming”）中包含用例、目标和评估方法。

- **监视匹配率：**&#x200B;跟踪从RT-CDP导出的配置文件与在每个目标上匹配的配置文件的比率。 匹配率显着下降可能表明存在身份解析问题、凭据问题或目标API更改。

- **跨目标协调禁止显示：**&#x200B;在使用禁止显示受众（例如，将现有客户排除在客户获取营销活动之外）时，请同时将禁止显示受众激活到所有相关广告平台以保持一致性。

- **审核并修剪不活动的激活：**&#x200B;定期审核目标数据流并停用不再需要的受众。 不活动的激活会消耗许可证容量并增加监控开销。

### 权衡决定

>[!NOTE]
>
>**取舍：受众新鲜度与分段灵活性**
>
>流式评估可提供近乎实时的受众更新，但会限制您可以使用的区段规则功能。 批量评估支持完整的区段规则函数集，但会引入延迟（以小时而不是分钟）。
>
>- **流式处理优惠：**&#x200B;受众成员资格必须在几分钟内反映在目标位置的实时用例（活动抑制、实时重新定位）
>- **批处理支持：**&#x200B;需要聚合函数、多实体查询或大时间窗口条件（生命周期值层、多接触行为区段）的复杂受众逻辑
>- **推荐：**&#x200B;对激活到实时新鲜度可提升业务价值的流式目的地的受众使用流式评估。 请对激活到基于文件的目标的复杂受众或在每日刷新足以满足要求时，使用批量评估。 对于同时需要这两个版本的受众，请考虑创建两个版本：用于实时激活的简化流区段以及用于定期扩充的综合批处理区段。

>[!NOTE]
>
>**取舍：最小数据导出与富属性映射**
>
>仅导出标识字段（经过哈希处理的电子邮件、设备ID）可最大限度地减少数据泄露并简化管理。 导出其他用户档案属性（人口统计信息、价值层、参与度分数）可丰富目标内容，但会增加治理复杂性和数据责任。
>
>- **最小导出优势：**&#x200B;隐私优先方法；治理风险较低；字段映射较简单；足以满足大多数广告平台定位和抑制用例
>- **丰富导出支持：**&#x200B;目标的下游个性化；CRM扩充；需要属性级详细信息的合作伙伴数据共享
>- **推荐：**&#x200B;对于广告目标，默认使用最小仅标识导出。 仅当目标用例明确要求配置文件属性并且治理审查确认符合性时才添加配置文件属性。 使用计算属性提供聚合的、敏感性较低的扩充值，而不是原始PII。

>[!NOTE]
>
>**取舍：每个目标单个受众与合并的多受众数据流**
>
>将每个受众激活为一个单独的数据流，可提供隔离和精细的监控。 通过单个数据流将多个受众激活到目标可简化管理，并减少隔离。
>
>- **支持单独的数据流：**&#x200B;独立监控、更轻松的故障排除、能够暂停单个受众激活而不影响其他受众
>- **支持合并的数据流：**&#x200B;需要维护的连接更少，简化了凭据管理，减少了操作开销
>- **推荐：**&#x200B;将多个相关受众激活到同一目标时（例如，将所有禁止显示区段激活到Facebook），请使用合并的数据流。 当受众具有不同的SLA、不同的属性映射或故障隔离很关键时，请使用单独的数据流。

## 相关文档

**目标**

- [目的地概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/home)
- [目标目录](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/overview)
- [将受众激活到流目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [将受众激活到批量配置文件导出目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [将按需受众激活到批处理目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [目标护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/guardrails)
- [Destination SDK概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/destination-sdk/overview)

**受众和分段**

- [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language参考](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/pql/overview)
- [流式客户细分](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/edge-segmentation)
- [受众构成概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/audience-composition)
- [分段护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)

**身份和配置文件**

- [Identity服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [身份标识图链接规则](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/identity-linking-logic)
- [配置文件概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/home)
- [合并策略概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/merge-policies/overview)

**数据建模和架构**

- [XDM系统概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/schema/composition)

**数据管理**

- [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [数据治理策略](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/policies/overview)
- [策略实施](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/enforcement/overview)
- [同意和偏好设置](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**监视和可观察性**

- [监测目标的数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/dataflows/ui/monitor-destinations)
- [警报概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/alerts/overview)
- [可观察性分析概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/home)
- [许可证用量仪表板](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**计算属性**

- [计算属性概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/overview)
- [计算属性UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/ui)

**数据收集和源**

- [源概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/home)
- [Web SDK概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/web-sdk/home)
- [配置数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/datastreams/configure)

**管理**

- [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)
- [访问控制概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/access-control/home)
- [基于属性的访问控制](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/access-control/abac/overview)

**护栏**

- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)
- [Identity服务护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/guardrails)
- [激活护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/guardrails)
- [摄取护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/ingestion/guardrails)
