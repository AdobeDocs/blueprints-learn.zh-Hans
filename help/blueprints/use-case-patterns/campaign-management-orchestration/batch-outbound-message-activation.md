---
title: 批量出站消息激活
description: 了解如何在单个批量执行中评估受众并投放计划的出站消息。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 192853ce-02ab-46e6-9092-3db5354bc19c
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '8246'
ht-degree: 1%

---

# 批量出站消息激活

本指南为使用[!DNL Adobe Journey Optimizer] (AJO)和[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)将计划的出站消息传递到定义的受众区段提供了完整的实施参考。 它专为需要了解所有可行的实施方法、促成每种选择的决策考虑因素以及在何处查找有关[!DNL Adobe Experience League]的详细文档的解决方案架构师、营销技术人员和实施工程师而设计。

批量出站消息激活是一对多出站消息传递的基本营销活动模式。 它涵盖从受众定义到消息投放和性能分析的整个生命周期。 本指南提供了三个实施选项 — 计划活动、受众触发的历程和API触发的活动 — 并为为每个用例选择正确的方法提供了结构化决策指导。

它提供了实施选项、权衡分析、UI导航路径和[!DNL Experience League]文档参考。

## 用例概述

组织经常需要在特定时间或响应系统事件，向已知受众区段投放单个消息。 此模式通过将[!DNL RT-CDP]中的受众评估与[!DNL Journey Optimizer]中的消息创作和营销活动执行结合起来来满足该要求。

业务场景简单明了：定义应该接收消息的人员、通过个性化创建消息内容、将受众和消息绑定到活动或历程中，并按计划、通过受众资格或通过系统触发器执行发送。 结果生成一个投放消息，其中具有投放、参与和转化量度的完整报告。

每当可以通过在一次执行中将单个消息交付给已知受众来推进业务目标时，此模式即适用。 它与事件触发的消息传递（响应实时行为事件）和多步骤协调的历程不同，多步骤协调的历程随时间通过多个接触点引导用户档案。 批量激活是最简单的营销活动模式，也是出站消息传递用例最常见的起点。

## 主要业务目标

本节介绍批量出站消息激活支持的主要业务目标。

### 提高电子邮件和营销活动参与度

**描述：**&#x200B;通过优化的内容和定位，提高打开率、点进率和整体促销活动响应率。

**KPI：**&#x200B;打开率、参与度、转化率

### 增加收入及销售额

**描述：**&#x200B;通过优化的数字渠道、营销活动和客户历程推动总收入增长。

**KPI：**&#x200B;转化率、递增收入、平均订单值

