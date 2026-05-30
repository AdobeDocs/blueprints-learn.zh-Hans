---
title: 事件触发的消息传递
description: 了解如何响应行为或系统事件而交付情境式实时消息。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 75137990-9848-40c0-abf3-adbd21d2de52
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1955'
ht-degree: 5%

---

# 事件触发的消息传递

本指南介绍事件触发的消息传递用例模式，该模式使用[!DNL Adobe Journey Optimizer] (AJO)、[!DNL Real-Time Customer Data Platform] (RT-CDP)和[!DNL Adobe Experience Platform] (AEP)来传递上下文实时消息，以响应行为或系统事件。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

此模式涵盖从事件摄取和历程创建到消息交付和性能报告的整个生命周期。

## 用例模式

本节介绍驱动事件触发式消息传递的核心模式和执行计划。

**事件触发的消息传送**

监听实时行为或系统事件，然后将上下文消息交付给触发的用户档案。

**执行计划：**&#x200B;事件摄取>历程条目>条件评估>消息投放>报告

## 用例概述

事件触发的消息传送响应于实时行为或系统事件提供上下文消息。 与批量出站消息激活不同（按计划发送到预评估的受众），此模式侦听符合条件的事件（例如购物车放弃、浏览会话、表单提交或系统状态更改），并立即将触发的用户档案输入到评估条件并发送消息的历程中。

该模式依赖于实时事件流式传输到AEP（通过Web SDK、Mobile SDK或服务器端API）、在AJO中具有单一事件条目的旅程，以及确定是否发送和发送内容的条件评估逻辑。 消息通常在触发事件后的几分钟内发送，因此此模式非常适合时间敏感型上下文相关通信。

与计划的批处理通信相比，组织使用此模式来实时响应客户操作，提高了相关性并提高了参与度和转化率。 常见情形包括放弃的购物车恢复、购买后跟进、注册后的欢迎邮件，以及付款故障或价格下降警报等时效性强的通知。

## 主要业务目标

此用例模式支持以下业务目标。

**[恢复放弃的购物车和历程](../../business-objectives/customer-experience/recover-abandoned-carts-journeys.md)**

通过及时、个性化的跟进，重新吸引在购买、申请或注册流程中放弃的用户。

| KPI |
| --- |
| 转化率、增量收入、参与度 |

**[提高转化率](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

提高完成所需操作（如购买、注册或表单提交）的访客和潜在客户的百分比。

| KPI |
| --- |
| 转化率、潜在客户转化、每个潜在客户的成本 |

**[提供个性化的客户体验](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

根据个人偏好、行为和生命周期阶段定制内容、选件和消息。

| KPI |
| --- |
| 参与度、转化率、客户满意度(CSAT) |

**[改进客户入门](../../business-objectives/customer-experience/improve-customer-onboarding.md)**

通过优化的个性化欢迎体验和激活历程，加快新客户的价值实现。

| KPI |
| --- |
| 参与度、维系率、转化率 |

## 战术用例示例

以下情形说明了如何跨不同的业务上下文应用事件触发的消息传递。

- **购物车放弃电子邮件或短信** — 当客户将商品添加到购物车但未在定义的时间范围内完成购买时，发送提醒消息
- **浏览放弃跟进** — 重新吸引查看了产品或内容但未执行转化操作的访客
- **购买后感谢或交叉销售** — 在购买事件后立即提供确认和交叉销售推荐
- **试用到期提醒** — 通知即将结束免费试用的用户，提供续订或转换消息
- **注册后的欢迎邮件** — 当新用户注册或创建帐户时，立即发送入门邮件
- **表单提交确认** — 通过上下文确认确认确认表单提交（联系请求、申请、注册）
- **付款失败通知** — 在定期付款失败时提醒客户，提示他们更新付款信息
- **应用程序卸载回送推送通知** — 当用户卸载移动应用程序时触发回送消息
- **预订或约会确认** — 在安排预订、预订或约会后立即发送确认
- **愿望清单项目的价格下降警报** — 当愿望清单中的产品降价时通知客户

## 关键绩效指标

以下KPI有助于衡量事件触发的消息传递实施的有效性。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 转化率 | 完成所需操作（购买、注册、续订）的触发消息收件人的百分比 | 转化/投放消息* 100 |
| 增量收入 | 与不发送控制组相比，由事件触发的消息产生的额外收入 | 来自触发发送的收入 — 控制组基线 |
| 打开率 | 收件人打开的已投放邮件的百分比 | 打开/交付* 100 |
| 点进率(CTR) | 至少生成一次点击的已投放消息的百分比 | 点击次数/交付次数* 100 |
| 转化时间 | 消息投放和转化事件之间的平均已用时间 | Avg（转化时间戳 — 投放时间戳） |
| 历程完成率 | 进入历程并到达消息投放步骤的用户档案的百分比（不会被条件或退出条件丢弃） | 到达投放的用户档案/进入历程的用户档案* 100 |
| 消息禁止显示率 | 由于频率限制、同意或条件评估而抑制的合格用户档案的百分比 | 隐含配置文件/合格配置文件总数* 100 |
| 跳出率 | 由于硬退回或软退回而无法投放的消息百分比 | 退回数/已发送数* 100 |

## 应用程序

在此用例模式中使用以下Adobe应用程序。

- **[!DNL Adobe Journey Optimizer] (AJO)** — 包含单一历程条目、条件评估、等待步骤、消息创作、渠道配置、频率管理和投放报告的事件编排
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 历程中基于条件的筛选的受众评估、同意和治理实施、配置文件扩充
- **[!DNL Adobe Experience Platform] (AEP)** — 通过Web SDK、Mobile SDK或服务器端API进行实时事件摄取；数据建模；身份解析；Edge Network

## 相关文档

以下资源提供了有关此实施中使用的功能的更多详细信息。

### 历程编排

- [历程入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [创建历程](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [历程属性](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [受众鉴定事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [条件活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在历程中添加消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [退出标准](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [历程条目管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [测试您的历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [发布历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### 渠道配置

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [创建 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP预热计划](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [电子邮件表面设置](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [管理禁止列表](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 消息创作和个性化

- [创建电子邮件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [辅助函数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [创建短信消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [设计推送通知](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### 频率和业务规则

- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [业务规则概述](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [API上限](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/channel-surfaces/capping)

### 冲突和优先级管理

- [冲突和优先级管理入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [识别潜在冲突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [优先级分数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [历程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### 报告和性能

- [历程实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### 数据收集和摄取

- [Web SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [移动SDK概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Edge Network Server API概述](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [配置数据流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [流式摄取概述](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### 数据建模和架构

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### 身份和配置文件

- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身份命名空间概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/features/namespaces)
- [身份标识图链接规则](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [配置文件概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [合并策略概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### 分段和受众

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### 数据治理和同意

- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [同意和偏好设置字段组](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### 计算属性

- [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [计算属性UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

### 监控和可观察性

- [警报概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [可观察性分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### 护栏

- [Journey Optimizer护栏](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [摄取护栏](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### 教程和指南

- [创建历程教程](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [安装Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
