---
title: 已知访客Web/应用程序Personalization
description: 了解如何根据实时用户档案和区段会员资格向已识别的访客提供个性化内容、优惠或促销。
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7957'
ht-degree: 2%

---


# 已知访客的Web/应用程序个性化

此参考计划提供了完整的实施指南，用于使用[!DNL Adobe Journey Optimizer] (AJO)和[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)跨数字表面为已识别的访客提供个性化内容。 它专为需要了解所有可行的实施方法、必须在每个阶段作出的决策以及支持配置的Experience League文档的解决方案架构师、营销技术人员和实施工程师而设计。

已知访客的Web/应用程序个性化是经过身份验证的数字体验的主要个性化模式。 与仅依赖会话内行为信号的匿名访客个性化不同，此模式利用完整的统一配置文件：历史行为数据、区段成员资格、忠诚度级别、购买历史记录、生命周期阶段、计算属性和倾向分数。 它支持跨网页（通过AJO Web渠道）、移动应用程序内消息和内容卡片的个性化。

本指南介绍所有可行的实施选项（基于区段、基于决策和多表面），以及权衡、决策指导和对[!DNL Adobe Experience League]文档的引用。

## 用例概述

拥有经过身份验证的数字资产的组织（电子商务网站、银行门户、订阅服务、忠诚度计划、移动应用程序）需要提供个性化体验，以反映每位客户与品牌的关系。 当访客登录或通过身份解析进行识别时，平台可以访问其完整的统一配置文件，并根据其特定属性、行为和偏好提供量身定制的内容。

此模式适用于以下情况：已识别的访客到达Web资产或打开移动应用程序，系统必须根据实时配置文件数据和受众成员资格确定要显示的最佳内容、选件或促销活动。 个性化决策在边缘进行（以毫秒为单位），从而可在没有可察觉延迟的情况下进行每秒内容交付。

该模式支持确定性个性化（其中特定内容映射到特定受众区段）和动态决策（其中AJO Decisioning评估资格规则和排名策略以根据用户档案选择最佳内容）。 它跨越多个数字表面（网页、移动应用程序内消息和内容卡），支持在客户的数字历程中实现一致的个性化。

## 主要业务目标

此用例模式实现了以下业务目标。

### 提供个性化的客户体验

根据个人偏好、行为和生命周期阶段定制内容、选件和消息。 有关详细信息，请参阅[提供个性化的客户体验](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)。

| KPI | 描述 |
| --- | --- |
| 参与度 | 跨数字表面与个性化内容进行交互的频率和深度 |
| 转化率 | 在收到个性化内容后完成所需操作的访客百分比 |
| 客户满意度(CSAT) | 由相关的个性化数字体验推动的整体满意度提升 |

### 提高网站参与度

通过相关体验，缩短网站停留时间、每次会话显示页面以及与Web内容的交互。 有关详细信息，请参阅[提高网站参与度](../../business-objectives/acquisition-growth/increase-website-engagement.md)。

| KPI | 描述 |
| --- | --- |
| Time On (Web)页 | 增加了在个性化内容领域停留的时间 |
| 参与度 | 包含个性化元素（点击、滚动、交互）的交互率 |
| 转化率 | 改进了从个性化内容与默认内容的转换 |

### 提高移动应用程序参与度

通过个性化的应用程序内体验，推动每日活动使用情况、功能采用和应用程序内转化。

| KPI | 描述 |
| --- | --- |
| 参与度 | 使用个性化消息和内容卡的应用程序内交互率 |
| 保留 | 由个性化体验驱动的改进的应用程序保留 |
| 转化率 | 通过个性化优惠和推荐实现应用程序内转化改进 |

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

## 用例模式

本节介绍核心模式及其功能链。

**已知访客的Web/应用程序个性化**

跨Web、移动应用程序内和内容卡表面根据实时配置文件和区段成员资格为已识别的访客提供个性化内容、优惠或促销。

**函数链：**&#x200B;受众评估> Personalization Decisioning >界面/渠道配置>内容交付>展示跟踪>报表

## 应用程序

在此用例模式中使用以下应用程序。

