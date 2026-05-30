---
title: 购买基于群组的营销和历程管理
description: 了解如何开发帐户级别的历程，使潜在客户有资格加入购买组，以提高B2B营销效率。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 2bf57f67-80c8-4368-98d2-05706427772d
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 1%

---

# 购买基于群组的营销和历程管理

本指南介绍了基于购买群组的营销和历程管理用例模式，该模式使用[!DNL Adobe Journey Optimizer B2B Edition]和[!DNL Real-Time CDP B2B Edition]通过购买群组管理实施帐户级别的历程编排。 它专为需要了解此模式的用途、支持的业务目标、支持的战术用例以及涉及的Adobe应用程序的解决方案架构师、营销技术人员和实施工程师而设计。

与人员级别的历程模式不同，此模式在帐户级别运行，确定与解决方案兴趣相关的购买组的个人商机，在购买组级别评分参与度，并编排多步骤帐户历程，将帐户通过管道阶段进展到销售准备情况。

## 用例模式

**购买基于群组的营销和历程管理**

开发客户级别的历程，使潜在客户有资格加入购买群体，以提高B2B营销效率。

**执行计划：**&#x200B;客户识别>购买组定义>潜在客户资格>客户历程执行>参与度评分>报告

## 用例概述

B2B组织面临一个根本性的挑战：购买决策很少由一个人做出。 复杂的B2B购买涉及多个利益相关者 — 决策者、影响者、支持者、预算持有人和技术评估者 — 他们共同组成一个“购买群体”。 传统的基于潜在客户的营销方式会单独对待每个人，忽略了一个关键信号，即客户中适当的角色组合是否参与并准备购买。

购买基于群组的营销和历程管理可通过将编排单位从个人商机转移到帐户和购买群组来解决此问题。 通过使用该模式，B2B营销人员可以定义解决方案兴趣（正在销售的产品或服务），创建购买组模板，以指定购买决策所需的角色，根据这些角色确定传入商机的资格，在购买组级别对参与度进行评分，以及编排响应购买组完整性和就绪信号的客户历程。

期望的结果是提高渠道质量和速度：只有当客户中的适当人员参与进来，并且买方小组已充分完成时，营销人员才会将客户提供给销售人员，从而减少浪费的销售工作并加快交易进度。

## 主要业务目标

此用例模式支持以下业务目标。

### 改进潜在客户资格鉴定和转化

通过评分、培养和个性化的跟进，提高销售线索质量并加快管道进度。

**KPI：**&#x200B;潜在客户转化、潜在客户/潜在客户转化、效率