**相关业务目标：** [增加收入和销售](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

### 简化活动执行

**描述：**&#x200B;通过模板、自动化和标准化流程缩短Campaign构建时间并简化多渠道Campaign交付。

**KPI：**&#x200B;上市速度、效率、准时完成百分比

## 战术用例示例

以下情形说明了批量出站消息激活的常见应用。

- **销售公告或促销电子邮件爆炸** — 在预定日期向符合条件的客户群广播促销优惠
- **产品发布推送通知** — 通过推送通知感兴趣的客户有关新产品可用性的信息
- **新闻稿或摘要电子邮件** — 向订阅者受众定期提供内容汇总
- **活动注册邀请** — 邀请符合条件的潜在客户参加网络研讨会、会议或面对面活动
- **订阅续订提醒电子邮件** — 提醒即将续订的客户采取行动
- **忠诚度计划里程碑通知** — 祝贺成员达到忠诚度等级或点阈值
- **特定call-to-action电子邮件** — 推动目标操作，如完成购买、更新首选项或注册程序
- 针对限时优惠或限时优惠的&#x200B;**短信促销活动** — 通过短信向已选择启用的受众发送紧急限时促销活动

## 关键绩效指标

下表定义了用于衡量促销活动效果的KPI。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 投放率 | 成功发送给收件人的邮件百分比 | 已投放/已发送x 100 |
| 打开率 | 收件人打开的已投放邮件的百分比 | 独特打开次数/交付次数x 100 |
| 点进率(CTR) | 点击了链接的已投放消息的百分比 | 独特点击次数/交付次数x 100 |
| 点击打开率(CTOR) | 已单击链接的已打开消息的百分比 | 独特点击次数/独特打开次数x 100 |
| 转化率 | 完成所需操作的收件人百分比 | 转化/已交付x 100 |
| 取消订阅率 | 接收消息后取消订阅的收件人百分比 | 取消订阅/已交付x 100 |
| 跳出率 | 无法投放的消息百分比 | 退回数/发送次数x 100 |
| 每封发送电子邮件的收入 | 归因于营销活动的收入除以发送的消息 | 总收入/已发送 |

## 用例模式

**批量出站消息激活**

评估受众，然后在单个批量执行中将计划的出站消息（电子邮件、短信、推送）交付给所有符合条件的用户档案。

**函数链：**&#x200B;受众评估>消息创作>营销活动执行>报告

## 应用程序

以下应用程序用于实现此模式。

- **[!DNL Adobe Journey Optimizer](AJO)** — 消息创作、渠道配置、活动执行、历程编排、内容实验、频率规则和报表
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — 受众评估、同意和治理实施
- **[!DNL Adobe Experience Platform](AEP)** — 配置文件存储、身份服务、架构、数据集、数据收集

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本功能 | 状态 | 必须准备就绪 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 假设就位 | 使用活动渠道配置配置的AJO沙盒。 发送委派的子域、分配的IP池以及IP预热完成。 分配了促销活动/历程创建权限的用户角色。 | [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)，[访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | 具有用于分段和个性化（如名称、电子邮件、偏好设置、层）的属性的XDM Individual Profile架构。 XDM ExperienceEvent架构正在捕获目标转化操作（例如，`commerce.purchases`、`web.webInteraction`），以用于营销活动后的转化跟踪。 两个架构的已启用配置文件的数据集。 | [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| 数据源和收集 | 假设就位 | CTA目标上的Web SDK或Analytics标记必须处于活动状态才能捕获转化事件。 用户档案属性的流式或批量摄取管道必须可操作。 | [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)，[源概述](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| 身份和配置文件配置 | 假设就位 | 为电子邮件（以及任何跨设备标识符）配置的身份命名空间。 发送时个性化映射、引入和可解析的配置文件属性所需的配置文件属性。 已配置合并策略。 | [身份服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| 受众定义和分段 | 必填 | 使用区段生成器或受众合成在RT-CDP中定义的目标受众。 已发布受众并使用非零群体进行评估。 通过RT-CDP受众评估在实施阶段1中涵盖。 | [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么这很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | 计算属性（例如上次购买后间隔天数、生命周期订单计数或参与度分数）可提高受众精度并支持更丰富的消息个性化。 | [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 数据生命周期管理 | 推荐 | 应该为推动转化跟踪的事件数据集制定数据保留策略（到期）。 必须为渠道级别的选择加入/选择退出实施配置同意架构字段。 | [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)，[同意和偏好设置字段组](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents) |
| 数据使用标签和执行 | 推荐 | 个性化中使用的PII字段上的治理标签可确保激活期间的合规性。 防止在消息内容或受众导出中使用未经授权的敏感配置文件数据。 | [数据管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)，[数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview) |
| 监视和可观察性 | 已包含 | 实时发送监视是报告阶段的一部分。 平台级别的摄取失败或许可证使用情况警报，提供了超出营销活动级别量度的操作可见性。 | [可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)，[警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| 报告和分析 | 已包含 | 报告阶段涵盖营销活动和历程报告。 为了进行更深入的跨渠道分析，CJA集成提供了超出funnel内置报表的AJO分析、归因建模和同类群组分析。 | [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)，[AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## 应用程序功能

此计划从应用程序功能目录中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Journey Optimizer] (AJO)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 渠道配置 | 阶段2：通道配置 | 配置或验证渠道界面（电子邮件、短信或推送），包括子域、IP池、发件人设置和禁止列表 |
| 消息创作 | 阶段3：消息创作 | 使用模板、电子邮件Designer、个性化表达式、条件内容块和内容片段创建消息内容 |
| 营销活动执行 | 阶段4：创建营销活动或历程 | 创建、配置和激活绑定受众、消息和执行计划的计划或API触发的营销活动 |
| 内容试验 | 阶段4：创建营销活动或历程 | （可选）配置A/B或多变量内容试验以优化消息性能 |
| 频度和业务规则 | 阶段4：创建营销活动或历程 | （可选）应用频率上限规则以防止在并发活动间过度发送消息 |
| 冲突和优先级管理 | 阶段4：创建营销活动或历程 | 当多个营销活动针对重叠受众时，分配优先级得分并配置冲突解决方案 |
| 报告和性能分析 | 第5阶段：报告和性能分析 | 在执行期间通过实时报告监控投放量度，并在完成后通过历史报告分析营销活动效果 |

### [!DNL Real-Time CDP] (RT-CDP)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 受众评估 | 第1阶段：受众评估 | 使用区段生成器或受众构成定义受众规则，选择评估方法（批处理、流或边缘），并验证受众群体 |
| 同意和治理实施 | 第1阶段：受众评估 | 强制实施同意首选项和数据使用策略，以确保只有同意的用户档案才会收到营销活动消息 |

## 先决条件

请在开始实施之前完成以下操作。

- [ ]个AJO沙盒已配置并处于活动状态
- [ ]发送子域已委派和验证（已配置SPF、DKIM、DMARC）
- [ ] IP池已分配并预热用于生产发送卷
- [ ]至少存在一个活动的渠道界面（电子邮件、短信或推送）
- [ ]用户帐户具有营销活动/历程创建和内容创作权限
- [ ] XDM配置文件架构包括受众分段和消息个性化所需的属性
- [ ] XDM事件架构捕获营销活动后跟踪的转化事件
- [ ]配置文件数据已通过Identity Service引入和统一
- [ ] Web SDK或Analytics标记在CTA目标页面上处于活动状态，可捕获转化事件
- [ 在目标消息传递渠道的用户档案中填充]同意字段
- [ ]个内容资产（图像、徽标、品牌指南）可用于消息设计

## 实施选项

本节介绍批量出站消息激活的三个实施选项，以及比较和决策指导。

### 选项A：计划的活动（一次性批量发送）

**最适合：**&#x200B;基于日期的发送 — 销售公告、产品发布、活动注册截止日期、续订提醒、新闻稿发送以及提前知道执行日期的任何发送。

**工作方式：**

计划的营销活动是批出站消息传递的最简单变体。 营销人员定义目标受众、创作消息内容、设置发送日期和时间，以及激活营销活动。 在安排的执行时间，AJO会评估受众以确定当前的符合条件群体，然后在一个批次中向所有符合条件的用户档案发送消息。

整个配置在AJO Campaigns界面中进行 — 没有历程画布、没有分支逻辑，也没有等待步骤。 这使得计划营销活动可以最快速地配置，也最轻松地管理。 可将营销活动设置为立即执行、特定的未来日期/时间或定期计划（每天、每周、每月）。

**关键注意事项：**

- 在执行时评估受众，因此将包含计划和执行之间符合条件的用户档案
- 无分支、等待或条件逻辑可用 — 消息将传递到所有符合条件的用户档案
- 直接在营销活动配置中支持内容试验（A/B测试）
- 营销活动属性包括与其他营销活动解决冲突的优先级得分

**优点：**

- 最简单的配置，开销最小
- 直接批量发送的最快启动时间
- 对定期计划的内置支持
- 本机支持的内容试验
- 受众在执行时重新评估新鲜度

**限制：**

- 投放前无等待步骤、条件或分支
- 无法对计划和执行之间的用户档案行为做出反应
- 仅限单个消息操作 — 无多点触控顺序
- 激活后无法编辑（必须复制和修改）

**Experience League：**

- [开始使用营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### 选项B：受众触发的历程

**最适合：**&#x200B;行为驱动发送 — 放弃的购物车通知、试用到期提醒、里程碑庆祝活动、基于资格的外联活动，以及触发器为受众资格或业务事件而不是日历日期的任何发送。

**工作方式：**

受众触发的历程使用历程画布在用户档案符合定义的受众或触发合格事件时投放消息。 历程进入由受众成员身份更改（用户档案进入受众）而不是固定计划触发。 历程画布允许在消息操作之前执行可选等待步骤、条件分支和禁止显示逻辑，比计划的活动提供更大的灵活性。

历程可在历程界面中使用读取Audience条目事件进行配置。 当配置文件符合受众资格时，他们将进入历程并浏览画布节点。 简单的实施可能只包含单个电子邮件操作节点，这使其在功能上类似于计划的营销活动，但具有基于受众鉴别的登入时间。 更复杂的实施可以在消息投放之前添加等待节点（例如，在鉴别后等待24小时）、条件节点（例如，检查配置文件是否打开了以前的电子邮件）或禁止逻辑。

**关键注意事项：**

- 历程条目由受众资格而非日历日期触发
- 历程画布支持等待、条件和拆分节点以实现预投放逻辑
- 历程重新进入规则控制配置文件是否可以多次进入旅程
- 历程仲裁设置确定用户档案已在竞争历程中的行为

**优点：**

- 基于受众资格而不是固定时间表的灵活进入时间
- 等待和条件节点允许预投放逻辑（例如，延迟、检查、禁止）
- 重新进入控件可防止将重复发送到同一配置文件
- 如果用例变化，可以扩展到多步历程
- 支持具有登入、退出和节点级指标的历程级报告

**限制：**

- 比计划的活动更多的配置开销
- 即使对于单消息用例，历程画布也会增加复杂性
- 历程必须已发布，并且在实时无法编辑（必须创建新版本）
- 条目上限可能会限制在一个时间范围内输入的配置文件数

**Experience League：**

- [历程入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [读取受众历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### 选项C：API触发的营销活动

**最适合：**&#x200B;系统启动的发送 — 包含追加销售内容的订单确认、支持票证解析跟进、包含营销内容的事务性通知，以及在特定时刻触发事件源自外部系统的任何发送。

**工作方式：**

API触发的营销活动在触发系统事件发生时通过REST API调用激活。 在AJO中预先配置了营销活动以及消息内容和渠道设置，但是API调用不会绑定预定义的受众，它指定了收件人用户档案，并且可以传递填充动态消息参数的上下文数据。

此变量非常适用于发送时间由外部系统（例如，订单管理系统、CRM工作流或支持平台）而不是受众评估或日历计划确定的情况。 在API触发器有效载荷中传递的上下文数据（如订单详细信息、票证编号或产品名称）可以使用未存储在配置文件上的上下文属性将消息内容个性化。

**关键注意事项：**

- 无需预绑定的受众 — 收件人在API触发器请求中指定
- 触发器有效负载中的上下文数据支持在配置文件属性之外进行动态个性化
- 营销活动的类型必须是“API触发”，并且必须先激活它，然后才能接收触发器请求
- 每个API触发器请求最多支持20个配置文件收件人
- 可以跳过受众评估（第1阶段），因为收件人来自API调用

**优点：**

- 事件时刻从外部系统实时触发
- 数据未存储在配置文件中的上下文个性化（订单详细信息、票证信息）
- 无受众评估开销 — 直接指定收件人
- 支持事务型+营销型混合消息传递

**限制：**

- 需要外部系统集成才能发送API触发器
- 每个API触发器请求最多20个收件人
- 无内置受众评估 — 调用系统必须确定收件人
- 由于API集成要求，提高了技术复杂性
- API触发的营销活动不支持内容试验

**Experience League：**

- [API触发的营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [使用API触发营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### 选项比较

下表比较了三个实施选项（基于主要标准）。

| 标准 | 选项A：计划的活动 | 选项B：受众触发的历程 | 选项C：API触发的营销活动 |
| --- | --- | --- | --- |
| 最适合 | 基于日期的发送（促销活动、启动项、新闻稿） | 行为驱动型发送（资格事件、里程碑） | 系统启动的发送（订单确认、事务性） |
| 复杂性 | 低 | 中 | Medium — 高 |
| 触发器类型 | 日历日期/时间或定期计划 | 受众资格或业务事件 | 外部系统API调用 |
| 预投放逻辑 | 无 | 等待，条件，拆分节点可用 | 无（调用系统中的逻辑） |
| 受众绑定 | 预定义的RT-CDP受众 | 预定义的RT-CDP受众 | API有效负载中指定的收件人 |
| 上下文数据 | 仅限配置文件属性 | 仅限配置文件属性 | 配置文件属性+ API有效负载数据 |
| 内容试验 | 支持 | 支持（根据消息操作） | 不支持 |
| 频率上限 | 支持 | 支持 | 支持 |
| 再入控制 | 不适用（一次性执行） | 可配置的重新进入规则 | 不适用（根据请求） |
| 配置界面 | AJO Campaigns | 历程 | AJO Campaigns +外部系统 |
| 需要 | 受众、渠道界面、消息 | 受众、渠道界面、消息、历程画布 | 渠道界面、消息、API集成 |

### 选择正确的选项

使用以下决策流选择适当的实施选项：

1. **发送是否由外部系统事件触发（例如，下达了订单，解决了票证）？** 如果是，请选择&#x200B;**选项C： API触发的营销活动**。 这是唯一支持具有上下文有效负载数据的系统启动触发器的选项。

2. **该发送是锚定在特定日历日期还是定期计划？** 如果是，请选择&#x200B;**选项A：计划的促销活动**。 这是为日期驱动发送配置的最简单和最快。

3. **发送是否需要响应受众资格或需要预投放逻辑（等待、条件、抑制）？** 如果是，请选择&#x200B;**选项B：受众触发的历程**。 历程画布为行为驱动的输入和投放前决策逻辑提供了灵活性。

4. **是否向已知受众发送简单广播，没有特殊的时间或逻辑要求？** 选择&#x200B;**选项A：计划促销活动**&#x200B;以获得最低的配置开销。

## 实施阶段

本节详细介绍了实施的每个阶段，包括决策点和特定于选项的指导。

### 第1阶段：评估受众

**应用程序函数：** RT-CDP：受众评估

此阶段定义并评估将接收营销活动消息的目标受众区段。 它根据用户档案属性、行为信号和禁止规则确定哪些用户档案符合发送条件。

>[!NOTE]
>对于选项C（API触发的营销活动），如果收件人完全在API触发器有效载荷中指定，则可以跳过此阶段。 但是，甚至API触发的营销活动也可受益于具有抑制受众，以过滤掉不应接收消息的用户档案。

#### 决策：受众标准

哪些条件定义了目标受众？ 什么禁止显示规则应排除配置文件？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 基于配置文件属性的受众 | 目标受众由人口统计、偏好设置或状态属性定义 | 构建最简单；支持所有评估方法 |
| 基于事件的行为受众 | 目标受众由在一个时间范围内采取（或不采取）的动作定义 | 需要事件数据摄取；时间窗口规则可能会限制流资格 |
| 受众构成（派生受众） | 目标受众需要跨多个源受众执行排名、拆分、排除或扩充操作 | 更强大但仅限批次的评估；每个沙盒仅限10个组合 |

#### 决策：评估方法

受众必须多久更新一次才能反映新的符合条件或取消符合条件的用户档案？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 批次评估 | 接受一天内受众新鲜度的预定活动；大型、复杂的受众 | 默认用于大多数段类型；按每日计划或按需求处理；支持所有段规则功能 |
| 流式处理评估 | 受众触发的历程，其中用户档案必须在符合条件时近乎实时地进入 | 自动适用于符合条件的区段规则表达式；并非所有区段类型都符合流式传输条件；近乎实时的延迟（秒到分钟） |
| 边缘评估 | 此模式不典型（用于同一页面个性化） | 区段规则支持有限；毫秒延迟；仅在与Web个性化模式结合时相关 |

#### 决策：合并策略

受众应使用哪个合并策略来解析配置文件片段？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 默认合并策略（按时间戳排序） | 最常见于批处理营销活动用例 | 最近的属性值wins；出站消息的标准值 |
| 自定义合并策略（数据集优先级） | 特定数据源何时应优先处理关键属性 | 当CRM数据应覆盖某些字段的Web收集数据时非常有用 |

#### UI导航

客户>受众>创建受众>构建规则

#### 关键配置详细信息

- 使用区段生成器以及配置文件属性、行为事件和区段成员资格的区段规则定义受众
- 应用禁止显示规则以排除已转化、最近收到类似消息或选择退出的用户档案
- 在继续之前，验证受众是否具有非零群体
- 对于批处理活动，请确保区段评估计划处于活动状态或触发按需评估
- 确认同意字段（`consents.marketing.email.val`、`consents.marketing.sms.val`等） 填充并强制执行

#### 不同选项的位置

选项A的&#x200B;**（计划的营销活动）：**

批次评估是典型的。 在活动执行时，将重新评估受众，从而定向最新的符合条件群体。 定义受众并验证其群体，然后继续创建营销活动。

选项B （受众触发的历程）的&#x200B;**：**

应首选流式评估，这样用户档案才会在符合条件时进入历程。 确保区段规则表达式符合流式处理条件（简单事件触发器、属性比较、有限时间窗口）。 配置受众并验证流资格是否处于活动状态。

选项C （API触发的营销活动）的&#x200B;**：**

可以完全跳过受众评估。 如果使用，请创建禁止受众以筛选不应接收消息的用户档案（例如，最近取消订阅、已转化）。 呼叫系统确定主要收件人。

#### Experience League文档

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [受众构成](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language参考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 阶段2：配置渠道

**应用程序函数：** AJO：渠道配置

此阶段将验证或创建渠道界面（预设），该界面定义消息的发送基础结构 — 子域、IP池、发件人身份、回复地址和取消订阅设置。 在创作消息内容或激活营销活动之前，必须存在有效的渠道平面。

#### 决策： Target渠道

哪个消息传送渠道将投放营销活动消息？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 电子邮件 | 大多数营销活动类型 — 新闻稿、促销活动、通知、续订 | 需要委派的子域、预热的IP池、发件人标识和取消订阅配置 |
| 短信 | 时间敏感型或简短的邮件 — 闪电式销售、预约提醒、 OTP代码 | 需要SMS提供商凭据（Sinch、Twilio或Infobip）；每消息成本较高；同意要求较严格 |
| 推送通知 | 移动参与受众 — 应用程序更新、基于位置的选件、应用程序内功能公告 | 需要APN (iOS)和/或FCM (Android)凭据；用户必须已安装授予推送权限的应用程序 |

#### 决策：渠道表面选择

沙盒中是否已存在合适的渠道平面，还是必须创建新的渠道平面？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 重用现有表面 | 经过验证的活动表面与所需的子域、发件人标识和渠道类型相匹配 | 最快路径；无需DNS或热机配置 |
| 创建新表面 | 没有与要求匹配的现有表面，或需要新的子域/发件人身份 | 需要子域委派、DNS验证、IP池分配以及可能的IP热备（新IP需要2-4周） |

#### 决策：取消订阅处理

如何在渠道平面上管理选择退出？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 一键式列表取消订阅标头 | 所有营销电子邮件的标准；主要ISP(Gmail、Yahoo)要求提供此功能 | 添加基于mailto：或URL的取消订阅标头，ISP将其显示为“取消订阅”按钮 |
| 电子邮件正文中的取消订阅链接 | 对于不支持list-unsubscribe标头的电子邮件客户端，需要用作回退 | 在电子邮件页脚中加入取消订阅链接，并将此链接与list-unsubscribe标头放在一起 |
| 两者（推荐） | 所有营销电子邮件的最佳实践 | 最大法规遵从性覆盖范围和最佳可投放性配置文件 |

#### UI导航

“管理”(Administration)>“渠道”(Channels)>“渠道曲面”(Channel surfaces)>“创建曲面”(Create surfaces)（或选取现有的）

#### 关键配置详细信息

- 对于电子邮件：绑定发送子域、IP池、发件人姓名、发件人电子邮件、回复地址和密件抄送地址（如果需要审核副本）
- 对于短信：配置短信提供商凭据和短代码或长代码设置
- 对于推送：使用应用程序的证书或服务器密钥配置APN和/或FCM凭据
- 在继续之前，验证渠道表面是否显示“活动”状态
- 确认已为发送子域正确配置DNS记录(SPF、DKIM、DMARC)
- 查看过时条目的禁止列表；在激活之前进行清理

#### Experience League文档

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [创建 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP预热计划](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [电子邮件表面设置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [管理禁止列表](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 阶段3：编写消息

**应用程序函数：** AJO：消息创作

此阶段将创建要交付给受众的消息内容。 这包括选择或创建内容模板、设计消息布局、使用用户档案属性添加个性化、为受众特定的变体配置条件内容块、创建可重用的内容片段，以及使用示例用户档案预览/测试消息。

#### 决策：内容方法

应如何创建消息内容？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 从现有模板开始 | 存在品牌批准的模板，并与消息类型（促销、事务性、新闻稿）匹配 | 最快的创作路径；确保品牌一致性；模板特定于沙盒 |
| 从头开始设计 | 不存在合适的模板或消息需要唯一的布局 | 更大的灵活性，但需要更大的工作量；考虑将另存为模板以供重复使用 |
| 导入HTML | 消息设计是在外部创建的（例如，在设计工具中），HTML可供导入 | 保留外部设计；可能需要调整AJO兼容性和个性化令牌 |

#### 决策： Personalization深度

哪些配置文件属性应该将消息个性化，以及是否需要条件内容块？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 基本个性化（姓名、问候语） | 简单的营销活动，其中具有个性化称呼的通用内容已经足够 | 工作量小；呈现问题的风险最低；使用标准配置文件属性 |
| 基于属性的个性化 | 消息内容因用户档案属性（层、首选项、位置）而异 | 需要经过验证的XDM路径；使用多个配置文件测试以确保所有变体正确呈现 |
| 条件内容块 | 不同的内容部分必须显示在同一消息的不同受众区段中 | 更加复杂的创作；每个条件都需要默认的回退；测试所有排列 |
| 上下文个性化（仅限选项C） | API触发的营销活动需要呈现在触发器有效载荷中传递的数据（订单详细信息、票证信息） | 上下文属性未存储在配置文件中；在消息中定义占位符并映射到有效负荷字段 |

#### 决策：片段策略

是否应将共享内容块创建为可重用片段？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 可重用片段 | 页眉、页脚、法律免责声明或取消订阅块在多个营销活动之间共享 | 对片段的更改会传播到引用它的所有消息（实时和草稿）；每条消息最多包含30个片段 |
| 内嵌内容 | 没有跨其他营销活动的共享元素的一次性消息 | 对一次性内容更简单；无传播风险 |

#### UI导航

营销活动>选择营销活动>编辑内容>向Designer发送电子邮件（或短信/推送编辑器）

#### 关键配置详细信息

- 使用拖放内容组件（文本、图像、按钮、分隔条、列）设计消息布局
- 设置电子邮件标头属性：主题行、标头文本和发件人表面
- 使用Handlebars语法插入个性化表达式（例如，`{{profile.person.name.firstName}}`）
- 配置用于设置格式（日期、数字、字符串处理）的辅助函数
- 添加条件内容规则，以根据配置文件属性或区段成员资格显示不同的内容
- 在不满足任何条件时配置默认回退内容
- 对于短信，在字符限制注意事项内撰写消息正文
- 对于推送，请配置标题、正文、图像和操作（深层链接或URL）
- 预览包含示例用户档案的消息，以验证个性化呈现
- 向内部利益相关者发送验证电子邮件以供审查
- 使用电子邮件渲染功能跨电子邮件客户端测试渲染

#### Experience League文档

- [创建电子邮件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [使用电子邮件Designer内容组件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [辅助函数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [发送电子邮件校样](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [电子邮件渲染](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)
- [创建短信消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [设计推送通知](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### 阶段4：创建活动或历程

**应用程序函数：** AJO：促销活动执行（选项A和C）或AJO：Journey Orchestration（选项B）

此阶段将创建活动或历程，以将受众、消息和执行机制绑定到可交付单元。 这是三个实施选项分歧最大的地方。

#### 决策：内容试验

该活动是否应包括A/B测试或多变量试验以优化消息性能？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 无试验 | 对内容有效性具有较高置信度的单个消息变体 | 最简单的配置；最快的激活速度 |
| A/B测试（2种变体） | 通过明确的假设验证测试主题行、CTA或内容布局 | 50/50或使用加权分配拆分流量；需要足够的受众规模才能实现统计意义 |
| 多变量测试（3个以上的变量） | 同时测试多个内容元素 | 需要更大的受众；达到置信阈值的持续时间更长；每个试验最多10个处理 |

#### 决策：频率封顶

此营销活动是否应遵守全球频率上限规则以防止过度发送消息？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 应用频率规则 | Campaign是更广泛的消息传送计划的一部分，具有多个并发发送 | 防止客户疲劳；超出上限的用户档案会被禁止交付 |
| 免除上限 | Campaign时间关键型或事务型，必须涉及所有符合条件的用户档案，无论近期的消息历史记录如何 | 请谨慎使用；将营销活动从频率规则中免除可能会引发消息过度发送的风险 |

#### 决策：优先级得分

此营销活动相对于其他活动的营销活动应该具有哪个优先级？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 高优先级(75-100) | 关键营销活动 — 主要产品发布、限时优惠、监管通知 | 发生冲突时，优先于较低优先级的营销活动 |
| Medium优先级(25-74) | 标准营销活动 — 新闻稿、参与活动、一般促销活动 | 与其他营销活动进行平衡；如果具有较高优先级的营销活动发生冲突，则可能被禁止 |
| 低优先级(0-24) | 友好发送 — 信息更新、次级促销 | 将被禁止，以支持更高优先级的活动 |

#### 不同选项的位置

选项A的&#x200B;**（计划的营销活动）：**

**UI导航：**&#x200B;营销活动>创建营销活动>计划>营销

1. 创建新的计划营销活动
2. 从受众选取器中选择目标受众
3. 选择渠道表面并链接创作的消息内容
4. 配置执行计划：立即、特定日期/时间或定期
5. 可选地启用内容试验并定义处理变体
6. 可以选择配置频率上限和优先级得分
7. 查看完整的营销活动配置
8. 激活营销活动

选项B （受众触发的历程）的&#x200B;**：**

**用户界面导航：**&#x200B;历程>创建历程

1. 通过“读取受众”进入事件创建新历程
2. 选择目标受众作为条目源
3. 配置重新进入规则（允许重新进入、一次性进入或等待期后重新进入）
4. 可以选择添加等待节点（例如，在资格鉴定后等待24小时）
5. 可以选择添加条件节点（例如，检查配置文件是否符合其他标准）
6. 添加消息操作节点并选择渠道表面和创作内容
7. 配置退出条件（例如，配置文件转换、配置文件取消订阅）
8. 可选地在消息操作上启用内容试验
9. 查看并发布历程

选项C （API触发的营销活动）的&#x200B;**：**

**UI导航：**&#x200B;营销活动>创建营销活动> API触发

1. 创建新的API触发的营销活动
2. 选择渠道表面并链接创作的消息内容
3. 为将在API触发器有效载荷中传递的数据配置上下文个性化令牌
4. 查看并激活营销活动
5. 记下在外部系统的API触发器集成中使用的促销活动ID
6. 调用系统向营销活动端点发送触发器请求，其中包含收件人用户档案和上下文数据

#### Experience League文档

- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [开始使用营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [API触发的营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [历程入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [读取受众历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [内容体验入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [优先级分数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [识别潜在冲突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### 阶段5：分析报告和性能

**应用程序函数：** AJO：报表和性能分析

此阶段通过实时报告监控执行期间的投放指标，并通过历史报告分析完成后的营销活动效果。 （可选）配置CJA集成，以进行更深入的跨渠道分析。

#### 决策：报告方法

此营销活动需要什么级别的报表？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅限AJO本机报表 | 标准交付和参与量度就足够了（已发送、已交付、打开、点击次数、跳出次数） | 无其他配置；报告内置到营销活动/历程UI中 |
| AJO本机报表+ CJA analysis | 在投放量度之外需要跨渠道影响分析、归因建模或funnel分析 | 需要与CJA数据集关联的AJO连接和数据视图；提供更深入的分析功能 |
| CJA程序化报告 | 利益相关者需要自动化功能板或计划报告交付 | 需要CJA报表API集成；对于执行功能板和定期性能摘要非常有用 |

#### 决策：转化跟踪

除了交付和参与量度，如何衡量活动成功与否？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 无转化跟踪 | 营销活动目标是了解或参与（打开、点击），无特定下游操作 | 最简单；无需其他事件跟踪 |
| Web转化跟踪 | Campaign CTA链接指向跟踪转化事件（购买、注册、表单提交）的网页 | 需要在目标页面上进行Web SDK或Analytics标记；必须在AEP数据集中捕获事件 |
| 自定义转化事件 | 促销活动成功与否由未在Web上捕获的业务特定事件来衡量（例如，店内购买、呼叫中心互动） | 需要将自定义事件摄取到AEP并包含在报表数据集中 |

#### UI导航

- 实时报告：营销活动>选择营销活动>实时报告（或历程>选择历程>实时报告）
- 历史报表：营销活动>选择营销活动>所有时间报表（或历程>选择历程>所有时间报表）

#### 关键配置详细信息

- 在活动执行期间访问实时报告，以监控实时交付和参与
- 审核关键量度：已发送、已投放、退回、打开、点击、取消订阅（电子邮件）；已发送、已投放、点击、错误（短信）；已发送、已投放、打开、操作（推送）
- 活动完成后，访问历史（所有时间）报告以进行全面分析
- 分析投放funnel：已定位>已发送>已投放>打开>点击量
- 查看错误和排除原因以确定投放问题
- 如果启用了内容实验，请查看实验结果并等待统计置信度，然后再声明入选者
- 对于CJA集成，请验证AJO数据视图是否包含相关的AJO数据集（消息反馈事件数据集、电子邮件跟踪体验事件数据集）

#### Experience League文档

- [营销活动实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [历程实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [内容试验报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## 实施注意事项

本节介绍护栏、常见隐患、最佳实践和权衡取舍决策。

### 护栏和限制

- 每个沙盒最多500个活动实时营销活动 — [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每个沙盒最多4,000个区段定义 — [实时客户资料护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 每个沙盒每个渠道类型最多有10个渠道表面
- API触发的营销活动支持每个触发器请求最多20个配置文件收件人
- 营销活动一旦激活即无法编辑 — 请改为复制和修改
- 实时报表每60秒刷新一次，并显示过去24小时的数据
- 活动完成后，可能需要长达2小时才能完全填充历史报表
- 每个内容试验最多10个处理（变量）
- 每个沙盒最多10个上限配置
- 每条消息最多包含30个内容片段
- 建议最大电子邮件大小为100 KB，以实现最佳可投放性
- IP预热计划应在新IP的2-4周内逐渐增加容量
- 禁止列表条目将保留一段可配置的期间（软退回的默认值为14天）

### 常见陷阱

- **在IP预热完成之前发送：** ISP将标记立即发送大量数据的新IP地址，从而导致可投放性差且可能被列入阻止名单。 在生产使用新IP之前始终完成IP预热计划。

- **不跨多个配置文件测试个性化：**&#x200B;如果引用的XDM路径不存在或某些配置文件为空，则适用于一个测试配置文件的Personalization令牌对于其他配置文件可能会失败。 始终使用代表不同数据完整性级别的多个测试配置文件进行预览。

- **跳过禁止列表审核：**&#x200B;过时的禁止列表条目可能会阻止传递到有效地址，而缺少条目可能导致传递到生成退回的无效地址。 在主要营销活动之前查看和清理禁止列表。

- **忽略促销活动的频率上限：**&#x200B;如果发送促销活动而没有频率上限，而其他促销活动也处于活动状态，则可能会导致用户档案在短时间内收到多封邮件，从而导致取消订阅和垃圾邮件投诉。

- **计划营销活动而不验证受众群体：**&#x200B;在确认目标受众具有非零的评估群体之前激活营销活动，会生成零条消息。 始终在激活之前验证受众规模。

- **对受众触发的历程使用批次评估：**&#x200B;如果历程在批次评估中使用读取受众条目，则用户档案不会近乎实时地进入。 在需要近乎实时的历程输入时对受众使用流式评估。

- **未配置同意实施：**&#x200B;未经有效的营销同意向用户档案发送消息违反了规定，并损害了可投放性声誉。 确保在渠道平面级别填充和强制执行同意字段。

### 最佳实践

- 对于简单的广播用例，从选项A（计划促销活动）开始，仅在需要预投放逻辑或行为驱动计时时升级到选项B（受众触发的历程）
- 电子邮件正文中始终包含一键式list-unsubscribe标头和取消订阅链接，以便最大限度地遵循相关说明
- 为页眉、页脚和法律免责声明创建可重复使用的内容片段，以确保活动之间的一致性
- 在激活营销活动之前设置频率上限规则，以防止并发发送之间出现消息过度情况
- 使用内容试验来优化主题行和CTA，从A/B测试开始，然后再进行多变量试验
- 为所有活动分配优先级得分，以确保以一致的方式解决冲突
- 安排在活动执行时间之前完成批量受众评估，以确保获得新的受众数据
- 发送校样电子邮件，并使用电子邮件渲染功能验证消息在激活之前能否在电子邮件客户端中正确显示
- 在活动激活后立即监控实时报告，以尽早发现投放问题
- 将营销活动配置和实验结果存档，以供将来参考和持续优化

### 权衡决定

在做出实施选择时，应该权衡以下因素。

#### 简单性与灵活性

计划的营销活动（选项A）提供了最简单的配置，但没有预投放逻辑。 受众触发的历程（选项B）提供预投放逻辑，但会增加配置复杂性。

- **选项A支持：**&#x200B;启动速度、操作简便性、营销人员自助服务
- **选项B支持：**&#x200B;行为定位、条件隐藏、多步历程的可扩展性
- **建议：**&#x200B;从选项A开始，直接发送。 仅当用例在交付之前确实需要等待、条件或分支逻辑时，才移至选项B。 避免将历程画布用于无法从编排功能中获益的简单批量发送。

#### 受众新鲜度与评估成本

流式评估提供近乎实时的受众更新，但具有区段规则限制。 批量评估支持所有区段规则功能，但按每日计划进行评估。

- **流优惠：**&#x200B;及时性、行为驱动的准确性、受众触发的历程条目
- **批次支持：**&#x200B;复杂的受众逻辑、较大的群体、较低的评估开销
- **建议：**&#x200B;对每日新鲜度充足的计划营销活动（选项A）使用批次评估。 对受众触发的历程使用流式评估（选项B），用户档案在符合条件时必须输入。 如果受众区段规则表达式不符合流式处理条件，请重构规则或接受批处理级别的延迟。

#### Personalization深度与创作复杂性

更深入的个性化（条件内容块、动态部分）可提高参与度，但会增加创作和测试工作量。

- **深层个性化优惠：**&#x200B;参与率更高，客户体验更相关，转化率更高
- **简单的个性化优点：**&#x200B;启动时间更短，测试负担更轻，减少出现错误的风险
- **推荐：**&#x200B;从基本个性化（名字、相关产品类别）和条件内容块中的层开始（基于测量到的性能提升）。 始终在激活之前测试多个测试配置文件中的所有内容变体。

#### 频率控制与消息到达率

严格的频率上限可防止过度发送消息，但可能会禁止向最近收到其他消息的用户档案发送营销活动。

- **严格的上限优惠：**&#x200B;客户体验质量、较低的取消订阅率、品牌声誉
- **宽松的上限优惠：**&#x200B;最大消息覆盖率、更高的总展示次数、营销活动覆盖率
- **推荐：**&#x200B;始终为营销活动启用频率上限。 设置特定于渠道的上限（例如，每周3-5封电子邮件，每周1-2封短信）。 只有真正的时间关键型或事务型消息才免于遵守上限规则。

## 相关文档

此部分提供按主题组织的[!DNL Experience League]文档的完整链接。

### 营销活动

- [开始使用营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [API触发的营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### 历程

- [历程入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [读取受众历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### 渠道配置

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [创建 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP预热计划](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [电子邮件表面设置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [管理禁止列表](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 消息创作和个性化

- [创建电子邮件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [使用电子邮件Designer内容组件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [导入电子邮件内容或对其进行编码](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/code-content)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [辅助函数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### 内容管理

- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [发送电子邮件校样](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [电子邮件渲染](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)

### 内容试验

- [内容体验入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [内容试验报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [统计计算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### 频率和冲突管理

- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [业务规则概述](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [冲突和优先级管理入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [优先级分数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [识别潜在冲突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [历程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### 受众和分段

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [受众构成](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language参考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 报告

- [营销活动实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [历程实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### 数据治理和同意

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [同意和偏好设置字段组](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### 数据建模和标识

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### 护栏

- [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [摄取护栏](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### 教程和快速入门

- [Journey Optimizer入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/get-started)
- [创建您的第一个营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [创建您的第一个历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
