---
title: 用例目录
description: 按垂直、成熟度级别或实施模式浏览行业用例，以找到您的Adobe Experience Platform历程的正确起点。
doc-type: overview-page
exl-id: 7a3c2f1e-9b4d-4e6a-8f5c-2d1b3a4e7c9f
source-git-commit: 8ad59ff130dae13553f10049eb685cf557a73ead
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 6%

---

# 用例目录

探索[!DNL Adobe Experience Platform]和应用程序的行业用例。 按行业浏览，查看垂直行业的用例；按成熟度级别浏览，以找到适合贵组织的起点；或按实施模式浏览，以了解适合您需求的技术方法。

每个用例通过用例模式链接到详细的实施指南，用例模式描述了使用例变为现实所需的功能链、决策点和配置步骤。

## 按行业浏览

>[!BEGINTABS]

>[!TAB 零售]

零售组织使用[!DNL Adobe Experience Platform]将在线商店、实际位置和忠诚度计划中的客户数据统一到每位购物者的单一视图中。

| | 用例 | 描述 | 成熟度 | 图案 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="个性化的产品推荐" width="40"> | [个性化产品推荐](retail/retail-overview.md#personalized-product-recommendations) | 根据浏览和购买历史记录显示个性化产品 | [!BADGE 新兴]{type=Informative} | [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="已放弃的购物车" width="40"> | [放弃的购物车电子邮件恢复](retail/retail-overview.md#abandoned-cart-email-recovery) | 为已放弃的购物车发送个性化提醒 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="库存紧迫性" width="40"> | [基于清单的紧急活动](retail/retail-overview.md#inventory-based-urgency-campaigns) | 产品库存不足时触发实时警报 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="交叉销售追加销售" width="40"> | [交叉销售和追加销售推荐](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | 在结账时和电子邮件中显示相关的交叉销售和追加销售产品 | [!BADGE 高级]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="欢迎系列" width="40"> | [新客户欢迎系列](retail/retail-overview.md#new-customer-welcome-series) | 通过个性化推荐自动执行多电子邮件欢迎系列 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="价格下降" width="40"> | [价格下降警报](retail/retail-overview.md#price-drop-alerts) | 当愿望清单或查看过的商品降价时通知客户 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="补货" width="40"> | [补货提醒](retail/retail-overview.md#replenishment-reminders) | 发送定期购买消耗性产品的自动提醒 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="类别页面" width="40"> | [个性化类别页面](retail/retail-overview.md#personalized-category-pages) | 根据每位客户的喜好动态地对类别页面重新排序 | [!BADGE 新兴]{type=Informative} | [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="购买后" width="40"> | [购买后跟进活动](retail/retail-overview.md#post-purchase-follow-up-campaigns) | 发送关怀提示、审核请求和相关产品建议 | [!BADGE 新兴]{type=Informative} | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [VIP客户独家优惠](retail/retail-overview.md#vip-customer-exclusive-offers) | 提供独家优惠并抢先接触高价值客户 | [!BADGE 高级]{type=Caution} | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [缺货通知](retail/retail-overview.md#out-of-stock-notifications) | 在缺货产品可用时通知客户 | [!BADGE 基础]{type=Neutral} | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [社交校对Personalization](retail/retail-overview.md#social-proof-personalization) | 根据客户个人资料显示个性化的评论和评级 | [!BADGE 新兴]{type=Informative} | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

>[!TAB 金融服务]

金融服务使用案例即将推出。[查看当前金融服务用例](financial-services/financial-services-overview.md)。

>[!TAB 医疗保健]

医疗保健用例即将推出。[查看当前的医疗保健用例](healthcare/healthcare-overview.md)。

>[!TAB 汽车]

汽车用例即将推出。[查看当前汽车用例](automotive/automotive-overview.md)。

>[!TAB 旅游和酒店业]

旅行和酒店使用案例即将推出。[查看当前的旅行和酒店用例](travel-hospitality/travel-hospitality-overview.md)。

>[!TAB 电信]

电信用例即将推出。[查看当前的电信用例](telecommunications/telecommunications-overview.md)。

>[!TAB 媒体和娱乐]

媒体和娱乐用例即将推出。[查看当前的媒体和娱乐用例](media-entertainment/media-entertainment-overview.md)。

>[!TAB 保险]

保险用例即将推出。[查看当前的保险用例](insurance/insurance-overview.md)。

>[!TAB B2B]

B2B用例即将推出。[查看当前B2B用例](b2b/b2b-overview.md)。

>[!ENDTABS]

## 按成熟度级别浏览

>[!BEGINTABS]

>[!TAB 基础]

使用单渠道交付的基本且经验证的模式。 组织开始其[!DNL Experience Platform]历程的理想起点。

| | 用例 | 行业 | 商业影响 | 图案 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="已放弃的购物车" width="40"> | [放弃的购物车电子邮件恢复](retail/retail-overview.md#abandoned-cart-email-recovery) | 零售 | 购物车回收率25-35% | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="库存紧迫性" width="40"> | [基于清单的紧急活动](retail/retail-overview.md#inventory-based-urgency-campaigns) | 零售 | 转化率增加30-40% | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="价格下降" width="40"> | [价格下降警报](retail/retail-overview.md#price-drop-alerts) | 零售 | 20-30%转化率 | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [缺货通知](retail/retail-overview.md#out-of-stock-notifications) | 零售 | 转化率40-50% | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |

>[!TAB 新兴]

多渠道和多步骤模式，这些模式以AI驱动的个性化和编排历程的基础功能为基础。

| | 用例 | 行业 | 商业影响 | 图案 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="产品推荐" width="40"> | [个性化产品推荐](retail/retail-overview.md#personalized-product-recommendations) | 零售 | CTR增加20-30%，转化提升15-25% | [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="类别页面" width="40"> | [个性化类别页面](retail/retail-overview.md#personalized-category-pages) | 零售 | 参与增加25-35% | [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="欢迎系列" width="40"> | [新客户欢迎系列](retail/retail-overview.md#new-customer-welcome-series) | 零售 | 40-50%的参与率 | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="补货" width="40"> | [补货提醒](retail/retail-overview.md#replenishment-reminders) | 零售 | 30-40%重复购买率 | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="购买后" width="40"> | [购买后跟进活动](retail/retail-overview.md#post-purchase-follow-up-campaigns) | 零售 | 15-20%的审阅率，10-15%的重复购买率 | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [社交校对Personalization](retail/retail-overview.md#social-proof-personalization) | 零售 | 转化率提高10-15% | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

>[!TAB 高级]

通过实时决策和人工智能驱动的选件选择实现跨渠道编排，从而提供最复杂的客户体验。

| | 用例 | 行业 | 商业影响 | 图案 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="交叉销售追加销售" width="40"> | [交叉销售和追加销售推荐](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | 零售 | AOV增加25至75美元，收入提升10%至15% | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| | [VIP客户独家优惠](retail/retail-overview.md#vip-customer-exclusive-offers) | 零售 | 来自VIP的参与率为50-70% | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!ENDTABS]

## 按实施模式浏览

>[!BEGINTABS]

>[!TAB 营销活动管理和编排]

### 事件触发的消息传递

通过及时的单渠道消息响应实时行为事件。

| | 用例 | 行业 | 成熟度 | 商业影响 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="已放弃的购物车" width="40"> | [放弃的购物车电子邮件恢复](retail/retail-overview.md#abandoned-cart-email-recovery) | 零售 | [!BADGE 基础]{type=Neutral} | 购物车回收率25-35% |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="库存紧迫性" width="40"> | [基于清单的紧急活动](retail/retail-overview.md#inventory-based-urgency-campaigns) | 零售 | [!BADGE 基础]{type=Neutral} | 转化率增加30-40% |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="价格下降" width="40"> | [价格下降警报](retail/retail-overview.md#price-drop-alerts) | 零售 | [!BADGE 基础]{type=Neutral} | 20-30%转化率 |
| | [缺货通知](retail/retail-overview.md#out-of-stock-notifications) | 零售 | [!BADGE 基础]{type=Neutral} | 转化率40-50% |

### 多步协调历程

指导客户完成根据参与度和行为调整的多点接触顺序。

| | 用例 | 行业 | 成熟度 | 商业影响 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="欢迎系列" width="40"> | [新客户欢迎系列](retail/retail-overview.md#new-customer-welcome-series) | 零售 | [!BADGE 新兴]{type=Informative} | 40-50%的参与率 |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="补货" width="40"> | [补货提醒](retail/retail-overview.md#replenishment-reminders) | 零售 | [!BADGE 新兴]{type=Informative} | 30-40%重复购买率 |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="购买后" width="40"> | [购买后跟进活动](retail/retail-overview.md#post-purchase-follow-up-campaigns) | 零售 | [!BADGE 新兴]{type=Informative} | 15-20%的审阅率，10-15%的重复购买率 |

### 使用Decisioning进行跨渠道历程

在每个接触点通过实时优惠决策编排跨渠道体验。

| | 用例 | 行业 | 成熟度 | 商业影响 |
| --- | --- | --- | --- | --- |
| | [VIP客户独家优惠](retail/retail-overview.md#vip-customer-exclusive-offers) | 零售 | [!BADGE 高级]{type=Caution} | 来自VIP的参与率为50-70% |

>[!TAB Personalization]

### 行为推荐

使用AI驱动模型根据行为信号呈现个性化内容和产品。

| | 用例 | 行业 | 成熟度 | 商业影响 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="产品推荐" width="40"> | [个性化产品推荐](retail/retail-overview.md#personalized-product-recommendations) | 零售 | [!BADGE 新兴]{type=Informative} | CTR增加20-30%，转化提升15-25% |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="类别页面" width="40"> | [个性化类别页面](retail/retail-overview.md#personalized-category-pages) | 零售 | [!BADGE 新兴]{type=Informative} | 参与增加25-35% |

### Offer Decisioning

使用集中式决策逻辑评估并为每个客户和上下文选择最佳优惠。

| | 用例 | 行业 | 成熟度 | 商业影响 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="交叉销售追加销售" width="40"> | [交叉销售和追加销售推荐](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | 零售 | [!BADGE 高级]{type=Caution} | AOV增加25至75美元，收入提升10%至15% |

### 已知访客Web/应用程序Personalization

根据个人资料、偏好和浏览上下文，为已识别的访客个性化Web和应用程序内容。

| | 用例 | 行业 | 成熟度 | 商业影响 |
| --- | --- | --- | --- | --- |
| | [社交校对Personalization](retail/retail-overview.md#social-proof-personalization) | 零售 | [!BADGE 新兴]{type=Informative} | 转化率提高10-15% |

>[!ENDTABS]