[了解有关改进潜在客户资格和转化的更多信息](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### 增加商机开发

通过表单、事件、内容和多渠道参与，为销售渠道生成更多符合条件的潜在客户。

**KPI：**&#x200B;潜在客户、每个潜在客户的成本、潜在客户转化

[了解有关提高商机开发率的更多信息](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### 增加收入和销售

通过优化的数字渠道、营销活动和客户历程推动总收入增长。

**KPI：**&#x200B;收入增长、管道周转率、交易完成率

[了解有关增加收入和销售额的更多信息](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

## 战术用例示例

以下是可以应用此模式的特定方案。

- **特定于解决方案的购买群组资格** — 使用指定所需角色（经济购买者、技术评估人员、冠军、最终用户）的角色模板为每个产品线（例如，“企业CRM”、“数据平台”、“安全套件”）定义购买群组，并根据这些角色确认CRM和营销自动化系统中的潜在客户。
- **用于管道加速的帐户历程** — 编排一个多步骤帐户历程，该历程向购买组中未充分参与的角色发送有针对性的培训电子邮件，在达到参与阈值时触发销售警报，并将帐户过渡至销售就绪阶段。
- **购买团体完整性促销活动** — 识别购买团体缺少角色的帐户（例如，未识别经济购买者），并启动定向的客户获取促销活动以吸引这些帐户中的正确角色。
- **交叉销售帐户历程** — 在初始交易完成后，为补充解决方案兴趣创建新的购买组，并协调客户历程，以培养扩展的购买委员会。
- **重新参与停滞的交易** — 检测购买团体参与分数已下降的帐户，并通过新内容、执行外联或活动邀请触发重新参与历程。
- **通过CRM见解进行销售和营销协调** — 直接在[!DNL Salesforce]或[!DNL Dynamics 365]内显示购买组状态、参与数据和帐户历程进度，以便销售代表能够实时查看符合营销条件的帐户。
- **事件驱动的购买群组更新** — 当潜在客户参加网络研讨会、下载白皮书、访问定价页面或请求演示时，自动更新购买群组会员资格和参与度分数。
- **多区域帐户协调** — 管理全球帐户中的购买组，其中不同的区域联系人担任不同的角色，统一不同地理区域的参与度评分。

## 关键绩效指标

以下KPI有助于衡量此用例模式的有效性。

| KPI | 描述 | 度量方法 |
| --- | --- | --- |
| 购买组完整率 | 已填写所有所需角色的购买组的百分比 | [!DNL AJO B2B] Analytics功能板：跟踪每个购买群组的角色覆盖率 |
| 购买团体参与度分数 | 购买组所有成员的总参与度分数 | [!DNL AJO B2B]参与度得分：个人级别得分汇总到购买团体 |
| 营销合格帐户(MQA)比率 | 达到营销资格阈值的帐户百分比 | 帐户历程退出标准：帐户正在过渡到“销售就绪”阶段 |
| 管道速度 | 从购买组创建到销售合格商机的平均时间 | CRM集成：跟踪从[!DNL AJO B2B]到CRM管道的暂存过渡 |
| 采购线索组资格率 | 成功获得购买群组角色资格的潜在客户百分比 | [!DNL AJO B2B]购买群组管理：合格与不合格的潜在客户比率 |
| 销售警报响应率 | 导致销售跟踪活动的销售警报百分比 | CRM销售分析：跟踪警报到活动的转换 |
| 帐户历程完成率 | 完成预期历程路径的帐户百分比 | [!DNL AJO B2B] Analytics功能板：历程完成量度 |
| 电子邮件参与率(B2B) | B2B培养电子邮件的打开率和点进率 | [!DNL AJO B2B]报告：电子邮件投放和参与量度 |

## 应用程序

在此用例模式中使用以下Adobe应用程序。

- **[!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])** — 编排帐户级别的历程，通过角色模板和解决方案兴趣来管理购买组，在人员和购买组级别对参与情况进行评分，作者B2B电子邮件内容，发送SMS消息，配置销售警报，并提供B2B分析功能板。
- **[!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])** — 从跨源B2B数据统一帐户配置文件，解析人员与帐户的关系，评估帐户级别的受众，配置特定于B2B的目标([!DNL Marketo Engage]、[!DNL LinkedIn]、CRM)，并跨B2B数据实施数据管理。

## 相关文档

以下资源提供了有关本指南中引用的应用程序和功能的更多详细信息。

### [!DNL AJO B2B Edition]

- [AJO B2B edition文档主页](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer-b2b/user/guide-overview)
- [购买群组概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [解决方案兴趣](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [角色模板](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [创建购买组](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)
- [购买群组阶段](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [帐户历程概述](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [帐户历程节点](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [销售警报电子邮件](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [CRM销售分析](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)

### B2B电子邮件和内容

- [B2B电子邮件创作](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [AJO B2B中的短信创作](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [用于电子邮件创作的AI助手](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### B2B分析和功能板

- [购买组仪表板](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [参与仪表板](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [智能仪表板](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [CJA B2B edition概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### [!DNL RT-CDP B2B Edition]

- [RT-CDP B2B edition概述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [Real-Time CDP中的B2B架构](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/rtcdp/schemas/b2b)
- [帐户受众](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/types/account-audiences)
- [Marketo Engage源连接器](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)

### 数据基础

- [XDM系统概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/xdm/home)
- [Identity服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/identity/home)
- [来源概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/sources/home)
- [分段服务概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/segmentation/home)

### 渠道配置

- [电子邮件配置入门](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [配置短信渠道](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### 数据治理和隐私

- [数据治理概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-governance/home)
- [高级数据生命周期管理](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/data-lifecycle/home)

### 目标

- [目的地概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/home)
- [目标目录](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/overview)
- [LinkedIn匹配受众目标](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/destinations/catalog/social/linkedin)

### 护栏

- [Real-Time Customer Profile护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/profile/guardrails)
- [分段护栏](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [摄取护栏](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/ingestion/guardrails)
- [Journey Optimizer护栏](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer/using/get-started/guardrails)

### 教程和快速入门

- [AJO B2B edition快速入门](https://experienceleague.adobe.com/zh-hans/docs/journey-optimizer-b2b/user/guide-overview)
- [RT-CDP B2B edition教程](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-tutorial)
