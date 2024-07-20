---
title: 多沙盒事件转发数据收集
description: 了解如何将使用 Experience Platform Web 和移动 SDK 收集的数据配置为收集单个事件并转发到多个 Experience Platform 沙盒。
solution: Data Collection
kt: 7202
exl-id: ecc94fc8-9fad-4b88-a153-3d0fc00d8d58
source-git-commit: 72eb4e2ff276279a2fc88ead0b17d77cc8e99b97
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 55%

---

# 多沙盒事件转发数据收集

此Blueprint显示如何将使用[!DNL Experience Platform] Web和Mobile SDK收集的数据配置为收集单个事件并转发到多个AEP沙盒。 此 Blueprint 特定于使用[!UICONTROL 事件转发]实现此目标的多沙盒数据收集。

除了使用[!UICONTROL 事件转发]功能复制事件之外，您还可以添加、过滤或处理原始收集的数据，以满足其他沙盒的要求。

[!UICONTROL 事件转发]使用单独的属性，该属性包含满足您的数据要求所必需的[!UICONTROL 数据元素]、[!UICONTROL 规则]和[!UICONTROL 扩展]。对于传入的事件，您的[!UICONTROL 事件转发]属性可以在转发之前收集数据并根据需要进行管理。

您的目标沙盒需要配置由 Adobe [!UICONTROL Cloud Connector] 扩展使用的 HTTP 流传输端点。

## 用例

* 全局数据报告 - 使用多个沙箱来隔离操作环境，以及需要将数据收集整合到一个沙箱中时，用于跨沙盒报告。通过[!UICONTROL 事件转发]将 Experience Edge 事件路由到报告沙盒，这样每个沙盒操作环境在收集数据时可将数据实时发送到报告沙盒。

* 根据每个沙盒操作环境的不同数据规则，跨沙盒管理数据收集。

## 应用程序

* [!DNL Experience Platform] 数据收集
* [!UICONTROL 事件转发]
* AEP [!UICONTROL 扩展]
* [!UICONTROL 云连接器扩展]

## 注意事项

使用[!UICONTROL 事件转发]方法将数据发送到多个沙盒时，在解决方案架构方面有一些必须考虑的注意事项。

### 无 HIPAA 数据

[!UICONTROL 事件转发]未视为HIPAA就绪，不应在收集HIPAA数据的任何HIPAA用例中使用。

但是，用于[!UICONTROL 事件转发]的基础架构被认为已就绪，完全由客户自行决定。 当[!UICONTROL 事件转发]标记属性驻留在[!UICONTROL 事件转发]系统中时，收集的整个数据有效负载都会发送到[!UICONTROL 事件转发]系统以供处理。此进程使[!UICONTROL 事件转发]涉及HIPAA用例。 整个有效负载已发送至[!UICONTROL 事件转发]系统，此过程将包含任何HIPAA值。 即使[!UICONTROL 事件转发]规则在发送到其目标之前过滤该数据，该HIPAA数据仍被发送到不为HIPAA就绪的基础结构。 但是，有效负荷数据永远不会存储，只是传递而已。

### 不同的数据流和流传输端点

当数据流从[!DNL Platform Edge Network]流经数据流时，在使用[!UICONTROL 事件转发]到另一个AEP沙盒时，要求永远不要使用与生成原始集合的数据流相同的数据流或流端点。 这可能会对 AEP 实例造成不利影响，并可能触发 DoS 情况。

### 估计的流量

每个用例都需要检查流量大小。这一点很重要，因为高流量可能会导致限流情况，如果发生此情况，客户会收到通知。

## 架构

![多沙盒[!UICONTROL 事件转发]](assets/multi-sandbox-data-collection.png)

1. 需要收集事件数据并将其发送至[!DNL Platform Edge Network]才能使用[!UICONTROL 事件转发]。 您可以使用客户端的Adobe标签或服务器到服务器数据收集的[!DNL Platform Edge Network Server API]。

   [!DNL Platform Edge Network API]可以提供服务器到服务器收集功能。 但是，这需要不同的编程模型才能实现。 请参阅 [Edge Network Server API 概述](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hans)。

1. 收集的有效负载从标记实施发送到[!DNL Platform Edge Network]到[!UICONTROL 事件转发]服务，并由其自己的[!UICONTROL 数据元素]、[!UICONTROL 规则]和[!UICONTROL 操作]处理。 若要详细了解这些差异，请参阅[标记和[!UICONTROL 事件转发]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=zh-Hans#differences-from-tags)。

1. 还需要有[!UICONTROL 事件转发]属性才能接收从[!DNL Platform Edge Network]收集的事件数据，无论该事件数据是由已部署的标记实现还是服务器到服务器集合发送到[!DNL Platform Edge Network]。

   作者定义用于在转发到第二个沙盒之前扩充事件数据的数据元素、规则和操作。考虑使用自定义代码 [!DNL JavaScript] 数据元素，以帮助构建用于沙盒摄入的数据。与 Platform 数据准备功能结合使用时，您有多种选择来管理数据结构。

1. 目前，需要在[!UICONTROL 事件转发]属性内使用 Adobe [!UICONTROL Cloud Connector 扩展]。在规则处理或扩充事件数据之后，在为POST配置的获取调用中使用[!UICONTROL Cloud Connector]，将有效负载发送到第二个沙盒。

1. 第二个沙盒需要数据摄取的流端点。 您还可以考虑AEP中的[!UICONTROL 数据准备]功能，以帮助将[!UICONTROL 事件转发]有效负载摄取和映射到XDM。 请参阅 AEP 文档[使用 UI 创建 HTTP API 流传输连接](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=zh-Hans)
