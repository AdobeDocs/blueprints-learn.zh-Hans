---
title: 用例目录
description: 按垂直方向浏览行业用例，以找到适合您的Adobe Experience Platform历程的起点，并提供指向实施模式和业务目标的链接。
doc-type: overview-page
exl-id: 38593314-b8c9-49f6-85db-a4345ec444e7
source-git-commit: 9d1ba8ce3fed83b1bd2b2615309ae7e3683e14f1
workflow-type: tm+mt
source-wordcount: '2379'
ht-degree: 1%

---

# 用例目录

行业用例展示了特定行业中的公司如何应用Adobe Experience Platform和应用程序来实现可衡量的业务成果。 每个用例描述一个具体的业务场景、其预期影响，以及指向提供详细实施指导的[用例模式](/help/blueprints/use-case-patterns/overview.md)的链接。

按行业浏览以查找与您的组织相关的用例，然后按照模式链接获取实施参考，包括决策指导、功能链和Experience League文档。

| 行业 | 关键主题 |
| --- | --- |
| [汽车](automotive/automotive-overview.md) | 车辆购买历程，服务生命周期，互联车辆体验，车主忠诚度 |
| [B2B](b2b/b2b-overview.md) | 基于帐户的营销、潜在客户评分、管道加速、客户扩展 |
| [金融服务](financial-services/financial-services-overview.md) | 产品推荐、客户流失预防、生命周期选件、欺诈个性化 |
| [医疗保健](healthcare/healthcare-overview.md) | 预约管理、药物遵守、患者入门、护理协调 |
| [保险](insurance/insurance-overview.md) | 政策更新、索赔体验、风险预防、交叉销售优化 |
| [媒体和娱乐](media-entertainment/media-entertainment-overview.md) | 内容推荐、订阅保留、试用转化、跨平台参与 |
| [零售](retail/retail-overview.md) | 产品个性化、购物车恢复、交叉销售优化、忠诚度参与 |
| [电信](telecommunications/telecommunications-overview.md) | 设备升级、防止流失、规划优化、网络参与 |
| [旅游和酒店业](travel-hospitality/travel-hospitality-overview.md) | 预订个性化、放弃恢复、忠诚度计划、季节性活动 |

## 用例如何连接到实施指南

每个用例都链接到&#x200B;**用例模式** — 一种可重复的实施方法，用于描述实现用例所需的功能链、决策点和配置步骤。 用例模式依次与[关键业务目标](/help/blueprints/business-objectives/overview.md)相关联，帮助您使实施工作与战略成果保持一致。

```
Industry Use Case → Use Case Pattern → Key Business Objective
```

## 按行业浏览

>[!BEGINTABS]

>[!TAB 零售]

