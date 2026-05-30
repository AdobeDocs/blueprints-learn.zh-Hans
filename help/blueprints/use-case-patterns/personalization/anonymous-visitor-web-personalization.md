---
title: 匿名访客Web Personalization
description: 了解如何根据会话中行为信号向未识别的访客提供个性化的Web内容。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: e2446801-ffce-40e6-bfe9-abec623c9201
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 4%

---

# 匿名访客Web个性化

本指南介绍了匿名访客Web个性化用例模式，该模式使用[!DNL Adobe Journey Optimizer] (AJO)、[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)和[!DNL Adobe Experience Platform] (AEP)根据会话内行为信号向匿名（未识别）访客提供个性化Web内容。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

模式只对有限的数据起作用 — 只有可以在当前会话中观察到的内容，以及以前使用同一设备或Cookie访问累积的任何匿名边缘配置文件。 这使得它适用于funnel顶部个性化，即访客没有帐户或没有进行身份验证。

## 用例模式

下面描述了此用例的核心模式和执行计划。

**匿名访客Web Personalization**

通过AJO Web渠道，根据会话中行为信号为未识别的访客提供个性化内容。

**执行计划：** Web表面配置>行为规则评估>内容交付>展示跟踪>报告

## 用例概述

匿名访客Web Personalization满足了向尚未识别身份的网站访客提供相关、个性化内容的业务需求，这些访客尚未登录，没有已知的身份，并且无法解析为统一的客户个人资料。 尽管存在此限制，但可以使用会话中行为信号来实现有意义的个性化：页面查看次数、网站逗留时间、滚动深度、反向链接来源、地理位置、设备类型和UTM促销活动参数。

此模式使用AJO的Web渠道表面和基于代码的体验来实时修改页面内容。 Edge分段是主要的评估方法，因为当访客导航网站时，必须在不到一秒钟的延迟内做出决策。 [!DNL Web SDK]收集行为信号并将它们发送到[!DNL AEP Edge Network]，边缘评估的受众规则将决定要投放的内容变体。

与利用完整的统一配置文件和区段成员资格的已知访客Web/应用程序个性化不同，此模式受当前会话中可观察的数据以及与访客的ECID ([!DNL Experience Cloud ID])关联的任何匿名边缘配置文件的限制。 这种区分对于实施规划至关重要：可用于个性化的行为信号仅限于[!DNL Web SDK]捕获的内容以及通过基于Cookie的ECID跨会话保留在边缘配置文件存储中的内容。

## 主要业务目标

此用例模式支持以下业务目标。

**[提高网站参与度](../../business-objectives/acquisition-growth/increase-website-engagement.md)**

通过针对匿名访客信号量身定制的相关体验，缩短网站访问时间、每次会话页面数以及与网络内容的交互。

| KPI |
| --- |
| Time On (Web)页 |
| 参与度 |
| 转化率 |

