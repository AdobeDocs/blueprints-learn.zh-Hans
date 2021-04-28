---
title: 联机/脱机Audience Activation蓝图
description: 线上/线下 Audience Activation。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 24b6ffe3021389d33e84688a8f1a90711ca4b772
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 联机/脱机Audience Activation蓝图

将线下属性和事件（如线下订单、交易、CRM 或忠诚度数据）与线上行为结合使用，实现线上定位和个性化。

将受众激活到基于用户档案的已知目的地（如电子邮件提供商、社交网络和广告目的地）。

## 用例

* 受众定位，针对社交和广告目的地上的已知受众。
* 具有线上和线下属性的线上个性化。
* 激活已知渠道（如电子邮件和短信）的受众。

## 应用程序

* Adobe Experience Platform
* [!UICONTROL 实时客户数据平台]

## 架构

<img src="assets/onoff.svg" alt="联机/脱机Audience Activation蓝图的参考体系结构" style="border:1px solid #4a4a4a" />

## 护栏

* [用户档案和区段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)

### 细分评估和激活的保证

| 分段类型 | 频率 | 吞吐量 | 延迟（区段评估） | 延迟(区段激活) | 激活有效负荷 |
|---|---|---|---|---|---|
| 边缘分割 | 边缘分割目前处于测试阶段，允许在Experience Platform Edge Network上评估有效的实时分割，以便通过Adobe Target和Adobe Journey Optimizer实时、同一页面决策。 |  | ~100毫秒 | 可立即在Adobe Target中进行个性化，在Edge用户档案中进行用户档案查找，并通过基于Cookie的目标进行激活。 | 受众边缘上可用于用户档案查找和基于Cookie的目标的成员资格。<br>受众会员资格和用户档案属性适用于Adobe Target和Journey Optimizer。 |
| 流传输区段 | 每次将新的流事件或记录引入实时客户用户档案，且区段定义是有效的流区段。 <br>有关流细分 [标准](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans) 的指导，请参阅细分文档 | 每秒最多1500事件。 | ~ p95 &lt;5分钟 | 流目标：流式受众会员资格在大约10分钟内激活，或根据目标的要求进行微批处理。<br>计划目标：流式受众成员关系会根据计划的目标投放时间批量激活。 | 流目标：受众成员关系更改、标识值和用户档案属性。<br>计划目标：受众成员关系更改、标识值和用户档案属性。 |
| 增量细分 | 自上次增量或批量细分评估以来，每小时一次新数据被引入实时客户用户档案。 |  |  | 流目标：增量受众会员资格在大约10分钟内激活，或根据目标的要求进行微批量激活。<br>计划目标：增量受众成员关系将根据计划的目标投放时间批量激活。 | 流目标：受众成员资格更改和身份值。<br>计划目标：受众成员关系更改、标识值和用户档案属性。 |
| 批分段 | 每天根据预定的系统集计划进行一次，或通过API手动启动的点对点。 |  | 每个作业大约1小时，存储容量高达10 TB，每个作业2小时，存储容量为10 TB到100 TB，用户档案存储容量为10 TB。 批区段作业绩效取决于数量用户档案、用户档案大小和要评估的区段数。 | 流目标：在基于目的地的需求的分段评估或微批处理的约10个完成内，激活批受众会员资格。<br>计划目标：批受众成员关系将根据计划的目标投放时间激活。 | 流目标：受众成员资格更改和身份值。<br>计划目标：受众成员关系更改、标识值和用户档案属性。 |

### 跨应用程序受众共享的护栏

| 受众应用程序集成 | 频率 | 吞吐量/卷 | 延迟（区段评估） | 延迟(区段激活) |
|---|---|---|---|---|
| 实时客户数据平台到Audience Manager | 取决于分段类型 — 请参阅上面的分段护栏表。 | 取决于分段类型 — 请参阅上面的分段护栏表。 | 取决于分段类型 — 请参阅上面的分段护栏表。 | 在完成细分评估后几分钟内。<br>在实时受众平台和Audience Manager之间进行初始客户配置同步大约需要4小时。<br>在4小时内实现的任何受众会员资格将作为“现有”受众会员资格写入后续批分段作业的Audience Manager。 |
| Adobe Analytics到Audience Manager |  | 默认情况下，每个Adobe Analytics报表包最多可共享75个受众。 如果使用Audience Manager许可证，则对Adobe Analytics与Adobe Target或Adobe Audience Manager与Adobe Target之间可共享的受众数量没有限制。 |  |  |
| Adobe Analytics到实时客户数据平台 | 当前不可用 | 当前不可用 | 当前不可用 | 当前不可用 |





## 实施步骤

1. 在 Experience Platform 中配置架构和数据集。
1. 在架构上配置正确的身份和身份命名空间，以确保摄入的数据可以拼接到统一的用户档案中。
1. 为用户档案启用架构和数据集。
1. 将数据引入 Platform。
1. 设置[!UICONTROL 实时客户数据平台]在Experience Platform和Audience Manager之间共享区段，以便在Experience Platform中定义的受众共享给Audience Manager。
1. 在 Experience Platform 中创作区段，以批次或流方式评估。系统自动确定以批次还是流式评估区段。
1. 配置目的地，以共享用户档案属性和受众成员到所需目的地。

## 实施注意事项

* 要将用户档案数据共享到目的地，您需要在目的地有效负荷中包含目的地使用的特定身份值。对于目标目标，任何必需的标识都必须被引入平台，并配置为[!UICONTROL 实时客户用户档案]的标识。

* 对于从 Experience Platform 到 Audience Manager 共享受众的激活情况，[!UICONTROL 实时客户档案]中包含的所有身份都共享给 Audience Manager。当所需目的地身份包括在[!UICONTROL 实时客户档案]中时，或者在[!UICONTROL 实时客户档案]中的身份可以与在 Audience Manager 中链接的所需目的地身份相关时，可以通过 Audience Manager 目的地共享来自 Experience Platform 的受众。

## 相关文档

* [实时客户数据平台产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/real-time-customer-data-platform.html)
* [用户档案和细分指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [分段文档](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [目的地文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hans)

## 相关视频和教程

* [实时客户数据平台概述](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hans)
* [[!UICONTROL 实时客户数据平台演示]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hans)
* [创建区段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hans)
