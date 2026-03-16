---
title: Brand Concierge对话体验
description: 了解如何将数字资产转换为支持AI、品牌安全的对话体验，以指导客户发现。
solution: Experience Platform, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7239'
ht-degree: 0%

---


# Brand Concierge对话体验

本指南为使用[!DNL Adobe Brand Concierge]并与[!DNL Adobe Experience Platform] (AEP)和[!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP])集成的AI支持的对话体验提供全面的实现参考。 它专为需要跨数字资产部署品牌安全的对话代理的解决方案架构师、营销技术人员和实施工程师而设计。

它涵盖了部署对话体验的所有可行方法，从产品咨询聊天机器人到完整的网站导航助手，并提供了有关何时选择每个选项的指导。 该计划涉及代理配置、品牌治理、内容集成、部署策略、从对话信号扩充配置文件以及分析优化。

[!DNL Brand Concierge]使品牌能够部署智能的对话代理，这些代理能够了解品牌声音、访问获得批准的产品目录和内容、根据实时配置文件数据提供个性化推荐，以及将意图和情绪信号捕获回统一客户配置文件。 这样产生的对话式体验既给人一种自然感，又符合品牌精神，同时还能丰富组织对每个客户的理解。

## 用例概述

越来越多的组织寻求将静态数字体验转换为动态、由AI提供支持的对话，以指导客户做出发现、产品选择和购买决策。[!DNL Adobe Brand Concierge] 通过提供位于现有数字资产上方的协调的会话AI层（由AEP Agent Orchestrator提供支持）来解决此问题。

此模式与传统聊天机器人实施不同，因为它与AEP的统一用户档案原生集成，使用品牌治理护栏确保每个响应符合品牌标准，并将对话信号反馈到客户数据平台，以进行下游个性化和激活。

目标受众包括数字体验团队、电子商务经理、内容策划师和营销技术人员，他们需要部署智能对话体验，以推动参与、转化和丰富用户档案。

## 主要业务目标

此用例模式支持以下业务目标。

### 提供个性化的客户体验

根据个人偏好、行为和生命周期阶段定制内容、选件和消息。

**KPI：**&#x200B;参与度、转化率、客户满意度(CSAT)

