---
title: 行为推荐
description: 了解如何使用选择策略和排名模型生成项目和内容推荐。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: db16e773-e0da-46c4-9fa5-d16f04feb46b
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7545'
ht-degree: 2%

---

# 行为推荐

本指南介绍如何使用[!DNL Adobe Journey Optimizer] (AJO) Decisioning、[!DNL Real-Time Customer Data Platform] (RT-CDP)和[!DNL Adobe Experience Platform] (AEP)实施行为产品和内容推荐。 它专为需要跨Web、移动应用程序和电子邮件渠道提供个性化推荐体验的解决方案架构师、营销技术人员和实施工程师而设计。

它提供了所有可行的实施选项、每个阶段的决策考虑以及指向[!DNL Adobe Experience League]文档的链接。 行为推荐使用行为信号（产品查看、购买、内容交互、搜索查询）与AJO Decisioning选择策略和排名模型相结合，生成项目级别或内容级别的推荐。 与offer decisioning（使用资格规则和业务限制来控制一组有限的优惠、促销或激励）不同，此模式适用于不断变化的大型项目目录（产品、文章、视频），其中的选择由行为亲和信号而不是受控制的资格驱动。

## 用例概述

拥有产品目录、内容库或媒体库的组织需要根据每位访客的行为历史记录和会话内活动，向其展示最相关的项目。 无论是主页上的“为您推荐”轮播、产品详细信息页面上的交叉销售小组件，还是电子邮件促销活动中嵌入的产品推荐，基本挑战都是相同的：将每位访客的行为配置文件与目录中最相关的项目相匹配，然后在适当的时候在正确的渠道中提供这些推荐。

此模式通过以下方式解决了该难题：通过[!DNL Web SDK]或[!DNL Mobile SDK]实时摄取行为信号，通过结合项目属性和行为上下文的AJO Decisioning选择策略处理这些信号，以及通过Web、应用程序内或电子邮件渠道交付推荐的项目。 排名模型可以基于公式（例如，按类别亲和度分数排序）或AI排名（例如，个性化推荐模型）。 模式还通过配置回退推荐来处理没有行为历史记录的新访客的冷启动方案。

此模式的目标受众包括电子商务营销团队、内容个性化团队和数字体验团队，这些团队寻求通过由真实用户行为驱动的个性化推荐提高参与度、转化率和平均订单价值。

## 主要业务目标

此用例模式支持以下业务目标。

### [推动交叉销售和追加销售收入](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

根据行为和购买历史，向现有客户推广补充性和优质产品或服务。

**KPI：**&#x200B;追加销售/交叉销售%，增量收入，客户存留期值

### [提高转化率](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

提高完成所需操作（如购买、注册或表单提交）的访客和潜在客户的百分比。

**KPI：**&#x200B;转化率、潜在客户转化、每个潜在客户的成本

### [提供个性化的客户体验](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

根据个人偏好、行为和生命周期阶段定制内容、选件和消息。

**KPI：**&#x200B;参与度、转化率、客户满意度(CSAT)

## 战术用例示例

以下是此模式的常见战术实施：

- 产品详细信息页面上的产品交叉销售小组件（“已购买客户”）
- 基于浏览历史记录的主页上的“为您推荐”轮播
- 媒体网站上基于阅读行为的内容推荐
- “最近查看的项目”与类似项目小部件相结合
- 购买后补充产品推荐
- 通过电子邮件发送基于行为亲和度的产品推荐
- 基于会话内浏览行为的特定于类别的推荐
- 基于行为信号的搜索结果重新排名

## 关键绩效指标

以下KPI有助于衡量行为推荐实施的有效性。

| KPI | 度量方法 |
| --- | --- |
| 推荐点进率(CTR) | 推荐项目的点击次数除以推荐展示次数 |
| 推荐转化率 | 推荐点击量的购买或所需操作数除以推荐总点击量 |
| 受推荐影响的收入 | 来自至少包含一个推荐驱动型产品的订单的总收入 |
| 平均订单值(AOV)提升 | 参与推荐的会话与未参与推荐的会话的AOV增加 |
| 每订单项目数 | 每个订单中涉及推荐的会话的项目数 |
| 推荐范围 | 收到个性化（非后备）推荐的符合条件的页面查看次数或会话的百分比 |
| 冷启动回退率 | 由于行为历史记录不足而由回退逻辑提供的推荐请求百分比 |

## 用例模式

**行为推荐**

使用AJO Decisioning选择策略和排名模型根据行为信号生成项目级或内容级推荐，以提供上下文内容。

**函数链：**&#x200B;行为信号摄取>决策策略评估>推荐交付>报告

有关组合模式的指导，请参阅实施注意事项下的模式组合部分。

## 应用程序

在此用例模式中使用以下应用程序。

