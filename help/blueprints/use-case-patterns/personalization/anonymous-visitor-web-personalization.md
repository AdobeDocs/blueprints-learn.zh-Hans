---
title: 匿名访客Web Personalization
description: 了解如何根据会话中行为信号向未识别的访客提供个性化的Web内容。
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '8076'
ht-degree: 1%

---


# 匿名访客Web个性化

此参考计划提供了实施指南，用于根据会话中行为信号向匿名（未识别）访客提供个性化Web内容。 它涵盖了完整的实施生命周期（从[!DNL Web SDK]配置和边缘受众定义到内容交付和性能报告），专为使用[!DNL Adobe Journey Optimizer] (AJO)、[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)和[!DNL Adobe Experience Platform] (AEP)的解决方案架构师、营销技术人员和实施工程师而设计。

使用此计划可了解架构、评估实施选项、做出明智的配置决策以及找到每个实施阶段的相关Experience League文档。

模式只对有限的数据起作用 — 只有可以在当前会话中观察到的内容，以及以前使用同一设备或Cookie访问累积的任何匿名边缘配置文件。 这使得它适用于funnel顶部个性化，即访客没有帐户或没有进行身份验证。

## 用例概述

匿名访客Web Personalization满足了向尚未识别身份的网站访客提供相关、个性化内容的业务需求，这些访客尚未登录，没有已知的身份，并且无法解析为统一的客户个人资料。 尽管存在此限制，但可以使用会话中行为信号来实现有意义的个性化：页面查看次数、网站逗留时间、滚动深度、反向链接来源、地理位置、设备类型和UTM促销活动参数。

此模式使用AJO的Web渠道表面和基于代码的体验来实时修改页面内容。 Edge分段是主要的评估方法，因为当访客导航网站时，必须在不到一秒钟的延迟内做出决策。 [!DNL Web SDK]收集行为信号并将它们发送到[!DNL AEP Edge Network]，边缘评估的受众规则将决定要投放的内容变体。

与利用完整的统一配置文件和区段成员资格的已知访客Web/应用程序个性化不同，此模式受当前会话中可观察的数据以及与访客的ECID ([!DNL Experience Cloud ID])关联的任何匿名边缘配置文件的限制。 这种区分对于实施规划至关重要：可用于个性化的行为信号仅限于[!DNL Web SDK]捕获的内容以及通过基于Cookie的ECID跨会话保留在边缘配置文件存储中的内容。

## 主要业务目标

此用例模式支持以下业务目标。

**[提高网站参与度](../../business-objectives/acquisition-growth/increase-website-engagement.md)**

通过针对匿名访客信号量身定制的相关体验，缩短网站访问时间、每次会话页面数以及与网络内容的交互。

| KPI |
| --- |
| Time On (Web)页 |
| 参与度 |
| 转化率 |