**[提供个性化的客户体验](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

根据个人的偏好、行为和生命周期阶段定制内容、选件和消息 — 即使对于尚未标识自己的访客。

| KPI |
| --- |
| 参与度 |
| 转化率 |
| 客户满意度(CSAT) |

**[提高转化率](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

通过根据行为上下文提供最相关的内容，提高完成所需操作（如购买、注册或表单提交）的访客和潜在客户的百分比。

| KPI |
| --- |
| 转化率 |
| 商机转换 |
| 每个潜在客户的成本 |

## 战术用例示例

以下示例说明了可应用此模式的特定场景。

- **基于反向链接源的登陆页面标题A/B测试** — 对来自Google、社交媒体或直接流量的访客测试不同的标题，以通过客户获取渠道优化参与
- **基于浏览行为的类别亲和度推荐** — 根据当前会话中查看的页面显示产品或内容推荐，以提高发现和转化
- **即将离开的访客的退出意向选件** — 当行为信号指示访客即将放弃网站时，提供促销选件或潜在客户捕获表单
- **地理定位促销横幅** — 根据访客的地理位置显示特定于位置的促销活动、商店定位器内容或区域选件
- **特定于设备的内容布局优化** — 根据访客使用的是台式机、平板电脑还是移动设备，调整内容布局、图像大小和CTA版面
- **新访客与回访访客的欢迎消息** — 区分首次访客与使用ECID跨会话持久性的回访匿名访客的体验
- **基于当前会话中已查看页面的内容推荐** — 根据访客已查看的页面动态显示相关文章、产品或资源
- **基于UTM促销活动参数的动态主页横幅** — 个性化主页横幅以匹配引用促销活动的消息传递或创意

## 关键绩效指标

使用以下KPI衡量此用例模式的有效性。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| Personalization展示率 | 投放了个性化内容的符合条件的页面查看次数的百分比 | AJO促销活动报表：展示次数/页面查看总数 |
| 点进率(CTR) | 导致点击的个性化内容展示的百分比 | AJO促销活动报表：点击次数/展示次数 |
| 参与度提升 | 增加个性化内容与默认内容的页面时间、每会话页面数或滚动深度 | CJA工作区比较：个性化同类群组与控制 |
| 转化率 | 向个性化内容公开并完成所需操作的访客百分比 | CJA funnel analysis：展示>互动>转化 |
| 跳出率降低 | 减少接收个性化内容的访客的单页会话 | CJA会话分析：个性化与默认跳出率差异 |
| 试验成功率 | 产生具有统计意义的入选者的A/B测试的百分比 | AJO实验报告：实验达到置信阈值 |

## 应用程序

在此用例模式中使用以下应用程序。

- **[!DNL Adobe Journey Optimizer] (AJO)** — Web渠道表面配置、内容创作（基于Web和代码的体验）、活动执行、内容试验（A/B测试）、决策（动态内容选择）和报表
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 基于会话中行为信号的实时受众评估的Edge分段；匿名边缘配置文件管理
- **[!DNL Adobe Experience Platform] (AEP)** — [!DNL Web SDK]用于行为信号收集，[!DNL Edge Network]用于实时数据路由和个性化投放，数据流配置

## 架构

以下参考架构说明了如何在边缘收集匿名访客信号、根据受众规则评估并使用这些信号提供个性化内容。

![匿名受众激活和个性化的参考架构](/help/blueprints/audience-activation/assets/anonymous_activation.png)

## 相关文档

以下Experience League资源提供了有关此用例模式中所用功能的更多详细信息。

**Web渠道体验和基于代码的体验**

- [Web渠道入门](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/web/get-started-web)
- [创建Web体验](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/web/create-web)
- [基于代码的体验渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [基于代码的体验配置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

**受众和分段**

- [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/segment-builder)
- [边缘分段](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/edge-segmentation)
- [流式客户细分](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language参考](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/pql/overview)

**Personalization和内容**

- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

**内容试验**

- [内容体验入门](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [内容试验报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [统计计算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

**决策管理**

- [决策管理概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [创建投放位置](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [创建决策规则](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [创建个性化优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [创建后备产品建议](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [创建集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [创建决策](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [在消息中投放优惠](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

**营销活动**

- [开始使用营销活动](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

**[!DNL Web SDK]和数据收集**

- [Web SDK概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/web-sdk/home)
- [安装Web SDK](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/web-sdk/install/overview)
- [配置数据流](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/datastreams/configure)
- [标记概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/tags/home)

**身份和配置文件**

- [Identity服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [合并策略概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/merge-policies/overview)
- [Real-time Customer Profile概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/home)

**数据建模**

- [XDM系统概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/schema/composition)

**报告和分析**

- [营销活动实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-workspace/home)
- [CJA概述](https://experienceleague.adobe.com/zh-hans/docs/analytics-platform/using/cja-overview/cja-overview)

**数据治理和隐私**

- [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home)
- [高级数据生命周期管理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-lifecycle/home)
- [同意和偏好设置字段组](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/field-groups/profile/consents)

**护栏**

- [Journey Optimizer护栏](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)
- [Identity服务护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/guardrails)
