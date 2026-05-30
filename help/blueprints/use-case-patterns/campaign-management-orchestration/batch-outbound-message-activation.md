---
title: 批量出站消息激活
description: 了解如何在单个批量执行中评估受众并投放计划的出站消息。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 192853ce-02ab-46e6-9092-3db5354bc19c
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1701'
ht-degree: 4%

---

# 批量出站消息激活

本指南介绍了批量出站消息激活用例模式，该模式使用[!DNL Adobe Journey Optimizer] (AJO)和[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)将计划的出站消息传递到定义的受众区段。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

批量出站消息激活是一对多出站消息传递的基本营销活动模式。 它涵盖从受众定义到消息投放和性能分析的整个生命周期。

## 用例模式

**批量出站消息激活**

评估受众，然后在单个批量执行中将计划的出站消息（电子邮件、短信、推送）交付给所有符合条件的用户档案。

**执行计划：**&#x200B;受众评估>消息创作>营销活动执行>报告

## 用例概述

组织经常需要在特定时间或响应系统事件，向已知受众区段投放单个消息。 此模式通过将[!DNL RT-CDP]中的受众评估与[!DNL Journey Optimizer]中的消息创作和营销活动执行结合起来来满足该要求。

业务场景简单明了：定义应该接收消息的人员、通过个性化创建消息内容、将受众和消息绑定到活动或历程中，并按计划、通过受众资格或通过系统触发器执行发送。 结果生成一个投放消息，其中具有投放、参与和转化量度的完整报告。

每当可以通过在一次执行中将单个消息交付给已知受众来推进业务目标时，此模式即适用。 它与事件触发的消息传递（响应实时行为事件）和多步骤协调的历程不同，多步骤协调的历程随时间通过多个接触点引导用户档案。 批量激活是最简单的营销活动模式，也是出站消息传递用例最常见的起点。

## 主要业务目标

本节介绍批量出站消息激活支持的主要业务目标。

### 提高电子邮件和营销活动参与度

**描述：**&#x200B;通过优化的内容和定位，提高打开率、点进率和整体促销活动响应率。

**KPI：**&#x200B;打开率、参与度、转化率

### 增加收入及销售额

**描述：**&#x200B;通过优化的数字渠道、营销活动和客户历程推动总收入增长。

**KPI：**&#x200B;转化率、递增收入、平均订单值

**相关业务目标：** [增加收入和销售](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

### 简化活动执行

**描述：**&#x200B;通过模板、自动化和标准化流程缩短Campaign构建时间并简化多渠道Campaign交付。

**KPI：**&#x200B;上市速度、效率、准时完成百分比

## 战术用例示例

以下情形说明了批量出站消息激活的常见应用。

- **销售公告或促销电子邮件爆炸** — 在预定日期向符合条件的客户群广播促销优惠
- **产品发布推送通知** — 通过推送通知感兴趣的客户有关新产品可用性的信息
- **新闻稿或摘要电子邮件** — 向订阅者受众定期提供内容汇总
- **活动注册邀请** — 邀请符合条件的潜在客户参加网络研讨会、会议或面对面活动
- **订阅续订提醒电子邮件** — 提醒即将续订的客户采取行动
- **忠诚度计划里程碑通知** — 祝贺成员达到忠诚度等级或点阈值
- **特定call-to-action电子邮件** — 推动目标操作，如完成购买、更新首选项或注册程序
- 针对限时优惠或限时优惠的&#x200B;**短信促销活动** — 通过短信向已选择启用的受众发送紧急限时促销活动

## 关键绩效指标

下表定义了用于衡量促销活动效果的KPI。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 投放率 | 成功发送给收件人的邮件百分比 | 已投放/已发送x 100 |
| 打开率 | 收件人打开的已投放邮件的百分比 | 独特打开次数/交付次数x 100 |
| 点进率(CTR) | 点击了链接的已投放消息的百分比 | 独特点击次数/交付次数x 100 |
| 点击打开率(CTOR) | 已单击链接的已打开消息的百分比 | 独特点击次数/独特打开次数x 100 |
| 转化率 | 完成所需操作的收件人百分比 | 转化/已交付x 100 |
| 取消订阅率 | 接收消息后取消订阅的收件人百分比 | 取消订阅/已交付x 100 |
| 跳出率 | 无法投放的消息百分比 | 退回数/发送次数x 100 |
| 每封发送电子邮件的收入 | 归因于营销活动的收入除以发送的消息 | 总收入/已发送 |

## 应用程序

以下应用程序用于实现此模式。

- **[!DNL Adobe Journey Optimizer] (AJO)** — 消息创作、渠道配置、活动执行、历程编排、内容实验、频率规则和报表
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 受众评估、同意和治理实施
- **[!DNL Adobe Experience Platform] (AEP)** — 配置文件存储、身份服务、架构、数据集、数据收集

## 相关文档

此部分提供按主题组织的[!DNL Experience League]文档的完整链接。

### 营销活动

- [开始使用营销活动](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [创建营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [API触发的营销活动](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### 历程

- [历程入门](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [读取受众历程](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### 渠道配置

- [电子邮件配置入门](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [创建 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP预热计划](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [电子邮件表面设置](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [配置短信渠道](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [配置推送通知渠道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [管理禁止列表](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 消息创作和个性化

- [创建电子邮件](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/email/create-email)
- [设计电子邮件内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [使用电子邮件Designer内容组件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [导入电子邮件内容或对其进行编码](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/code-content)
- [添加个性化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization语法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [辅助函数](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [动态内容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### 内容管理

- [使用电子邮件模板](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用内容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [预览和测试内容](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [发送电子邮件校样](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [电子邮件渲染](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)

### 内容试验

- [内容体验入门](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [创建内容试验](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [内容试验报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [统计计算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### 频率和冲突管理

- [频率规则](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [业务规则概述](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [冲突和优先级管理入门](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [优先级分数](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [识别潜在冲突](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [历程上限和仲裁](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### 受众和分段

- [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home)
- [区段生成器UI指南](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/segment-builder)
- [流式客户细分](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [边缘分段](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/methods/edge-segmentation)
- [受众构成](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language参考](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/pql/overview)

### 报告

- [营销活动实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [营销活动全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [历程实时报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [历程全局报告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA集成指南](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### 数据治理和同意

- [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home)
- [数据使用标签概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/labels/overview)
- [同意和偏好设置字段组](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/field-groups/profile/consents)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### 数据建模和标识

- [XDM系统概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/home)
- [架构组合基础](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/schema/composition)
- [Identity服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home)
- [合并策略概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/merge-policies/overview)

### 护栏

- [Journey Optimizer护栏](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)
- [摄取护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/ingestion/guardrails)

### 教程和快速入门

- [Journey Optimizer入门](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/get-started/get-started)
- [创建您的第一个营销活动](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [创建您的第一个历程](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/orchestrate-journeys/journey)
