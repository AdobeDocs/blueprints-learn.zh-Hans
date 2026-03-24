---
title: 事件转发
description: 了解如何将通过Edge Network收集的实时事件数据转发到非Adobe目标以用于分析、存储或广告。
solution: Experience Platform
exl-id: 24964d27-db56-4fa4-a79f-1b6750564b34
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '6342'
ht-degree: 0%

---

# 事件转发

本指南介绍如何使用[!DNL Adobe Experience Platform] Edge Network实施服务器端事件转发。 它专为需要通过Edge Network将收集的实时事件数据分发到非Adobe目标（如第三方分析平台、云存储端点、广告网络或自定义Webhook）的解决方案架构师、营销技术人员和实施工程师而设计。

它提供了配置事件转发的所有可行方法，说明了它们之间的利弊，并提供了指向[!DNL Adobe Experience League]文档的链接以获取详细的过程指导。

## 用例概述

通过[!DNL Adobe Experience Platform] Web SDK、Mobile SDK或Server API收集行为数据的组织通常需要与非Adobe系统（如[!DNL Google Analytics]或[!DNL Snowflake]等分析平台、用于转化跟踪的广告网络、用于长期存储的数据仓库或自定义内部服务）共享该事件流。 传统上，这要求客户端标记激增，这会增加页面权重、引入延迟，并产生隐私和治理风险。

事件转发通过在Edge Network上操作服务器端解决了此问题。 当访客交互通过Web SDK或服务器API触发事件时，该事件通过数据流路由到Edge Network。 事件转发规则（在专用事件转发属性中配置）会评估传入事件数据并选择性地将其转发到一个或多个已配置的目标。 这种服务器端方法可减少客户端标记膨胀，提高页面性能，集中数据管理，并使组织能够准确地控制哪些数据离开Adobe生态系统。

此模式的目标受众包括已部署（或计划部署）用于数据收集的[!DNL Adobe Experience Platform] Web SDK或服务器API的组织，这些组织希望通过将事件数据分发到非Adobe端点来扩展该投资，而无需添加客户端JavaScript标记。

## 主要业务目标

此用例模式支持以下业务目标。

### 提高数据质量和改善管理

确保数据干净、完整且合规，以实现准确定位、减少浪费和可靠的分析。 事件转发可在服务器端集中数据分发，为组织提供单一控制点来管理与外部系统共享的数据，降低数据泄露的风险，并确保在数据离开[!DNL Adobe] Edge Network之前应用治理策略。

**KPI：**&#x200B;效率，成本节约

有关详细信息，请参阅[改进数据质量和管理](../../business-objectives/cost-efficiency/improve-data-quality-governance.md)。

### 整合营销技术并使其现代化

通过迁移到统一、可扩展的平台，减少工具碎片化和技术债务。 事件转发使组织能够使用一个服务器端数据分发机制替换多个客户端供应商标记，从而减少页面加载开销并简化技术栈栈。

**KPI：**&#x200B;成本节约、效率、上市速度

有关详细信息，请参阅[整合营销技术并使其现代化](../../business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md)。

## 战术用例示例

以下是适用于此用例模式的常见战术情景。

- **第三方分析扩充** — 实时将页面查看、点击和转化事件转发到[!DNL Google Analytics]、[!DNL Snowflake]或其他Analytics平台，而无需添加客户端标记
- **Advertising转化跟踪** — 将购买和商机生成事件发送到[!DNL Meta]转化API、[!DNL Google Ads]、[!DNL TikTok]或[!DNL Snap]，以进行服务器端转化衡量和优化
- **数据仓库流** — 将原始事件数据路由到云数据仓库([!DNL Google BigQuery]、[!DNL Amazon S3]、[!DNL Azure Event Hubs])，以进行长期存储和离线分析
- **自定义webhook集成** — 通过HTTP端点将过滤或转换的事件数据转发到内部微服务、CRM系统或合作伙伴平台
- **标记减少和页面性能改进** — 将多个客户端供应商JavaScript标记替换为单个Web SDK实施以及服务器端事件转发规则，从而减轻页面重量并改进Core Web Vitals
- **与隐私兼容的数据共享** — 在与第三方共享事件数据之前，在服务器端应用数据过滤和字段级密文规则，确保PII在到达外部系统之前被剥离或散列
- **多云事件分发** — 同时从单个服务器端规则集将同一事件流转发到多个目标（例如，分析、广告和数据仓库）
- **实时欺诈信号转发** — 将高价值交易事件转发到欺诈检测系统，以便实时进行风险评分和发出警报

## 关键绩效指标

以下KPI可帮助衡量此用例模式是否成功。

