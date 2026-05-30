---
title: 多步协调历程
description: 了解如何在一段时间内通过分支的多点接触历程引导用户档案，其中包含等待、条件和多个消息操作。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 5667b188-1b20-4a85-aebb-74efd5f771a1
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1798'
ht-degree: 5%

---

# 多步编排历程

本指南介绍了多步骤编排的历程用例模式，该模式使用[!DNL Adobe Journey Optimizer] (AJO)和[!DNL Real-Time Customer Data Platform] (RT-CDP)来编排随时间推移交付多条消息的分支和多点接触客户历程。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

## 用例模式

**多步骤编排历程**

随时间推移通过含等待、条件和多个消息操作的分支、多触点历程引导用户档案。

**执行计划：**&#x200B;受众评估>历程执行（多节点）>条件分支>消息投放(xN) >退出标准>报表

## 用例概述

多步骤编排的历程可处理单个消息不足以达到预期客户结果的业务情形。 该历程不是一次性发送，而是通过电子邮件、短信消息、推送通知或应用程序内消息等一系列接触点引导每个用户档案，这些接触点在几天或几周内间隔开，并根据用户档案属性、行为信号或事件数据调整路径的分支逻辑。

这些历程是AJO中最复杂的营销活动模式。 它们将基于受众或基于事件的进入与一组操作节点（消息）、条件节点（分支逻辑）、等待节点（时间延迟）和退出标准（转化事件或超时）相结合。 每个用户档案均以自己的速度独立完成历程，并在每个步骤接收与上下文相关的内容。

此模式包含更简单的模式 — 为单次发送营销活动批量激活出站消息，为单次事件响应使用事件触发的消息传递。 当用例需要随时间通过多次交互培养用户档案时，请使用此模式。

>[!NOTE]
>如果您的历程需要在各个决策点动态选择最佳优惠、内容或渠道，请参阅[具有决策的跨渠道历程](cross-channel-journey-with-decisioning.md)。 该模式通过AJO Decisioning集成扩展了这一模式。

## 主要业务目标

此用例模式支持以下业务目标。

### 提高客户维系率

透过价值导向型经验及持续培养关系，让现有客户持续参与及不断更新。

**KPI：**&#x200B;维系、客户存留期值、参与度

[了解有关提高客户维系率的更多信息](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### 改进客户入门

通过优化的个性化欢迎体验和激活历程，加快新客户的价值实现。

**KPI：**&#x200B;参与度、维系率、转化率

[详细了解如何改进客户入门](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)

### 重新吸引休眠客户

通过基于行为信号的有针对性的重新激活促销活动，吸引非活跃或失效的客户。

**KPI：**&#x200B;参与度、维系率、转化率

[了解有关提高客户维系率的更多信息](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### 恢复放弃的购物车和历程

通过及时、个性化的跟进，重新吸引在购买、申请或注册流程中放弃的用户。

**KPI：**&#x200B;转化率、递增收入、参与度

[了解有关回收废弃购物车和历程的更多信息](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)

## 战术用例示例

以下场景说明了多步编排历程模式的常见应用。

- **客户入门培训系列** — 欢迎电子邮件，随后是功能培训，然后在注册后的前14天内提供激活提示
- **重新参与滴注式营销活动** — 提醒电子邮件，然后是激励优惠，最后通知已过期客户超过3周
- **忠诚度里程碑历程** — 逐级升级通知，后跟独占优惠，然后在会员资格周年临近时提供续订提醒
- **回馈序列** — “我们想你”电子邮件，通过电子邮件提供折扣优惠，然后为失效购买者发送最终短信提醒
- **产品采用历程** — 试用欢迎、使用提示，然后随着试用期的进展提供升级提示
- **订阅续订序列** — 30天通知，7天提醒，然后为即将续订的订阅发送到期日消息
- **购买后培养** — 感谢电子邮件、使用方法指南、交叉销售推荐，然后在购买30天后提交审核请求

## 关键绩效指标

使用以下KPI衡量多步编排的历程实施的有效性。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 历程完成率 | 完成完整历程且未提前退出的用户档案的百分比 | 历程报表：已退出（完成）/已输入 |
| 步骤转化率 | 从一个步骤进展到下一个步骤的配置文件百分比 | 历程报告中的按节点量度 |
| 渠道参与率 | 每个接触点的打开率、点进率和响应率 | 每消息投放和参与量度 |
| 退出条件转化率 | 在历程超时前触发退出事件（例如，购买、注册）的配置文件百分比 | 退出条件命中计数/输入的总数 |
| 转化时间 | 从历程进入到退出标准事件的平均持续时间 | 历程分析：从条目时间戳到转化事件时间戳 |
| 历程流失率 | 在每个步骤停止参与的用户档案百分比（流失分析） | 跨历程步骤的CJA流失可视化图表 |
| 保留/重新参与率 | 返回活动状态的目标用户档案的百分比 | CJA中的旅程后行为分析 |

## 应用程序

以下应用程序用于实现此用例模式。

- **[!DNL Adobe Journey Optimizer] (AJO)** —历程编排引擎、消息创作、渠道配置、内容试验、频度和冲突管理以及报告
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 历程进入受众的受众评估和定义、个性化的配置文件数据和条件分支
- **[!DNL Adobe Experience Platform] (AEP)** — 配置文件存储、身份服务、事件数据摄取和基础数据基础架构

## 相关文档

以下资源提供了有关此实施中使用的功能的更多详细信息。

### 历程

- [历程入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [创建历程](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [历程属性](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [发布历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [测试您的历程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)

### 历程活动

- [读取受众活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [受众鉴定事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [条件活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在历程中添加消息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [结束活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [配置自定义操作](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions)

### 登入和退出管理

- [历程条目管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [退出标准](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### 渠道配置

- [电子邮件配置入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [设置渠道平面](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [创建 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP预热计划](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [配置短信渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 消息创作和个性化

- [创建电子邮件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [使用电子邮件Designer内容组件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [辅助函数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用电子邮件模板](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [预览和测试内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 内容试验

- [内容体验入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [内容试验报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [统计计算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### 频率、冲突和优先级

- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [业务规则概述](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [冲突和优先级管理入门](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [优先级分数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [历程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [识别潜在冲突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### 受众和分段

- [分段服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language参考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [流式客户细分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/edge-segmentation)

### 报告和分析

- [历程实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Analysis Workspace概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [CJA概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

### 同意和治理

- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [数据治理概述](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [管理禁止列表](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 数据基础

- [XDM系统概述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity服务概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [配置文件概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [计算属性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