- **[!DNL Adobe Journey Optimizer] (AJO)决策** — 选择策略、排名模型、项目目录和决策策略，用于评估行为信号并返回每个访客的最相关项目
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 行为配置文件数据累积、推荐范围的受众评估以及行为亲和度评分的计算属性
- **[!DNL Adobe Experience Platform] (AEP)** — 通过[!DNL Web SDK]和[!DNL Mobile SDK]进行的行为事件摄取，[!DNL Edge Network]正在处理，事件和目录数据的XDM架构管理

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本功能 | 状态 | 必须准备就绪 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 假设就位 | 启用了Decisioning权限的AJO沙盒。 设置了访问项目目录管理、选择策略配置和渠道表面管理的用户角色。 | [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)，[访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | 体验事件架构捕获具有项目/产品标识符的行为信号（产品查看、添加到购物车、购买、内容交互）。 推荐项目集的项目目录架构（产品属性、类别、图像、价格）。 具有标识字段的配置文件架构。 为[!DNL Real-Time Customer Profile]启用的所有架构。 | [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)，[创建数据集](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create) |
| 数据源和收集 | 必填 | 通过[!DNL Web SDK]或[!DNL Mobile SDK]实时行为事件流至关重要 — 推荐质量取决于新的行为信号。 必须引入项目目录数据（批处理或流式传输）。 为Edge决策启用了AJO服务的数据流。 | [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)，[Mobile SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)，[配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| 身份和配置文件配置 | 必填 | 行为信号必须与身份（通过ECID已知或匿名）关联才能构建行为配置文件。 对于已知访客推荐，必须配置经过身份验证的身份（CRM ID、电子邮件）。 在Edge上处于活动状态的合并策略用于实时推荐交付。 | [身份服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| 受众定义和分段 | 推荐 | 受众可用于确定推荐的范围（例如，仅向高级成员推荐高级产品）或进行筛选。 如果推荐是纯行为的，则不需要严格设置。 对于基于电子邮件的推荐（选项C），它是定义目标受众所必需的。 | [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么这很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | 类别亲和度分数、产品交互频率、购买回访间隔和总支出等计算属性提高了推荐排名质量。[!DNL Customer AI] 倾向分数可以通过预测购买可能性来进一步增强相关性。 | [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)，[客户人工智能概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| 数据生命周期管理 | 推荐 | 行为事件数据应具有适当的过期策略 — 推荐相关性会随着数据过时而降低。 在行为事件数据集上设置数据集过期策略可确保最新性并管理存储。 同意执行可确保合规地使用行为数据。 | [数据集过期](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration)，[高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 数据使用标签和执行 | 推荐 | 行为数据上的治理标签可确保合规地使用推荐的交互历史记录。 当行为数据包括浏览模式、购买历史记录或健康/金融产品兴趣信号时，尤为重要。 | [数据管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)，[数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview) |
| 监视和可观察性 | 推荐 | 应监测推荐提交延迟、回退率和项目目录摄取健康状况。 针对行为事件摄取失败和决策错误发出警报有助于保持推荐质量。 | [可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)，[警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| 报告和分析 | 已包含 | 推荐性能报告是函数链步骤4的一部分。[!DNL Customer Journey Analytics] 分析跨表面和区段的推荐有效性、收入影响和项目级表现可提供优化见解。 | [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)，[Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## 应用程序功能

此计划从“应用程序功能目录”中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Journey Optimizer] (AJO)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| Decisioning | 项目目录和选择策略设置 | 配置项目目录（决策项目）、具有行为排名模型的选择策略、筛选规则和后备推荐 |
| 渠道配置 | 渠道和表面配置 | 为要呈现推荐的Web（基于代码的体验）、应用程序内、内容卡或电子邮件渠道配置投放界面 |
| 消息创作 | 内容和投放配置 | 设计推荐项目的推荐呈现模板、项目显示布局和个性化表达式 |
| 报告和性能分析 | 报告和优化 | 通过AJO本机报表和[!DNL Customer Journey Analytics]集成监控推荐点进、转化和收入量度 |

### [!DNL Real-Time CDP] (RT-CDP)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 受众评估 | 受众范围（选项C） | 评估用于设定推荐范围或定义电子邮件推荐营销活动的目标群体的受众区段 |
| 轮廓扩充 | 行为信号扩充 | 使用可提高推荐排名的计算属性（类别亲和度分数、交互频率）丰富用户档案 |

## 先决条件

在开始实施之前完成以下操作：

- [ ] AJO Decisioning已在Target沙盒中配置并启用
- [ ] [!DNL Web SDK]或[!DNL Mobile SDK]已部署，并通过产品/内容标识符收集行为事件
- [ ]产品或内容目录数据可用于引入（产品名称、类别、价格、图像URL、可用性）
- [ ]行为事件架构包含链接到目录项目的项目/产品标识符
- [ ]数据流配置为启用[!DNL Adobe Journey Optimizer]服务（Edge决策所必需的）
- [ 已配置与`isActiveOnEdge: true`的]合并策略（实时Web/应用程序推荐所必需的）
- [ ]对于电子邮件推荐（选项C）：已配置并验证电子邮件渠道平面
- [ ]对于电子邮件推荐（选项C）：已定义目标受众并评估

## 实施选项

以下选项描述了实施行为推荐的不同方法。 选择最符合您的渠道要求和技术限制的选项。

### 选项A：Web实时推荐

**最适合：**&#x200B;网页上的产品或内容推荐 — 产品详细信息页面交叉销售小组件、主页推荐轮播、类别页面个性化列表和搜索结果个性化。

**工作方式：**

在访客浏览网站时，通过[!DNL Web SDK]实时收集行为信号。 每个页面查看、产品交互或搜索查询都将流式传输到AEP并与访客的配置文件相关联（对于匿名访客通过ECID，对于已知访客通过身份验证后产生的身份）。 加载包含推荐表面的页面时，[!DNL Web SDK]通过[!DNL Edge Network]向AJO请求决策评估。 决策引擎根据选择策略评估访客的行为配置文件，应用排名逻辑，过滤掉不合格项目（已购买、缺货），并返回推荐项目。

推荐是通过基于代码的体验或Web渠道表面在页面上呈现的。 渲染可以是轮盘、网格、单项小部件或推荐模板中定义的任何自定义布局。 “展示次数”和“点击次数”事件会自动跟踪回AEP以报告性能。

**关键注意事项：**

- Edge决策要求合并策略在Edge上处于活动状态
- 推荐延迟取决于[!DNL Edge Network]响应时间（对于单范围请求，SLA小于500毫秒）
- 匿名访客会收到基于会话中行为的推荐；已知访客从跨会话行为历史记录中受益
- 没有行为历史的冷启动访客将收到回退建议

**优点：**

- 基于会话内行为的实时个性化
- 通过[!DNL Edge Network]进行的次秒推荐投放
- 适用于匿名和已知访客
- 自动展示和点击跟踪
- 新推荐不需要重新加载页面

**限制：**

- Edge配置文件存储包含完整配置文件属性的子集
- 具有许多用户档案属性的复杂排名模型可能需要中心端评估
- 需要具有行为事件跟踪的[!DNL Web SDK]部署

**Experience League：**

- [使用Edge Decisioning API提供优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)

### 选项B：移动应用程序推荐

**最适合：**&#x200B;应用程序内产品推荐、个性化内容馈送、通知驱动推荐和移动商务体验。

**工作方式：**

用户与应用程序交互时，通过[!DNL Mobile SDK]收集行为信号。 产品查看、内容交互、搜索和购买将流式传输到AEP。 加载包含推荐表面的屏幕时，[!DNL Mobile SDK]请求决策评估。 推荐是通过应用程序内消息、内容卡或移动应用程序中基于代码的体验来交付的。

内容卡特别适合移动设备应用程序中的推荐用例，因为它们会持续保留在信息源之类的体验中，以便用户方便时浏览。 应用程序内消息可用于由特定行为触发的上下文推荐（例如，在将项目添加到购物车后显示补充产品）。

**关键注意事项：**

- [!DNL Mobile SDK]必须为相关交互配置行为事件跟踪
- 内容卡提供持久性推荐表面；应用程序内消息是短暂的
- 离线行为跟踪需要SDK队列管理才能提交延迟事件
- 应用商店更新周期会影响推荐呈现更改的部署速度

**优点：**

- 具有流畅、应用程序集成的推荐呈现功能的本机移动体验
- 内容卡提供持久、可浏览的推荐信息源
- 应用程序内消息启用情境式、行为触发的建议
- 利用设备级信号（位置、应用程序使用模式）增强相关性

**限制：**

- 需要[!DNL Mobile SDK]集成和应用程序开发资源
- 渲染更改需要应用程序更新（除非使用基于代码的体验搭配服务器驱动的布局）
- 离线周期会在行为信号收集中产生间隙

**Experience League：**

- [移动SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 选项C：电子邮件行为推荐

**最适合：**&#x200B;电子邮件营销活动中的产品推荐 — 已放弃的浏览带有已查看的产品推荐的电子邮件、购买后交叉销售电子邮件、定期“为您挑选”摘要，以及带有个性化产品建议的重新参与电子邮件。

**工作方式：**

在电子邮件发送时或呈现时，从先前会话累积的行为配置文件数据会通知推荐选择。 受众被定义为定向相应的收件人（例如，浏览但未购买的访客、最近购买的客户）。 营销活动或历程配置为发送包含推荐投放位置的电子邮件。 在发送时，AJO Decisioning会根据选择策略评估每个收件人的行为配置文件，并将推荐的项目注入电子邮件内容。

此选项依赖于累积的行为历史，而不是会话中的信号。 计算属性（类别亲和度分数、最近产品查看次数、购买频率）显着提高了电子邮件的推荐质量，因为它们将行为历史记录提取到个人资料级别信号中，而选择策略可以有效地评估这些信号。

**关键注意事项：**

- 在发送时而不是打开时评估电子邮件推荐 — 发送时的行为配置文件状态决定了推荐
- 强烈建议使用计算属性来提高排名质量
- 电子邮件渲染限制（无JavaScript，CSS受限）会约束推荐显示格式
- 需要已配置并验证的电子邮件渠道界面

**优点：**

- 利用各个会话中的完整行为历史记录进行更深入的个性化
- 与现有活动和历程工作流集成
- 对于无法使用Web/应用程序接触点的重新参与和回馈方案有效
- 可以在一封电子邮件中包含多个推荐投放

**限制：**

- 推荐在发送时是静态的 — 它们在电子邮件打开时不会更新
- 电子邮件渲染约束限制了推荐显示格式
- 需要受众评估和活动/历程编排基础架构
- 由于额外的依赖项（渠道配置、受众定义、活动执行），实施复杂性更高

**Experience League：**

- [创建电子邮件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### 选项比较

下表总结了实施选项之间的主要差异。

| 标准 | 选项A：Web实时 | 选项B：移动设备应用程序 | 选项C：电子邮件行为 |
| --- | --- | --- | --- |
| 最适合 | 网页推荐（PDP、主页、类别） | 应用程序内推荐和内容馈送 | 通过电子邮件发送包含产品推荐的营销活动 |
| 行为信号源 | 会话内+跨会话([!DNL Web SDK]) | 应用程序内交互([!DNL Mobile SDK]) | 累计行为历史记录（个人资料） |
| 推荐延迟 | 子秒([!DNL Edge Network]) | 子秒([!DNL Edge Network]) | 在发送时（中心端评估） |
| 访客类型 | 匿名和已知 | 已知（应用程序用户） | 已知（电子邮件收件人） |
| 复杂性 | 中 | Medium — 高 | 高 |
| 渠道依赖关系 | [!DNL Web SDK]，基于代码的体验表面 | [!DNL Mobile SDK]，应用程序内/内容卡表面 | 电子邮件渠道界面、受众、营销活动/历程 |
| 需要 | [!DNL Web SDK]部署，Edge合并策略 | [!DNL Mobile SDK]部署，Edge合并策略 | 电子邮件界面、受众定义、活动设置 |

### 选择正确的选项

请遵循以下指南为您的情况选择最佳选项：

- 如果您的主要目标是网站上的实时产品推荐，请&#x200B;**从选项A**&#x200B;开始。 这是最常见的起点，它以最低的实施复杂性提供了立竿见影的价值。
- **如果您的移动应用程序是主要参与渠道，并且应用程序内推荐将提高有意义的转化，请选择选项B**。 选项B可以使用相同的选择策略和物料目录与选项A并行运行。
- **在要将行为推荐扩展到电子邮件营销活动中时添加选项C**。 这通常位于选项A或B之上，使用相同的项目目录和选择策略，但使用特定于电子邮件的渲染模板和基于受众的定位。
- **将选项A + C**&#x200B;合并为一个通用模式：适用于活动访客的实时Web推荐，以及适用于离开但未进行转化的访客的放弃浏览或购买后电子邮件推荐。

## 实施阶段

以下阶段将指导您完成行为推荐的端到端实施。

### 阶段1：配置行为事件模式和数据收集

**应用程序函数：** AEP：数据建模和准备(F2)，AEP：数据源和收集(F3)

此阶段建立可捕获行为信号和项目目录数据的XDM架构、数据集和数据收集机制。 所有推荐逻辑都依赖于此数据基础。

#### 决策：行为事件模式设计

哪些行为信号应会驱动推荐？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅限产品查看 | 简单的交叉销售/追加销售推荐 | 实施工作量最低；信号深度有限 |
| 产品查看次数和购买次数 | 具有购买排除和交叉销售逻辑的建议 | 适度努力；启用“排除已购买”的筛选条件 |
| 完整行为套件（查看、购买、添加到购物车、搜索、内容交互） | 具有多信号排名的复杂推荐 | 信号质量最高；需要全面的[!DNL Web SDK]/[!DNL Mobile SDK]检测 |

#### 决策：物料目录摄取方法

产品或内容目录将如何引入到AEP中？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 通过源连接器批量摄取 | 定期进行目录更新（每日/每周） | 设置更简单；目录更改未实时反映 |
| 流式摄取 | 目录需要近乎实时的更新（价格变化、可用性） | 更复杂；确保推荐反映当前库存 |
| 手动/API上传 | 不经常更改的小目录 | 设置最简单；不适用于大型或动态目录 |

**UI导航：**&#x200B;数据管理>架构>创建架构；数据收集>数据流>新建数据流

**密钥配置详细信息：**

- 体验事件架构必须在事件有效负载中包含产品/项目标识符（SKU、产品ID、内容ID）
- 项目目录架构应包括用于筛选和排名的属性：类别、价格、图像URL、可用性状态、标记
- 数据流必须为Edge决策启用[!DNL Adobe Journey Optimizer]服务
- [!DNL Web SDK] `sendEvent`调用必须包含映射到XDM商务字段的产品交互数据

**Experience League文档：**

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [定义两个架构之间的关系](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### 阶段2：配置标识和配置文件

**应用程序函数：** AEP：标识和配置文件配置(F4)

此阶段将设置身份命名空间、主要身份指定和合并策略，以确保行为信号与访客配置文件正确关联并可用于实时推荐交付。

#### 决策：Edge决策的合并策略

推荐用例是否需要实时Edge评估？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 对Edge合并策略有效 | 选项A和B（Web和移动实时推荐） | 对于次秒推荐交付，此变量是必需的；每个沙盒仅有一个Edge合并策略 |
| 标准合并策略（不在Edge上） | 仅选项C（在发送时评估电子邮件推荐） | 足以进行中心端评估；不会占用Edge合并策略插槽 |

#### 决策：匿名与已知访客身份

如何处理来自匿名访客的行为信号？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅限ECID（匿名） | 推荐主要基于会话中行为的匿名访客 | 设置更简单；除非访客进行身份验证，否则无跨会话连续性 |
| ECID +经过身份验证的身份（CRM ID、电子邮件） | 面向具有身份拼接的已知访客的跨会话推荐 | 更丰富的行为配置文件；需要身份验证流程 |
| 两者均具有标识图链接 | 具有身份拼接的完全匿名与已知历程 | 最全面；需要身份关联规则配置 |

**UI导航：**&#x200B;身份>身份命名空间；配置文件>合并策略

**密钥配置详细信息：**

- [!DNL Web SDK]和[!DNL Mobile SDK]已预配置并自动使用ECID命名空间
- 必须为经过身份验证的标识创建自定义标识命名空间（CRM ID、忠诚度ID）
- 体验事件架构上的主要标识应该是Web/移动行为事件的ECID
- 合并策略必须使用专用设备图形进行跨设备的身份拼合

**Experience League文档：**

- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [身份标识图链接规则](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)

### 阶段3：设置物料目录和选择策略

**应用程序功能：** AJO： Decisioning

此阶段配置项目目录（决策项目）、将行为信号与项目属性相结合以进行排名的选择策略、用于排除不合格项目的过滤规则，以及冷启动配置文件的备用推荐。

#### 决定：物料目录范围

哪些项目可供推荐？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 产品目录（电子商务） | 推荐购买的物理或数字产品 | 项目属性包括价格、类别、可用性、图像 |
| 内容目录（媒体/发布） | 推荐文章、视频或教育内容 | 项目属性包括主题、作者、发布日期、内容类型 |
| 混合目录 | 推荐产品和内容 | 需要统一的项目架构来容纳这两种类型 |

#### 决策：排名方法

应该如何对符合条件的项目进行排名以确定最佳推荐？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 基于公式的排名 | 清除排名的业务逻辑（例如，按类别亲和度得分乘以项目热门程度排序） | 透明、可审核的排名；需要定义的排名公式 |
| AI排名（自动优化） | 机器学习应根据转化数据确定最佳排名 | 需要至少1,000个转化事件才能进行模型训练；透明度较低 |
| 基于优先级（手动） | 简单、手动策划的推荐排序 | 最易于配置；不适应个人行为 |

#### 决策：筛选规则

应从推荐中排除哪些项目？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 排除已购买的项目 | 交叉销售和发现推荐 | 需要行为配置文件中的购买历史记录 |
| 排除缺货商品 | 使用动态库存的电子商务 | 需要实时或近乎实时的目录更新 |
| 排除之前已取消的项目 | 用户可以驳回建议的内容建议 | 需要在行为事件中进行解除跟踪 |
| 类别范围的过滤 | 建议仅限于特定类别 | 使用项目属性进行筛选 |

#### 决定：冷启动战略

对于没有行为历史记录的新访客，应该显示什么？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 热门项目（全球畅销商品） | 通用后备 | 易于维护；未个性化 |
| 特定于类别的常用项目 | 访客已到达类别页面 | 与上下文相关的回退；需要页面上下文 |
| 精选的编辑精选 | 品牌希望对冷启动体验进行编辑控制 | 需要手动管理和更新 |
| 趋势项目（时间加权的人气） | 反映当前趋势的动态回退 | 需要趋势信号计算 |

**UI导航：** [!DNL Journey Optimizer] >组件>决策管理>决策；[!DNL Journey Optimizer] >组件>决策管理>优惠；[!DNL Journey Optimizer] >组件>决策管理>投放

**密钥配置详细信息：**

- 使用属性（类别、价格、图像URL、标记）创建表示目录中的每个产品或内容项目的决策项目
- 定义将项目目录过滤与行为排名逻辑相结合的选择策略
- 配置排名模型 — 基于公式的表达式可以引用配置文件属性（例如，计算属性中的类别亲和度分数）
- 创建用作冷启动配置文件的默认推荐的备用选件/项目
- 使用集合限定符（标记）将项目组织到集合中以进行逻辑分组
- 在选择策略中设置筛选规则以强制执行业务规则（不包括已购买、有货）

**Experience League文档：**

- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [创建投放位置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [创建决策规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [创建个性化优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [创建后备产品建议](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [创建集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [创建决策](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 阶段4：配置渠道和表面

**应用程序函数：** AJO：渠道配置

此阶段将配置将在其中呈现推荐的投放界面。 该配置因实施选项而异。

#### 决策：投放表面类型

推荐将显示在何处？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 基于代码的体验(Web) | 具有自定义渲染的网页上的推荐小组件 | 渲染的最大灵活性；需要前端开发 |
| Web渠道表面 | 标准Web个性化表面 | 使用AJO Web设计器；比基于代码的设计器更不灵活 |
| 应用程序内消息 | 由应用程序行为触发的上下文推荐 | 短暂；交互或解除后消失 |
| 内容卡（移动设备） | 移动应用程序中的持久推荐馈送 | 持续到用户执行操作为止；可浏览信息源体验 |
| 电子邮件 | 嵌入在电子邮件营销活动中的产品推荐 | 发送时为静态；受电子邮件渲染约束约束 |

**选项差异的位置：**

选项A （Web实时推荐）的&#x200B;**：**
配置基于代码的体验表面或Web渠道表面。 基于代码的体验为自定义推荐渲染（轮盘、网格、项目卡）提供了最大的灵活性。 表面URI用于标识推荐在页面上出现的位置。

选项B的&#x200B;**（移动应用推荐）：**
配置应用程序内消息或内容卡界面。 建议将内容卡用于持久推荐信息源。 应用程序内消息非常适用于情境式、行为触发的推荐。

选项C （电子邮件行为建议）的&#x200B;**：**
使用子域委派、IP池分配和发件人设置配置电子邮件渠道表面。 确保已验证表面的可交付性。

**UI导航：**&#x200B;管理>渠道>渠道界面>创建界面

**Experience League文档：**

- [设置渠道平面](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 阶段5：配置内容和投放

**应用程序函数：** AJO：消息创作

此阶段定义推荐呈现模板，用于控制向访客显示推荐项目的方式。 这包括项目布局设计、提取项目属性（名称、图像、价格、链接）的个性化表达式以及整体推荐体验设计。

#### 决策：推荐显示格式

应如何呈现推荐的项目？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 轮播（水平滚动） | 垂直空间受限的主页或类别页面 | 熟悉的UX模式；以紧凑的空间显示多个项目 |
| 网格（多行） | 具有充裕空间的专用推荐部分 | 一次显示更多项目；非常适用于“为您推荐”的部分 |
| 单个项目小组件 | 特定页面位置的上下文推荐（例如，侧栏） | 占用空间最小；高效能放置 |
| 内联电子邮件块 | 嵌入在电子邮件正文中的推荐 | 受电子邮件HTML/CSS约束；通常为2-4项 |

#### 决定：要显示的建议数量

每个投放位置应返回多少个决策项目？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 3-4项 | 标准推荐构件 | 平衡相关性与视觉密度 |
| 6-8项 | 具有滚动或网格布局的轮播 | 访客有更多的选项；需要足够的目录深度 |
| 1个项目 | 上下文单一产品推荐 | 最高的相关性影响；最简单的呈现 |
| 10个以上的项目 | 信息源样式推荐体验 | 内容密集型用例（媒体、发布） |

**选项差异的位置：**

选项A （Web实时推荐）的&#x200B;**：**
使用基于代码的体验模板设计推荐呈现。 使用HTML/CSS/JavaScript创建轮播布局、网格布局或小组件布局。 Personalization表达式引用决策响应属性（项目名称、图像URL、价格、产品URL）。 展示和点击跟踪由[!DNL Web SDK]自动处理。

选项B的&#x200B;**（移动应用推荐）：**
使用项目显示逻辑配置内容卡或应用程序内消息模板。 使用移动设备应用程序本机呈现的基于JSON的内容结构。 包含每个推荐项目的深层链接。

选项C （电子邮件行为建议）的&#x200B;**：**
使用电子邮件Designer设计电子邮件内容。 使用决策支持的内容块插入推荐投放位置。 为电子邮件模板中的项目属性配置个性化表达式。 主题行个性化可引用顶级推荐项目。

**UI导航：**&#x200B;内容管理>内容模板；营销活动/历程>编辑内容>向Designer发送电子邮件

**密钥配置详细信息：**

- 每个推荐投放都必须引用阶段3中创建的决策
- Personalization表达式使用Handlebars语法呈现项目属性
- 对于Web：配置基于代码的体验，以调用决策并呈现响应
- 对于电子邮件：将决策嵌入到营销活动或历程的电子邮件操作中
- 使用具有已知行为历史记录的测试配置文件预览推荐

**Experience League文档：**

- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### 阶段6：设置受众范围界定和活动/历程（仅限选项C）

**应用程序函数：** RT-CDP：受众评估、AJO：营销活动执行或Journey Orchestration

对于基于电子邮件的推荐（选项C），此阶段定义目标受众，并配置用于发送推荐电子邮件的营销活动或历程。 选项A和B会跳过此阶段，因为推荐会在页面/屏幕加载时实时交付。

#### 决策：受众评估方法

应如何评估推荐电子邮件的目标受众？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 批次评估 | 计划的推荐电子邮件营销活动（每日、每周摘要） | 可预测的发送时间；在发送前评估受众 |
| 流式处理评估 | 事件触发的推荐电子邮件（放弃的浏览、购买后） | 近乎实时的受众鉴别；与Journey Orchestration配对 |

#### 决定：交付机制

电子邮件应该通过营销活动还是历程投放？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 计划的营销活动 | 一次性或定期推荐电子邮件突发到定义的受众 | 更简单的设置；批量受众评估和发送 |
| 使用audience entry进行历程 | 受众资格触发的持续推荐电子邮件 | 启用多步骤流程（例如，推荐电子邮件后跟提醒） |
| 事件触发的历程 | 特定事件触发的建议电子邮件（浏览放弃、购买） | 实时触发；需要基于事件的历程条目 |

**UI导航：**&#x200B;客户>受众>创建受众>生成规则；营销活动>创建营销活动；历程>创建历程

**密钥配置详细信息：**

- 使用引用行为历史记录（例如，“过去7天内查看过产品但未购买”）的区段规则表达式定义目标受众
- 使用引用阶段4中的渠道表面的电子邮件操作配置营销活动或历程
- 将阶段3中的决策嵌入到电子邮件内容中
- 设置计划和频率规则以避免过度发送消息

**Experience League文档：**

- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [营销活动实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)

### 阶段7：配置报告和优化

**应用程序功能：** AJO： Reporting &amp; Performance Analysis， S5： Reporting &amp; Analysis

此阶段建立了对推荐点进、转化和收入量度的性能监控。 它创建了报告基础架构，以衡量推荐有效性并确定优化机会。

#### 决策：报告深度

需要什么级别的报表分析？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅限AJO本机报表 | 基本推荐性能监控 | 快速设置；仅限于AJO跟踪的指标 |
| AJO + [!DNL Customer Journey Analytics]集成 | 跨渠道推荐影响分析和收入归因 | 需要[!DNL Customer Journey Analytics]连接和数据视图；提供更深入的见解 |
| 具有自定义功能板的完整[!DNL Customer Journey Analytics]工作区 | 具有项目级、区段级和曲面级分析的持续优化程序 | 最全面；需要[!DNL Customer Journey Analytics]专业知识和设置 |

**UI导航：**&#x200B;营销活动>选择营销活动>所有时间报表；历程>选择历程>所有时间报表；[!DNL Customer Journey Analytics] >项目>创建新项目

**密钥配置详细信息：**

- 查看AJO营销活动和历程报告的交付和参与量度
- 对于[!DNL Customer Journey Analytics]集成，请创建包含AJO体验事件数据集（消息反馈、电子邮件跟踪、决策）的连接
- 使用特定于推荐的维度（项目名称、项目类别、推荐表面）和量度（展示次数、点击次数、转化次数、收入）创建[!DNL Customer Journey Analytics]数据视图
- 为推荐CTR、转化率和每次展示收入构建计算量度
- 创建[!DNL Customer Journey Analytics]个工作区面板，比较跨表面、区段和时间段的推荐性能

**Experience League文档：**

- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [创建或编辑连接](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [创建或编辑数据视图](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [计算量度概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

## 实施注意事项

在实施之前和期间，请查看以下护栏、隐患、最佳实践和权衡。

### 护栏和限制

- 每个沙盒最多10,000个批准的个性化优惠（决策项） — [决策管理护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每个决策最多30个投放位置
- 每个决策请求最多30个收集范围
- 选件交付响应时间SLA：在P95时，对于单范围Edge请求，少于500毫秒
- 人工智能排名模型需要至少1,000个转化事件才能进行训练
- 在高吞吐量情况下，选件上限计数器可能会有高达几秒钟的延迟
- Edge决策仅限于Edge Profile Store中可用的配置文件属性
- 每个沙盒只能有一个合并策略在Edge上处于活动状态 — [配置文件护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 每个沙盒最多有25个活动计算属性 — [计算属性护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- 每个沙盒最多4,000个区段定义 — [分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 流式摄取：每个HTTP连接每秒最多20,000条记录 — [摄取护栏](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### 常见陷阱

- **决策仅返回回退项：**&#x200B;验证个性化决策项是否在其有效日期范围内获得批准，以及资格规则是否与访客的配置文件属性相匹配。 检查是否尚未达到上限限制。
- **Edge投放返回空的个性化设置：**&#x200B;请确保数据流配置为启用[!DNL Adobe Journey Optimizer]服务，并且决策范围在[!DNL Web SDK]请求中的格式正确。
- **未应用排名公式：**&#x200B;请验证公式语法有效并且引用了可访问的配置文件属性。 公式错误会静默地回退到基于优先级的排名。
- **过时推荐：**&#x200B;如果行为事件数据未实时流动，推荐将基于过时的行为配置文件。 验证[!DNL Web SDK]或[!DNL Mobile SDK]是否正在主动流式传输事件。
- **冷启动回退率过高：**&#x200B;如果很大一部分访客收到回退建议，请考虑使用上下文信号（当前页面类别、反向链接来源）丰富冷启动策略，而不是仅依赖行为历史记录。
- **推荐未在页面上呈现：**&#x200B;请验证基于代码的体验表面URI是否与页面URL模式匹配，以及[!DNL Web SDK]是否正确请求和呈现决策响应。
- **推荐中缺少目录项：**&#x200B;请确保所有目录项都已作为决策项引入，使用正确的集合限定符进行标记，并包含在选择策略引用的相应集合中。

### 最佳实践

- 在投资于AI排名模型之前，先从使用计算属性（类别亲和度、交互回访间隔）的基于公式的排名模型开始。 基于公式的模型是透明的、可审核的，并且提供了用于比较的实体基线。
- 从第一天开始实施展示和点击跟踪。 如果没有交互数据，AI排名模型就无法训练，并且您无法衡量推荐有效性。
- 为不同的推荐表面（主页、PDP、电子邮件）创建单独的选择策略，而不是在任何地方重用单个策略。 不同的表面服务于不同的用户意图。
- 使用计算属性将行为历史记录提取到排名信号中。 原始事件数据过于细化，无法进行有效的基于公式的排名；汇总信号（如“类别亲和度分数”和“上次购买间隔天数”）的效果更佳。
- 将后备推荐与个性化推荐分开测试。 确保后备项目是优质、适合品牌的预设，为新访客提供良好的体验。
- 监控冷启动回退率，将其作为关键运行状况量度。 随着时间的推移，回退率不断下降表明行为覆盖范围不断扩大。
- 对于电子邮件推荐，计划会在行为配置文件最完整的时段发送（例如，在浏览高峰时间后发送，而不是在浏览高峰期发送）。

### 权衡决定

应根据您的特定要求评估以下权衡。

#### 实时信号与累计历史记录

会话中行为信号提供直接的相关性，但深度有限。 累积的行为历史记录提供了深度，但可能会过时。 这些源之间的平衡会影响推荐质量。

- **选项A支持：**&#x200B;即时相关实时信号，辅以已知访客的累积历史记录
- **选项C支持：**&#x200B;独占累计历史记录，因为电子邮件是异步发送的
- **推荐：**&#x200B;对于Web和移动设备（选项A、B），将会话内信号与从历史行为派生的计算属性相结合。 对于电子邮件（选项C），请大量投资计算属性，这些属性将行为历史记录总结为可操作的个人资料级别信号。

#### 基于公式的模型与AI排名模型

基于公式的排名是透明且直接的。 AI排名模型会自动调整，但需要训练数据，并且排名决策的可见性较低。

- **基于公式的优惠：**&#x200B;对排名逻辑的透明度、可审计性、即时部署和细粒度业务控制
- **AI排名优惠：**&#x200B;自动优化、发现不明显的模式，并减少手动调整工作
- **建议：**&#x200B;从基于公式的排名开始，以建立性能基线并累计转化数据。 只要您有足够的培训数据（1,000多个转化事件），并且希望优化超过手动公式调整所能达到的效果，就可以过渡到AI排名模型。

#### 推荐的覆盖范围与相关性

扩展项目目录和放松筛选规则会增加收到个性化推荐的请求的百分比，但可能会降低每个推荐的相关性。

- **高覆盖率优惠：**&#x200B;最大限度地增加查看个性化推荐的访客数量；当主要目标是参与时非常有用
- **高相关性支持：**&#x200B;只显示高度相关的项目，即使这意味着更多访客会看到后备推荐；当主要目标是转化时，非常有用
- **推荐：**&#x200B;从适度筛选开始（排除已购项目、缺货项目）并监视回退率和转化率。 仅当转化数据支持筛选规则时，才应加强筛选规则。

#### Personalization深度与实施复杂性的比较

更丰富的行为信号和更复杂的排名模型提高了推荐质量，但增加了实施复杂性和维护负担。

- **更简单的实施优点：**&#x200B;更快的价值实现、更少的维护、更易于调试和迭代
- **更深入的个性化优惠：**&#x200B;更高的转化率、更好的客户体验、竞争优势互补
- **推荐：**&#x200B;分阶段实施。 从产品查看信号和基于公式的排名开始（阶段1）。 添加用于行为扩充的计算属性（阶段2）。 一旦基础成熟并有足够的训练数据可用，即评估人工智能排名模型（第3阶段）。

## 相关文档

以下资源提供了有关在此模式中使用的技术和功能的更多详细信息。

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
- [使用Edge Decisioning API提供优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### 数据收集和Web/移动SDK

- [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [安装Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [移动SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Edge Network Server API概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### XDM和数据建模

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [创建数据集](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create)
- [定义两个架构之间的关系](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### 身份和配置文件

- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Real-time Customer Profile概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### 受众和分段

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### 计算属性和配置文件扩充

- [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [计算属性UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Customer AI概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### 渠道配置

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [设置渠道平面](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### 消息创作和个性化

- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### 报告和分析

- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [计算量度概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### 数据治理和生命周期

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [数据集过期时间](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### 监控和可观察性

- [可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

### 护栏

- [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [摄取护栏](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Identity服务护栏](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)

### 教程和指南

- [源概述](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [标记概述](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
- [同意和偏好设置字段组](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