- **页面加载时间减少** — 测量到了将客户端标记迁移到服务器端事件转发后页面加载速度和Core Web Vitals的改进
- **数据传递成功率** — 成功转发到目标端点的事件百分比，无错误或超时
- **标记计数减少** — 实施服务器端等效项后删除的客户端供应商标记数
- **数据新鲜度/延迟** — 客户端上发生事件与事件到达目标端点之间的时间（目标：从秒到秒）
- **治理合规性比率** — 通过服务器端筛选规则以确保没有PII或受限制的数据到达未经授权目标的出站数据共享百分比
- **运营效率** — 减少开发人员管理客户端标记部署和解决标记冲突所花费的时间

## 用例模式

本节介绍用于实施事件转发的模式和函数链。

**事件转发** — 将通过Edge Network收集的实时事件数据转发到非Adobe目标以用于分析、存储或广告。

**函数链：**&#x200B;数据流配置>事件规则定义>目标映射>转发执行>监视

## 应用程序

在此用例模式中使用以下应用程序。

- **[!DNL Adobe Experience Platform] (Edge Network)** — 通过配置的数据流从Web SDK、Mobile SDK或Server API接收实时事件数据并进行路由
- **[!DNL Adobe Experience Platform]（事件转发）** — 提供服务器端规则引擎，用于评估、筛选、转换事件数据并将其转发到外部目标
- **[!DNL Adobe Experience Platform]（标记/数据收集）** — 管理事件转发属性生命周期、扩展、规则和发布工作流

## 基本函数

必须具备以下基本功能才能使用此用例模式。 对于每个函数，状态都指示它通常是必需的、假定为预配置还是不适用。

