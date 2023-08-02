---
title: 零售行业 - 通过 Experience Cloud 应用程序激活
description: 跨数字媒体、电子邮件、推送和 Web 渠道提供实时客户体验。
solution: Real-Time Customer Data Platform, Customer Journey Analytics, Journey Orchestration, Campaign, Analytics, Target
kt: 9474
exl-id: a675bc81-e76c-491a-8718-359867d63351
source-git-commit: ae7347be5095ca4a7f99f9371dd94d87097112b0
workflow-type: ht
source-wordcount: '630'
ht-degree: 100%

---

# 零售行业业务挑战

综合体验业务旨在个性化整个客户历程，以提高忠诚度、向现有客户追加销售，并优化整个营销活动的营销支出。实现目标的战略是扩展其数字功能，以包括线下客户数据和交易数据，从而推动增长。

## Adobe 方法

* 生成统一的客户档案，其中包含可实时激活的所有相关线上/线下数据
* 跨 Web、媒体和推送渠道编排客户互动，以推动首次或第二次购买行为。

## 提供的商业价值

| 目标 | 战术 | 解锁的价值 |
|---|---|---|
| **编排实时客户历程&#x200B;**<br></br>**促使新客户重复购买&#x200B;**<br></br>**提高营销效率并降低媒体成本**</ul> | <ul><li>强大的数据和身份策略，以推动全面的实时用户档案。</li><li>实时客户和事务数据流，包括 90 天的历史负载</li><li>将区段流传输到 Advertising Networks 和 Adobe Target，以推动媒体支出和个性化工作。</li><li>客户在 Adobe Campaign 的实时历程，包括衡量绩效的策略</li></ul> | <ul><li><strong>Real-time Customer Data Platform：</strong>跨媒体、电子邮件、推送和 Web 提供实时客户体验</li><li><strong>数据源：</strong>流数据，涵盖此零售商的用户档案商店、订单系统、产品目录和零售商店。</li><li><strong>实时媒体激活：</strong>将区段流传输到 Advertising Networks 以进行归因和广告抑制</li><li><strong>实时 Web 个性化：</strong>将激活的区段流传输到 Adobe Target，以便根据零售商的 Web 体验激活区段。</li><li><strong>大规模历程编排：</strong>实时触发消息，附加所有可用的客户数据，并实时激活到电子邮件和推送渠道</li></ul> |


## 用例

| 类别 | 目标 | 用例 | 描述 |
|:----|:----|:----|:----|
| 客户历程 | 客户获取 | 欢迎系列 | 通过业务、产品和服务简介来欢迎新订阅者 |
| | | 第一次购买计划 | |
| | 提高销售额 | 放弃的购物车/浏览 | 恢复潜在购买者并提高销售额 |
| | | 产品审查/交叉销售 | 通过产品评论交叉销售更多商品。 |
| | | 产品促销 |  |
| | | 需要重新排序 | 循环的产品/服务的定期提醒 |
| | 品牌忠诚度 | 赢回 | 恢复处于非活动状态的客户。 |
| | | 生日提醒 | 通过参加客户的生日庆祝活动，与客户建立更加亲近的关系！ |
| 销售 | 管理库存 | 补齐现货 | 通过向客户显示所需产品有现货来改善库存 |
| | | 次优类别 | 为用户确定最佳类别/销售 |
| | | 最畅销商品 | |
| | | 降价提醒 | 向用户显示他们喜欢的商品已降价 |
| | | 类似产品 |  |
| 个性化 | 提高转化率 | 优惠券/优惠 | 向客户显示最佳优惠/优惠券 |
| | | 个性化产品搜索 | 改善搜索体验 |
| | | 产品推荐 | 改善产品浏览体验 |
| | | 全渠道体验 | 跨所有渠道接触客户 |
| 衡量 | 了解客户历程 | 跨渠道营销活动 | 衡量跨渠道营销活动 |
| | | 区段表现 | 了解区段表现和贡献 |
| | | 流失报告 | 可视化每个阶段的转化情况 |
| | | 同类群组分析 | 衡量区段组之间的参与度 |
| | | 线上到线下报告 | 了解客户转化如何带动店内体验 |
| | | 归因 | 查看哪个接触点/体验对购买转化影响最大 |
| | | 预测性洞察 | 进一步了解客户倾向 |

## 架构

<img src="../vertical-blueprints/assets/retail-architecture.png" alt="零售参考架构" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />


## 相关蓝图


| 用例/集成  | 链接 |
|:----|:----|
| CJA + AEP | [Customer Journey Analytics Blueprint 概述](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=zh-Hans) |
| | [Customer Journey Analytics - 用例](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cja-usecases.html?lang=zh-Hans) |
| AJO + AEP | [Adobe Journey Optimizer - 用例](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/journey-optimizer.html?lang=zh-Hans) |
| | [决策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=zh-Hans) |
| RTCDP + AEP | [线上/线下受众激活](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=zh-Hans) |
| | [Experience Platform + 应用程序激活](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=zh-Hans) |
| Marketo + AEP | [B2B 激活与营销](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/overview.html?lang=zh-Hans) | |
| Target + AEP | [Adobe Target 用例 - 行为 Web/移动个性化](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/behavioral.html?lang=zh-Hans) | [使用已知客户数据的 Web/移动个性化](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/known-personalization.html?lang=zh-Hans) | |
