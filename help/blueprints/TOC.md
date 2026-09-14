---
user-guide-title: 客户体验编排业务目标、用例、体系结构图和Blueprint
breadcrumb-title: 用例和Blueprint
user-guide-description: 探索Adobe Experience Platform和应用程序的关键业务目标、用例模式以及行业用例。 可视化架构图和Blueprint为系统集成、数据流和解决方案设计提供了技术参考 — 将业务价值与实施联系起来。
product: Adobe Experience Platform
mini-toc-levels: 3
role: Developer, User
nudge: orange
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '1169'
ht-degree: 15%
---

# 客户体验编排Blueprint {#architecture}

+ [客户体验编排Blueprint](/help/blueprints/overview.md)
+ AEP与应用程序的主要业务目标{#business-objectives}
  + [概述](/help/blueprints/business-objectives/overview.md)
  + 收购与增长{#acquisition-growth}
    + [获取新客户](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)
    + [增加商机开发](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)
    + [提高网站参与度](/help/blueprints/business-objectives/acquisition-growth/increase-website-engagement.md)
  + 收入和盈利{#revenue-monetization}
    + [提高转化率](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)
    + [增加收入和销售](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)
    + [提高交叉销售和追加销售收入](/help/blueprints/business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)
    + [提高客户忠诚度和存留期值](/help/blueprints/business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)
  + 成本和效率{#cost-efficiency}
    + [降低客户购置成本](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)
    + [优化营销支出和ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)
    + [提高数据质量和改善管理](/help/blueprints/business-objectives/cost-efficiency/improve-data-quality-governance.md)
    + [整合营销技术并使其现代化](/help/blueprints/business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md)
  + 客户体验{#customer-experience-objectives}
    + [提供个性化的客户体验](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)
    + [提高客户保留率](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)
    + [改进客户入门](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)
    + [恢复放弃的购物车和历程](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)
  + Analytics &amp; Insights{#analytics-insights}
    + [改进分析和报告](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)
    + [启用数据驱动型决策](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)
    + [改进营销归因](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md)
  + 资格鉴定和销售(B2B){#qualification-sales-b2b}
    + [改进潜在客户资格鉴定和转化](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)
    + [提高客户参与度](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)
+ 用例模式{#use-case-patterns}
  + [概述](/help/blueprints/use-case-patterns/overview.md)
  + Audience Building &amp; Activation{#audience-building-activation}
    + [Audience Activation到目标](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md)
    + [具有区段匹配的受众Collaboration](/help/blueprints/use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md)
    + [事件转发](/help/blueprints/use-case-patterns/audience-building-activation/event-forwarding.md)
    + [支持和销售人员的实时配置文件查找](/help/blueprints/use-case-patterns/audience-building-activation/real-time-profile-lookup.md)
    + [用于扩充用户档案的自定义数据科学](/help/blueprints/use-case-patterns/audience-building-activation/data-science-profile-enrichment.md)
  + 个性化{#personalization-patterns}
    + [匿名访客Web Personalization](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md)
    + [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)
    + [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)
    + [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)
    + [用于Web/移动Personalization的Edge配置文件访问](/help/blueprints/use-case-patterns/personalization/edge-profile-access.md)
    + [与Adobe Target共享受众](/help/blueprints/use-case-patterns/personalization/audience-sharing-with-target.md)
  + 营销活动管理和编排{#campaign-orchestration-patterns}
    + [批量出站消息激活](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md)
    + [事件触发的消息传递](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)
    + [多步协调历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)
    + [使用Decisioning进行跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
    + [Campaign v8批量编排和事务性消息传递](/help/blueprints/use-case-patterns/campaign-management-orchestration/campaign-v8-orchestration.md)
    + [第三方消息传递与Journey Optimizer的集成](/help/blueprints/use-case-patterns/campaign-management-orchestration/third-party-messaging.md)
  + 分析{#analysis-patterns}
    + [Customer Analytics和Insight生成](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md)
  + B2B 激活与营销{#b2b-patterns}
    + [B2B Audience Activation](/help/blueprints/use-case-patterns/b2b/account-audience-activation.md)
    + [购买基于群组的营销和历程管理](/help/blueprints/use-case-patterns/b2b/buying-group-marketing.md)
    + [B2B分析](/help/blueprints/use-case-patterns/b2b/account-analytics.md)
    + [使用Marketo数据的B2B历程](/help/blueprints/use-case-patterns/b2b/marketo-data-journeys.md)
    + [AJO B2B付费媒体控制器](/help/blueprints/use-case-patterns/b2b/paid-media-orchestration.md)
    + [Marketo和Workfront摄取和创建](/help/blueprints/use-case-patterns/b2b/campaign-intake-and-creation.md)
    + [Marketo和Workfront审阅和批准](/help/blueprints/use-case-patterns/b2b/campaign-review-and-approval.md)
  + 对话体验{#conversational-experience-patterns}
    + [Brand Concierge对话体验](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md)
+ 行业用例示例{#industry-use-cases}
  + [用例目录](/help/blueprints/industry-use-cases/use-case-catalog.md)
  + [汽车](/help/blueprints/industry-use-cases/automotive/automotive-overview.md)
  + [B2B](/help/blueprints/industry-use-cases/b2b/b2b-overview.md)
  + [金融服务](/help/blueprints/industry-use-cases/financial-services/financial-services-overview.md)
  + [医疗保健](/help/blueprints/industry-use-cases/healthcare/healthcare-overview.md)
  + [保险](/help/blueprints/industry-use-cases/insurance/insurance-overview.md)
  + [媒体和娱乐](/help/blueprints/industry-use-cases/media-entertainment/media-entertainment-overview.md)
  + [零售](/help/blueprints/industry-use-cases/retail/retail-overview.md)
  + [电信](/help/blueprints/industry-use-cases/telecommunications/telecommunications-overview.md)
  + [技术](/help/blueprints/industry-use-cases/technology/technology-overview.md)
  + [旅游和酒店业](/help/blueprints/industry-use-cases/travel-hospitality/travel-hospitality-overview.md)
+ 架构图和Blueprint{#architecture-diagrams}
  + 架构概述{#architecture-overview}
    + [Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
    + [Experience Platform与应用程序](/help/blueprints/experience-platform/platform-applications.md)
    + [Experience Platform数据流](/help/blueprints/experience-platform/platform-data-flow.md)
    + [Experience Platform护栏](/help/blueprints/experience-platform/guardrails.md)
    + 部署{#deployment}
      + [Experience Platform Web SDK &amp; [!DNL Edge Network]](/help/blueprints/experience-platform/deployment/websdk.md)
      + [应用程序 SDK](/help/blueprints/experience-platform/deployment/appsdk.md)
  + 受众和用户档案激活{#audience-activation}
    + [Device Based — 使用Audience Manager进行匿名受众定位](/help/blueprints/audience-activation/audience-manager.md)
    + Real-Time Customer Data Platform (RTCDP) {#known-customer-audience-activation}
      + [Audience Activation到社交和广告目标](/help/blueprints/audience-activation/advertising-activation.md)
      + [将受众和配置文件激活到企业目标Blueprint](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [支持与销售方案的实时配置文件访问](/help/blueprints/audience-activation/customer-activity.md)
      + [用于Web和移动个性化的实时边缘配置文件访问](/help/blueprints/audience-activation/real-time-lookup.md)
      + [使用区段匹配进行受众协作](/help/blueprints/audience-activation/segment-match.md)
      + [使用Target实现已知的客户个性化](/help/blueprints/audience-activation/rtcdp-target.md)
      + [用于扩充用户档案的自定义数据科学](/help/blueprints/audience-activation/data-science.md)
  + B2B激活和营销{#b2b-activation}
    + [概述](/help/blueprints/b2b/overview.md)
    + [B2B激活](/help/blueprints/b2b/b2bactivation.md)
    + [B2B帐户激活](/help/blueprints/b2b/b2b-account-activation.md)
    + [购买基于群组的营销和历程管理](/help/blueprints/b2b/b2b-buying-group-journeys.md)
    + [使用Marketo数据的B2B历程](/help/blueprints/b2b/b2b-journeys-with-marketo.md)
    + [B2B付费媒体控制器](/help/blueprints/b2b/ajo-b2b-paid-media-controller.md)
    + Marketo Engage和Workfront集成Blueprint{#marketo-engage-and-workfront-integration-blueprint}
      + [概述](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md)
      + [摄取和创建](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md)
      + [审阅并批准](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md)
      + [客户成功案例](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md)
  + Customer Journey Analytics{#customer-journey-analytics}
    + [概述](/help/blueprints/customer-journey-analytics/overview.md)
    + [B2B Customer Journey Analytics](/help/blueprints/customer-journey-analytics/b2b-cja.md)
    + [将CJA受众共享到RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
    + [CJA 和 Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
    + [数据分析和智能](/help/blueprints/customer-journey-analytics/analysis.md)
  + 客户历程{#customer-journeys}
    + [概述](/help/blueprints/customer-journeys/overview.md)
    + Journey Optimizer{#journey-optimizer}
      + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md)
      + [AJO历程](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md)
      + [AJO营销活动](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md)
      + [第三方报文传送](/help/blueprints/customer-journeys/journey-optimizer/3rd-party-messaging.md)
    + 决策管理{#decision-management}
      + [概述](/help/blueprints/customer-journeys/decision-management/decision-management-overview.md)
      + [Edge上的决策管理](/help/blueprints/customer-journeys/decision-management/decision-management-edge.md)
      + [中心上的决策管理](/help/blueprints/customer-journeys/decision-management/decision-management-hub.md)
    + Campaign v8{#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8/campaign-v8-overview.md)
      + [Real-Time CDP与Adobe [!DNL Campaign] v8](/help/blueprints/customer-journeys/campaign-v8/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer 与 Adobe Campaign v8](/help/blueprints/customer-journeys/campaign-v8/ajo-and-campaign-v8.md)
    + 已弃用的Blueprint{#deprecated-blueprints}
      + Campaign Standard{#campaign-standard}
        + [[!DNL Campaign Standard]](https://experienceleague.adobe.com/zh-hans/docs/campaign-standard){target="_blank"}
        + [Real-Time CDP与Adobe [!DNL Campaign Standard]](https://experienceleague.adobe.com/zh-hans/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/get-started-sources-destinations)
      + Campaign v7{#campaign-v7}
        + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md)

+ 动手实验室{#labs}
  + [实验操作概述](/help/blueprints/labs/overview.md)
  + 实践研讨会{#workshops}
    + AEP基础{#aep-foundations}
      + [概述](/help/blueprints/labs/aep-foundations/overview.md)
      + [设置](/help/blueprints/labs/aep-foundations/setup.md)
      + 沙盒设置{#aep-sandbox}
        + [Developer Console设置](/help/blueprints/labs/aep-foundations/sandbox-setup/developer-console-setup.md)
        + [部署说明](/help/blueprints/labs/aep-foundations/sandbox-setup/deployment-instructions.md)
      + Postman设置{#aep-postman}
        + [Postman安装](/help/blueprints/labs/aep-foundations/postman-setup/postman-installation.md)
        + [环境文件](/help/blueprints/labs/aep-foundations/postman-setup/environment-file.md)
        + [API收藏集](/help/blueprints/labs/aep-foundations/postman-setup/api-collection.md)
        + [沙盒访问](/help/blueprints/labs/aep-foundations/postman-setup/sandbox-access.md)
        + [访问令牌](/help/blueprints/labs/aep-foundations/postman-setup/access-token.md)
      + Real-time Customer Profile{#aep-rtcp}
        + [讲座](/help/blueprints/labs/aep-foundations/real-time-customer-profile/lectures.md)
        + 检查用户档案{#aep-rtcp-inspect}
          + [概述](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/overview.md)
          + [配置文件基础知识](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/profile-basics.md)
          + [合并政策](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/merge-policies.md)
          + [配置文件和标识API](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/profile-and-identity-apis.md)
      + LID方法{#aep-lid}
        + [先决条件](/help/blueprints/labs/aep-foundations/lid-methodology/prerequisites.md)
        + [标签](/help/blueprints/labs/aep-foundations/lid-methodology/label.md)
        + 识别{#aep-lid-identify}
          + [概述](/help/blueprints/labs/aep-foundations/lid-methodology/identify/overview.md)
          + [第1部分 — 剩余表类型](/help/blueprints/labs/aep-foundations/lid-methodology/identify/part-1-remaining-table-types.md)
          + [第2部分 — 关键字段](/help/blueprints/labs/aep-foundations/lid-methodology/identify/part-2-key-fields.md)
        + [反规范化](/help/blueprints/labs/aep-foundations/lid-methodology/denormalize.md)
      + XDM建模{#aep-xdm}
        + [讲座](/help/blueprints/labs/aep-foundations/xdm-modeling/lectures.md)
        + UI建模{#aep-xdm-ui}
          + [概述](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/overview.md)
          + [登录和浏览](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/login-and-browse.md)
          + [模型标准对象](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/model-standard-objects.md)
          + [为自定义对象建模](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/model-custom-objects.md)
          + [为配置文件配置](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/configure-for-profile.md)
        + API建模{#aep-xdm-api}
          + [概述](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/overview.md)
          + 构建架构{#aep-xdm-api-build}
            + [概述](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/overview.md)
            + [获取标准字段组](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/get-standard-field-groups.md)
            + [创建自定义字段组](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/create-custom-field-groups.md)
            + [获取配置文件类](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/get-profile-class.md)
            + [创建架构](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/create-schema.md)
            + [查看架构](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/view-schema.md)
            + [修改架构 — JSON修补程序](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/modify-schema-json-patch.md)
          + 标记标识字段{#aep-xdm-api-identity}
            + [概述](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/overview.md)
            + [创建主要身份](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/create-primary-identity.md)
            + [创建其他标识](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/create-other-identities.md)
            + [查看架构](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/view-schema.md)
          + 定义关系{#aep-xdm-api-relationships}
            + [概述](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/overview.md)
            + [获取计划架构ID](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/get-plan-schema-id.md)
            + [创建架构关系](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/create-schema-relationship.md)
            + [创建计划引用标识](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/create-plan-reference-identity.md)
            + [查看架构](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/view-schema.md)
          + [回顾](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/recap.md)
        + 附加实验室{#aep-xdm-bonus}
          + [使用API实现自动化](/help/blueprints/labs/aep-foundations/xdm-modeling/bonus-labs/automate-with-apis.md)
      + 数据摄取{#aep-ingestion}
        + [讲座](/help/blueprints/labs/aep-foundations/data-ingestion/lectures.md)
        + [实验室概述](/help/blueprints/labs/aep-foundations/data-ingestion/lab-overview.md)
        + [示例文件](/help/blueprints/labs/aep-foundations/data-ingestion/sample-files.md)
        + 批量摄取{#aep-ingestion-batch}
          + [概述](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/overview.md)
          + [创建数据流](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/create-dataflow.md)
          + 映射数据{#aep-ingestion-batch-mapping}
            + [概述](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/overview.md)
            + [修复直通映射](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/fix-passthrough-mappings.md)
            + [计算字段](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/calculated-fields.md)
            + [检查最终映射集](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/check-final-mapping-set.md)
          + [运行数据流](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/run-dataflow.md)
          + [调试错误](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/debugging-errors.md)
          + [创建新数据流](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/create-a-new-dataflow.md)
          + [修复错误](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/fixing-errors.md)
          + [验证和验证](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/verification-and-validation.md)
        + 流摄取{#aep-ingestion-stream}
          + [概述](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/overview.md)
          + [设置Source](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/setup-source.md)
          + [配置映射](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/configure-mapping.md)
          + [检查最终映射集](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/check-final-mapping-set.md)
          + [流式传输配置文件](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/stream-a-profile.md)
          + [验证已摄取的配置文件](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/verify-ingested-profile.md)
          + [监控和调试错误](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/monitoring-and-debugging-errors.md)
          + [验证和验证](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/verification-and-validation.md)
        + 附加实验室{#aep-ingestion-bonus}
          + [修复CreateDate的MAPPER错误](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/fix-mapper-errors-for-createdate.md)
          + [流式传输订单事件](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/stream-an-order-event.md)
          + 使用数据登陆区{#aep-ingestion-dlz}
            + [概述](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/overview.md)
            + [设置Source](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/setup-source.md)
            + [创建映射](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/create-mappings.md)
            + [计划数据流](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/schedule-dataflow.md)
            + [重试失败的数据流](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/retry-a-failed-dataflow.md)
            + 加载订单{#aep-ingestion-dlz-orders}
              + [概述](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/overview.md)
              + [设置Source](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/setup-source.md)
              + [初始映射](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/initial-mappings.md)
              + [对象复制映射](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/object-copy-mappings.md)
              + [验证和计划数据流](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/verify-and-schedule-dataflow.md)
      + 分段和激活{#aep-segmentation}
        + [讲座](/help/blueprints/labs/aep-foundations/segmentation-and-activation/lecture.md)
        + Edge激活{#aep-segmentation-edge}
          + [概述](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/overview.md)
          + [创建Edge受众](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/create-edge-audience.md)
          + [发送Edge事件](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/send-an-edge-event.md)
          + 设置事件转发{#aep-segmentation-edge-ef}
            + [概述](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/overview.md)
            + [创建属性](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/create-property.md)
            + [创建数据流](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/create-datastream.md)
      + 受众构建{#aep-audiences}
        + 用例1 — 客户获取{#aep-uc1}
          + [概述](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/overview.md)
          + 配置目标{#aep-uc1-destinations}
            + [设置自定义Personalization目标](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/configure-destinations/setup-custom-personalization-destination.md)
            + [设置流目标](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/configure-destinations/setup-streaming-destination.md)
          + [构建受众1](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-1.md)
          + [构建受众2](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-2.md)
          + [构建受众3](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-3.md)
          + [发送Edge事件](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/send-an-edge-event.md)
          + [批判性思维评论](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/critical-thinking-review.md)
        + 用例2 — 追加销售{#aep-uc2}
          + [概述](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/overview.md)
          + [前期工作](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/pre-work.md)
          + [选项1 — 使用受众进行聚合](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/option-1-using-audiences-to-aggregate.md)
          + [选项2 — 使用预聚合](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/option-2-use-pre-aggregates.md)
          + [批判性思维评论](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/critical-thinking-review.md)
        + 用例3 — 外联{#aep-uc3}
          + [概述](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/overview.md)
          + [构建用例3](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/build-use-case-3.md)
          + [批判性思维评论](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/critical-thinking-review.md)
        + 附加实验室{#aep-audiences-bonus}
          + [将订单事件发送到中心](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/send-order-event-to-hub.md)
          + [将Web事件发送到中心](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/send-web-event-to-hub.md)
          + [监控您的事件](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/monitor-your-event.md)
    + AJO基础{#ajo-foundations}
      + [概述](/help/blueprints/labs/ajo-foundations/overview.md)
      + [设置](/help/blueprints/labs/ajo-foundations/setup.md)
      + 沙盒设置{#ajo-sandbox}
        + [Developer Console设置](/help/blueprints/labs/ajo-foundations/sandbox-setup/developer-console-setup.md)
        + [部署说明](/help/blueprints/labs/ajo-foundations/sandbox-setup/deployment-instructions.md)
      + Postman设置{#ajo-postman}
        + [Postman安装](/help/blueprints/labs/ajo-foundations/postman-setup/postman-installation.md)
        + [导入环境文件](/help/blueprints/labs/ajo-foundations/postman-setup/import-environment-file.md)
        + [导入API收藏集](/help/blueprints/labs/ajo-foundations/postman-setup/import-api-collection.md)
      + 架构构建基块{#ajo-architecture}
        + [讲座](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/lecture.md)
        + 将用例映射到架构{#ajo-architecture-mapping}
          + [概述](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/overview.md)
          + [实验室简介](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-introduction.md)
          + [实验室练习](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-exercise.md)
          + [实验室审查](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-review.md)
      + 数据存储{#ajo-data-stores}
        + [实时客户资料讲座](/help/blueprints/labs/ajo-foundations/data-stores/real-time-customer-profile-lecture.md)
        + 正在运行的配置文件{#ajo-profile}
          + [概述](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/overview.md)
          + [登录和浏览](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/login-and-browse.md)
          + [创建数据流](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/create-datastream.md)
          + [发送Edge Web事件](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/send-an-edge-web-event.md)
          + [验证中心上的配置文件](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-on-hub.md)
          + [在Edge上验证配置文件](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-on-edge.md)
          + [验证数据湖上的事件](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-event-on-data-lake.md)
          + [验证配置文件快照](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-snapshot.md)
          + [摘要](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/summary.md)
        + [关系存储讲座](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-lecture.md)
        + 正在运行的关系存储{#ajo-relational}
          + [概述](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/overview.md)
          + [浏览架构](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/browse-schemas.md)
          + [配置文件Target Dimension](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/profile-target-dimension.md)
          + [读取受众](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/read-an-audience.md)
          + [摘要](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/summary.md)
        + 配置电子邮件渠道{#ajo-email}
          + [概述](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/overview.md)
          + [为配置文件配置](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/configure-for-profile.md)
          + [为关系配置](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/configure-for-relational.md)
          + [等待活动状态](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/waiting-for-active-status.md)
      + 编排的营销活动{#ajo-campaigns}
        + [消息投放讲座](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-lecture.md)
        + 消息投放的实际操作{#ajo-campaigns-delivery}
          + [概述](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/overview.md)
          + [创建一个营销活动](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/create-a-campaign.md)
          + [构建受众](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/build-an-audience.md)
          + [添加分支活动](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/add-fork-activity.md)
          + [添加电子邮件活动](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/add-email-activities.md)
          + [测试活动](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/test-the-campaign.md)
          + [摘要](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/summary.md)
        + [工作流构建块讲座](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/workflow-building-blocks-lecture.md)
        + 旗舰手机发布{#ajo-campaigns-flagship}
          + [概述](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/overview.md)
          + [配置短信渠道](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/configure-sms-channel.md)
          + [创建编排的营销活动](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/create-an-orchestrated-campaign.md)
          + [构建受众](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/build-an-audience.md)
          + [创建结果分支](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/fork-the-result.md)
          + [保存受众](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/save-the-audience.md)
          + [筛选线条](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/filter-the-lines.md)
          + [撰写短信](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/compose-the-sms.md)
          + [运行工作流](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/run-the-workflow.md)
          + [摘要](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/summary.md)
      + 历程{#ajo-journeys}
        + [讲座](/help/blueprints/labs/ajo-foundations/journeys/lecture.md)
        + 购买后兴奋{#ajo-journeys-post-purchase}
          + [概述](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/overview.md)
          + [配置事件](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/configure-event.md)
          + [配置自定义操作](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/configure-custom-action.md)
          + [构建历程](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/build-journey.md)
          + [测试历程](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/test-journey.md)
          + [发送事件](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/send-an-event.md)
          + [验证已摄取的事件](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/validate-event-ingested.md)
          + [验证历程](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/validate-journey.md)
          + [摘要](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/summary.md)
      + Decisioning{#ajo-decisioning}
        + [体验Edge](/help/blueprints/labs/ajo-foundations/decisioning/experience-edge.md)
        + 决策解释{#ajo-decisioning-explained}
          + [概述](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/overview.md)
          + [简介](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/introduction.md)
          + [决策项XDM](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-item-xdm.md)
          + [决策项创建](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-item-creation.md)
          + [集合](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/collections.md)
          + [排名公式](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/ranking-formulas.md)
          + [选择策略](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/selection-strategies.md)
          + [决策策略](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-policies.md)
          + [护栏、AI模型决定未来](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/guardrails-ai-models-decisioning-future.md)
        + 已放弃的浏览{#ajo-decisioning-abandoned}
          + [概述](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/overview.md)
          + [创建决策规则](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-decision-rule.md)
          + [创建优惠属性](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-attributes.md)
          + [创建选件项目](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-items.md)
          + [创建优惠收藏集](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-collection.md)
          + [创建排名公式](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-ranking-formula.md)
          + [创建选择策略](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-selection-strategy.md)
          + [创建基于代码的体验渠道](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-code-based-experience-channel.md)
          + [创建历程](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-the-journey.md)
          + [决策和CBE的实际操作](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/decisioning-and-cbes-in-action.md)
          + [摘要](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/summary.md)
      + 使用AI创作内容{#ajo-content-ai}
        + [讲座](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/lecture.md)
        + [概述](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/overview.md)
        + [品牌管理](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/brand-management.md)
        + [构建内容片段](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/building-content-fragments.md)
        + [构建内容模板](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/building-content-template.md)
        + [创建电子邮件](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/creating-the-email.md)
        + [AI助手和内容Personalization](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/ai-assistant-and-content-personalization.md)
        + [Personalization和内容试验](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/personalization-and-content-experimentation.md)
        + [内容模拟](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/content-simulation.md)
        + [品牌整合](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/brand-alignment.md)
        + [测试电子邮件](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/test-the-email.md)
        + [概要](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/summary.md)