**[提供个性化的客户体验](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

根据个人的偏好、行为和生命周期阶段定制内容、选件和消息 — 即使对于尚未标识自己的访客。

| KPI |
| --- |
| 参与度 |
| 转化率 |
| 客户满意度(CSAT) |

**[提高转化率](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

通过根据行为上下文提供最相关的内容，提高完成所需操作（如购买、注册或表单提交）的访客和潜在客户的百分比。

| KPI |
| --- |
| 转化率 |
| 商机转换 |
| 每个潜在客户的成本 |

## 战术用例示例

以下示例说明了可应用此模式的特定场景。

- **基于反向链接源的登陆页面标题A/B测试** — 对来自Google、社交媒体或直接流量的访客测试不同的标题，以通过客户获取渠道优化参与
- **基于浏览行为的类别亲和度推荐** — 根据当前会话中查看的页面显示产品或内容推荐，以提高发现和转化
- **即将离开的访客的退出意向选件** — 当行为信号指示访客即将放弃网站时，提供促销选件或潜在客户捕获表单
- **地理定位促销横幅** — 根据访客的地理位置显示特定于位置的促销活动、商店定位器内容或区域选件
- **特定于设备的内容布局优化** — 根据访客使用的是台式机、平板电脑还是移动设备，调整内容布局、图像大小和CTA版面
- **新访客与回访访客的欢迎消息** — 区分首次访客与使用ECID跨会话持久性的回访匿名访客的体验
- **基于当前会话中已查看页面的内容推荐** — 根据访客已查看的页面动态显示相关文章、产品或资源
- **基于UTM促销活动参数的动态主页横幅** — 个性化主页横幅以匹配引用促销活动的消息传递或创意

## 关键绩效指标

使用以下KPI衡量此用例模式的有效性。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| Personalization展示率 | 投放了个性化内容的符合条件的页面查看次数的百分比 | AJO促销活动报表：展示次数/页面查看总数 |
| 点进率(CTR) | 导致点击的个性化内容展示的百分比 | AJO促销活动报表：点击次数/展示次数 |
| 参与度提升 | 增加个性化内容与默认内容的页面时间、每会话页面数或滚动深度 | CJA工作区比较：个性化同类群组与控制 |
| 转化率 | 向个性化内容公开并完成所需操作的访客百分比 | CJA funnel analysis：展示>互动>转化 |
| 跳出率降低 | 减少接收个性化内容的访客的单页会话 | CJA会话分析：个性化与默认跳出率差异 |
| 试验成功率 | 产生具有统计意义的入选者的A/B测试的百分比 | AJO实验报告：实验达到置信阈值 |

## 用例模式

下面描述了此用例的核心模式和功能链。

**匿名访客Web Personalization**

通过AJO Web渠道，根据会话中行为信号为未识别的访客提供个性化内容。

**函数链：** Web表面配置>行为规则评估>内容交付>展示跟踪>报告

## 应用程序

在此用例模式中使用以下应用程序。

- **[!DNL Adobe Journey Optimizer] (AJO)** — Web渠道表面配置、内容创作（基于Web和代码的体验）、活动执行、内容试验（A/B测试）、决策（动态内容选择）和报表
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 基于会话中行为信号的实时受众评估的Edge分段；匿名边缘配置文件管理
- **[!DNL Adobe Experience Platform] (AEP)** — [!DNL Web SDK]用于行为信号收集，[!DNL Edge Network]用于实时数据路由和个性化投放，数据流配置

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本函数 | 状态 | 必须准备好的内容 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 假设就位 | 配置了Web渠道权限的AJO沙盒。[!DNL Web SDK] 向实施团队授予实施权限和数据流访问权限。 为用户提供允许Web渠道配置、受众管理和活动执行的角色。 | [访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | 体验事件架构捕获Web行为信号（页面查看次数、点击次数、滚动深度、引用数据、UTM参数）。 架构必须包含标准Web交互字段组，并启用边缘配置文件以支持实时评估。 必须创建对应的数据集并启用配置文件。 | [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| 数据源和收集 | 必填 | 必须在配置了数据流以将数据路由到[!DNL AEP Edge Network]的所有目标Web属性上实施[!DNL Web SDK]。 数据流必须启用[!DNL Adobe Experience Platform]和[!DNL Adobe Journey Optimizer]服务。 这是一个关键依赖项 — 如果没有[!DNL Web SDK]，将无法进行行为信号收集或体验交付。 | [Web SDK 概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home) |
| 身份和配置文件配置 | 必填 | ECID ([!DNL Experience Cloud ID])配置为匿名访客的主要身份命名空间。 必须使用`isActiveOnEdge: true`配置Edge合并策略，才能解析边缘上的匿名配置文件数据。 每个沙盒的Edge上只能有一个活动合并策略。 | [Identity Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| 受众定义和分段 | 必填 | 根据会话中行为信号定义的Edge评估的受众区段。 Edge分段对于次秒评估延迟是强制性的。 区段规则必须仅使用符合边缘条件的区段规则表达式（简单属性检查和区段成员资格 — 无时间序列查询或复杂聚合）。 | [Edge分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么它很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 不适用 | 匿名访客的值有限，因为要聚合的历史配置文件数据最少。 如果Edge配置文件跨多个会话从先前的匿名访问中收集到有意义的行为数据，则可能会变得适用。 | [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 数据生命周期管理 | 推荐 | 应为匿名边缘配置文件配置假名配置文件过期，以管理存储并遵守隐私要求。 仅限ECID的用户档案可设置为在14天到365天之间过期。 应为行为数据收集强制实施Cookie同意策略。 | [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 数据使用标签和执行 | 推荐 | 行为数据上的治理标签可确保法规遵从性，尤其是对于地理定位（S2敏感地理标签）和基于设备的个性化。 标签可防止在未经授权的个性化上下文中使用受限制的行为数据。 | [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| 监视和可观察性 | 推荐 | [!DNL Edge Network]和[!DNL Web SDK]数据流监视可帮助检测个性化投放问题。 为数据流失败、摄取错误和边缘投放异常配置警报。 对于个性化故障会降低访客体验的生产部署而言，这一点至关重要。 | [可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 报告和分析 | 已包含 | Personalization性能报表是功能链（第5阶段）的一部分。 对匿名访客个性化有效性进行CJA分析后，可在AJO原生报表之外进行深入的funnel分析、同类群组比较和转化影响测量。 | [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## 应用程序功能

此计划从“应用程序功能目录”中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Journey Optimizer] (AJO)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 渠道配置 | 阶段1：Web表面配置 | 配置Web渠道界面，定义将在目标Web属性上提供个性化内容的位置 |
| 消息创作 | 阶段3：内容创作和变量创建 | 使用Web设计器、基于代码的体验编辑器或内容模板为Web界面创作个性化的内容变体 |
| 营销活动执行 | 阶段4：营销活动和投放配置 | 创建和激活绑定受众、内容和投放配置的Web营销活动 |
| Decisioning | 阶段3：内容创作和变量创建（选项C） | 为基于行为信号的动态内容选择配置决策策略、资格规则和排名策略 |
| 内容试验 | 阶段3：内容创作和变量创建（选项B） | 使用流量分配、成功量度和置信度阈值配置A/B和多变量内容试验 |
| 报告和性能分析 | 第5阶段：报告和性能分析 | 监测个性化投放量度、变量有效性、实验结果和转化影响 |

### [!DNL Real-Time CDP] (RT-CDP)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 受众评估 | 阶段2：行为受众定义 | 使用会话中行为信号定义和评估基于边缘的受众区段，以实现实时个性化定位 |

## 先决条件

请在开始实施之前完成以下操作。

- [ 在所有目标Web属性上实施了] [!DNL Web SDK]，其中`sendEvent`调用捕获了页面查看次数、点击次数和相关行为交互
- [ 在数据收集UI中配置了]数据流，启用了[!DNL Adobe Experience Platform]和[!DNL Adobe Journey Optimizer]服务
- [ ]体验事件架构存在于Web交互字段组（页面查看次数、引用数据、UTM参数、设备上下文）中，并且已为配置文件启用
- [ ] ECID身份命名空间已配置并在Web行为事件架构中指定为主要身份
- [ ] Edge合并策略在target沙盒中配置了`isActiveOnEdge: true`
- [ ] AJO Web渠道已配置并可在Target沙盒中访问
- [ ]为每个个性化用例设计和批准内容变体（副本、图像、CTA）
- [ ]成功量度已定义（构成测量的转化或参与事件）
- [ 在收集行为数据之前，在网站上实施了] Cookie同意机制以遵守隐私法规

## 实施选项

本节介绍了三种实施方法。 选择最适合您的个性化要求的选项。

### 选项A：基于规则的Web个性化

**最适合：**&#x200B;简单、确定性的个性化 — 地理定位横幅、特定于引用源的头条、特定于设备的布局、新增与回访访客的消息传递。 当可以通过直接条件逻辑确定内容变体时（如果条件X，则显示内容Y），请选择此选项。

**工作方式：**

基于规则的个性化使用边缘计算的受众区段来确定访客看到的内容变体。 每个受众区段都通过营销活动中定义的条件规则映射到特定内容变体。 当访客加载页面时，[!DNL Web SDK]向[!DNL Edge Network]发送行为信号，后者根据定义的受众规则（以毫秒为单位）评估访客的边缘配置文件。 匹配的内容变体在[!DNL Edge Network]响应中返回并在页面上呈现。

此方法需要在RT-CDP中定义不同的受众区段（例如“来自Google搜索的访客”、“加利福尼亚的访客”、“移动设备访客”），并在AJO中创建相应的内容变体。 营销活动使用条件内容规则将每个受众捆绑到其内容变体，或者为每个区段单独捆绑营销活动。 不涉及AI排名或流量拆分 — 受众与内容之间的关系是确定性的。

**关键注意事项：**

- 需要明确定义的受众标准，这些标准可以表示为符合边缘条件的区段规则表达式
- 必须为每个受众区段预创作内容变体
- 添加新的个性化规则需要创建新的受众区段和内容变体
- 不提供内容变体有效性的统计测量

**优点：**

- 最易于实施和理解 — 受众和内容之间明确的原因和效果关系
- 无需试验性开销或流量拆分
- 确定性行为使测试和QA变得简单
- 延迟低，因为边缘评估完全基于规则
- 当企业已经知道哪些内容最适合每个区段时，即可正常使用

**限制：**

- 没有内置机制来衡量个性化是否优于默认内容
- 需要手动确定要显示每个区段的内容
- 不会随着时间的推移而调整或优化 — 在手动更改之前是静态规则
- 扩展到多个区段和变体会增加配置的复杂性

**Experience League：**

- [Web渠道入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### 选项B：基于试验的Web个性化

**最适合：** A/B和多变量测试 — 测试标题变体、CTA按钮颜色、版面选择、促销优惠 — 具有统计意义测量。 在提交永久个性化规则之前，如果您需要验证哪个内容变体的表现最佳，请选择此选项。

**工作方式：**

基于试验的个性化使用AJO内容试验将访客随机分配给内容处理组，并衡量哪个变体对于定义的成功量度表现最佳。 流量在变量之间拆分（例如，A/B为50/50，A/B/C为33/33/34），并跟踪性能，直到达到统计显着性为止。

该实验嵌入在AJO Web营销活动中。 当访客加载页面时，[!DNL Edge Network]会根据配置的流量分配将它们分配给处理组。 在实验期间，访客始终看到相同的处理方式（会话级或访客级持久性取决于配置）。 成功量度（点击次数、转化次数、参与事件）通过[!DNL Web SDK]进行跟踪并在AJO试验报告中报告。

此选项不需要预定义的受众区段进行定位 — 所有访客（或目标子集）都参与试验。 目标是发现哪些内容表现最佳，而不是以预定内容定位已知区段。

**关键注意事项：**

- 需要足够的流量，才能在合理的时间范围内达到统计意义
- 实验使用具有随时有效置信区间的贝叶斯统计模型
- 建议使用维持组（不接收个性化内容）来衡量增量提升
- 每次只能有一个试验处于活动状态
- 对试验进行修改时，需要停止并重新启动活动

**优点：**

- 提供对内容变体有效性的严格统计测量
- 从个性化决策（数据驱动的内容选择）中删除猜测值
- 支持保留组进行真正的增量提升测量
- 带有置信区间和入选者声明的内置试验报告
- 通过确定入选变体，结果可为未来基于规则的个性化（选项A）提供参考依据

**限制：**

- 需要有意义的流量 — 低流量页面可能需要数周才能产生意义
- 流量拆分意味着某些访客在测试期间看到次优内容
- 试验期间无法按区段进行个性化（所有访客或子集均等参与）
- 每个试验最多10个处理变量
- 无连续优化 — 实验是离散的，有开始和结束

**Experience League：**

- [内容体验入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [内容试验报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### 选项C：基于决策的Web个性化

**最佳选择：**&#x200B;动态内容选择 — 类别亲和度推荐、退出意图优惠、行为推荐 — 决策策略在此过程中评估会话信号并从合格项目的目录中选择最佳内容。 当内容选择逻辑对于简单规则而言过于复杂，或者您想要进行人工智能排名优化，或者符合条件的内容项集较大且动态时，可选择此选项。

**工作方式：**

基于Decisioning的个性化使用AJO Decisioning评估行为信号，并从受管理的内容项目（选件）目录中为每位访客选择最佳内容变体。 每个内容项都具有资格规则（符合条件的人员）、表示形式（内容在每个投放位置中看起来是什么样子）和可选的上限限制（可以显示的频率）。 决策策略将投放位置（内容显示在页面上）链接到内容项集合，并应用排名策略来选择最佳选项。

当访客加载页面时，[!DNL Web SDK]发送包含决策范围的[!DNL Edge Network]请求。 决策引擎根据内容项目资格规则评估访客的边缘配置文件，应用排名策略（基于优先级、基于公式或人工智能排名），并返回入选的内容项目。 这种情况发生在边缘，延迟时间为亚秒。

排名策略确定合格内容项的排序方式。 基于优先级的排名使用手动分配的优先级值。 基于公式的排名使用自定义表达式（例如，为页面查看的回访间隔加权）。 人工智能排名使用的机器学习模型会随着时间的推移优化所选的成功量度，但需要至少1,000个转化事件才能进行训练。

**关键注意事项：**

- 需要设置决策组件：投放位置、资格规则、内容项、回退项、收藏集和决策策略
- 人工智能排名策略需要足够的转化量（1,000多个事件）来训练模型
- Edge决策仅限于Edge Profile Store中可用的配置文件属性
- 必须在Decisioning库中管理和维护内容项目
- 对于没有个性化项目符合条件的情况，必须定义回退内容

**优点：**

- 可扩展到大型内容目录，而无需单独的受众到内容映射
- AI排名策略根据观察到的性能持续优化内容选择
- 资格规则和上限约束可提供对内容交付的细粒度控制
- 支持难以表达为受众区段的复杂业务逻辑
- 跨渠道可重用 — 相同的决策策略可以支持Web、电子邮件和移动个性化

**限制：**

- 更高的实施复杂性 — 需要设置完整的决策组件栈栈
- 人工智能排名需要大量的转化量和时间来进行有效培训
- Edge配置文件数据限制限制了匿名访客的资格规则的复杂性
- 内容项目管理开销 — 每个项目都需要表示法、资格规则和维护
- 调试决策逻辑比基于规则的方法更复杂

**Experience League：**

- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [创建投放位置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [创建个性化优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [创建决策](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)

### 选项比较

下表比较了三个实施选项（基于主要标准）。

| 标准 | 选项A：基于规则 | 选项B：试验 | 选项C：决策 |
| --- | --- | --- | --- |
| 最适合 | 已知的区段到内容映射 | 了解哪些内容效果最佳 | 从大型目录中选择动态内容 |
| 复杂性 | 低 | 中 | 高 |
| 延迟 | 次秒（边缘） | 次秒（边缘） | 次秒（边缘） |
| Personalization precision | 区段级别（受众规则） | 访客级别（随机分配） | 访客级别（资格+排名） |
| 内容优化 | 手动（无测量） | 统计测试(A/B) | 连续（人工智能排名）或手动（优先级） |
| 需要受众区段 | 是（边缘评估） | 否（流量拆分） | 可选（适用于资格规则） |
| 测量功能 | 无内置功能（需要CJA） | 内置试验报告 | 内置决策报告 |
| 内容目录大小 | 小（1:1区段到内容） | 小型（2-10种变体） | 大型（不限数量的合格项目） |
| 需要 | Edge受众，内容变体 | 已启用试验的活动 | Decisioning组件（投放、优惠、策略） |

### 选择正确的选项

使用以下决策逻辑选择适当的实施选项：

1. **您是否已经知道应向每个访客区段显示哪些内容？**
   - 是：以&#x200B;**选项A （基于规则）开头**。 您已为每个区段制定了内容策略，需要确定性投放。
   - 否：进入问题2。

2. **是否需要测试少量内容变体以找到最佳业绩者？**
   - 是：选择&#x200B;**选项B（试验）**。 您希望在提交内容策略之前进行统计验证。
   - 否：进入问题3。

3. **您是否拥有包含资格和排名要求复杂的大型内容项目目录？**
   - 是：选择&#x200B;**选项C （决策）**。 您需要扩展范围超过简单规则的动态内容选择。
   - 否：为简单起见，先从&#x200B;**选项A（基于规则）**&#x200B;开始，然后随着需求的增长逐渐过渡到选项B或C。

**组合选项：**&#x200B;这些选项不互斥。 一个常见的进展是首先从选项B（试验）开始发现入选内容，然后使用选项A（基于规则）部署入选者以进行持续交付。 对于需要基于目录进行动态选择的用例，可以将选项C（决策）栈叠到顶部，而选项A处理更简单的确定性规则。

## 实施阶段

以下阶段描述了端到端实施工作流程。

### 阶段1：配置Web界面

**应用程序函数：** AJO：渠道配置

定义Web渠道界面，用于指定在您的网站上交付个性化内容的位置。 Web表面标识特定页面URL或URL模式以及AJO可以插入或替换内容的页面位置（CSS选择器或基于代码的体验表面）。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决策：表面类型** — 应如何向页面交付个性化内容？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| Web渠道（可视编辑器） | 个性化涉及使用拖放可视编辑器修改可见的页面元素（横幅、标题、图像、CTA） | 需要Web设计器浏览器扩展。 最适合营销主导的内容更改。 仅限对现有页面元素进行可视修改。 |
| 基于代码的体验 | 个性化要求注入网站应用程序代码使用和呈现的结构化数据(JSON) | 需要开发人员实施才能使用JSON有效负载。 为复杂的个性化提供最大灵活性。 最适用于SPA、动态组件和程序化渲染。 |
| 二者（混合） | 同一网站上的不同个性化需要不同的投放机制 | 使用Web渠道进行简单的视觉更改和基于代码的体验以进行程序化渲染。 增加了实施的复杂性，但最大限度地扩大了覆盖范围。 |

>[!NOTE]
>**决定：表面范围** — Web表面应覆盖哪个URL范围？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 精确的URL匹配 | Personalization定位特定页面（例如，主页、登陆页面） | 最精确的定位。 每个页面都需要单独的表面。 |
| 带有通配符的URL模式 | Personalization适用于某个类别的页面（例如，所有产品页面、所有博客文章） | 减少表面管理开销。 内容变体必须设计为可在所有匹配页面中使用。 |
| 单页应用程序(SPA)表面 | 网站是一个SPA，其中URL更改不会触发全页重新加载 | 需要在视图更改时具有`sendEvent`调用的SPA感知[!DNL Web SDK]配置。 表面定义使用SPA视图名称而不是URL。 |

**用户界面导航：** [!DNL Journey Optimizer] >管理>渠道> Web配置

**密钥配置详细信息：**

- 为表面定义页面URL或URL模式
- 指定内容放置的CSS选择器或表面URI
- 对于基于代码的体验，定义应用程序代码将引用的表面名称
- 将表面与将在其中创建营销活动的AJO沙盒关联

**Experience League文档：**

- [Web渠道入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [创建Web体验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [基于代码的体验渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [基于代码的体验配置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

### 第2阶段：定义行为受众

**应用程序函数：** RT-CDP：受众评估

根据推动个性化定位的会话中行为信号定义边缘评估的受众区段。 这些受众可确定哪些访客符合每个个性化体验的资格。 Edge评估对于此模式是强制性的，因为必须在访客浏览网站时于次秒时间范围内做出个性化决策。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决策：行为信号选择** — 哪个会话内信号应该推动个性化定位？

| 信号 | 使用时间 | Edge资格 |
| --- | --- | --- |
| 反向链接源/UTM参数 | 特定于营销活动的登陆页面个性化 | 符合条件 — 对当前事件的简单属性检查 |
| 地理位置（国家/地区、城市） | 区域促销、特定语言的内容、商店定位器 | 合格 — 配置文件属性检查 |
| 设备类型（台式机、移动设备、平板电脑） | 设备优化的内容布局和CTA | 合格 — 配置文件属性检查 |
| 在会话中查看的页面 | 类别亲和度，内容推荐 | 符合条件且具有约束 — 仅对简单事件计数进行检查 |
| 新访客与回访访客 | 欢迎消息，渐进式参与 | 符合条件 — ECID持久性指示回访访客 |
| 网站逗留时间/滚动深度 | 退出意图、基于参与的优惠 | 可能需要自定义实施 — 本身不符合边缘条件 |

>[!NOTE]
>**决策：受众评估方法** — 此模式的所有受众都必须使用边缘评估。 在定义区段之前确认资格。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 边缘评估 | 此模式所需 | 区段规则表达式必须符合边缘条件：简单属性比较、区段成员资格检查、无时间序列查询或聚合函数。 次秒评估延迟。 |
| 流式评估（回退） | 当区段规则表达式不符合边缘条件，但近乎实时是可接受的 | 数秒到数分钟的延迟。 支持更复杂的区段规则表达式。 可能会在个性化投放中引入显着的延迟。 |

**UI导航：**&#x200B;客户>受众>创建受众>生成规则

**密钥配置详细信息：**

- 使用区段生成器通过行为属性定义受众规则
- 通过确认区段规则表达式仅使用支持的函数（简单属性比较、区段成员资格）验证边缘资格
- 将合并策略设置为在F4中配置的边缘活动合并策略
- 预览受众群体以验证区段会返回预期结果
- 对于基于会话内页面查看的受众，请使用当前会话中的事件级属性，而不是时间序列查询

**选项差异的位置：**

选项A的&#x200B;**（基于规则）：**
为每个内容变体创建不同的受众区段。 每个区段表示一个特定的行为条件（例如，“反向链接= Google和地域=美国”映射到内容变量A）。 受众数等于个性化规则数。

选项B的&#x200B;**（试验）：**
受众定义是可选的。 如果试验面向所有访客，则不需要受众 — 流量拆分处理变量分配。 如果试验以特定子集为目标（例如，仅移动访客），请为试验资格定义单个定位受众。

选项C （决策）的&#x200B;**：**
定义受众以用作内容项目的资格规则。 这些受众可确定哪些访客符合决策策略中哪些内容项目的条件。 该决策引擎处理从合格项目中的内容选择。

**Experience League文档：**

- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Profile Query Language参考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### 阶段3：创作内容并创建变体

**应用程序功能：** AJO：消息创作，AJO：内容试验（选项B），AJO：决策（选项C）

创建将根据受众成员资格（选项A）、试验分配（选项B）或决策逻辑（选项C）交付给访客的个性化内容变体。 此阶段涵盖使用AJO Web设计器或基于代码的体验编辑器创建内容，以及控制内容选择方式的试验或决策配置。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决策：内容创作方法** — 应如何创作Web内容变体？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| Web可视化编辑器 | 营销团队无需代码即可直观地修改页面元素 | 需要浏览器扩展。 最适合文本、图像和CTA修改。 仅限修改现有页面元素。 |
| 基于代码的体验编辑器 | 内容需要应用程序代码呈现的结构化数据(JSON) | 最大的灵活性。 需要开发人员实施才能使用有效负载。 最适合动态组件和SPA。 |
| HTML/CSS代码编辑器 | 内容修改需要自定义HTML或CSS | 直接代码控制。 需要HTML/CSS专业知识。 最适合复杂布局更改。 |

>[!NOTE]
>**决策： Personalization令牌** — 内容是否应包含使用配置文件或上下文属性的动态个性化？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 静态内容变体 | 每个变体都是一段固定内容，没有动态令牌 | 最简单的方法。 内容是可预测的，并且易于进行QA。 没有缺少属性值的风险。 |
| 使用个性化表达式创建动态内容 | 内容包括可解析为配置文件或事件属性（例如，城市名称、反向链接来源）的Handlebars样式令牌 | 更相关的内容。 要求匿名配置文件中可能为null的属性的回退值。 对辅助函数使用`{{profile.homeAddress.city}}`语法。 |
| 条件内容块 | 不同的内容块根据单个变量中的属性条件渲染 | 减少所需的不同变体的数量。 增加了内容复杂性。 适用于共享布局中的次要变量。 |

**UI导航：** [!DNL Journey Optimizer] >营销活动>选择营销活动>编辑内容

**密钥配置详细信息：**

- 使用Web设计器（可视化修改）或基于代码的体验编辑器（JSON有效负载）创作内容
- 使用个性化表达式编辑器插入来自边缘配置文件属性的动态令牌
- 为匿名用户档案中可能为空的个性化令牌配置后备内容
- 使用测试用户档案预览内容以验证跨场景渲染

**选项差异的位置：**

选项A的&#x200B;**（基于规则）：**
为阶段2中定义的每个受众区段创作不同的内容变体。 使用营销活动配置中的条件内容规则将每个变体绑定到其目标受众。 确保存在与任何受众规则都不匹配的访客的默认内容变体。

选项B的&#x200B;**（试验）：**
创作处理变量（A、B、C等） 用于试验。 在营销活动上启用内容实验，定义治疗变体的内容，设置流量分配百分比，并配置成功量度。

- 定义具有不同内容的2-10个处理变量
- 设置流量分配（例如，A/B为50/50，低风险测试为加权拆分）
- 可选地包括保持组（例如，10%接收默认内容）以测量增量提升
- 选择成功量度：唯一打开次数、唯一点击次数、转化次数或自定义量度
- 设定置信度阈值：95%用于标准测试，99%用于重大决策，90%用于定向学习
- **UI导航：**&#x200B;营销活动>内容试验>添加处理>流量分配>成功量度

选项C （决策）的&#x200B;**：**
设置决策组件栈栈，并将其集成到营销活动中。

1. **创建投放位置** — 定义页面上内容项目的显示位置（Web HTML、Web JSON、Web图像）
   - **UI导航：** [!DNL Journey Optimizer] >组件>决策管理>投放位置
2. **定义资格规则** — 根据Edge配置文件属性创建规则，以确定哪些访客符合每个内容项目的资格
   - **UI导航：** [!DNL Journey Optimizer] >组件>决策管理>规则
3. **创建内容项（优惠）** — 为每个投放位置、资格规则、优先级和可选上限创作具有演示文稿的个性化内容项
   - **UI导航：** [!DNL Journey Optimizer] >组件>决策管理>优惠>创建优惠
4. **创建后备内容** — 定义在没有个性化项目符合条件时返回的后备项目
   - **用户界面导航：** [!DNL Journey Optimizer] >组件>决策管理>优惠>创建后备优惠
5. **组织为收藏集** — 使用收藏集限定符（标记）对内容项进行分组并创建收藏集
   - **UI导航：** [!DNL Journey Optimizer] >组件>决策管理>集合限定符/集合
6. **创建决策策略** — 将投放位置链接到收藏集并选择排名策略（基于优先级、基于公式或人工智能排名）
   - **UI导航：** [!DNL Journey Optimizer] >组件>决策管理>决策>创建决策

**Experience League文档：**

- [创建Web体验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [基于代码的体验渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [创建个性化优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [创建决策](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 阶段4：配置活动和投放

**应用程序函数：** AJO：营销活动执行

创建并激活AJO Web营销活动，该活动会将Web界面（阶段1）、受众定位或试验配置（阶段2-3）和内容变体（阶段3）绑定到可交付成果单元中。 营销活动控制向访客提供个性化内容的时间和方式。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决策：营销活动类型** — 应如何触发营销活动？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 计划的营销活动（始终运行） | Personalization应持续为所有符合条件的访客运行 | 将开始日期设置为无结束日期，以实现历久不衰的个性化。 在Edge实时进行受众评估。 最常用于Web个性化。 |
| 计划的营销活动（有时间） | Personalization与特定的促销期间或季节性活动相关联 | 设置明确的开始和结束日期。 Campaign在结束日期自动停用。 对于促销活动非常有用。 |
| API触发的营销活动 | Personalization投放必须由外部系统事件触发 | 需要API集成。 匿名Web个性化不太常见。 当个性化活动处于活动状态且后端系统必须控制时使用。 |

**UI导航：** [!DNL Journey Optimizer] >营销活动>创建营销活动

**密钥配置详细信息：**

- 选择在第1阶段配置的Web渠道和Web表面
- 绑定目标受众（适用于选项A）或配置试验设置（适用于选项B）或嵌入决策（适用于选项C）
- 设置营销活动计划（开始日期、结束日期或始终开启）
- 配置活动级别的频率上限（如果适用）
- 审查所有配置并激活营销活动

**选项差异的位置：**

选项A的&#x200B;**（基于规则）：**
为每个个性化规则创建一个营销活动，每个营销活动均面向不同的边缘受众及其对应的内容变体。 或者，使用具有条件内容规则的单个营销活动，这些条件内容规则会将受众成员资格映射到一个营销活动中的内容变体。

选项B的&#x200B;**（试验）：**
创建启用了内容实验的单个营销活动。 试验配置（变体、流量分配、成功量度）在阶段3中定义。 激活营销活动以开始试验。

选项C （决策）的&#x200B;**：**
创建嵌入阶段3中配置的决策策略的营销活动。 营销活动的内容操作引用决策范围，该范围会在边缘触发决策引擎。 激活营销活动以开始交付基于决策的内容。

**Experience League文档：**

- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [开始使用营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### 阶段5：报告和分析性能

**应用程序函数：** AJO：报表和性能分析

使用AJO内置报告监控个性化性能，还可以选择使用CJA扩展分析，以更深入地了解跨渠道信息。 此阶段包括访问实时和历史活动报告、审查实验结果和构建自定义分析工作区。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>**决策：报告深度** — 性能分析应该深入到什么程度？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅限AJO本机报表 | 基本交付和参与量度就足够了 | 提供现成的展示次数、点击次数、CTR和转化量度。 可在campaign UI中立即使用。 自定义受限。 |
| AJO报表+ CJA analysis | 需要深入的funnel分析、同类群组比较或跨渠道影响测量 | 需要与CJA数据集关联的AJO连接和数据视图。 启用自由格式分析、自定义计算量度、归因建模和受众发布。 |

**UI导航：** [!DNL Journey Optimizer] >营销活动>选择营销活动>查看报告

**密钥配置详细信息：**

- 在活动营销活动期间访问实时报告以监控实时投放（每60秒刷新一次，显示最近24小时）
- 活动完成后访问历史（所有时间）报表以进行全面分析（可能需要长达2小时才能完全填充）
- 对于选项B（试验）：查看试验报告，了解治疗性能比较、置信区间和入选者声明
- 对于CJA analysis：确保CJA连接包含AJO体验事件数据集，并且数据视图配置了Web个性化量度

**选项差异的位置：**

选项A的&#x200B;**（基于规则）：**
查看每个受众区段的促销活动报表，以比较不同个性化内容变体的交付情况和参与量度。 使用CJA构建一个比较工作区，用于衡量个性化内容与默认内容的转化影响。

选项B的&#x200B;**（试验）：**
查看试验报告以了解统计置信度、治疗提升度和入选者识别。 等待达到置信度阈值后，再声明入选者。 将入选内容作为永久变量应用（过渡到选项A以进行持续交付）。

- **UI导航：**&#x200B;营销活动>内容试验>查看报告
- **Experience League：** [内容试验报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

选项C （决策）的&#x200B;**：**
审查决策绩效指标，包括优惠展示率、选择频度和每个内容项目的转化归因。 分析排名策略的执行方式以及回退内容的提供是否过于频繁（表明资格规则过于严格）。

**Experience League文档：**

- [营销活动实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [内容试验中的统计计算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

## 实施注意事项

此部分涵盖此用例模式的护栏、常见隐患、最佳实践和取舍决策。

### 护栏和限制

在实施之前和期间查看以下护栏。

- Edge区段仅限于简单属性检查和区段成员资格 — 无时间序列查询或复杂聚合 — [Edge分段资格](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- 每个沙盒的Edge上只能有一个活动合并策略 — [配置文件护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 每个沙盒最多4,000个区段定义 — [分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 每个沙盒最多500个活动实时营销活动 — [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每个内容试验最多10个处理变体 — [内容试验限制](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每个沙盒最多10,000个批准的个性化优惠（选项C） — [决策管理护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每个决策最多30个投放位置（选项C） — [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 人工智能排名模型要求至少1,000个转化事件用于训练（选项C）
- [!DNL Edge Network]响应时间SLA：对于边缘评估的区段，小于200毫秒
- 假名配置文件过期：对于仅ECID配置文件可配置14天到365天
- 实时报表每60秒刷新一次，并显示过去24小时的数据
- 活动完成后，可能需要长达2小时才能完全填充历史报表

### 常见陷阱

避免出现以下常见实施错误。

- **[!DNL Web SDK]未向AEP发送行为信号：**&#x200B;请验证数据流已启用[!DNL Adobe Experience Platform]服务并且事件数据集已正确映射。 如果没有此设置，边缘配置文件将不会被填充，受众评估将会以静默方式失败 — 访客会收到默认内容，而不会出现错误指示。
- **Edge受众返回零资格条件：** Edge分段具有严格的资格要求。 时间序列查询、聚合函数和多实体查询不符合边缘条件。 使用简单属性比较或区段成员资格检查重写区段规则表达式。
- **边缘上的合并策略未处于活动状态：**&#x200B;如果受众区段使用的合并策略没有`isActiveOnEdge: true`，则边缘配置文件查找将失败，并且不会提供个性化设置。 每个沙盒只能有一个合并策略在边缘上处于活动状态 — 验证不存在冲突。
- **页面加载时Personalization闪烁：**&#x200B;在页面渲染目标内容区域之前，必须执行检索个性化建议的[!DNL Web SDK] `sendEvent`调用。 实施预隐藏代码片段或异步渲染，以防止默认内容在个性化内容加载之前闪烁。
- **未在SPA路由更改上呈现内容：**&#x200B;当路由更改时，单页应用程序需要具有更新视图信息的显式`sendEvent`调用。 否则，[!DNL Edge Network]不会为新视图重新评估个性化。
- **试验未达到统计显着性：**&#x200B;流量不足或处理变量过多会稀释每个变量的样本量。 减少变体的数量或增加试验持续时间。 不要过早停止试验 — 结果可能会产生误导。
- **仅返回回退内容的决策：**&#x200B;检查个性化内容项目在其有效日期范围内是否获得批准，以及资格规则是否与匿名访客的边缘配置文件属性相匹配。 此外，验证是否尚未达到上限限制。

### 最佳实践

请遵循这些建议以便成功实施。

- **开始简单，然后迭代：**&#x200B;从选项A（基于规则）开始进行初始个性化，然后使用选项B（试验）验证假设和选项C（决策）进行高级用例。 每个选项都建立在基础基础架构之上。
- **使用预隐藏防止闪烁：**&#x200B;在要传递个性化的页面上实施AEP预隐藏代码片段。 这会隐藏目标内容区域，直到个性化内容准备好呈现为止，从而防止出现闪烁情况。
- **有意设计后备内容：**&#x200B;默认（非个性化）内容本身应是高质量的体验。 不符合个性化条件的访客（或[!DNL Edge Network]响应延迟时）不应收到降级体验。
- **在构建受众之前验证Edge资格：**&#x200B;在投资开发受众规则之前，请查看Experience League中的资格条件，以确认区段规则表达式符合Edge资格。 不符合条件的表达式将静默回退到批量或流式评估，对于此模式具有不可接受的延迟。
- **监视边缘交付性能：**&#x200B;为[!DNL Edge Network]响应时间和个性化交付失败设置监视警报。 访客不会看到Edge交付问题（它们会看到默认内容），并且在没有主动监控的情况下可能会检测不到。
- **配置假名配置文件过期时间：**&#x200B;为匿名边缘配置文件设置适当的过期时间，以便在跨会话个性化（识别回访访客）与隐私合规性和存储管理之间取得平衡。
- **使用代表性用户档案进行测试：**&#x200B;在预览个性化内容时，请使用代表实际匿名访客方案（无CRM数据、行为历史记录有限、各种地理位置和设备）的测试用户档案。

### 权衡决定

在规划实施时，请考虑以下取舍。

>[!NOTE]
>**取舍：Personalization广度与实施复杂性**
>
>更细粒度的个性化（许多受众，许多内容变体）会生成更相关的体验，但会增加配置复杂性和内容生成开销。
>
>- **广泛的个性化优势：**&#x200B;简单，上市时间更快，内容生产成本更低。 一小部分受众和变体涵盖了具有有意义的个性化的大多数访客。
>- **粒度个性化偏好：**&#x200B;最大相关性、较高的参与度提升、更好的转化率。 许多受众和变体通过定制的内容处理特定的行为信号。
>- **推荐：**&#x200B;首先从针对最常见访客区段（例如，反向链接来源、设备类型、地理区域）的3-5条高影响力的个性化规则开始。 衡量影响，然后根据观察到的性能和业务价值扩展到更精细的规则。

>[!NOTE]
>**取舍：基于规则的确定性与AI驱动的优化**
>
>基于规则的方法（选项A）使业务部门能够完全控制每个访客看到的内容。 人工智能排名方法（选项C）会随着时间的推移优化内容选择，但会降低选择特定内容的原因的可见性。
>
>- **基于规则的好处：**&#x200B;可预测性、可审计性、业务控制。 营销团队确切知道每个区段接收哪些内容，并且可以向利益相关者解释逻辑。
>- **AI驱动的优点：**&#x200B;性能优化、可扩展性、持续改进。 AI模型发现人类规则编写可能遗漏的内容 — 访客相关性。
>- **建议：**&#x200B;在品牌一致性和利益相关者透明度最为重要的情况下，使用基于规则的内容决策进行高风险的决策。 在手动规则管理变得笨拙且连续优化带来可衡量的提升的大型内容目录中使用人工智能排名。

>[!NOTE]
>**取舍：匿名配置文件持久性与隐私合规性**
>
>假名配置文件过期时间越长，就越有利于跨会话个性化（识别回访访客，随时间建立行为上下文）。 较短的到期时间提高了隐私合规性并降低了存储成本。
>
>- **更长的过期优惠：**&#x200B;更丰富的匿名个人资料、更好的回访访客识别、更多用于个性化决策的数据。 将到期时间设置为90-365天。
>- **更短的到期时间：**&#x200B;隐私合规(GDPR、CCPA)，降低了存储成本，最大程度地降低了配置文件数据失效的风险。 将到期时间设置为14-30天。
>- **建议：**&#x200B;使过期时间与贵组织的Cookie同意政策和隐私要求保持一致。 对于大多数实施，30-90天可在个性化价值和隐私合规性之间实现合理平衡。

## 相关文档

以下Experience League资源提供了有关此用例模式中所用功能的更多详细信息。

**Web渠道体验和基于代码的体验**

- [Web渠道入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [创建Web体验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [基于代码的体验渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [基于代码的体验配置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

**受众和分段**

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language参考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

**Personalization和内容**

- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

**内容试验**

- [内容体验入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [内容试验报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [统计计算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

**决策管理**

- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [创建投放位置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [创建决策规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [创建个性化优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [创建后备产品建议](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [创建集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [创建决策](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

**营销活动**

- [开始使用营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

**[!DNL Web SDK]和数据收集**

- [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [安装Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [标记概述](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)

**身份和配置文件**

- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Real-time Customer Profile概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**数据建模**

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**报告和分析**

- [营销活动实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

**数据治理和隐私**

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [同意和偏好设置字段组](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

**护栏**

- [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity服务护栏](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
