---
title: Customer Experience Orchestration用例、体系结构图和Blueprint
description: 探索Adobe Experience Platform和应用程序的关键业务目标、用例模式以及行业用例。 可视化架构图和Blueprint为系统集成、数据流和解决方案设计提供了技术参考 — 将业务价值与实施联系起来。
doc-type: overview-page
exl-id: 52898310-9723-4ec2-ba10-f45fefe29e93
TQID: https://experienceleague.adobe.com/hScp-97-JZqFMfBJdM6820M95dVE7YoagKJYfruEdao
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: e79d9d6490e4f50c4611dd879b53f0e63a90cd65
workflow-type: tm+mt
source-wordcount: 333
ht-degree: 4%

---

# Customer Experience Orchestration用例和架构图

此网站包含&#x200B;**关键业务目标**，其中概述了可使用Adobe Experience Platform和应用程序实现的示例主要业务价值和目标。 **用例模式**&#x200B;通过可重复的实施方法描述常见的平台和应用程序功能。 **行业用例示例**&#x200B;将模式应用于垂直特定的业务场景。 **架构图和Blueprint**&#x200B;是可视化架构和数据流参考图，说明系统集成点、数据和内容流以及操作顺序，为解决方案设计提供技术参考。 这些层共同将业务价值与实施依赖项和体系结构联系起来。

## 主要业务目标

各组织寻求通过数字体验计划实现的战略成果。 每个目标都映射为描述如何实施Adobe Experience Platform和应用程序的用例模式。

<table>
<tr>
  <td><a href="business-objectives/overview.md#acquisition--growth"><strong>收购与增长</strong></a></td>
  <td><a href="business-objectives/overview.md#revenue--monetization"><strong>收入和盈利</strong></a></td>
  <td><a href="business-objectives/overview.md#cost--efficiency"><strong>成本和效率</strong></a></td>
</tr>
<tr>
  <td><a href="business-objectives/overview.md#customer-experience"><strong>客户体验</strong></a></td>
  <td><a href="business-objectives/overview.md#analytics--insights"><strong>Analytics &amp; Insights</strong></a></td>
  <td><a href="business-objectives/overview.md#qualification--sales-b2b"><strong>资格鉴定和销售(B2B)</strong></a></td>
</tr>
</table>

[查看所有业务目标](business-objectives/overview.md)

## 用例模式

可重复的实施方法，这些方法描述如何使用提供这些功能的相关功能和应用程序组件实现特定结果。

<table>
<tr>
  <td><a href="use-case-patterns/overview.md#audience-building--activation"><strong>Audience Building &amp; Activation</strong></a></td>
  <td><a href="use-case-patterns/overview.md#personalization"><strong>个性化</strong></a></td>
  <td><a href="use-case-patterns/overview.md#campaign-management--orchestration"><strong>营销活动管理和编排</strong></a></td>
</tr>
<tr>
  <td><a href="use-case-patterns/overview.md#analysis"><strong>分析</strong></a></td>
  <td><a href="use-case-patterns/overview.md#conversational-experience"><strong>对话体验</strong></a></td>
  <td></td>
</tr>
</table>

[查看所有用例模式](use-case-patterns/overview.md)

## 按行业探索用例示例

针对特定行业定制的使用案例，每个行业对应于实施模式和业务目标。

<table>
<tr>
  <td><a href="industry-use-cases/retail/retail-overview.md"><strong>零售</strong></a></td>
  <td><a href="industry-use-cases/financial-services/financial-services-overview.md"><strong>金融服务</strong></a></td>
  <td><a href="industry-use-cases/healthcare/healthcare-overview.md"><strong>医疗保健</strong></a></td>
</tr>
<tr>
  <td><a href="industry-use-cases/automotive/automotive-overview.md"><strong>汽车</strong></a></td>
  <td><a href="industry-use-cases/travel-hospitality/travel-hospitality-overview.md"><strong>旅游和酒店业</strong></a></td>
  <td><a href="industry-use-cases/telecommunications/telecommunications-overview.md"><strong>电信</strong></a></td>
</tr>
<tr>
  <td><a href="industry-use-cases/media-entertainment/media-entertainment-overview.md"><strong>媒体和娱乐</strong></a></td>
  <td><a href="industry-use-cases/insurance/insurance-overview.md"><strong>保险</strong></a></td>
  <td><a href="industry-use-cases/b2b/b2b-overview.md"><strong>B2B</strong></a></td>
</tr>
</table>

[查看所有行业用例](industry-use-cases/use-case-catalog.md)

## 架构图和Blueprint

可视化架构和数据流参考图，其中说明了Adobe Experience Platform和应用程序的系统集成点、数据和内容流以及操作顺序。

<table>
<tr>
  <td>
    <a href="experience-platform/guardrails.md">
      <img alt="Experience Platform中心和Edge架构" src="experience-platform/assets/aep_edge_hub_latency_v1.svg" />
    </a>
    <div>
      <a href="experience-platform/guardrails.md">
    <strong>Experience Platform Hub和Edge架构和护栏图</strong>
    </a>
    </div>
  </td>
   <td>
    <a href="experience-platform/deployment/websdk.md">
      <img alt="Edge序列图" src="experience-platform/deployment/assets/web_sdk_sequence.svg" />
    </a>
    <div>
      <a href="experience-platform/deployment/websdk.md">
    <strong>Web SDK和Edge Network序列图</strong>
    </a>
    </div>
  </td>
  <td>
    <a href="customer-journeys/journey-optimizer/journey-optimizer-overview.md">
      <img alt="Journey Optimizer概述图" src="customer-journeys/journey-optimizer/images/ajo-architecture.svg" />
    </a>
    <div>
      <a href="customer-journeys/journey-optimizer/journey-optimizer-overview.md">
    <strong>Adobe Journey Optimizer概述图</strong>
    </a>
    </div>
  </td>
</tr>
</table>