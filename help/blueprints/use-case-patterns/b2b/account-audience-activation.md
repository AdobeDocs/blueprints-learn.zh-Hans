---
title: B2B Audience Activation
description: 了解如何跨Web、电子邮件和广告渠道激活基于帐户的B2B受众。
solution: Real-Time Customer Data Platform
exl-id: 2b979159-37aa-41d4-a6b4-1105538f6546
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1540'
ht-degree: 2%

---

# B2B受众激活

本指南介绍B2B Audience Activation用例模式，该模式使用[!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition在Web、电子邮件、广告和CRM渠道中构建、评估和激活帐户级别的受众。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

此模式涵盖了从统一帐户配置文件到进行受众评估和激活再到特定于B2B的目标（如[!DNL Marketo Engage]、[!DNL LinkedIn]和CRM系统）的整个生命周期。

## 用例模式

**B2B受众激活**

跨Web、电子邮件和广告渠道激活基于帐户的B2B受众。

**执行计划：**&#x200B;帐户配置文件扩充>帐户受众评估>目标配置> Audience Activation >监控

## 用例概述

B2B营销团队需要在帐户级别（而不是个人级别）定位和激活受众。 与B2C受众激活不同（B2C受众激活的定位单位是单个消费者个人资料），B2B受众激活需要了解人员和他们所属的帐户之间的关系，根据帐户级别属性并结合人员级别参与信号来评估受众成员资格，并将这些受众交付到支持基于帐户的定位的目标。

[!DNL RT-CDP] B2B edition通过专门用于帐户、商机和促销活动的XDM类以及映射人员与帐户关系的B2B身份解析来扩展标准[!DNL Real-Time Customer Data Platform]。 这使营销人员能够构建帐户受众，这些受众将来自与这些帐户关联的人员的行业数据（行业、收入、员工人数）、技术数据（技术栈栈、产品使用情况）和行为数据（Web访问次数、电子邮件参与度、事件出席率）组合在一起。

激活的帐户受众在需求挖掘funnel中的强大用例：在[!DNL LinkedIn]和展示广告上开展funnel最热门的宣传运动，[!DNL Marketo Engage]中的funnel中培养计划，以及通过CRM集成实现底部funnel销售支持。 客户抑制受众通过排除现有客户、已结束的丢失的帐户或已在活跃销售周期中的帐户来防止浪费支出。

>[!NOTE]
>如果您的用例涉及在人员级别(B2C)而不是帐户级别激活受众，请参阅[目标受众激活](../audience-building-activation/audience-activation-to-destinations.md)。 该模式使用标准RT-CDP数据模型，不需要B2B edition。

## 主要业务目标

此用例模式支持以下业务目标。

### 增加商机开发

通过表单、事件、内容和多渠道参与，为销售渠道生成更多符合条件的潜在客户。

**KPI：**&#x200B;潜在客户、每个潜在客户的成本、潜在客户转化

[了解有关提高商机开发率的更多信息](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### 改进潜在客户资格鉴定和转化

通过评分、培养和个性化的跟进，提高销售线索质量并加快管道进度。

**KPI：**&#x200B;潜在客户转化、潜在客户/潜在客户转化、效率

[了解有关改进潜在客户资格和转化的更多信息](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### 获取新客户

通过有针对性的客户获取促销活动、相似受众和付费媒体优化来扩展客户群。

**KPI：**&#x200B;新客户、客户获取成本、潜在客户/潜在客户转化

[了解有关获取新客户的更多信息](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### 优化营销支出和ROI

通过更好的定位、归因、受众抑制和预算分配提高营销投资回报。

**KPI：**&#x200B;成本节约、客户获取成本、递增收入

[了解有关优化营销支出和ROI的更多信息](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## 战术用例示例

以下场景说明了如何将此模式应用于实践。

- **在[!DNL LinkedIn]**&#x200B;上基于帐户的广告 — 使用从[!DNL RT-CDP] B2B edition激活的帐户列表，在[!DNL LinkedIn]上定位与您理想的客户个人资料(ICP)和赞助内容以及InMail促销活动相匹配的帐户
- **[!DNL Marketo Engage]Nurture计划目标** — 将帐户受众激活到[!DNL Marketo Engage]，以根据帐户级别的资格条件将关联的潜在客户和联系人注册到目标的Nurture流中
- **CRM帐户列表同步** — 将符合条件的帐户列表推送到[!DNL Salesforce]或[!DNL Microsoft Dynamics]，以查看销售团队的可见性、区域分配和出站潜在客户工作流
- **针对付费媒体的帐户抑制** — 从付费客户获取营销活动中禁止现有客户、赢取已结帐的帐户或处于活跃销售周期的帐户，以减少浪费的支出
- **基于意图的帐户定位** — 在帐户级别将第三方意图信号与第一方参与数据相结合，以识别和激活市场内帐户的受众
- **与现有客户进行产品交叉销售** — 使用一个产品系列而不是另一个产品系列构建客户受众，然后激活到电子邮件和广告渠道以进行交叉销售促销活动
- **活动和网络研讨会定位** — 将帐户受众激活到广告和电子邮件渠道，以从目标帐户进行事件注册
- **竞争替换促销活动** — 使用通过广告和电子邮件渠道激活定制消息传递的竞争对手产品的目标客户
- **分层客户参与** — 根据聚合的人员级别活动将客户划分到参与层（高、中、低），并为每个层激活差异化促销活动
- **合作伙伴联合营销受众** — 通过云存储目标与渠道合作伙伴或联合营销计划共享帐户受众区段

## 关键绩效指标

以下KPI可帮助衡量此用例模式是否成功。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 帐户范围 | 通过激活渠道访问的目标帐户数量 | 跟踪每个目标激活的唯一帐户 |
| 帐户参与率 | 显示参与信号的已激活帐户的百分比 | 衡量汇总到帐户的人员级别参与度 |
| 管道影响 | 归因于基于帐户的激活活动的收入管道 | 跟踪从激活的帐户受众创建的机会 |
| 每个参与帐户的成本 | 营销支出除以显示参与度的帐户数 | 跨广告和电子邮件渠道成本计算 |
| 潜在客户转化率 | 已激活帐户中转换为业务机会的潜在客户百分比 | 跟踪已激活受众的销售线索到业务机会的转化 |
| 受众抑制节省 | 通过从付费营销活动中取消不符合条件的帐户来节省成本 | 从抑制受众中衡量支出减少情况 |
| 帐户覆盖范围 | 激活的受众覆盖的可寻址市场(TAM)总数的百分比 | 将激活的帐户与总ICP世界进行比较 |

## 应用程序

以下应用程序用于实现此用例模式。

- **[!DNL Real-Time CDP]B2B edition** — 用于统一帐户配置文件、B2B身份解析、帐户受众评估、特定于B2B的目标配置和帐户受众激活的核心平台
- **[!DNL Adobe Experience Platform] (AEP)** — 用于B2B XDM数据建模、从CRM和营销自动化源摄取数据、标识服务和治理的基础基础架构
- **[!DNL Marketo Engage]** — 由激活的帐户受众提供的潜在客户培养计划、评分和营销活动执行的主要B2B营销自动化目标

## 相关文档

以下资源为此用例模式中使用的功能提供了其他上下文和详细指导。

**[!DNL RT-CDP]B2B edition**

- [Real-Time CDP B2B edition概述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [Real-Time CDP中的B2B架构](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/rtcdp/schemas/b2b)
- [帐户受众](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/types/account-audiences)
- [RT-CDP B2B edition产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

**受众评估和分段**

- [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [受众构成](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/audience-composition)
- [流式客户细分](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [分段护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)

**目标和激活**

- [目的地概述](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [目标目录](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [LinkedIn匹配受众目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)
- [Amazon S3目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [将受众激活到流目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [将受众激活到批处理目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [激活护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/guardrails)

**数据源和连接器**

- [来源概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/home)
- [Marketo Engage连接器](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce连接器](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/connectors/crm/salesforce)

**数据建模和标识**

- [XDM系统概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/home)
- [Identity服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home)
- [配置文件概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/home)
- [合并策略概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/merge-policies/overview)

**数据治理和隐私**

- [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [同意和偏好设置](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**监视和可观察性**

- [警报概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/observability/alerts/overview)
- [监视目标数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/dataflows/ui/monitor-destinations)
- [监测源数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/api-tutorials/monitor)
- [许可证用量仪表板](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Reporting &amp; Analytics**

- [CJA概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-overview/cja-overview)
- [连接概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-connections/overview)
- [数据视图概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-dataviews/data-views)

**教程和指南**

- [Real-Time CDP B2B edition快速入门](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro)
- [为B2B源创建架构](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/rtcdp/schemas/b2b)
- [沙盒工具](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sandbox/sandbox-tooling-api/overview)
