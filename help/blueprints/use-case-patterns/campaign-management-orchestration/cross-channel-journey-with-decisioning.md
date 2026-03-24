---
title: 使用Decisioning进行跨渠道历程
description: 了解如何结合实时决策来编排多步历程以选择最佳渠道、内容或选件。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: eabdd91f-bb7d-4de3-adb5-5940d3ca4a78
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '9029'
ht-degree: 2%

---

# 使用决策的跨渠道历程

本指南提供了包含决策的跨渠道历程的完整实施参考。 它专为需要编排多步骤、多渠道历程（在一个或多个历程节点纳入实时决策）的解决方案架构师、营销技术人员和实施工程师而设计。

使用本指南可了解实施选择的整体情况、评估利弊并导航到相关的Experience League文档以了解详细的配置说明。

具有决策的跨渠道历程是[!DNL Adobe Experience Platform]生态系统中最复杂的活动编排模式。 通过结合实时决策（使用[!DNL AJO]决策评估用户档案的当前上下文，并在历程画布内的一个或多个决策点动态选择最佳渠道、内容或选件），该功能扩展了多步骤编排的历程。

## 用例概述

组织越来越需要提供自适应、个性化的客户历程，这些历程会动态响应每个人的实时上下文，而不是遵循固定的预定顺序。 客户的首选渠道、参与历史记录、忠诚度级别、预测的存留期值以及当前产品兴趣都将在每个接触点制定下一个最佳操作。

包含决策的跨渠道历程通过结合两个强大的[!DNL AJO]功能来满足此需求：历程编排（管理多步骤流程、计时、条件和渠道交付）和决策（评估资格规则、应用排名策略并在每个决策点选择最佳优惠或内容变体）。

此模式适用于以下情况：

- 历程必须动态适应每个用户档案的实时状态，而不是遵循固定渠道或内容序列
- 多个选件、内容变体或渠道是一个或多个历程节点的候选项目，应根据配置文件上下文选择最佳选项
- 需要人工智能辅助或基于公式的排名，以优化历程中的选件选择
- 公司希望将渠道选择逻辑和选件管理整合到一个集中的决策框架中，而不是维护复杂的分支逻辑

目标受众包括营销人员，他们管理生命周期计划、忠诚度历程、回馈序列和入门流程，在这些流程中，大规模个性化需要在每个接触点进行自动决策。

>[!NOTE]
>如果您的历程不需要在单个节点进行动态决策，例如，固定序列培养或入门计划，请参阅[多步编排历程](multi-step-orchestrated-journey.md)。 该模式可更轻松地配置，并且不需要AJO Decisioning。

## 主要业务目标

此用例模式支持以下业务目标。