| 基本函数 | 状态 | 必须准备好的内容 | Experience League参考 |
| --- | --- | --- | --- |
| 管理和治理 | 必填 | 沙盒必须处于活动状态并配置了相应的用户角色和权限。 管理事件转发的用户需要[!DNL Adobe Admin Console]中的数据收集权限，包括管理事件转发属性、扩展和规则的权限。 | [访问控制概述](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 数据建模和准备 | 必填 | 必须为流经Edge Network的事件数据定义XDM架构。 数据流必须引用有效的XDM ExperienceEvent架构，以便事件转发规则可以访问用于筛选、转换和映射的结构化字段。 | [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| 数据源和收集 | 必填 | 数据收集机制必须处于活动状态 — Web SDK、Mobile SDK或Edge Network Server API — 才能通过配置的数据流发送事件。 数据流是连接客户端集合与服务器端事件转发的基本路由层。 | [配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| 身份和配置文件配置 | 不适用 | 事件转发在身份解析或配置文件统一发生之前对Edge Network层的原始事件数据运行。 不需要身份命名空间和合并策略，除非转发的事件也需要贡献到Real-Time Customer Profile（这是一个单独的数据流服务配置，而不是事件转发问题）。 | |
| 受众定义和分段 | 不适用 | 事件转发会实时处理单个事件，而不评估受众成员资格。 基于受众的筛选不是事件转发功能链的一部分。 如果需要基于受众的激活，请参阅Audience Activation目标参考计划。 | |

## 支持功能

以下功能增强此用例模式，但核心执行不需要这些功能。

| 支持功能 | 状态 | 为什么它很重要 | Experience League参考 |
| --- | --- | --- | --- |
| 计算/派生属性创建 | 不适用 | 事件转发对原始事件数据而非配置文件级别的计算属性运行。 计算属性在事件转发上下文中不可用。 | |
| 数据生命周期管理 | 推荐 | 如果事件数据也正在被摄取到AEP数据集（通过同一数据流），则应为这些数据集配置数据保留策略（过期），以管理存储成本和法规遵从性。 事件转发本身并不存储数据，但并行AEP摄取路径存储数据。 | [高级数据生命周期管理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 数据使用标签和执行 | 推荐 | 虽然事件转发规则提供了字段级筛选（允许您从转发的有效负载中排除敏感数据），但若将相同的数据用于受众激活或个性化，则将数据使用标签应用于基础架构和数据集可确保实施治理策略。 | [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| 监视和可观察性 | 已包含 | 监控对于事件转发至关重要。 事件转发监视仪表板提供转发成功率、错误率和目标响应代码的可见性。 应针对目标故障配置警报。 | [事件转发监视](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring) |
| 报告和分析 | 推荐 | 如果转发的事件馈送第三方分析平台，请考虑将相同的AEP事件数据集连接到CJA以实现统一的跨渠道视图。 这样即可在Adobe端和第三方分析之间进行比较。 | [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## 应用程序功能

此计划从“应用程序功能目录”中练习以下功能。 函数会映射到实施阶段而不是编号步骤。

### [!DNL Adobe Experience Platform] (AEP)

| 函数 | 实施阶段 | 描述 |
| --- | --- | --- |
| 数据流配置 | 阶段1：数据流配置 | 配置数据流以接收Edge Network事件并启用事件转发服务 |
| 事件转发属性设置 | 阶段2：事件转发属性和扩展 | 创建事件转发属性并安装特定于目标的扩展 |
| 事件规则定义 | 阶段3：事件规则定义 | 定义评估传入事件数据并确定转发内容和转发位置的规则 |
| 目标映射 | 阶段3：事件规则定义 | 在转发规则中，将事件数据元素映射到特定于目标的负载格式 |
| 转发执行 | 第4阶段：发布和激活 | 将事件转发配置发布到Edge Network以供实时执行 |
| 监测 | 第5阶段：监控和验证 | 监测转发成功率、错误代码和目标运行状况 |

## 先决条件

确保在开始实施之前已满足以下条件。

- [ 具有Edge Network和事件转发权利的] [!DNL Adobe Experience Platform]许可证
- [ 在[!DNL Adobe Admin Console]中配置了]数据收集权限（管理属性、扩展、规则和发布以进行事件转发）
- [ ]至少有一个通过数据流发送事件的活动数据收集机制（Web SDK、Mobile SDK或服务器API）
- [ 为正在收集的事件数据定义了]个XDM ExperienceEvent架构
- [ ]数据流已创建并链接到收集机制
- [ ]目标端点凭据和文档可用（例如，[!DNL Meta]转化API访问令牌、[!DNL Google Analytics]测量ID、webhook URL、云存储凭据）
- [ ]了解事件数据模型以及每个目标所需的字段/事件

## 实施选项

此部分介绍了实施事件转发的可用方法，并提供了有关选择正确选项的指导。

### 选项A：基于扩展的事件转发

**最适合：**&#x200B;个使用受良好支持的目标平台的团队（[!DNL Meta]、[!DNL Google]、[!DNL AWS]、[!DNL Azure]、[!DNL Snowflake]等） 数据收集目录中提供了预置的事件转发扩展。

**工作方式：**

基于扩展的事件转发利用了由Adobe或第三方合作伙伴维护的预建集成。 每个扩展都是为特定目标专门构建的，可处理身份验证、有效负载格式和端点通信。 实施人员将安装事件转发属性中的扩展，配置身份验证凭据，并构建将XDM数据元素映射到扩展操作字段的规则。

此方法最大限度地减少了自定义开发，因为扩展可抽象出目标的API要求。 例如，[!DNL Meta]转化API扩展将XDM商业事件转换为[!DNL Meta]预期的格式，处理PII字段的哈希处理、重复数据删除参数和访问令牌管理。 同样，[!DNL Google Cloud Platform]或[!DNL AWS]扩展处理其各自云服务的身份验证和有效负载格式。

扩展可用性决定了支持的目标，这是一个权衡问题。 如果目标目标目标不存在扩展，则必须使用选项B（自定义Webhook）。

**关键注意事项：**

- 扩展可用性各不相同 — 在计划之前请检查[数据收集扩展目录](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- 扩展由Adobe或合作伙伴维护；更新可能会引入重大更改，这些更改需要调整规则
- 某些扩展仅支持特定的事件类型或需要特定的XDM字段映射
- 扩展在其配置UI中处理身份验证和凭据管理

**优点：**

- 实施受支持目标的最快时间
- 预建的有效负载格式可减少映射错误
- 由扩展处理的身份验证和凭据管理
- 由Adobe或认证合作伙伴维护和更新
- 减少了自定义代码并减轻了维护负担

**限制：**

- 仅限于具有可用扩展的目标
- 与自定义Webhook相比，负载自定义的灵活性较低
- 扩展更新可能需要重新配置规则
- 某些扩展可能不支持所有目标API功能

**Experience League：**

- [事件转发扩展目录](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Meta Conversions API扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/meta/overview)
- [Google Cloud Platform扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [AWS扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/aws/overview)
- [Snowflake扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/snowflake/overview)

### 选项B：自定义webhook（获取API）事件转发

**最适合：**&#x200B;需要将事件转发到没有预建扩展的目标，或需要完全控制HTTP请求有效负载、标头和身份验证机制的团队。

**工作方式：**

自定义基于webhook的事件转发使用[!DNL Adobe Cloud Connector]扩展（默认包含）向任何端点发出任意HTTP请求。 实施人员定义数据元素以提取和转换传入XDM事件的值，然后使用云连接器的“发出获取调用”操作类型配置规则操作。 此操作允许完全控制HTTP方法、URL、标头和请求正文。

请求正文通常使用数据元素和自定义代码构造，以根据目标的API规范设置有效负荷的格式。 此方法支持任何可通过HTTP访问的端点（REST API、Webhook、云函数或内部服务），使其成为最灵活的选项。

取舍是加大实施工作量和持续维护。 实施者必须了解目标API，手动处理身份验证（例如，设置授权标头，管理令牌刷新），并在目标API发展时保持有效负载格式。

**关键注意事项：**

- 需要了解目标API规范（HTTP方法、URL结构、有效负载格式、身份验证）
- 必须在数据元素或密码中手动管理身份验证凭据
- 有效负载转换（哈希处理、编码、重构）可能需要自定义代码
- 目标API发生更改时没有自动更新 — 需要手动维护
- 数据收集中的密码功能可以安全地存储API密钥和令牌

**优点：**

- 支持任何可通过HTTP访问的端点 — 无扩展依赖关系
- 完全控制请求有效负载、标头和身份验证
- 可以转发到内部服务、自定义API或小平台
- 使用自定义代码启用复杂的有效负载转换
- 可以在自定义代码中实施重试逻辑和错误处理

**限制：**

- 增加初步实施工作量
- 有效负荷格式和身份验证的持续维护责任
- 无预建错误处理或凭据轮换 — 必须手动实施
- 需要开发人员在HTTP协议和目标API细节方面的专业知识

**Experience League：**

- [Adobe云连接器扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [事件转发密钥](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)

### 选项C：混合（扩展+自定义Webhook）

**最适合：**&#x200B;组织将事件转发到多个目标，其中某些目标具有预建扩展，而其他目标需要自定义集成。

**工作方式：**

混合方法结合了对支持良好的目标进行的基于扩展的转发，以及对缺少扩展的目标进行的自定义webhook操作。 单个事件转发属性包含多个规则 — 一些规则使用扩展操作（例如，用于广告转化跟踪的[!DNL Meta]转化API扩展），另一些规则使用Cloud Connector获取操作（例如，转发到内部数据湖端点）。

此方法可最大程度地扩大覆盖范围，同时最大限度地减少不必要的自定义开发。 每个规则都独立运行，因此基于扩展的规则受益于预建的有效负载格式，而自定义规则保持完全的灵活性。

**关键注意事项：**

- 属性复杂性会随着规则和目标的数量而增加
- 对于基于扩展的规则和自定义规则，测试和调试可能需要采用不同的方法
- 发布更改会影响资产中的所有规则 — 使用库和环境安全地暂存更改
- 请考虑使用明确的命名惯例来组织规则，以区分基于扩展的操作和自定义操作

**优点：**

- 跨多种目标类型的最佳覆盖范围
- 在可用的情况下利用预建扩展，从而减少工作量
- 保持自定义目标的灵活性
- 单个事件转发属性管理所有转发逻辑

**限制：**

- 使用多种规则类型时提高属性复杂性
- 混合维护模型 — 某些规则通过扩展自动更新，而另一些规则需要手动维护
- 调试需要熟悉扩展配置和自定义获取调用模式

**Experience League：**

- [事件转发概述](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [事件转发快速入门](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)

### 选项比较

下表比较了三个实施选项。

| 标准 | 选项A：基于扩展 | 选项B：自定义Webhook | 选项C：混合 |
| --- | --- | --- | --- |
| 最适合 | 支持的目标（[!DNL Meta]、[!DNL Google]、[!DNL AWS]等） | 定制端点、小众平台、内部服务 | 支持混合的多个目标 |
| 复杂性 | 低 | Medium — 高 | 中 |
| 实施时间 | 天 | 天 — 周 | 因目标组合而异 |
| 灵活性 | 仅限扩展功能 | 完全控制 | 在需要时实现完全控制 |
| 维护 | 低（扩展管理） | 高（手动维护） | 混合 |
| 需要 | 扩展可用于目标 | 目标API文档 | 两者全部，具体取决于目标 |
| 需要自定义代码 | 最小 | 中等 — 重要 | 不同 |

### 选择正确的选项

首先，清点目标目标并检查每个目标中是否存在预建的事件转发扩展。

1. **如果所有目标都有扩展** — 选择选项A。这为您提供了最快的实施，以及最低的维护负担。 扩展处理身份验证、有效负载格式和API版本管理。

2. **如果没有目标具有扩展，或者您需要完整的负载控制** — 选择选项B。使用Cloud Connector扩展对任何端点发出自定义HTTP请求。 当您需要应用复杂的转换、自定义散列或发送到内部服务时，这也是正确的选择。

3. **如果您同时具有受支持和不受支持的目标** — 请选择选项C。将扩展用于[!DNL Meta]、[!DNL Google]和[!DNL AWS]等平台，并将自定义Webhook用于其他所有方面。 这是具有各种分析和广告栈栈的组织最常见的生产场景。

## 实施阶段

以下阶段描述了事件转发的端到端实施流程。

### 阶段1：数据流配置

**应用程序函数：** AEP：数据流配置

**要配置的内容：**&#x200B;一个数据流，用于接收来自Web SDK、Mobile SDK或Server API实施的事件，并将它们路由到Edge Network，事件转发规则可以在其中处理它们。 如果要将事件转发添加到现有数据收集部署，则将在现有数据流上启用事件转发。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决定：新数据流与现有数据流**
>
>您应该为事件转发创建新的数据流还是在现有数据流上启用事件转发？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 使用现有数据流 | 您已拥有Web SDK或服务器API，可通过数据流发送事件 | 最常见的情况；事件转发仅作为数据流上的附加服务启用。 无需客户端更改。 |
>| 创建新数据流 | 这是一项全新实施，没有现有的数据收集，或者您需要针对特定事件类型设置单独的数据流 | 需要客户端SDK配置指向新数据流ID。 允许独立配置。 |

>[!NOTE]
>
>**决定：与事件转发一起启用哪些AEP服务**
>
>数据流可以将事件同时路由到多个AEP服务。 事件转发是一个服务；其他（AEP数据摄取，[!DNL Target]，[!DNL Analytics]）可以并行运行。
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 仅事件转发 | 您只需要将事件转发到非Adobe目标，而不需要AEP数据集中的数据 | 最大程度地降低数据处理成本。 事件通过Edge Network转发规则，但未摄取到AEP数据湖中。 |
>| 事件转发+ AEP摄取 | 您需要在AEP（用于用户档案、受众、历程）中转发到外部系统的相同事件 | 对于将[!DNL RT-CDP]或[!DNL AJO]与第三方分析结合使用的组织来说，最常用。 数据流将事件同时发送到AEP数据集和事件转发规则。 |
>| 事件转发+多个Adobe服务 | 您需要同时路由到AEP、[!DNL Target]、[!DNL Analytics]和外部目标的事件 | 启用数据流上的所有必需服务。 每个服务单独接收事件。 |

**用户界面导航：** [!DNL Experience Platform] >数据收集>数据流>选择或创建数据流

**密钥配置详细信息：**

- 数据流必须在其高级设置或服务配置下启用事件转发
- 将事件转发属性（在第2阶段创建）链接到数据流
- 确认分配给数据流的XDM架构与收集机制发送的事件结构相匹配

**Experience League文档：**

- [配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [数据流概述](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview)
- [事件转发概述](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)

### 阶段2：事件转发属性和扩展

**应用程序函数：** AEP：事件转发属性安装程序

**您将配置的内容：**&#x200B;数据收集UI中的事件转发属性，以及目标目标所需的扩展。 事件转发属性是定义服务器端转发逻辑的所有规则、数据元素和扩展的容器。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决策：单个属性与多个属性**
>
>您应该为所有目标还是为单独的属性使用一个事件转发属性？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 单个属性 | 大多数实施；所有转发规则共享相同的事件流 | 更易于管理、单一的发布工作流程，所有规则都针对每个事件进行评估。 使用规则条件过滤哪些事件转到哪些目标。 |
>| 多个属性 | 您需要不同的团队来独立管理不同的目标集成，或者您具有严格的环境隔离要求 | 每个资产都有自己的发布工作流程，并且可以链接到不同的数据流。 增加了管理开销，但改善了访问控制边界。 |

>[!NOTE]
>
>**决定：要安装哪些扩展**
>
>根据您的目标目标和选择的实施选项（上述A、B或C）选择扩展。
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 目标特定的扩展（[!DNL Meta]、[!DNL Google]、[!DNL AWS]等） | 目标具有预建扩展，并且您需要最少的自定义配置（选项A或C） | 每个扩展都需要特定于目标的凭据（API令牌、测量ID、帐户ID）。 有关支持的事件类型和必填字段，请参阅扩展文档。 |
>| 仅限云连接器扩展 | 所有目标都将使用自定义HTTP请求（选项B） | 默认情况下，会安装Cloud Connector扩展。 使用“密钥”功能安全地存储API密钥和身份验证令牌。 |
>| 特定于目标的连接器和云连接器 | 您同时具有受支持和自定义的目标（选项C） | 为受良好支持的目标安装特定扩展，并在其他目标中使用云连接器。 |

**UI导航：** [!DNL Experience Platform] >数据收集>事件转发>创建属性（或选择现有）

**密钥配置详细信息：**

- 使用明确的约定命名属性（例如，“Event Forwarding - Production”或“EF - Analytics &amp; Advertising”）
- 安装[!DNL Adobe Cloud Connector]扩展（默认情况下包含在自定义webhook操作中）
- 安装特定于目标的扩展并配置其凭据
- 使用“密钥”功能（数据收集>事件转发>密钥）安全地存储API密钥、令牌和凭据
- 配置环境（开发、暂存、生产）以实现安全发布工作流程

**Experience League文档：**

- [事件转发快速入门](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)
- [事件转发扩展目录](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [事件转发密钥](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)
- [Adobe云连接器扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### 阶段3：事件规则定义

**应用程序函数：** AEP：事件规则定义，AEP：目标映射

**您将配置的内容：**&#x200B;用于评估传入事件数据、应用条件以筛选应转发的事件，以及定义将数据发送到目标端点的操作的规则。 每个规则都包含条件（触发时间）和操作（要执行的操作）。 数据元素从XDM事件有效负载中提取并转换值，以在规则条件和操作配置中使用。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决定：事件过滤策略**
>
>如何确定哪些事件转发到每个目标？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 转发所有事件 | 目标需要一个完整的事件流（例如，数据仓库用于原始事件存储） | 最简单的配置 — 无需任何条件。 目标位置的数据量很大。 考虑目标成本和费率限制。 |
>| 按事件类型筛选 | 不同的目标需要不同的事件类型（例如，从购买到广告，从页面查看到分析） | 使用基于`arc.event.xdm.eventType`或类似XDM字段的条件。 减少目标位置不必要的数据。 |
>| 按事件属性过滤 | 只应转发符合特定条件的特定事件（例如，超过阈值的购买、特定页面路径的事件） | 在规则条件中使用数据元素值。 更加复杂，但会减少目的地的噪音。 |

>[!NOTE]
>
>**决定：数据转换方法**
>
>应该如何为目标有效负载转换XDM事件数据？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 通过数据元素进行直接XDM字段映射 | 目标字段会完全映射到XDM字段（与基于扩展的转发相同） | 创建引用XDM路径的数据元素（例如，`arc.event.xdm.commerce.order.priceTotal`）。 扩展通常提供映射UI。 |
>| 自定义代码转换 | 目标要求的有效负载格式与XDM有显着差异，或者字段需要散列、连接或重组 | 使用自定义代码数据元素或操作级自定义代码转换有效负载。 更灵活，但更难以维护。 |
>| 数据元素和自定义代码的组合 | 有些字段直接映射，而另一些字段则需要转换 | 将数据元素用于简单映射，将自定义代码块用于复杂转换。 在可维护性和灵活性之间取得平衡。 |

>[!NOTE]
>
>**决定：转发数据中的PII处理**
>
>在转发之前应如何处理个人身份信息？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 完全排除PII字段 | 目标不需要PII，并且治理策略会限制共享 | 配置规则以忽略转发有效负载中的PII字段。 实现隐私合规的最简单方法。 |
>| 转发前的哈希PII字段 | 目标需要哈希标识符（例如，[!DNL Meta]需要用于转化API的SHA-256哈希电子邮件） | 使用自定义代码数据元素来应用SHA-256哈希处理。 某些扩展会自动处理哈希处理。 |
>| 按合约基准转发PII | 目标具有数据处理协议，并且存在共享PII的法律基础 | 确保数据使用标签和治理策略(S3)允许共享。 记录法律依据。 |

**UI导航：** [!DNL Experience Platform] >数据收集>事件转发>选择属性>数据元素/规则

**密钥配置详细信息：**

- **数据元素**&#x200B;使用路径前缀`arc.event.xdm.`引用传入XDM事件（例如，页面URL的`arc.event.xdm.web.webPageDetails.URL`）
- **规则条件**&#x200B;评估数据元素值以确定是否应触发规则
- **规则操作**&#x200B;使用特定于扩展的操作（对于选项A）或云连接器“发出获取调用”操作（对于选项B）将数据发送到目标
- 每个规则可以有多个操作，允许将单个事件转发到多个目标
- 当同一事件可能触发多个规则时，可使用规则排序来控制评估顺序
- 在发布到生产环境之前，在开发环境中彻底测试规则

**选项差异的位置：**

选项A （基于扩展）的&#x200B;**：**

使用目标扩展的预建操作类型配置规则操作。 例如，[!DNL Meta]转化API扩展提供了“发送事件”操作，可将XDM字段映射到[!DNL Meta]事件参数(event_name、event_time、user_data、custom_data)。 该扩展处理有效负载格式、散列和API通信。

选项B （自定义Webhook）的&#x200B;**：**

使用Cloud Connector扩展的“发出获取调用”操作配置规则操作。 指定目标URL、HTTP方法（通常为POST）、请求标头（包括授权），并使用数据元素和/或自定义代码构建请求正文。 您负责精确匹配目标API的预期有效负载格式。

选项C （混合）的&#x200B;**：**

为每个目标创建单独的规则。 基于扩展的规则使用扩展的操作类型；自定义规则使用云连接器获取调用。 所有规则都共存于同一属性中，并针对每个传入事件进行独立评估。

**Experience League文档：**

- [事件转发规则](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [事件转发中的数据元素](https://experienceleague.adobe.com/en/docs/experience-platform/tags/ui/data-elements)
- [数据收集中的规则](https://experienceleague.adobe.com/en/docs/experience-platform/tags/ui/rules)
- [Adobe云连接器扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### 第4阶段：发布和激活

**应用程序函数：** AEP：转发执行

**要配置的内容：**&#x200B;发布工作流程，用于提升从开发到暂存再到生产的事件转发规则。 事件转发使用与Tags相同的基于库的发布模型，以及环境和构建构件，这些构件可控制Edge Network中处于活动状态的配置。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决定：发布工作流程严格**
>
>发布过程应该有多严格？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 直接到生产（开发>生产） | 小型团队、低风险目的地或概念验证实施 | 部署速度更快，但生产问题风险更高。 适用于非关键目标的初始测试。 |
>| 全面环境进展（开发>暂存>生产） | 具有关键目标（广告平台、数据仓库）的生产实施 | 建议用于所有生产用例。 暂存允许在生产部署之前使用实际流量进行验证。 |

**UI导航：** [!DNL Experience Platform] >数据收集>事件转发>选择属性>发布流

**密钥配置详细信息：**

- 创建一个库，其中包含要发布的所有规则、数据元素和扩展配置
- 首先在开发环境中使用事件转发监控工具进行生成和测试，以验证事件是否正确转发
- 提升至暂存环境，以供对实时流量进行预生产验证
- 仅在确认在暂存环境中成功交付事件后发布到生产环境
- 使用库版本控制来跟踪更改并在需要时启用回滚

**Experience League文档：**

- [发布概述](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/overview)
- [库](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/libraries)
- [环境](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/environments)
- [内部版本](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/builds)

### 第5阶段：监测和验证

**应用程序函数：** AEP：正在监视

**您将配置哪些功能：**&#x200B;监视功能板和验证进程以确认事件转发成功、诊断故障以及维护事件转发部署的运行状况。

此阶段中的&#x200B;**决策点：**

>[!NOTE]
>
>**决定：监视深度**
>
>应在多大程度上监测事件转发？
>
>| 选项 | 何时选择 | 注意事项 |
>| --- | --- | --- |
>| 仅限事件转发监视仪表板 | 对非关键目标或初始部署进行基本监控 | 提供转发成功/失败率和目标响应代码的概述。 对于大多数实施来说已经足够。 |
>| 事件转发监控+目标端验证 | 数据完整性直接影响业务成果的关键目标（广告转化跟踪、数据仓库完整性） | 具有目标端接收确认的交叉引用Adobe端转发指标。 捕获目标接受请求但无法处理数据的边缘情况。 |
>| 完整可观察性栈栈（事件转发监控+目标验证+ AEP警报） | 具有SLA数据交付要求的企业级部署 | 将事件转发监控与AEP平台警报结合使用，以便全面了解相关信息。 配置用于转发故障阈值的警报通知。 |

**UI导航：** [!DNL Experience Platform] >数据收集>事件转发>选择属性>监视

**密钥配置详细信息：**

- 事件转发监视工具显示每个规则和每个目标的事件量、成功率和错误详细信息
- 监视目标的HTTP响应代码 — 2xx表示成功，4xx表示客户端错误（可能是有效负载或身份验证问题），5xx表示目标端失败
- 使用[!DNL Adobe Experience Platform Debugger]浏览器扩展检查从客户端通过Edge Network流向事件转发规则的事件
- 通过检查转发的事件是否出现在目标系统中来端到端验证（例如，检查[!DNL Google Analytics]实时报表、[!DNL Meta]事件管理器或Data Warehouse表）
- 为源故障和数据流故障设置AEP警报，以捕获可能会阻止事件到达事件转发规则的上游问题

**Experience League文档：**

- [事件转发监测](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring)
- [Adobe Experience Platform Debugger](https://experienceleague.adobe.com/en/docs/experience-platform/debugger/home)
- [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

## 实施注意事项

此部分涵盖在整个实施过程中要牢记的护栏、常见隐患、最佳实践和权衡取舍决策。

### 护栏和限制

- 事件转发在Edge Network中实时处理事件 — 默认情况下，失败的投放不存在批处理模式或重试队列
- Edge Network速率限制适用于每个数据流处理的事件数量总计 — [Edge Network护栏](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/guardrails)
- 事件转发规则执行服务器端并且无法访问客户端资源(DOM、Cookie、localStorage)
- 事件转发规则中的自定义代码在沙盒环境中运行 — 并非所有浏览器JavaScript API都可用
- Cloud Connector获取调用具有超时限制 — 响应缓慢的目标可能会导致超时
- 事件转发受Edge Network地理位置路由的约束 — 事件在最近的Edge位置处理
- 转发请求的最大有效负载大小受Edge Network限制约束

### 常见陷阱

- **转发所有XDM字段而不筛选：**&#x200B;将整个XDM事件有效负载发送到只需要几个字段的目标将浪费带宽、增加目标成本，并且可能会无意中共享PII。 始终仅映射转发规则中的必填字段。

- **不保护带有密码的凭据：**&#x200B;对数据元素或规则操作中的API密钥或令牌进行硬编码会产生安全风险。 始终使用数据收集密钥功能安全地存储凭据并在规则中引用它们。

- **忽略目标速率限制：**&#x200B;第三方目标通常具有API速率限制。 如果事件卷超出目标的容量，可能会丢弃事件或限制API访问。 查看目标文档以了解速率限制，并根据需要实施筛选以减少事件量。

- **直接发布到生产环境而不进行暂存：**&#x200B;跳过暂存环境意味着仅在生产环境中发现错误，这可能会导致关键目标的数据丢失。 始终先在暂存环境中使用实时流量进行验证。

- **未监视HTTP响应代码：**&#x200B;触发规则时没有出现错误，无法保证目标已成功处理数据。 监视目标响应代码（在事件转发监视工具中可用）并调查任何非2xx响应。

- **配置错误的XDM路径引用：**&#x200B;数据元素使用`arc.event.xdm.`前缀引用传入的事件字段。 不正确的路径（例如，缺少某一级别的嵌套）会静默地生成null值，而不是引发错误。 使用调试器验证数据元素值。

### 最佳实践

- **从单个目标开始，然后逐步展开** — 在添加其他规则和目标之前，验证具有一个目标的端到端事件转发。 这简化了调试，并增强了人们对基础架构的信心。

- **使用一致的命名约定** — 使用可标识目标、事件类型和环境的清晰约定命名数据元素、规则和库（例如，“规则： Meta — 购买事件”、“DE：订单总计”）。

- **为隐私实施字段级筛选** — 即使目标声明正确处理PII，也应用服务器端筛选，在离开Edge Network之前删除或散列敏感字段。 与客户端标记相比，这是事件转发的主要治理优势。

- **版本配置** — 使用库发布工作流维护事件转发配置的版本化快照。 记录每个库版本包含的内容以进行审核和回滚。

- **使用Platform Debugger进行测试** — [!DNL Adobe Experience Platform Debugger]扩展提供了从客户端SDK到Edge Network处理的事件生命周期的可见性。 在开发和故障诊断过程中使用它。

- **将事件转发规则与XDM架构设计保持一致** — 如果事件转发是已知的要求，请设计您的XDM架构和事件分类以包含目标所需的字段。 部署后修改模式更改更具破坏性。

### 权衡决定

>[!NOTE]
>
>**取舍：扩展简单性与webhook灵活性**
>
>预构建的扩展可最大程度地减少实施工作量和维护工作，但它们会将您限制为该扩展支持的功能和有效负载格式。 自定义Webhook提供完全控制，但需要更多的开发和日常维护。
>
>- **基于扩展的（选项A）优点：**&#x200B;上市速度快，减少开发人员依赖性，自动凭据管理，维护工作量降低
>- 基于&#x200B;**Webhook（选项B）的优点：**&#x200B;完全有效负载控制，支持任何HTTP端点，自定义转换逻辑，独立于扩展发布周期
>- **建议：**&#x200B;当扩展可用且足够时，请使用扩展。 仅当目标缺少扩展或者扩展不支持您需要的特定API功能时，才回退到自定义Webhook。 混合方法（选项C）是大多数组织务实的选择。

>[!NOTE]
>
>**取舍：转发所有事件与选择性过滤**
>
>将所有事件转发到目标可确保完整性，但会增加数据量、目标成本和隐私风险。 选择性过滤会减少噪音，但可能会丢失可能有用的事件。
>
>- **转发所有事件均有利于：**&#x200B;数据完整性、简洁性、可长期保存（如果需要，稍后会提供数据）
>- **选择性过滤优惠：**&#x200B;成本效益、降低隐私风险、清除目标数据、遵守数据最小化原则
>- **推荐：**&#x200B;默认为根据事件类型和业务相关性进行选择性筛选。 仅转发每个目标实际需要的事件和字段。 这符合数据最小化原则（GDPR第5条）并降低了运营成本。

>[!NOTE]
>
>**取舍：单个属性与多个属性**
>
>单个事件转发属性更易于管理，但意味着所有规则都共享一个发布工作流。 多个属性提供了隔离功能，但会增加管理开销。
>
>- **单个属性更适合：**&#x200B;简洁性、统一发布、共享的数据元素、更易于调试
>- **多个属性支持：**&#x200B;团队级访问控制、独立发布节奏、目标故障隔离
>- **推荐：**&#x200B;对于大多数实施从单个属性开始。 仅当不同的团队拥有不同的目标集成并需要独立的发布周期，或者法规要求严格隔离数据流时，才应拆分为多个资产。

## 相关文档

以下资源提供了有关本指南涵盖的主题的更多详细信息。

**事件转发**

- [事件转发概述](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [事件转发快速入门](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)
- [事件转发监测](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring)
- [事件转发密钥](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)

**事件转发扩展**

- [服务器端扩展目录](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Adobe云连接器扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Meta Conversions API扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/meta/overview)
- [Google Cloud Platform扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [AWS扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/aws/overview)
- [Snowflake扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/snowflake/overview)
- [Google Ads增强型转化扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-ads-enhanced-conversions/overview)
- [Mailchimp扩展](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/mailchimp/overview)

**数据收集和Edge Network**

- [配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [数据流概述](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview)
- [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Edge Network Server API概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [标记概述](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
