---
title: 数据访问和导出Blueprint
description: 此Blueprint提供并概述了从Adobe Experience Platform和应用程序访问和导出数据的所有方法。
product: adobe experience platform
solution: Experience Platform, Journey Optimizer, Real-time Customer Data Platform, Tags
source-git-commit: 67e66068bb8a2106dd8aa9784b5a39377225c045
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 4%

---

# 数据访问和导出Blueprint

数据访问和导出Blueprint概述了从Adobe Experience Platform和应用程序访问或导出数据的所有可能方法。

Blueprint将划分为两个类别，用于从Experience Platform和应用程序访问数据。 首先，处理Experience Platform和应用程序数据的方法；这将被视为数据输出的推送类型方法。 其次，从Experience Platform和应用程序访问数据的方法；这将被视为数据访问的拉取类型方法。

数据访问方法

* [实时客户资料访问API](#rtcp-profile-access-api)
* [数据访问API](#data-access-api)
* [查询服务](#query-service)

数据导出方法

* [客户端标记](#client-side-tags-extensions)
* [事件转发](#event-forwarding)
* [Real-time Customer Data Platform目标](#RTCDP-destinations)
* [Journey Optimizer自定义操作](#jo-custom-actions)

## 数据访问和导出概述架构

<img src="../experience-platform/assets/aep_data_flow.svg" alt="数据准备和摄入 Blueprint 的参考架构" style="width:90%; border:1px solid #4a4a4a" />

## 数据访问方法

### 实时客户资料访问API {#rtcp-profile-access-api}

客户可以使用实时客户资料访问API从实时客户资料存储中访问单个统一的资料，包括所有资料标识、受众成员身份、属性和体验事件。

请参阅 [实时客户资料访问API](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=en) 文档以了解其他信息。

#### 用例

* 查找单个用户档案以向座席客户交互添加上下文，例如通过聊天和呼叫中心进行的支持交互，或在销售点进行销售交互。
* 允许向外部系统（例如Web个性化系统或选件决策系统）所做的个性化决策添加上下文。

#### 注意事项

* 实时客户资料 [护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) 。
* 专为一次进行单个用户档案查找而设计。 不用于批量访问或下载整个配置文件群体以用于分析或数据科学。
* 用户档案查找响应时间与用户档案护栏相连。 低延迟要求 — 例如，对于同一页面个性化要求，应使用边缘配置文件或客户个性化目标来实现低延迟的配置文件访问。 [文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=en).

### 数据访问API {#data-access-api}

使用数据访问API，客户可以直接访问存储在Experience Platform数据湖中的原始数据集文件。

* 有关使用数据访问API的其他详细信息，请参阅 [文档](https://experienceleague.adobe.com/docs/experience-platform/data-access/home.html?lang=en).

#### 用例

* 从Experience Platform中提取原始和已处理的数据文件，以便在企业环境中进行存储和评估。

#### 注意事项

* 与使用标记、事件转发或RTCDP目标等流数据出口方法相比，以批量异步方式访问数据时，对数据的访问将具有内在的延迟时间。
* 数据文件在处理为Experience Platform时，会批量存储为文件集合，并进行压缩和存储，格式为镶木地板。 因此，在访问文件并将其下载到其他环境时，必须按批次和文件（与整个数据集对应）系统地访问这些文件，而且对数据的任何操作都必须考虑以镶木地板格式压缩的文件。

### 查询服务 {#query-service}

使用experience platform查询服务，客户可以查询Experience Platform内的数据集并保留查询结果。 SQL客户端可用于查询查询响应并将查询响应保留在SQL客户端可支持的所需存储目标中。 查询服务UI可用于将SQL结果存储在Experience Platform中的目标数据集中，或将结果保存到本地计算机。

* 有关连接到SQL客户端以保留来自Experience Platform查询服务的SQL结果的其他详细信息，请参阅以下内容 [文档](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=en).

#### 用例

* 从Experience Platform数据集查询原始数据并保留查询结果。
* 查询用户档案快照数据集以提取有关实时客户用户档案的分析。 [文档](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=en#profile-attribute-datasets).
* 将查询结果存储到单独的数据集中以用于访问，或存储到启用了用户档案的数据集中，该数据集稍后可通过RTCDP和其他访问实时Experience Cloud档案的应用程序进行获取。

#### 注意事项

* 与使用标记、事件转发或RTCDP目标等流数据出口方法相比，以批量异步方式查询数据时，对数据的访问将具有内在的延迟时间。
* 只能使用查询服务查询Experience Platform数据湖中可用的数据。 实时客户资料存储、身份图、Customer Journey Analytics不能使用查询服务直接查询。 仅当数据集导出到数据湖时，才能查询这些数据集，如配置文件快照数据集的示例中所示。
* 请注意，查询结果数和查询超时的防护适用，如 [查询服务护栏](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=en) 文档。

## 数据导出方法

### 客户端标记扩展 {#client-side-tags-extensions}

可以使用Adobe的标记解决方案部署扩展。 部署扩展后，数据请求将直接部署在客户端浏览器或应用程序上，并且可以调用请求以将数据和请求发送到所需目标。

请参阅 [标记概述](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en) 文档以了解其他信息。

#### 用例

* 使用标记直接从客户端环境收集原始流信息。

#### 注意事项

* 不能直接访问任何服务器端信息，如Experience Platform实时客户资料和受众成员资格。
* 向页面添加其他数据收集标记可能会增加页面加载时间。
* 能够设置规则，以便仅在满足特定条件时才请求数据。
* 直接从客户端收集数据，以限制在收集数据之前可以执行的转换和扩充类型。

### 事件转发 {#event-forwarding}

数据收集请求会直接收集到Adobe的边缘网络。 可以将边缘网络请求到外部RESTful端点配置为将这些请求转发到外部目标。

请参阅以下内容 [事件转发](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en) 文档以了解其他信息。

#### Use Caseas

* 使用Adobe的服务器端事件转发，直接从客户端环境收集原始流信息到企业端点。

#### 注意事项

* 要使用事件转发，必须使用WebSDK或MobileSDK将数据发送到边缘网络。
* 事件转发方法可减少页面加载时间和页面重量，因为页面上添加了其他标记。
* 当前不支持从边缘配置文件或其他数据源扩充内容。
* 支持有限的数据过滤和简单的映射转换。

### Real-time Customer Data Platform目标 {#RTCDP-destinations}

配置文件属性数据和受众成员资格数据可以激活到企业和广告目标。 这意味着必须将获取的数据摄取到Experience Platform实时客户资料中。

请参阅 [Real-time Customer Data Platform目标](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en) 文档以了解其他信息。

#### 用例

* 激活配置文件属性信息，包括企业间数据存储库、分析工具、电子邮件系统或支持系统的受众成员资格。
* 向外部广告供应商激活用户档案受众成员资格，以定位和个性化用户档案的内容。

#### 注意事项

* 可以激活用户档案属性和受众成员关系。 原始体验事件当前无法作为RTCDP目标的一部分进行激活。
* 根据区段评估的性质和目标接受的摄取协议的性质，会在流式处理或批量处理中进行激活。

### Journey Optimizer自定义操作 {#jo-custom-actions}

使用Journey Optimizer客户可以从历程画布中调用自定义操作，以将有效负载或消息发送到已配置的外部API端点。 可以将操作配置为来自任何提供商的任何服务，这些服务可通过具有JSON格式有效负载的REST API调用。 此有效负载可以包括在历程中配置的事件信息、用户档案属性和先前事件数据、转换和扩充。

请参阅 [Journey Optimizer自定义操作](https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=en) 文档以了解其他信息。

#### 用例

* 来自Experience Platform和Journey Optimizer的激活事件，其中包含来自实时客户资料的其他信息。
* 当客户到达历程的特定点时通知外部系统。

#### 注意事项

* 对支持的吞吐量的护栏 [Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=en) 和 [实时客户资料](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) 。
* 自定义操作可以逐个在流中对历程中的每个事件或用户档案执行。 无法跨客户历程以文件或聚合请求的形式执行批量操作或批量数据输出。
* 对实时客户配置文件属性和体验事件的流式访问，这些属性和体验事件可包含在激活有效负载中。
* 在将事件发送到外部目标之前，可以过滤并应用简单的映射转换。