**[提供个性化的客户体验](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
根据个人偏好、行为和生命周期阶段定制内容、选件和消息。
**KPI：**&#x200B;参与度、转化率、客户满意度(CSAT)

**[提高客户忠诚度和存留期值](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
通过忠诚度计划、奖励和个性化参与，深化客户关系并最大化长期价值。
**KPI：**&#x200B;客户存留期值，保留，追加销售/交叉销售%

**[提高客户保留率](../../business-objectives/customer-experience/improve-customer-retention.md)**
透过价值导向型经验及持续培养关系，让现有客户持续参与及不断更新。
**KPI：**&#x200B;维系、客户存留期值、参与度

**[推动交叉销售和追加销售收入](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
根据行为和购买历史，向现有客户推广补充性和优质产品或服务。
**KPI：**&#x200B;追加销售/交叉销售%，增量收入，客户存留期值

## 战术用例示例

以下场景说明了如何将具有决策的跨渠道历程应用于实践。

- **自适应回送历程** — 多步骤历程，决策根据每个用户档案的参与历史记录选择渠道（电子邮件、推送或短信），并根据预测的生命周期值动态选择最佳激励优惠
- **下一个最佳行动生命周期历程** — 决策功能决定了在客户生命周期的每个阶段传达什么内容，可从入门内容、交叉销售优惠、忠诚度奖励或维系奖励中进行选择
- **通过动态内容选择进行个性化入门** — 新的客户入门历程，其中每个接触点都使用决策功能选择最相关的产品教育内容、提示或激活优惠
- **具有个性化奖励的跨渠道忠诚度计划历程** — 忠诚度会员在决策功能根据层级、购买历史记录和类别亲和度选择个性化奖励优惠的历程中前进
- **动态重新参与渠道和激励优化** — 休眠客户重新参与，其中动态选择外联渠道和激励以最大化响应概率
- **包含人工智能排名内容推荐的客户生命周期培养** — 人工智能排名决策在每个接触点选择最相关的内容或产品推荐的持续培养历程

## 关键绩效指标

使用以下KPI衡量此用例模式的有效性。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 历程完成率 | 完成完整历程的用户档案的百分比 | 历程报表：已完成/已输入 |
| 优惠接受率 | 参与（已点击、已兑换）的决策选定优惠的百分比 | 决策报告：优惠点击次数/优惠展示次数 |
| 渠道参与率 | 历程中使用的每个渠道的打开率和点击率 | 历程报告中的每渠道投放量度 |
| 转化率 | 完成目标转化操作的历程参与者的百分比 | 历程退出事件跟踪或CJA funnel analysis |
| 后备优惠率 | 返回后备优惠而不是个性化优惠的决策请求百分比 | 决策报告：回退选择/选择总数 |
| 客户存留期值影响 | 历程参与者与对照组的CLV更改 | CJA同类群组分析以及保持型比较 |
| 交叉销售/追加销售收入 | 归因于决策所选优惠的增量收入 | 对优惠驱动型转化的CJA归因分析 |
| 决策排名效果 | AI排名选件与随机/基于优先级的选择之间的性能差异 | A/B比较排名策略的实验 |

## 用例模式

**具有决策的跨渠道历程**

编排多步骤、多渠道历程，该历程在一个或多个节点结合了实时决策以选择最佳渠道、内容或选件。

**功能链：**&#x200B;受众评估>历程执行>决策节点>渠道选择>消息投放>报表

## 应用程序

以下应用程序用于实现此用例模式。

- **[!DNL Adobe Journey Optimizer]([!DNL AJO])** —历程编排（多步骤画布设计、进入条件、等待、条件、退出条件）、跨渠道消息创作、渠道表面配置、冲突和优先级管理
- **[!DNL Adobe Journey Optimizer]决策** — 优惠和内容项目管理、资格规则、排名策略（优先级、公式、AI）、决策策略、投放、后备优惠
- **[!DNL Adobe Real-Time Customer Data Platform]([!DNL RT-CDP])** — 历程进入和优惠资格区段的受众评估，具有计算属性和倾向分数的配置文件扩充，同意和治理实施
- **[!DNL Adobe Experience Platform]([!DNL AEP])** — 实时客户配置文件存储、跨渠道解析身份服务、数据建模和引入基础结构

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本函数 | 状态 | 必须准备好的内容 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 假设就位 | 配置了历程、营销活动和决策权限的[!DNL AJO]沙盒。 所有可能的投放渠道的渠道平面。 历程设计者、决策管理者和内容作者的用户角色。 | [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)，[访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | 配置文件架构必须包括用于决策的属性（例如，忠诚度级别、购买历史记录、渠道偏好设置、参与度分数）。 必须配置优惠目录和决策项架构。 ExperienceEvent架构必须捕获资格规则和排名公式使用的行为信号。 | [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| 数据源和收集 | 假设就位 | 决策使用的配置文件属性和行为信号必须是最新的。 如果历程使用事件触发的进入或退出标准，则需要实时事件流。 Web SDK、Mobile SDK或服务器端收藏集必须对于提供决策上下文的渠道处于活动状态。 | [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)，[源概述](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| 身份和配置文件配置 | 必填 | 跨渠道身份解析至关重要 — 历程必须跨电子邮件、推送、短信和Web解析用户档案。 合并策略必须生成用于决策的统一配置文件。 必须配置所有客户标识符（CRM ID、电子邮件、ECID、电话）的标识命名空间。 | [身份服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| 受众定义和分段 | 必填 | 历程的登录受众定义。 历程中用于优惠资格规则和条件分支的其他区段。 评估方法必须符合延迟要求（实时条目流式传输，计划批量传输）。 | [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么它很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | 计算属性（如客户人工智能倾向分数、参与度分数、渠道偏好分数和生命周期值计算）显着提高了决策质量。 这些丰富的用户档案属性支持更复杂的资格规则和排名公式。 | [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)，[客户人工智能概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| 数据生命周期管理 | 推荐 | 优惠历史记录和决策事件数据会随时间累积，因此应该具有保留策略。 跨多个渠道的同意强制执行至关重要 — 必须从渠道的投放路径中排除未经渠道有效同意的用户档案。 | [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)，[Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| 数据使用标签和执行 | 推荐 | 当决策可能将用户档案路由到具有不同数据使用限制的不同渠道时，跨多个渠道和选件类型实施治理很重要。 确保跨所有渠道的合规性选件交付。 | [数据管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)，[策略实施](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview) |
| 监视和可观察性 | 已包含 | 历程和决策监控对于生产运行至关重要。 历程进入失败、决策回退尖峰和投放错误警报可帮助快速解决问题。 | [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)，[可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 报告和分析 | 已包含 | 历程和决策报告在报告阶段涵盖。 CJA对决策有效性、渠道组合优化、优惠性能和旅程ROI的分析提供了完善排名策略并随时间优化旅程所需的见解。 | [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)，[AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## 应用程序功能

此计划从应用程序功能目录中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Journey Optimizer] ([!DNL AJO])

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 渠道配置 | 阶段2：通道配置 | 为决策可能选择或历程使用的所有渠道（电子邮件、短信、推送、应用程序内）配置渠道平面 |
| 消息创作 | 阶段4：消息创作 | 为每个渠道创作消息内容并集成决策输出 — 优惠投放位置、动态内容块、选定优惠中的个性化令牌 |
| Decisioning | 阶段3：决策设置 | 为历程中的每个决策点配置优惠项目、资格规则、排名策略、决策策略和后备优惠 |
| Journey Orchestration | 阶段5：历程设计和激活 | 设计包含进入条件、决策节点、渠道路由、等待步骤、消息操作和退出标准的多步历程画布 |
| 冲突和优先级管理 | 阶段5：历程设计和激活 | 配置优先级得分和冲突检测（如果多个历程可能同时定位同一用户档案） |
| 频度和业务规则 | 阶段5：历程设计和激活 | 跨渠道实施消息频率限制以防止多渠道历程中过度发送消息 |
| 报告和性能分析 | 第6阶段：报告和监控 | 监控历程和每节点交付量度、决策性能和渠道参与 |

### [!DNL Real-Time CDP] ([!DNL RT-CDP])

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 受众评估 | 第1阶段：受众评估 | 定义和评估进入受众或合格进入事件；创建决策使用的资格区段 |
| 轮廓扩充 | 先决条件/支持 | 使用计算的属性和倾向分数丰富用户档案，从而提高决策质量 |
| 同意和治理实施 | 阶段2：通道配置 | 在所有渠道中强制实施同意首选项；确保合规的选件交付 |

## 先决条件

请在开始实施之前完成以下操作。

- [ ] [!DNL AJO]沙盒已配置journey orchestration和决策功能
- [ ]所有目标渠道（电子邮件、短信、推送）都具有已验证的活动渠道表面
- [ ]配置文件架构包括决策所需的属性（忠诚度级别、购买历史记录、渠道偏好设置、参与度分数）
- [ ]已配置跨渠道身份解析 — 配置文件可以跨电子邮件、推送令牌、电话号码和Web标识符进行解析
- [ ]已定义登录受众并使用非零填充进行评估
- [ ]优惠目录内容（创意资产、副本、法律免责声明）已获得批准并可供配置
- [ 正在摄取]同意数据，并且所有目标渠道的同意强制活动处于活动状态
- [ 已设计和批准每个渠道的]内容模板和片段
- [ 如果组织具有跨营销活动频率策略，则定义和部署]频率上限规则
- [ ]如果使用人工智能排名决策，则至少存在1,000个转化事件进行模型训练

## 实施选项

查看以下选项并选择最适合您要求的方法。

### 选项A：使用Offer Decisioning进行历程（固定渠道、动态内容）

**最适合：**&#x200B;渠道顺序已预先确定，但应动态选择每个接触点上的内容或优惠的历程 — 提供个性化奖励的忠诚度历程、重新参与动态激励、提供人工智能排名内容推荐的生命周期培养。

#### 工作原理

历程画布定义渠道和时间的固定序列（例如，第0天：电子邮件，第3天：推送，第7天：短信）。 在每个消息操作节点处，决策策略从合格项目的配置目录中选择要包括在消息中的最佳优惠或内容。 优惠在[!DNL AJO]决策目录中管理，其资格规则用于筛选哪些优惠符合资格的个人资料，排名策略用于确定哪个资格优惠最适合。

这种方法将“时间和地点”（历程编排）与“内容”（决策）分隔开来。 历程设计器控制渠道流，而决策管理器独立控制优惠目录、资格规则和排名逻辑。 这种关注点分离使实施更具可维护性，并允许选件目录演进而不修改历程画布。

使用电子邮件Designer或其他渠道编辑器，将优惠投放位置直接嵌入到消息内容中。 在投放时呈现消息时，决策引擎会评估用户档案的资格和排名，以便为消息中的每个投放位置选择最佳选件。

#### 关键注意事项

- 渠道序列是静态的 — 所有用户档案都遵循相同的渠道路径，无论其偏好如何
- 决策复杂性较低，因为它只选择内容/选件，而不选择渠道
- 优惠目录可以独立于历程进行管理
- 必须为每个投放位置配置后备优惠，以处理没有合格个性化优惠的用户档案

#### 优点

- 更简单的历程画布 — 没有用于渠道选择的分支逻辑
- 历程设计和选件管理之间关注点的明确分离
- 更容易测试和验证 — 每个渠道路径都是确定性的
- 降低实施复杂性和加快上市时间
- 优惠目录更改会立即生效，无需修改历程

#### 限制

- 无法根据个人用户档案行为或偏好设置调整渠道
- 优选一个信道而不是另一个信道的用户档案仍然在预定信道上接收消息
- 没有针对渠道级别的参与率进行优化

#### Experience League引用

- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)

### 选项B：通过动态渠道选择（固定历程、动态渠道）进行内容

**最适合于：**&#x200B;历程，其中每个接触点的内容都相似，但应根据用户档案上下文动态选择渠道 — 自适应回馈（电子邮件与推送对比，基于参与度的短信），以及以渠道优化为主要目标的次优行动方案。

#### 工作原理

历程使用由用户档案属性（例如渠道偏好分数、上次参与渠道或同意状态）或决策输出通知的条件节点将用户档案路由到不同的渠道路径。 每个路径都通过自己的消息操作节点提供特定于渠道的内容。 决策逻辑根据用户档案的行为历史记录确定最有可能引发参与的渠道。

可以使用历程条件节点通过配置文件属性评估（例如，如果`channelPreference = "push"`路由到推送路径）来实施渠道选择，也可以使用包含特定于渠道的项目的决策来实施渠道选择，其中每个“优惠”代表一个渠道，排名策略确定最佳渠道。

此方法优化了投放渠道，同时使内容在各渠道之间保持相对一致。 它要求为每个可能的渠道创作消息内容，必须为所有候选渠道配置渠道平面。

#### 关键注意事项

- 要求每个候选渠道具有消息内容变体
- 对于所有可能的渠道，渠道表面必须处于活动状态
- 条件逻辑或决策配置必须考虑是否同意 — 未经短信同意的用户档案无法路由到短信路径
- 历程画布更为复杂，每个渠道都有分支路径

#### 优点

- 优化每个个人资料的渠道选择
- 通过在用户档案的首选渠道上访问用户档案，提高整体参与度
- 通过同意感知路由自动尊重特定于渠道的同意
- 可以将参与历史记录和渠道偏好得分纳入路由决策

#### 限制

- 具有多个渠道分支的更复杂的历程画布
- 必须为每个渠道单独创作内容（尽管消息意图相同）
- 更难以测试 — 必须验证所有可能的通道路径
- 每个渠道中的内容个性化都是静态的（无Offer Decisioning）

#### Experience League引用

- [条件活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [创建旅程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### 选项C：完全自适应历程（动态渠道+动态内容）

**最适合：**&#x200B;最大个性化 — 在每个节点动态选择渠道和内容/选件。 适用于高价值客户群体、复杂的忠诚度计划以及具有成熟决策实践和丰富用户档案数据的组织。

#### 工作原理

此选项将选项A和B组合在一起。历程在两个级别使用决策：第一，确定每个接触点使用的渠道；第二，确定在选定渠道中交付的内容或选件。 历程中的每个决策点都会评估用户档案的当前上下文，以进行渠道和内容选择。

该实施需要全面的决策设置，以及渠道选择和内容/选件选择的决策策略。 渠道选择可以使用决策策略，其中每个项目代表具有基于同意和参与的合格规则的渠道，而内容选择使用具有按相关性排序的优惠项目的单独决策策略。

这是最复杂的变体，需要在Journey Orchestration和Decisioning之间实现最深入的集成。 它提供了最高级别的个性化，但也要求最全面的配置、测试和持续管理。

#### 关键注意事项

- 需要两个决策层 — 渠道选择和内容选择
- 每个节点的嵌套分支和决策功能会导致历程画布复杂度最高
- 需要对所有可能的渠道 — 内容组合进行广泛的测试
- 需要丰富的配置文件数据（参与历史记录、渠道偏好设置、产品亲和度、倾向分数）以便进行有效决策
- AI排名的决策功能从计算属性中获得显着优势

#### 优点

- 最大程度的个性化 — 每个接触点都针对渠道和内容进行了优化
- 针对配置良好的实施的最佳参与和转化潜力
- 集中了决策中的所有个性化逻辑，而不是静态历程分支
- 可以通过AI排名模型学习持续改进

#### 限制

- 最高的实施复杂性和最长的上市时间
- 需要最广泛的选件目录和渠道内容准备
- 出现投放问题时更难进行故障排除
- 需要具有丰富配置文件属性的成熟数据基础架构
- 人工智能排名需要足够的转化事件量来进行模型训练

#### Experience League引用

- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 选项比较

使用下表大致比较三个实施选项。

| 标准 | 选项A：Offer decisioning | 选项B：动态渠道 | 选项C：完全自适应 |
| --- | --- | --- | --- |
| 最适合 | 固定渠道序列、动态内容 | 渠道优化，内容一致 | 两个维度中的最大个性化值 |
| 复杂性 | 中 | Medium — 高 | 高 |
| 历程画布 | 简单（与操作节点上的决策保持线性） | 审核（渠道路径的分支） | 复杂（具有多级决策的嵌套分支） |
| 决策范围 | 仅限内容/选件选择 | 仅限渠道选择 | 渠道和内容选择 |
| 内容要求 | 每个渠道一个内容集（包含优惠投放） | 每个候选渠道的内容 | 包含每个候选渠道的选件投放位置的内容 |
| 配置文件数据需求 | 审核（优惠资格属性） | 审核（渠道偏好设置、参与度） | 高（渠道和优惠属性） |
| 上市时间 | 更快 | 审核 | 最长 |
| 持续管理 | 优惠目录管理 | 通道路由逻辑管理 | 优惠目录和渠道路由 |
| Personalization深度 | 内容各异，渠道固定 | 渠道各不相同，内容类似 | 渠道和内容都有所不同 |

### 选择正确的选项

请遵循以下指南来确定适合您情况的最佳选择。

- **如果您的渠道策略已定义（例如，“我们始终先发送电子邮件，然后推送，再发送短信”），并且主要的个性化需求是在每个接触点选择正确的优惠或内容，则从选项A**&#x200B;开始。 这是刚开始使用决策功能的组织最常见的起点。

- **如果渠道优化是您的主要目标，请选择选项B** — 您希望联系最有可能接触的渠道上的每个客户，但各渠道的消息内容相对一致。 这需要用户档案上的渠道偏好设置数据。

- **只有在您拥有成熟的决策基础结构、丰富的配置文件数据（包括计算的属性和倾向分数）、填充良好的优惠目录以及管理复杂性的组织能力时，才能选择选项C**。 许多组织从选项A或B开始，随着决策成熟度的提高，逐渐演变为选项C。

- **如果您不确定**，则从选项A开始。它以最低的复杂性提供了有意义的个性化，如果您以后发展为选项C，则您为选项A构建的选件目录可以直接重用。

## 实施阶段

以下阶段将逐步介绍此用例模式的端到端实施。

### 第1阶段：受众评估

**应用程序函数：** [!DNL RT-CDP]：受众评估

此阶段配置登录受众，以确定哪些配置文件进入历程，以及用于历程中的优惠资格规则或条件分支的任何其他区段。 受众定义是所有下游历程和决策逻辑的基础。

#### 决策：条目类型

用户档案应如何进入历程 — 通过计划的受众读取或实时事件触发器？

>[!NOTE]
>根据历程的时间和触发要求，选择一个登入类型。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 读取受众（批量条目） | 生命周期计划、忠诚度历程、计划的重新参与活动 | 配置文件在计划时间批量输入；在读取时评估受众；支持较大的受众大小 |
| 受众资格（流） | 行为触发的历程，当用户档案进入或退出区段时会发生进入 | 近乎实时的录入；需要符合流式处理条件的区段定义；适用于基于里程碑的历程 |
| 单一事件（事件触发器） | 特定事件应触发历程（例如，购买、购物车放弃、注册） | 事件的实时条目；需要事件架构配置；限制为每秒5,000个事件 |

#### 决策：受众评估方法

受众必须多久才能使配置文件符合条件？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 批次 | 每日或定期受众更新便已足够；计划的营销活动式历程 | 每个作业最多可处理2400万个配置文件；基于计划；支持大多数区段规则表达式 |
| 流 | 对于事件触发的或基于资格的条目，需要实时受众会员资格 | 近乎实时；区段规则函数集有限；无基于时间的聚合 |
| Edge | 需要同一会话资格 | 毫秒延迟；仅限简单属性检查；仅限于Edge配置文件属性 |

#### 关键配置详细信息

**UI导航：**&#x200B;客户>受众>创建受众>生成规则

- 使用区段生成器定义登录受众，区段规则表达式将定位相关的配置文件属性和行为事件
- 如果优惠资格规则将引用区段会员资格（例如，“高价值客户”、“忠诚度黄金层”），则创建其他资格区段
- 在继续历程配置之前，验证受众填充是否非零
- 选择生成决策所需的统一配置文件视图的合并策略

#### Experience League文档

- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Profile Query Language参考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 阶段2：通道配置

**应用程序函数：** [!DNL AJO]：通道配置

此阶段为历程可能用于消息投放的每个渠道配置渠道平面。 在创作消息或发布历程之前，所有候选渠道都必须具有已验证的活动表面。 对于此模式，您通常会至少为电子邮件、短信和推送配置界面 — 如果决策可能选择这些渠道，则可能为应用程序内或Web配置。

#### 决策：要配置哪些渠道

哪些渠道是历程的候选渠道 — 作为固定历程步骤（选项A/B）或作为决策可选渠道（选项B/C）？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅电子邮件 | 带有Offer Decisioning的单渠道历程（选项A，仅限电子邮件） | 配置最简单；需要子域委派和IP热身 |
| 电子邮件+推送 | 双渠道历程；常见于以参与为中心的历程 | 推送需要使用APN/FCM凭据；移动设备应用程序必须集成SDK |
| 电子邮件+短信+推送 | 完整的跨渠道历程；最常见于选项B和C | SMS需要提供者凭据(Sinch、Twilio、Infobip)；每个渠道需要自己的界面 |
| 电子邮件+短信+推送+应用程序内 | 包括会话内表面的最大渠道覆盖率 | 应用程序内需要配置Mobile SDK和应用程序表面 |

#### 决策：子域委派方法（电子邮件）

如何将发送子域委派给Adobe？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 完全委派 | 组织希望Adobe管理发送子域的所有DNS记录 | 设置最简单；Adobe处理SPF、DKIM、DMARC；减少对DNS的控制 |
| CNAME委派 | 组织需要保持对DNS记录的控制 | 更复杂的设置；客户管理DNS；提供更大的灵活性 |

#### 关键配置详细信息

**UI导航：**&#x200B;管理>渠道>渠道界面>创建界面

- 对于电子邮件：配置子域、IP池、发件人姓名、回复地址和取消订阅处理
- 对于短信：配置短信提供商凭据和发件人号码
- 对于推送：为iOS和Android配置APN和FCM凭据
- 在继续之前，验证每个曲面是否处于活动状态
- 确认电子邮件发送IP的IP预热已完成

#### Experience League文档

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [创建 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 阶段3：决策设置

**应用程序功能：** [!DNL AJO]： Decisioning

此阶段配置完整的决策框架，包括投放位置、资格规则、个性化优惠、后备优惠、收藏集限定词、收藏集、排名策略和决策策略。 此阶段创建将在历程决策点调用的决策逻辑。

#### 决策：决策范围

决策应该选择什么 — 选件/内容（选项A）、渠道（选项B）或两者（选项C）？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅限选件/内容选择 | 渠道顺序是固定的；内容中包含个性化 | 决策策略以每个投放位置具有内容表示的优惠项目为目标 |
| 仅限渠道选择 | 内容一致；优化在投放渠道上进行 | 决策项目代表渠道；资格包括同意检查；排名使用参与数据 |
| 渠道和内容 | 跨渠道和内容的完全自适应个性化 | 需要两层的决策策略；最复杂但最个性化 |

#### 决策：排名策略

如何对符合条件的优惠进行排名以选择最佳优惠？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 基于优先级（手动） | 业务规则决定选件重要性的简单排名 | 每个选件都有一个优先级分数；最高优先级入选；确定性且易于理解 |
| 基于公式（自定义表达式） | 排名应考虑到配置文件属性（例如，CLV、层、亲和度分数） | 自定义排名公式计算配置文件上下文；比优先级更动态；不需要ML |
| AI排名（自动优化） | 应根据历史转化数据自动优化排名 | AI模型从转化事件中学习；需要至少1,000个事件进行训练；不断改进 |

#### 决策：优惠上限

选件显示的次数是否应有限制？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 每个配置文件上限 | 防止将同一选件重复显示在同一配置文件中 | 防止选件疲劳；在高吞吐量下可能会出现计数器滞后 |
| 全局上限 | 限制所有用户档案的总展示次数（例如，有限的库存促销） | 控制总风险；对于限量供应非常有用 |
| 无上限 | 每个符合条件的展示都应显示选件 | 最简单；适用于历久不衰的内容或无限优惠 |

#### 关键配置详细信息

**UI导航：**&#x200B;组件>决策管理>版面/优惠/决策

- 为每个渠道和内容类型组合创建投放位置（例如，电子邮件HTML横幅、推送JSON、短信文本）
- 使用引用用户档案属性或受众成员资格的区段规则表达式定义资格规则
- 创建包含每个投放位置的表示的个性化优惠、分配资格规则和设置优先级
- 创建涵盖所有投放位置的后备优惠 — 当没有个性化优惠符合条件时返回
- 使用收藏集限定符（标记）将优惠组织到收藏集中
- 配置排名策略 — 基于优先级、基于公式或人工智能排名
- 创建绑定投放位置、收藏集、排名策略和后备优惠的决策策略
- 先批准所有优惠，然后才能通过决策选择它们

#### 不同选项的位置

选项A (Offer Decisioning)的&#x200B;**：**
创建侧重于每个渠道中内容个性化的投放位置和选件（例如，电子邮件主页横幅选件、电子邮件页脚选件、推送通知正文选件）。 决策策略为消息中的每个版面选择最佳内容。

选项B （动态渠道选择）的&#x200B;**：**
创建代表每个渠道的决策项。 资格规则包括同意检查（例如，用户档案必须具有短信同意才能符合短信项目的资格）。 排名使用渠道参与度得分或基于公式的表达式。

选项C （完全自适应）的&#x200B;**：**
配置两个决策层：一组用于渠道选择的决策策略，另一组用于所选渠道中的内容/选件选择。 这两个层都需要投放位置、选件、资格规则和排名策略。

#### Experience League文档

- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [创建投放位置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [创建决策规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [创建个性化优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [创建后备产品建议](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [创建集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [创建决策](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 阶段4：消息创作

**应用程序函数：** [!DNL AJO]：消息创作

此阶段为历程中的每个渠道和接触点配置消息内容，并将决策输出（选定的优惠内容）集成到消息模板中。 历程中的每个消息操作节点都需要具有相应渠道界面、个性化令牌和选件版面集成的创作内容。

#### 决策：内容方法

应如何为每个渠道创建消息内容？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 基于模板 | 组织已建立品牌模板；一致性很重要 | 更快的创作；确保品牌一致性；可能会限制设计的灵活性 |
| 从头开始设计 | 此历程的唯一创意；无现有模板 | 完整的设计控制；创作时间较长；使用电子邮件Designer拖放 |
| 导入HTML | Creative团队在外部生产HTML；导入到[!DNL AJO] | 保留外部设计工作流；需要HTML与Email Designer兼容 |

#### 决定：Personalization范围

除决策输出之外，消息应包含什么级别的个性化？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 基本个性化（姓名、问候语） | 除了选件选择之外的最低个性化需求 | 简单Handlebars表达式；复杂性低 |
| 条件内容块 | 不同区段或属性的不同内容部分 | 使用动态内容规则；内容因配置文件属性或区段成员资格而异 |
| 通过Decisioning集成实现完全个性化 | 消息中嵌入的选件投放位置，与基于用户档案的个性化相结合 | 将Offer Decisioning输出与Handlebars个性化令牌整合在一起；体验最丰富 |

#### 关键配置详细信息

**UI导航：**&#x200B;选择营销活动或历程操作>编辑内容>向Designer/渠道编辑器发送电子邮件

- 为历程中使用的每个渠道（电子邮件、短信、推送、应用程序内）创作消息内容
- 将优惠决策投放位置嵌入到消息内容中，决策选定优惠应在此处显示
- 使用配置文件属性的Handlebars语法添加个性化表达式（例如，`{{profile.person.name.firstName}}`）
- 为特定于区段的消息传递配置条件内容块
- 为共享元素（页眉、页脚、法律免责声明）创建可重复使用的内容片段
- 使用示例配置文件预览和测试，以验证个性化呈现是否正确
- 发送验证消息以供利益相关者审核

#### 不同选项的位置

选项A (Offer Decisioning)的&#x200B;**：**
每条消息都包含优惠投放位置，其中显示了决策选择的内容。 消息布局一致，但选件区域会动态显示每个用户档案的最佳选件。

选项B （动态渠道选择）的&#x200B;**：**
每个渠道都有单独创作的消息内容。 虽然各个渠道中的内容类似，但已调整为适应渠道限制（电子邮件HTML与短信文本与推送通知格式）。

选项C （完全自适应）的&#x200B;**：**
每个渠道都有其自己的消息内容，嵌入了选件投放位置。 该渠道中的渠道和选件内容都是动态选择的。

#### Experience League文档

- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [创建短信消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [设计推送通知](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### 阶段5：历程设计和激活

**应用程序函数：** [!DNL AJO]：Journey Orchestration，[!DNL AJO]：冲突和优先级管理，[!DNL AJO]：频率和业务规则

此阶段配置完整的历程画布，包括登入配置、链接到配置的决策策略的决策节点、渠道路由的条件拆分（选项B/C）、每个渠道路径的消息操作节点、接触点之间的等待节点、退出标准、冲突/优先级设置和频率上限规则。 此阶段会将之前配置的所有组件组合到编排的历程流中并激活该流程。

#### 决定：重新进入政策

用户档案在完成或退出后能否重新进入历程？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 允许重新进入（使用冷却） | 用户档案可能再次符合条件的定期历程（例如，季度忠诚度续订） | 设置冷却时段（至少5分钟）以防止立即重新进入；配置文件从头开始 |
| 禁止重新进入 | 每个用户档案应仅遍历一次的一次性历程（例如，载入） | 配置文件在完成或退出后无法重新进入；更简单的行为 |

#### 决策：退出条件

在完成之前，应在什么条件下从历程中删除用户档案？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 受众会员资格更改 | 当个人资料离开登录受众或进入禁止显示受众时，应该退出 | 区段更改时实时退出；对于“已转化”或“已退出”退出很有用 |
| 事件发生 | 特定事件（例如，购买、取消订阅）应触发退出 | 事件时实时退出；需要事件架构配置 |
| 超时 | 历程中经过的最长持续时间 | 默认最长为91天；防止配置文件无限期保留 |

#### 决策：历程超时

用户档案在历程中可以保留的最长时长是多少？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 91天（最长） | 具有扩展培养序列的长时间运行生命周期历程 | 允许的最长持续时间；配置文件在91天后退出，而不考虑 |
| 自定义较短的持续时间 | 有时限的营销活动或季节性历程 | 根据历程业务逻辑进行设置；较短的超时可减少陈旧的用户档案 |

#### 决策：冲突和优先级设置

此历程是否应优先评分以便与其他历程/营销活动解决冲突？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 高优先级(70-100) | 应优先处理的关键客户历程（维系、忠诚度） | 当多个通信竞争时，优先级别越高；请谨慎使用 |
| Medium优先级(30-69) | 标准生命周期历程 | 优先级均衡；可能被较高优先级的通信抑制 |
| 低优先级(0-29) | 补充或信息性历程 | 在与更重要的通信竞争时将被压制 |

#### 关键配置详细信息

**用户界面导航：**&#x200B;历程>创建历程

- 创建历程并配置属性（名称、描述、时区、超时）
- 配置条目：读取受众（用于批处理）或事件触发器（用于实时）
- 添加链接到阶段3中配置的决策策略的决策节点
- 根据决策输出或配置文件属性为渠道路由添加条件拆分（选项B/C）
- 为每个渠道路径添加消息操作节点，链接到阶段4中的创作内容
- 在接触点之间添加等待节点（对于受众读取历程，至少1小时）
- 定义退出标准（受众更改、事件、超时）
- 分配冲突解决的优先级分数
- 如果应用跨历程频率限制，则配置频率封顶
- 在发布之前使用测试用户档案在测试模式下测试历程
- 发布历程以使其上线

#### 不同选项的位置

选项A (Offer Decisioning)的&#x200B;**：**
历程画布与嵌入在每个消息操作节点中的决策策略是线性的。 渠道选择无分支。 优惠决策是在操作节点内的消息呈现时做出的。

选项B （动态渠道选择）的&#x200B;**：**
在每个等待步骤后，添加一个条件节点，以评估渠道选择标准（用户档案属性、决策输出或同意状态）。 每个条件分支都指向特定于渠道的消息操作节点。 为不符合任何条件的配置文件包含默认/其他路径。

选项C （完全自适应）的&#x200B;**：**
将渠道选择条件节点与嵌入决策策略的消息操作节点相结合。 在每个接触点：首先，条件或决策确定频道；然后，在所选频道的消息操作中，决策策略选择最佳优惠/内容。

#### Experience League文档

- [创建旅程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [历程属性](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [读取受众活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [条件活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在历程中添加消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [退出标准](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [历程条目管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [测试您的历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [发布历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [优先级分数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [冲突和优先级管理概述](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### 第6阶段：报告和监测

**应用程序函数：** [!DNL AJO]：报表和性能分析

此阶段通过实时报告（在执行期间）和历史报告（完成后）配置旅程和决策性能监控。 决策特定的量度，包括优惠选择分布、回退率和排名有效性。 （可选）CJA工作区分析，以实现深入的跨渠道历程和决策ROI分析。

#### 决策：报告深度

需要什么级别的报表分析？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅[!DNL AJO]个本机报告 | 交付和参与量度的运行监控 | 内置实时和历史报表；无其他配置；仅限于[!DNL AJO]个量度 |
| [!DNL AJO] + CJA分析 | 深入跨渠道分析、决策有效性、历程ROI、同类群组分析 | 需要CJA连接和数据视图；提供归因、funnel和同类群组分析功能 |

#### 关键配置详细信息

**用户界面导航：**&#x200B;历程>选择历程>实时报告/所有时间报告

- 在初始执行期间监控历程实时报告，以了解登入、退出和每节点的量度
- 审核决策性能：优惠选择分发、后备优惠率、排名有效性
- 历程完成后，查看历史报告以进行端到端的funnel分析
- 对于CJA分析：确保CJA连接包含[!DNL AJO]数据集（消息反馈事件、电子邮件跟踪事件）
- 通过用于渠道组合分析、选件性能比较和历程转化漏斗的面板构建CJA工作区
- 创建历程启动日期和重大配置更改的注释

#### Experience League文档

- [历程实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## 实施注意事项

在实施之前和期间查看以下护栏、常见隐患、最佳实践和权衡取舍决策。

### 护栏和限制

- 每个沙盒最多有500个实时历程 — [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 最长历程持续时间为91天（全局超时）
- 每个历程画布最多50个活动
- 读取受众历程每秒最多可处理20,000个配置文件
- 单一事件历程在每个沙盒中每秒最多支持5,000个事件
- 每个沙盒最多10,000个批准的个性化优惠
- 每个决策最多30个投放位置
- 选件交付响应时间SLA：对于单范围请求，在P95时小于500毫秒
- 人工智能排名模型需要至少1,000个转化事件才能进行训练
- 每个沙盒每个渠道类型最多有10个渠道表面
- 对于受众读取的历程，等待步骤最小持续时间为1小时
- 历程重新进入冷却时间最短为5分钟
- 每个沙盒最多4,000个区段定义 — [平台护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### 常见陷阱

**决策始终返回后备优惠：**&#x200B;验证个性化优惠在其有效日期范围内是否获得批准（不是处于草稿状态），以及资格规则是否与目标用户档案的属性相匹配。 检查是否尚未达到优惠上限限制。 使用应明确符合个性化优惠资格的用户档案进行测试。

**历程已发布，但用户档案未进入：**&#x200B;对于受众读取的历程，请确认受众的评估群体大于零。 对于事件触发的历程，请验证事件架构、触发条件以及是否发送了事件。 检查登录受众合并策略是否与历程的预期合并策略匹配。

**未正确应用排名公式：**&#x200B;请验证公式语法是否有效，并引用可访问的配置文件属性。 公式错误会在没有警告的情况下自动回退到基于优先级的排名。 使用具有不同属性值的用户档案的测试排名，以确认公式产生预期的顺序。

**渠道路由忽略同意：**&#x200B;渠道选择的条件节点必须包括同意检查。 未经短信同意的用户档案不得路由到短信路径。 使用决策进行渠道选择时，将同意构建到资格规则中（选项B/C）。

**高吞吐量下选件上限计数器滞后：**&#x200B;在高吞吐量情况下，选件上限计数器可能会有几秒钟的延迟。 如果确切的上限至关重要，请将全局上限与缓冲区或频率规则结合使用。

**历程画布超过50个活动的限制：**&#x200B;具有许多渠道分支和决策节点的复杂选项C旅程可能会接近50个活动的限制。 通过整合条件逻辑、减少接触点数量或拆分为多个顺序历程来简化。

**Edge决策返回空的个性化设置：**&#x200B;如果为实时决策使用边缘决策，请确保数据流启用了[!DNL Adobe Journey Optimizer]服务并且决策范围的格式正确。 Edge决策仅限于Edge Profile Store中可用的配置文件属性。

### 最佳实践

**从简单开始，不断改进：**&#x200B;从选项A（固定渠道、动态优惠）开始验证决策框架，然后随着数据成熟度和组织容量的增长，逐渐改进为选项B或C。

**投资于配置文件扩充：**&#x200B;参与度分数、渠道偏好指数和客户人工智能倾向分数等计算属性可显着改善决策质量。 在配置复杂的排名策略之前，构建这些扩充属性。

**始终配置后备优惠：**&#x200B;每个决策策略都必须有一个后备优惠。 将后备优惠设计为真正有用的内容（不是空占位符），因为它们提供的配置文件不符合任何个性化优惠的条件。

**使用不同的配置文件进行测试：**&#x200B;使用测试模式，测试模式中的配置文件代表不同的资格路径、渠道首选项和属性组合。 在发布之前，请验证每个可能的历程路径和决策结果是否正常工作。

**将回退率监测为运行状况量度：**&#x200B;回退优惠率较高表示资格规则过于严格，或者优惠目录未涵盖足够的配置文件区段。 对于配置良好的决策，设定回退率低于20%的目标。

**使用内容片段实现跨渠道一致性：**&#x200B;创建共享的内容片段（页眉、页脚、法律免责声明、取消订阅块）以维护历程中电子邮件、短信和推送消息之间的品牌一致性。

**主动配置退出条件：**&#x200B;定义转化事件的退出条件（例如，购买、注册），以便完成所需操作的用户档案立即从历程中删除，而不是继续接收消息。

**分配有意义的优先级得分：**&#x200B;在运行多个历程和营销活动时，根据业务影响分配优先级得分。 高价值维系历程的优先级应高于信息通信。

### 权衡决定

请查看以下权衡取舍以告知您的实施选择。

#### 决策复杂性与上市时间

更复杂的决策（具有人工智能排名的选项C）可提供更高的个性化，但需要更多的配置、数据准备和测试时间。

- **选项A/B支持：**&#x200B;部署速度更快，测试更简单，日常管理开销更低
- **选项C支持：**&#x200B;最大个性化、连续AI驱动优化、最高参与潜力
- **建议：**&#x200B;对于初始启动，以选项A或B开头。 收集性能数据并并行构建用户档案扩充属性。 如果您至少有1,000个转化事件用于AI排名培训和填充良好的选件目录，请改进为选项C。

#### 渠道选择的静态分支与决策

渠道选择可以通过简单的历程条件节点（直接评估用户档案属性）或通过决策框架（其中渠道被建模为具有资格和排名的决策项目）实现。

- **静态条件节点支持：**&#x200B;简单、透明、易于故障排除。 当渠道选择逻辑简单时最佳（例如，“如果存在推送令牌并且上次推送在30天内打开，请使用推送；否则使用电子邮件”）。
- **基于决策的渠道选择更适合：**&#x200B;集中管理、AI优化潜力、无需修改历程画布即可改进排名逻辑的能力。 当渠道选择复杂并且应该随时间改进时达到最佳效果。
- **推荐：**&#x200B;如果渠道选择标准简单且定义正确，请使用选项B的静态条件节点。 当您希望AI随时间推移优化渠道选择，或者当渠道选择逻辑足够复杂以从集中式资格和排名管理中受益时，可使用基于决策的渠道选择。

#### 与目录可管理性相比，提供精细度

包含许多目标选件的大型、精细选件目录可产生更精确的个性化，但需要更多的管理工作。 资格更广泛的较小目录更易于管理，但不太个性化。

- **大型目录（许多特定选件）的好处：**&#x200B;个性化精度高，针对不同受众选择的相关性更高，回退率更低
- **小型目录（范围更广的优惠）的好处：**&#x200B;更易于管理、设置更快、测试更简单、孤立的优惠风险更低
- **推荐：**&#x200B;从5-15个个性化优惠开始，并根据决策提供后备。 在观察哪些区段最常收到后备优惠时添加更多优惠。 使用收藏集限定符按类别、层或产品线组织优惠，以实现可管理的增长。

#### 基于优先级的决策与人工智能排名的决策

基于优先级的排名具有确定性和透明度。 人工智能排名决策会自动优化，但需要训练数据，并且透明度较低。

- **基于优先级的排名有利于：**&#x200B;可预测性、透明度、即时部署、无培训数据要求
- **AI排名决策支持：**&#x200B;持续优化、数据驱动选择、发现不明显优惠配置文件亲和度的能力
- **推荐：**&#x200B;对初始部署使用基于优先级或基于公式的排名。 当您至少累积1,000个转化事件并想要从基于规则的优化转变为基于模型的优化时，请过渡到AI排名决策。

## 相关文档

以下资源提供了有关此用例模式中所用功能的更多详细信息。

### 历程编排

- [历程入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [创建旅程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [历程属性](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [读取受众活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [受众鉴定事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [条件活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在历程中添加消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [退出标准](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [历程条目管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [测试您的历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [发布历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

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
- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### 渠道配置

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [创建 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP预热计划](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [电子邮件表面设置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 消息创作和个性化

- [创建电子邮件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 冲突、优先级和频率管理

- [冲突和优先级管理概述](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [优先级分数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [识别潜在冲突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [历程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### 受众和分段

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [受众构成](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language参考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 报告和分析

- [历程实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### 个人资料和身份

- [Real-time Customer Profile概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Customer AI概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### 数据治理和同意

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [管理禁止列表](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 护栏

- [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity服务护栏](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
