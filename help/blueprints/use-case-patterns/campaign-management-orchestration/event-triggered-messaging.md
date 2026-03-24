---
title: 事件触发的消息传递
description: 了解如何响应行为或系统事件而交付情境式实时消息。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 75137990-9848-40c0-abf3-adbd21d2de52
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '9040'
ht-degree: 1%

---

# 事件触发的消息传递

本指南为使用[!DNL Adobe Journey Optimizer] (AJO)、[!DNL Real-Time Customer Data Platform] (RT-CDP)和[!DNL Adobe Experience Platform] (AEP)的事件触发消息提供全面的实施蓝图。 它专为需要投放情境式实时消息以响应行为或系统事件的解决方案架构师、营销技术人员和实施工程师而设计。

使用本指南了解要配置哪些内容，在何处存在实施选择，以及促成每项决策的利弊取舍。

该指南涵盖从事件摄取到历程创建再到消息交付和性能报告的整个生命周期，其中针对三个不同的实施选项提供了详细的决策指导。

## 用例概述

事件触发的消息传送响应于实时行为或系统事件提供上下文消息。 与批量出站消息激活不同（按计划发送到预评估的受众），此模式侦听符合条件的事件（例如购物车放弃、浏览会话、表单提交或系统状态更改），并立即将触发的用户档案输入到评估条件并发送消息的历程中。

该模式依赖于实时事件流式传输到AEP（通过Web SDK、Mobile SDK或服务器端API）、在AJO中具有单一事件条目的旅程，以及确定是否发送和发送内容的条件评估逻辑。 消息通常在触发事件后的几分钟内发送，因此此模式非常适合时间敏感型上下文相关通信。

与计划的批处理通信相比，组织使用此模式来实时响应客户操作，提高了相关性并提高了参与度和转化率。 常见情形包括放弃的购物车恢复、购买后跟进、注册后的欢迎邮件，以及付款故障或价格下降警报等时效性强的通知。

## 主要业务目标

此用例模式支持以下业务目标。

**[恢复放弃的购物车和历程](../../business-objectives/customer-experience/recover-abandoned-carts-journeys.md)**

通过及时、个性化的跟进，重新吸引在购买、申请或注册流程中放弃的用户。

| KPI |
| --- |
| 转化率、增量收入、参与度 |

