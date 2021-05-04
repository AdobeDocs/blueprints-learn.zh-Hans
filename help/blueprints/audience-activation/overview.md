---
title: 受众和用户档案激活
description: 通过 Real-time Customer Data Platform 交付受众激活且以个人资料为中心的客户体验。
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: 58368eb06b9bbd6c332424bdcfa2789dde7d4c2f
workflow-type: tm+mt
source-wordcount: '1201'
ht-degree: 16%

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

### 瓜德拉伊图

<img src="assets/activation_guardrails.svg" alt="受众和用户档案激活蓝图的护栏图" style="border:1px solid #4a4a4a" />

* [用户档案和区段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)

### 细分评估和激活的保证

| 分段类型 | 用例 | 频率 | 吞吐量 | 延迟（区段评估） | 延迟(区段激活) | 激活有效负荷 |
|--------------------------|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 边缘分割 | Web/移动个性化（同一页/下一页） | 边缘分段目前处于测试阶段，但尚未普遍可用。 | - | 大约100毫秒 | 目标和Journey Optimizer:<ul><li>在同一个个性化请求中立即可用。</li></ul><br>基于Cookie的目标：<ul><li>可供下一页决策使用。</li></ul> | 边缘用户档案查找(目标和Journey Optimizer):<ul><li>受众会员资格</li><li>用户档案属性</li></ul><br>基于Cookie的目标：<ul><li>受众会员资格</li></ul> |
| 流传输区段 | 基于触发器的营销（流） | 每次将新的流事件或记录引入实时客户用户档案，且区段定义是有效的流区段。 <br>有关流细分标准细分文档的指导，请参 [阅细分文档](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans) | 每秒最多1500事件。 | 大约5分钟，第95页 | 流目标：<ul><li>距离Audience Manager和目标约1分钟</li><li>大约10分钟到外部目标或根据目标进行的微批。</li></ul><br>计划目标：<ul><li>根据计划的目标投放时间批量激活到外部目标。</li></ul> | 流目标： <ul><li>受众会员资格更改</li><li>标识值</li><li>用户档案属性</li></ul><br>计划目标：<ul><li>受众会员资格更改</li><li>标识值</li><li>用户档案属性</li></ul> |
| 增量细分 | <li>批处理消息<li>定位活动和体验 | 自上次增量或批量细分评估以来，每小时一次新数据被引入实时客户用户档案。 | 不适用 | 取决于用户档案数、用户档案大小和要评估的区段数。 | 流目标：<ul><li>距离Audience Manager和目标约1分钟</li><li>大约10分钟到外部目标或根据目标进行的微批。</li></ul><br>计划目标：<ul><li>根据计划的目标投放时间批量激活到外部目标。</li></ul> | 流目标： <ul><li>受众会员资格更改</li><li>标识值</li></ul><br>计划目标：<ul><li>受众会员资格更改</li><li>标识值</li><li>用户档案属性</li></ul> |
| 批分段 | <ul><li>批处理消息</li><li>定位活动和体验</li></ul> | 每天根据预定的系统集计划进行一次，或通过API手动启动的点对点。 | 不适用 | 取决于用户档案数、用户档案大小和要评估的区段数。<ul><li>每个作业大约1小时，最大可容纳10 TB的用户档案存储</li><li>每作业2小时，容量为10 TB到100 TB用户档案存储。</li></ul> | 流目标：<ul><li>距离Audience Manager和目标约1分钟</li><li>大约10分钟到外部目标或根据目标进行的微批。</li></ul><br>计划目标：<ul><li>根据计划的目标投放时间批量激活到外部目标。</li></ul> | 流目标： <ul><li>受众会员资格更改</li><li>标识值</li></ul><br>计划目标：<ul><li>受众会员资格更改</li><li>标识值</li><li>用户档案属性</li></ul> |

### 跨应用程序受众共享的护栏

|受众应用程序集成 |用例 |频率 |吞吐量/卷 |延迟（区段评估） |延迟(区段激活) |
|-||-||-||-||
|实时客户数据平台到Audience Manager |利用已知的用户档案受众丰富第三方广告 |取决于分段类型 — 请参阅上面的分段护栏表。 |取决于分段类型 — 请参阅上面的分段护栏表。 |取决于分段类型 — 请参阅上面的分段护栏表。 | <ul><li>在完成细分评估后几分钟内。</li><li>RTCDP和AAM之间的初始受众配置同步大约需要4小时。</li><li>在4小时内实现的任何受众会员资格将作为“现有”受众会员资格写入后续批分段作业的AAM。</li></ul> |
| Adobe Analytics到Audience Manager |使用基于粒度行为的受众丰富第三方广告 |  |默认情况下，每个Adobe Analytics报表包最多可共享75个受众。 如果使用Audience Manager许可证，则没有限制。 |  |  |
| Adobe Analytics到实时客户数据平台 |当前不可用。 |当前不可用 |当前不可用 |当前不可用 |当前不可用 |


### 激活属性和身份

* [!UICONTROL 实时受众数据平台可] 以激活成员资格，以及属性和身份更改，这些更改针对属于为激活选择的区段的用户档案。如果您的目标是激活属性或身份，则必须定义一个全局区段，其中包含所有用户档案，这些属性和身份更新都将发送到该区段。 此时，您可以选择要作为目标配置的一部分激活的区段和所需属性。
* 请注意，批处理目标不支持激活仅属性更改事件。 可以随选定的受众属性一起发送完整或增量的激活成员关系，但您无法通过批处理目标激活仅属性更改事件。

### 将批处理区段激活到流化目标

* 支持将批量段激活到流目标。 在区段作业完成后，批处理区段作业会将消息放在管道上以进行流激活

### 将流区段激活为批处理目标

* 支持流式段激活到批处理目标。 批目标计划根据批目标计划导出用户档案段成员关系。 这包括通过流和批处理方法确定的段成员关系。

### 激活体验事件

* 不支持激活原始体验事件。 要根据体验事件进行激活，必须使用包含或排除体验事件逻辑的必要规则创建区段。 这会创建一个根据体验事件定义的细分，并且可以激活区段成员身份作为激活原始体验事件的代理。 还可考虑使用[!UICONTROL 启动服务器端]激活通过SDK收集的原始体验事件。


## 相关博客帖子

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
