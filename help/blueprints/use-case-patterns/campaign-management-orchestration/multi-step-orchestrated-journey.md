---
title: 多步协调历程
description: 了解如何在一段时间内通过分支的多点接触历程引导用户档案，其中包含等待、条件和多个消息操作。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 5667b188-1b20-4a85-aebb-74efd5f771a1
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '8211'
ht-degree: 1%

---

# 多步编排历程

本指南为使用[!DNL Adobe Journey Optimizer] (AJO)和[!DNL Real-Time Customer Data Platform] (RT-CDP)构建多步骤编排的历程提供了全面的实施蓝图。 它专为需要编排随时间推移提供多种消息的分支和多点触控客户历程的解决方案架构师、营销技术人员和实施工程师而设计。

它提供了所有可行的实施选项、每个配置点的决策考虑以及指向[!DNL Adobe Experience League]文档的链接。 使用本指南来规划、配置和验证多步骤历程实施。

## 用例概述

多步骤编排的历程可处理单个消息不足以达到预期客户结果的业务情形。 该历程不是一次性发送，而是通过电子邮件、短信消息、推送通知或应用程序内消息等一系列接触点引导每个用户档案，这些接触点在几天或几周内间隔开，并根据用户档案属性、行为信号或事件数据调整路径的分支逻辑。

这些历程是AJO中最复杂的营销活动模式。 它们将基于受众或基于事件的进入与一组操作节点（消息）、条件节点（分支逻辑）、等待节点（时间延迟）和退出标准（转化事件或超时）相结合。 每个用户档案均以自己的速度独立完成历程，并在每个步骤接收与上下文相关的内容。

此模式包含更简单的模式 — 为单次发送营销活动批量激活出站消息，为单次事件响应使用事件触发的消息传递。 当用例需要随时间通过多次交互培养用户档案时，请使用此模式。

>[!NOTE]
>如果您的历程需要在各个决策点动态选择最佳优惠、内容或渠道，请参阅[具有决策的跨渠道历程](cross-channel-journey-with-decisioning.md)。 该模式通过AJO Decisioning集成扩展了这一模式。

## 主要业务目标

此用例模式支持以下业务目标。

### 提高客户维系率

透过价值导向型经验及持续培养关系，让现有客户持续参与及不断更新。

**KPI：**&#x200B;维系、客户存留期值、参与度

