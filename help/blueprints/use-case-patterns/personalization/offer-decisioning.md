---
title: Offer Decisioning
description: 了解如何使用集中式决策逻辑跨渠道为用户档案选择下一个最佳选件或内容。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 8fd511b3-0200-41bf-aff1-e3f2a00a578e
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '8026'
ht-degree: 2%

---

# Offer Decisioning

本指南为使用[!DNL Adobe Journey Optimizer] (AJO) Decisioning和[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)的Offer Decisioning提供全面的实施参考。 它专为需要实施集中化优惠选择逻辑以跨渠道为每个客户档案确定下一个最佳优惠的解决方案架构师、营销技术人员和实施工程师而设计。

使用本指南了解需要配置哪些内容、存在哪些选择以及每个决策适用哪些权衡。

此模式将“显示内容”决策与“显示位置”渠道逻辑分离，从而实现跨电子邮件、Web、移动应用程序和任何其他接触点的一致且优化的优惠选择。 AJO Decisioning管理整个优惠生命周期：优惠创建和目录管理、资格规则（谁可以查看每个优惠）、排名策略（如何在合格优惠中进行选择）、投放位置（优惠出现的位置）和决策策略（将所有内容捆绑在一起）。

## 用例概述

组织经常需要在交互时向每位客户提供最相关的选件、促销或激励。 无论互动发生在电子邮件促销活动中、网站主页上、移动应用程序中，还是多步历程中的决策点，挑战都是一样的：根据客户身份、客户资格以及最有可能带来预期结果的选件，从可用选项目录中选择最佳选件。

Offer Decisioning通过在AJO的决策管理引擎中集中所有优惠选择逻辑来解决此问题。 决策引擎不会将优惠分配硬编码到单独的促销活动或渠道中，而是评估每个用户档案的属性、受众成员资格和上下文信号，以实时确定最佳优惠。 这种集中化可确保同一客户获得一致且经过优化的优惠，无论他们通过哪个渠道开展业务。

此模式与已知访客的Web/应用程序个性化模式在范围上有所不同 — offer decisioning与渠道无关，并且是集中式的，而已知访客个性化侧重于数字表面个性化。 它与目录模型中的行为推荐不同 — 当符合条件的项目集受业务规则、资格限制或监管要求（促销、金融产品、激励）制约时，可使用Offer Decisioning。 当项目集很大、不断变化并且选择由行为相似性或亲和度信号（产品目录、内容库）驱动时，使用行为推荐。

## 主要业务目标

此用例模式支持以下业务目标。