- **[!DNL Adobe Journey Optimizer](AJO)** — Web渠道配置、应用程序内渠道配置、内容卡渠道配置、决策（优惠选择和排名）、消息创作（个性化内容创建）、营销活动执行、内容试验以及报告
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — 受众评估（边缘、流和批处理）、通过Edge Network进行实时配置文件查找、使用计算属性和倾向分数扩充配置文件
- **[!DNL Adobe Experience Platform](AEP)** — 配置文件存储，身份服务， Web SDK， Mobile SDK，数据流配置，边缘网络交付

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本功能 | 状态 | 必须准备就绪 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 假设就位 | 配置了Web渠道、应用程序内渠道和决策权限的AJO沙盒。 设置了营销人员和内容作者角色的用户。 | [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)，[访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | 配置文件架构必须包括用于个性化和分段的属性（例如，忠诚度级别、购买历史记录、产品兴趣、生命周期阶段）。 用于Web/应用程序交互跟踪和转化事件的体验事件架构。 为[!DNL Real-Time Customer Profile]启用的数据集。 | [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| 数据源和收集 | 必填 | 在Web资产上实施的Web SDK可用于体验交付和展示跟踪。 在移动应用程序上实施的移动SDK，用于应用程序内和内容卡交付。 数据流配置为启用AJO服务以进行边缘个性化。 边缘上可用的实时配置文件数据，可用于亚秒级个性化。 | [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)，[Mobile SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)，[配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| 身份和配置文件配置 | 必填 | 配置的已知身份命名空间（CRM ID、电子邮件、经过身份验证的用户ID）。 匿名会话和经过身份验证的会话之间的身份拼接可操作，以实现从匿名到已知访客个性化的无缝过渡。 已使用`isActiveOnEdge: true`配置Edge合并策略以在边缘解析已验证的配置文件。 | [身份服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| 受众定义和分段 | 必填 | 使用配置文件属性、行为数据和计算属性定义的受众。 为实时个性化资格启用Edge或流评估。 用于基于区段的个性化的受众必须具有进行Edge评估的资格。 | [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[Edge分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么这很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | 计算属性（例如[!DNL Customer AI]倾向分数、生命周期值、参与度分数、产品亲和度、上次购买后间隔天数）通过为受众定义和内容选择提供更丰富的信号，可显着提升个性化质量。 | [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)，[客户人工智能概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| 数据生命周期管理 | 推荐 | 用户档案和事件数据保留策略可确保全新的相关数据为个性化决策提供支持。 同意实施可确保个性化尊重用户偏好。 | [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)，[Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| 数据使用标签和执行 | 推荐 | 用于个性化的配置文件属性（尤其是与PII相邻的属性，如购买历史记录、位置、财务数据）上的治理标签可确保遵守数据使用策略。 | [数据管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)，[数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview) |
| 监视和可观察性 | 推荐 | Edge交付和个性化性能监控有助于检测会降低个性化体验的延迟问题、交付失败或数据刷新问题。 | [可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)，[警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| 报告和分析 | 已包含 | Personalization性能报表是函数链步骤6的一部分。[!DNL Customer Journey Analytics] 通过分析可深入调查个性化对各个访客区段转化、参与和收入的影响。 | [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)，[AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## 应用程序功能

此计划从“应用程序功能目录”中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Journey Optimizer] (AJO)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 渠道配置 | 表面和渠道配置 | 配置Web、应用程序内和内容卡渠道表面以进行个性化投放 |
| 消息创作 | 内容创作 | 为每个表面使用动态内容、个性化表达式和条件块创作个性化内容变体 |
| 营销活动执行 | Campaign设置和激活 | 创建和激活绑定受众、表面和内容的Web营销活动（计划或API触发） |
| Decisioning | 决策设置（选项B/C） | 使用资格规则、排名策略和动态个性化的优惠/内容项目配置决策策略 |
| 内容试验 | 优化（可选） | 对个性化的内容变体运行A/B测试以优化性能 |
| 频度和业务规则 | Campaign设置和激活 | 强制实施展示频率上限以防止过度个性化疲劳 |
| 报告和性能分析 | 报告和优化 | 按表面和区段监测个性化投放、参与和转化量度 |

### [!DNL Real-Time CDP] (RT-CDP)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 受众评估 | 受众定义和评估 | 使用Edge或流式评估的用户档案属性、行为数据和计算属性定义和评估受众 |
| 实时配置文件查找 | 内容交付（运行时） | 通过Edge Network访问实时配置文件属性和区段成员资格，以便做出次秒个性化决策 |
| 轮廓扩充 | 实施前（支持） | 使用计算属性、[!DNL Customer AI]分数和聚合的行为信号丰富用户档案，从而提高个性化质量 |

## 先决条件

在实施此用例模式之前，请确保满足以下条件：

- [ 在目标Web属性上实施了]个Web SDK，并为页面查看和交互跟踪配置了`alloy("sendEvent")`
- [ 在Target移动应用程序上实施了]移动SDK（如果使用应用程序内或内容卡表面）
- [ ]数据流配置了[!DNL Adobe Journey Optimizer]服务已启用
- [ ]配置文件架构包括用于个性化的属性（忠诚度级别、购买历史记录、产品兴趣、生命周期阶段）
- [ 为展示和转化跟踪配置了]体验事件架构
- [ ]已创建的已知身份命名空间和在匿名(ECID)和已验证的身份之间运行身份拼接
- [ 使用`isActiveOnEdge: true`配置的] Edge合并策略
- [ 通过符合边缘条件的评估为实时个性化定义了]个受众
- [ 为每个个性化变量准备的]内容资产（图像、副本、CTA）
- [ 已记录]个Personalization策略：哪些属性驱动哪些内容，针对哪些界面

## 实施选项

此部分介绍了此用例模式的可用实施方法。

### 选项A：基于区段的Web个性化

**最适合：**&#x200B;确定性个性化，其中特定内容变体直接映射到受众区段 — 特定于忠诚度层的主页横幅、生命周期阶段消息传送、客户区段促销内容。 非常适用于内容到区段的映射定义良好且不需要动态排名或优化的情况。

**工作方式：**

基于区段的个性化将内容变体直接映射到受众区段。 当在页面加载时根据符合边缘条件的受众评估已知访客的配置文件时，系统会确定访客属于哪些区段并显示相应的内容变体。 选择基于区段成员资格优先级 — 如果访客符合多个区段的条件，则会显示优先级最高的区段的内容。

此方法使用AJO Web渠道营销活动（或应用程序内/内容卡营销活动）以及条件内容规则或多个处理定位配置。 每个受众区段都与特定的内容体验相关联。 不涉及决策引擎 — 内容选择逻辑完全由区段驱动。

使用AJO消息创作界面创作内容，该界面具有动态内容块，可根据受众成员资格或配置文件属性呈现不同的内容。 Web SDK或移动SDK通过Edge Network实时提供个性化体验。

**关键注意事项：**

- 必须为每个区段预创作内容变体
- 区段定义必须符合Edge条件才能进行实时鉴别
- 添加新区段或内容变体需要更新营销活动配置
- 内容选择是确定性的 — 相同的区段始终会看到相同的内容

**优点：**

- 通过清晰的内容到区段映射轻松实施和维护
- 易于理解并向利益相关者解释个性化逻辑
- 无决策开销 — 更快的内容解析
- 完全控制每个区段接收的内容

**限制：**

- 当区段和内容变量数量增加时，灵活性有限
- 无法基于超出区段成员资格的配置文件级信号动态优化内容选择
- 添加新内容变体需要手动更新促销活动
- 不支持多个选件竞争同一投放位置的次优选件方案

**Experience League：**

- [Web渠道入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [创建Web体验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### 选项B：基于决策的个性化

**最适合：**&#x200B;动态个性化，其中必须使用资格规则和排名策略为每个配置文件选择最佳内容或优惠 — 主页上的次优优惠、个性化产品推荐、动态促销横幅选择。 当多个选件或内容项目争夺同一版面并且系统必须选择最佳选件或内容项目时，这是非常理想的选择。

**工作方式：**

基于决策的个性化使用AJO Decisioning根据内容项目或选件的目录评估每位访客的配置文件，应用资格规则以确定哪些项目符合资格，然后应用排名策略（基于优先级、基于公式或人工智能排名）来选择每个投放位置的最佳项目。

实施涉及创建投放位置（其中显示内容）、使用资格规则和内容表示定义优惠、将优惠组织到收藏集中，以及创建决策策略，通过排名策略将投放位置绑定到收藏集。 在运行时，当访客加载页面时，Edge Network会根据访客的配置文件评估决策策略并返回选定的选件内容。

此方法支持复杂的个性化方案，包括次优优惠、带上限的个性化促销和人工智能优化的内容选择。 优惠可以具有每个配置文件和全局上限限制、有效日期范围以及结合配置文件属性和受众会员资格的复杂资格标准。

**关键注意事项：**

- 需要更多前期配置（投放、优惠、资格规则、收藏集、决策）
- 排名策略可以基于优先级（手动）、基于公式（自定义表达式）或AI排名（自动优化）
- 人工智能排名要求至少1,000个转化事件用于模型训练
- 在高吞吐量情况下，优惠上限计数器可能会稍有滞后
- 对于没有个性化优惠合格的情况，必须配置后备优惠

**优点：**

- 动态、按用户档案的内容选择，无硬编码区段到内容映射
- 支持复杂的资格标准和排名逻辑
- AI排名选项可实现自动优化，无需手动干预
- 优惠上限可防止过度暴露特定内容
- 集中化优惠管理 — 可在各种活动和渠道中重用优惠

**限制：**

- 比基于区段的个性化更高的实施复杂性
- 人工智能排名需要足够的转化事件量才能进行训练
- 与直接基于区段的内容交付相比，决策评估增加了很少的延迟
- 基于公式的排名需要仔细设计，以避免无意中确定优先次序

**Experience League：**

- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [创建个性化优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [创建决策](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 选项C：多表面个性化（Web +应用程序内+内容卡）

**最适合：**&#x200B;跨多个数字表面的一致个性化 — 在网页、移动应用程序内消息和内容卡上提供协调的个性化体验。 适用于组织同时具有Web和移动应用程序属性并希望跨所有数字接触点使用统一的个性化逻辑的情况。

**工作方式：**

多表面个性化可扩展选项A（基于区段）或选项B（基于决策），以跨多个AJO表面类型提供个性化内容。 每个表面类型（Web、应用程序内、内容卡）可能具有不同的内容格式和交付机制，但基础个性化逻辑（受众成员资格或决策）是共享的。

实施包括为每种表面类型配置渠道表面，创作特定于表面的内容（Web表面的Web HTML/CSS，应用程序内消息的结构化，内容卡卡片布局），以及创建针对相应表面的营销活动。 Web SDK处理Web界面交付，而移动SDK处理应用程序内和内容卡交付。

内容卡对于帐户仪表板或应用程序主屏幕上持续的、可拒绝的个性化消息特别有用。 应用程序内消息非常适用于特定于上下文的会话通信。 Web个性化可处理主页横幅、推荐小部件和促销内容。

**关键注意事项：**

- 每种表面类型都需要有自己的渠道表面配置和内容创作
- 必须同时实施和配置Web SDK和Mobile SDK
- 必须为每种表面格式（不同的尺寸、布局、交互模式）设计内容
- 共享受众和决策逻辑可确保表面之间的一致性
- 测试必须涵盖跨设备的所有表面类型

**优点：**

- 跨所有数字接触点的一致个性化体验
- 共享受众和决策逻辑可减少重复
- 内容卡提供持久、非侵入式的个性化表面
- 应用程序内消息可在移动设备上启用特定于上下文的会话个性化

**限制：**

- 最高的实施复杂性 — 需要针对每种表面类型进行配置
- 需要同时实施Web SDK和Mobile SDK
- 必须为每个表面格式设计和维护内容
- 测试范围会随着每种附加表面类型的增加而增大

**Experience League：**

- [应用程序内渠道概述](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [内容卡渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Web渠道入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)

### 选项比较

下表比较了三个实施选项。

| 标准 | 选项A：基于分段 | 选项B：基于决策 | 选项C：多曲面 |
| --- | --- | --- | --- |
| 最适合 | 已知的区段到内容映射 | 每个用户档案的动态内容选择 | 跨Web和移动的一致个性化 |
| 复杂性 | 低 | Medium — 高 | 高（构建于A或B） |
| 延迟 | 最快（直接区段分辨率） | 略高（决策评估） | 视乎相关期权（A或B）而定 |
| 灵活性 | 仅限于预定义的区段内容对 | 高 — 动态排名和资格 | 最高 — 具有共享逻辑的多表面 |
| 内容管理 | 手动区段到内容映射 | 具有资格规则的集中式优惠库 | 具有共享个性化逻辑的每表面内容 |
| 优化 | 手动A/B测试 | 提供了人工智能排名自动优化 | 每表面优化 |
| 需要 | 符合Edge条件的受众， Web SDK | 投放位置、优惠、资格规则、决策 | Web SDK + Mobile SDK，多表面配置 |
| 支持的表面 | Web（主要） | Web（主要） | Web +应用程序内+内容卡 |

### 选择正确的选项

从这些问题开始，选择正确的实施方法：

1. **有多少表面？** 如果您需要在Web和移动设备应用程序上进行个性化，请选择选项C（该选项基于A或B构建基础逻辑）。 如果是Web版，请选择A和B。

2. **您的内容选择动态如何？** 如果您有明确定义的区段到内容变体的映射（例如，3-5个忠诚度层，每个层都有特定的主页横幅），请选择选项A。如果您需要从具有复杂资格和排名的优惠方案目录中进行选择，请选择选项B。

3. **是否需要AI优化选择？** 如果您希望系统自动学习并优化哪些内容对每个配置文件表现最佳，请选择具有人工智能排名决策的选项B 。

4. **有多少内容变体？** 如果少于10个具有明确区段映射的内容变体，则选项A会更简单。 如果您有数十个选件需要资格筛选和排名，则选项B的规模会更大。

5. **是否计划扩展到其他渠道？** 如果您的决策逻辑最终应跨电子邮件、Web和其他渠道提供优惠，则选项B提供了跨渠道Offer Decisioning扩展的集中式决策基础。

## 实施阶段

本节将详细介绍实施的每个阶段。

### 阶段1：定义受众并配置评估

**应用程序函数：** RT-CDP：受众评估

**您将配置的内容：**&#x200B;定义推动个性化内容选择的受众。 这些受众表示将接收个性化体验的访客区段 — 忠诚度层、生命周期阶段、行为同类群组或产品亲和度组。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决定：受众评估方法**
>
>必须多快解决受众会员资格以进行个性化？ 这会直接影响个性化是在页面加载时发生，还是需要延迟。
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 边缘评估 | 实时Web/应用程序个性化，需要不到一秒钟的资格 | 仅限进行简单的配置文件属性检查和区段成员资格。 无时间序列查询或复杂聚合。 对于已知访客个性化是必需的。 |
>| 流式处理评估 | 当配置文件根据行为事件进入/退出受众时的近乎实时的资格 | 支持单个事件和有限的时间窗口查询。 受众更改会在几分钟内反映出来。 适用于可接受轻微延迟的应用程序内和内容卡表面。 |
>| 批次评估 | 每日根据复杂聚合或历史模式刷新区段 | 支持完整的区段规则功能。 不适用于实时个性化，但可用复杂的预计算区段补充边缘受众。 |

>[!NOTE]
>**决策： Personalization属性**
>
>哪些配置文件属性应该驱动受众定义和内容选择？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 用户档案属性（忠诚度级别、生命周期阶段） | 基于已知客户属性的确定性个性化 | 稳定、定义良好的属性。 易于映射到内容变体。 如果配置文件配置正确，则可在边缘使用。 |
>| 行为信号（购买历史记录、浏览模式） | 基于近期行为和参与模式的Personalization | 需要计算属性或流区段。 更加动态，但需要维护的更加复杂。 |
>| 倾向分数([!DNL Customer AI]) | 基于转化、流失或购买可能性的预测个性化 | 需要计算属性。 支持复杂的个性化，但需要ML模型训练数据。 |
>| 组合方法 | 大多数生产实施 | 使用用户档案属性进行主要分段，并使用行为信号和倾向分数进行细化。 |

**UI导航：**&#x200B;客户>受众>创建受众>生成规则

**密钥配置详细信息：**

- 使用区段生成器和引用配置文件属性的区段规则表达式来定义受众
- 确保区段规则表达式符合边缘评估（简单属性检查、区段成员资格）的条件
- 为实时个性化用例配置符合边缘条件的受众
- 考虑使用隐藏受众来排除最近转换或退出的访客

**Experience League文档：**

- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language参考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 第2阶段：设置决策（仅限选项B和C）

**应用程序功能：** AJO： Decisioning

**您将配置的内容：**&#x200B;设置决策基础结构，以便为每个访客动态选择最佳内容或选件。 这包括投放位置（优惠的展示位置）、优惠（有哪些内容可用）、资格规则（有资格）、排名策略（如何选择最佳方案）和决策策略（一切如何关联）。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决定：排名策略**
>
>如何对符合条件的优惠进行排名以选择最适合每位访客的优惠？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 基于优先级（手动） | 具有清晰优惠层次结构的简单用例 | 每个选件都有一个手动优先级值。 最高优先级的合格优惠入选。 易于理解和控制。 |
>| 基于公式（自定义表达式） | 何时将排名考虑用户档案属性 | 自定义排名公式引用用户档案数据（例如，按忠诚度级别+回访间隔列出的分数）。 灵活，但需要配方设计和测试。 |
>| AI排名（自动优化） | 您希望系统自动优化优惠选择时 | ML模型可了解哪些选件对哪些用户档案的效果最佳。 至少需要1,000个转化事件才能进行训练。 最适合高流量放置。 |

>[!NOTE]
>**决定：优惠上限**
>
>是否应该限制向访客或所有访客显示选件的次数？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 每个配置文件上限 | 防止疲劳地重复看到同一选件 | 限制一段时间内每位访客的展示次数。 确保个性化体验的多样性。 |
>| 全局上限 | 限制促销或有限可用性选件的总展示次数 | 限制所有访客的总展示次数。 对于数量有限的促销活动非常有用。 |
>| 无上限 | 常青内容或始终相关的选件 | 无展示次数限制。 适用于忠诚度级别横幅等永久内容。 |

**UI导航：** [!DNL Journey Optimizer] >组件>决策管理

**密钥配置详细信息：**

- 为将显示选件的每个表面创建版面（Web横幅、应用程序内消息区域、内容卡插槽）
- 使用引用用户档案属性和受众成员资格的区段规则表达式来定义资格规则
- 为每个投放位置创建具有内容表示的个性化优惠
- 创建涵盖所有投放位置的后备优惠（在无个性化优惠符合条件时显示）
- 使用收藏集限定符（标记）组织优惠并将其分组到收藏集中
- 使用所选排名策略创建将投放位置绑定到收藏集的决策策略

**Experience League文档：**

- [创建投放位置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [创建决策规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [创建个性化优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [创建后备产品建议](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [创建集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [创建决策](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 阶段3：配置表面和通道

**应用程序函数：** AJO：渠道配置

**您将配置的内容：**&#x200B;配置用于定义将投放个性化内容的位置的渠道界面。 每个表面类型（Web、应用程序内、内容卡）都需要其自己的配置，用于指定表面URI、内容格式和投放参数。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决定：目标表面**
>
>哪些数字界面将接收个性化内容？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 仅限Web渠道 | Personalization关注Web资产 | 需要Web SDK。 最简单的实施。 包括主页横幅、促销区域、推荐小组件。 |
>| 仅限应用程序内渠道 | Personalization专注于移动应用程序体验 | 需要使用Mobile SDK。 涵盖应用程序中特定于上下文的会话消息。 |
>| 仅限内容卡渠道 | 永久性、可拒绝的个性化消息 | 需要使用Mobile SDK或Web SDK。 卡片会一直保留，直到被取消。 非常适合仪表板和主屏幕。 |
>| 多个曲面（选项C） | 跨Web和移动的一致个性化 | 需要Web SDK和Mobile SDK。 每个表面都需要单独的配置和内容。 |

>[!NOTE]
>**决定： Web表面配置方法**
>
>应该如何配置Web界面以进行内容交付？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 单页应用程序(SPA) | 具有客户端路由的现代Web应用程序 | 在Web SDK `sendEvent`调用中使用`renderDecisions: true`。 由SDK自动呈现的内容。 |
>| 多页应用程序(MPA) | 传统的服务器渲染网页 | 通过Edge Network响应在页面加载时交付的内容。 可能需要页面级表面URI配置。 |

**UI导航：** [!DNL Journey Optimizer] >管理>渠道>渠道界面

**密钥配置详细信息：**

- 对于Web表面：配置与目标页面匹配的Web表面URI
- 对于应用程序内表面：使用应用程序ID和表面类型配置移动设备应用程序表面
- 对于内容卡表面：使用应用程序ID或Web上下文配置内容卡表面
- 确保数据流为边缘个性化投放启用了AJO服务

**Experience League文档：**

- [Web渠道入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Web渠道配置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)
- [应用程序内渠道先决条件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [内容卡配置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)

### 阶段4：创作内容

**应用程序函数：** AJO：消息创作

**您将配置的内容：**&#x200B;为每个表面和区段或选件创作个性化内容变体。 这包括设计可视布局、添加引用配置文件属性的个性化表达式、配置条件内容块以及创建可重复使用的内容片段。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决策：内容方法**
>
>应如何为此用例构建个性化内容？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 条件内容块 | 同一布局中的不同内容部分因受众而异 | 具有条件规则的单个内容资产。 适用于次要变量（标题、CTA文本、图像交换）。 |
>| 根据处理区分内容变体 | 每个受众的布局或设计存在根本性差异 | 多个完整的内容资产。 更灵活，但需要维护。 内容试验所需。 |
>| 决策驱动的内容 | 从优惠目录动态选择的内容 | 优惠呈现定义内容。 内容管理集中在选件库中。 |

>[!NOTE]
>**决策： Personalization深度**
>
>应该个性化多少内容？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 表面层个性化 | 仅个性化特定元素（主页图像、CTA、优惠横幅） | 降低复杂性。 将个性化重点放在高影响力的领域。 最常见的起点。 |
>| 整页个性化 | 整个页面布局或内容排序都是个性化的 | 更高的复杂性。 需要大量内容创建。 提供最定制的体验。 |
>| 令牌级个性化 | 内联个性化令牌（名称、层、积分余额） | 最简单的形式。 将配置文件属性值插入其他静态内容中。 |

**UI导航：** [!DNL Journey Optimizer] >营销活动>创建营销活动>编辑内容

**选项差异的位置：**

选项A的&#x200B;**（基于区段）：**

- 使用Web设计器或代码编辑器为每个受众区段创作内容变体
- 将动态内容块与基于受众成员资格的条件结合使用
- 配置引用配置文件属性的个性化表达式（例如，`{{profile.person.name.firstName}}`、`{{profile.loyalty.tier}}`）
- 设置条件规则以根据区段成员资格显示不同的内容

选项B （基于决策）的&#x200B;**：**

- 针对阶段2中定义的每个版面，作者提供内容表示
- 每个选件都有一个或多个与投放位置匹配的呈现（HTML、图像、JSON）
- 通过嵌入决策投放位置，将决策输出集成到网页或应用程序中
- 内容在运行时动态选择 — 创作侧重于单个选件项目

选项C （多表面）的&#x200B;**：**

- 为每个目标表面创作特定于表面的内容（Web HTML/CSS、应用程序内结构化消息、内容卡布局）
- 在适应每个表面的格式约束的同时，维护跨表面一致的个性化逻辑
- 测试每种表面类型上的内容渲染

**Experience League文档：**

- [创建Web体验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [辅助函数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [创建应用程序内消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [创建内容卡片](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### 阶段5：设置和激活活动

**应用程序函数：** AJO：营销活动执行

**您将配置的内容：**&#x200B;创建并激活将受众、表面和内容绑定在一起以进行投放的AJO营销活动。 对于Web个性化，营销活动通常配置为立即激活或持续激活，而不是一次性计划发送。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决定：营销活动类型**
>
>应如何触发个性化营销活动？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 计划的营销活动（始终运行） | 持续为所有符合条件的访客运行的持续个性化 | 将开始日期设置为立即且无结束日期。 活动将保持活动状态，直到手动停止。 最常用于Web个性化。 |
>| 计划的营销活动（有时间） | 与特定促销期关联的Personalization | 设置开始和结束日期。 营销活动在结束日期后自动停止。 适用于季节性促销或限时优惠。 |
>| API触发的营销活动 | 由特定应用程序事件触发的Personalization | 以编程方式触发。 当个性化设置只应针对特定系统事件显示时非常有用。 |

>[!NOTE]
>**决定：频率上限**
>
>此个性化的展示频率是否应受到限制？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 应用频率规则 | 可能会使访客疲乏的促销或基于选件的个性化 | 防止出现太多相同的个性化设置。 通过AJO业务规则配置。 |
>| 无频率限制 | 常青内容个性化（忠诚度级别横幅、仪表板内容） | 不会导致疲劳的始终相关的内容。 无需印象限制。 |

**UI导航：** [!DNL Journey Optimizer] >营销活动>创建营销活动

**密钥配置详细信息：**

- 选择Web、应用程序内或内容卡渠道以及在阶段3中配置的表面
- 绑定阶段1中定义的目标受众
- 链接阶段4中创作的内容
- 配置营销活动计划（立即、日期范围或API触发）
- 查看并激活营销活动
- 对于内容实验：启用实验切换，定义处理，设置流量分配和成功量度，然后再激活

**Experience League文档：**

- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [开始使用营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [内容体验入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### 阶段6：跟踪展示次数并收集数据

**应用程序函数：** AEP：数据源和集合

**您将配置的内容：**&#x200B;确保将来自个性化体验的展示次数、交互和转化跟踪回平台，以便进行报表、受众重新评估和决策优化。

**密钥配置详细信息：**

- 验证呈现个性化内容时Web SDK是否发送`decisioning.propositionDisplay`事件
- 验证当访客与个性化内容（单击、解除）交互时，Web SDK是否发送`decisioning.propositionInteract`事件
- 对于Mobile SDK：验证是否捕获了应用程序内消息和内容卡交互事件
- 为下游成功量度（购买、注册、功能采用）配置转化事件跟踪
- 确保事件包含归因到特定个性化决策的建议ID

**Experience League文档：**

- [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [使用Web SDK跟踪事件](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/commands/sendevent/overview)
- [移动SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)

### 第7阶段：报告和优化

**应用程序功能：** AJO： Reporting &amp; Performance Analysis， Reporting &amp; Analysis

**您将配置的内容：**&#x200B;设置性能监控和分析，以衡量跨界面、区段和内容变体的个性化效果。 使用AJO本地报表进行操作量度，使用[!DNL Customer Journey Analytics]进行跨渠道业务影响分析。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决定：报告范围**
>
>此个性化用例需要什么级别的分析？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 仅限AJO本机报表 | 交付和参与量度的运行监控 | 内置营销活动报表，包含展示次数、点击次数和转化数据。 设置速度最快。 |
>| CJA跨渠道分析 | 深入分析个性化对业务成果的影响 | 需要CJA连接和数据视图。 支持跨渠道的funnel分析、同类群组比较和归因建模。 |
>| AJO + CJA | 全面的运营和分析可视性 | 使用AJO进行日常监控，使用CJA进行战略分析。 建议在生产实施中使用。 |

**UI导航：**

- AJO报表：促销活动>选择促销活动>查看报表
- CJA：“项目”>“创建新项目”

**密钥配置详细信息：**

- 在活动个性化投放期间访问活动实时报告
- 查看已完成的营销活动的历史报告或定期分析
- 对于CJA：配置包含AJO体验事件数据集的连接，并使用个性化指标创建数据视图
- 构建用于跟踪个性化参与率、转化提升、选件接受率和每次访问收入的仪表板
- 对于基于决策的个性化（选项B）：按投放位置和策略有效性排名监控优惠表现

**Experience League文档：**

- [营销活动实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [内容试验报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## 实施注意事项

本节介绍了与此用例模式相关的护栏、常见隐患、最佳实践和权衡决策。

### 护栏和限制

- 对于边缘评估的区段，Edge Network查找的响应时间SLA小于200毫秒 — [实时客户资料护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 每个沙盒最多4,000个区段定义 — [分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Edge区段仅限于简单属性检查和区段成员资格查询 — 无时间序列查询 — [Edge分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- 每个沙盒只能有一个合并策略在Edge上处于活动状态 — [合并策略](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- 每个沙盒最多10,000个批准的个性化优惠 — [决策管理护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每个决策最多30个投放位置 — [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 人工智能排名模型需要至少1,000个转化事件才能进行训练
- 对于单范围请求，SLA在P95下的选件交付响应时间小于500毫秒
- 每个沙盒最多500个活动实时营销活动 — [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每个沙盒最多有25个活动计算属性 — [计算属性护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)

### 常见陷阱

- **未配置Edge合并策略：**&#x200B;如果没有边缘活动合并策略，Edge Network将无法解析已验证的配置文件，从而导致个性化失败或回退到匿名行为。 确保沙盒中只有一个合并策略具有`isActiveOnEdge: true`。
- **不符合边缘条件的受众：**&#x200B;如果受众区段规则表达式使用时间序列查询、复杂聚合或仅对批处理区段的`inSegment()`引用，则它们不符合边缘评估条件，并且无法实现实时个性化。 在受众定义期间验证Edge资格。
- **身份验证期间存在身份拼接间隙：**&#x200B;当访客从匿名过渡到已验证时，可能会出现配置文件尚未解析的短暂情况。 确保正确配置了身份拼接，并且Web SDK在登录后立即通过`identityMap`发送经过身份验证的身份。
- **决策中缺少后备优惠：**&#x200B;如果未配置后备优惠，并且访客没有符合条件的个性化优惠，决策将返回空内容，从而造成体验受损。 始终配置涵盖所有投放位置的后备优惠。
- **Web SDK未发送建议显示事件：**&#x200B;如果将`renderDecisions`设置为`true`但未发送显示事件，则报告将不会反映实际展示次数。 通过在浏览器开发人员工具中检查网络请求来验证事件跟踪。
- **页面加载时内容闪烁：**&#x200B;如果在决策调用期间未预先隐藏个性化内容，则访客可能会在替换默认内容之前短暂看到该内容。 使用预隐藏代码片段或基于CSS的预隐藏可消除闪烁。

### 最佳实践

- 从最初实施的基于区段的个性化（选项A）开始，然后随着选件目录的增长和优化需求的增加，演变为基于决策的个性化（选项B）
- 尽可能使用边缘评估的受众进行实时个性化；保留流和批量受众以供补充用例
- 在个性化体验上实施内容实验，以验证个性化是否可带来比默认内容明显提升的体验
- 设计具有优雅降级策略的个性化 — 如果无法在边缘解析用户档案，则显示设计良好的默认内容而不是损坏的体验
- 使用计算属性创建高价值个性化信号，如参与度分数、产品亲和度和上次购买后间隔天数，这会提高基于区段和基于决策的个性化质量
- 维护内容治理流程，以确保个性化内容在所有表面保持最新、符合品牌要求和合规性
- 按区段监控个性化表现，以确定哪些受众从个性化中受益最大，以及提升度最强的地方

### 权衡决定

>[!NOTE]
>**取舍：Personalization粒度与内容管理复杂性**
>
>更细粒度的个性化（更多区段、更多内容变体、更多界面）提供日益定制的体验，但需要按比例进行更多的内容创建、维护和治理工作。
>
>- **更高的粒度支持：**&#x200B;更好的客户体验、更高的参与度、更强的转化提升
>- **更小的粒度有利于：**&#x200B;更快的实施、更低的内容维护负担、更简单的管理
>- **建议：**&#x200B;从3至5个具有明显内容差异的高影响力区段（例如，忠诚度级别或生命周期阶段）开始。 基于测量到的性能提升扩展粒度。 使用决策（选项B）来扩展粒度，而无需成比例地增加内容管理。

>[!NOTE]
>**权衡：实时决策与确定性内容控制**
>
>基于决策的个性化（选项B）提供动态优化，但减少了对每个访客所看到内容的直接控制。 基于区段的个性化（选项A）提供完全的确定性控制，但限制动态优化。
>
>- **决策支持：**&#x200B;可扩展性、自动优化、复杂的资格方案
>- **基于区段的优惠：**&#x200B;可预测性、合规性控制、利益相关者透明度
>- **建议：**&#x200B;对于需要精确控制的合规性敏感内容（法规消息、层级特定的定价），使用基于区段的个性化。 对动态优化可增加价值的促销内容、优惠和推荐使用决策。

>[!NOTE]
>**取舍： Edge数据可用性与个性化丰富度**
>
>Edge评估的个性化仅限于边缘配置文件存储中可用的属性。 更丰富的个性化信号（完整行为历史记录、复杂的计算属性）可能需要服务器端查找或预计算。
>
>- **仅支持Edge：**&#x200B;秒延迟，最简单的架构
>- **预计算的扩充好处：**&#x200B;更丰富的个性化信号，更复杂的受众定义
>- **推荐：**&#x200B;使用计算属性将丰富行为信号预聚合到边缘可用的配置文件属性中。 这提供了丰富的行为数据以及边缘计算的速度。

## 相关文档

以下资源提供了有关本指南中引用的技术和配置的更多详细信息。

### Web渠道个性化

- [Web渠道入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [创建Web体验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Web渠道配置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### 应用程序内和内容卡渠道

- [应用程序内渠道概述](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [应用程序内渠道先决条件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [创建应用程序内消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [内容卡渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [内容卡配置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [创建内容卡片](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### 决策管理

- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [创建投放位置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [创建决策规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
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
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### 受众和分段

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language参考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 身份和配置文件

- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [身份标识图链接规则](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [配置文件概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### 数据收集和SDK

- [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [安装Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [移动SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Edge Network Server API概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### 营销活动和试验

- [开始使用营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [内容体验入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [内容试验报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### 计算属性和扩充

- [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [计算属性UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Customer AI概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### 报告和分析

- [营销活动实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### 治理和隐私

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### 护栏

- [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity服务护栏](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