| | 用例 | 描述 | 成熟度 | 图案 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/retail/icon-abandoned-cart.png" alt="已放弃的购物车" width="40"> | [放弃的购物车电子邮件恢复](retail/retail-overview.md#abandoned-cart-email-recovery) | 为已放弃的购物车发送个性化提醒 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/retail/icon-inventory-urgency.png" alt="库存紧迫性" width="40"> | [基于清单的紧急活动](retail/retail-overview.md#inventory-based-urgency-campaigns) | 产品库存不足时触发实时警报 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/retail/icon-price-drop.png" alt="价格下降" width="40"> | [价格下降警报](retail/retail-overview.md#price-drop-alerts) | 当愿望清单或查看过的商品降价时通知客户 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [缺货通知](retail/retail-overview.md#out-of-stock-notifications) | 在缺货产品可用时通知客户 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/retail/icon-product-recommendations.png" alt="产品推荐" width="40"> | [个性化产品推荐](retail/retail-overview.md#personalized-product-recommendations) | 根据浏览和购买历史记录显示个性化产品 | [!BADGE 新兴]{type=Informative} | [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/retail/icon-category-pages.png" alt="类别页面" width="40"> | [个性化类别页面](retail/retail-overview.md#personalized-category-pages) | 根据客户首选项动态重新排序类别页面 | [!BADGE 新兴]{type=Informative} | [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/retail/icon-welcome-series.png" alt="欢迎系列" width="40"> | [新客户欢迎系列](retail/retail-overview.md#new-customer-welcome-series) | 通过个性化推荐自动执行多电子邮件欢迎系列 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/retail/icon-replenishment.png" alt="补货" width="40"> | [补货提醒](retail/retail-overview.md#replenishment-reminders) | 发送定期购买消耗性产品的自动提醒 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/retail/icon-post-purchase.png" alt="购买后" width="40"> | [购买后跟进活动](retail/retail-overview.md#post-purchase-follow-up-campaigns) | 发送关怀提示、审核请求和相关产品建议 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [社交校对Personalization](retail/retail-overview.md#social-proof-personalization) | 根据客户个人资料显示个性化的评论和评级 | [!BADGE 新兴]{type=Informative} | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/retail/icon-cross-sell-upsell.png" alt="交叉销售追加销售" width="40"> | [交叉销售和追加销售推荐](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | 在结账时和电子邮件中显示相关的交叉销售和追加销售产品 | [!BADGE 高级]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| | [VIP客户独家优惠](retail/retail-overview.md#vip-customer-exclusive-offers) | 提供独家优惠并抢先接触高价值客户 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!TAB 汽车]

| | 用例 | 描述 | 成熟度 | 图案 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/automotive/icon-service-reminders.png" alt="服务提醒" width="40"> | [服务约会提醒](automotive/automotive-overview.md#service-appointment-reminders) | 根据车辆里程和服务历史记录发送个性化服务提醒 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/automotive/icon-recall-notifications.png" alt="撤回通知" width="40"> | [车辆召回通知](automotive/automotive-overview.md#vehicle-recall-notifications) | 使用服务计划选项发送个性化召回通知 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/automotive/icon-test-drive.png" alt="测试驱动" width="40"> | [试用计划](automotive/automotive-overview.md#test-drive-scheduling) | 使用经销商推荐启用个性化的测试驱动计划 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/automotive/icon-model-launch.png" alt="模型启动" width="40"> | [新模型启动促销活动](automotive/automotive-overview.md#new-model-launch-campaigns) | 根据当前车辆和偏好定位对新车型感兴趣的客户 | [!BADGE 基础]{type=Neutral} | [批出站消息激活](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| <img src="assets/use-case-icons/automotive/icon-trade-in.png" alt="以旧换新" width="40"> | [折价促销活动](automotive/automotive-overview.md#trade-in-value-campaigns) | 主动为准备升级的客户提供以旧换新价值评估 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/automotive/icon-parts-accessories.png" alt="部件附件" width="40"> | [部件和附件推荐](automotive/automotive-overview.md#parts-and-accessories-recommendations) | 根据车辆型号和保有期限推荐部件和附件 | [!BADGE 新兴]{type=Informative} | [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/automotive/icon-warranty.png" alt="保修" width="40"> | [保修和延长服务计划](automotive/automotive-overview.md#warranty-and-extended-service-plans) | 根据车辆使用时间，在最佳时间建议保修和服务计划 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/automotive/icon-connected-car.png" alt="联网汽车" width="40"> | [连接的汽车功能激活](automotive/automotive-overview.md#connected-car-feature-activation) | 根据车辆功能提供个性化的互联汽车功能推荐 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/automotive/icon-dealer-network.png" alt="经销商网络" width="40"> | [经销商网络协调](automotive/automotive-overview.md#dealer-network-coordination) | 根据位置和偏好启用个性化的经销商推荐 | [!BADGE 新兴]{type=Informative} | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/automotive/icon-vehicle-purchase.png" alt="车辆购买" width="40"> | [车辆购买Personalization](automotive/automotive-overview.md#vehicle-purchase-journey-personalization) | 使从研究到购买的车辆购买历程个性化 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| <img src="assets/use-case-icons/automotive/icon-financing.png" alt="融资" width="40"> | [融资和保险优惠](automotive/automotive-overview.md#financing-and-insurance-offers) | 根据信用状况提供个性化的融资和保险优惠 | [!BADGE 高级]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/automotive/icon-owner-loyalty.png" alt="所有者忠诚度" width="40"> | [所有者忠诚度计划](automotive/automotive-overview.md#owner-loyalty-programs) | 根据所有权历史记录个性化忠诚度沟通、奖励和独家优惠 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!TAB 金融服务]

| | 用例 | 描述 | 成熟度 | 图案 |
| --- | --- | --- | --- | --- |
| | [基于事务的警报和建议](financial-services/financial-services-overview.md#transaction-based-alerts-and-recommendations) | 发送交易和个性化推荐的实时警报 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [信用卡申请放弃恢复](financial-services/financial-services-overview.md#credit-card-application-abandonment-recovery) | 重新吸引已开始但未完成信用卡申请的客户 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [欺诈警报Personalization](financial-services/financial-services-overview.md#fraud-alert-personalization) | 根据客户喜好将欺诈警报和安全通信个性化 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/financial-services/icon-lead-nurturing.png" alt="潜在客户培养" width="40"> | [高价值潜在客户培养](financial-services/financial-services-overview.md#high-value-lead-nurturing) | 识别高价值潜在客户，并通过个性化的内容和优惠培养 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/financial-services/icon-account-dashboard.png" alt="帐户信息板" width="40"> | [个性化帐户信息板](financial-services/financial-services-overview.md#personalized-account-dashboard) | 根据帐户活动和财务目标个性化在线银行仪表板 | [!BADGE 新兴]{type=Informative} | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| | [投资Portfolio推荐](financial-services/financial-services-overview.md#investment-portfolio-recommendations) | 根据风险状况和目标提供个性化的投资推荐 | [!BADGE 新兴]{type=Informative} | [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| | [抵押贷款预批准促销活动](financial-services/financial-services-overview.md#mortgage-pre-approval-campaigns) | 根据配置文件和人生阶段定位可能进入抵押贷款市场的客户 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/financial-services/icon-product-recommendation.png" alt="产品推荐" width="40"> | 针对现有客户的[产品推荐](financial-services/financial-services-overview.md#product-recommendation-for-existing-customers) | 根据用户档案、交易和存留期推荐相关金融产品 | [!BADGE 高级]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/financial-services/icon-churn-prevention.png" alt="流失预防" width="40"> | [流失预防营销活动](financial-services/financial-services-overview.md#churn-prevention-campaigns) | 识别具有AI支持的预测的高风险客户，并参与保留期优惠 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| <img src="assets/use-case-icons/financial-services/icon-life-stage.png" alt="生命阶段" width="40"> | [基于生命周期阶段的产品优惠](financial-services/financial-services-overview.md#life-stage-based-product-offers) | 识别进入新生命阶段的客户并提供相关金融产品 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [忠诚度计划参与度](financial-services/financial-services-overview.md#loyalty-program-engagement) | 按层级和历史记录个性化忠诚度沟通、奖励和优惠 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [个性化的金融教育内容](financial-services/financial-services-overview.md#personalized-financial-education-content) | 根据客户的用户档案和兴趣提供个性化的金融教育 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!TAB 医疗保健]

| | 用例 | 描述 | 成熟度 | 图案 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/healthcare/icon-appointment-reminder.png" alt="约会提醒" width="40"> | [约会提醒自动化](healthcare/healthcare-overview.md#appointment-reminder-automation) | 通过首选通信渠道发送个性化约会提醒 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/healthcare/icon-post-visit.png" alt="访问后" width="40"> | [访问后跟进活动](healthcare/healthcare-overview.md#post-visit-follow-up-campaigns) | 发送访问后调查、护理指示和跟进预约提醒 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [实验室结果通知](healthcare/healthcare-overview.md#lab-results-notification) | 当通过首选渠道获得实验室结果时通知患者 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [保险范围验证](healthcare/healthcare-overview.md#insurance-coverage-verification) | 在预约之前主动确认和传达保险范围 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [远程保健约会提醒](healthcare/healthcare-overview.md#telehealth-appointment-reminders) | 为远程医疗预约发送个性化提醒，并附上连接说明 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/healthcare/icon-preventive-care.png" alt="预防性护理" width="40"> | [预防性护理提醒](healthcare/healthcare-overview.md#preventive-care-reminders) | 提醒患者根据年龄和病史推荐的预防性护理 | [!BADGE 基础]{type=Neutral} | [批出站消息激活](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| <img src="assets/use-case-icons/healthcare/icon-medication-adherence.png" alt="药物依从性" width="40"> | [药物遵守活动](healthcare/healthcare-overview.md#medication-adherence-campaigns) | 发送个性化提醒，帮助患者按计划服用药物 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [慢性病管理计划](healthcare/healthcare-overview.md#chronic-disease-management-programs) | 个性化慢性疾病管理沟通和监测提醒 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [新患者入门历程](healthcare/healthcare-overview.md#new-patient-onboarding-journey) | 通过欢迎信息、门户访问和计划自动执行多步骤上线 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [健康计划参与度](healthcare/healthcare-overview.md#wellness-program-engagement) | 使健康计划的沟通、挑战和奖励个性化 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [关怀团队协调](healthcare/healthcare-overview.md#care-team-coordination) | 在患者及其护理团队之间实现个性化通信 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [个性化健康内容交付](healthcare/healthcare-overview.md#personalized-health-content-delivery) | 根据患者情况提供个性化的健康教育内容 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!TAB 保险]

| | 用例 | 描述 | 成熟度 | 图案 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/insurance/icon-policy-renewal.png" alt="策略续订" width="40"> | [策略续订营销活动](insurance/insurance-overview.md#policy-renewal-campaigns) | 发送个性化的保单续订提醒和优惠 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [策略更改通知](insurance/insurance-overview.md#policy-change-notifications) | 发送有关策略更改和覆盖范围更新的个性化通知 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [报价单放弃恢复](insurance/insurance-overview.md#quote-abandonment-recovery) | 重新吸引已开始但未完成保险报价的客户 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [防止欺诈索赔](insurance/insurance-overview.md#claims-fraud-prevention) | 使用智能欺诈检测来识别可疑的索赔模式 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [灾难性事件响应](insurance/insurance-overview.md#catastrophic-event-response) | 在自然灾害期间主动与受影响地区的客户沟通 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [代理和代理协调](insurance/insurance-overview.md#agent-and-broker-coordination) | 在客户和分配的代理之间启用个性化通信 | [!BADGE 基础]{type=Neutral} | [批出站消息激活](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| <img src="assets/use-case-icons/insurance/icon-claims-process.png" alt="索赔流程" width="40"> | [索赔流程Personalization](insurance/insurance-overview.md#claims-process-personalization) | 个性化理赔流程通信、状态更新和支持资源 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [风险评估与预防](insurance/insurance-overview.md#risk-assessment-and-prevention) | 提供个性化的风险评估信息和预防提示 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [健康和预防计划](insurance/insurance-overview.md#wellness-and-prevention-programs) | 为保险客户提供个性化的健康计划沟通和奖励 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/insurance/icon-cross-sell.png" alt="交叉销售" width="40"> | [交叉销售产品推荐](insurance/insurance-overview.md#cross-sell-product-recommendations) | 根据现有保单和寿险阶段建议额外的保险产品 | [!BADGE 高级]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/insurance/icon-life-stage-based-product-offers.png" alt="生命阶段" width="40"> | [基于生命周期阶段的产品优惠](insurance/insurance-overview.md#life-stage-based-product-offers) | 识别进入新寿险阶段的客户并提供相关保险产品 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [折扣和节省机会](insurance/insurance-overview.md#discount-and-savings-opportunities) | 识别并传递个性化的折扣机会 | [!BADGE 高级]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |

>[!TAB 媒体和娱乐]

| | 用例 | 描述 | 成熟度 | 图案 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/media-entertainment/icon-new-content.png" alt="新内容" width="40"> | [新内容发布通知](media-entertainment/media-entertainment-overview.md#new-content-release-notifications) | 通知订阅者与其首选项匹配的新内容 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [监视列表和收藏夹提醒](media-entertainment/media-entertainment-overview.md#watchlist-and-favorites-reminders) | 在监视列表中发送有关未观看内容的提醒 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [实时活动查看提醒](media-entertainment/media-entertainment-overview.md#live-event-viewing-reminders) | 通知用户与其兴趣相匹配的即将举行的实时活动 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [内容完成营销活动](media-entertainment/media-entertainment-overview.md#content-completion-campaigns) | 提醒用户完成他们已开始但未完成的内容 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/media-entertainment/icon-content-recommendations.png" alt="内容推荐" width="40"> | [内容推荐引擎](media-entertainment/media-entertainment-overview.md#content-recommendation-engine) | 根据查看历史记录提供个性化的内容推荐 | [!BADGE 新兴]{type=Informative} | [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| | [个性化主页体验](media-entertainment/media-entertainment-overview.md#personalized-homepage-experience) | 动态地个性化主页，以便首先显示最相关的内容 | [!BADGE 新兴]{type=Informative} | [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| | [个性化播放列表生成](media-entertainment/media-entertainment-overview.md#personalized-playlist-generation) | 根据收听历史记录和首选项自动生成播放列表 | [!BADGE 新兴]{type=Informative} | [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| | [免费试用转化促销活动](media-entertainment/media-entertainment-overview.md#free-trial-conversion-campaigns) | 吸引包含个性化内容的免费试用用户以鼓励转化 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [跨平台内容同步](media-entertainment/media-entertainment-overview.md#cross-platform-content-sync) | 通过同步的首选项提供跨设备的无缝内容体验 | [!BADGE 新兴]{type=Informative} | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| | [社交共享Personalization](media-entertainment/media-entertainment-overview.md#social-sharing-personalization) | 根据内容首选项个性化社交共享提示 | [!BADGE 新兴]{type=Informative} | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/media-entertainment/icon-subscription-churn.png" alt="订阅流失" width="40"> | [订阅流失预防](media-entertainment/media-entertainment-overview.md#subscription-churn-prevention) | 识别有风险的订阅者并参与维系服务 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [高级功能追加销售](media-entertainment/media-entertainment-overview.md#premium-feature-upsell) | 确定将从个性化优惠的高级功能中受益的用户 | [!BADGE 高级]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |

>[!TAB 电信]

| | 用例 | 描述 | 成熟度 | 图案 |
| --- | --- | --- | --- | --- |
| | [数据使用情况警报和建议](telecommunications/telecommunications-overview.md#data-usage-alerts-and-recommendations) | 当客户达到数据限制时发送个性化警报 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [服务中断通知](telecommunications/telecommunications-overview.md#service-outage-notifications) | 主动通知客户其所在地区的服务中断 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [帐单付款提醒](telecommunications/telecommunications-overview.md#bill-payment-reminders) | 发送带有付款选项的个性化账单付款提醒 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [5G升级促销活动](telecommunications/telecommunications-overview.md#5g-upgrade-campaigns) | 符合资格获得个性化优惠的5G升级的目标客户 | [!BADGE 基础]{type=Neutral} | [批出站消息激活](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| <img src="assets/use-case-icons/telecommunications/icon-plan-optimization.png" alt="计划优化" width="40"> | [计划优化营销活动](telecommunications/telecommunications-overview.md#plan-optimization-campaigns) | 分析使用模式并建议最佳计划更改 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [新客户入门培训历程](telecommunications/telecommunications-overview.md#new-customer-onboarding-journey) | 使用欢迎信息和功能教程自动进行个性化载入 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [网络性能Personalization](telecommunications/telecommunications-overview.md#network-performance-personalization) | 根据位置和设备个性化网络性能信息 | [!BADGE 新兴]{type=Informative} | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/telecommunications/icon-device-upgrade.png" alt="设备升级" width="40"> | [设备升级建议](telecommunications/telecommunications-overview.md#device-upgrade-recommendations) | 识别符合条件的客户并提供个性化的设备推荐 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| <img src="assets/use-case-icons/telecommunications/icon-churn-prevention.png" alt="流失预防" width="40"> | [高价值客户的流失预防](telecommunications/telecommunications-overview.md#churn-prevention-for-high-value-customers) | 识别高价值风险客户，并提供维系服务 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [家庭计划管理](telecommunications/telecommunications-overview.md#family-plan-management) | 按家庭使用情况为家庭计划管理员提供个性化通信 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [加载项服务建议](telecommunications/telecommunications-overview.md#add-on-service-recommendations) | 根据计划、使用和偏好推荐相关的附加服务 | [!BADGE 高级]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| | [忠诚度计划参与度](telecommunications/telecommunications-overview.md#loyalty-program-engagement) | 按层级和历史记录个性化忠诚度沟通、奖励和优惠 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!TAB 旅游和酒店业]

| | 用例 | 描述 | 成熟度 | 图案 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/travel-hospitality/icon-cart-abandonment.png" alt="放弃购买" width="40"> | [购物车放弃恢复历程](travel-hospitality/travel-hospitality-overview.md#cart-abandonment-recovery-journey) | 检测放弃的预订购物车并触发个性化电子邮件历程 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-booking-reminders.png" alt="预订提醒" width="40"> | [多渠道预订提醒](travel-hospitality/travel-hospitality-overview.md#multi-channel-booking-reminders) | 通过电子邮件、文本和推送发送个性化预订提醒 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-seasonal-campaigns.png" alt="季节性活动" width="40"> | [季节性促销活动Personalization](travel-hospitality/travel-hospitality-overview.md#seasonal-campaign-personalization) | 根据季节性偏好和过去的预订，个性化营销活动 | [!BADGE 基础]{type=Neutral} | [批出站消息激活](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-personalized-homepage.png" alt="个性化主页" width="40"> | [新访客的个性化主页](travel-hospitality/travel-hospitality-overview.md#personalized-homepage-for-new-visitors) | 根据位置和浏览行为显示个性化推荐 | [!BADGE 新兴]{type=Informative} | [匿名访客Web Personalization](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-high-intent.png" alt="高意图" width="40"> | [高意图访客定位](travel-hospitality/travel-hospitality-overview.md#high-intent-visitor-targeting) | 通过AI评分识别高意图访客，并通过个性化优惠进行定位 | [!BADGE 新兴]{type=Informative} | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-post-booking-upsell.png" alt="预订后追加销售" width="40"> | [后期预订追加销售活动](travel-hospitality/travel-hospitality-overview.md#post-booking-upsell-campaigns) | 在预订后触发升级、偏移和包追加销售促销活动 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-win-back.png" alt="双赢" width="40"> | [失效客户的回馈促销活动](travel-hospitality/travel-hospitality-overview.md#win-back-campaigns-for-lapsed-customers) | 通过个性化的回馈优惠吸引失效客户 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-dynamic-itinerary.png" alt="动态行程" width="40"> | [动态行程推荐](travel-hospitality/travel-hospitality-overview.md#dynamic-itinerary-recommendations) | 根据过去的预订和偏好设置显示个性化路线 | [!BADGE 新兴]{type=Informative} | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-recently-browsed.png" alt="最近浏览" width="40"> | 首页上[最近浏览的产品](travel-hospitality/travel-hospitality-overview.md#recently-browsed-products-on-homepage) | 显示最近查看的目标以鼓励回访 | [!BADGE 新兴]{type=Informative} | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-group-booking.png" alt="组预订" width="40"> | [组预订推荐](travel-hospitality/travel-hospitality-overview.md#group-booking-recommendations) | 向频繁进行团体预订的人推荐团体包和家庭友好选项 | [!BADGE 新兴]{type=Informative} | [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-exit-intent.png" alt="退出意图" width="40"> | [具有目标优惠的退出意图模式](travel-hospitality/travel-hospitality-overview.md#exit-intent-modal-with-targeted-offers) | 当访客显示退出意图时，使用相关选件显示个性化模式窗口 | [!BADGE 高级]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-loyalty-program.png" alt="忠诚度计划" width="40"> | [忠诚度计划Personalization](travel-hospitality/travel-hospitality-overview.md#loyalty-program-personalization) | 按忠诚度级别和积分平衡个性化网站、优惠和通信 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!TAB B2B]

| | 用例 | 描述 | 成熟度 | 图案 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/b2b/icon-webinar-demo.png" alt="网络研讨会演示" width="40"> | [网络研讨会和演示计划](b2b/b2b-overview.md#webinar-and-demo-scheduling) | 根据潜在客户兴趣个性化网络研讨会邀请和演示计划 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/b2b/icon-abm.png" alt="ABM" width="40"> | [Account-Based Marketing Personalization](b2b/b2b-overview.md#account-based-marketing-personalization) | 根据购买信号为目标客户个性化营销通信 | [!BADGE 新兴]{type=Informative} | [B2B 受众激活](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md) |
| <img src="assets/use-case-icons/b2b/icon-lead-scoring.png" alt="商机评分" width="40"> | [潜在客户评分和培养](b2b/b2b-overview.md#lead-scoring-and-nurturing) | 通过培养活动自动对潜在客户进行评分，并将高分客户引向销售 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/b2b/icon-content-personalization.png" alt="内容个性化" width="40"> | [面向潜在客户的Personalization内容](b2b/b2b-overview.md#content-personalization-for-prospects) | 根据潜在客户行业、角色和参与情况使网站内容和资源个性化 | [!BADGE 新兴]{type=Informative} | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/b2b/icon-event-registration.png" alt="事件注册" width="40"> | [活动注册和跟进](b2b/b2b-overview.md#event-registration-and-follow-up) | 自动化个性化的事件注册确认、提醒和跟进 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/b2b/icon-trial-conversion.png" alt="试用转换" width="40"> | [产品试用转换促销活动](b2b/b2b-overview.md#product-trial-conversion-campaigns) | 通过个性化的推荐吸引试用用户，以鼓励付费转化 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/b2b/icon-customer-onboarding.png" alt="客户入门" width="40"> | [客户成功和入门](b2b/b2b-overview.md#customer-success-and-onboarding) | 通过相关培训和资源使入门历程个性化 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/b2b/icon-competitive-replacement.png" alt="竞争替代" width="40"> | [竞争替换促销活动](b2b/b2b-overview.md#competitive-replacement-campaigns) | 使用具有个性化迁移优惠的竞争对手产品定位潜在客户 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/b2b/icon-case-study.png" alt="案例研究" width="40"> | [案例研究和ROI Personalization](b2b/b2b-overview.md#case-study-and-roi-personalization) | 根据潜在客户的行业提供个性化的案例分析和ROI计算器 | [!BADGE 新兴]{type=Informative} | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| | [客户宣传计划](b2b/b2b-overview.md#customer-advocacy-programs) | 寻找并吸引满意的客户提供参考和证明 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/b2b/icon-contract-renewal.png" alt="合同续订" width="40"> | [合同续订活动](b2b/b2b-overview.md#contract-renewal-campaigns) | 主动与通过个性化优惠寻求续订的客户接洽 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| <img src="assets/use-case-icons/b2b/icon-upsell-expansion.png" alt="追加销售扩展" width="40"> | [追加销售和扩展机会](b2b/b2b-overview.md#upsell-and-expansion-opportunities) | 根据使用模式和增长指标确定准备好升级的客户 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!ENDTABS]
