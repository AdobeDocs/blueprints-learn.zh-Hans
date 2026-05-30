---
title: Audience Activation到目标
description: 了解如何使用Adobe Real-Time CDP评估受众区段并将其发布到外部目标以进行定位或抑制。
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: b0b9d937-45d2-48f9-ac4c-3611c6e35f58
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1365'
ht-degree: 4%

---

# Audience Activation到目标

本指南介绍受众激活到目标用例模式，该模式评估Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)中的受众区段，并将其发布到广告平台、云存储、CRM系统或数据合作伙伴，以进行定位、抑制、相似人群拓展建模或分析扩充。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

此模式涵盖受众激活的整个生命周期，从定义和评估受众区段（通过配置目标连接和发布受众），到监控激活运行状况并强制实施治理合规性。

## 用例模式

**Audience Activation到目标** — 评估受众区段并将其发布到外部目标以进行定位或抑制。

**执行计划：**&#x200B;受众评估>目标配置> Audience Activation >监控

## 用例概述

组织需要向外部系统交付受众数据，以便为付费媒体活动提供支持、丰富CRM记录、与合作伙伴共享数据或提供下游分析。 Audience Activation到目标是RT-CDP中的基本激活模式：它评估哪些配置文件符合目标受众的条件，连接到一个或多个外部目标，将配置文件属性映射到目标特定的字段，并发布受众以供下游使用。

每当目标是在正确的时间以正确的格式将受众数据获取到外部系统时，此模式即适用。 它不涉及消息投放、网站个性化或分析。 它是RT-CDP实施的最常见起点，并作为其他模式在其上构建的构建块。

典型的利益相关者包括管理付费媒体的数字营销团队、充实仓库的数据团队、为营销活动准备联系人列表的CRM团队以及确保出站数据流符合治理要求的隐私团队。

>[!NOTE]
>如果您的组织使用[!DNL Real-Time CDP] B2B edition并激活到基于帐户的目标，请参阅[B2B受众激活](../b2b/account-audience-activation.md)。 该模式共享相同的激活机制，但使用B2B帐户和人员数据模型，并需要B2B edition许可证。

## 主要业务目标

此用例模式支持以下业务目标。

### 获取新客户

通过有针对性的客户获取促销活动、相似受众和付费媒体优化来扩展客户群。

**KPI：**&#x200B;新客户、客户获取成本、潜在客户/潜在客户转化

[了解有关获取新客户的更多信息](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### 降低客户购置成本

提高定位效率，抑制现有客户参与客户获取促销活动，并优化媒体支出。

**KPI：**&#x200B;客户获取成本，每个潜在客户的成本，效率

[了解有关降低客户获取成本的更多信息](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### 优化营销支出和ROI

通过更好的定位、归因、受众抑制和预算分配提高营销投资回报。

**KPI：**&#x200B;成本节约、客户获取成本、递增收入

[了解有关优化营销支出和ROI的更多信息](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## 战术用例示例

- **广告平台受众定位** — 将符合条件的区段推送到付费媒体平台以进行营销活动定位
- **现有客户的付费媒体抑制** — 将已知客户排除在广告平台上的客户获取促销活动之外，以消除浪费的支出
- **相似种子受众** — 将高价值客户区段推送到Facebook、Google Ads或交易台，作为相似人群拓展的种子受众
- **为销售支持进行CRM同步** — 激活高意图或高价值受众，以便销售团队可以优先开展外展活动
- **数据合作伙伴受众共享** — 与数据合作伙伴共享符合条件的受众区段，以进行协作定位或测量
- **用于数据仓库扩充的云存储导出** — 将受众成员资格和配置文件属性导出到Amazon S3、Azure Blob、Google Cloud Storage或SFTP，以用于下游分析
- **重定位受众激活** — 激活未转换为重定位平台的网站访客
- **联系人列表同步到电子邮件服务提供商** — 将受众会员资格推送到第三方电子邮件平台，以便协调外联

## 关键绩效指标

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 客户购置成本(CAC) | 通过激活的受众获取新客户的成本 | 归因于激活受众的总媒体支出/新客户 |
| 受众匹配率 | 已成功匹配目标的激活配置文件的百分比 | 在目标匹配的用户档案/从RT-CDP导出的用户档案 |
| 禁止显示节省 | 通过抑制现有客户进行客户获取促销活动来避免媒体支出 | 预计的CPM x抑制的受众规模 |
| 激活交付率 | 成功传送到目标的配置文件百分比 | 源受众中已交付的用户档案/用户档案 |
| 激活时间 | 从受众定义到首次在目标投放所经过的时间 | 从区段创建到首次确认的数据流运行的测量 |
| 受众群体准确性 | 目标处的预期受众大小和实际受众大小之间的匹配情况 | 目标受众规模/RT-CDP受众规模 |

## 应用程序

- **Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)** — 受众评估、目标管理、受众激活、同意和治理实施
- **Adobe [!DNL Experience Platform] (AEP)** — 配置文件存储，身份服务，分段引擎，数据管理

## 架构

以下参考架构说明了受众和配置文件数据如何从Real-Time CDP流向企业目标，包括云存储、流式端点和SaaS应用程序。

![受众和配置文件激活到企业目标的参考架构](/help/blueprints/audience-activation/assets/known_activation.png)

## 相关文档

**目标**

- [目的地概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/home)
- [目标目录](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/overview)
- [将受众激活到流目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [将受众激活到批量配置文件导出目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [将按需受众激活到批处理目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [目标护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/guardrails)
- [Destination SDK概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/destination-sdk/overview)

**受众和分段**

- [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language参考](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/pql/overview)
- [流式客户细分](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/edge-segmentation)
- [受众构成概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/audience-composition)
- [分段护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)

**身份和配置文件**

- [Identity服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [身份标识图链接规则](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/identity-linking-logic)
- [配置文件概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/home)
- [合并策略概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/merge-policies/overview)

**数据建模和架构**

- [XDM系统概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/schema/composition)

**数据管理**

- [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [数据治理策略](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/policies/overview)
- [策略实施](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/enforcement/overview)
- [同意和偏好设置](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**监视和可观察性**

- [监测目标的数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/dataflows/ui/monitor-destinations)
- [警报概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/alerts/overview)
- [可观察性分析概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/home)
- [许可证用量仪表板](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**计算属性**

- [计算属性概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/overview)
- [计算属性UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/computed-attributes/ui)

**数据收集和源**

- [来源概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/home)
- [Web SDK概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/web-sdk/home)
- [配置数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/datastreams/configure)

**管理**

- [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)
- [访问控制概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/access-control/home)
- [基于属性的访问控制](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/access-control/abac/overview)

**护栏**

- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)
- [Identity服务护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/guardrails)
- [激活护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/guardrails)
- [摄取护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/ingestion/guardrails)
