---
title: 受众和用户档案激活
description: 通过 Real-time Customer Data Platform 交付受众激活且以个人资料为中心的客户体验。
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: 9e0954334e8b8a8c5bf52651611e7afa165f6d21
workflow-type: tm+mt
source-wordcount: '1249'
ht-degree: 15%

---


# 受众和用户档案激活

受众和用户档案激活是在数据驱动营销世界中取得成功的关键。 但是，许多品牌仍然将精力集中在渠道优先激活上，这往往会带来不一致的覆盖范围和个性化。

通过渠道优先的方法，每个渠道都充当一个筒仓，个性化努力仅以该渠道上与品牌互动的客户为目标。此方法并不反映客户与跨多个不同接触点的品牌互动的现实。受众和用户档案激活使品牌能够将多个渠道的客户互动关联起来，从而提供可激活给所有渠道的集中用户档案和受众。

| Blueprint | 描述 | Experience Cloud 应用程序 |
|---|---|---|
| **[匿名 Audience Activation](anonymous.md)** | <ul><li>跨 Web 和广告渠道定位目标受众，以获取匿名和行为客户数据。</li><li>与第三方受众数据集成以提高个性化。</li></ul> | <ul><li>Adobe Audience Manager</li></ul> |
| **[线上/线下 Audience Activation](online-offline.md)** | <ul><li>激活到基于用户档案的已知目标，如电子邮件提供商、社交网络和广告目标。 </li><li>将离线属性和事件（如离线订单、交易、CRM或忠诚度数据）与在线行为结合使用，实现在线定位和个性化。</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL 实时客户数据平台]</li><li>Adobe Audience Manager（可选）</li></ul> |
| **[受众和用户档案激活到企业目标](enterprise-destinations.md)** | <ul><li>将用户档案和受众更改复制和更新到企业存储，以用于激活和报告使用案例。 </li></ul><ul><li>通过从[!UICONTROL 实时客户数据平台]到企业系统和应用程序的客户操作通知，向客户发起销售或支持操作。</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL 实时客户数据平台]</li><li>Experience Platform激活</li><li>Adobe Audience Manager（可选）</li></ul> |
| **[客户活动中心](customer-activity.md)** | <ul><li>为座席支持的交互（如支持和销售体验）提供更深入的消费者背景信息。通过对Experience Platform的用户档案查找，工程师可以接收有关消费者的更多上下文，例如最近购买、活动交互、倾向、受众会员资格，以及存储在实时客户用户档案中的其他属性和洞察。</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |

## 受众和用户档案激活蓝图的护栏

* [用户档案和区段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)

### 细分评估和激活的保证

|分段类型 |频率 |吞吐量 |延迟（区段评估） |延迟(区段激活) |激活负载 |
|-||-||-||-||
|边缘细分 |边缘分割目前处于测试阶段，允许在Experience Platform Edge Network上评估有效的实时分割，以便通过Adobe Target和Adobe Journey Optimizer实时、同一页面决策。 |  | ~ 100毫秒 |可立即在Adobe Target中进行个性化、在Edge用户档案中进行用户档案查找，以及通过基于Cookie的目标进行激活。 |受众边缘上可用于用户档案查找和基于Cookie的目标的会员资格。<br>受众会员资格和用户档案属性适用于Adobe Target和Journey Optimizer。|
|流细分 |每次新的流事件或记录被引入实时客户用户档案，且区段定义是有效的流区段时。 <br>有关流细分 [标准](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans) 的指导，请参阅细分文档 |每秒最多1500个事件。| ~ p95 &lt; 5分钟 |流目标：流式受众会员资格在大约10分钟内激活，或根据目标的要求进行微批处理。<br>计划目标：流式受众成员关系会根据计划的目标投放时间批量激活。|流目标：受众成员关系更改、标识值和用户档案属性。<br>计划目标：受众成员关系更改、标识值和用户档案属性。|
|增量分段 |自上次增量或批量细分评估后，每小时一次新数据被引入实时客户用户档案。 |  |  |流目标：增量受众会员资格在大约10分钟内激活，或根据目标的要求进行微批量激活。<br>计划目标：增量受众成员关系将根据计划的目标投放时间批量激活。|流目标：受众成员资格更改和身份值。<br>计划目标：受众成员关系更改、标识值和用户档案属性。|
|批分段 |基于预定的系统集计划每天一次，或通过API手动启动点对点。 |  |每个作业大约1小时，存储容量高达10TB，每个作业2小时，存储容量为10TB到100TB。 批区段作业绩效取决于数量用户档案、用户档案大小和要评估的区段数。 |流目标：在基于目的地的需求的分段评估或微批处理的约10个完成内，激活批受众会员资格。<br>计划目标：批受众成员关系将根据计划的目标投放时间激活。|流目标：受众成员资格更改和身份值。<br>计划目标：受众成员关系更改、标识值和用户档案属性。 |

### 跨应用程序受众共享的护栏

|受众应用程序集成 |频率 |吞吐量/卷 |延迟（区段评估） |延迟(区段激活) |
|-||-||-||
|实时客户数据平台到Audience Manager |取决于分段类型 — 请参阅上面的分段护栏表。 |取决于分段类型 — 请参阅上面的分段护栏表。 |取决于分段类型 — 请参阅上面的分段护栏表。 |在完成细分评估后的几分钟内。<br>在实时受众平台和Audience Manager之间进行初始客户配置同步大约需要4小时。<br>在4小时内实现的任何受众会员资格将作为“现有”受众会员资格写入后续批分段作业的Audience Manager。|
|实时客户数据平台到Ad Cloud |请注意，将受众从实时客户数据平台共享到Adobe Advertising Cloud需要Audience Manager。 同样，适用于向受众 Manager实时客户数据平台共享的保证将申请将实时客户数据平台受众集成到Advertising Cloud。 | - |-  | - |
| Adobe Analytics到实时客户数据平台 |当前不可用 |当前不可用 |当前不可用 |当前不可用 |
| Adobe Analytics到Audience Manager |-  |默认情况下，每个Adobe Analytics报表包最多可共享75个受众。 如果使用Audience Manager许可证，则对Adobe Analytics与Adobe Target或Adobe Audience Manager与Adobe Target之间可共享的受众数量没有限制。 | - |-  |


### 用于激活属性和身份的护栏

* [!UICONTROL 实时受众数据平台可] 以激活成员资格，以及属性和身份更改，这些更改针对属于为激活选择的区段的用户档案。如果您的目标是激活属性或身份，则必须定义一个全局区段，其中包含所有用户档案，这些属性和身份更新都将发送到该区段。 此时，您可以选择要作为目标配置的一部分激活的区段和所需属性。
* 请注意，批处理目标不支持激活仅属性更改事件。 可以随选定的受众属性一起发送完整或增量的激活成员关系，但您无法通过批处理目标激活仅属性更改事件。

将批处理区段激活到流化目标

* 支持将批量段激活到流目标。 在区段作业完成后，批处理区段作业会将消息放在管道上以进行流激活

将流区段激活为批处理目标

* 支持流式段激活到批处理目标。 批目标计划根据批目标计划导出用户档案段成员关系。 这包括通过流和批处理方法确定的段成员关系。

激活体验事件

* 不支持激活原始体验事件。 要根据体验事件进行激活，必须使用包含或排除体验事件逻辑的必要规则创建区段。 这会创建一个根据体验事件定义的细分，并且可以激活区段成员身份作为激活原始体验事件的代理。 还可考虑使用[!UICONTROL 启动服务器端]激活通过SDK收集的原始体验事件。


## 相关博客帖子

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
