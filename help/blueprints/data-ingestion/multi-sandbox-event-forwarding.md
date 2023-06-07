---
title: 多沙盒事件转发数据收集
description: 了解如何将使用Experience PlatformWeb和移动SDK收集的数据配置为收集单个事件并转发到多个Experience Platform沙箱。
solution: Data Collection
kt: 7202
source-git-commit: e9a9abeaa722bb2f9a232f4e861b1b5eae86edd1
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 4%

---


# 多沙盒事件转发数据收集

此Blueprint显示如何将使用Experience PlatformWeb和移动SDK收集的数据配置为收集单个事件并转发到多个AEP沙盒。 此Blueprint特定于使用的多沙盒数据收集 [!UICONTROL 事件转发] 以实现这一目标。

除了使用复制事件之外 [!UICONTROL 事件转发] 功能，您可以添加、筛选或处理符合其他沙盒要求的原始收集数据。

[!UICONTROL 事件转发] 使用包含 [!UICONTROL 数据元素]， [!UICONTROL 规则]、和 [!UICONTROL 扩展] 对于您的数据要求是必需的。 对于传入事件，您的 [!UICONTROL 事件转发] 属性可以收集数据，并在转发之前根据需要进行管理。

您的目标沙盒要求配置由Adobe使用的HTTP流端点 [!UICONTROL 云连接器] 扩展。

## 用例

* 全局数据报告 — 使用多个沙盒隔离操作环境时，以及将数据收集整合到一个沙盒以进行跨沙盒报告的需要。 路由Experience Edge事件 [!UICONTROL 事件转发] “到”报告沙盒允许每个沙盒操作环境将数据实时收集时发送到报告沙盒。

* 根据每个沙盒操作环境的不同数据规则，跨沙盒管理数据收集。

## 应用程序

* [!DNL Experience Platform] 数据收集
* [!UICONTROL 事件转发]
* AEP [!UICONTROL 扩展]
* [!UICONTROL 云连接器扩展]

## 注意事项

替换为 [!UICONTROL 事件转发] 作为将数据发送到多个沙盒的方法，在您的解决方案架构中必须考虑一些注意事项。

### 无HIPAA数据

[!UICONTROL 事件转发] 不被认为是HIPAA就绪，不应在收集HIPAA数据的任何HIPAA用例中使用。 但是，用于以下目的的基础架构： [!UICONTROL 事件转发] 随时准备就绪，且完全由客户自行决定。 而您的 [!UICONTROL 事件转发] Tag属性位于 [!UICONTROL 事件转发] 系统，则收集的所有数据有效负载都会发送到 [!UICONTROL 事件转发] 处理系统。 正是这个过程使得 [!UICONTROL 事件转发] 关于HIPAA用例。 整个有效负载已发送至 [!UICONTROL 事件转发] 系统，这将包括任何HIPAA值。 即使 [!UICONTROL 事件转发] 规则将在将数据发送到目标之前筛选这些数据，这样HIPAA数据仍会发送到不符合HIPAA要求的基础架构。 但是，有效负载数据永远不会存储，只是传递数据。

### 不同的数据流和流端点

当数据流从以下位置流经数据流时： [!UICONTROL 平台边缘网络]，使用时 [!UICONTROL 事件转发] 对于另一个AEP沙盒，要求不要使用与生成原始收藏集的数据流相同的数据流或流端点。 这可能会对AEP实例造成不利影响，并可能触发DoS情况。

### 预计的流量

每个用例都需要查看流量。 这一点很重要，因为高流量可能会导致限制情况，如果发生这种情况，客户会收到通知。

## 架构

![多沙盒 [!UICONTROL 事件转发]](assets/multi-sandbox-data-collection.png)

1. 收集事件数据并将其发送至 [!UICONTROL 平台边缘网络] 为使用，需要 [!UICONTROL 事件转发]. 客户可以使用客户端的Adobe标记或 [!UICONTROL 平台Edge Network服务器API] 用于服务器到服务器数据收集。 此 [!UICONTROL Platform Edge Network API] 可以提供服务器到服务器的收集功能。 但是，这确实需要不同的编程模型才能实现。 请参阅 [Edge Network服务器API概述](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=en).

1. 收集的有效负载从标记实施发送到 [!UICONTROL 平台边缘网络] 到 [!UICONTROL 事件转发] 服务并由其自身处理 [!UICONTROL 数据元素]， [!UICONTROL 规则] 和 [!UICONTROL 操作]. 您可以详细了解以下各项的差异： [标记和 [!UICONTROL 事件转发]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en#differences-from-tags).

1. An [!UICONTROL 事件转发] 属性也是接收从收集的事件数据所必需的 [!UICONTROL 平台边缘网络]. 该事件数据是由部署的标记实施还是服务器到服务器收集发送到Platform Edge Network。 作者定义在转发到第二个沙盒之前用于扩充事件数据的数据元素、规则和操作。 考虑使用自定义代码 [!DNL JavaScript] 数据元素，以帮助构建用于沙盒提取的数据。 通过与Platform数据准备功能相结合，您有多个选项可用于管理数据结构。

1. 目前，Adobe的使用 [!UICONTROL 云连接器扩展] 在中需要 [!UICONTROL 事件转发] 属性。 在规则处理或扩充事件数据后，可在为将有效负载发送到第二个沙盒的POST配置的获取调用中使用Cloud Connector

1. 第二个沙盒需要数据摄取的流端点。 您还可以考虑AEP中的数据准备功能，以帮助摄取和映射 [!UICONTROL 事件转发] 有效负载到XDM。 请参阅AEP文档创建 [使用UI的HTTP API流连接](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=zh-Hans)
