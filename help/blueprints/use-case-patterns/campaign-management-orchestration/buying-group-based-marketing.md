---
title: 购买基于群组的营销和历程管理
description: 了解如何开发帐户级别的历程，使潜在客户有资格加入购买组，以提高B2B营销效率。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 2bf57f67-80c8-4368-98d2-05706427772d
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7932'
ht-degree: 0%

---

# 购买基于群组的营销和历程管理

本指南为购买基于群组的营销和历程管理提供了全面的实施参考。 它面向需要通过使用[!DNL Adobe Journey Optimizer B2B Edition]和[!DNL Real-Time CDP B2B Edition]购买群组管理来实施帐户级历程编排的解决方案架构师、营销技术人员和实施工程师。

使用本文档了解要配置哪些内容、在何处存在实施选择以及促成每项决策的是哪些利弊得失。

与人员级别的历程模式不同，此模式在帐户级别运行，确定与解决方案兴趣相关的购买组的个人商机，在购买组级别评分参与度，并编排多步骤帐户历程，将帐户通过管道阶段进展到销售准备情况。

## 用例概述

B2B组织面临一个根本性的挑战：购买决策很少由一个人做出。 复杂的B2B购买涉及多个利益相关者 — 决策者、影响者、支持者、预算持有人和技术评估者 — 他们共同组成一个“购买群体”。 传统的基于潜在客户的营销方式会单独对待每个人，忽略了一个关键信号，即客户中适当的角色组合是否参与并准备购买。

购买基于群组的营销和历程管理可通过将编排单位从个人商机转移到帐户和购买群组来解决此问题。 通过使用该模式，B2B营销人员可以定义解决方案兴趣（正在销售的产品或服务），创建购买组模板，以指定购买决策所需的角色，根据这些角色确定传入商机的资格，在购买组级别对参与度进行评分，以及编排响应购买组完整性和就绪信号的客户历程。

期望的结果是提高渠道质量和速度：只有当客户中的适当人员参与进来，并且买方小组已充分完成时，营销人员才会将客户提供给销售人员，从而减少浪费的销售工作并加快交易进度。

## 主要业务目标

此用例模式支持以下业务目标。

### 改进潜在客户资格鉴定和转化

通过评分、培养和个性化的跟进，提高销售线索质量并加快管道进度。

**KPI：**&#x200B;潜在客户转化、潜在客户/潜在客户转化、效率

