---
title: Audience Collaboration
description: 了解如何使用区段匹配在沙盒或组织之间共享和匹配受众区段。
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: 7014849c-5e32-4ec3-a531-c0e8ce896f44
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1351'
ht-degree: 3%

---

# Audience Collaboration

本指南介绍了受众协作用例模式，该模式在[!DNL Real-Time CDP]和[!DNL Adobe Experience Platform]中使用[!DNL Segment Match]以隐私安全的方式跨沙盒或组织共享和匹配受众区段。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

[!DNL Segment Match]允许两个或多个[!DNL Experience Platform]组织（或组织内的沙盒）通过共享区段成员资格信息而协作处理受众数据，而无需公开底层PII。 参与者可以估计重叠、共享受众并将匹配的配置文件激活到下游目标。

## 用例模式

此用例遵循Audience Collaboration模式。

使用[!DNL Segment Match]在沙盒或组织之间共享和匹配受众区段。

**执行计划：**&#x200B;区段选择>匹配配置>重叠估算>受众共享>激活

## 用例概述

组织越来越需要与合作伙伴、子公司或跨业务部门协作处理受众数据，同时保持严格的隐私控制。 受众协作通过启用[!DNL Segment Match]中的安全区段共享来满足此需求，该功能位于[!DNL Real-Time CDP]中，允许两个或更多[!DNL Experience Platform]组织（或沙盒）使用经过哈希处理的隐私安全标识符交换受众成员资格信息。

业务场景通常涉及一个组织（发件人），该组织已构建有价值的受众区段，并想要与合作伙伴组织（接收者）共享该区段，以进行联合定位、禁止或扩充。 在共享之前，双方均可以估计受众重叠以评估价值。 共享后，接收组织可以通过其自己的目标激活匹配的受众。

此模式与标准受众激活不同，因为它在组织或沙盒之间运行，而不是与外部广告或营销目标运行。 它还与数据清理室或第三方协作平台不同，因为它使用[!DNL Experience Platform]身份基础结构在Adobe生态系统中以本机方式运行。

## 主要业务目标

此用例模式支持以下业务目标。

### 获取新客户

通过有针对性的客户获取促销活动、相似受众和付费媒体优化来扩展客户群。 受众协作使组织能够通过将其区段与合作伙伴受众匹配、识别高价值重叠以及通过联合激活接触全新客户来发现新的潜在客户池。

- **KPI：**&#x200B;新客户、客户获取成本、潜在客户/潜在客户转化
- [获取新客户](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### 降低客户购置成本

提高定位效率，抑制现有客户参与客户获取促销活动，并优化媒体支出。 通过跨组织或业务部门共享抑制区段，团队可以避免在已转化客户上浪费支出，并将预算集中在真正的新客户上。

- **KPI：**&#x200B;客户获取成本，每个潜在客户的成本，效率
- [降低客户购置成本](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### 优化营销支出和ROI

通过更好的定位、归因、受众抑制和预算分配提高营销投资回报。 [!DNL Segment Match]支持跨组织受众抑制和联合定位，从而减少重复并提高精度。

- **KPI：**&#x200B;成本节约、客户获取成本、递增收入
- [优化营销支出和ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## 战术用例示例

- **发布者 — 广告商受众匹配** — 品牌与媒体发布者共享其高价值客户区段，以评估重叠并定位与个性化广告匹配的用户，从而提高促销活动相关性而又不公开PII。
- **控股公司内的跨品牌抑制** — 父组织下的多个品牌共享客户区段，以通过收购促销活动抑制姐妹品牌的现有客户，从而减少浪费的广告支出。
- **零售媒体网络受众扩充** — retailer与CPG品牌合作伙伴共享基于购买的区段，使品牌能够以更高的转化率在retailer的媒体网络上定位经验证的购买者。
- **联合营销合作伙伴受众发现** — 两个非竞争品牌在启动联合营销活动之前评估受众重叠以评估合作伙伴潜力，使用重叠估计验证受众一致性。
- **数据合作区段共享** — 数据合作共享中的组织对受众区段进行了哈希处理，以扩大定位范围，同时维护隐私合规性和数据治理控制。
- **多沙盒受众联合** — 一家全球企业跨地区沙盒共享受众区段，以实现跨市场的一致客户定位，同时遵守地区数据驻留要求。
- **忠诚度计划跨合作伙伴激活** — 忠诚度联盟与参与商户共享忠诚度级别区段，以便每个合作伙伴可以向共享的客户群提供适合级别的促销活动。
- **测量和归因协作** — 广告商与媒体合作伙伴共享转化区段，以便合作伙伴可以通过将公开的用户与转化者进行匹配来衡量促销活动的有效性。

## 关键绩效指标

以下KPI有助于衡量受众协作实施是否成功。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 受众重叠率 | 共享区段中发件人和接收者之间匹配的配置文件百分比 | [!DNL Segment Match]重叠估计报告 |
| 匹配的受众规模 | 成功匹配并可供激活的配置文件数 | [!DNL Segment Match]共享状态和受众群体计数 |
| 从匹配受众获取新客户 | 通过定位匹配区段的营销活动获得的全新客户 | 使用匹配受众跟踪营销活动的转化 |
| 客户购置成本降低 | 使用匹配受众与广泛定位时，降低每次购置成本 | 比较匹配受众与不匹配受众性能的促销活动成本分析 |
| 禁止显示节省 | 通过抑制客户获取促销活动中的已知客户来节省媒体支出 | 前/后抑制媒体支出比较 |
| 营销活动效果提升 | 提高了使用匹配受众的营销活动的转化率、点进率或参与度 | A/B测试比较匹配的受众营销活动与控制 |
| 访问Collaboration的时间 | 从区段共享启动到激活准备状态所经过的时间 | [!DNL Segment Match]工作流时间戳 |

## 应用程序

在此用例模式中使用以下应用程序。

- **[!DNL Real-Time CDP]** — 提供[!DNL Segment Match]功能以进行隐私安全的受众共享、针对区段创建的受众评估以及针对匹配受众下游使用的目标激活。
- **[!DNL Adobe Experience Platform]** — 提供[!DNL Segment Match]所依赖的基础数据基础架构，包括身份解析、配置文件统一、数据管理和同意执行。

## 相关文档

以下资源提供了有关此用例模式中所用功能的更多详细信息。

### [!DNL Segment Match]

- [区段匹配概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/segment-match/overview)
- [区段匹配疑难解答](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### 分段和受众

- [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/segment-builder)
- [受众构成概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language参考](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/pql/overview)
- [流式客户细分](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/edge-segmentation)

### 身份和配置文件

- [Identity服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [合并策略概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/merge-policies/overview)
- [Real-time Customer Profile概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/home)

### 数据治理和同意

- [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [策略实施](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/enforcement/overview)
- [同意和偏好设置](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [同意和偏好设置字段组](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/field-groups/profile/consents)

### 目标和激活

- [目的地概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/home)
- [目标目录](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/overview)
- [监测目标的数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/dataflows/ui/monitor-destinations)

### 数据建模和模式

- [XDM系统概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/schema/composition)

### 管理和访问控制

- [访问控制概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/access-control/home)
- [沙盒概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/home)

### 监控和可观察性

- [警报概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/alerts/overview)
- [可观察性分析概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/home)

### 护栏

- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)
- [分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [激活护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/guardrails)

### 教程

- [创建架构](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [为配置文件启用数据集](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/catalog/datasets/enable-for-profile)