[了解有关提供个性化客户体验的更多信息](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

### 提高客户参与度

提高所有数字和物理接触点的交互频率和深度。

**KPI：**&#x200B;参与度，(Web)页面的逗留时间，打开率

[了解有关提高客户参与度的更多信息](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)

### 提高转化率

提高完成所需操作（如购买、注册或表单提交）的访客和潜在客户的百分比。

**KPI：**&#x200B;转化率、潜在客户转化、每个潜在客户的成本

[了解有关提高转化率的更多信息](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)

### 获取新客户

通过有针对性的客户获取促销活动、相似受众和付费媒体优化来扩展客户群。

**KPI：**&#x200B;追加销售/交叉销售%，增量收入，客户存留期值

[了解有关获取新客户的更多信息](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

## 战术用例示例

以下场景说明了如何将此模式应用于实践。

- **产品发现助手** — 在产品列表页面上部署对话代理，该代理会根据客户需求、偏好和预算提出资格确认问题并缩小产品推荐范围
- **引导式比较顾问** — 帮助客户通过自然的对话并排比较产品，突出显示与其指定优先级相关的差异
- **大小合适门房** — 使用对话式问答来指导服装或鞋类购物者选择大小，从而降低退货率并提高购买信心
- **订阅或计划选择器** — 根据使用模式和规定需求，引导客户通过带有个性化推荐的服务层或订阅计划选项
- **站点导航助手** — 帮助访客根据其声明的意图查找相关内容、支持资源或产品类别，从而降低复杂站点的跳出率
- **购买前咨询** — 通过围绕推荐构建的多轮对话，提供高考虑的购买指导（例如，电子产品、金融产品、保险）
- **忠诚度计划礼宾员** — 通过对话互动，帮助忠诚度会员发现奖励、了解层级优势和发现赎回机会
- **重新参与对话** — 根据以前的浏览历史记录或放弃的购物车项目向回访访客发起主动对话外联
- **实时代理升级与上下文** — 将复杂的查询无缝地移交给实时销售或支持代理，同时保留完整的对话上下文和客户个人资料数据
- **购买后支持和追加销售** — 通过对话渠道在购买后提供设置帮助、补充产品建议和满意度登记表，从而吸引客户

## 关键绩效指标

以下KPI可帮助衡量此用例模式是否成功。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 对话参与率 | 发起和持续对话的访客百分比 | 已开始对话/符合条件的页面查看 |
| 会话完成率 | 达成有意义解决方案的对话百分比 | 已完成的对话/已开始的对话 |
| 对话转化率 | 导致所需操作（购买、注册、潜在客户表单）的对话百分比 | 对话的转化率/对话总数 |
| 平均对话深度 | 每个对话的轮次数，表示参与质量 | 每个会话的平均消息计数 |
| 客户满意度(CSAT) | 通过体验内反馈获得的对话后满意度分数 | 调查回复或向上/向下缩进评级 |
| 推荐接受率 | 接受或单击的产品推荐的百分比 | 根据建议采取行动/提供建议 |
| 实时代理切换率 | 提升到实时代理的对话百分比 | 移交/总对话 |
| 配置文件扩充率 | 产生新意图或偏好设置信号的对话百分比 | 扩充的用户档案/对话总数 |
| 受对话影响的收入 | [!DNL Brand Concierge]对话在转化之前进行的购买所产生的收入 | 对话到购买的历程的归因分析 |
| 解决时间 | 从对话开始到解决或移交的平均持续时间 | 跨对话事件的时间戳分析 |

## 用例模式

**Brand Concierge对话体验**

将数字资产转变为AI支持的品牌安全对话体验，通过自然对话引导客户发现，利用意图和情绪信号丰富用户档案，并提供个性化的产品推荐。

**函数链：**&#x200B;代理配置>品牌治理设置>内容集成>对话式体验部署>配置文件扩充>分析和优化

## 应用程序

以下应用程序用于实现此用例模式。

- **[!DNL Brand Concierge]** — AI支持的对话体验应用程序提供代理orchestrator、Product Advisor Agent、Site Advisory Agent、品牌治理和对话分析
- **[!DNL Adobe Experience Platform] (AEP)** — 统一的数据基础，为对话信号提供XDM架构、身份解析、实时客户配置文件和数据收集基础架构
- **[!DNL Real-Time CDP] ([!DNL RT-CDP])** — 客户数据平台，提供个性化对话的实时配置文件查找、从对话信号中细分受众，以及包含意图和情绪数据的配置文件扩充

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本函数 | 状态 | 必须准备好的内容 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 必填 | 为沙盒配置启用了[!DNL Brand Concierge]权利；为对话体验管理员、内容管理员和Analytics用户配置角色；为包含PII或敏感客户信号的对话数据实施ABAC策略 | [访问控制概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | 用于对话事件的XDM架构（ExperienceEvent类，其中包含特定于对话的字段组，用于捕获意图、情绪、产品交互和切换事件）；使用对话首选项和意图属性扩展的配置文件架构；用于接地推荐的产品目录查找架构 | [XDM系统概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/home) |
| 数据源和收集 | 必填 | [!DNL Web SDK]或[!DNL Mobile SDK]配置了将对话事件数据路由到AEP数据集的数据流；用于在对话期间实时捕获事件的[!DNL Edge Network]集成；通过源连接器或批量摄取而摄取的产品目录数据 | [Web SDK 概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/web-sdk/home) |
| 身份和配置文件配置 | 必填 | 为访客识别配置的身份命名空间（匿名使用ECID，身份验证使用CRM ID或电子邮件）；为边缘激活配置的合并策略，用于在对话期间实时查找配置文件；跨设备对话持续性的身份链接规则 | [Identity Service概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home) |
| 受众定义和分段 | 假设就位 | 核心对话部署不需要受众，但个性化对话策略需要受众（例如，高价值客户区段接收不同的对话流）；建议对实时对话个性化进行流式或边缘评估 | [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么它很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | 将对话信号聚合到用户档案级别的属性中（例如，总对话、主导产品兴趣、平均情绪分数），以用于下游分段和个性化 | [计算属性概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/overview) |
| 数据生命周期管理 | 推荐 | 为对话事件数据配置保留策略，管理对话记录和分析的同意，并支持对话记录的隐私删除请求 | [高级数据生命周期管理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-lifecycle/home) |
| 数据使用标签和执行 | 推荐 | 为包含PII、情绪或意图信号的对话数据字段添加标签；实施治理策略，防止敏感对话数据到达未经授权的目的地 | [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home) |
| 监视和可观察性 | 推荐 | 监测会话事件摄取管道，跟踪配置文件扩充成功率，并提醒可能会影响会话个性化质量的数据流失败 | [可观察性分析概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/home) |
| 报告和分析 | 已包含 | 使用[!DNL Brand Concierge]内置分析和[!DNL CJA]分析对话性能、客户反馈、转化归因和代理效率，以进行跨渠道对话影响分析 | [CJA概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-overview/cja-overview) |

## 应用程序功能

此计划从“应用程序功能目录”中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Brand Concierge]

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 代理配置 | 阶段1：代理配置 | 使用代理专业化（产品顾问、站点咨询）和基本行为设置配置[!DNL Brand Concierge]代理协调器 |
| 品牌治理设置 | 第2阶段：品牌治理设置 | 定义塑造所有对话交互的品牌声音、语调、消息传送护栏、批准的内容边界和禁止的主题 |
| 内容集成 | 阶段3：内容集成 | 连接品牌认可的内容源（包括AEM内容、产品目录、知识库和其他可信数据）以进行接地响应 |
| 产品顾问配置 | 阶段3：内容集成 | 配置Product Advisor Agent以提供个性化的产品推荐、引导式比较和品牌一致的响应交付 |
| 站点咨询配置 | 阶段3：内容集成 | 配置网站咨询代理，以通过根据访客行为和意图信号调整交互来增强导航 |
| 对话体验部署 | 阶段4：对话式体验部署 | 跨支持的渠道（Web、移动应用程序、自定义SDK）部署具有文本和语音交互支持的对话体验 |
| 低代码流管理 | 阶段4：对话式体验部署 | 使营销团队能够使用低代码配置工具更新对话语调、流程和内容 |
| 会话配置文件扩充 | 阶段5：配置文件扩充 | 通过对话中捕获的意图、情绪、产品亲和力和行为信号，丰富AEP客户配置文件 |
| 对话分析 | 阶段6：分析和优化 | 通过内置的Analytics功能板监控参与量度、客户反馈、转化数据和对话质量 |
| 代理实时移交 | 阶段4：对话式体验部署 | 为现场销售或支持代理配置无缝切换，同时保留完整的对话上下文 |

### [!DNL Real-Time CDP]

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 实时配置文件查找 | 阶段4：对话式体验部署 | 访问实时客户配置文件属性和区段成员资格，以根据已知的客户数据个性化对话响应 |
| 轮廓扩充 | 阶段5：配置文件扩充 | 使用从对话式行为事件（意图分数、情绪趋势、产品亲和度）派生的计算属性丰富用户档案 |
| 受众评估 | 阶段5：配置文件扩充 | 基于对话信号评估受众成员资格，以实现参与对话区段的下游定位 |

## 先决条件

在实施开始之前，必须准备好以下项目。

- 该组织的[!DNL Adobe Brand Concierge]权利有效
- AEP和[!DNL RT-CDP]许可证已配置足够的配置文件和事件卷权限
- 可用的品牌指南文档定义了语音、语调、批准的消息传递和禁止的主题
- 为集成准备的产品目录或内容存储库（AEM资产、PIM数据或结构化产品信息源）
- 为具有SDK集成技术访问权限的对话体验部署标识的Web资产
- 如果需要进行切换，则可以使用实时代理基础架构（联系中心平台、CRM集成）
- 为对话式数据捕获和分析而建立的同意管理框架
- [!DNL Web SDK]或[!DNL Mobile SDK]已在目标属性上部署（或计划进行并发部署）
- 利益相关者就对话范围进行协调（仅限产品咨询、站点导航或两者）
- 为AI支持的对话数据捕获和使用完成隐私和法律审查

## 实施选项

以下部分介绍了实施此用例模式的不同方法。

### 选项A：产品顾问部署

**最适合：**&#x200B;侧重于引导式产品发现、比较和推荐体验以促进转化和平均订单价值的电子商务和零售组织。

**工作方式：**

Product Advisor Agent被配置为主要的对话专业领域。 它连接到产品目录，了解产品属性和关系，并通过免费对话指导客户获得个性化推荐。 代理使用品牌治理护栏确保推荐与业务优先级保持一致（例如，推广库存商品，突出显示有利利润的产品）。

产品顾问可与实时客户配置文件集成以访问购买历史记录、浏览行为和首选项数据，从而根据客户的配置文件提供客户已经拥有、以前考虑过或可能需要的建议。 当体验事件和意图信号流回配置文件以供下游使用时，会捕获对话。

**关键注意事项：**

- 需要结构良好的产品目录（具有丰富的属性数据）才能提供有效的推荐
- 产品数据必须保持最新，以避免推荐缺货或停产的产品
- 品牌治理必须定义代理如何处理竞争产品提及次数和价格比较

**优点：**

- 通过引导式购买转换直接产生可衡量的收入影响
- 通过更明智的购买决策降低产品退货率
- 捕获高价值产品亲和度和意图信号以实现下游个性化
- 现有电子商务体验的自然扩展

**限制：**

- 需要持续进行产品目录维护和同步
- 仅限于以产品为中心的对话；站点导航问题可能得不到解决
- 有效性取决于目录数据的质量和完整性

**Experience League：**

- [Brand Concierge概述](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge产品顾问](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)

### 选项B：站点咨询部署

**最适合于：**&#x200B;具有复杂数字属性（媒体、金融服务、医疗保健、技术）的组织，在这些组织中，访客需要导航帮助才能查找相关内容、资源或自助服务工具。

**工作方式：**

站点咨询代理配置为主要对话专业领域。 该指南对网站内容结构编制索引，了解页面关系和内容类别，并根据访客行为信号和既定意图调整其指南。 当访客参与时，代理会解释他们的需求，并将他们导向最相关的内容、工具或资源。

Site Advisory使用实时行为信号（当前页面、反向链接来源、导航路径）与配置文件数据（以前的访问、内容偏好设置、客户层）相结合来提供与上下文相关的导航帮助。 这对于具有深层内容层次结构、多个产品线或复杂的自助服务工作流的网站尤其有用。

**关键注意事项：**

- 需要全面的内容索引并随着网站内容的更改定期重新抓取
- 在访客通常难以找到所需内容的具有大量内容的网站上最有效
- 品牌治理应定义范围边界（代理可导航到的站点区域）

**优点：**

- 降低跳出率并提高复杂网站上的内容可发现性
- 捕获显示内容差距和用户体验问题的导航意图信号
- 比Product Advisor更低的实施复杂性（无需产品目录集成）
- 提供对访客正在查找但无法找到内容的分析洞察

**限制：**

- 与以产品为重点的对话相比，与收入转化关系不那么直接相关
- 要求内容结构合理并定期更新以提供准确指导
- 随着站点结构的演变，可能需要频繁地重新培训

**Experience League：**

- [Brand Concierge概述](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge站点顾问](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)

### 选项C：组合的产品顾问+站点咨询部署

**最适合：**&#x200B;希望获得涵盖产品发现和网站导航的全面对话体验的组织，通常是具有丰富数字属性和不同访客意图的大型零售或B2C品牌。

**工作方式：**

Product Advisor Agent和站点咨询代理均在[!DNL Brand Concierge] orchestrator中配置。 Agent Orchestrator使用意图检测将对话路由到相应的专业领域 — 产品相关查询将转至Product Advisor ，而导航和内容查找查询将转至Site Advisory。 Orchestrator可以管理单个会话中不同专业之间的无缝转换。

此方法可提供最完整的对话体验，并处理从“帮助我查找产品”到“在哪里可以查看我的订单状态？”的所有访客需求。 品牌治理护栏在两个专业领域统一应用，确保一致的品牌声音，无论对话主题如何。

**关键注意事项：**

- 更高的实施复杂性要求产品目录和内容集成
- 专业之间的目的路由必须经过周密调整，以避免对话方向错误
- 品牌治理设置范围更广，可同时覆盖产品和导航上下文

**优点：**

- 为访客提供最全面的对话体验
- 单一入口点处理不同的访客意图，无需单独的界面
- 跨专业化对话（例如，导致支持导航的产品问题）自然得到处理
- 从各种对话信号中扩充的最丰富个人资料

**限制：**

- 最高的实施工作量和持续的维护工作
- 需要产品目录和内容团队之间的协调
- 更复杂的测试和质量保证要求
- 更多地涉及品牌治理配置

**Experience League：**

- [Brand Concierge概述](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### 选项比较

| 标准 | 选项A：产品顾问 | 选项B：站点咨询 | 选项C：合并 |
| --- | --- | --- | --- |
| 最适合 | 电子商务、产品驱动型转化 | 大量内容的站点，自助导航 | 全方位数字体验 |
| 复杂性 | 中 | 低Medium | 高 |
| 价值实现时间 | 4-6周 | 3-5周 | 6-10周 |
| 收入影响 | 高（直接转化影响） | Medium（通过参与间接） | 最高（转化率和参与度） |
| 内容要求 | 具有丰富属性的产品目录 | 网站内容索引 | 产品目录和内容索引 |
| 轮廓扩充 | 产品亲和度、购买意图 | 导航意图，内容偏好设置 | 全信号频谱 |
| 维护工作 | 产品目录同步 | 内容重新索引 | 两者均正在进行 |

### 选择正确的选项

首先评估您的主要业务目标和数字资产特征：

1. **如果您的主要目标是推动产品转化**，并且您的数字资产以商业为中心，请选择&#x200B;**选项A （产品顾问）**。 这是零售和电子商务品牌最常见的起点。

2. **如果您的主要目标是提高内容可发现性**，并且您的网站具有深层内容层次结构或复杂的自助服务工作流，请选择&#x200B;**选项B （网站咨询）**。 这是媒体、金融服务、医疗保健和技术公司的理想选择。

3. **如果您需要全面的涵盖范围**&#x200B;并且同时具有产品商务和内容导航需求，请选择&#x200B;**选项C（组合）**。 考虑从一个专业化开始，在第一个专业化稳定并优化后，添加第二个专业。

建议大多数组织采用分阶段的方法：先部署一个专业领域，验证性能并收集经验教训，然后展开到组合部署。

## 实施阶段

以下阶段概述了建议的实施顺序。

### 阶段1：代理配置

**应用程序函数：** [!DNL Brand Concierge]：代理配置

配置核心[!DNL Brand Concierge]代理Orchestrator，包括选择代理专业化（产品顾问、站点咨询或两者），配置基本代理行为，以及在[!DNL Brand Concierge]和AEP之间建立连接以进行配置文件访问和事件捕获。

#### 决策：代理专业化选择

确定应为此部署激活的代理专业。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅产品顾问 | 以Commerce为中心的部署以产品发现和转化为目标 | 需要产品目录集成；实现收入影响的最快途径 |
| 仅站点咨询 | 以内容和导航为中心的部署 | 集成复杂性较低；最适合非商业网站 |
| 两种专业 | 跨产品和内容的全面对话覆盖 | 复杂性更高；请考虑从一次开始分阶段推出 |

#### 决策：会话启动模型

确定应在数字财产上开始对话的方式。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 访客启动（被动） | 聊天小组件可用但无法主动参与的默认方法 | 降低中断风险；依赖访客对聊天选项的了解 |
| 主动参与（触发） | 代理根据行为信号（例如，延长停留时间、重复页面访问、购物车犹豫）发起对话 | 参与率较高，但如果触发器过于激进，可能会引起访客的烦恼；需要行为触发器调整 |
| 混合（被动，带有上下文提示） | 聊天小组件是被动的，但会根据页面内容或访客行为显示上下文提示 | 均衡方法；在不强制参与的情况下提示指南 |

#### 配置代理

**UI导航：** [!DNL Experience Platform] > AI助手> [!DNL Brand Concierge] >代理配置

关键配置详细信息：

- 定义将在对话界面中显示的代理名称和描述
- 选择包含代理应访问的客户配置文件和事件数据的AEP沙盒
- 配置代理编排器，以根据意图检测在专业之间路由查询
- 设置会话会话参数（超时持续时间、最大会话长度、并发会话限制）
- 启用实时配置文件查找集成，以便代理可以在对话期间访问访客配置文件数据

**选项差异的位置：**

选项A的&#x200B;**（产品顾问）：**
启用Product Advisor专业化并配置其与产品目录数据源的连接。 设置产品推荐参数，包括每个响应的最大推荐、产品属性显示首选项和比较处理规则。

选项B的&#x200B;**（站点咨询）：**
启用“站点建议”专业化并配置其与站点内容索引的连接。 设置导航参数，包括内容范围边界、页面类别处理和深层链接生成首选项。

选项C （组合）的&#x200B;**：**
启用这两个专业化并配置Orchestrator的意图路由逻辑。 定义路由规则，以确定何时应由产品顾问或站点顾问处理对话，以及如何在单个对话中管理专业化之间的过渡。

**Experience League文档：**

- [Brand Concierge概述](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [AI Assistant概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/ai-assistant/home)
- [AEP Agent Orchestrator](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### 第2阶段：品牌治理设置

**应用程序函数：** [!DNL Brand Concierge]：品牌治理设置

配置塑造所有对话交互的品牌治理护栏。 这包括品牌声音和音调定义、批准的内容范围、禁止的主题、响应风格指南和上报规则。 品牌治理确保每个AI生成的响应都符合品牌标准。

#### 决定：治理严格程度

确定品牌治理护栏应该在多大程度上限制对话式回应。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 严格的治理 | 高度管控的行业（金融服务、医疗保健、保险）或高端品牌，需要精确的音调控制 | 限制对话灵活性；可能导致更频繁地“我无法帮助解决此问题”响应；最高品牌安全性 |
| 审核治理 | 大多数消费者品牌，品牌声音的一致性很重要，但某些对话灵活性是可以接受的 | 在品牌安全和对话自然性之间取得良好的平衡；建议将重点放在大多数实施中 |
| 灵活的治理 | 注重对话性格和参与度的休闲或生活方式品牌 | 最自然的对话感；需要更持续地监控品牌外响应 |

#### 决策：主题外处理策略

确定代理应如何处理其配置范围之外的问题。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 重定向到范围 | 代理确认问题并重定向到可以帮助处理的主题 | 保持参与度，但可能会因合理的话题外需求而令访客感到沮丧 |
| 移交给实时代理 | 代理选件，用于将访客与人工代理连接起来以进行主题外问题 | 最佳客户体验，但需要实时代理基础架构和人员 |
| 资源正常下降 | 代理程序说明它不能帮助处理该主题，并提供相关资源或支持渠道的链接 | 低摩擦回退；不需要实时代理可用性 |

#### 配置品牌治理

**UI导航：** [!DNL Experience Platform] > AI助手> [!DNL Brand Concierge] >品牌管理

关键配置详细信息：

- 定义品牌属性：品牌名称、标语、使命、价值和人格特征，以传达对话语调
- 设置音调参数：形式水平、幽默容忍、同理心水平和产品推荐自信
- 配置批准的内容边界：代理有权讨论的主题和明确禁止的主题
- 定义响应格式准则：最大响应长度、列表与散文的使用、表情符号策略和链接格式
- 设置升级触发器：应自动将对话路由到实时代理的条件（例如，投诉检测、重复的不满信号、高价值客户识别）
- 配置竞争提及处理：当访客询问竞争对手的产品时，代理应如何响应
- 定义免责声明和法律通知要求：受监管行业的强制性披露

**Experience League文档：**

- [Brand Concierge品牌治理](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [AI Assistant操作见解](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/ai-assistant/home)

### 阶段3：内容集成

**应用程序功能：** [!DNL Brand Concierge]：内容集成、产品顾问配置、站点咨询配置

配置内容源，以便根据准确、品牌认可的信息提供对话式响应。 这包括产品目录集成、AEM内容连接、知识库导入和内容刷新计划。

#### 决策：产品目录集成方法

确定应如何将产品数据提供给Product Advisor Agent。 （仅选项A和C）

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| AEP数据集集成 | 产品目录已通过源连接器作为查找数据集引入AEP | 利用现有的数据基础架构；使产品数据与用户档案数据保持同步；需要基本的数据建模和收集以包含产品目录 |
| 直接馈送集成 | 产品目录存在于可提供结构化信息源的PIM或商务平台中 | 可以提供更多实时库存和定价数据；需要信息源配置和计划 |
| AEM内容集成 | 产品内容在AEM中进行管理，并且应充当权威的产品数据源 | 最适合将AEM作为内容中心的品牌；确保Web内容和对话响应之间的一致性 |

#### 决策：内容刷新频率

确定代理的内容知识库更新频率。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 实时/近乎实时 | 产品可用性、定价或内容更改频繁（例如，快闪销售、对库存敏感的零售） | 最高的准确性但更高的基础架构负载；对于对库存敏感的建议来说至关重要 |
| 每日刷新 | 已计划和计划内容变更（例如，编辑日历、每周促销活动） | 精确度和性能之间的良好平衡；适用于大多数实施 |
| 按需刷新 | 内容更改不频繁，可以在发生更新时手动触发 | 开销最低；适用于静态产品目录或稳定的内容站点 |

#### 配置内容源

**UI导航：** [!DNL Experience Platform] > AI助手> [!DNL Brand Concierge] >内容源

关键配置详细信息：

- 将产品目录数据源与产品名称、说明、属性、定价、可用性、图像和类别层次结构的字段映射连接起来
- 为站点页面、知识库文章、常见问题解答内容和支持文档配置内容索引
- 设置内容范围边界，以定义代理可以引用和排除的内容
- 配置在代理无法找到相关内容以回答问题时的内容回退行为
- 设置内容质量规则：包含在响应、引文要求和源归因中的最低内容置信度阈值

**选项差异的位置：**

选项A的&#x200B;**（产品顾问）：**
重点关注产品目录与富产品属性映射的集成。 配置Product Advisor Agent的推荐逻辑，包括要推荐多少个产品、如何处理缺货项目、如何显示产品比较以及如何将客户配置文件数据（购买历史记录、浏览行为）合并到推荐排名中。

选项B的&#x200B;**（站点咨询）：**
侧重于使用页面层次结构映射进行网站内容索引。 配置网站咨询代理的导航逻辑，包括如何解释访客意图、区分哪些内容类别的优先级、如何处理不明确的导航请求以及如何根据访客的当前页面上下文和会话行为调整建议。

选项C （组合）的&#x200B;**：**
配置产品目录和站点内容源。 确保内容路由逻辑将内容正确分配给适当的专业化，并正确映射产品内容和站点导航内容之间的交叉引用。

**Experience League文档：**

- [Brand Concierge内容配置](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge产品顾问](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Brand Concierge站点顾问](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [源概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/home)

### 第4阶段：对话体验部署

**应用程序功能：** [!DNL Brand Concierge]：对话式体验部署、低代码流管理、实时代理切换；[!DNL RT-CDP]：实时配置文件查找

部署有关目标数字资产的对话体验，包括渠道配置、构件自定义、个性化的配置文件查找集成、实时代理切换规则以及用于持续内容管理的低代码工具。

#### 决策：部署渠道

确定应将对话体验部署到的渠道。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| Web（嵌入式构件） | 主要Web属性是客户的主要接触点 | 最常见的起点；需要[!DNL Web SDK]集成；同时支持匿名访客和经过身份验证的访客 |
| 移动应用程序（SDK集成） | 移动应用程序是一个重要的客户参与渠道 | 需要[!DNL Mobile SDK]集成；请考虑对话UI的屏幕不动产约束 |
| 自定义SDK部署 | 对话式体验需要嵌入到自定义应用程序、网亭或非标准数字属性中 | 最大的灵活性；需要更多的开发工作；适用于店内自助服务亭或专有平台 |
| 多渠道部署 | 需要同时跨Web、移动和其他渠道进行对话体验 | 覆盖率最高；要求跨渠道实施一致的品牌治理；如有可能，跨渠道的对话上下文应保持不变 |

#### 决策：用于对话的Personalization深度

确定工程师应使用多少客户配置文件数据来个性化对话。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅匿名（会话上下文） | 隐私优先方法或当大多数访客无法识别时 | 仅使用会话中的行为信号；无需配置文件查找；适用于匿名产品发现 |
| 配置文件感知（经过身份验证的访客） | 访客通常会登录，并根据历史记录增值提供个性化推荐 | 需要通过[!DNL RT-CDP]进行实时配置文件查找；对于已知客户，推荐质量显着提高 |
| 渐进式个性化 | 在对话期间将匿名和身份验证与渐进式配置文件构建相结合 | 从会话上下文开始；在访客提供信息或进行身份验证时实现丰富；在隐私和个性化之间实现平衡 |

#### 决策：实时代理切换配置

确定是否应将对话上报给现场的代理人员。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 不切换（仅限自助服务） | AI代理可以处理所有预期的会话类型，或者实时代理不可用 | 部署最简单；可能会使具有复杂需求的访客感到沮丧；适用于低风险、产品浏览的场景 |
| 基于规则的切换 | 特定触发器应呈报给现场代理（例如，投诉检测、高价值客户、复杂查询） | 可预测的升级行为；需要定义升级规则和触发器；需要实时代理平台集成 |
| 访客请求的切换 | 访客可以在对话的任何时刻请求实时代理 | 最佳客户体验；需要始终可用的代理人员配备或队列管理；交谈内容必须转移 |

#### 部署对话体验

**UI导航：** [!DNL Experience Platform] > AI助手> [!DNL Brand Concierge] >部署

关键配置详细信息：

- 配置对话小部件的外观：位置、配色方案、头像、欢迎消息和交互样式（文本、语音或两者）
- 与[!DNL Web SDK]或[!DNL Mobile SDK]集成以进行事件捕获和配置文件解析
- 配置实时配置文件查找以访问客户属性、细分成员资格和对话期间的最近活动
- 设置与联系中心平台的实时代理切换集成，包括上下文传输协议、队列路由和代理通知
- 为营销团队启用低代码流管理工具，以便在没有开发人员参与的情况下更新对话启动器、促销消息、季节性内容和流变量
- 配置会话会话持久性规则：会话历史记录保留多长时间，会话是否可以跨会话恢复，以及跨设备会话连续性

**Experience League文档：**

- [Brand Concierge部署](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Web SDK概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/web-sdk/home)
- [Edge Network Server API概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/edge-network-server-api/overview)
- [配置文件API实体端点](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/api/entities)
- [Real-time Customer Profile概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/home)

### 阶段5：配置文件扩充

**应用程序函数：** [!DNL Brand Concierge]：对话式配置文件扩充；[!DNL RT-CDP]：配置文件扩充，受众评估

配置捕获和扩充管道，将对话信号反馈到AEP统一客户个人资料中。 这包括将会话事件映射到XDM、提取意图和情绪信号、从会话数据创建计算属性以及基于会话行为构建受众。

#### 决策：对话信号捕获范围

确定应捕获哪些对话信号并将其写入客户个人资料。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅核心参与信号 | 最小化的配置文件扩充；捕获对话开始、结束、持续时间和完成状态 | 最低的数据量；足以进行基本分析；有限的个性化价值 |
| 意图和偏好设置信号 | 捕获推断的产品兴趣、声明的偏好和讨论的主题类别 | 高个性化值；中等数据量；最推荐 |
| 完整信号捕获 | 捕获意图、情绪、产品交互、推荐响应、移交事件和反馈分数 | 最丰富的用户档案扩充；最大数据量；支持高级分析和机器学习驱动的个性化 |

#### 决策：根据对话数据创建受众

确定是否应当根据用于下游激活的对话行为创建受众。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 无对话受众 | 对话数据仅用于Analytics，而不用于受众激活 | 最简单的方法；如果对话是对现有接洽渠道的补充，则适合采用这种方法 |
| 基于意图的受众 | 根据叙述的产品兴趣或对话中的导航意图创建受众 | 启用重新定位表示感兴趣但未转化的访客；商业价值高 |
| 行为受众 | 根据对话参与模式（例如，高参与度、放弃的对话、重复访问）创建受众 | 支持以对话为依据的历程编排和跨渠道跟进 |

#### 配置配置文件扩充

**UI导航：** [!DNL Experience Platform] >客户>配置文件>计算属性（适用于派生信号）；客户>受众>创建受众（适用于对话受众）

关键配置详细信息：

- 将对话事件映射到XDM ExperienceEvent架构字段，这些字段捕获对话ID、消息计数、讨论的主题、引用的产品、情绪得分和解决状态
- 将[!DNL Brand Concierge]配置文件扩充配置为将意图和首选项信号写入统一配置文件
- 从对话事件数据创建计算属性：总对话（存留期）、主要产品类别兴趣（30天）、平均情绪得分（90天）、对话到购买的转化率
- 根据用于下游激活的对话信号定义流式或批量受众区段（例如，“过去7天内讨论过产品类别X但未购买的访客”）
- 通过查找样本配置文件以确认填充对话属性来验证配置文件扩充

**Experience League文档：**

- [计算属性概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/overview)
- [计算属性UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/ui)
- [区段生成器UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Real-time Customer Profile概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/home)

### 第6阶段：分析和优化

**应用程序函数：** [!DNL Brand Concierge]：对话分析

设置Analytics功能板和报表，以衡量对话体验表现、识别优化机会和跟踪KPI。 这包括[!DNL Brand Concierge]内置分析、用于跨渠道对话影响分析的可选[!DNL CJA]集成以及持续优化工作流程。

#### 决策： Analytics深度

确定所需的对话分析级别。

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 内置[!DNL Brand Concierge]分析 | 只需关于对话量、参与度、满意度和转化的标准报告即可 | 激活速度最快；涵盖核心KPI；跨渠道关联能力有限 |
| [!DNL Brand Concierge] + [!DNL CJA]集成 | 需要跨渠道分析来了解对话如何影响更广泛的客户历程 | 需要设置[!DNL CJA]连接和数据视图；启用跨对话和其他渠道的归因分析 |
| 完整Analytics栈栈（[!DNL Brand Concierge] + [!DNL CJA] +自定义功能板） | 根据分析见解创建执行级报表、高级归因建模和自定义受众 | 最高的分析能力；需要[!DNL CJA]专业知识；支持数据驱动的对话优化 |

#### 配置分析和优化

**UI导航：** [!DNL Experience Platform] > AI助手> [!DNL Brand Concierge] > Analytics； [!DNL Analytics Platform] > Workspace（适用于[!DNL CJA]）

关键配置详细信息：

- 查看[!DNL Brand Concierge]内置分析功能板：对话量趋势、参与率、完成率、CSAT分数、推荐接受率和移交频率
- 将[!DNL CJA]连接配置为包含用于跨渠道分析的对话事件数据集（如果选择[!DNL CJA]集成）
- 构建[!DNL CJA]工作区分析以分析对话到转化归因，确定哪些对话主题与购买行为相关
- 设置对话质量监控：跟踪座席争执的主题、常见的未回答的问题以及一段时间内的情绪趋势
- 定义优化工作流程：根据Analytics分析定期审查品牌治理更新、内容刷新触发器和对话流改进的工作频率

**Experience League文档：**

- [Brand Concierge分析](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [CJA Analysis Workspace概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/home)
- [创建或编辑CJA连接](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-connections/create-connection)
- [创建或编辑CJA数据视图](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/create-dataview)

## 实施注意事项

以下部分涵盖在实施过程中要牢记的护栏、常见隐患、最佳实践和权衡取舍决定。

### 护栏和限制

- [!DNL Brand Concierge]会话体验受人工智能响应生成速率限制的约束；并发会话容量取决于授权层
- 对话期间的实时配置文件查找受每个沙盒的配置文件API速率限制的约束 — [实时客户配置文件护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)
- 对话事件数据摄取遵循标准AEP流摄取限制 — [摄取护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/ingestion/guardrails)
- 产品目录大小和内容索引卷受[!DNL Brand Concierge]内容集成限制的约束
- 每个沙盒最多25个计算属性应用于对话信号聚合 — [计算属性护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/overview)
- 每个沙盒最多4,000个区段定义适用于对话受众 — [分段护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)

### 常见陷阱

- **品牌治理定义不足：**&#x200B;如果部署时没有进行完整的品牌治理配置，则会导致品牌外响应，从而损害客户信任。 在部署之前，在阶段2中投入大量时间定义语气、边界和上报规则。
- **过时的产品目录数据：**&#x200B;产品顾问基于过时的库存、定价或可用性数据的建议会令客户感到沮丧并削弱信心。 通过验证检查建立自动内容刷新管道。
- **过于积极主动的主动参与触发器：**&#x200B;过于积极设置行为触发器（例如，在页面上经过3秒后触发对话）会惹恼访客，并提高跳出率。 从保守的触发器开始，并根据参与数据进行调整。
- **忽略匿名访客体验：**&#x200B;仅将个性化重点放在经过身份验证的访客上会忽略大部分流量。 设计会话流程，以使用会话中行为信号为匿名访客提供价值。
- **跳过配置文件扩充配置：**&#x200B;部署对话而不将信号捕获回配置文件，会浪费宝贵的意图和偏好设置数据。 在部署的同时配置配置文件扩充，而不是作为事后处理。
- **忽略实时代理切换体验：**&#x200B;较差的切换体验（丢失上下文、重复的问题、等待时间较长）比完全不提供切换更会损害整体的对话体验。 在启动之前测试完整的端到端移交流程。

### 最佳实践

- 从单个代理专业化（产品顾问或站点咨询）开始，在建立基线性能后展开。
- 在配置护栏之前，与营销、法律和客户体验利益相关者举办品牌治理研讨会。
- 使用渐进式个性化：在访客提供信息或进行身份验证时，通过基于会话上下文的响应开始对话并深化个性化。
- 使用低代码流管理工具对会话启动器、提示和推荐呈现格式实施A/B测试。
- 安排定期（每周或每两周）审查对话分析，以确定内容差距、常见故障点和优化机会。
- 在对话分析和品牌治理更新之间创建反馈循环 — 使用对话数据优化语调、添加新的已批准主题并调整上报规则。
- 监控对话情绪趋势，作为产品问题、网站问题或品牌认知变化早期预警系统。
- 设计对话流程，自然捕捉丰富个人资料的信号，而不会让互动感觉像是在审问。

### 权衡决定

>[!NOTE]
>应根据贵组织的特定要求和限制来评估以下权衡取舍决策。

**对话个性化深度与隐私简洁性**

更深层的配置文件集成支持更个性化和有效的对话，但会增加数据收集的复杂性、同意要求和隐私合规性负担。

- **深层个性化优惠：**&#x200B;转化率更高、推荐质量更好、配置文件丰富更丰富，以及更吸引回头客户的对话
- **隐私简洁性更受青睐：**&#x200B;部署速度更快、同意管理更简单、监管风险更低，以及隐私优先的品牌定位
- **推荐：**&#x200B;从渐进式个性化开始，它适用于匿名访客，并为经过身份验证的会话添加基于个人资料的个性化。 这可在所有标识级别提供价值，同时使隐私合规性处于可管理状态。 根据现有的同意框架实施同意捕获以进行对话分析。

**品牌治理严格性与对话自然性**

严格的品牌治理护栏确保每个响应都符合品牌标准，但过于僵化的限制让对话感觉像机器一样并减少参与。

- **严格的治理优惠：**&#x200B;品牌安全、法规合规性、一致的消息传递和可预测的代理行为
- **灵活的治理优惠：**&#x200B;自然的对话流程、更高的参与度、更好的客户满意度，以及处理更多查询的能力
- **建议：**&#x200B;从适度治理开始，并根据对话分析进行收紧或放松。 监测“我无法帮助解决此问题”响应的速率，作为过度限制的指示器。 使用低代码流管理工具，无需开发人员参与即可快速迭代治理设置。

**实时内容刷新与系统性能**

实时内容同步确保代理始终具有最新的产品和内容数据，但连续刷新会占用更多基础架构资源，并且可能会带来延迟。

- **实时刷新优惠：**&#x200B;对库存敏感的推荐、对时间敏感的促销和快速更改内容的准确性
- **计划的刷新有利于：**&#x200B;系统稳定性、可预测的资源消耗并降低基础架构成本
- **建议：**&#x200B;使用每日内容刷新作为默认值，仅对库存可用性和定价数据进行近乎实时的刷新，这些数据对客户体验有重大影响。 监测内容准确度量度以确定刷新频率是否足够。

**全面的信号捕获与数据管理开销**

捕获每个对话信号提供了最丰富的信息配置文件扩充和分析，但增加了数据量、存储成本和治理复杂性。

- **完整信号捕获优势：**&#x200B;高级分析、ML模型训练、全面的配置文件扩充和最大下游个性化值
- **选择性捕获优势：**&#x200B;降低存储成本，简化数据管理，提高配置文件查找性能，更轻松地遵守数据最小化原则
- **建议：**&#x200B;从意图和偏好设置信号捕获（中间位置）开始，仅在验证附加数据创建可衡量的下游值之后才展开到完整信号捕获。 将数据集过期策略应用于会话事件数据以管理存储增长。

## 相关文档

以下资源提供了实施此用例模式的其他信息。

**[!DNL Brand Concierge]**

- [Brand Concierge概述](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge产品顾问](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Brand Concierge站点顾问](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [AI Assistant概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/ai-assistant/home)

**[!DNL Adobe Experience Platform]**

- [AEP概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/landing/home)
- [XDM系统概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/schema/composition)
- [Real-time Customer Profile概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/home)

**数据收集和集成**

- [Web SDK概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/web-sdk/home)
- [移动SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [配置数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/datastreams/configure)
- [Edge Network Server API概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/edge-network-server-api/overview)
- [源概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/home)

**身份和配置文件**

- [Identity服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [合并策略概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/merge-policies/overview)
- [计算属性概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/overview)

**受众和分段**

- [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/streaming-segmentation)

**数据治理和隐私**

- [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home)
- [同意和偏好设置字段组](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/field-groups/profile/consents)
- [Privacy Service概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/privacy/home)
- [高级数据生命周期管理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-lifecycle/home)

**监视和可观察性**

- [可观察性分析概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/home)
- [警报概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/alerts/overview)

**分析和报告**

- [CJA概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA连接概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-connections/overview)
- [CJA数据视图概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/data-views)
- [Analysis Workspace概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/home)

**护栏**

- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)
- [摄取护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/ingestion/guardrails)
- [分段护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)