[了解有关改进潜在客户资格和转化的更多信息](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### 增加商机开发

通过表单、事件、内容和多渠道参与，为销售渠道生成更多符合条件的潜在客户。

**KPI：**&#x200B;潜在客户、每个潜在客户的成本、潜在客户转化

[了解有关提高商机开发率的更多信息](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### 增加收入和销售

通过优化的数字渠道、营销活动和客户历程推动总收入增长。

**KPI：**&#x200B;收入增长、管道周转率、交易完成率

[了解有关增加收入和销售额的更多信息](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

## 战术用例示例

以下是可以应用此模式的特定方案。

- **特定于解决方案的购买群组资格** — 使用指定所需角色（经济购买者、技术评估人员、冠军、最终用户）的角色模板为每个产品线（例如，“企业CRM”、“数据平台”、“安全套件”）定义购买群组，并根据这些角色确认CRM和营销自动化系统中的潜在客户。
- **用于管道加速的帐户历程** — 编排一个多步骤帐户历程，该历程向购买组中未充分参与的角色发送有针对性的培训电子邮件，在达到参与阈值时触发销售警报，并将帐户过渡至销售就绪阶段。
- **购买团体完整性促销活动** — 识别购买团体缺少角色的帐户（例如，未识别经济购买者），并启动定向的客户获取促销活动以吸引这些帐户中的正确角色。
- **交叉销售帐户历程** — 在初始交易完成后，为补充解决方案兴趣创建新的购买组，并协调客户历程，以培养扩展的购买委员会。
- **重新参与停滞的交易** — 检测购买团体参与分数已下降的帐户，并通过新内容、执行外联或活动邀请触发重新参与历程。
- **通过CRM见解进行销售和营销协调** — 直接在[!DNL Salesforce]或[!DNL Dynamics 365]内显示购买组状态、参与数据和帐户历程进度，以便销售代表能够实时查看符合营销条件的帐户。
- **事件驱动的购买群组更新** — 当潜在客户参加网络研讨会、下载白皮书、访问定价页面或请求演示时，自动更新购买群组会员资格和参与度分数。
- **多区域帐户协调** — 管理全球帐户中的购买组，其中不同的区域联系人担任不同的角色，统一不同地理区域的参与度评分。

## 关键绩效指标

以下KPI有助于衡量此用例模式的有效性。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 购买组完整率 | 已填写所有所需角色的购买组的百分比 | [!DNL AJO B2B] Analytics功能板：跟踪每个购买群组的角色覆盖率 |
| 购买团体参与度分数 | 购买组所有成员的总参与度分数 | [!DNL AJO B2B]参与度得分：个人级别得分汇总到购买团体 |
| 营销合格帐户(MQA)比率 | 达到营销资格阈值的帐户百分比 | 帐户历程退出标准：帐户正在过渡到“销售就绪”阶段 |
| 管道速度 | 从购买组创建到销售合格商机的平均时间 | CRM集成：跟踪从[!DNL AJO B2B]到CRM管道的暂存过渡 |
| 采购线索组资格率 | 成功获得购买群组角色资格的潜在客户百分比 | [!DNL AJO B2B]购买群组管理：合格与不合格的潜在客户比率 |
| 销售警报响应率 | 导致销售跟踪活动的销售警报百分比 | CRM销售分析：跟踪警报到活动的转换 |
| 帐户历程完成率 | 完成预期历程路径的帐户百分比 | [!DNL AJO B2B] Analytics功能板：历程完成量度 |
| 电子邮件参与率(B2B) | B2B培养电子邮件的打开率和点进率 | [!DNL AJO B2B]报告：电子邮件投放和参与量度 |

## 用例模式

**购买基于群组的营销和历程管理**

开发客户级别的历程，使潜在客户有资格加入购买群体，以提高B2B营销效率。

**功能链：**&#x200B;客户识别>购买组定义>潜在客户资格>客户历程执行>参与度评分>报告

## 应用程序

在此用例模式中使用以下Adobe应用程序。

- **[!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])** — 编排帐户级别的历程，通过角色模板和解决方案兴趣来管理购买组，在人员和购买组级别对参与情况进行评分，作者B2B电子邮件内容，发送SMS消息，配置销售警报，并提供B2B分析功能板。
- **[!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])** — 从跨源B2B数据统一帐户配置文件，解析人员与帐户的关系，评估帐户级别的受众，配置特定于B2B的目标([!DNL Marketo Engage]、[!DNL LinkedIn]、CRM)，并跨B2B数据实施数据管理。

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本函数 | 状态 | 必须准备好的内容 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 必填 | 沙盒配置了[!DNL AJO B2B Edition]和[!DNL RT-CDP B2B Edition]授权。 为B2B营销人员、销售操作和管理员配置的角色，这些角色具有购买群组管理、帐户历程和CRM集成设置的适当权限。 | [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)，[访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | 使用特定于B2B的类配置的B2B XDM架构：XDM业务帐户、XDM业务机会、XDM业务人员（潜在客户/联系人）、XDM业务营销活动和XDM业务营销列表。 帐户属性、人员属性和活动/参与数据的字段组必须到位。 为每个架构创建并启用配置文件的数据集。 | [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[B2B架构类](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| 数据源和收集 | 必填 | 已建立B2B数据摄取管道，通常通过[!DNL Marketo Engage]源连接器或[!DNL Salesforce]/[!DNL Dynamics] CRM源连接器建立。 客户、人员、机会、营销活动和营销活动成员数据必须流入AEP数据集。 还必须引入行为参与数据（Web访问、电子邮件交互、内容下载）以进行参与度评分。 | [源概述](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)，[Marketo Engage连接器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| 身份和配置文件配置 | 必填 | B2B身份解析配置为解析人员与帐户的关系。 B2B标识符的标识命名空间（[!DNL Marketo]个人ID、[!DNL Salesforce]潜在客户/联系人ID、帐户ID）必须存在。 为B2B配置文件统一配置的合并策略。 帐户配置文件必须与跨源数据统一。 | [身份服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[B2B身份解析](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) |
| 受众定义和分段 | 必填 | 使用帐户属性、人员属性和活动数据创建的帐户级别受众定义。 客户受众可识别哪些客户进入购买团体历程。 批量评估通常足以满足B2B帐户历程的需求，但流式评估可用于实时帐户资格触发器。 | [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences) |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么它很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 推荐 | 计算属性可以将人员级别的参与事件（电子邮件打开、内容下载、网络研讨会出席情况）汇总到帐户级别的参与量度中，以便提供购买团体评分和帐户资格逻辑。 | [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 数据生命周期管理 | 推荐 | 同意管理对于B2B电子邮件和短信通信至关重要。 数据集到期策略可帮助管理临时参与数据的生命周期，并确保遵守数据保留要求。 | [高级数据生命周期管理](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 数据使用标签和执行 | 推荐 | B2B数据通常包含敏感的公司信息和业务联系人的个人数据。 数据治理策略可确保跨目标合规地使用B2B数据，尤其是在激活到广告平台或第三方系统时。 | [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| 监视和可观察性 | 推荐 | 监视可确保B2B数据管道（CRM/[!DNL Marketo]同步）运行正常、帐户配置文件正在更新，以及帐户历程执行正在继续且没有失败。 针对源数据流故障发出警报对于保持数据货币至关重要。 | [可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 报告和分析 | 已包含 | [!DNL AJO B2B Edition]内的B2B分析功能板提供购买团体参与度、帐户历程绩效和管道量度。[!DNL CJA B2B Edition] 通过帐户级别的工作区分析、购买组分析和机会关联扩展分析。 | [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## 应用程序功能

此计划从应用程序功能目录中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 解决方案兴趣配置 | 第1阶段：解决方案兴趣和购买团体设置 | 定义将产品或服务映射到购买团体资格标准的解决方案兴趣 |
| 购买群组管理 | 第1阶段：解决方案兴趣和购买团体设置 | 使用角色模板、角色映射和解决方案兴趣定义创建和管理购买组 |
| 帐户Journey Orchestration | 阶段3：客户历程设计和执行 | 通过条件、操作和基于参与的分支来设计和管理多步骤客户历程 |
| 参与度评分 | 阶段2：潜在客户资格和参与度评分 | 对购买团体中的个人级别参与度评分，以衡量购买团体完整性和准备情况 |
| 帐户资格 | 阶段2：潜在客户资格和参与度评分 | 使用AI支持的帐户资格代理评估帐户准备情况和管道质量 |
| B2B电子邮件创作 | 阶段3：客户历程设计和执行 | 使用模板、可视化片段、品牌主题和AI辅助内容生成创建B2B电子邮件内容 |
| 短信渠道管理 | 阶段3：客户历程设计和执行 | 配置和管理B2B帐户历程中的短信通信 |
| 销售警报配置 | 第4阶段：销售协调和CRM集成 | 配置销售警报电子邮件以通知销售团队帐户参与里程碑和购买信号 |
| CRM销售分析 | 第4阶段：销售协调和CRM集成 | 提供CRM内的可见性([!DNL Salesforce]， [!DNL Dynamics])，以便了解购买组状态、参与数据和帐户历程进度 |
| B2B Analytics功能板 | 阶段5：报告和优化 | 通过智能和参与仪表板，监控帐户历程表现、购买团体参与和管道量度 |

### [!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 帐户个人资料统一 | 阶段0：B2B数据基础 | 使用专门的XDM B2B架构类和字段组将跨源B2B数据整合到统一的帐户配置文件中 |
| B2B身份解析 | 阶段0：B2B数据基础 | 使用主要标识符解决人员与帐户的关系，支持多级帐户层次结构和多对多人员与帐户映射 |
| 帐户受众评估 | 阶段0：B2B数据基础 | 评估结合帐户属性、人员属性和活动数据的帐户级别区段成员资格 |
| 帐户目标配置 | 第4阶段：销售协调和CRM集成 | 使用帐户级别字段映射配置与特定于B2B的目标（[!DNL Marketo Engage]、[!DNL LinkedIn]、CRM系统）的连接 |
| 帐户Audience Activation | 第4阶段：销售协调和CRM集成 | 将基于帐户的受众发布到目标，以实现基于帐户的定位和禁止 |
| [!DNL Marketo Engage]集成 | 阶段0：B2B数据基础 | 使用本机B2B源和目标连接器，通过[!DNL Marketo Engage]双向摄取和激活数据 |
| B2B数据管理 | 阶段0：B2B数据基础 | 跨B2B帐户数据集中和激活过程实施数据使用策略和同意 |

## 先决条件

请在开始实施之前完成以下操作。

- [ ] [!DNL AJO B2B Edition]许可证已在目标沙盒中配置并启用
- [ ] [!DNL RT-CDP B2B Edition]许可证已在目标沙盒中配置并启用
- [ ] CRM系统（[!DNL Salesforce]或[!DNL Microsoft Dynamics 365]）可使用适当的API凭据进行双向数据同步访问
- [ 已连接] [!DNL Marketo Engage]实例（如果使用[!DNL Marketo]作为营销自动化平台），并配置了源连接器
- [ ]个B2B XDM架构已部署：具有必填字段组的Account、Person、Opportunity、Campaign和Campaign成员类
- [ 已将]帐户和人员数据摄取到AEP，并解决了人员与帐户的关系
- [ 已配置]电子邮件渠道：委派子域、已预热的IP池，以及为B2B电子邮件发送创建的渠道表面
- [ 已配置]个短信提供程序（如果在帐户历程中使用短信渠道）： [!DNL Sinch]、[!DNL Twilio]或已设置[!DNL Infobip]凭据
- [ ]销售团队已登记到CRM销售分析组件（已安装[!DNL Salesforce]个AppExchange包或[!DNL Dynamics]个解决方案）
- [ ]已准备内容资产：用于培养和销售提醒电子邮件的B2B电子邮件模板、品牌主题和可视化片段
- [ ]定义的解决方案兴趣分类：将具有关联购买组的产品/服务列表
- [ ]设计的购买小组角色模板：每个解决方案兴趣所需的角色和角色（例如，经济买家、技术评估人员、冠军）

## 实施选项

本节介绍各种可用的实施方法，每种方法均针对不同的组织需求和成熟度级别而量身定制。

### 选项A：线性客户历程的单一解决方案兴趣

**最适合：**&#x200B;刚开始购买群组管理的组织，他们希望从单个产品线或解决方案产品开始，验证方法并在扩展至多个解决方案兴趣之前进行迭代。

**工作方式：**

此方法侧重于单个购买群组模板对单个解决方案感兴趣（一个产品或服务）。 线性客户历程的设计包含顺序阶段：客户识别、购买群组形成、培养参与、参与度评分阈值和销售切换。 历程遵循简单路径，没有复杂的分支或并行轨道。

潜在客户有资格购买群组角色，因为他们是从CRM或[!DNL Marketo Engage]引入的。 客户历程向未充分参与的角色发送培养电子邮件，监控参与度分数，并在购买组达到定义的完整性和参与阈值时触发销售警报。 在引入复杂性之前，此方法提供了清晰、可衡量的概念验证。

**关键注意事项：**

- 实施和验证更加简单，适用于首次部署
- 限制一次只能购买一项产品/服务
- 线性历程结构可能无法适应复杂的多阶段购买周期

**优点：**

- 以最低的配置复杂性实现价值的最快时间
- 与单个解决方案兴趣关联的明确成功量度
- 更容易解释并获得组织的认可
- 简单明了的报告和KPI衡量

**限制：**

- 不涉及交叉销售或多产品方案
- 对多种解决方案感兴趣的客户需要单独的、不协调的历程
- 可能无法充分利用购买群组管理功能

**Experience League：**

- [AJO B2B edition概述](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [创建购买组](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)

### 选项B：具有分支帐户历程的多个解决方案兴趣

**最适合：**&#x200B;拥有多个产品系列或服务产品，并且需要根据解决方案兴趣管理不同的购买群组的组织，以及根据活跃的解决方案兴趣以及每个购买群在资格鉴定过程中的时间长短，划分相应客户历程的组织。

**工作方式：**

定义了多个解决方案兴趣，每个兴趣都有自己的购买群组角色模板。 客户历程从客户识别开始，并根据行为信号、第一方数据或明确意图，评估哪些解决方案利益适用于每个客户。 该历程将针对每个活跃的解决方案兴趣进行分支，为同一帐户中的不同购买群体运行并行培养跟踪。

参与度得分是每个购买组独立运行的，允许一个购买组达到销售准备状态，而另一个购买组仍在培育。 销售警报是根据解决方案兴趣配置的，因此当特定购买组符合条件时，相应的销售团队或专家将收到通知。 CRM分析显示帐户的所有活跃购买组，为销售提供整体视图。

**关键注意事项：**

- 需要明确定义的解决方案兴趣分类和不同的购买组模板
- 历程复杂性会随着对解决方案的兴趣而增加
- 必须计划跨购买组协调（例如，在多个购买组中担任角色的共享联系人）

**优点：**

- 支持交叉销售和多产品客户策略
- 每个购买组的独立评分提供了精细的管道可见性
- 销售团队会收到针对每个解决方案兴趣的警报
- 最大程度地提高[!DNL AJO B2B Edition]购买团体管理功能

**限制：**

- 更高的实施复杂性和更长的部署时间
- 需要更多内容资产（根据解决方案兴趣单独跟踪电子邮件）
- 由于每个帐户拥有多个购买组，因此报告过程会更加复杂
- 处于多个购买群组中的过度发送消息联系人的风险（需要频率管理）

**Experience League：**

- [解决方案兴趣](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [帐户历程](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)

### 选项C：AI辅助的具有自动旅程进展的帐户资格

**最适合于：**&#x200B;具有大量历史数据的成熟B2B组织，这些组织希望利用AI支持的帐户资格代理来自动评估帐户准备情况、减少手动资格审核工作量，并根据AI生成的准备分数动态调整历程路径。

**工作方式：**

此方法以选项B的多解决方案兴趣基础为基础，但添加了AI支持的帐户鉴别，以自动执行历程阶段之间的过渡。 AI资格鉴定代理使用更广泛的信号集（购买群组完整性、参与速度、首次匹配、历史转化模式和意图数据）评估帐户就绪性，而不是仅依赖基于规则的参与得分阈值。

客户历程使用AI资格鉴定输出确定后续步骤：准备程度高的客户会被快速跟踪到销售警报，处于中间层的客户会获得强化培养，而准备程度低的客户会被置于长期认知跟踪中。 当新的参与数据到达时，AI代理会不断重新评估，实现动态历程进展，而无需手动干预。

**关键注意事项：**

- 需要足够的历史数据来训练有效的资格鉴定模型
- 在完全部署之前，应该根据实际管道结果来验证人工智能输出
- 与[!DNL CJA B2B Edition]很好地结合以分析资格准确性和管道关联

**优点：**

- 减少手动鉴定工作并消除基于阈值的任意切换
- 动态适应不断变化的帐户行为和参与模式
- 通过合并多个信号来提高管道质量，而不是简单的参与分数
- 持续重新评估可防止帐户卡在不正确的历程阶段中

**限制：**

- 需要历史转化数据才能进行有意义的人工智能训练
- “黑匣子”资格鉴定决策可能让销售团队在开始时更难理解和信任
- 当帐户意外合格或完全不合格时，疑难解答会更加复杂
- 取决于所有输入信号的数据质量和完整性

**Experience League：**

- [帐户资格](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [AJO B2B中的AI助手](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)

### 选项比较

| 标准 | 选项A：单一解决方案兴趣 | 选项B：多个解决方案兴趣 | 备选案文C：人工智能协助的资格 |
| --- | --- | --- | --- |
| 最适合 | 第一个部署，单个产品线 | 多产品组织 | 具有历史数据的成熟组织 |
| 复杂性 | 低 | Medium — 高 | 高 |
| 价值实现时间 | 2-4周 | 4-8周 | 6-12周 |
| 解决方案兴趣 | 1 | 多个 | 多个 |
| 历程结构 | 线性 | 分支，平行轨道 | 动态、AI驱动的进展 |
| 评分方法 | 基于规则的阈值 | 基于规则的每个购买组 | AI支持的资格+规则 |
| 内容要求 | 最小（一条培养轨迹） | 高（按解决方案利息） | 高+动态内容选择 |
| 销售协调 | 单个警报工作流 | 按解决方案兴趣警报 | 排定优先级的AI评分警报 |
| 需要 | 基本B2B数据基础 | 明确定义的解决方案分类 | 历史转化数据+分类 |

### 选择正确的选项

从这些问题开始，确定最佳实施方法：

1. **有多少不同的产品或服务具有独立的购买委员会？** 如果答案是一（或者组织希望首先证明这一概念），请从选项A开始。如果为多个，则转到问题2。

2. **是否有足够的关于成功/失败交易、购买委员会构成和参与模式的历史数据？** 如果是，并且公司希望最大程度地减少人工鉴别，则选项C提供了最自动化的方法。 如果没有，选项B通过基于规则的评分提供多解决方案兴趣支持。

3. **组织的更改管理容量是多少？** 选项B和C需要更协调的组织结构（内容制作、销售支持、跨职能协调）。 如果容量有限，请从选项A开始并展开。

一个常见的进展路径是：从选项A开始，通过一种解决方案兴趣来证明概念，随着可信度的增长通过添加解决方案兴趣扩展到选项B，然后在有足够的历史数据可用于有效训练模型时叠加选项C的AI资格。

## 实施阶段

以下阶段描述了此用例模式的分步实施流程。

### 阶段0：B2B数据基础

**应用程序功能：** [!DNL RT-CDP B2B]：帐户配置文件统一、B2B身份解析、[!DNL Marketo Engage]集成、B2B数据管理、帐户受众评估

此阶段在[!DNL RT-CDP B2B Edition]中建立B2B数据基础结构。 您要将来自CRM、营销自动化和其他来源的帐户数据统一到单个帐户配置文件中，解决人员与帐户的关系，配置B2B数据管理，并创建帐户级别的受众以引入[!DNL AJO B2B Edition]购买群组管理。

#### 决策：B2B数据源策略

哪些系统是帐户、人员和参与数据的主要来源？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| [!DNL Marketo Engage]作为主源 | [!DNL Marketo]是组织的营销自动化平台，具有丰富的参与历史记录 | 本机双向连接器简化了设置；参与数据自动流动；从[!DNL Marketo]继承了人员与帐户的关系 |
| CRM ([!DNL Salesforce]/[!DNL Dynamics])作为主源 | CRM是帐户和联系人的记录系统；未使用[!DNL Marketo] | 需要CRM源连接器配置；参与数据可能需要补充源；CRM帐户与联系人关联中的人员与帐户关系 |
| 混合：帐户的CRM + [!DNL Marketo]的参与度 | CRM拥有帐户/联系人主数据，而[!DNL Marketo]捕获行为参与 | 使用两者的组织最常见的模式；需要仔细的标识解析以将[!DNL Marketo]个人链接到CRM联系人 |

#### 决策：客户受众策略

应该如何为历程条目定义帐户受众？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 基于第一图的帐户受众 | 基于行业、公司规模、收入层或地理位置的目标客户 | 有利于ABM目标列表；不需要参与数据；范围广泛 |
| 基于参与度的帐户受众 | 定位用户已显示行为意图信号的帐户 | 需要参与数据流动；更精确的定位；可能遗漏具有潜在兴趣的帐户 |
| 组合式第一代+参与 | 定位符合理想客户配置文件并显示参与情况的客户 | 最精确；需要这两种数据类型；建议用于生成合格的管道 |

**UI导航：**&#x200B;平台>源>目录>选择源（[!DNL Marketo Engage]、[!DNL Salesforce]等） >设置数据流

**密钥配置详细信息：**

- 为每个B2B实体(Account、Person、Opportunity、Campaign、Campaign Member)配置具有必填字段组的B2B XDM架构
- 使用适当的计划（B2B数据通常为1-4小时间隔）为CRM和/或[!DNL Marketo Engage]设置源连接器
- 为B2B标识符配置身份命名空间（[!DNL Marketo]个人ID、SFDC潜在客户ID、SFDC联系人ID、帐户ID）
- 启用B2B身份解析以将人员链接到帐户
- 使用[!DNL RT-CDP]中的帐户受众功能创建帐户级别受众

**Experience League文档：**

- [RT-CDP B2B edition概述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [Real-Time CDP中的B2B架构](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Marketo Engage源连接器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [B2B身份解析](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)

### 第1阶段：解决方案兴趣和购买团体设置

**应用程序功能：** [!DNL AJO B2B]：解决方案兴趣配置，购买群组管理

此阶段定义解决方案兴趣（产品/服务）和购买群组模板，这些模板构成了购买群组管理模型的核心。 您将创建解决方案兴趣，根据角色要求定义角色模板，并配置如何授予潜在客户购买小组角色的资格。

#### 决策：解决方案兴趣粒度

应在什么级别定义解决方案兴趣？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 产品级解决方案兴趣 | 每种不同的产品都有自己的购买群体 | 最细粒度；启用特定于产品的购买群组模板；可能会导致每个帐户拥有多个购买群组 |
| 解决方案类别级别的兴趣 | 将相关产品分组为解决方案类别（例如，“Marketing Cloud”而不是单个产品） | 更易于管理；购买组更少；角色可能更通用；建议用于初始部署 |
| 用例级别的兴趣 | 定义围绕业务成果而非产品的兴趣（例如，“数字转型”） | 与咨询式销售保持一致；购买团体角色可能跨越多个产品；更难以映射到CRM管道阶段 |

#### 决策：购买群组角色模板设计

如何在每个购买组内定义角色？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 标准角色模板 | 使用跨越所有解决方案利益（例如，经济买家、技术评估人员、冠军、最终用户）的通用角色集 | 一致的评分和鉴定；更易于管理；可能无法捕获特定于解决方案的角色 |
| 特定于解决方案的角色模板 | 根据产品的实际购买委员会，按解决方案兴趣定义独特角色 | 更准确的资格鉴定；需要更深入地了解每个购买过程；更高的维护级别 |
| 分层角色模板 | 定义所需的角色（资格所必需的）和可选角色（增强完整性，但不是必需的） | 在精确度和灵活性之间取得平衡；防止过于严格的资格标准阻塞管道 |

**UI导航：** [!DNL AJO B2B Edition] >购买群组>解决方案兴趣>创建解决方案兴趣

**UI导航：** [!DNL AJO B2B Edition] >购买组>角色模板>创建角色模板

**密钥配置详细信息：**

- 用名称、描述及其解决的业务成果定义每个解决方案的兴趣
- 创建角色模板，指定每个购买组所需的角色（例如，“决策者”、“影响者”、“从业人员”、“执行发起人”）
- 配置潜在客户到角色的资格条件：系统如何确定潜在客户映射到哪个角色（根据职务、部门、资历或自定义属性）
- 设置完整性阈值：定义必须填充哪些百分比的角色才能将购买组视为“完整”
- 将解决方案兴趣与指示潜在兴趣的帐户受众或帐户属性关联

**选项差异的位置：**

选项A的&#x200B;**（单一解决方案兴趣）：**
创建一个感兴趣的解决方案和一个角色模板。 专注于清晰、熟知的组织主要产品或服务的购买动议。

选项B的&#x200B;**（多个解决方案兴趣）：**
创建多个解决方案兴趣，每个兴趣都有自己的角色模板。 将每个解决方案的兴趣映射到相应的CRM产品/机会类型，以便进行下游管道跟踪。

选项C （AI辅助的资格）的&#x200B;**：**
配置解决方案兴趣和角色模板（如选项B中所述），但另外使用有关成功购买组组合和交易结果的历史数据配置AI资格鉴定代理，以培训资格鉴定模型。

**Experience League文档：**

- [购买群组概述](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [解决方案兴趣](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [角色模板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [创建购买组](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)

### 阶段2：潜在客户资格和参与度评分

**应用程序功能：** [!DNL AJO B2B]：参与度评分，帐户资格

此阶段将建立参与度评分模型，该模型可衡量购买组内人员级别的参与度，并将其累计到购买组和帐户级别的准备程度分数。 您将配置评分规则，定义资格鉴定参与阈值，并可以选择启用AI支持的帐户资格鉴定。

#### 决策：参与度评分模型

应在人员和购买团体级别对参与度进行什么评分？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 基于活动的评分 | 将点值分配给特定操作（电子邮件打开= 5点，内容下载= 15点，演示请求= 50点） | 透明且易于调整；随着内容和渠道的更改，需要持续维护；最为[!DNL Marketo]用户所熟悉 |
| 回访间隔加权评分 | 最近活动的权重高于旧活动（衰退得分模型） | 更好地反映当前意图；防止陈旧的高分数夸大鉴别；配置更加复杂 |
| AI支持的评分 | 使用[!DNL AJO B2B] AI资格代理基于模式识别生成就绪性分数 | 最先进；自动适应；需要历史数据；最初对销售团队可能不透明 |

#### 决定：资格阈值方法

何时应认为某个购买组已做好销售移交的准备？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅限得分阈值 | 当总参与度分数超过定义的值时，购买团体符合条件 | 实施简单；分数阈值可能需要随着时间的推移而调整；不考虑角色组成 |
| 完整性+得分阈值 | 当满足最低角色覆盖率和得分阈值时，购买团体符合条件 | 更强大的资格鉴定；防止移交高分但缺少关键角色的购买组 |
| AI决定的就绪性 | AI资格代理使用超过分数和完整性的多个信号确定就绪性 | 最复杂；说明购买速度、竞争信号和历史模式；仅选项C |

**UI导航：** [!DNL AJO B2B Edition] >购买群组>参与度评分>配置评分规则

**密钥配置详细信息：**

- 定义参与度评分规则：为行为事件（电子邮件打开、点击、网页访问、内容下载、表单提交、网络研讨会出席情况、演示请求）分配点值
- 如果使用对时间敏感的评分，则配置得分衰减或回访间隔权重
- 设置购买群组级别得分汇总：人员得分如何合并到购买群组得分中（总和、加权平均值或每个角色的最小阈值）
- 定义资格阈值：触发过渡到下一个购买阶段的分数和完整性级别
- 配置AI资格鉴定代理（选项C）：使用历史交易数据进行训练，定义代理应考虑的信号并设置置信度阈值

**Experience League文档：**

- [参与度评分](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [购买群组阶段](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [帐户资格](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)

### 阶段3：帐户历程设计和执行

**应用程序功能：** [!DNL AJO B2B]：帐户Journey Orchestration、B2B电子邮件创作、短信渠道管理

此阶段将设计和部署用于协调与购买小组成员互动的帐户历程。 您将创建包含进入条件、操作节点（电子邮件、短信）、条件分支（基于购买组阶段、参与度分数、角色覆盖率）、等待步骤和退出标准的帐户历程。

#### 决策：历程条目触发器

什么事件或条件导致帐户进入历程？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 帐户受众资格 | 在加入目标帐户受众时输入的帐户 | 面向批次；适合基于ABM列表的条目；受众必须预先定义 |
| 购买组创建事件 | 首次为帐户创建购买组时输入的帐户 | 事件导向；由潜在客户资格触发购买小组角色；更实时 |
| 帐户属性更改 | 在特定属性发生更改时输入的帐户（例如，意图分数、帐户层） | 需要实时或近乎实时地更新触发属性 |

#### 决策：B2B培养的渠道组合

客户历程应使用哪些渠道吸引购买小组成员？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅电子邮件 | 大多数B2B交互都是通过电子邮件进行的；不存在短信选择加入基础结构 | 配置最简单；最常见的B2B模式；可能错过移动优先联系人 |
| 电子邮件+短信 | 组织有来自业务联系人的短信选择加入；需要紧急通知 | 短信对时间敏感型警报（事件提醒、会议确认）有效；需要短信提供商配置 |
| 电子邮件+短信+销售警报 | 全方位：通过电子邮件/短信以及销售团队通知进行营销培养 | 最全面；要求销售团队采用警报工作流；协调营销和销售接触点 |

#### 决策：历程分支策略

历程应如何根据帐户和购买群组状态进行分支？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 基于阶段的分支 | 基于购买分组阶段的分支（例如，意识、考虑、决策） | 与传统funnel阶段保持一致；内容映射到阶段；清晰的进展路径 |
| 基于角色的分支 | 将不同的内容发送给不同的购买小组角色（技术内容发送给评估人员，ROI内容发送给经济购买者） | 更加个性化；需要特定于角色的内容资产；提升内容制作工作 |
| 基于参与的分支 | 基于参与度分数阈值的分支（低参与度=重新参与度，高=加速） | 动态和响应；适应实际行为；可以创建复杂的分支树 |

**UI导航：** [!DNL AJO B2B Edition] >帐户历程>创建历程

**密钥配置详细信息：**

- 使用选定的进入条件创建帐户历程画布
- 添加帐户历程节点：电子邮件操作、短信操作、等待步骤、条件拆分和路径分支
- 使用带有品牌主题、可视化片段和AI辅助内容生成的B2B Email Designer创作B2B电子邮件内容
- 配置引用帐户属性、人员属性和购买群组数据的个性化令牌
- 设置接触点之间的等待持续时间（B2B历程通常使用更长的等待：电子邮件之间的等待时间为3至7天）
- 定义退出标准：帐户离开历程的条件（购买组达到资格阈值、在CRM中创建机会、帐户选择退出）
- 如果使用短信渠道，配置短信操作（需要短信提供商配置并联系选择加入功能）
- 在发布之前使用测试帐户测试历程

**选项差异的位置：**

选项A的&#x200B;**（单一解决方案兴趣）：**
设计具有连续阶段的线性历程。 登录基于单个帐户受众或购买群组创建事件。 一个电子邮件随着内容的紧迫性和深度不断增长而不断培养。

选项B的&#x200B;**（多个解决方案兴趣）：**
根据解决方案的兴趣设计一个包含并行分支的历程。 使用条件节点将帐户路由到基于购买组存在的相应培养轨迹。 每个分支都有自己的内容和评分阈值。

选项C （AI辅助的资格）的&#x200B;**：**
设计历程，其中条件节点评估AI资格分数而不是（或除了）基于规则的阈值。 包括动态路径选择，其中AI确定是否加速、维护帐户或取消帐户的优先级。

**Experience League文档：**

- [帐户历程概述](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [帐户历程节点](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [B2B电子邮件创作](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [AJO B2B中的短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [用于电子邮件创作的AI助手](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### 第4阶段：销售协调和CRM集成

**应用程序功能：** [!DNL AJO B2B]：销售警报配置，CRM销售分析；[!DNL RT-CDP B2B]：帐户目标配置，帐户Audience Activation

此阶段通过配置销售警报电子邮件、部署CRM销售分析以实现in-CRM可见性，以及选择性地将帐户受众激活到B2B目标（[!DNL LinkedIn]、[!DNL Marketo]、CRM系统）来在营销和销售之间架起桥梁。

#### 决策：销售警报触发策略

何时应通知销售人员帐户购买群的状态？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 基于里程碑的警报 | 当购买团体达到特定里程碑（符合条件、完整、高度参与）时通知销售 | 清晰、离散的通知；防止警报疲劳；可能错过逐渐参与的趋势 |
| 基于阈值的警报 | 当参与度分数超过定义的阈值时通知销售人员 | 连续监控；可能随着分数在阈值附近波动而触发多个警报 |
| 暂存过渡警报 | 在购买组过渡到新阶段（例如，从考虑阶段过渡到决策阶段）时通知销售人员 | 与管道阶段保持一致；销售操作的最明确信号；需要定义良好的阶段定义 |

#### 决策： CRM集成深度

在CRM中应该在多大程度上显示购买组数据？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅限销售警报（无CRM内组件） | 组织未使用[!DNL Salesforce]或[!DNL Dynamics]，或者CRM集成不可行 | 集成工作量最低；销售人员会收到电子邮件通知，但没有CRM仪表板；可见性有限 |
| CRM销售分析仪表板 | 组织使用[!DNL Salesforce]或[!DNL Dynamics]，希望购买团体状态在CRM中可见 | 需要安装CRM销售分析包；提供丰富的帐户级别智能；建议用于大多数实施 |
| 完全双向CRM同步 | 购买组阶段和分数会写回CRM对象，从而影响CRM工作流程和报表 | 最高的集成复杂性；支持CRM本机管道报告；需要自定义CRM配置 |

**UI导航：** [!DNL AJO B2B Edition] >管理>销售警报配置

**UI导航：** [!DNL AJO B2B Edition] >管理> CRM销售分析>配置

**密钥配置详细信息：**

- 配置销售警报电子邮件模板：包括购买组状态、参与角色、参与得分以及建议的后续行动
- 定义警报路由规则：哪些销售代表或团队会根据客户所有权、区域或解决方案兴趣接收警报
- 为[!DNL Salesforce]或[!DNL Dynamics 365]安装和配置CRM销售分析
- 将购买群组数据映射到CRM对象，以便销售人员可以在其CRM工作流中查看购买群组构成、参与和历程进度
- （可选）配置帐户目标连接以将帐户受众激活到[!DNL LinkedIn]（对于ABM广告）、[!DNL Marketo Engage]（对于潜在客户级别的跟进）或其他B2B目标

**Experience League文档：**

- [销售警报电子邮件](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [CRM销售分析](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)
- [目的地概述](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [LinkedIn匹配受众目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)

### 阶段5：报告和优化

**应用程序功能：** [!DNL AJO B2B]： B2B Analytics仪表板

此阶段建立了报告和分析框架，用于衡量购买组表现、客户历程有效性和管道影响。[!DNL AJO B2B Edition] 提供内置analytics功能板；[!DNL CJA B2B Edition]（如果许可）通过更深入的跨渠道帐户级别见解扩展了分析。

#### 决定：报告方法

应配置哪些分析工具进行持续性能监控？

| 选项 | 何时选择 | 注意事项 |
| --- | --- | --- |
| 仅[!DNL AJO B2B]个仪表板 | [!DNL AJO B2B Edition]的内置仪表板足以购买组和历程量度 | 配置最快；涵盖核心B2B量度；自定义分析功能有限 |
| [!DNL AJO B2B]个功能板+ [!DNL CJA B2B Edition] | 组织需要更深入的跨渠道分析、购买组分析、机会关联和自定义归因 | 需要[!DNL CJA B2B Edition]许可证；最全面；支持帐户级别的自由格式分析 |
| [!DNL AJO B2B]个功能板+ CRM报表 | 组织更喜欢在CRM中将管道报表与购买团体量度集中在一起 | 需要CRM功能板开发；将营销和销售量度整合到一个位置；仅限于CRM报表功能 |

**UI导航：** [!DNL AJO B2B Edition] >功能板>参与概述/智能功能板

**密钥配置详细信息：**

- 访问[!DNL AJO B2B]参与仪表板，以监控购买组参与度分数、完整性率和阶段分布
- 访问智能仪表板，以获取AI驱动的帐户准备情况和管道质量见解
- 如果使用[!DNL CJA B2B Edition]：配置包含[!DNL AJO B2B]个数据集的基于帐户的CJA连接，使用购买组和帐户容器设置B2B数据视图，并构建用于购买组进度、机会关联和归因的工作区分析
- 定义报告节奏：每周购买小组绩效审查、每月管道影响分析、季度项目优化
- 为重要事件（营销活动启动、内容刷新、评分模型更改）创建注释以关联性能趋势

**Experience League文档：**

- [B2B analytics功能板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [参与仪表板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [智能仪表板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [CJA B2B edition概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

## 实施注意事项

以下部分涵盖在实施过程中要牢记的护栏、常见隐患、最佳实践和权衡取舍决定。

### 护栏和限制

- [!DNL AJO B2B Edition]帐户历程限制（包括每个历程的最大并发历程和最大帐户数）遵循[!DNL AJO B2B Edition]产品护栏 — [AJO B2B护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [!DNL RT-CDP B2B Edition]支持最多50个B2B架构类，并遵循标准配置文件和分段护栏 — [实时客户配置文件护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 帐户受众评估对批量计划运行；并非所有区段类型都支持实时帐户受众更新 — [分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- B2B源连接器摄取具有最小计划间隔（对于[!DNL Marketo]通常为15分钟，对于CRM源则有所不同） — [摄取护栏](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- 每个沙盒的电子邮件渠道表面限制为每个渠道类型10个 — [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### 常见陷阱

- **为每个购买组定义过多角色：**&#x200B;过度指定角色（例如，需要8-10个不同的角色）使购买组几乎不可能达到完整性阈值。 从3-5个基本角色开始，随着模型的成熟而扩展。
- **将参与度分数阈值设置得太高或太低：**&#x200B;如果阈值太高，则没有购买组符合条件，使管道无法运行。 如果太低，不合格的账户就会泛滥销售。 从历史数据分析（如果有）开始，并根据销售反馈进行迭代。
- **忽略人员到帐户的解析质量：**&#x200B;如果人员未正确链接到帐户，则即使与合适的人接触，购买组也会缺少成员。 在启动购买团体历程之前，请投资于身份解析质量。
- **多个购买组中的消息过度发送联系人：**&#x200B;单个联系人可能具有多个购买组中的角色（例如，CTO是CRM和Data Platform购买的技术评估员）。 如果没有频率管理，此人将从每个活动历程接收电子邮件。 实施跨历程频率规则。
- **忽略销售支持：**&#x200B;销售团队必须了解如何解释购买组数据、参与度分数和销售警报。 如果不进行培训和采用，则无论数据质量如何，营销到销售的移交都会失败。
- **将帐户历程视为个人历程：**&#x200B;帐户历程在帐户级别运行，向帐户的购买团体中的个人发送电子邮件。 历程设计必须考虑每个帐户节点执行会有多个用户接收消息，这与人员级别[!DNL AJO]历程截然不同。

### 最佳实践

- **从一个解决方案兴趣开始，然后展开** — 在扩展至多个解决方案兴趣之前，证明该模型适用于一个购买动作。 这允许团队在增加复杂性之前优化角色模板、评分模型和内容。
- **将购买群组角色与CRM销售流程保持一致** — 将购买群组角色映射到销售团队已识别的角色。 使用相同的语言（经济买家、Champion等） 所以切换是直观的。
- **与销售人员实施反馈循环** — 定期收集关于符合营销条件的客户质量的销售反馈。 使用此反馈可调整参与度评分阈值和角色资格标准。
- **为角色设计内容，而不仅仅是阶段** — 不同的购买团体角色需要不同的内容：执行用户希望投资回报和战略影响，技术评估人员希望了解体系结构和集成详细信息，最终用户希望进行易于使用的演示。 将内容资产映射到角色，以实现更有效的培养。
- **提前设置CRM销售分析** — 不要等到完整历程上线才部署CRM可见性。 销售团队需要提前查看购买组数据，以便就角色准确性和客户定位提供反馈。
- **策略性地使用等待步骤** — B2B购买周期较长。 帐户历程等待步骤应该反映这一现实（每次接触间隔5至14天），而不是消费者式的紧急情况（1至3天）。
- **监控参与速度，而不仅仅是参与度得分** — 两周内从20分提高到80分的购买团体发出的信号比六个月内达到80分的购买团体发出的信号更强烈。 配置评分和资格以考虑周转率。

### 权衡决定

应根据贵组织的特定需求评估以下权衡。

#### 购买组完整性与管道数量

在授予购买群体资格之前要求填补所有职位可最大限度地提高渠道质量，但可能会严重限制合格账户的数量，尤其是对于组织数据库覆盖范围有限的新产品或市场。

- **完整性阈值越高，有利于：**&#x200B;管道质量；销售获得完全格式化的购买组；每个帐户的成功率越高
- **较低的完整性阈值有利于：** Pipeline volume；更多的客户可达到销售额；覆盖范围更广；数量较多但质量可能较低
- **推荐：**&#x200B;从中等阈值（60-70%角色覆盖率）开始，并根据实际获胜率数据进行调整。 对于数据覆盖良好的成熟市场，增长率应接近80%以上。 对于新市场，一开始接受50%至60%，然后借助购买团体完整度促销活动来填补空白。

#### 评分粒度与操作简单性

高度精细的评分模型（包括数十种活动类型、回访间隔加权和特定于角色的评分）可提供更准确的资格信号，但更难以维护、解释和排除故障。

- **更高的粒度更适合：**&#x200B;资格鉴定的准确性；帐户之间的细微差别；更好地与复杂的购买过程保持一致
- **更小的粒度更适合：**&#x200B;操作简单性；更易于维护和向销售人员解释；实施速度更快；边缘案例更少
- **推荐：**&#x200B;从简单的评分模型（10-15个活动类型、统一点值）开始，仅在简单模型无法区分帐户质量时增加复杂性。 彻底记录评分模型以便进行销售协调。

#### 单个历程与多个专用历程

一个单一、全面的客户历程，在一个画布中处理所有阶段和解决方案兴趣，提供了统一的控制能力，但可能会变得笨拙。 多个专用历程（每个阶段一个历程或解决方案关注一个）单个更简单，但更难以协调。

- **单一历程优势：**&#x200B;整体视图；更易于确保一致的时间和消息传送；更易于监视；一个位置用于所有逻辑
- **多个历程更适合：**&#x200B;模块性；更容易更新一个阶段而不影响其他阶段；不同团队可以拥有不同的历程；更干净的画布设计
- **推荐：**&#x200B;对于选项A，适合使用单个历程。 对于选项B和C，请使用主“编排”历程，该历程根据解决方案兴趣或购买阶段将帐户路由到专业化的子历程。

## 相关文档

以下资源提供了有关本指南中引用的应用程序和功能的更多详细信息。

### [!DNL AJO B2B Edition]

- [AJO B2B edition文档主页](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [购买群组概述](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [解决方案兴趣](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [角色模板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [创建购买组](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)
- [购买群组阶段](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [帐户历程概述](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [帐户历程节点](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [销售警报电子邮件](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [CRM销售分析](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)

### B2B电子邮件和内容

- [B2B电子邮件创作](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [AJO B2B中的短信创作](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [用于电子邮件创作的AI助手](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### B2B分析和功能板

- [购买组仪表板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [参与仪表板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [智能仪表板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [CJA B2B edition概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### [!DNL RT-CDP B2B Edition]

- [RT-CDP B2B edition概述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [Real-Time CDP中的B2B架构](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [帐户受众](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Marketo Engage源连接器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)

### 数据基础

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [源概述](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### 渠道配置

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### 数据治理和隐私

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [高级数据生命周期管理](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### 目标

- [目的地概述](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [目标目录](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [LinkedIn匹配受众目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)

### 护栏

- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [摄取护栏](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### 教程和快速入门

- [AJO B2B edition快速入门](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [RT-CDP B2B edition教程](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-tutorial)