[了解有关提高客户维系率的更多信息](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### 改进客户入门

通过优化的个性化欢迎体验和激活历程，加快新客户的价值实现。

**KPI：**&#x200B;参与度、维系率、转化率

[详细了解如何改进客户入门](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)

### 重新吸引休眠客户

通过基于行为信号的有针对性的重新激活促销活动，吸引非活跃或失效的客户。

**KPI：**&#x200B;参与度、维系率、转化率

[了解有关提高客户维系率的更多信息](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### 恢复放弃的购物车和历程

通过及时、个性化的跟进，重新吸引在购买、申请或注册流程中放弃的用户。

**KPI：**&#x200B;转化率、递增收入、参与度

[了解有关回收废弃购物车和历程的更多信息](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)

## 战术用例示例

以下场景说明了多步编排历程模式的常见应用。

- **客户入门培训系列** — 欢迎电子邮件，随后是功能培训，然后在注册后的前14天内提供激活提示
- **重新参与滴注式营销活动** — 提醒电子邮件，然后是激励优惠，最后通知已过期客户超过3周
- **忠诚度里程碑历程** — 逐级升级通知，后跟独占优惠，然后在会员资格周年临近时提供续订提醒
- **回馈序列** — “我们想你”电子邮件，通过电子邮件提供折扣优惠，然后为失效购买者发送最终短信提醒
- **产品采用历程** — 试用欢迎、使用提示，然后随着试用期的进展提供升级提示
- **订阅续订序列** — 30天通知，7天提醒，然后为即将续订的订阅发送到期日消息
- **购买后培养** — 感谢电子邮件、使用方法指南、交叉销售推荐，然后在购买30天后提交审核请求

## 关键绩效指标

使用以下KPI衡量多步编排的历程实施的有效性。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 历程完成率 | 完成完整历程且未提前退出的用户档案的百分比 | 历程报表：已退出（完成）/已输入 |
| 步骤转化率 | 从一个步骤进展到下一个步骤的配置文件百分比 | 历程报告中的按节点量度 |
| 渠道参与率 | 每个接触点的打开率、点进率和响应率 | 每消息投放和参与量度 |
| 退出条件转化率 | 在历程超时前触发退出事件（例如，购买、注册）的配置文件百分比 | 退出条件命中计数/输入的总数 |
| 转化时间 | 从历程进入到退出标准事件的平均持续时间 | 历程分析：从条目时间戳到转化事件时间戳 |
| 历程流失率 | 在每个步骤停止参与的用户档案百分比（流失分析） | 跨历程步骤的CJA流失可视化图表 |
| 保留/重新参与率 | 返回活动状态的目标用户档案的百分比 | CJA中的旅程后行为分析 |

## 用例模式

**多步骤编排历程**

随时间推移通过含等待、条件和多个消息操作的分支、多触点历程引导用户档案。

**函数链：**&#x200B;受众评估>历程执行（多节点）>条件分支>消息投放(xN) >退出条件>报表

## 应用程序

以下应用程序用于实现此用例模式。

- **[!DNL Adobe Journey Optimizer](AJO)** —历程编排引擎、消息创作、渠道配置、内容试验、频度和冲突管理以及报告
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — 历程进入受众的受众评估和定义、个性化的配置文件数据和条件分支
- **[!DNL Adobe Experience Platform](AEP)** — 配置文件存储、身份服务、事件数据摄取和基础数据基础架构

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本函数 | 状态 | 必须准备好的内容 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 假设就位 | 具有历程创建和发布权限的AJO沙盒。 必须配置历程中使用的所有渠道的渠道平面。 用户必须具有适当的角色（营销人员、历程管理员），并具有历程和营销活动权限。 | [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)，[访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | XDM配置文件架构具有用于跨多条消息进行条件分支和个性化的属性（例如，忠诚度级别、产品兴趣、参与度分数）。 用于促进退出标准和条件评估的转化事件的体验事件架构（例如，购买事件、表单提交）。 | [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| 数据源和收集 | 假设就位 | 如果退出标准或条件取决于实时事件（例如，退出历程的购买事件），则事件流必须处于活动状态。 分支中使用的配置文件属性的批量摄取。 用于行为事件收集的Web SDK或服务器端API。 | [流式摄取概述](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)，[源概述](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| 身份和配置文件配置 | 假设就位 | 用户档案必须在历程中使用的所有渠道（电子邮件、短信、推送）中可解析。 如果历程跨越Web和移动接触点，则必须配置跨设备身份。 必须为沙盒配置合并策略。 | [身份服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| 受众定义和分段 | 必填 | 必须为受众读取的历程定义进入受众。 区段还可以在条件节点中使用以进行分支。 评估方法（批量或流）必须与历程进入要求匹配。 | [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么它很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | 计算属性（例如参与度分数、上次活动后间隔天数或生命周期购买值）改进了条件分支逻辑，从而实现更智能的历程路径决策。 | [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 数据生命周期管理 | 推荐 | 历程事件数据保留应配置数据集过期策略，以管理存储并遵守数据保留法规。 同意执行可确保仅选择加入的用户档案在每个渠道接触点接收消息。 | [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)，[数据集过期时间](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| 数据使用标签和执行 | 推荐 | 治理标签可确保跨多个消息接触点的合规性个性化，在历程使用PII或敏感数据实现跨渠道个性化时尤其重要。 | [数据管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)，[数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview) |
| 监视和可观察性 | 已包含 | 历程执行监控有关处理失败、配置文件条目瓶颈和投放问题的警报。 对于延迟或故障会影响客户体验的生产历程至关重要。 | [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)，[可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 报告和分析 | 已包含 | CJA funnel和整个历程的流失分析比单独的AJO本机报表提供更深入的insight。 支持分步转化分析、同类群组比较和历程优化。 | [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)，[Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## 应用程序功能

此计划从“应用程序功能目录”中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Journey Optimizer] (AJO)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 渠道配置 | 阶段1：通道设置 | 为历程中的每个消息传送接触点配置渠道界面（电子邮件、短信、推送） |
| 消息创作 | 阶段2：创建消息内容 | 为每个历程操作节点使用个性化、动态内容和模板创作消息内容 |
| Journey Orchestration | 阶段3：历程设计和激活 | 设计包含进入、操作、条件、等待和退出节点的多步旅程画布；测试和发布 |
| 频度和业务规则 | 第4阶段：治理和优化 | 配置频度上限以防止在历程接触点和其他并发营销活动之间发送过度消息 |
| 冲突和优先级管理 | 第4阶段：治理和优化 | 为与其他活动通信竞争的历程分配优先级得分并配置冲突检测 |
| 内容试验 | 第4阶段：治理和优化 | 对历程操作节点中的消息内容运行A/B测试以优化性能 |
| 报告和性能分析 | 第5阶段：报告和监控 | 监测历程执行、每步交付量度和参与性能 |

### [!DNL Real-Time CDP] (RT-CDP)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 受众评估 | 阶段1：通道设置（先决条件） | 定义和评估受众读取历程的登入受众；定义分支的条件受众 |
| 同意和治理实施 | 第4阶段：治理和优化 | 在历程消息操作中强制实施同意首选项和数据使用策略 |

## 先决条件

在开始实施之前，请先完成以下先决条件。

- [ ] AJO沙盒已配置历程创建和发布权限
- [ ]至少一个渠道界面（电子邮件、短信或推送）已配置并处于活动状态
- [ ]配置文件架构包括条件分支和个性化所需的属性
- [ ] Experience Event架构配置为退出条件中使用的转化事件
- [ ]事件流对于在退出标准或事件触发的条目中使用的实时事件处于活动状态
- [ ]身份命名空间和合并策略配置为跨渠道配置文件解析
- [ 为每个消息接触点准备]内容资产（图像、副本、CTA）
- [ 定义并评估]进入受众（对于受众读取的历程）
- [ ]触发事件架构已配置（对于事件触发的历程）
- [ ]测试配置文件可用于历程测试模式验证
- [ ]禁止列表已审核并且是所用所有渠道的最新列表

## 实施选项

查看以下选项，确定多步编排历程的最佳方法。

### 选项A：受众读取的编排历程

**最适合：**&#x200B;基于时间的培养序列，其中已知受众进入历程并逐步通过计划的接触点 — 入门系列、续订序列、重新参与滴答、忠诚度里程碑历程。

**工作方式：**

在历程条目中读取受众，无论是一次性读取还是按定期计划。 所有符合条件的用户档案同时进入历程，然后按照自己的速度在画布中前进，并受等待持续时间和条件评估的控制。 每个用户档案在历程中的路径都是独立的 — 一些人可能采用“参与”分支，而其他人根据其行为或属性采用“未参与”分支。

在执行“读取受众”活动时评估受众。 对于定期历程，会在每次循环时重新评估受众，新的符合条件的用户档案将进入历程，而历程中已有的用户档案将继续其路径。 此方法提供了可预测的进入时间，非常适合于计划的生命周期计划。

**关键注意事项：**

- 必须在历程激活之前定义和评估受众
- 循环读取允许在每个周期输入新限定词
- 历程中的用户档案不会重新读取；只有新限定符会在后续读取时输入
- 对于受众读取的历程，等待步骤最小持续时间为1小时

**优点：**

- 可预测的入门时间安排与业务计划一致
- 支持大受众量（每秒最多20,000个配置文件默认限制）
- 易于对已知受众群体进行测试和监控
- 可以计划为定期进入（每天、每周、每月）

**限制：**

- 输入是基于批处理的，而不是实时的 — 用户档案在计划的读取时间输入，而不是在符合条件时输入
- 不适用于需要立即响应的行为启动的序列
- 对于历程中已有的用户档案，两次读取之间的受众更改不会反映出来

**Experience League：**

- [读取受众活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [创建旅程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### 选项B：事件触发的编排历程

**最适合：**&#x200B;实时事件开始历程的行为启动序列 — 购物车放弃升级、购买后培养、里程碑触发的忠诚度历程、试用激活序列。

**工作方式：**

单一事件（例如，购买、购物车放弃、表单提交或应用程序安装）会实时触发各个配置文件的历程进入。 收到事件后，用户档案进入历程，然后依次通过包含条件、等待和分支的接触点。 此方法将事件触发的消息传递的即时性与完整历程的多步编排结合使用。

必须将触发事件配置为旅程事件，并定义其架构和条件。 历程连续侦听事件，并在事件到达时逐个输入用户档案。 后续旅程节点可以评估用户档案的响应，以确定要遵循的分支。

**关键注意事项：**

- 需要实时事件流处于活动状态
- 必须精确配置事件架构和条件以避免错误触发器
- 重新进入规则是关键的 — 确定如果事件再次触发，配置文件是否可以重新进入
- 每个沙盒每秒最多支持5,000个事件

**优点：**

- 基于客户行为的实时输入 — 高度情境化
- 每个用户档案在事件发生时单独进入，而不是按计划进入
- 自然适合行为响应序列（放弃购买、购买后）
- 可与配置文件数据组合以在输入后进行个性化分支

**限制：**

- 需要建立流事件基础架构
- 事件架构配置和测试中的复杂性更高
- 每个事件输入一个配置文件 — 不适用于批量受众激活
- 调试需要跟踪各个配置文件历程

**Experience League：**

- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [受众鉴定事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)

### 选项C：多渠道编排历程

**最适合：**&#x200B;在每个接触点使用不同渠道的跨渠道序列 — 依次发送电子邮件、短信、推送提升，或发送电子邮件和应用程序内补充消息。 可以使用受众读取或事件触发的条目。

**工作方式：**

此选项通过在同一历程中合并多个消息传递渠道来扩展选项A或选项B。 历程中的每个操作节点都可以定位不同的渠道（电子邮件、短信、推送、应用程序内或Web），因此需要为每个渠道设置单独的渠道平面。 历程设计者在每个步骤中选择适当的渠道，启用提升模式（例如，先发送电子邮件，如果没有参与，则发送短信）或补充模式（例如，具有应用程序内强化的电子邮件）。

跨渠道历程需要使用的每个渠道的渠道平面，并且必须考虑特定于渠道的个性化、字符限制和选择加入要求。 条件节点可以检查与以前消息（例如，“已打开电子邮件？”）的参与情况 作为分支条件)来确定下一个渠道。

**关键注意事项：**

- 历程中使用的每个渠道需要活动的渠道平面
- 每个渠道都有不同的个性化功能和内容限制
- 必须按渠道验证同意 — 可以选择接收用户档案以发送电子邮件，但不选择接收短信
- 应配置特定于渠道的频度上限以防止跨渠道过度消息传送

**优点：**

- 通过让用户档案在其首选渠道中参与来最大程度地扩大访问范围
- 为无响应用户档案启用上报策略
- 支持跨渠道的补充性消息传送以实现强化
- 尽可能提供最完善的客户体验

**限制：**

- 最高的实施复杂性 — 需要为每个渠道进行配置
- 必须在每个接触点为每个渠道创作内容
- 跨渠道的同意和频率管理变得更加复杂
- 测试需要在所有渠道表面进行验证

**Experience League：**

- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 选项比较

下表比较了三个实施选项（基于主要标准）。

| 标准 | 选项A：受众已读 | 选项B：事件触发 | 选项C：多渠道 |
| --- | --- | --- | --- |
| 最适合 | 计划的生命周期计划，培养系列 | 行为响应序列，购物车放弃 | 跨渠道升级，补充性消息传递 |
| 进入计时 | 已计划（批次） | 实时（事件驱动） | 计划或实时 |
| 复杂性 | 中 | Medium — 高 | 高 |
| 条目数量 | 每秒最多20,000个配置文件 | 每秒最多5,000个事件 | 与底层输入方法相同 |
| 渠道范围 | 单个或多个渠道 | 单个或多个渠道 | 需要多个渠道 |
| 需要 | 定义的受众、评估计划 | 流事件基础架构 | 每个渠道的渠道表面 |
| 实时响应 | 否 — 批次条目 | 是 — 发生事件时立即 | 取决于输入方法 |

### 选择正确的选项

使用以下决策流选择正确的实施方法：

1. **历程是否由客户行为或事件启动？** 如果是，请选择&#x200B;**选项B** （事件触发）。 如果历程是由计划的受众读取启动的，请选择&#x200B;**选项A** （受众读取）。

2. **历程是否使用多个消息渠道（例如，电子邮件和短信）？** 如果是，请在输入方法选择（A或B）之上应用&#x200B;**选项C**（多渠道）。 如果历程在整个过程中使用单个渠道，则仅选项A或B就足够了。

3. **是否需要根据参与情况升级到其他渠道？** 如果是，请选择&#x200B;**选项C**，其条件节点检查与先前消息的参与情况并分支到备用渠道。

4. **是否提前知道受众并按计划处理？** 如果是，请选择&#x200B;**选项A**。如果用户档案在执行操作时应进入历程，请选择&#x200B;**选项B**。

## 实施阶段

以下阶段将指导您完成多步协调历程的端到端实施。

### 第1阶段：设置渠道并准备受众

**应用程序函数：** AJO：渠道配置，RT-CDP：受众评估

在设计历程之前，所有渠道表面都必须处于活动状态，并且必须定义和评估进入受众（适用于选项A）。 此阶段确保基础设施机构做好了消息传送的准备。

#### 确定每个接触点的渠道类型

历程将在每个接触点使用哪些消息传递渠道？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅电子邮件 | 历程仅通过电子邮件进行沟通（入门、培养） | 设置最简单；需要电子邮件子域和IP池；取决于收件箱的位置 |
| 仅短信 | 时效性警报、约会提醒 | 需要短信提供商凭据(Sinch、Twilio、Infobip)；每条消息的成本较高；选择退出规则更严格 |
| 仅推送 | 移动用户的应用程序内参与序列 | 需要APN/FCM凭据；用户必须已安装应用程序 |
| 多渠道 | 跨渠道的升级或补充性消息传递 | 需要每个渠道的渠道表面；最复杂但覆盖范围最高 |

#### 确定受众评估方法（选项A）

用户档案必须多久才符合进入受众的条件？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 批次评估 | 按计划（每天、每周）读取受众；无需实时输入 | 简单设置；在历程读取之前评估受众；支持复杂的区段规则 |
| 流式处理评估 | 随着属性的更改，配置文件应近乎实时地符合条件 | 区段规则表达式必须符合流式处理条件；近乎实时的条件 |

#### 确定子域委派方法（电子邮件渠道）

如何将电子邮件发送子域委派给Adobe？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 完全委派 | Adobe管理DNS记录；最简单的设置 | 配置速度最快；Adobe处理SPF、DKIM、DMARC |
| CNAME委派 | 组织保留DNS控制 | 需要DNS管理员参与；必须配置CNAME记录 |

#### UI导航

- 渠道曲面：“管理”>“渠道”>“渠道曲面”>“创建曲面”
- 子域：管理>渠道>子域
- 短信配置：管理>渠道>短信配置
- 推送配置：管理>渠道>推送通知设置
- 受众：客户>受众>创建受众>构建规则

#### 关键配置详细信息

- 验证电子邮件的IP池预热状态 — 新的IP池需要在2-4周内逐步进行预热计划
- 对于短信，请配置提供商凭据并验证发件人号码注册
- 对于推送，上传APNs证书和FCM服务器密钥
- 使用区段生成器定义进入受众，区段规则涵盖目标群体
- 在受众定义中包含禁止显示规则（排除最近转化的、全局取消订阅的）

#### 不同选项的位置

选项A的&#x200B;**（受众读取）：**
定义和评估进入受众。 确认受众具有非零群体。 确定历程将使用一次性受众读取还是定期读取计划。

选项B的&#x200B;**（事件触发）：**
验证触发事件架构是否已配置，以及事件是否已流式传输到平台。 无需预定义受众 — 用户档案在事件接收时单独输入。

选项C （多通道）的&#x200B;**：**
为历程中使用的每个渠道（电子邮件、短信、推送、应用程序内）配置渠道平面。 验证目标群体的每个渠道的同意状态。

#### Experience League文档

- [设置渠道平面](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [IP预热计划](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)


### 阶段2：创建消息内容

**应用程序函数：** AJO：消息创作

为历程中的每个接触点创作消息内容。 每个消息可能具有不同的内容、个性化深度和渠道。 此阶段将创建历程操作节点将引用的所有可交付结果内容。

#### 确定内容方法

每条消息应该从模板开始、从头开始设计还是导入HTML？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 现有内容模板 | 具有既定布局的品牌一致消息 | 最快；确保品牌合规性；模板必须存在并且与渠道类型匹配 |
| 从头开始设计 | 每个接触点的独特自定义布局 | 最灵活；构建时间更长；使用电子邮件Designer拖放 |
| 导入HTML | 通过外部设计工具预建HTML | 需要干净的HTML；可能需要调整响应能力 |

#### 决定个性化深度

每封邮件应包含多少个性化？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 基本令牌插入 | 名字、城市、简单配置文件属性 | 低复杂性；对XDM路径使用Handlebars语法 |
| 条件内容块 | 根据区段或属性显示的不同内容 | Medium复杂性；需要动态内容规则 |
| 历程上下文个性化 | 内容因历程路径、以前的交互而异 | 更高的复杂性；利用历程上下文变量和事件数据 |

#### 确定片段策略

是否应将共享的内容块（页眉、页脚、法律文本）创建为可重用片段？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 可重用片段 | 多条消息共享共同的元素；需要品牌一致性 | 更改会使用该片段传播到所有消息；每条消息最多包含30个片段 |
| 内嵌内容 | 具有独特布局的一次性消息 | 针对单一使用内容的速度更快；没有跨消息一致性优势 |

#### UI导航

- 内容管理>内容模板>浏览
- 向Designer发送电子邮件（在营销活动或历程操作中）
- 内容管理>片段>创建片段

#### 关键配置详细信息

- 为历程中的每个消息操作创作内容 — 四步历程可能需要4个不同的消息设计
- 使用引用XDM配置文件路径的个性化表达式（例如，`{{profile.person.name.firstName}}`）
- 为特定于区段的变量配置动态内容块
- 使用测试用户档案预览每封邮件以验证个性化呈现
- 向内部利益相关者发送验证以进行内容审查
- 对于短信，请遵守字符限制（标准GSM编码为160个字符）
- 对于推送，请配置标题、正文、图像和深层链接/URL操作

#### Experience League文档

- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [创建电子邮件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [创建短信消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [设计推送通知](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)
- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)


### 阶段3：设计和激活历程

**应用程序函数：** AJO： Journey Orchestration

设计包括进入节点、操作节点（消息）、条件节点（分支）、等待节点（时间延迟）和退出标准的多步旅程画布。 然后使用测试用户档案进行测试并发布。

#### 决定条目类型

用户档案应该如何进入历程？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 读取受众 | 计划培养序列；已知受众批量处理 | 在读取时评估受众；支持一次性或循环读取；每秒最多20,000个配置文件 |
| 单一事件 | 实时行为触发器（购买、购物车放弃） | 实时输入；需要事件流；每秒最多5,000个事件 |
| 受众资格 | 用户档案近乎实时地进入或退出受众时的进入 | 流式评估；由区段成员资格更改触发 |
| 业务事件 | 组织范围内的事件触发受众的历程 | 对于产品发布、天气事件、系统警报非常有用 |

#### 决定重新进入策略

用户档案在完成或退出后能否重新进入历程？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 允许重新进入（使用冷却） | 用户档案可能需要重复历程（定期购买、季节性重新参与） | 冷却时间最短为5分钟；防止在冷却窗口内出现重复条目 |
| 禁止重新进入 | 一次性历程（入门、单一生命周期事件） | 配置文件完成或退出历程，无法再次进入 |

#### 确定接触点之间的等待持续时间

历程应在每条消息之间等待多长时间？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 固定持续时间（例如3天） | 无论用户档案行为如何，步调都是一致的 | 简单；可预测的时间；受众阅读历程至少1小时 |
| 特定日期/时间 | 消息必须到达一个确切时间（例如，续订日期） | 使用配置文件属性或表达式来确定确切日期/时间 |
| 自定义表达式 | 基于用户档案数据或历程上下文的动态等待 | 非常灵活；需要表达式创作 |

#### 确定分支条件

什么条件决定了配置文件采用的路径？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 配置文件属性检查 | 根据忠诚度级别、产品兴趣和地理位置进行分支 | 使用评估时可用的配置文件数据 |
| 区段成员资格检查 | 根据配置文件是否属于特定受众进行分支 | 需要定义受众并评估 |
| 事件数据检查 | 根据用户档案是否执行了操作（已打开的电子邮件、已单击的链接）的分支 | 评估历程范围内的事件数据；对于基于参与的分支很有用 |
| 百分比拆分 | 跨路径随机分布用户档案（用于A/B测试或控制转出） | 不使用配置文件数据；纯随机分配 |

#### 确定退出条件

什么事件或条件会导致用户档案提早退出历程？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 转化事件 | 配置文件完成所需的操作（购买、注册、表单提交） | 需要事件流；最常见的退出条件 |
| 受众成员资格退出 | 配置文件将离开登录受众或加入排除受众 | 近乎实时地评估流受众 |
| 超时 | 已达到最大历程持续时间（最多91天） | 默认安全网；可在历程属性中配置 |
| 无退出条件 | 配置文件自然完成整个历程路径 | 最简单；除非手动删除，否则所有配置文件都会遍历整个历程 |

#### 确定历程超时

用户档案在历程中可以保留的最长时长是多少？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 91天（最长） | 长期历程（季度续订、扩展入门） | 允许的最大值；在超时时仍在历程中的配置文件会自动退出 |
| 自定义较短的持续时间 | 历程应在规定的时间范围（7天、14天、30天）内完成 | 根据用例的自然生命周期进行设置 |

#### UI导航

- 创建旅程：历程>创建历程
- 历程属性：历程画布>属性面板
- 进入节点：历程画布>拖动“读取受众”或事件活动
- 操作节点：历程画布>拖动渠道操作（电子邮件、短信、推送）
- 条件节点：历程画布>拖动“条件”活动
- 等待节点：历程画布>拖动“等待”活动
- 退出标准：历程属性>退出标准>配置
- 测试模式：历程画布>测试模式切换
- 发布：历程画布>发布

#### 关键配置详细信息

- 使用明确的描述性约定命名历程（例如，“Onboarding_Series_Email_v1”）
- 设置历程时区以进行一致的等待步骤处理
- 使用相应的渠道界面配置每个操作节点，并将其链接到创作的消息内容
- 每个分支必须以结束活动终止
- 配置适合用例的重新进入规则
- 对测试用户档案使用测试模式以在发布之前模拟完整历程路径
- 验证测试用户档案是否遍历预期路径并接收正确的消息

#### 不同选项的位置

选项A的&#x200B;**（受众读取）：**

- 将“读取受众”活动拖动为登入节点
- 选择阶段1中定义的目标受众
- （可选）配置定期读取计划（每天、每周）
- 如果担心下游系统负载，请配置读取速率限制

选项B的&#x200B;**（事件触发）：**

- 将触发事件拖动为登入节点
- 配置事件架构和进入条件
- 请仔细设置重新进入规则，以避免重复事件中重复输入

选项C （多通道）的&#x200B;**：**

- 使用选项A或B的录入方法
- 在每个操作节点上，为该接触点选择适当的渠道平面
- 在渠道之间添加条件节点以检查参与（例如，“配置文件是否打开了电子邮件？”） 和路由到备用通道

#### Experience League文档

- [创建旅程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [历程属性](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [读取受众活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [受众鉴定事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [在历程中添加消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [条件活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [退出标准](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [结束活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [历程条目管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [测试您的历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [发布历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)


### 阶段4：配置治理和优化

**应用程序功能：** AJO：频率和业务规则，AJO：冲突和优先级管理，AJO：内容试验，RT-CDP：同意和治理实施

应用频度上限以防止过度消息传送，分配用于解决与其他活动通信的冲突的优先级分数，可以选择在历程消息中配置A/B测试，以及验证同意实施。

#### 决定频率上限配置

历程消息是否应遵守全球频率上限？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 应用频率规则 | 历程与其他营销活动和历程一起运行；用户档案消息不应过于丰富 | 如果用户档案已经通过其他通信达到了上限，则可能会禁止发送消息 |
| 免除上限 | 历程消息至关重要，必须始终投放（事务性、法规性） | 请谨慎使用；如果过度使用，则可能导致消息疲劳 |

#### 决定优先级得分分配

此历程相对于其他活动营销活动和历程应该排位如何？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 高优先级(70-100) | 历程报文是关键的生命周期通信（入门、续订） | 当与其他通信发生冲突时，优先级别越高 |
| Medium优先级(30-69) | 历程信息很重要，但并不紧急（培养、教育） | 可能被较高优先级的通信抑制 |
| 低优先级(0-29) | 历程消息为补充或促销 | 与更高优先级的报文竞争时将被抑制 |

#### 决定内容试验

历程消息是否应包括A/B或多变量测试？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 是 — A/B测试 | 优化特定接触点上的主题行、CTA或内容布局 | 要求每个变体有足够的容量以实现统计意义；支持2-10个治疗方案 |
| 无试验 | 内容已最终确定或数量太低，无法进行有意义的测试 | 设置更简单；无需变量跟踪 |

#### UI导航

- 频率规则：管理>业务规则>创建规则
- 优先级分数：历程属性>优先级分数
- 冲突检测：管理>业务规则>冲突和优先级
- 内容体验：历程画布>选择消息操作>内容体验切换开关
- 同意政策：隐私>政策>同意政策

#### 关键配置详细信息

- 设置特定于渠道的频率上限（例如，每周最多3封电子邮件，每天最多1条短信，每天最多2次推送）
- 为历程分配一个优先级分数(0-100)，该分数反映历程相对于其他活动通信的业务重要性
- 查看冲突检测面板以识别任何重叠的活动或历程
- 如果运行内容实验，请定义处理变体、设置流量分配、选择成功量度（打开、点击或转化），并设置置信度阈值（通常为95%）
- 验证同意实施是否对历程中使用的每个渠道有效

#### Experience League文档

- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [业务规则概述](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [优先级分数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [识别潜在冲突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [历程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [内容体验入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)


### 阶段5：配置报告和监控

**应用程序功能：** AJO： Reporting &amp; Performance Analysis、Monitoring &amp; Observability、Reporting &amp; Analysis

在激活期间和之后监测历程执行，审查每步交付和参与量度，为历程处理失败配置警报，并可以选择为深度funnel和流失可视化构建CJA工作区分析。

#### 确定报告方法

此历程需要哪些报告工具？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅限AJO本机报表 | 基本交付和参与监控就足够了 | 实时报表（在执行期间）和所有时间报表（执行后）；对于实时，每60秒刷新一次 |
| AJO + CJA analysis | 需要深度funnel分析、步骤转化率、流失可视化图表或跨历程比较 | 需要与AJO数据集关联的CJA连接和数据视图；最全面 |
| 仅限CJA | 组织使用CJA作为主要分析平台 | 需要CJA配置；AJO本机报表仍作为备份提供 |

#### 决定警报配置

哪些历程失败应触发警报？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 历程处理警报 | 始终建议在生产历程中使用 | 配置文件条目失败、操作节点错误和历程停止警报 |
| 投放失败警报 | 对于具有高价值通信的历程至关重要 | 退回率超过阈值时发出警报，投放失败 |

#### UI导航

- 历程实时报告：历程>选择历程>实时报告
- 历程所有时间报表：历程>选择历程>所有时间报表
- 警报：警报>警报规则>订阅
- CJA工作区：“项目”>“创建新项目”

#### 关键配置详细信息

- 在历程执行期间访问实时报告，以实时监视用户档案条目、退出次数和每步投放指标
- 历程完成后（或积累足够的数据后），查看所有时间报表以进行全面分析
- 为历程处理失败和投放问题配置平台警报
- 对于CJA分析，请确保CJA连接包含AJO体验事件数据集（消息反馈、电子邮件跟踪、历程步骤事件）
- 使用以下方式构建CJA Workspace：
   - funnel可视化图表显示每个历程步骤的用户档案计数
   - 用于识别流失点的流失可视化图表
   - 步骤转化率计算
   - 转化时间分析
   - 渠道级别参与细分（用于多渠道历程）

#### Experience League文档

- [历程实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## 实施注意事项

在实施之前和过程中，请查看以下护栏、隐患、最佳实践和权衡。

### 护栏和限制

- 每个沙盒最多&#x200B;**500个实时历程** — [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 最长&#x200B;**历程持续时间为91天** （全局超时） — 在超时时仍在历程中的配置文件会自动退出
- 每个历程画布最多&#x200B;**50个活动**
- 读取受众历程进程，每秒最多&#x200B;**20,000个配置文件**（默认限制）
- 单一事件历程支持每个沙盒每秒最多&#x200B;**5,000个事件**
- 对于受众读取历程，等待步骤的最短持续时间为&#x200B;**1小时**
- 历程&#x200B;**重新进入冷却最小值为5分钟**
- 每个沙盒每个渠道类型&#x200B;**最多** 10个渠道表面
- 建议的最大电子邮件大小为&#x200B;**100 KB**&#x200B;以实现最佳可投放性
- 每条消息最多&#x200B;**30个内容片段**
- 每个试验最多&#x200B;**10个内容试验处理**（变量）
- 每个沙盒最多&#x200B;**10个上限配置**
- 每个沙盒最多&#x200B;**4,000个区段定义**

### 常见陷阱

- **发布但不测试：**&#x200B;在发布之前，始终使用测试模式和测试配置文件来验证完整的历程路径。 验证配置文件是否遍历预期的分支、等待步骤是否正确推进以及消息是否正确呈现。
- **分支上缺少结束活动：**&#x200B;每个历程分支都必须以结束活动终止。 如果任何分支没有终止节点，则历程将无法发布。
- **过于宽泛的进入条件：**&#x200B;定义松散的进入受众或事件条件可能会向历程大量提供意外配置文件。 通过特定的属性检查和禁止显示规则细化条目标准。
- **忽略重新进入规则：**&#x200B;对于事件触发的历程，配置文件可能会多次触发触发事件。 如果没有正确的重新进入配置（拒绝重新进入或冷却时段），用户档案可能会在历程中累积，从而导致消息重复。
- **等待步骤时区混淆：**&#x200B;在UTC中处理等待持续时间。 在历程属性中明确设置历程时区，以确保等待步骤在预期的本地时间推进。
- **无法直接编辑实时历程：**&#x200B;实时历程。 要进行更改，请复制历程、修改副本、停止原始版本并发布新版本。 在上线之前规划历程版本控制。
- **未定义退出条件：**&#x200B;如果没有退出条件，转换中间历程的用户档案将继续接收后续消息 — 这些消息可能无关或相互矛盾。 始终为转化事件配置退出条件。
- **渠道同意未对齐：**&#x200B;可能会为电子邮件选择用户档案，但不会选择使用短信。 多渠道历程必须尊重每个渠道的同意。 验证是否在每个渠道表面填充并强制执行同意字段。

### 最佳实践

- **开始简单、迭代：**&#x200B;在添加复杂分支之前，以2-3步的线性历程开始。 在条件和渠道中进行分层之前，验证核心流程是否正常工作。
- **使用描述性命名约定：**&#x200B;明确命名历程节点、条件和等待步骤（例如，“Wait_3_Days_After_Welcome”而不是“Wait 1”）。 这使得测试模式的调试和报告解释更加容易。
- **提前配置退出条件：**&#x200B;在设计历程路径之前将转化事件定义为退出条件。 这可以确保从历程中删除转换的用户档案，而不管他们位于哪个步骤。
- **设置有意义的等待持续时间：**&#x200B;根据客户行为数据设置基本等待持续时间 — 典型交互之间的时间、预期的响应窗口和适合渠道的节奏（例如，电子邮件之间为2-3天，短信之间为1周）。
- **使用条件节点检查参与：**&#x200B;在消息操作后，添加条件以检查配置文件是否参与（已打开、已单击）。 将参与的用户档案路由到一条路径，将未参与的用户档案路由到上报或备用渠道路径。
- **利用计算属性进行分支：**&#x200B;使用计算属性（如参与分数、购买频率或上次活动后间隔天数）做出数据驱动的分支决策，而不是任意分支。
- **反复监视和优化：**&#x200B;在初始运行期间每周查看历程报告。 识别流失点、调整等待持续时间、优化条件并根据每步性能数据优化消息内容。
- **版本您的历程：**&#x200B;进行更改时，请复制历程以创建新版本。 维护版本更改日志以进行审核和优化跟踪。

### 权衡决定

应根据您的特定业务要求评估以下权衡。

#### 受众读取条目与事件触发的条目

受众读取条目提供了易于管理和测试的可预测、基于批次的处理。 事件触发的条目提供了实时响应性，这种响应性更与上下文相关，但需要流式基础架构和更仔细的重新条目管理。

- **受众读取优势：**&#x200B;可预测性、大批量处理、计划的生命周期程序、更简单的测试
- **事件触发的好处：**&#x200B;实时相关性、行为上下文、个人资料步调、对客户操作的即时响应
- **建议：**&#x200B;对于时间受业务驱动的计划生命周期计划（入门、续订），请使用受众读取。 对于时间由客户驱动的行为响应序列（放弃购买、购买后），使用事件触发。

#### 单渠道历程与多渠道历程

单渠道历程可以更轻松地实施、测试和管理。 多渠道历程提供了更广泛的触及范围和上报功能，但增加了内容创建、同意管理和频率治理的复杂性。

- **单渠道优惠：**&#x200B;更快实施，更简单的同意管理，更少的内容制作工作，更易于调试
- **多渠道优惠：**&#x200B;更高的参与潜能，无响应用户档案的渠道提升，更全面的客户体验
- **推荐：**&#x200B;从单渠道历程开始，并在扩展到多渠道之前验证流量和业务影响。 增量添加渠道，其中参与数据显示主要渠道未有效触及受众。

#### 历程复杂性与可管理性

具有许多条件和路径的高度分支历程可以处理更多场景，但越来越难以测试、调试和优化。 使用较少分支的更简单历程更易于管理，但可能会提供不太个性化的体验。

- **复杂历程优先：**&#x200B;粒度个性化、特定于区段的路径、全面的方案覆盖
- **更简单的历程更受欢迎：**&#x200B;部署更快、测试更轻松、报告更清晰、维护负担更轻
- **推荐：**&#x200B;将历程限制为3-5个主要分支和15-25个活动。 如果逻辑要求更复杂，请考虑通过跨历程协调拆分为多个历程，而不是单个整体历程。

#### 频度上限严格度与历程完成度

严格的频率限制可防止过度消息传送，但可能会抑制历程消息，导致用户档案跳过步骤并降低历程完成率。 宽松的帽子确保投放历程消息，但风险渠道疲劳。

- **严格的限制优先：**&#x200B;客户体验保护、降低取消订阅率、品牌信任
- **宽松的封顶优惠：**&#x200B;历程完成率、完整消息顺序投放、营销计划效果
- **推荐：**&#x200B;为关键历程消息（入门、续订）分配更高的优先级分数，以便在达到上限时优先于促销活动。 只对真正重要的通信保留“免于上限”。

## 相关文档

以下资源提供了有关此实施中使用的功能的更多详细信息。

### 历程

- [历程入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [创建旅程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [历程属性](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [发布历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [测试您的历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)

### 历程活动

- [读取受众活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [受众鉴定事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [条件活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在历程中添加消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [结束活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [配置自定义操作](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions)

### 登入和退出管理

- [历程条目管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [退出标准](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### 渠道配置

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [设置渠道平面](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [创建 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP预热计划](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 消息创作和个性化

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

### 内容试验

- [内容体验入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [内容试验报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [统计计算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### 频率、冲突和优先级

- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [业务规则概述](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [冲突和优先级管理入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [优先级分数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [历程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [识别潜在冲突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### 受众和分段

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language参考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/edge-segmentation)

### 报告和分析

- [历程实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

### 同意和治理

- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [管理禁止列表](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 数据基础

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [配置文件概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
