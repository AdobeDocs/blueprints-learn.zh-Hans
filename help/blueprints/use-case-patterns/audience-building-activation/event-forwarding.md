---
title: 事件转发
description: 了解如何将通过Edge Network收集的实时事件数据转发到非Adobe目标以用于分析、存储或广告。
solution: Experience Platform
exl-id: 24964d27-db56-4fa4-a79f-1b6750564b34
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1165'
ht-degree: 0%

---

# 事件转发

本指南介绍了事件转发用例模式，该模式使用[!DNL Adobe Experience Platform] Edge Network上的服务器端处理将实时事件数据分发到非Adobe目标，如第三方Analytics平台、云存储端点、广告网络或自定义Webhook。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

## 用例模式

本节介绍用于实施事件转发的模式和执行计划。

**事件转发** — 将通过Edge Network收集的实时事件数据转发到非Adobe目标以用于分析、存储或广告。

**执行计划：**&#x200B;数据流配置>事件规则定义>目标映射>转发执行>监视

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

## 应用程序

在此用例模式中使用以下应用程序。

- **[!DNL Adobe Experience Platform] (Edge Network)** — 通过配置的数据流从Web SDK、Mobile SDK或Server API接收实时事件数据并进行路由
- **[!DNL Adobe Experience Platform]（事件转发）** — 提供服务器端规则引擎，用于评估、筛选、转换事件数据并将其转发到外部目标
- **[!DNL Adobe Experience Platform]（标记/数据收集）** — 管理事件转发属性生命周期、扩展、规则和发布工作流

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