**[提高转化率](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

提高完成所需操作（如购买、注册或表单提交）的访客和潜在客户的百分比。

| KPI |
| --- |
| 转化率、潜在客户转化、每个潜在客户的成本 |

**[提供个性化的客户体验](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

根据个人偏好、行为和生命周期阶段定制内容、选件和消息。

| KPI |
| --- |
| 参与度、转化率、客户满意度(CSAT) |

**[改进客户入门](../../business-objectives/customer-experience/improve-customer-onboarding.md)**

通过优化的个性化欢迎体验和激活历程，加快新客户的价值实现。

| KPI |
| --- |
| 参与度、维系率、转化率 |

## 战术用例示例

以下情形说明了如何跨不同的业务上下文应用事件触发的消息传递。

- **购物车放弃电子邮件或短信** — 当客户将商品添加到购物车但未在定义的时间范围内完成购买时，发送提醒消息
- **浏览放弃跟进** — 重新吸引查看了产品或内容但未执行转化操作的访客
- **购买后感谢或交叉销售** — 在购买事件后立即提供确认和交叉销售推荐
- **试用到期提醒** — 通知即将结束免费试用的用户，提供续订或转换消息
- **注册后的欢迎邮件** — 当新用户注册或创建帐户时，立即发送入门邮件
- **表单提交确认** — 通过上下文确认确认确认表单提交（联系请求、申请、注册）
- **付款失败通知** — 在定期付款失败时提醒客户，提示他们更新付款信息
- **应用程序卸载回送推送通知** — 当用户卸载移动应用程序时触发回送消息
- **预订或约会确认** — 在安排预订、预订或约会后立即发送确认
- **愿望清单项目的价格下降警报** — 当愿望清单中的产品降价时通知客户

## 关键绩效指标

以下KPI有助于衡量事件触发的消息传递实施的有效性。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 转化率 | 完成所需操作（购买、注册、续订）的触发消息收件人的百分比 | 转化/投放消息* 100 |
| 增量收入 | 与不发送控制组相比，由事件触发的消息产生的额外收入 | 来自触发发送的收入 — 控制组基线 |
| 打开率 | 收件人打开的已投放邮件的百分比 | 打开/交付* 100 |
| 点进率(CTR) | 至少生成一次点击的已投放消息的百分比 | 点击次数/交付次数* 100 |
| 转化时间 | 消息投放和转化事件之间的平均已用时间 | Avg（转化时间戳 — 投放时间戳） |
| 历程完成率 | 进入历程并到达消息投放步骤的用户档案的百分比（不会被条件或退出条件丢弃） | 到达投放的用户档案/进入历程的用户档案* 100 |
| 消息禁止显示率 | 由于频率限制、同意或条件评估而抑制的合格用户档案的百分比 | 隐含配置文件/合格配置文件总数* 100 |
| 跳出率 | 由于硬退回或软退回而无法投放的消息百分比 | 退回数/已发送数* 100 |

## 用例模式

本节介绍驱动事件触发式消息传递的核心模式和功能链。

**事件触发的消息传送**

监听实时行为或系统事件，然后将上下文消息交付给触发的用户档案。

**函数链：**&#x200B;事件摄取>历程条目>条件评估>消息投放>报告

## 应用程序

在此用例模式中使用以下Adobe应用程序。

- **[!DNL Adobe Journey Optimizer](AJO)** — 包含单一历程条目、条件评估、等待步骤、消息创作、渠道配置、频率管理和投放报告的事件编排
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — 历程中基于条件的筛选的受众评估、同意和治理实施、配置文件扩充
- **[!DNL Adobe Experience Platform](AEP)** — 通过Web SDK、Mobile SDK或服务器端API进行实时事件摄取；数据建模；身份解析；Edge Network

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本功能 | 状态 | 必须准备就绪 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 假设就位 | 使用活动渠道配置配置的AJO沙盒。 历程创建和发布权限分配给实施团队。 为历程管理、内容创作和渠道管理配置的用户角色。 | [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)，[访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | XDM ExperienceEvent架构必须使用条件评估和消息个性化所需的所有上下文字段捕获触发事件（例如，购物车事件、产品详细信息、购物车值的`commerce.productListAdds`）。 必须为实时客户配置文件启用架构。 必须创建对应的数据集并启用配置文件。 | [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| 数据源和收集 | 必填 | 必须配置实时事件流 — 用于Web事件的Web SDK、用于应用程序事件的Mobile SDK或用于系统事件的Edge Network Server API。 数据流必须在启用AEP和AJO服务的情况下进行配置，将事件路由到正确的数据集。 这是一个关键依赖关系，因为模式依赖于实时事件摄取。 | [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)，[配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| 身份和配置文件配置 | 必填 | 触发事件必须与已知身份（电子邮件、CRM ID或经过身份验证的会话）关联，以便历程能够解析用户档案并投放消息。 对于触发事件使用的标识符，必须存在身份命名空间。 匿名事件需要在传递消息之前通过身份图进行身份拼接。 必须配置合并策略。 | [身份服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| 受众定义和分段 | 推荐 | 虽然对于事件触发的历程不是完全必需的（条目基于事件，而不是基于受众），但可以使用受众区段在历程中进行条件评估（例如，仅当配置文件位于“高价值客户”区段时发送，或者如果配置文件位于“最近联系”区段时禁止）。 建议对历程中的实时区段成员资格检查进行流式评估。 | [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[流式分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么这很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | 计算属性（例如购物车放弃计数、上次购买间隔天数、平均订单值和生命周期购买总计）可改进触发的历程中的条件评估和个性化。 这些行为聚合有助于做出更准确的定位决策（例如，区分首次放弃者和重复放弃者）。 | [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 数据生命周期管理 | 推荐 | 应该为瞬态行为事件（页面查看、搜索、点击）配置事件数据过期时间，以管理存储成本和法规遵从性。 在消息投放期间必须存在同意架构字段，才能实施特定于渠道的选择加入/选择退出。 | [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)，[数据集过期时间](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| 数据使用标签和执行 | 推荐 | 事件和用户档案字段上的治理标签可确保合规的个性化。 如果触发的消息包括使用PII或行为数据的个性化内容，则应审查数据使用标签和治理策略，以防止在消息内容中使用未经授权的数据。 | [数据管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)，[数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview) |
| 监视和可观察性 | 已包含 | 历程执行监控是报告阶段的一部分。 此外，为事件摄取失败或历程处理延迟配置警报，以检测会阻止发送触发消息的管道问题。 | [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)，[可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 报告和分析 | 已包含 | 历程绩效报表包含在报表阶段。 要更深入地分析各个渠道以及随时间推移触发的消息传递有效性，请配置CJA连接和工作区以分析转化归因、转化时间和渠道性能。 | [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)，[AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## 应用程序功能

此计划从“应用程序功能目录”中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Journey Optimizer] (AJO)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| Journey Orchestration | 历程创建和配置 | 创建具有单一事件条目的历程、配置符合条件的事件、添加条件节点、等待步骤、消息操作、退出标准和重新进入规则 |
| 渠道配置 | 渠道界面设置 | 配置或验证渠道界面（电子邮件、短信、推送），包括子域委派、IP池、发件人设置和禁止列表管理 |
| 消息创作 | 消息内容创建 | 使用事件驱动的个性化、条件内容块和可重用片段创作上下文消息内容 |
| 频度和业务规则 | 历程创建和配置（选项C） | 配置频度上限和重复数据删除规则，防止来自高频事件源的过度消息传递 |
| 冲突和优先级管理 | 历程创建和配置 | 为竞争相同用户档案的历程分配优先级得分并配置冲突检测 |
| 报告和性能分析 | 报告和监控 | 通过实时和历史报告监控旅程交付量度；通过CJA访问程序化性能数据 |

### [!DNL Real-Time CDP] (RT-CDP)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 受众评估 | 基础设置(F5) | 评估在历程中用于基于条件的过滤的受众区段（例如，高价值客户区段、禁止显示区段） |
| 同意和治理实施 | 基本设置(S2/S3) | 在消息投放期间强制执行同意偏好设置和数据使用治理策略，以确保通信的合规性 |

## 先决条件

请在开始实施之前完成以下操作。

- [ 为历程创建和发布权限设置了]个AJO沙盒(F1)
- [ ] XDM ExperienceEvent架构通过上下文字段捕获触发事件，已为实时客户个人资料启用(F2)
- [ 通过Web SDK、Mobile SDK或Edge Network Server API配置了将数据流路由事件发送到正确AEP数据集的]实时事件流式传输(F3)
- [ 为触发事件中的标识符配置的]身份命名空间；已设置身份链接规则(F4)
- [ ]渠道界面（电子邮件、短信或推送）已配置并已通过成功的测试发送验证
- [ 使用样本用户档案创作、审阅和测试]消息内容
- [ 在目标渠道的用户档案中填充了]同意字段（例如，`consents.marketing.email.val`）
- [ ]如果使用基于条件的受众筛选（选项B/C），则定义流式计算的受众区段并主动评估

## 实施选项

此部分介绍了用于事件触发消息传递的三个实施选项。 每个选项都以上一个选项为基础，添加了其他功能。

### 选项A：简单事件触发消息

**最适合：**&#x200B;无需延迟或条件逻辑的即时单消息响应 — 订单确认、欢迎电子邮件、表单提交确认、预订确认。

**工作方式：**

历程通过单一事件进入节点侦听符合条件的事件。 当接收到事件时，用户档案进入旅程，通过最小条件评估（同意检查，用户档案存在验证），并立即通过配置的频道操作节点接收单个消息。

这是最简单的实施变体。 历程画布包含一个事件进入节点、一个用于基本资格检查的可选条件节点、一个消息操作节点和一个结束节点。 没有等待步骤，没有复杂的分支，也没有转化检查。 消息通常会在触发事件后的几秒到几分钟内发出。

来自触发事件的事件数据（产品名称、订单总计、表单详细信息）可用于通过个性化编辑器中的上下文属性进行消息个性化。 此方法可最大程度地提高交付速度并最大程度地降低历程复杂性。

**关键注意事项：**

- 无论客户是否在事件后自行转化（无转化检查），都会发送消息
- 最适合本身需要立即响应的事件（确认、确认）
- 重新进入规则应仔细配置 — 对于确认式消息，允许重新进入，以便每个事件生成消息；对于欢迎式消息，阻止重新进入

**优点：**

- 最快交付时间（事件后的秒到分钟）
- 最简单的历程配置，只需最少的活动部件
- 历程失败或配置文件受阻的风险最低
- 易于测试和维护

**限制：**

- 无法检查客户在发送前是否自行转化
- 无法合并时间延迟的条件逻辑
- 如果事件频繁发生而没有频率管理，则可能会生成不必要的消息

**Experience League：**

- [创建旅程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)

### 选项B：等待的条件性事件触发消息

**最佳选择：**&#x200B;延迟、有条件的响应，客户应在收到消息之前有时间自行转化 — 放弃购买（等待1-4个小时，然后检查是否仍然放弃购买）、浏览放弃购买（等待24个小时，检查是否购买了）、试用到期（等到过期日期临近）。

**工作方式：**

历程侦听符合条件的事件，进入用户档案，并引入评估条件之前的等待期。 在等待之后，条件节点检查客户是否已自转化（例如，完成购买、续订订阅）或者原始上下文是否仍然有效。 仅当满足条件时（例如，购物车仍被放弃），历程才会继续进行消息投放。

历程画布包含事件进入节点、等待节点（可配置的持续时间或特定日期/时间）、检查转化事件或配置文件状态变化的条件节点、分支路径（发送消息与退出而不发送）、限定路径上的消息操作节点以及每个分支上的结束节点。 退出标准可以配置为在转化事件发生在等待期间时自动从历程中删除配置文件，而无需进行显式条件检查。

这种方法通过让客户有时间自行转化、改善客户体验并提高所发送消息的感知相关性来减少不必要的消息传送。

**关键注意事项：**

- 等待时间显着影响转化率 — 较短的等待（1-2个小时）产生更高的紧急程度，但发送更不必要；较长的等待（24-48个小时）会减少数量，但可能会错过相关窗口
- 条件评估要求在AEP中捕获转化事件并与同一配置文件标识关联
- 退出标准为转化检查提供了更干净的替代显式条件节点
- 重新进入规则必须考虑等待期 — 配置文件在等待期间不应重新进入历程

**优点：**

- 通过检查自转化减少不必要的消息传送
- 产生更高质量、更相关的通信
- 通过可配置的延迟窗口支持时效性用例
- 退出标准在转化时启用自动删除历程

**限制：**

- 通过等待和条件节点增加历程复杂性
- 在等待期间，用户档案会占用历程版块（以91天的历程超时为准）
- 要求在等待窗口内将转化事件摄取到AEP中，以便准确评估条件
- 与选项A相比，交付时间更长

**Experience League：**

- [等待活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [条件活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [退出标准](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### 选项C：使用频率管理触发的事件

**最适合：**&#x200B;关注消息疲劳的高频事件源 — 页面查看次数、产品查看次数、搜索查询、重复购物车添加。 可以作为叠加应用于选项A或选项B的顶部。

**工作方式：**

此选项将频率管理添加到选项A或选项B中，以防止过度发送消息。 高频行为事件（如产品查看或重复的购物车添加）可能会在短时间内多次触发历程。 如果没有频率管理，用户档案可能会收到重复或过多的消息。

频率治理通过两个互补机制实现：AJO业务规则（频率上限），该规则限制用户档案每个时段每个渠道接收的消息数；以及旅程级别的重新进入规则，该规则定义用户档案可以重新进入同一旅程之前的冷却时段。 业务规则在组织级别运行，并对所有营销活动和历程强制实施上限（例如，每周最多3封电子邮件），而重新进入冷却在个人历程级别运行（例如，用户档案无法在上次进入的72小时内重新进入此特定历程）。

此外，可以配置冲突和优先级管理为触发的历程分配优先级得分，确保当多个历程或营销活动争夺同一用户档案时，优先级最高的通信优先。

**关键注意事项：**

- 频度上限必须在防止疲劳和确保投放重要触发消息之间取得平衡
- 建议使用特定于渠道的上限 — 电子邮件、短信和推送具有不同的疲劳阈值
- 历程重新进入冷却系统和组织级别的频度上限可协同工作；这两种系统都应进行配置
- 优先级分数确定达到上限时哪种通信优先 — 应为优先级较高的历程分配更高的分数

**优点：**

- 防止来自高频事件源的消息疲劳
- 维护品牌声誉和用户满意度
- 组织级别的上限可为所有营销活动和历程提供安全网
- 优先级评分确保在达到上限时发送最重要的消息

**限制：**

- 某些符合条件的用户档案将被禁止，可能缺少相关消息
- 频度上限配置增加了管理复杂性
- 大写可能会与其他活动的营销活动和共享同一渠道的历程意外交互
- 随着报文传送组合的变化，需要持续监控和调整

**Experience League：**

- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [业务规则概述](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [优先级分数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [历程条目管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)

### 选项比较

下表比较了三个实施选项（基于主要标准）。

| 标准 | 选项A：简单事件触发 | 选项B：有条件且等待 | 选项C：频率管理 |
| --- | --- | --- | --- |
| 最适合 | 即时确认、确认 | 放弃恢复，延迟的条件响应 | 高频事件源，多历程环境 |
| 复杂性 | 低 | 中 | Medium — 高（添加到A或B） |
| 消息延迟 | 几秒到几分钟 | 分钟到小时/天（可配置的等待） | 与相关购股权（A或B）相同 |
| 自转化检查 | 否 | 是（通过条件或退出条件） | 取决于基本期权 |
| 频率保护 | 无（除非与C组合） | 无（除非与C组合） | 是 — 渠道上限和再次进入冷却 |
| 历程画布节点 | 3-4（事件、可选条件、操作、结束） | 5-7（事件、等待、条件、分支、操作、结束） | 与A或B相同，以及业务规则配置 |
| 需要 | 事件架构、渠道界面、消息内容 | 所有选项A +转化事件摄取 | 全部选项A或B +频率规则配置 |

### 选择正确的选项

使用以下决策指南选择正确的实施选项。

1. **是否需要立即发送消息而不延迟？** 如果是，则从&#x200B;**选项A**&#x200B;开始。确认消息、欢迎电子邮件和确认通常不需要等待时间。

2. **客户在收到邮件之前是否有时间自行转换？** 如果是，请选择&#x200B;**选项B**。购物车放弃、浏览放弃和试用到期用例受益于允许客户自行完成操作的等待期。

3. **触发事件是否为高频（同一配置文件每个会话或每天发生多次）？** 如果是，请将&#x200B;**选项C**&#x200B;添加为选项A或B的叠加图。产品查看、页面查看和搜索事件可能会生成大量需要频率保护的触发器。

4. **沙盒中是否有多个触发的历程和营销活动处于活动状态？** 如果是，无论事件频率如何，都添加&#x200B;**选项C**&#x200B;以管理跨历程通信负载并防止渠道疲劳。

实际上，大多数生产实施都使用选项B + C作为放弃式用例（具有频率治理的条件等待）和选项A + C作为确认式用例（具有频率治理的立即发送作为安全网）。

## 实施阶段

以下阶段将逐步介绍事件触发的消息传送的端到端实施。

### 阶段1：配置事件模式和数据收集

**应用程序函数：** AEP：数据建模(F2)，AEP：数据源和集合(F3)

**您将配置的内容：**&#x200B;捕获触发事件的XDM ExperienceEvent架构、存储这些事件的数据集以及将事件流式传输到AEP的实时数据收集管道（Web SDK、Mobile SDK或服务器API）。 此阶段建立了历程将侦听的数据基础。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决策：正在触发事件类型**
>
>什么事件会触发消息？ 事件类型确定所需的架构字段和收集方法。
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| Commerce事件（购物车添加、购买、结账） | 电子商务用例 — 放弃购买、购买后 | 需要包含`productListItems`、`cart`和`order`字段的Commerce字段组 |
>| Web交互事件（页面查看、产品查看） | 浏览放弃，内容参与触发器 | 需要包含`webPageDetails`、`webInteraction`字段的Web详细信息字段组 |
>| 应用程序事件（应用程序安装、卸载、应用程序内操作） | 移动参与触发器 | 需要Mobile SDK实施和应用程序字段组 |
>| 系统事件（付款失败、订阅更改、状态更新） | 运行通知 | 需要服务器端API或源连接器来摄取系统事件 |
>| 表单提交事件 | 商机开发、注册确认 | 需要自定义字段组来捕获表单数据字段 |

>[!NOTE]
>
>**决策：收集方法**
>
>如何捕获触发事件并将其流式传输到AEP？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| Web SDK | 基于Web的行为事件（购物车添加、页面查看、表单提交） | 需要在网站上安装Web SDK；事件通过Edge Network实时流式传输 |
>| Mobile SDK | 移动应用程序事件（应用程序打开、应用程序内操作、推送令牌注册） | 需要在本机应用程序或React Native包装器中集成Mobile SDK |
>| Edge Network服务器API | 服务器端系统事件（支付处理、订阅管理、后端触发器） | 无客户端依赖关系；从组织的后端系统发送的事件 |
>| Source连接器 | 来自外部系统的事件（CRM、营销自动化、旧版平台） | 通常基于批处理；可能不支持实时触发，除非支持流式传输 |

**UI导航：**&#x200B;数据收集>数据流>新建数据流（用于数据流设置）；架构>创建架构（用于事件架构）；数据集>从架构创建数据集（用于数据集创建）

**密钥配置详细信息：**

- 事件架构必须包含历程条件评估和消息个性化所需的所有字段
- 数据流必须同时启用[!DNL Adobe Experience Platform]和[!DNL Adobe Journey Optimizer]服务
- 必须为实时客户配置文件启用数据集，以便事件与统一配置文件关联
- 事件数据必须包含可解析为已知配置文件的标识字段（电子邮件、CRM ID、ECID）

**Experience League文档：**

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Edge Network Server API概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [流式摄取概述](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### 阶段2：配置标识和配置文件

**应用程序函数：** AEP：标识和配置文件配置(F4)

**您将配置哪些内容：**&#x200B;触发事件上标识符的身份命名空间、事件架构上指定的主要身份、跨设备解析的身份链接规则以及配置文件统一的合并策略。 这可确保触发事件与统一的客户个人资料关联，以便历程能够解决联系人信息并投放消息。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决策：事件架构**&#x200B;的主要标识
>
>触发事件上的哪个标识字段应作为配置文件解析的主要标识？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 电子邮件地址 | 来自已验证Web会话或捕获电子邮件的表单的事件 | 直接解析可接触的身份；发送电子邮件的最简单途径 |
>| CRM ID | 来自CRM ID是主要标识符的经过身份验证系统的事件 | 需要创建CRM ID命名空间；用户档案必须具有链接的电子邮件或电话才能投放消息 |
>| ECID (Experience Cloud ID) | 无身份验证身份可用的匿名Web或应用程序事件 | 需要身份拼接以将ECID链接到已知身份；消息无法单独发送到ECID |
>| 电话号码 | 来自移动或呼叫中心交互的事件 | 支持短信投放；需要电话命名空间 |

**UI导航：**&#x200B;身份>创建身份命名空间；架构>选择架构>选择字段>身份>设置为主身份；配置文件>合并策略

**密钥配置详细信息：**

- 在ECID通过身份图链接到已知的可接触身份（电子邮件、电话）之前，匿名事件（仅限ECID）无法触发消息投放
- AJO使用的合并策略必须与用于受众评估的合并策略一致
- 对于基于Web的触发消息传递，请确保身份图通过登录事件将ECID链接到经过身份验证的身份

**Experience League文档：**

- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [身份标识图链接规则](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### 阶段3：设置渠道平面

**应用程序函数：** AJO：渠道配置

**您将配置的内容：**&#x200B;为触发的消息定义发送基础结构的渠道界面（预设） — 子域委派、IP池、发件人身份、回复地址、取消订阅处理和特定于渠道的凭据（SMS提供程序、推送证书）。 在创建消息内容或发布历程之前，必须存在有效的渠道平面。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决定：消息频道**
>
>触发的消息将使用哪个渠道？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 电子邮件 | 最触发的报文传送使用案例 — 放弃恢复、确认、入门 | 需要子域委派、IP池、发件人配置；支持丰富的HTML内容和个性化 |
>| 短信 | 时效性强的通知、简洁的警报、短信参与度高的受众 | 需要短信提供商集成(Sinch、Twilio、Infobip)；受字符限制和更严格的同意要求的约束 |
>| 推送通知 | 移动应用程序参与度，应用程序用户的重新参与度 | 需要推送凭据配置（iOS的APN、Android的FCM）；用户必须安装已启用推送的应用程序 |
>| 多个渠道 | 使用渠道偏好设置或回退逻辑的综合参与策略 | 需要多个渠道平面；可通过历程条件节点管理渠道选择 |

>[!NOTE]
>
>**决定：子域委派方法（电子邮件）**
>
>如何将电子邮件发送子域委派给Adobe？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 完全委派 | 组织希望Adobe管理发送子域的所有DNS记录 | 设置最简单；Adobe会自动管理SPF、DKIM、DMARC记录 |
>| CNAME委派 | 组织希望在指向Adobe基础架构时保持DNS控制 | 需要手动DNS记录管理；提供对DNS的更多组织控制 |

**UI导航：**&#x200B;管理>渠道>子域（用于子域设置）；管理>渠道> IP池（用于IP池配置）；管理>渠道>渠道表面>创建表面（用于表面创建）

**密钥配置详细信息：**

- 子域验证和DNS传播最多可能需要48小时
- 新的IP池需要预热计划（卷逐渐增加2-4周）
- 配置一键式list-unsubscribe标头以实现电子邮件合规性
- 对于短信，请在创建短信渠道表面之前配置提供商凭据
- 对于推送，请在创建推送渠道表面之前配置APN和FCM凭据

**Experience League文档：**

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [创建 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [设置渠道平面](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 阶段4：创建消息内容

**应用程序函数：** AJO：消息创作

**您将配置的内容：**&#x200B;历程将投放的消息内容，包括布局设计、使用配置文件和事件属性的个性化令牌、条件内容块、可重用片段（页眉、页脚、法律免责声明）以及内容预览和测试。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决策：内容方法**
>
>应如何创建消息内容？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 从现有模板开始 | 存在组织模板且需要品牌一致性 | 内容创建的最快路径；确保品牌合规性；模板更改传播到新消息中 |
>| 在电子邮件Designer中从头开始设计 | 此特定触发消息所需的自定义布局 | 完全的创意控制；拖放式可视化编辑器；速度较慢但更灵活 |
>| 导入HTML | 内容由外部团队或机构设计，并以HTML的形式提供 | 需要HTML编码专业知识；可能无法完全支持所有Email Designer功能 |

>[!NOTE]
>
>**决定：事件个性化**
>
>消息内容中应该使用哪些事件数据？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 事件上下文属性 | 消息应包括触发事件的详细信息（产品名称、购物车值、表单字段） | 在个性化编辑器中使用上下文事件属性；数据来自触发事件有效负载 |
>| 轮廓属性 | 消息应包括用户档案级别的数据（名字、忠诚度级别、位置） | 通过XDM路径使用配置文件属性（例如，`profile.person.name.firstName`）；数据来自统一配置文件 |
>| 事件和配置文件属性 | 消息应将事件上下文与用户档案个性化相结合 | 针对触发消息的最常见方法；确保相关性（事件）和个性化（用户档案） |

**UI导航：**&#x200B;内容管理>内容模板>浏览（用于模板选择）；促销活动或历程操作>编辑内容>向Designer发送电子邮件（用于内容设计）；选择文本组件> Personalization图标（用于添加个性化）

**密钥配置详细信息：**

- 使用上下文属性通过触发事件的数据（例如，产品名称、购物车值）进行个性化
- 将配置文件属性用于名称、偏好设置和忠诚度数据
- 配置条件内容块以按配置文件区段或属性更改内容（例如，针对忠诚度成员使用不同的CTA）
- 为在触发的消息之间共享的页眉、页脚和法律免责声明创建可重用片段
- 使用多个测试配置文件预览，以验证个性化正确呈现
- 在发布历程之前向内部利益相关者发送验证

**Experience League文档：**

- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 阶段5：创建和配置旅程

**应用程序功能：** AJO：Journey Orchestration、AJO：频率和业务规则（选项C）、AJO：冲突和优先级管理

**要配置的内容：**&#x200B;侦听触发事件并协调消息投放的历程。 这是核心实施阶段，其中设计历程画布的事件进入节点、条件节点、等待步骤（对于选项B）、消息操作节点和退出标准。 此阶段还包括频率管理（选项C）和冲突/优先级配置。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决定：重新进入规则**
>
>如果触发事件再次发生，配置文件能否重新进入此历程？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 允许再次进入（带冷却） | 该事件可以合法地重复发生，并且每次发生均需要发送消息（例如，每个购物车放弃都应触发恢复消息） | 设置一个冷却周期（至少5分钟）以防止重复事件快速重新进入；通常冷却的时间范围为1小时到72小时 |
>| 不重新进入 | 每个用户档案只应发送一次消息，而不管事件是否重复（例如，首次注册后的欢迎消息） | 用户档案会在首次历程完成后永久排除；适用于一次性生命周期消息 |

>[!NOTE]
>
>**决定：等待持续时间（仅限选项B）**
>
>历程应等待多长时间才能评估条件并发送消息？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 短等待（1-4小时） | 紧急使用案例，如放弃购买，即时跟进有效 | 报文量较高；可能会遇到一些自转换者；最适合高价值购物车恢复 |
>| Medium等待（12-24小时） | 中等紧急用例，如浏览放弃或内容参与 | 平衡的方法；减少不必要的发送，同时保持相关性 |
>| 长等待（2-7天） | 低紧急使用案例，如试用到期提醒或定期签到 | 报文数量减少；丧失情境关联性的风险提高 |
>| 自定义日期/时间 | 与特定日期绑定的用例（例如，在审判到期日期前3天发送） | 等到计算的日期/时间；使用自定义表达式编辑器 |

>[!NOTE]
>
>**决定：退出条件**
>
>在什么条件下，应在达到消息操作之前从历程中删除用户档案？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 转化事件（例如，购买已完成） | 目标为转化的购物车或浏览放弃情况 | 检测到转化事件时，配置文件会自动退出；最干净的方法是选择选项B |
>| 受众会员资格更改 | 如果用户离开符合条件的区段，则配置文件应退出 | 需要近乎实时更新的流评估受众 |
>| 历程超时（最长91天） | 默认行为 — 配置文件在最大历程持续时间后退出 | 安全网；不应是短期触发的历程的主要退出机制 |
>| 没有明确的退出条件 | 简单确认（选项A），每个符合条件的用户档案都应收到消息 | 用户档案在消息操作和结束节点后自然退出 |

>[!NOTE]
>
>**决定：频率管理（选项C）**
>
>每个时间段应接收多少条触发的消息？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 特定于渠道的上限（例如，每周3封电子邮件，每天1条短信） | 不同的渠道具有不同的疲劳阈值 | 推荐的方法；尊重每个渠道的入侵级别 |
>| 全球上限（例如，所有渠道每周5条报文） | 简化所有通信类型的治理 | 更易于管理，但更少细节；可能会过度限制侵入性较小的渠道 |
>| 仅历程级重新进入冷却 | 此特定历程所需的频率治理，但不适用于整个组织 | 实施最简单；无法防止跨历程疲劳 |

**UI导航：**&#x200B;历程>创建历程（用于旅程创建）；历程画布>拖动事件活动（用于事件输入）；历程画布>拖动“等待”活动（用于等待配置）；历程画布>拖动“条件”活动（用于条件分支）；历程属性>退出标准（用于退出配置）；管理>业务规则>创建规则（用于频率上限）

**密钥配置详细信息：**

- 通过选择事件模式并定义符合条件条件来配置历程事件
- 对于选项B，在事件条目之后以及任何条件评估之前立即添加等待节点
- 使用配置文件属性、事件数据或受众成员资格检查配置条件节点
- 将消息操作节点链接到渠道界面，并创作第3阶段和第4阶段的内容
- 将历程超时设置为适当的持续时间（对于触发的历程，不超过91天）
- 对于选项C，在发布历程之前通过管理>业务规则创建频率规则
- 如果其他营销活动或历程针对重叠受众，则为历程分配优先级分数

**选项差异的位置：**

选项A的&#x200B;**（简单事件触发）：**
历程画布最小：事件条目>可选同意/资格条件>消息操作>结束。 无等待步骤或转换检查。 根据事件是否应在每次发生时生成消息设置重新进入规则。

选项B的&#x200B;**条件（等待条件）：**
在事件输入后添加等待节点。 等待后，添加条件节点以检查转化（例如，检查历程进入后是否发生了`commerce.purchases`事件）或使用退出条件自动删除转换后的配置文件。 分支到“未转换”路径上的消息操作以及“已转换”路径上的结束节点。

选项C （频率管理）的&#x200B;**：**
在发布之前，通过“管理” > “业务规则”配置组织级别的频度上限。 在历程属性中设置历程级别的重新进入冷却。 或者，通过历程属性分配优先级分数，以控制达到上限时哪种通信优先。 这可以在选项A或选项B之上应用。

**Experience League文档：**

- [创建旅程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [历程属性](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [条件活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在历程中添加消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [退出标准](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [历程条目管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [优先级分数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [识别潜在冲突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### 阶段6：测试和部署历程

**应用程序函数：** AJO： Journey Orchestration

**您将配置的内容：**&#x200B;测试模式验证以验证历程在测试配置文件中的运行情况，然后发布历程以使其上线。

**UI导航：**&#x200B;历程画布>测试模式切换（用于测试）；历程画布>发布（用于部署）

**密钥配置详细信息：**

- 在历程画布上启用测试模式以使用测试配置文件模拟事件触发器
- 选择具有有效渠道联系信息（电子邮件地址、电话号码）的测试配置文件
- 触发测试事件并验证测试配置文件是否遍历预期路径
- 对于选项B，验证等待步骤的行为是否正确，以及条件评估是否生成预期的分支
- 验证个性化令牌在测试消息中是否正确呈现
- 成功测试后，发布历程以使其上线
- 监测发布后的历程状态和初始用户档案条目量度

**Experience League文档：**

- [测试您的历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [发布历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### 阶段7：监控和报告性能

**应用程序功能：** AJO： Reporting &amp; Performance Analysis， S4： Monitoring &amp; Observability， S5： Reporting &amp; Analysis

**您将配置的内容：**&#x200B;用于投放和参与监视的实时和历史历程报告，用于事件摄取和历程处理失败的平台警报，以及可选的CJA工作区，用于更深入的跨渠道分析触发的消息传递效率。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决策：报告深度**
>
>此用例需要多少报告分析？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 仅限AJO本机报表 | 对投放量度的运行监控就足够了 | 立即可用；封面已发送、已投放、已退回、已打开、已单击；无需其他配置 |
>| AJO本机+ CJA集成 | 需要跨渠道分析、转化归因和趋势分析 | 需要与CJA数据集关联的AJO连接和数据视图；提供更深入的分析功能 |

**UI导航：**&#x200B;历程>选择历程>实时报告（适用于实时监控）；历程>选择历程>所有时间报告（适用于历史分析）；警报>警报规则>订阅（适用于警报配置）

**密钥配置详细信息：**

- 在活动执行期间访问历程实时报告，以监控用户档案条目、退出和交付量度
- 在历程处于活动状态足够长的时间来累积有意义的数据后，查看历史报表
- 为源流运行失败（事件摄取）和历程处理延迟配置警报
- 对于CJA集成，请确保CJA连接包含AJO体验事件数据集（消息反馈事件数据集、电子邮件跟踪体验事件数据集）

**Experience League文档：**

- [历程实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## 实施注意事项

本节介绍事件触发的消息传递实施的护栏、常见隐患、最佳实践和权衡决策。

### 护栏和限制

以下平台护栏和限制适用于事件触发的消息传递实施。

- **单一事件吞吐量：**&#x200B;单一事件历程的每个沙盒每秒最多5,000个事件 — [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- **实时历程限制：**&#x200B;每个沙盒最多500个实时历程 — [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- **历程画布限制：**&#x200B;每个历程画布最多50个活动
- **历程超时：**&#x200B;最长历程持续时间为91天（全局超时）
- **重新进入冷却：**&#x200B;最小重新进入冷却为5分钟
- **频率上限配置：**&#x200B;每个沙盒最多10个上限配置
- **渠道表面：**&#x200B;每个沙盒每个渠道类型最多10个渠道表面
- **流式引入：**&#x200B;每个HTTP连接每秒最多20,000条记录 — [引入护栏](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- **计算属性：**&#x200B;每个沙盒最多25个计算属性 — [计算属性护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview#guardrails)
- **内容片段：**&#x200B;每条消息最多30个内容片段
- **实时报告刷新：**&#x200B;实时报告每60秒刷新一次，并显示过去24小时的数据
- **历史报告延迟：**&#x200B;执行结束后，可能需要长达2小时才能完全填充历史（所有时间）报告

### 常见陷阱

实施事件触发的消息传递时，请注意以下常见问题。

- **没有身份解析的匿名事件：**&#x200B;触发事件时，仅带有ECID（匿名Cookie ID）无法解析为可联系的用户档案以进行消息传递。 确保触发事件包含经过身份验证的身份或身份图将ECID链接到已知联系人。 如果没有身份解析，用户档案会进入历程，但在消息投放步骤失败。

- **缺少选项B条件检查的转换事件：**&#x200B;如果转换事件（例如，购买）未摄取到AEP或与触发事件相同的配置文件标识没有关联，则条件检查将错误评估为“未转换”，并发送不必要的消息。 验证转化事件是否实时流入AEP并与触发的事件共享身份。

- **过于宽松的重新进入规则：**&#x200B;允许高频事件源在不设置冷却期的情况下重新进入，可能会导致同一配置文件在几分钟内收到多封邮件。 始终设置与业务上下文匹配的重新进入冷却（例如，4小时冷却以放弃购买，24小时冷却以放弃浏览）。

- **等待步骤时区未对齐：**&#x200B;默认情况下在UTC中处理等待步骤。 如果历程定向了跨多个时区的用户档案，并且等待应与收件人的本地时间一致，请相应地配置历程的时区设置。

- **频率上限与其他营销活动冲突：**&#x200B;组织级别的频率上限适用于所有营销活动和历程。 如果配置文件已从其他活动营销活动中达到上限，则可能会禁止新的触发历程。 监测禁止率并调整优先级分数，以确保重要触发消息获得优先顺序。

- **由于缺少依赖项导致历程发布失败：**&#x200B;历程画布中的每个分支都必须以结束活动终止。 所有操作节点必须引用具有活动消息内容的有效渠道平面。 请在发布之前验证所有依赖项。

### 最佳实践

对于成功实施事件触发的消息传递，请遵循这些建议。

- **开始简单，然后迭代：**&#x200B;对于新的触发消息传递用例，从选项A开始。 仅在验证事件管道和消息投放之后添加等待和条件逻辑（选项B）。 当多个触发的历程处于活动状态时，添加频率治理（选项C）。

- **使用退出条件而不是条件节点进行转化检查：**&#x200B;退出条件会在发生符合条件的事件（例如，购买）时自动从历程中删除配置文件，从而消除在等待步骤后需要显式条件节点的必要。 这会生成更干净的历程画布和更响应式转化检测。

- **在开发沙盒中使用实际事件数据进行测试：**&#x200B;将测试模式与实际事件负载（不仅仅是测试配置文件）结合使用，以验证事件架构字段、个性化令牌和条件表达式是否可与类似生产的数据一起正常工作。

- **设置特定于事件的重新进入冷却：**&#x200B;将冷却期间与触发事件的业务上下文相匹配。 购物车放弃历程通常使用4-24小时冷却；确认历程可能允许立即重新进入；载入历程应完全阻止重新进入。

- **将禁止显示率监测为运行状况量度：**&#x200B;如果禁止显示率（用户档案符合条件但因频率上限或条件而无法接收消息）超过30-40%，请检查上限是否过于严格，或者触发事件的定义是否过于宽泛。

- **版本历程而不是编辑实时历程：**&#x200B;无法直接编辑实时历程。 通过复制历程、进行更改，然后停止旧版本并发布新版本来创建新版本。 这可避免中断历程中的当前配置文件。

- **在条件节点中包含回退/默认路径：**&#x200B;始终在条件节点中配置默认(else)路径以处理意外的配置文件状态。 与任何条件分支都不匹配的配置文件应正常退出，而不是继续卡住。

### 权衡决定

在设计事件触发的报文传送实施时，请考虑以下取舍。

>[!NOTE]
>
>**取舍：邮件速度与邮件相关性**
>
>即时消息投放（选项A）可最大限度地提高速度，但可能会将消息发送给可以自行转化的客户。 延迟条件投放（选项B）通过筛选掉自转化器来提高相关性，但会引入延迟，这可能会降低紧迫性。
>
>- **选项A支持：**&#x200B;快速、简单、确认式用例，每个事件都需要消息
>- **选项B支持：**&#x200B;相关性、减少消息疲劳、丢弃型使用案例（自转化很常见）
>- **建议：**&#x200B;将选项A用于速度为主值的事务型消息和确认消息。 对于相关性超出速度的恢复和重新参与消息，请使用选项B。 试验等待时间以找到每个用例的最佳平衡。

>[!NOTE]
>
>**取舍：频率保护与消息覆盖率**
>
>严格的频率限制（选项C）可防止疲劳，但在用户档案接近其上限时可能会禁止显示重要的触发消息。 允许或未设置上限可最大限度地扩大覆盖范围，但存在过度发送消息和渠道疲劳的风险。
>
>- **严格的限制优先：**&#x200B;客户体验、品牌声誉、可投放性（垃圾邮件投诉较少）
>- **允许大写字母优先：**&#x200B;消息覆盖率，转换机会，避免错过的触发器
>- **推荐：**&#x200B;从行业标准上限（每周3-5封电子邮件、每周1-2个短信、每周2-3个推送/天）开始，并根据参与量度和取消订阅率进行调整。 为触发的消息分配更高的优先级分数，以便在达到上限时战胜批量活动。

>[!NOTE]
>
>**取舍：历程简单与历程复杂**
>
>简单的历程（少数节点，无分支）更易于构建、测试和维护，但提供的上下文适应有限。 复杂的历程（多个条件、分支路径、区段检查）支持更细致的响应，但会增加复杂性和错误风险。
>
>- **简单的历程有好处：**&#x200B;实施更快、调试更容易、维护负担更轻
>- **精致的历程大受欢迎：**&#x200B;更精确的定位、更好的个性化、减少不必要的发送
>- **推荐：**&#x200B;从满足业务要求的最简单历程开始。 根据性能数据递增复杂性。 可靠工作的简单历程比未检测到错误的复杂历程更有价值。

## 相关文档

以下资源提供了有关此实施中使用的功能的更多详细信息。

### 历程编排

- [历程入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [创建旅程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [历程属性](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [受众鉴定事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [条件活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在历程中添加消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [退出标准](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [历程条目管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [测试您的历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [发布历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

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
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [辅助函数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [创建短信消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [设计推送通知](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### 频率和业务规则

- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [业务规则概述](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [API上限](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/channel-surfaces/capping)

### 冲突和优先级管理

- [冲突和优先级管理入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [识别潜在冲突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [优先级分数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [历程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### 报告和性能

- [历程实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### 数据收集和摄取

- [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [移动SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Edge Network Server API概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [流式摄取概述](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### 数据建模和架构

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### 身份和配置文件

- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [身份标识图链接规则](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [配置文件概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### 分段和受众

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### 数据治理和同意

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [同意和偏好设置字段组](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### 计算属性

- [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [计算属性UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

### 监控和可观察性

- [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### 护栏

- [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [摄取护栏](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### 教程和指南

- [创建历程教程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [安装Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
