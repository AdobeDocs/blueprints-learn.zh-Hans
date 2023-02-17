---
title: 数据访问和导出 Blueprint
description: 此 Blueprint 概述了通过 Adobe Experience Platform 和应用程序访问和导出数据的所有方法。
product: adobe experience platform
solution: Experience Platform, Journey Optimizer, Real-time Customer Data Platform, Tags
exl-id: 2ca51a29-2db2-468f-8688-fc8bc061b47b
source-git-commit: dabb5ae0bf2fc186f67d4aa93a2e9e8c5bb04498
workflow-type: ht
source-wordcount: '1513'
ht-degree: 100%

---

# 数据访问和导出 Blueprint

数据访问和导出 Blueprint 概述了通过 Adobe Experience Platform 和应用程序访问或导出数据的所有可能方法。

该 Blueprint 分为两个类别，分别用于通过 Experience Platform 和应用程序访问数据。首先是通过 Experience Platform 和应用程序导出数据的方法；这被视为数据导出的推送类型方法。其次是通过 Experience Platform 和应用程序访问数据的方法；这被视为数据访问的拉取类型方法。

数据访问方法：

* [实时客户档案访问 API](#rtcp-profile-access-api)
* [数据访问 API](#data-access-api)
* [查询服务](#query-service)

数据导出方法：

* [客户端标记](#client-side-tags-extensions)
* [事件转发](#event-forwarding)
* [Real-time Customer Data Platform 目标](#RTCDP-destinations)
* [Journey Optimizer 自定义操作](#jo-custom-actions)

## 数据访问和导出概述架构

<img src="../experience-platform/assets/aep_data_flow.svg" alt="数据准备和摄入 Blueprint 的参考架构" style="width:90%; border:1px solid #4a4a4a; margin-bottom: 15px;" class="modal-image" />

## 数据访问方法

### 实时客户档案访问 API {#rtcp-profile-access-api}

客户可以使用实时客户档案访问 API 从实时客户档案存储中访问单个统一的用户档案，包括所有用户档案标识、受众成员资格、属性和体验事件。

请参阅[实时客户档案访问 API](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=zh-Hans) 文档以了解其他信息。

#### 用例

* 查找单个用户档案以便为座席客户互动添加背景信息，例如聊天和呼叫中心中的支持互动，或者销售点的销售互动。
* 能够为外部系统（例如 Web 个性化系统或优惠决策系统）所做的个性化决策添加背景信息。

#### 注意事项

* 实时客户档案[护栏](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)适用。
* 专为一次进行单个用户档案查找而设计。不用于出于分析或数据科学目的批量访问或下载所有用户档案。
* 用户档案查找响应时间遵循用户档案护栏。实时低延迟要求 - 例如，对于同页个性化要求，应利用来自 [Adobe Target 连接](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=zh-Hans)或[自定义个性化连接](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=zh-Hans)的边缘用户档案来实时访问用户档案，实现浏览器内和应用程序内个性化。

### 数据访问 API {#data-access-api}

使用数据访问 API，客户可以直接访问存储在 Experience Platform 数据湖中的原始数据集文件。

* 有关使用数据访问 API 的其他详细信息，请参阅此[文档](https://experienceleague.adobe.com/docs/experience-platform/data-access/home.html?lang=zh-Hans)。

#### 用例

* 从 Experience Platform 中提取原始和已处理的数据文件，以便在企业环境中进行存储和评估。

#### 注意事项

* 与使用标记、事件转发或 RTCDP 目标等流传输数据导出方法相比，以批次异步方式访问数据时，对数据的访问将具有固有的延迟。
* 在处理到 Experience Platform 中时，数据文件会批量存储为文件集合，并以拼接格式进行压缩和存储。因此，在访问文件并将其下载到其他环境时，必须按批次和文件（与整个数据集对应）系统地访问这些文件，而且对数据的任何操作都必须考虑以拼接格式压缩的文件。

### 查询服务 {#query-service}

使用 Experience Platform 查询服务，客户可以查询 Experience Platform 内的数据集并保留查询结果。SQL 客户端可用于查询查询响应并将查询响应保留在 SQL 客户端可支持的所需存储目标中。查询服务 UI 可用于将 SQL 结果存储在 Experience Platform 中的目标数据集中，或将结果保存到本地计算机。

* 有关连接到 SQL 客户端以保留来自 Experience Platform 查询服务的 SQL 结果的其他详细信息，请参阅以下[文档](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=zh-Hans)。

#### 用例

* 从 Experience Platform 数据集查询原始数据并保留查询结果。
* 查询用户档案快照数据集以提取有关实时客户用户档案的分析。[文档](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=zh-Hans#profile-attribute-datasets).
* 将查询结果存储到单独的数据集中以便访问，或存储到已启用用户档案的数据集中，该数据集稍后可通过 RTCDP 和其他访问实时客户档案的 Experience Cloud 应用程序导出。

#### 注意事项

* 与使用标记、事件转发或 RTCDP 目标等流传输数据导出方法相比，以批次异步方式访问数据时，对数据的查询将具有固有的延迟。
* 使用查询服务只能查询 Experience Platform 数据湖中可用的数据。实时客户档案存储、标识图、Customer Journey Analytics 不能使用查询服务直接查询。仅当将数据集导出到数据湖后，才能查询这些数据集，如用户档案快照数据集的示例中所示。
* 请注意，查询结果数和查询超时的护栏适用，如[查询服务护栏](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=zh-Hans)文档中所述。

## 数据导出方法

### 客户端标记扩展 {#client-side-tags-extensions}

可以使用 Adobe 的标记解决方案部署扩展。部署扩展后，数据请求将直接部署在客户端浏览器或应用程序上，并且可以调用请求以将数据和请求发送到所需目标。

请参阅[标记概述](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)文档以了解其他信息。

#### 用例

* 使用标记直接从客户端环境收集原始流传输信息。

#### 注意事项

* 不能直接访问任何服务器端信息，如 Experience Platform 实时客户档案和受众成员资格。
* 向页面添加其他数据收集标记可能会增加页面加载时间。
* 能够设置规则，以便仅在满足特定条件时才请求数据。
* 直接从客户端收集数据，以限制在收集数据之前可以执行的转换和扩充类型。

### 事件转发 {#event-forwarding}

数据收集请求会直接收集到 Adobe 的边缘网络。可以在边缘网络配置到外部 RESTful 端点的请求，从而将这些请求转发到外部目标。

请参阅以下[事件转发](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=zh-Hans)文档以了解其他信息。

#### 用例

* 使用 Adobe 的服务器端事件转发，直接从客户端环境将原始流传输信息收集到企业端点。

#### 注意事项

* 要使用事件转发，必须使用 WebSDK 或 MobileSDK 将数据发送到边缘网络。
* 事件转发方法可减少页面加载时间和页面权重，因为页面上添加了更多标记。
* 当前不支持从边缘用户档案或其他数据源进行扩充。
* 支持有限的数据筛选和简单的映射转换。

### Real-time Customer Data Platform 目标 {#RTCDP-destinations}

用户档案属性数据和受众成员资格数据可以激活到企业和广告目标。这意味着必须将导出的数据摄入到 Experience Platform 实时客户档案中。

请参阅 [Real-time Customer Data Platform 目标](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=zh-Hans)文档以了解其他信息。

#### 用例

* 激活用户档案属性信息，包括企业间数据存储、分析工具、电子邮件系统或支持系统的受众成员资格。
* 将用户档案受众成员资格激活到外部广告供应商，以根据用户档案定位和个性化内容。

#### 注意事项

* 可激活用户档案属性和受众会员资格。原始体验事件当前无法作为 RTCDP 目标的一部分进行激活。
* 根据区段评估的性质和目标接受的摄入协议的性质，可能按流传输或批次方式进行激活。

### Journey Optimizer 自定义操作 {#jo-custom-actions}

使用 Journey Optimizer，客户可以从历程画布中调用自定义操作，以将有效负载或消息发送到已配置的外部 API 端点。可以将操作配置为来自任何提供商的任何服务，只要该服务可使用 JSON 格式有效负载通过 REST API 调用。此有效负载可以包括在历程中配置的事件信息、用户档案属性和先前事件数据、转换和扩充。

请参阅 [Journey Optimizer 自定义操作](https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=zh-Hans)文档以了解其他信息。

#### 用例

* 来自 Experience Platform 和 Journey Optimizer 的激活事件，其中包含来自实时客户档案的其他信息。
* 当客户到达历程的特定点时通知外部系统。

#### 注意事项

* 有关 [Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=zh-Hans) 支持的吞吐量和[实时客户档案](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)支持的扩充的护栏。
* 自定义操作可以按流传输方式逐一对历程中的每个事件或用户档案执行。无法跨客户历程以文件或聚合请求的形式执行批量操作或批量数据导出。
* 对实时客户用户档案属性和体验事件的流传输访问，这些属性和体验事件可包含在激活有效负载中。
* 在将事件发送到外部目标之前，可以过滤并应用简单的映射转换。