**[提供个性化的客户体验](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
根据个人偏好、行为和生命周期阶段定制内容、选件和消息。
**KPI：**&#x200B;参与度、转化率、客户满意度(CSAT)

**[推动交叉销售和追加销售收入](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
根据行为和购买历史，向现有客户推广补充性和优质产品或服务。
**KPI：**&#x200B;追加销售/交叉销售%，增量收入，客户存留期值

**[提高客户忠诚度和存留期值](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
通过忠诚度计划、奖励和个性化参与，深化客户关系并最大化长期价值。
**KPI：**&#x200B;客户存留期值，保留，追加销售/交叉销售%

## 战术用例示例

以下场景说明了如何在实践中应用Offer Decisioning。

- 电子邮件促销活动中的下一个最佳优惠 — 在发送时为每个收件人选择最相关的促销活动
- 网站上的实时促销横幅 — 决策功能根据访客的配置文件在页面加载时选择选件
- 以最佳方式刺激用户生命周期阶段的个性化应用程序内卡
- 跨渠道优惠一致性 — 相同的决策逻辑提供电子邮件、Web和推送服务，以便客户看到统一的优惠体验
- 基于客户价值层的动态优惠券或折扣选择（例如，高价值客户会获得优质优惠）
- 基于当前订阅级别的产品升级或追加销售选件选择
- 基于层级和活动历史的忠诚度奖励优惠个性化

## 关键绩效指标

以下KPI有助于衡量Offer Decisioning实施的有效性。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 优惠接受率 | 导致点击、赎回或转化的已交付优惠的百分比 | 优惠点击次数或赎回/投放的优惠总数 |
| 选件选择分发 | 在所有决策中选定的每个优惠的比例 | 每个优惠的计数/呈现的决策总数 |
| 回退率 | 没有符合条件的个性化优惠且已提供回退的决策百分比 | 后备展示次数/决策总数 |
| 转化率 | 完成所需操作（购买、注册、赎回）的优惠接收者百分比 | 转化/优惠展示次数 |
| 增量收入 | 与对照组或后备优惠相比，归属于决策选定优惠的收入 | 来自个性化优惠的收入 — 来自后备/控制的收入 |
| 跨渠道一致性分数 | 在定义的窗口内跨多个渠道接收相同选件的用户档案的百分比 | 一致的优惠/多渠道展示次数总计 |
| 优惠点进率 | 导致点击的优惠展示次数百分比 | 优惠点击次数/优惠展示次数 |

## 用例模式

本节介绍Offer Decisioning的功能链和模式定义。

**Offer Decisioning**

使用集中式决策逻辑跨渠道为用户档案选择下一个最佳优惠或内容。

**功能链：**&#x200B;受众评估>优惠资格>排名策略>决策执行>投放>报告

请参阅[实施选项](#implementation-options)部分，了解每个组合的表现方式。

## 应用程序

在此用例模式中使用以下Adobe应用程序。

- **[!DNL Adobe Journey Optimizer](AJO)** — 用于优惠创建、资格规则、排名策略、投放位置和决策策略的决策管理引擎；用于优惠投放的渠道配置和消息创作；营销活动和历程执行
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — 优惠资格区段的受众评估；资格和排名中使用的配置文件数据和计算属性
- **[!DNL Adobe Experience Platform](AEP)** — 支持AJO和RT-CDP的统一配置文件存储、身份解析和数据基础

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本函数 | 状态 | 必须准备好的内容 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 假设就位 | 启用了Decisioning权限的AJO沙盒。 分配给实施团队的优惠管理角色（决策经理、优惠批准者）。 | [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)，[访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | 配置文件架构必须包括用于优惠资格规则的属性（例如，忠诚度级别、购买历史记录、订阅类型）。 应建立用于跟踪优惠展示次数、点击次数和转化次数的优惠响应/交互架构。 | [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| 数据源和收集 | 假设就位 | 资格规则中使用的配置文件属性必须是最新的。 对于Web交付（选项B），必须在数据流上启用AJO服务的情况下实施Web SDK。 对于电子邮件投放，用户档案属性必须在发送时可解析。 | [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)，[配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| 身份和配置文件配置 | 假设就位 | 必须在提供优惠的所有渠道中解析用户档案。 为了实现跨渠道选件一致性，统一身份至关重要 — 必须在电子邮件、Web和移动上下文中识别相同的配置文件。 实时Web/应用程序投放需要边缘活动合并策略。 | [身份服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| 受众定义和分段 | 必填 | 必须定义和评估用作优惠资格标准的受众（例如“高价值客户”、“试用用户”、“忠诚度金级客户”）。 评估方法必须与投放延迟相匹配 — 实时Web/应用程序的边缘评估，电子邮件促销活动的批量或流式传输。 | [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么它很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | 客户人工智能倾向分数、生命周期值计算和参与量度可显着改善排名策略的有效性。 计算属性（如“上次购买间隔天数”或“90天内的总支出”）可提供更精确的资格规则和基于公式的排名。 | [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)，[客户人工智能概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| 数据生命周期管理 | 推荐 | 优惠历史记录和决策事件数据会随时间累积。 应配置保留策略（过期）以提供交互事件数据集来管理存储并遵守数据保留要求。 | [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)，[数据集过期时间](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| 数据使用标签和执行 | 推荐 | 治理标签可确保具有敏感定位标准（例如，财务状态、健康状况）的选件符合数据使用策略。 资格规则中使用的字段上的标签可阻止不合规的选件定位。 | [数据管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)，[数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview) |
| 监视和可观察性 | 推荐 | 应监控决策引擎性能、回退率和优惠投放运行状况。 针对高回退率的警报可能表示资格规则配置错误或数据刷新问题。 | [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)，[可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 报告和分析 | 已包含 | 选件性能报告是功能链（第7阶段）的一部分。 CJA analysis支持跨渠道选件有效性衡量、收入影响归因和优化机会识别。 | [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)，[Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## 应用程序功能

此计划从“应用程序功能目录”中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Journey Optimizer] (AJO)

下表列出了AJO的功能及其配置实施阶段。

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| Decisioning | 阶段3：决策设置 | 创建优惠项目、定义资格规则、配置排名策略、创建后备优惠、定义投放位置和构建决策策略 |
| 渠道配置 | 阶段4：通道和表面配置 | 配置电子邮件、Web、应用程序内或基于代码的渠道界面以进行选件交付 |
| 消息创作 | 阶段5：内容和投放配置 | 设计包含选件放置区域的消息模板；配置基于代码的体验以进行Web/应用程序交付 |
| 营销活动执行 | 阶段5：内容和投放配置 | 执行计划或API触发的营销活动，以调用决策策略（选项A） |
| 内容试验 | 阶段5：内容和投放配置 | 可选A/B测试不同的排名策略或提供创意变体 |
| 报告和性能分析 | 第7阶段：报告和性能监控 | 监控选件选择分布、接受率、回退率和渠道级别的性能 |

### [!DNL Real-Time CDP] (RT-CDP)

下表列出了RT-CDP函数及其配置位置的实施阶段。

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 受众评估 | 第2阶段：受众评估 | 定义和评估用于优惠资格规则的受众；选择适当的评估方法（批处理、流或边缘） |
| 轮廓扩充 | 阶段1（支持）：计算属性 | 使用计算的属性和倾向分数丰富用户档案，从而提高排名策略的有效性 |

## 先决条件

在开始实施之前，请先完成以下先决条件。

- [ 已启用决策管理功能的]个AJO沙盒
- [ 具有决策管理权限（创建/编辑优惠、投放位置、决策）的]用户角色
- [ ]配置文件架构包含优惠资格所需的属性（例如，忠诚度级别、客户区段、订阅级别）
- [ ]配置文件数据为最新数据，且已主动摄取以保持资格属性新鲜度
- [ 选项A（电子邮件）的]：电子邮件渠道表面配置了验证的子域和预热的IP池
- [ 选项B (Web/App)的]：在数据流上启用AJO服务的情况下实施了Web SDK；配置了边缘活动合并策略
- [ 选项C(历程)的]：历程画布权限和至少配置了一个历程进入事件或受众
- [ ]为每个优惠和版面组合准备的优惠创意资产（图像、文案、CTA）
- [ ]为每个投放位置准备了后备优惠内容
- [ 在RT-CDP中定义和评估的优惠资格规则的]受众

## 实施选项

此部分介绍Offer Decisioning的可用实施选项。 每个选项提供不同的投放渠道和用例上下文。

### 选项A：电子邮件Offer Decisioning

此选项最适合选择要包含在出站电子邮件促销活动（促销电子邮件、新闻稿个性化、包含动态优惠内容的生命周期电子邮件）中的最佳优惠。 在每个收件人的消息渲染时做出决定。

#### 工作原理

在电子邮件呈现期间调用决策策略，以选择最适合每个收件人的优惠。 电子邮件模板包括优惠投放区域，决策引擎将在其中插入所选优惠的内容表示形式（图像、HTML或文本）。 在发送时，引擎会根据优惠资格规则评估每个收件人的用户档案，应用排名策略，并将入选优惠的内容嵌入到电子邮件中。

此方法适用于计划的营销活动（在营销活动执行时评估）和旅程嵌入的电子邮件（在用户档案到达消息操作节点时评估）。 优惠内容（图像、标题、正文和CTA）根据决策结果按收件人进行个性化。

#### 关键注意事项

- 在发送时，使用用户档案的当前状态评估优惠资格
- 由于决策是在消息呈现期间进行的，因此批量受众评估便已足够
- 每个选件都需要一个HTML或图像内容呈现来表示电子邮件投放位置
- 备用选件必须具有用于每个电子邮件版面的内容

#### 优点

- 最简单的实施路径 — 使用标准活动或历程电子邮件投放
- 无客户端SDK要求
- 使用现有的电子邮件基础架构和渠道界面
- 通过批量执行活动支持大量受众

#### 限制

- 决策在发送时作出；无法适应发送后行为
- 投放电子邮件后，选件内容为静态内容（无实时更新）
- 仅限于Hub配置文件存储区中可用的配置文件属性（不限于Edge）

#### Experience League资源

- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### 选项B：Web/应用程序实时优惠决策

此选项最适合在网页或移动应用程序上进行实时选件选择 — 主页促销横幅、帐户仪表板选件小组件、应用程序内选件卡或任何在页面加载或屏幕呈现时应选择选件的数字表面。

#### 工作原理

决策策略在页面加载时调用，或在应用程序屏幕渲染时通过Edge Decisioning网络或基于代码的体验调用。 当访客加载页面时，Web SDK会向Edge Network发送请求，后者根据选件资格规则和排名策略评估访客的边缘配置文件。 在响应中返回选定的选件，并在数字表面上的配置版面中渲染。

对于基于代码的体验，应用程序会检索决策响应并使用自定义前端逻辑呈现选件内容。 对于Web渠道体验，AJO Web渠道可以使用可视化或基于代码的创作，将选件内容直接注入页面。

#### 关键注意事项

- 需要在数据流上启用AJO服务的情况下实施Web SDK或移动SDK
- 实时配置文件查找需要Edge活动的合并策略
- 用于资格的受众必须支持Edge评估（简单的属性检查和区段成员资格）
- 优惠内容呈现应使用JSON或图像URL格式进行客户端渲染
- 必须实施展示跟踪以捕获优惠视图和点击量

#### 优点

- 基于访客当前配置文件状态的实时会话内选件选择
- 通过Edge Network进行的次秒决策延迟
- 选件可适应边缘可用的最新配置文件数据
- 支持通过内容试验对优惠策略进行A/B测试

#### 限制

- 需要客户端SDK实施（Web SDK或Mobile SDK）
- Edge配置文件有一个完整的中心配置文件属性的子集 — 复杂的资格规则可能无法正确评估
- Edge区段具有区段规则复杂性限制（无时间序列查询）
- 需要在基于代码的体验中进行自定义渲染的前端开发

#### Experience League资源

- [使用Edge Decisioning API提供优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [基于代码的体验渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based-experience/get-started-code-based)

**这与已知访客Web/应用程序个性化选项B有何不同：**

基础架构是相同的 — 两者使用边缘位置的AJO Decisioning和Web SDK，并且采用边缘活动合并策略。 不同之处在于目录治理模型。 此选项管理包含资格规则、上限计数器和有效日期的限制优惠目录 — 当业务或法规限制决定可以显示哪些优惠以及显示频率时，使用此选项。[已知访客的Web/应用程序个性化](known-visitor-web-app-personalization.md)选项B使用区段成员资格或排名策略从内容项目中进行选择，而不使用选件生命周期管理。 如果您的项目集很大，并且不断变化，不需要设置上限或进行资格管理，请改用已知访客选项B。

### 选项C：历程决策节点

此选项最适合于多步历程中的优惠选择 — 在客户历程的决策点选择最佳优惠，然后通过下一个操作节点交付它。 当优惠决策是包含等待、条件和多个消息操作的更广泛编排流程的一部分时，可使用此选项。

#### 工作原理

从AJO历程画布中的决策节点调用决策策略。 当用户档案到达决策节点时，引擎会评估优惠资格和排名以选择最佳优惠。 选定的选件会通知下一个消息操作 — 要包含哪个选件内容，要使用哪个渠道，或根据选件结果采用哪个历程分支。

这种方法会启用自适应历程，其中优惠决策影响后续历程步骤。 例如，历程可能选择最佳选件，通过电子邮件投放该选件，等待参与，如果没有打开该选件，则后续使用推送通知。

#### 关键注意事项

- 历程必须设计为决策节点，后跟一个或多个消息操作节点
- 可使用用户档案到达决策节点时的状态评估优惠资格
- 决策和投放之间的历程等待步骤可能会导致用户档案的状态发生更改
- 可与历程分支相结合，根据选择的选件采用不同的路径

#### 优点

- 将选件选择集成到多步编排流程中
- 启用自适应历程，其中选件选择影响后续步骤
- 支持在同一历程中进行跨渠道投放（电子邮件、推送、短信）
- 可以与历程条件结合使用来进行选件后参与跟踪

#### 限制

- 设置比独立的营销活动决策更复杂
- 应用历程吞吐量限制（每秒输入速率5,000个配置文件）
- 决策绑定到历程上下文 — 更改需要历程版本控制
- 必须重新发布历程，优惠目录或决策策略更新才能生效

#### Experience League资源

- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [历程入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### 选项比较

下表比较了三个实施选项（基于主要标准）。

| 标准 | 选项A：电子邮件决策 | 选项B：Web/应用程序实时 | 选项C：历程决策节点 |
| --- | --- | --- | --- |
| 最适合 | 具有每个收件人优惠选择的批量电子邮件营销活动 | Web/应用程序表面实时显示优惠横幅 | 多步骤编排历程中的选件选择 |
| 决策延迟 | 在发送时间（批量渲染期间每个收件人的秒数） | 次秒(Edge Network) | 在历程节点执行时（秒） |
| 渠道 | 电子邮件 | Web、移动应用程序、基于代码的表面 | 历程中的任何渠道（电子邮件、推送、短信） |
| 需要SDK | 否 | 是（Web SDK或移动SDK） | 否（适用于电子邮件/推送）；是（如果Web渠道是历程操作） |
| 受众评估 | 批量处理或流式处理 | Edge | 批处理、流或边缘（取决于历程条目） |
| 配置文件数据范围 | 完整中心配置文件 | Edge配置文件（子集） | 完整中心配置文件 |
| 复杂性 | 低 | Medium — 高 | 中 |
| 吞吐量 | 高（批量Campaign量） | 高（Edge Network规模） | Medium（适用旅程吞吐量限制） |

### 选择正确的选项

使用以下指南为您的用例选择最佳实施选项。

- **如果主要用例是在出站电子邮件营销活动中为每个收件人选择最佳选件，并且没有可用的客户端SDK，请选择选项A**。 这是最简单的实施途径，非常适用于促销电子邮件、新闻通讯和生命周期营销活动。
- **如果访客加载网页或打开移动应用程序时必须实时选择选件，请选择选项B**。 这需要Web SDK或Mobile SDK以及边缘活动合并策略，但提供了最快、最符合上下文的选件选择。
- **如果优惠决策是包含多个步骤、等待和条件分支的更广泛客户历程的一部分，请选择选项C**。 这是所选选件应影响下游历程操作或需要基于选件参与的多渠道跟进时的正确选择。
- **合并选项**，前提是必须跨渠道一致地交付选件。 对全部三个选项使用相同的决策策略，以确保客户在电子邮件（选项A）、网站（选项B）和历程跟进（选项C）中看到相同优惠。

## 实施阶段

以下阶段概述了Offer Decisioning的端到端实施顺序。

### 阶段1：验证基本先决条件

**应用程序函数：** AEP：数据建模和准备，AEP：身份和配置文件配置

此阶段将验证基础数据层是否支持Offer Decisioning。 配置文件架构必须包括选件资格规则中使用的属性，并且身份配置必须启用跨渠道配置文件解析。

#### 决策：资格的用户档案属性

确定优惠资格规则中将使用的配置文件属性。

>[!NOTE]
>配置文件属性的选择会影响资格规则设计和排名策略的有效性。 考虑计算属性和倾向分数以提高决策质量。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 标准配置文件属性（忠诚度级别、购买历史记录） | 属性已存在于配置文件架构中 | 无需更改架构；验证数据新鲜度 |
| 计算属性（生命周期值、参与度分数） | 资格或排名取决于汇总的行为数据 | 需要S1配置；添加了对计算属性刷新节奏的依赖关系 |
| 客户人工智能倾向分数 | 排名应利用基于ML的预测 | 需要足够的训练数据（超过10,000个配置文件以及目标事件）；模型训练时间 |

#### 关键配置详细信息

- 验证配置文件架构是否包含资格规则中引用的字段（例如，`_tenantId.loyaltyTier`、`_tenantId.subscriptionType`）
- 确认存在针对展示、点击和转化事件的优惠交互跟踪架构
- 对于选项B：验证是否配置了边缘活动合并策略以及Web SDK数据流是否启用了AJO服务

#### Experience League文档

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [为轮廓启用架构](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### 第2阶段：配置受众评估

**应用程序函数：** RT-CDP：受众评估

此阶段定义和评估用作选件资格标准的受众。 这些受众确定哪些客户区段有资格获得特定选件（例如，“高价值客户”有资格获得高级选件，“试用用户”有资格获得转化选件）。

#### 决策：受众评估方法

确定受众会员资格必须多久更新一次选件资格。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 批次评估 | 选项A（电子邮件营销活动），在发送时评估资格 | 最简单；支持所有区段规则表达式；每日或按需刷新 |
| 流式处理评估 | 在批处理之间需要近乎实时的受众更新时，选项A或C | 自动适用于符合条件的区段；对区段规则的支持有限（单个事件、属性比较） |
| 边缘评估 | 选项B（Web/应用程序实时），其中资格必须在页面加载时评估 | 次秒；实时Web/应用程序选件需要此变量；仅限于简单属性检查和区段成员资格 |

**UI导航：**&#x200B;客户>受众>创建受众>生成规则

#### 关键配置详细信息

- 为优惠资格定义定位受众（例如，“忠诚度金级客户”、“高价值客户”、“试用用户”）
- 根据需要定义禁止显示受众（例如“最近接收的选件X”）
- 对于选项B：验证资格受众是否有资格进行边缘评估 — 避免在区段规则表达式中进行时间序列查询和复杂聚合

#### 不同选项的位置

选项A （电子邮件决策）的&#x200B;**：**
批量或流式评估就足够了。 在活动执行之前或期间评估受众。 完全支持复杂区段规则表达式，包括基于时间的条件和事件聚合。

选项B的&#x200B;**（Web/应用程序实时）：**
需要Edge评估。 受众必须使用简单的属性检查或区段成员资格条件。 通过验证区段规则表达式是否符合边缘分段资格来测试边缘资格。

选项C （历程决策节点）的&#x200B;**：**
任何评估方法均取决于历程进入标准。 如果历程使用基于受众的条目，则受众评估方法与历程的要求相匹配。

#### Experience League文档

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### 阶段3：设置决策

**应用程序功能：** AJO： Decisioning

这是构建优惠目录、资格规则、排名策略和决策政策的核心阶段。 此阶段将创建所有投放选项(A、B、C)共享的决策引擎配置。

#### 决策：投放渠道和内容格式

确定选件的显示位置以及格式。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 电子邮件(HTML) | 选项A — 在电子邮件正文中呈现为HTML的优惠内容 | 支持丰富格式；必须与电子邮件客户端兼容 |
| 电子邮件（图像URL） | 选项A — 在电子邮件中呈现为托管图像的选件 | 更简单；必须托管和访问图像；无动态文本 |
| Web (HTML) | 选项B — 在网页上呈现为HTML的优惠 | 完整版面控件；支持交互式元素 |
| Web/移动(JSON) | 选项B — 以JSON形式返回的选件数据以进行自定义渲染 | 最大的灵活性；需要前端开发才能呈现 |
| 基于代码(JSON) | 选项B — 为基于代码的体验表面提供数据 | 应用程序控件呈现；最灵活 |

#### 决策：排名策略

确定应如何从符合条件的优惠中选择最佳优惠。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 基于优先级（手动） | 小型选件目录；用于选件排序的明确业务规则 | 配置最简单；手动为每个选件分配优先级值；确定性 |
| 基于公式（自定义表达式） | 排名应考虑用户档案属性（例如，忠诚度级别、回访间隔） | 灵活；使用配置文件数据计算排名分数；需要区段规则表达式设计 |
| AI排名（自动优化） | 大型优惠目录；希望ML随时间推移优化选择 | 至少需要1,000个转化事件才能进行模型训练；从选件性能数据中学习 |

#### 决策：优惠上限

确定是否应当对选件的显示次数进行限制。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 每个配置文件上限 | 防止向同一客户显示同一选件的次数过多 | 避免选件疲劳；在高吞吐量情况下，计数器会延迟几秒钟 |
| 全局上限 | 限制所有配置文件中某个选件的总展示次数（例如，有限库存） | 控制优惠供应；达到上限后，优惠将从决策中排除 |
| 无上限 | 选件具有无限可用性 | 最简单；适用于始终如一的促销活动 |

**UI导航：**&#x200B;组件>决策管理>版面/规则/优惠/决策

#### 关键配置详细信息

1. **创建投放位置** — 通过指定每个投放位置的渠道类型和内容格式来定义优惠的显示位置。
   - UI：组件>决策管理>投放
   - 为每个渠道/格式组合创建一个投放位置（例如，“电子邮件主页横幅 — HTML”、“Web主页 — JSON”、“移动设备应用程序卡 — JSON”）

2. **定义资格规则** — 使用引用配置文件属性或受众成员资格的区段规则表达式创建规则。
   - UI：组件>决策管理>规则
   - 规则可以引用受众会员资格、用户档案属性（忠诚度级别、订阅类型）、日期约束或上下文数据

3. **创建个性化优惠** — 为每个投放位置生成具有内容表示的每个优惠、分配资格规则、设置优先级并配置可选的上限。
   - UI：组件>决策管理>优惠>创建优惠
   - 每个选件需要每个版面的内容表示（例如，适用于电子邮件的HTML，适用于Web的JSON）
   - 分配资格规则以控制哪些配置文件可以查看每个选件
   - 设置优惠有效日期（开始/结束）和可选的频率上限
   - 批准每个选件以使其符合决策条件

4. **创建后备优惠** — 为无个性化优惠合格时显示的每个投放位置构建默认优惠。
   - UI：组件>决策管理>优惠>创建后备优惠
   - 对于决策中使用的每个投放位置，回退都必须具有表示形式

5. **创建收藏集限定符和收藏集** — 使用限定符标记将优惠组织到收藏集中。
   - UI：组件>决策管理>收集限定符
   - 用于决策范围的组相关优惠（例如“夏季促销活动”、“忠诚度奖励”）

6. **创建决策策略** — 将投放位置、收藏集、排名策略和备用优惠绑定到可执行决策中。
   - UI：组件>决策管理>决策>创建决策
   - 每个决策范围将投放位置链接到收藏集，并指定排名方法

#### Experience League文档

- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [创建投放位置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [创建决策规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [创建个性化优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [创建后备产品建议](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [创建集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [创建集合限定符](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [创建决策](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 阶段4：配置渠道和表面

**应用程序函数：** AJO：渠道配置

此阶段将配置用于投放优惠的渠道平面。 配置取决于所使用的实施选项。

#### 决策：渠道类型

确定用例所需的消息传送渠道。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 电子邮件 | 带有电子邮件投放的选项A或选项C | 需要子域委派、IP池、发件人设置 |
| Web | Web表面交付的选项B | 需要Web SDK和数据流配置 |
| 应用程序内 | 移动应用程序交付的选项B | 需要Mobile SDK和推送凭据 |
| 基于代码的体验 | 用于自定义渲染曲面的选项B | 最灵活；应用程序处理渲染 |

#### 不同选项的位置

选项A （电子邮件决策）的&#x200B;**：**
- UI：管理>渠道>渠道界面>创建界面（电子邮件）
- 配置子域、IP池、发件人姓名/电子邮件、回复、取消订阅设置
- 验证用于发送子域的SPF、DKIM和DMARC记录

选项B的&#x200B;**（Web/应用程序实时）：**
- UI：管理>渠道>渠道界面>创建界面（Web或应用程序内）
- 对于Web：配置Web表面URL模式
- 对于基于代码的体验：定义应用程序的表面URI
- 验证数据流是否启用了AJO服务

选项C （历程决策节点）的&#x200B;**：**
- 为历程中使用的每个渠道（电子邮件、推送、短信或Web）配置渠道平面
- 每个历程消息操作都需要相应的活动渠道平面

#### Experience League文档

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [电子邮件表面设置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 阶段5：配置内容和投放

**应用程序函数：** AJO：消息创作，AJO：营销活动执行

此阶段设计消息模板或体验平面以显示选定的选件，然后配置投放机制（营销活动、历程或基于代码的体验）。

#### 决策：优惠呈现的内容方法

确定如何将选件内容集成到消息或体验中。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 电子邮件Designer中的优惠决策组件 | 选项A — 电子邮件模板中的嵌入优惠投放位置 | 拖放；根据决策结果自动呈现优惠内容 |
| 决策策略中基于代码的体验 | 选项B — 应用程序检索并呈现选件数据 | 最大程度地控制渲染；需要前端开发 |
| 嵌入了决策的历程消息操作 | 选项C — 决策节点馈送为历程消息提供内容 | 选件选择和交付在历程流中编排 |

#### 决策：营销活动类型（仅限选项A）

确定这是计划的营销活动还是API触发的营销活动。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 计划的营销活动 | 一次性或定期批次发送给定义的受众 | 在执行时评估受众；设置日期/时间或循环 |
| API触发的营销活动 | 事件驱动或系统触发的发送至指定用户档案的发送 | 在触发器有效负载中指定的配置文件；每个请求最多支持20个收件人 |

#### 不同选项的位置

选项A （电子邮件决策）的&#x200B;**：**

1. 使用电子邮件Designer创作电子邮件
   - UI：营销活动>创建营销活动>选择电子邮件>编辑内容
   - 在电子邮件布局中插入优惠决策组件以定义投放区域
   - 为配置文件级别的内容（名称、忠诚度级别）添加个性化令牌
   - 通过可选的个性化配置主题行和预标题
2. 创建和配置营销活动
   - UI：营销活动>创建营销活动>计划或API触发
   - 绑定目标受众并选择渠道平面
   - 设置执行计划或API触发器配置
   - 查看并激活营销活动

选项B的&#x200B;**（Web/应用程序实时）：**

1. 配置基于代码的体验或Web渠道
   - UI：营销活动>创建营销活动>基于代码的体验（或Web）
   - 将决策策略链接到体验表面
   - 定义渲染格式（基于代码的JSON响应；Web渠道的可视化编辑器）
2. 实施客户端渲染
   - 使用Web SDK `sendEvent`响应检索所选选件
   - 在页面上的指定投放位置呈现选件内容
   - 实施展示和点击跟踪

选项C （历程决策节点）的&#x200B;**：**

1. 使用决策节点设计历程
   - UI：历程>创建历程>添加决策节点
   - 配置决策节点以从阶段3调用决策策略
2. 在决策后添加消息操作节点
   - 配置引用所选选件的电子邮件、推送或短信操作
   - 根据优惠参与度添加等待步骤、条件或分支
3. 发布历程

#### Experience League文档

- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [历程入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 第6阶段：测试和验证

**应用程序功能：** AJO： Decisioning， AJO：消息创作

此阶段将验证决策引擎是否返回测试用户档案的正确选件，以及选件内容是否会在每个投放渠道中正确呈现。

#### 测试决策逻辑

使用具有已知属性的测试用户档案，验证是否根据资格和排名选择正确的选件。

- 创建符合不同资格标准（例如，Gold tier、Silver tier、Trial user）的测试配置文件
- 验证每个测试配置文件是否接收到预期的选件
- 验证与无资格规则匹配的用户档案是否会收到后备优惠

#### 测试内容渲染

预览每个投放渠道中的优惠内容。

- 选项A：将电子邮件预览与测试配置文件结合使用，以验证选件内容是否正确呈现
- 选项B：在暂存环境中测试Edge Decisioning响应
- 对于选项C：使用历程测试模式验证决策节点是否正确选择

#### 验证展示跟踪

确认正在跟踪优惠展示次数、点击量和转化。

- 验证优惠交互事件是否显示在跟踪数据集中
- 确认优惠展示次数和下游转化之间的归因

#### Experience League文档

- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [发送电子邮件校样](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)

### 阶段7：配置报告和性能监控

**应用程序函数：** AJO：报表和性能分析

此阶段将设置报告以跟踪选件选择分布、接受率、转化影响和回退率。 此阶段涵盖AJO原生报表和基于CJA的跨渠道分析。

#### 决策：报告方法

确定优惠性能分析所需的报表工具。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅限AJO本机报表 | 对单个活动或历程的操作监控 | 快速访问；内置交付和参与量度；有限的跨实体分析 |
| CJA工作区分析 | 跨渠道选件有效性、收入归因、funnel分析 | 需要CJA连接和数据视图；更深入的分析功能 |
| AJO和CJA | 全面的业务和分析覆盖面 | 建议用于生产实施；AJO用于实时监控，CJA用于战略分析 |

#### 关键配置详细信息

1. **AJO本机报告** — 使用内置报告监控营销活动或旅程性能。
   - UI：营销活动>选择营销活动>所有时间报表（或实时报表）
   - 查看特定于选件的量度：每个选件的展示次数、每个选件的点进率、回退率
   - 监测投放funnel：目标>已发送>已投放>打开>点击量

2. **CJA analysis （推荐）** — 构建跨渠道优惠性能功能板。
   - 配置CJA连接，包括AJO选件交互数据集
   - 使用特定于优惠的维度（优惠名称、投放位置、决策）和量度（展示次数、点击次数、转化次数）创建数据视图
   - 构建工作区分析用于：选件选择分布、按区段列出的接受率、收入影响、跨渠道选件一致性

#### Experience League文档

- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

## 实施注意事项

本节介绍Offer Decisioning实施的护栏、常见隐患、最佳实践和权衡决策。

### 护栏和限制

在规划实施时，请注意以下平台护栏和限制。

- 每个沙盒最多10,000个批准的个性化优惠 — [决策管理护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每个决策最多30个投放位置
- 每个决策请求最多30个收集范围
- 人工智能排名模型需要至少1,000个转化事件才能进行训练
- 在高吞吐量情况下，选件上限计数器可能会有高达几秒钟的延迟
- Edge决策仅限于Edge Profile Store中可用的配置文件属性
- 每个沙盒最多4,000个区段定义 — [平台护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 每个沙盒只能有一个合并策略在Edge上处于活动状态
- 每个沙盒最多500个活动实时营销活动
- 历程进入率限制：每秒5,000个配置文件
- 每个沙盒每个渠道类型最多有10个渠道表面

### 常见陷阱

避免在实施过程中遇到这些常见问题。

- **决策始终返回后备优惠：**&#x200B;这通常意味着个性化优惠未获得批准，超出其有效日期范围，或者资格规则与测试用户档案的属性不匹配。 验证每个条件：审批状态、日期范围和区段规则表达式准确性。 另外，检查是否尚未达到上限限制。
- **选件未出现在集合中：**&#x200B;请确保选件已使用正确的集合限定符进行标记，并且集合筛选器匹配。 优惠必须同时经过标记和批准才能显示在基于收藏集的决策范围中。
- **未应用排名公式：**&#x200B;请验证公式语法有效并且引用了可访问的配置文件属性。 公式错误以静默方式回退到基于优先级的排名，并且没有可见错误。
- **Edge投放返回空的个性化设置：**&#x200B;请确保数据流配置为启用[!DNL Adobe Journey Optimizer]服务并且决策范围的格式正确。 验证边缘活动合并策略是否存在。
- **跨渠道的优惠不一致：**&#x200B;如果每个渠道使用不同的决策策略，则同一配置文件可能会接收不同的优惠。 使用跨渠道的单个决策策略以实现一致性，或根据特定于渠道的投放位置接受有意的分歧。
- **选件内容未在电子邮件中呈现：**&#x200B;请验证选件的内容呈现是否符合电子邮件版面格式（HTML或图像URL）。 缺少表示会导致放置区域为空。

### 最佳实践

请遵循以下建议以成功实施Offer Decisioning。

- **从小优惠目录开始并迭代** — 从5-10个优惠开始，并在决策框架验证后展开。 这简化了故障诊断，并确保资格规则在缩放之前正常工作。
- **策略性地使用收藏集限定符** — 按类别标记优惠（例如，“客户获取”、“保留”、“追加销售”），以实现可跨营销活动和历程重复使用的基于收藏集的灵活决策范围。
- **始终创建有意义的备用选件** — 备用选件不仅仅是一个安全网；对于不符合任何资格规则的用户档案，它们也是默认体验。 投资提供价值的后备内容（即使没有个性化）。
- **尽可能设计相互排斥的资格规则** — 当多个选件具有重叠的资格时，排名策略变得至关重要。 如果业务要求为特定区段指定特定选件，请使资格规则相互排斥，而不是仅依赖排名。
- **使用选项B**&#x200B;的边缘代表配置文件进行测试 — Edge配置文件包含中心配置文件属性的子集。 使用具有Edge-available属性的用户档案进行测试，以确保资格在生产环境中正确评估。
- **将回退率监测为运行状况量度** — 回退率较高（高于20-30%）表示优惠目录未涵盖足够的客户区段。 展开优惠目录或扩大资格规则。
- **版本决策策略而不是编辑实时决策策略** — 创建新的决策策略版本，而不是修改活动决策策略版本。 这样可防止实时营销活动受到干扰，并可对决策策略进行A/B比较。

### 权衡决定

在制定体系结构和配置决策时，请考虑以下取舍。

#### 资格精确度与优惠范围

严格的资格规则可确保每个选件仅访问最相关的用户档案，但在用户档案与任何选件不匹配时，可能会导致较高的回退率。 广泛的资格规则可最大化选件覆盖范围，但降低个性化准确性。

- **资格限制优惠：**&#x200B;更高的接受率、更好的个性化、更低的选件疲劳度
- **广泛的资格优惠：**&#x200B;降低后备率，更多配置文件接收个性化优惠，简化规则管理
- **建议：**&#x200B;从更广泛的资格规则开始，并根据绩效数据收紧这些规则。 监控回退率和接受率以找到适当的平衡。 使用排名策略区分广泛合格的优惠。

#### 基于优先级的排名与人工智能排名比较

基于优先级的排名让企业能够完全控制显示哪些选件，而人工智能排名的排名可优化转化，但减少人为控制选件选择。

- **基于优先级的优惠：**&#x200B;业务控制、可预测性、无培训数据要求、立即部署
- **AI排名优惠：**&#x200B;转化优化、发现意外模式、自动适应不断变化的客户行为
- **推荐：**&#x200B;对于以业务控制为重心的初始启动和监管敏感型优惠，使用基于优先级的排名。 一旦有足够的转化数据（1,000多个事件）可用，即可过渡到AI排名，以实现大容量、性能优化用例。

#### 单个决策策略与每渠道决策策略

单个决策策略可确保跨所有渠道提供一致性，但会限制每渠道优化。 每个渠道策略允许特定于渠道的排名和资格，但可能会带来客户体验不一致的风险。

- **单个策略优势：**&#x200B;跨渠道一致性、更简单的管理、统一的报告
- **每个渠道策略支持：**&#x200B;渠道优化排名、特定于渠道的资格（例如，仅限Web的优惠）、独立迭代
- **推荐：**&#x200B;从单个决策策略开始，以实现跨渠道一致性。 仅当业务需求需要特定于渠道的优惠策略（例如，Web独占的闪存Flash销售）时，才创建每渠道策略。

#### 中心决策（选项A/C）与边缘决策（选项B）

中心决策有权访问完整的配置文件，但在发送时运行。 Edge Decisioning会实时运行，延迟时间不到一秒，但仅限于边缘可用的用户档案属性。

- **中心决策支持：**&#x200B;访问完整的配置文件数据、复杂的资格规则、批量活动卷
- **Edge决策支持：**&#x200B;实时上下文、会话内个性化、每秒响应
- **建议：**&#x200B;对完整配置文件数据可提高选件相关性的出站渠道（电子邮件、推送）使用中心决策。 对实时响应至关重要的入站渠道（Web、应用程序）使用边缘决策。 确保Edge的资格规则仅使用Edge可用的属性。

## 相关文档

以下资源提供了有关此用例模式中使用的组件的其他详细信息。

### 决策管理

- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [创建投放位置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [创建决策规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [创建个性化优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [创建后备产品建议](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [创建集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [创建集合限定符](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [创建决策](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 选件交付

- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [使用Edge Decisioning API提供优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [使用Decisioning API提供优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/decisioning-api)

### 渠道配置

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [电子邮件表面设置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### 消息创作和个性化

- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 营销活动和历程

- [开始使用营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [历程入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### 内容试验

- [内容体验入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### 受众和分段

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### 个人资料和身份

- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Customer AI概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### 数据建模和收集

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

### 报告和分析

- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### 数据治理和生命周期

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### 护栏

- [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### 教程

- [决策管理API快速入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/getting-started)
