---
title: B2B Audience Activation
description: 了解如何跨Web、电子邮件和广告渠道激活基于帐户的B2B受众。
solution: Real-Time Customer Data Platform
exl-id: 2b979159-37aa-41d4-a6b4-1105538f6546
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7611'
ht-degree: 0%

---

# B2B受众激活

本指南提供了使用[!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition激活基于帐户的B2B受众的全面实施参考。 它专为需要跨Web、电子邮件、广告和CRM渠道构建、评估和激活帐户级受众的解决方案架构师、营销技术人员和实施工程师而设计。

它涵盖了从统一帐户配置文件到进行受众评估和激活再到特定于B2B的目标（如[!DNL Marketo Engage]、[!DNL LinkedIn]和CRM系统）的整个生命周期。 所有可行的实施方法都提供了权衡和决策指导，以帮助您为组织选择正确的路径。

## 用例概述

B2B营销团队需要在帐户级别（而不是个人级别）定位和激活受众。 与B2C受众激活不同（B2C受众激活的定位单位是单个消费者个人资料），B2B受众激活需要了解人员和他们所属的帐户之间的关系，根据帐户级别属性并结合人员级别参与信号来评估受众成员资格，并将这些受众交付到支持基于帐户的定位的目标。

[!DNL RT-CDP] B2B edition通过专门用于帐户、商机和促销活动的XDM类以及映射人员与帐户关系的B2B身份解析来扩展标准[!DNL Real-Time Customer Data Platform]。 这使营销人员能够构建帐户受众，这些受众将来自与这些帐户关联的人员的行业数据（行业、收入、员工人数）、技术数据（技术栈栈、产品使用情况）和行为数据（Web访问次数、电子邮件参与度、事件出席率）组合在一起。

激活的帐户受众在需求挖掘funnel中的强大用例：在[!DNL LinkedIn]和展示广告上开展funnel最热门的宣传运动，[!DNL Marketo Engage]中的funnel中培养计划，以及通过CRM集成实现底部funnel销售支持。 客户抑制受众通过排除现有客户、已结束的丢失的帐户或已在活跃销售周期中的帐户来防止浪费支出。

>[!NOTE]
>如果您的用例涉及在人员级别(B2C)而不是帐户级别激活受众，请参阅[目标受众激活](audience-activation-to-destinations.md)。 该模式使用标准RT-CDP数据模型，不需要B2B edition。

## 主要业务目标

此用例模式支持以下业务目标。

### 增加商机开发

通过表单、事件、内容和多渠道参与，为销售渠道生成更多符合条件的潜在客户。

**KPI：**&#x200B;潜在客户、每个潜在客户的成本、潜在客户转化

[了解有关提高商机开发率的更多信息](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### 改进潜在客户资格鉴定和转化

通过评分、培养和个性化的跟进，提高销售线索质量并加快管道进度。

**KPI：**&#x200B;潜在客户转化、潜在客户/潜在客户转化、效率

[了解有关改进潜在客户资格和转化的更多信息](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### 获取新客户

通过有针对性的客户获取促销活动、相似受众和付费媒体优化来扩展客户群。

**KPI：**&#x200B;新客户、客户获取成本、潜在客户/潜在客户转化

[了解有关获取新客户的更多信息](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### 优化营销支出和ROI

通过更好的定位、归因、受众抑制和预算分配提高营销投资回报。

**KPI：**&#x200B;成本节约、客户获取成本、递增收入

[了解有关优化营销支出和ROI的更多信息](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## 战术用例示例

以下场景说明了如何将此模式应用于实践。

- **在[!DNL LinkedIn]**&#x200B;上基于帐户的广告 — 使用从[!DNL RT-CDP] B2B edition激活的帐户列表，在[!DNL LinkedIn]上定位与您理想的客户个人资料(ICP)和赞助内容以及InMail促销活动相匹配的帐户
- **[!DNL Marketo Engage]Nurture计划目标** — 将帐户受众激活到[!DNL Marketo Engage]，以根据帐户级别的资格条件将关联的潜在客户和联系人注册到目标的Nurture流中
- **CRM帐户列表同步** — 将符合条件的帐户列表推送到[!DNL Salesforce]或[!DNL Microsoft Dynamics]，以查看销售团队的可见性、区域分配和出站潜在客户工作流
- **针对付费媒体的帐户抑制** — 从付费客户获取营销活动中禁止现有客户、赢取已结帐的帐户或处于活跃销售周期的帐户，以减少浪费的支出
- **基于意图的帐户定位** — 在帐户级别将第三方意图信号与第一方参与数据相结合，以识别和激活市场内帐户的受众
- **与现有客户进行产品交叉销售** — 使用一个产品系列而不是另一个产品系列构建客户受众，然后激活到电子邮件和广告渠道以进行交叉销售促销活动
- **活动和网络研讨会定位** — 将帐户受众激活到广告和电子邮件渠道，以从目标帐户进行事件注册
- **竞争替换促销活动** — 使用通过广告和电子邮件渠道激活定制消息传递的竞争对手产品的目标客户
- **分层客户参与** — 根据聚合的人员级别活动将客户划分到参与层（高、中、低），并为每个层激活差异化促销活动
- **合作伙伴联合营销受众** — 通过云存储目标与渠道合作伙伴或联合营销计划共享帐户受众区段

## 关键绩效指标

以下KPI可帮助衡量此用例模式是否成功。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 帐户范围 | 通过激活渠道访问的目标帐户数量 | 跟踪每个目标激活的唯一帐户 |
| 帐户参与率 | 显示参与信号的已激活帐户的百分比 | 衡量汇总到帐户的人员级别参与度 |
| 管道影响 | 归因于基于帐户的激活活动的收入管道 | 跟踪从激活的帐户受众创建的机会 |
| 每个参与帐户的成本 | 营销支出除以显示参与度的帐户数 | 跨广告和电子邮件渠道成本计算 |
| 潜在客户转化率 | 已激活帐户中转换为业务机会的潜在客户百分比 | 跟踪已激活受众的销售线索到业务机会的转化 |
| 受众抑制节省 | 通过从付费营销活动中取消不符合条件的帐户来节省成本 | 从抑制受众中衡量支出减少情况 |
| 帐户覆盖范围 | 激活的受众覆盖的可寻址市场(TAM)总数的百分比 | 将激活的帐户与总ICP世界进行比较 |

## 用例模式

**B2B受众激活**

跨Web、电子邮件和广告渠道激活基于帐户的B2B受众。

**功能链：**&#x200B;帐户配置文件扩充>帐户受众评估>目标配置> Audience Activation >监控

## 应用程序

以下应用程序用于实现此用例模式。

- **[!DNL Real-Time CDP]B2B edition** — 用于统一帐户配置文件、B2B身份解析、帐户受众评估、特定于B2B的目标配置和帐户受众激活的核心平台
- **[!DNL Adobe Experience Platform](AEP)** — 用于B2B XDM数据建模、从CRM和营销自动化源摄取数据、标识服务和治理的基础基础架构
- **[!DNL Marketo Engage]** — 由激活的帐户受众提供的潜在客户培养计划、评分和营销活动执行的主要B2B营销自动化目标

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本函数 | 状态 | 必须准备好的内容 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 必填 | 沙盒配置了[!DNL RT-CDP]已启用B2B edition。 为B2B数据管理、受众创建和目标激活配置的角色。 如果帐户数据包含受限字段，则实施ABAC策略。 | [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)，[访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | 使用XDM业务帐户、XDM业务机会、XDM业务营销活动和XDM Individual Profile类配置的B2B XDM架构。 应用于帐户属性、人员 — 帐户关系和机会数据的B2B字段组。 为每个B2B实体创建并启用配置文件的数据集。 在客户、人员、商机和营销活动实体之间定义的架构关系。 | Real-Time CDP中的[XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[B2B架构](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b) |
| 数据源和收集 | 必填 | 已为CRM ([!DNL Salesforce]， [!DNL Microsoft Dynamics])和营销自动化([!DNL Marketo Engage])配置Source连接器，以摄取帐户、人员、机会和营销活动数据。 批量或流式摄取管道处于活动状态。 配置为将源数据转换为B2B XDM架构的数据准备映射。 | [源概述](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)，[Marketo Engage连接器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| 身份和配置文件配置 | 必填 | 为帐户标识符（帐户ID、CRM帐户ID）和人员标识符（电子邮件、CRM联系人ID、Marketo潜在客户ID）配置的B2B身份命名空间。 通过B2B身份解析解析的人员 — 帐户关系。 为统一帐户配置文件配置的合并策略。 | [Identity Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[Real-Time CDP的B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b) |
| 受众定义和分段 | 必填 | 使用帐户属性、人员属性和活动数据创建的帐户级别受众定义。 为帐户受众配置的评估计划。 为排除不符合条件的帐户而定义的隐藏受众。 | [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么它很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | 在帐户级别汇总参与度分数、生命周期值和活动量度可提高受众准确性。 计算属性可以将人员级别的事件（电子邮件打开、Web访问、内容下载）汇总到帐户级别以用于分段。 | [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 数据生命周期管理 | 推荐 | B2B数据保留策略可确保清理过时的帐户和机会数据。 对B2B联系人的同意管理可确保遵守电子邮件营销法规。 数据集到期策略阻止累积过期的CRM同步数据。 | [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 数据使用标签和执行 | 已包含 | B2B帐户数据通常包含合同限制（收入数字、来自第三方提供商的员工计数）。 数据使用标签会阻止将受限帐户属性激活到未授权的目标。 治理策略确保在激活期间正确处理联系人记录中的PII字段。 | [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| 监视和可观察性 | 已包含 | 监控CRM和[!DNL Marketo Engage]源连接器数据流可确保帐户数据保持最新。 目标激活监视确认受众已成功交付到[!DNL LinkedIn]、[!DNL Marketo]和CRM目标。 警报规则会捕获会导致帐户数据过时的摄取故障。 | [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)，[监视目标数据流](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations) |
| 报告和分析 | 推荐 | [!DNL CJA] B2B edition提供帐户级别的分析，包括受众范围、参与和管道影响。 基于帐户的归因有助于衡量激活营销活动对机会进展和收入的影响。 | [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## 应用程序功能

此计划从“应用程序功能目录”中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Real-Time CDP] B2B edition ([!DNL RT-CDP] B2B)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 帐户个人资料统一 | 阶段1：帐户配置文件扩充 | 使用B2B XDM架构类将CRM、营销自动化和第三方源中的帐户数据整合到统一的帐户配置文件中 |
| B2B身份解析 | 阶段1：帐户配置文件扩充 | 使用主要标识符解决人员与帐户的关系，将联系人和潜在客户映射到其关联帐户 |
| 帐户受众评估 | 第2阶段：客户受众评估 | 通过组合帐户属性、人员属性和人员活动数据来评估帐户级别的区段成员资格 |
| 帐户目标配置 | 阶段3：目标配置 | 使用帐户级别字段映射配置与特定于B2B的目标（[!DNL Marketo Engage]、[!DNL LinkedIn]、CRM、云存储）的连接 |
| 帐户Audience Activation | 第4阶段：Audience Activation | 将基于帐户的受众发布到已配置的目标，以进行定位、禁止显示或CRM同步 |
| [!DNL Marketo Engage]集成 | 阶段3：目标配置 | 使用本机B2B源和目标连接器配置[!DNL Marketo Engage]的双向数据流 |
| B2B数据管理 | 第5阶段：治理和监控 | 跨B2B帐户数据激活实施数据使用策略和同意，以防止未经授权的数据泄露 |

### [!DNL Real-Time CDP] ([!DNL RT-CDP]) — 标准函数

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 受众评估 | 第2阶段：客户受众评估 | 帐户受众的基础评估引擎，支持对帐户级别区段定义进行批量评估 |
| 目标配置 | 阶段3：目标配置 | 特定于B2B的目标配置所使用的核心目标连接基础架构 |
| Audience Activation | 第4阶段：Audience Activation | 帐户受众激活使用的核心激活数据流基础架构 |
| 同意和治理实施 | 第5阶段：治理和监控 | 在激活时强制实施同意首选项和数据使用策略 |

## 先决条件

请在开始实施之前完成以下操作。

- [ 已在组织中配置和激活] [!DNL RT-CDP] B2B edition许可证
- [ ] CRM系统（[!DNL Salesforce]或[!DNL Microsoft Dynamics]）可使用源连接器配置的API凭据进行访问
- [ 使用[!DNL Marketo]作为目标时，] [!DNL Marketo Engage]实例已设置API访问权限（Munchkin ID、客户端ID、客户端密钥）
- [ 将[!DNL LinkedIn]用作目标时，具有匹配受众功能的] [!DNL LinkedIn]营销活动管理器帐户
- [ 使用account、person、opportunity和campaign类创建的]个B2B XDM架构(F2)
- [ ]个Source连接器已配置并主动摄取CRM和营销自动化数据(F3)
- [ ]已解析人员到帐户的身份关系并已统一帐户配置文件(F4)
- [ ]为受众定义商定的帐户命名惯例和分类
- [ 为帐户级别的数据敏感度分类定义的]数据治理策略

## 实施选项

以下选项描述了实施此用例模式的不同方法。 查看每个选项，并选择最适合您要求的选项。

### 选项A：将受众激活流式传输到[!DNL Marketo Engage]

**最适合：**&#x200B;使用[!DNL Marketo Engage]作为主要B2B营销自动化平台的组织，需要近乎实时的受众会员资格更新以触发培养计划、更新潜在客户得分或修改营销活动会员资格，因为客户符合资格或不符合资格。

**工作方式：**

此选项使用[!DNL RT-CDP]中的本机[!DNL Marketo Engage]目标连接器将帐户受众成员资格更改直接流式传输到[!DNL Marketo Engage]。 当帐户符合或退出受众区段时，[!DNL Marketo]中关联的潜在客户和联系人将更新为区段成员资格属性。[!DNL Marketo] 然后，智能营销活动可根据这些成员资格更改进行触发。

[!DNL Marketo Engage]目标是流式目标，这意味着受众成员资格更改会在发生时递增发送，而不是按计划的批次发送。 这加快了需要响应客户资格更改的活动采取行动的时间。 字段映射将[!DNL RT-CDP]配置文件属性连接到[!DNL Marketo]潜在客户/联系人字段，从而允许使用来自[!DNL RT-CDP]的帐户级别数据扩充[!DNL Marketo]记录。

**关键注意事项：**

- 需要具有API访问权限的活动[!DNL Marketo Engage]订阅
- 流式激活发送的是增量更新，而不是完整的受众快照
- [!DNL Marketo]中的人员级别记录已更新，而不是直接更新帐户级别记录
- 必须将[!DNL Marketo]智能营销活动配置为对区段成员资格字段更新执行操作

**优点：**

- [!DNL Marketo]中的近乎实时的受众会员资格更新
- 本机双向连接器简化了集成
- 增量更新可最大程度地减少数据传输量
- [!DNL Marketo]可以根据受众更改立即触发培养计划

**限制：**

- 仅限于[!DNL Marketo Engage]作为激活目标
- 流式评估资格限制适用于基础受众定义
- 需要[!DNL RT-CDP]帐户受众和[!DNL Marketo]潜在客户/联系人记录之间的映射
- 可能需要复杂的[!DNL Marketo]项目逻辑才能将人员级别更新转换为帐户级别操作

**Experience League：**

- [Marketo Engage目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [将受众激活到Marketo Engage目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage#activate)

### 选项B：将受众批量激活到广告平台

**最适合：**&#x200B;在[!DNL LinkedIn]、显示网络或其他广告平台上基于帐户的广告营销活动，在这些平台上，每日受众刷新次数已足够，主要目标是帐户级别的触及率和知名度，而不是实时响应。

**工作方式：**

此选项按计划的批处理节奏将帐户受众激活到广告平台目标（[!DNL LinkedIn]个匹配的受众、[!DNL Google]个客户匹配、[!DNL Facebook]个自定义受众或[!DNL The Trade Desk]）。 激活数据流导出帐户受众成员，这些成员具有广告平台用来与其用户群匹配的映射标识字段（通常是关联联系人的哈希电子邮件地址）。

具体来说，对于[!DNL LinkedIn]，[!DNL LinkedIn]匹配受众目标除了接受基于电子邮件的匹配之外，还接受公司名称和基于域的匹配，从而实现真正的帐户级别定位。 其他广告平台通常要求与符合条件的帐户关联的联系人提供个人级别的标识符（电子邮件、电话）。

批量激活按可配置的计划运行（每天、每6小时等） 和会导出完整受众快照或增量更改，具体取决于目标类型。 此方法非常适用于持续开展的提高认识活动，这些活动以小时而不是分钟为单位衡量受众新鲜度要求。

**关键注意事项：**

- 受众新鲜度取决于批量计划（通常每天）
- Advertising平台有自己的匹配率限制
- [!DNL LinkedIn]支持帐户级别匹配；其他平台需要人员级别标识符
- 导出文件格式和标识要求因目标而异

**优点：**

- 同时支持多个广告平台
- 批处理可以有效处理大量受众
- 客户抑制受众减少了浪费的广告支出
- [!DNL LinkedIn]个匹配的受众启用本机帐户级别定位

**限制：**

- 受众更新不是实时的；延迟取决于批量计划
- 匹配率因平台和可用身份字段而异
- 某些平台不支持真正的帐户级别匹配，仅支持人员级别
- 需要为每个广告平台分别配置目标

**Experience League：**

- [LinkedIn匹配受众目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Google客户匹配目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/advertising/google-customer-match)
- [目标目录](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)

### 选项C：对云存储的基于文件的激活

**最适合：**&#x200B;需要在下游使用帐户受众方面具有最大灵活性的组织，包括CRM导入、数据仓库扩充、合作伙伴数据共享或自定义集成（其中首选的是基于文件的切换）。

**工作方式：**

此选项按计划的节奏将帐户受众导出为CSV、JSON或Parquet文件到云存储目标([!DNL Amazon S3]、[!DNL Azure Blob Storage]、[!DNL Google Cloud Storage]、SFTP)。 导出包括帐户属性、关联联系人中的人员级别字段以及受众成员资格元数据。 下游系统通过其自身的导入过程使用这些文件。

基于文件的激活可提供对导出格式、字段选择和计划的最全面控制。 它支持完全导出（每次运行完整受众快照）和增量导出（仅支持自上次运行以来的更改）。 当目标系统没有本机[!DNL RT-CDP]目标连接器，或者当组织需要在将数据加载到目标系统之前对其进行预处理或转换时，通常使用此方法。

**关键注意事项：**

- 需要云存储基础结构（[!DNL S3]、[!DNL Azure Blob]、[!DNL GCS]或SFTP）
- 必须构建和维护下游导入流程
- 文件格式(CSV、JSON、Parquet)必须与下游系统要求匹配
- 导出计划必须与下游处理窗口保持一致

**优点：**

- 最大程度地灵活使用受众数据
- 支持任何可以读取文件的下游系统
- 完全控制导出格式、字段和计划
- 可以从单个导出为多个下游使用者提供服务
- 支持完整和增量导出模式

**限制：**

- 所有选项的最大延迟（仅限批处理）
- 需要构建和维护下游导入工作流
- 无本机集成 — 需要额外的开发工作
- 文件管理（清理、存档）必须单独处理

**Experience League：**

- [Amazon S3目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Azure Blob存储目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/azure-blob)
- [将受众激活到批处理目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/api/connect-activate-batch-destinations)

### 选项D：流式激活CRM系统

**最适合：**&#x200B;销售营销协调用例，在这些用例中，帐户资格更改必须近乎实时地反映在CRM （[!DNL Salesforce]或[!DNL Dynamics]）中，以便显示销售团队的可见性、区域分配更新或自动销售工作流。

**工作方式：**

此选项使用流式目标连接器([!DNL Salesforce] CRM， [!DNL Microsoft Dynamics])将帐户受众成员资格更改直接推送到CRM帐户或联系人记录。 当帐户符合或退出受众时，将使用指示区段成员资格的自定义字段更新CRM记录。 然后，销售团队可以根据这些字段构建CRM报表、视图和警报。

当受众成员资格发生更改时，流连接器会发送增量更新。 字段映射将[!DNL RT-CDP]帐户和人员属性连接到CRM字段，从而能够使用来自[!DNL RT-CDP]的统一数据扩充CRM记录。 此方法可关闭营销情报（帐户资格）和销售执行（CRM工作流）之间的循环。

**关键注意事项：**

- 需要具有适当写入权限的CRM API访问权限
- 必须创建CRM自定义字段才能接收受众成员资格数据
- 流卷必须在CRM API速率限制范围内
- 必须将CRM工作流自动化配置为处理字段更新

**优点：**

- 近乎实时的CRM更新，让销售团队具有可见性
- 启用由受众更改触发的自动化CRM工作流
- 使用[!DNL RT-CDP]中的统一帐户数据扩充CRM记录
- 支持帐户级别和联系人级别字段更新

**限制：**

- CRM API速率限制可能会限制大量更新
- 需要CRM自定义（自定义字段、工作流）
- 仅限于[!DNL Salesforce]和[!DNL Microsoft Dynamics]作为本机连接器
- 流式评估限制适用于基础受众

**Experience League：**

- [Salesforce CRM目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)

### 选项比较

下表比较了每个实施选项的主要特性。

| 标准 | 选项A：[!DNL Marketo]流 | 选项B：Advertising批处理 | 选项C：云存储 | 选项D：CRM流 |
| --- | --- | --- | --- | --- |
| 最适合 | 培养计划激活 | 基于帐户的广告 | 灵活的下游集成 | 销售与营销协调 |
| 复杂性 | 低 | 中 | Medium — 高 | 中 |
| 延迟 | 近乎实时（分钟） | 批次（小时） | 批次（小时） | 近乎实时（分钟） |
| 灵活性 | 低（仅[!DNL Marketo]） | Medium（广告平台） | 高（任何下游系统） | 低（仅限CRM） |
| 需要 | [!DNL Marketo Engage]许可证 | Advertising平台帐户 | 云存储基础架构 | CRM API访问 |
| 帐户级别定位 | 通过人员记录 | 仅[!DNL LinkedIn]（其他人级别） | 可配置 | 通过帐户/联系人记录 |
| 维护工作 | 低 | 低Medium | 高 | 中 |

### 选择正确的选项

使用以下决策指南选择正确的激活方法：

1. **如果您的主要目标是B2B潜在客户培养，并且您使用[!DNL Marketo Engage]**，请选择选项A。本机流连接器为营销自动化工作流提供了最快的行动时间。

2. **如果您的主要目标是通过广告基于帐户的意识和需求生成**，请选择选项B。[!DNL LinkedIn] “匹配的受众”提供了最强的帐户级别定位。 使用其他广告平台扩大覆盖范围。

3. **如果您需要向没有本机[!DNL RT-CDP]连接器的系统提供帐户受众**，或者如果您需要最大限度地控制数据格式和下游处理，请选择“选项C”。这也是合作伙伴共享数据或扩充数据仓库的最佳选择。

4. **如果您的主要目标是销售支持和CRM对符合营销条件的客户的可见性**，请选择选项D。这通过近乎实时地更新CRM记录来结束营销到销售的切换循环。

大多数B2B组织将同时实施多个选项 — 例如，A选项适用于nurture程序， B选项适用于[!DNL LinkedIn]广告，D选项适用于CRM同步。 这些选项并非互斥；同一帐户受众可同时激活到多个目标。

## 实施阶段

以下阶段描述了实施此用例模式的分步流程。

### 阶段1：帐户配置文件扩充

此阶段通过整合来自CRM、营销自动化和第三方来源的数据来建立统一的帐户配置文件。

**应用程序函数：** [!DNL RT-CDP] B2B：帐户配置文件统一，[!DNL RT-CDP] B2B： B2B标识解析

**您将配置的内容：**&#x200B;此阶段通过合并CRM、营销自动化和第三方源中的数据来建立统一的帐户配置文件。 B2B身份解析映射人员与帐户的关系，以便可以聚合人员级别的参与数据（电子邮件打开、Web访问、内容下载）并在帐户级别的受众评估中使用。 此阶段的基础函数F2、F3和F4必须已经到位。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决定：帐户标识符策略**
>
>哪个标识符跨系统用作主帐户密钥？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| CRM帐户ID（例如[!DNL Salesforce]帐户ID） | CRM是帐户的记录系统 | 最常见的方法。 确保[!DNL RT-CDP]与CRM保持一致。 要求所有源系统引用相同的CRM帐户ID。 |
>| 自定义帐户ID | 多个CRM实例或一个专有帐户主机 | 需要源系统ID与规范帐户ID之间的映射层。 更加灵活，但增加了复杂性。 |
>| DUNS编号或域 | 第三方数据扩充是主要帐户源 | 当第一数据提供程序是主源时非常有用。 可能需要基于域的解析的模糊匹配。 |

>[!NOTE]
>**决定：人员与帐户关系模型**
>
>人员（潜在客户、联系人）如何与帐户关联？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 一对一（每个人属于一个帐户） | 使用干净的CRM数据的简单B2B模型 | 简单明了。 最常见于中端市场B2B。 |
>| 多对多（人员可以属于多个帐户） | 复杂的企业关系、顾问或合作伙伴网络 | [!DNL RT-CDP] B2B edition本机支持此功能。 增加了受众复杂性，但准确反映了现实世界的关系。 |

**UI导航：**&#x200B;平台>配置文件>浏览（验证统一帐户配置文件）

**密钥配置详细信息：**

- 验证F2中是否已实施B2B XDM架构（XDM业务帐户、XDM业务人员帐户）
- 确认CRM和[!DNL Marketo]源连接器正在从F3中主动摄取帐户和人员数据
- 验证人员与帐户的关系是否在身份图中通过F4解析
- 通过浏览示例帐户配置文件来检查帐户配置文件的完整性

**Experience League文档：**

- [Real-Time CDP B2B edition概述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [Real-Time CDP中的B2B架构](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Marketo Engage连接器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce连接器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/crm/salesforce)

### 第2阶段：客户受众评估

此阶段使用帐户属性、人员属性和人员活动数据的组合来定义和评估帐户级别的受众。

**应用程序函数：** [!DNL RT-CDP] B2B：帐户受众评估，[!DNL RT-CDP]：受众评估

**您将配置的内容：**&#x200B;此阶段使用帐户属性、人员属性和人员活动数据的组合来定义和评估帐户级别的受众。 使用[!DNL RT-CDP] B2B edition中的客户受众，您可以根据公司特征（行业、收入、员工人数）以及与这些客户关联的人员的参与行为来细分客户。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决定：受众评估方法**
>
>帐户受众成员资格的更新速度必须如何？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 批量评估（每天） | Campaign受众每日节奏进行刷新，基于文件的激活，广告平台受众 | 大多数帐户受众都使用批次评估。 处理组合了帐户和人员属性的复杂多实体查询。 对于大多数B2B用例，即每日刷新可以接受的情况已足够。 |
>| 流式处理评估 | 需要近乎实时资格的[!DNL Marketo]或CRM激活 | 帐户受众的流资格有限。 只有简单的帐户属性条件符合流式评估的条件。 人员级别的行为条件通常需要批处理。 |

>[!NOTE]
>**决定：帐户受众定义方法**
>
>您将如何定义帐户受众标准？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 仅限帐户属性 | 简单的第一目标定位（行业、收入、地区） | 实施速度最快。 仅限帐户级别的数据。 用于广泛定位。 |
>| 帐户+人员属性 | 定向关联人员符合特定条件（职务、部门）的帐户 | 更精确的定位。 结合第一和人口统计数据。 |
>| 帐户+人员属性+人员活动 | 定向具有参与联系人（电子邮件打开、Web访问、内容下载）的帐户 | 最强大但最复杂。 需要来自F3的行为事件数据。 通常需要批量评估。 |
>| 受众构成 | 复杂的受众逻辑，需要排名、拆分、排除或扩充操作 | 对派生的帐户受众使用可视化受众构成画布。 仅限于批次评估。 |

>[!NOTE]
>**决定：禁止显示受众策略**
>
>激活时应排除哪些帐户？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 现有客户抑制 | 针对全新客户的客户获取活动 | 排除具有有效订阅或成功关闭机会的客户 |
>| 有效的销售周期抑制 | 避免干扰活跃销售参与中的客户 | 排除在特定阶段以上有未结商机的客户 |
>| 最近的参与抑制 | 防止最近联系的帐户过度发送消息 | 排除回顾时间范围内（如30天）涉及的帐户 |
>| 无禁止显示 | 针对所有符合条件的客户的品牌认知活动 | 请谨慎使用；这可能会导致在不符合条件的客户上浪费开支 |

**UI导航：**&#x200B;客户>受众>创建受众>生成规则（选择“帐户”作为受众类型）

**密钥配置详细信息：**

- 在Segment Builder中创建新受众时，选择“帐户”作为受众类型
- 帐户属性显示在区段生成器的帐户部分下（行业、收入、帐户状态）
- 可以通过帐户受众生成器中的“人员”关系添加人员属性和活动
- 配置批处理评估计划（如果沙盒尚不存在）
- 创建定位受众（要包括的帐户）和禁止显示受众（要排除的帐户）

**Experience League文档：**

- [帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [受众构成](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### 阶段3：目标配置

此阶段将建立经过身份验证的连接，以连接到将要交付帐户受众的目标目标。

**应用程序函数：** [!DNL RT-CDP] B2B：帐户目标配置，[!DNL RT-CDP] B2B： [!DNL Marketo Engage]集成，[!DNL RT-CDP]：目标配置

**您将配置的内容：**&#x200B;此阶段将建立经过身份验证的连接，以连接到将交付帐户受众的目标目标。 配置包括从目录中选择目标、提供身份验证凭据、配置帐户级别和人员级别字段映射，以及设置导出计划。 每种目标类型都有独特的要求和功能。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决策：目标选择**
>
>哪些目标将接收激活的帐户受众？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| [!DNL Marketo Engage] | B2B领导培养、评分和活动执行 | 本机流连接器。 更新潜在客户/联系人记录。 需要[!DNL Marketo] API凭据（Munchkin ID、客户端ID、客户端密码）。 |
>| [!DNL LinkedIn]个匹配的受众 | [!DNL LinkedIn]上基于帐户的广告 | 支持公司名称和域匹配以实现帐户级别定位。 批量激活。 需要[!DNL LinkedIn]营销活动管理器访问权限。 |
>| [!DNL Salesforce] CRM | 销售支持和CRM帐户列表同步 | 流连接器会更新帐户或联系人记录。 需要具有写入权限的[!DNL Salesforce] API访问权限。 |
>| [!DNL Microsoft Dynamics 365] | 基于[!DNL Dynamics]的组织的销售支持 | 流连接器。 需要[!DNL Dynamics 365] API访问权限。 |
>| 云存储([!DNL S3]， [!DNL Azure Blob]， [!DNL GCS]， SFTP) | 自定义集成、Data Warehouse、合作伙伴共享 | 基于文件的批量导出。 最大程度的灵活性，但需要下游处理。 |
>| [!DNL Google]客户匹配 | 搜索和展示广告定位 | 通过经过哈希处理的电子邮件进行人员级别匹配。 批量激活。 |
>| [!DNL The Trade Desk] | 程序化显示和视频广告 | 人员级别匹配。 批量激活。 |

>[!NOTE]
>**决定：字段映射策略**
>
>应将哪些帐户和人员字段映射到目标？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 仅标识字段 | 只需要匹配标识符的Advertising平台 | 最少的数据传输。 电子邮件或公司域上的目标匹配。 |
>| 身份+核心帐户属性 | CRM或[!DNL Marketo]，其中帐户上下文改进了定位 | 包括行业、收入、员工人数、客户层。 扩充下游记录。 |
>| 完整属性集 | 云存储或数据仓库导出 | 包括所有相关的帐户和人员属性。 最大导出有效负载。 |

**UI导航：**&#x200B;连接>目标>目录>搜索目标>配置

**密钥配置详细信息：**

- 导航到目标目录并选择目标目标
- 提供特定于目标类型的身份验证凭据
- 配置将[!DNL RT-CDP]个XDM字段连接到目标字段的字段映射
- 对于[!DNL Marketo Engage]：提供Munchkin ID、客户端ID和客户端密钥
- 对于[!DNL LinkedIn]：通过OAuth授权，然后选择[!DNL LinkedIn]广告帐户
- 对于云存储：提供存储段/容器名称、路径、文件格式和凭据
- 对于CRM：提供实例URL、API凭据和目标对象类型（帐户或联系人）

**选项差异的位置：**

选项A的&#x200B;**（[!DNL Marketo Engage]流）：**

导航到目标>目录> Adobe > [!DNL Marketo Engage]。 配置Munchkin ID和API凭据。 将[!DNL RT-CDP]标识字段（电子邮件）和配置文件属性映射到[!DNL Marketo]潜在客户字段。 目标会自动处理增量流更新。

选项B （Advertising平台批次）的&#x200B;**：**

导航到目标>目录> Advertising/Social >选择平台。 通过OAuth授权。 配置导出计划（推荐：每日）。 映射经过哈希处理的电子邮件标识符和任何支持的匹配字段。 对于[!DNL LinkedIn]，还映射公司名称和域字段以进行帐户级别匹配。

选项C （基于云存储文件）的&#x200B;**：**

导航到目标>目录>云存储>选择提供程序。 配置存储桶/容器、文件路径模板和文件格式（CSV、JSON或Parquet）。 设置导出计划并选择完全或增量导出。 映射所有所需的帐户和人员属性字段。

选项D （CRM流）的&#x200B;**：**

导航到目标>目录> CRM >选择[!DNL Salesforce]或[!DNL Dynamics]。 提供API凭据和实例URL。 将[!DNL RT-CDP]字段映射到CRM帐户或联系人字段。 确保CRM中存在用于接收受众成员资格数据的自定义字段。

**Experience League文档：**

- [目的地概述](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [目标目录](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [LinkedIn匹配受众目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Amazon S3目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)

### 第4阶段：受众激活

此阶段会将评估的帐户受众发布到配置的目标。

**应用程序函数：** [!DNL RT-CDP] B2B：帐户Audience Activation，[!DNL RT-CDP]： Audience Activation

**您将配置的内容：**&#x200B;此阶段将评估后的帐户受众发布到配置的目标。 激活会创建将帐户受众（源）连接到外部目标（目标）的数据流，应用属性映射，并根据配置的计划或流行为启动导出。 您还将配置隐藏受众以从激活中排除不符合条件的帐户。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决定：导出类型**
>
>激活应该导出完整的受众快照，还是只导出增量更改？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 增量导出 | 下游系统处理增量数据的流目标([!DNL Marketo]、CRM)或批处理目标 | 每次导出的数据量较小。 处理速度更快。 需要下游系统来管理状态。 流目标的默认值。 |
>| 完全导出 | 下游系统替换每次运行的完整受众的批处理目标 | 更大的数据量，但更简单的下游逻辑。 在下游系统不保持状态时很有用。 适用于基于文件的目标。 |

>[!NOTE]
>**决定：激活范围**
>
>每个目标应该激活多少受众？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 每个数据流单个受众 | 通过明确的受众到目标映射进行简单激活 | 最容易进行监控和故障诊断。 一个受众失败不会影响其他受众。 |
>| 每个数据流多个受众 | 前往同一目标的多个相关受众 | 更有效地使用目标连接。 所有受众共享相同的字段映射和计划。 |

**UI导航：**&#x200B;连接>目标>浏览>选择目标>激活受众

**密钥配置详细信息：**

- 从受众列表中选择目标受众
- 查看并确认阶段3中配置的字段映射
- 对于批处理目标：配置导出计划（时间、频率）
- 对于流目标：激活在配置后立即开始
- （可选）使用排除功能添加禁止显示受众
- 触发初始测试激活运行以验证数据流

**选项差异的位置：**

选项A的&#x200B;**（[!DNL Marketo Engage]流）：**

选择要激活的帐户受众。 激活将立即开始流式传输。 在[!DNL Marketo]中验证是否正在使用区段成员资格字段更新潜在客户/联系人记录。 根据这些字段更改配置要触发的[!DNL Marketo]智能营销活动。

选项B （Advertising平台批次）的&#x200B;**：**

选择帐户受众并配置每日导出计划。 首次导出完成后，在广告平台中验证受众是否出现以及填充了成员计数。 允许平台24-48小时处理初始受众文件。

选项C （基于云存储文件）的&#x200B;**：**

选择帐户受众并配置导出计划和文件格式。 在第一次导出后，验证文件是否以预期的格式和内容出现在目标存储位置。 确认下游导入过程已成功使用导出的文件。

选项D （CRM流）的&#x200B;**：**

选择要激活的帐户受众。 激活将立即开始流式传输。 在CRM中验证是否正在使用映射的字段更新帐户或联系人记录。 配置CRM报表、列表视图或工作流自动化以处理更新的字段。

**Experience League文档：**

- [将受众激活到流目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [将受众激活到批处理目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [激活护栏](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [目的地概述](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)

### 第5阶段：治理和监测

此阶段确保帐户受众激活符合数据治理策略和同意首选项，并监控正在进行的激活数据流运行状况。

**应用程序函数：** [!DNL RT-CDP] B2B： B2B数据管理，[!DNL RT-CDP]：同意和治理实施

**您将配置的内容：**&#x200B;此阶段将确保帐户受众激活符合数据治理策略和同意首选项，并确保监视正在进行的激活数据流运行状况。 B2B数据管理对敏感帐户属性（收入、来自第三方提供商的员工计数）实施限制，而同意实施可确保人员级别的通信遵循选择退出偏好设置。 监视可确认激活数据流是否成功完成。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决定：治理强制级别**
>
>应该对B2B激活实施多严格的数据治理？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 全面执行（阻止违规） | 具有敏感数据的生产激活 | 阻止任何违反治理策略的激活。 可能需要迭代字段映射调整以解决违规。 |
>| 警告并继续 | 开发或测试环境 | 允许继续激活但记录警告。 在初始设置期间用于确定潜在问题时非常有用。 |

>[!NOTE]
>**决定：监视方法**
>
>应如何监控激活运行状况？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 基于警报的监控 | 必须快速捕获故障的生产环境 | 为目标激活失败、源流失败和数据流延迟配置警报。 需要设置警报订阅。 |
>| 手动监测 | 开发或低流量激活 | 定期查看目标UI中的数据流运行。 开销较少，但存在延迟故障检测的风险。 |
>| 两者 | 具有复杂的多目标激活的生产环境 | 严重故障预警以及趋势的定期仪表板审查。 建议用于大多数B2B实施。 |

**UI导航：**&#x200B;隐私>策略（用于管理），连接>目标>浏览>选择目标>数据流运行（用于监视）

**密钥配置详细信息：**

- 将数据使用标签应用于包含受限属性的B2B数据集
- 通过评估针对目标营销操作的激活，验证治理策略是否已实施
- 为目标激活失败和源连接器失败配置警报
- 在每个激活周期后查看数据流运行指标（导出用户档案，记录失败）
- 设置许可证使用情况仪表板审核以根据授权跟踪帐户配置文件数量

**Experience League文档：**

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [同意和偏好设置](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [监视目标数据流](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [激活护栏](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

## 实施注意事项

以下部分为成功实施提供了其他指导。

### 护栏和限制

查看以下适用于此用例模式的平台护栏和限制。

- 每个沙盒最多4,000个区段定义，包括帐户受众 — [分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 帐户受众主要使用批次评估进行评估；流式处理资格仅限于简单的帐户属性条件
- 每个目标连接最多100个数据流 — [目标护栏](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- 批量目标每个文件区段最多可导出500万个配置文件
- 流式目标具有由目标合作伙伴设置的每秒吞吐量限制（例如，[!DNL Marketo] API速率限制）
- 合成的受众（来自受众构成）仅限于批次评估，无法使用流式处理
- 每个受众组合画布最多10个组合块
- [!DNL LinkedIn]个匹配的受众需要最小受众规模（通常为300个成员）才能进行激活
- CRM流目标受CRM提供商的API速率限制（例如，[!DNL Salesforce]个批量API每日限制）的约束
- [!DNL RT-CDP] B2B edition许可证控制企业帐户配置文件总数 — [RT-CDP产品描述](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

### 常见陷阱

在实施此用例模式时，请注意以下常见问题。

- **不完整的人员到帐户映射：**&#x200B;如果人员记录（潜在客户、联系人）未通过B2B身份解析正确链接到帐户记录，则依赖于人员属性或活动的帐户受众将会少计符合条件的帐户。 在构建帐户受众之前，请在F4中验证人员与帐户的关系。

- **导致受众漂移的陈旧CRM数据：**&#x200B;如果CRM源连接器未按定期计划运行或静默失败，则帐户属性（行业、收入、状态）将变得陈旧。 这会导致受众包含不再符合条件的帐户，或排除应该符合条件的帐户。 监视源连接器数据流运行状况。

- **Advertising平台匹配率预期：**&#x200B;将帐户受众激活到[!DNL LinkedIn]以外的广告平台时，匹配率取决于与合格帐户关联的联系人的人员级别标识符（哈希电子邮件）是否有效。 没有具有电子邮件地址的关联联系人的帐户不匹配。 监测匹配率并考虑扩充联系数据。

- **[!DNL Marketo]字段映射未对齐：**&#x200B;流式传输到[!DNL Marketo Engage]时，[!DNL RT-CDP]字段映射必须针对现有的[!DNL Marketo]潜在客户或联系人字段。 如果映射的[!DNL Marketo]字段不存在，则更新将以静默方式失败。 在配置目标之前，在[!DNL Marketo]中预创建所有目标字段。

- **阻止激活的治理策略：**&#x200B;帐户属性字段上的数据使用标签（尤其是第三方固件数据）在激活到广告目标时可能会触发治理违规。 在激活之前评估治理合规性，并根据需要调整字段映射以排除受限制的字段。

- **将帐户和人员数据与仅批处理评估结合在一起的帐户受众：**&#x200B;引用人员级别行为事件（例如“至少有一个联系人在过去30天内打开了电子邮件的帐户”）的帐户受众需要批处理评估。 如果用例需要实时资格，则此约束可能会导致意外滞后。

### 最佳实践

请遵循这些建议以获得最佳结果。

- 从少量定义良好的客户受众（ICP层、垂直行业、参与层）开始，然后扩展到复杂的多属性定义
- 为现有客户、活跃商机和最近参与的客户创建专用的禁止受众，以避免浪费支出和渠道冲突
- 使用受众组合通过根据汇总的参与度分数对帐户进行排名来构建分层的帐户受众（高/中/低参与度）
- 对于协调的多渠道营销活动，同时将同一帐户受众激活到多个目标（例如，[!DNL LinkedIn]用于广告，[!DNL Marketo]用于电子邮件， CRM用于销售可见性）
- 为帐户受众实施一致的命名约定，其中包括定位标准和预期渠道（例如“B2B_ICP_Enterprise_Tech_LinkedIn”或“B2B_Suppression_ActiveOpps”）
- 安排在非高峰时间批量激活，以将对下游系统的影响降至最低，并与广告平台处理窗口保持一致
- 监视初始激活后每个目标的匹配率，并迭代身份字段映射以改进匹配
- 维护与[!DNL Marketo Engage]的双向数据流：将参与数据从[!DNL Marketo]摄取到[!DNL RT-CDP] （源连接器）并为闭环系统激活回[!DNL Marketo] （目标连接器）

### 权衡决定

在做出实施决策时，请考虑以下取舍。

>[!NOTE]
>**取舍：受众新鲜度与评估复杂性**
>
>将帐户属性和人员级别行为数据结合在一起的帐户受众可提供最精确的定位，但仅限于批量评估（每日刷新）。 仅基于帐户属性的更简单受众可能有资格进行具有近乎实时更新的流式评估。
>
>- **批处理（复杂标准）支持：**&#x200B;定位精度，结合第一图和行为信号，综合帐户评分
>- **流（简单标准）支持：**&#x200B;受众更新速度、对帐户更改的实时响应、[!DNL Marketo]和CRM中的更快操作时间
>- **建议：**&#x200B;对可以接受每日刷新的主要定位受众使用批次评估（大多数B2B用例）。 保留对时间敏感的触发器的流评估，例如帐户状态更改或高价值帐户警报。

>[!NOTE]
>**取舍：集中激活与特定于目标的受众比较**
>
>您可以将单个统一的帐户受众激活到多个目标，或创建特定于目标的受众，这些受众针对每个渠道的功能和要求进行定制。
>
>- **集中化的受众优势：**&#x200B;跨渠道的一致性、更简单的受众管理、统一的报告
>- **目标特定受众支持：**&#x200B;每个渠道优化的定位（例如，[!DNL LinkedIn]从公司级别属性中受益，而[!DNL Marketo]需要潜在客户级别详细信息）、渠道特定的禁止显示规则
>- **推荐：**&#x200B;从集中式受众开始，以保持一致性，然后仅在渠道要求明显不同时（例如，广告与电子邮件的隐藏窗口不同）创建特定于目标的变体。

>[!NOTE]
>**取舍：实时CRM同步与批次CRM更新**
>
>流式传输到CRM可提供即时的销售可见性，但会使用CRM API配额。 批量文件导出效率更高，但会引入延迟。
>
>- **流CRM同步支持：**&#x200B;销售响应能力、即时帐户警报、实时管道可见性
>- **批次CRM更新支持：** API配额保留、批量更新效率、与CRM数据加载窗口一致
>- **建议：**&#x200B;使用流式CRM同步进行高优先级的帐户资格更改（例如，将帐户移至“销售就绪”层）。 使用批处理文件导出进行批量更新，如每月帐户评分刷新或地区重新分配列表。

## 相关文档

以下资源为此用例模式中使用的功能提供了其他上下文和详细指导。

**[!DNL RT-CDP]B2B edition**

- [Real-Time CDP B2B edition概述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [Real-Time CDP中的B2B架构](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [RT-CDP B2B edition产品描述](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

**受众评估和分段**

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [受众构成](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

**目标和激活**

- [目的地概述](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [目标目录](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [LinkedIn匹配受众目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)
- [Amazon S3目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [将受众激活到流目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [将受众激活到批处理目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [激活护栏](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

**数据源和连接器**

- [源概述](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Marketo Engage连接器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce连接器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/crm/salesforce)

**数据建模和标识**

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [配置文件概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

**数据治理和隐私**

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [同意和偏好设置](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**监视和可观察性**

- [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [监视目标数据流](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [监测源数据流](https://experienceleague.adobe.com/en/docs/experience-platform/sources/api-tutorials/monitor)
- [许可证用量仪表板](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Reporting &amp; Analytics**

- [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [连接概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [数据视图概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)

**教程和指南**

- [Real-Time CDP B2B edition快速入门](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro)
- [为B2B源创建架构](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [沙盒工具](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/sandbox-tooling-api/overview)
