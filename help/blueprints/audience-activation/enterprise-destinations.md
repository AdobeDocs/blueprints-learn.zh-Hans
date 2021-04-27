---
title: 受众和用户档案激活到企业目标Blueprint
description: 受众和用户档案激活到企业目标
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: 2f35195b875d85033993f31c8cef0f85a7f6cccc
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 15%

---

# 受众和用户档案激活到企业目标Blueprint

从[!UICONTROL 实时客户数据平台]共享用户档案和受众更改以及流式或批量事件到企业数据存储和应用程序。 这些用户档案和受众事件可用于向客户发起销售或支持行动，例如跟踪放弃的应用程序流程或网络研讨会注册，或使用[!UICONTROL 实时客户数据平台]的最新客户属性和智能更新企业应用程序。

## 用例

* 用户档案和受众激活到云存储目标，或用于企业跟踪、存储、分析和激活客户数据和洞察的流目标。

## 应用程序

* Adobe Experience Platform 激活

## 架构

<img src="assets/enterprise_destination.svg" alt="企业激活方案的参考体系结构" style="border:1px solid #4a4a4a" />

## 护栏

[用户档案和区段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)

### 细分评估和激活的保证

|分段类型 |频率 |吞吐量 |延迟（区段评估） |延迟(区段激活) |激活负载 |
|-||-||-||-||
|边缘细分 |边缘分割目前处于测试阶段，允许在Experience Platform Edge Network上评估有效的实时分割，以便通过Adobe Target和Adobe Journey Optimizer实时、同一页面决策。 |  | ~ 100毫秒 |可立即在Adobe Target中进行个性化、在Edge用户档案中进行用户档案查找，以及通过基于Cookie的目标进行激活。 |受众边缘上可用于用户档案查找和基于Cookie的目标的会员资格。<br>受众会员资格和用户档案属性适用于Adobe Target和Journey Optimizer。|
|流细分 |每次新的流事件或记录被引入实时客户用户档案，且区段定义是有效的流区段时。 <br>有关流细分 [标准](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans) 的指导，请参阅细分文档 |每秒最多1500个事件。| ~ p95 &lt;5分钟 |流目标：流式受众会员资格在大约10分钟内激活，或根据目标的要求进行微批处理。<br>计划目标：流式受众成员关系会根据计划的目标投放时间批量激活。|流目标：受众成员关系更改、标识值和用户档案属性。<br>计划目标：受众成员关系更改、标识值和用户档案属性。|
|增量分段 |自上次增量或批量细分评估以来，每小时一次新数据被引入实时客户用户档案。 |  |  |流目标：增量受众会员资格在大约10分钟内激活，或根据目标的要求进行微批量激活。<br>计划目标：增量受众成员关系将根据计划的目标投放时间批量激活。|流目标：受众成员资格更改和身份值。<br>计划目标：受众成员关系更改、标识值和用户档案属性。|
|批分段 |基于预定的系统集计划每天一次，或通过API手动启动点对点。 |  |每个作业大约1小时(最大为10 TB的用户档案存储大小)，每个作业2小时(最大为10 TB至100 TB的用户档案存储大小)。 批区段作业绩效取决于数量用户档案、用户档案大小和要评估的区段数。 |流目标：在基于目的地的需求的分段评估或微批处理的约10个完成内，激活批受众会员资格。<br>计划目标：批受众成员关系将根据计划的目标投放时间激活。|流目标：受众成员资格更改和身份值。<br>计划目标：受众成员关系更改、标识值和用户档案属性。 |



## 实施步骤

1. 为要摄取的数据创建模式。
1. 为要摄取的数据创建数据集。
1. 在架构上配置正确的身份和身份命名空间，以确保摄入的数据可以拼接到统一的用户档案中。
1. 启用模式和数据集以进行用户档案处理。
1. 配置任何数据获取源。
1. 在Experience Platform中创作区段，以批量或流形式进行评估。 系统自动确定以批次还是流式评估区段。
1. 配置目的地，以共享用户档案属性和受众成员到所需目的地。

## 实施注意事项

激活属性和身份

* [!UICONTROL 实时受众数据平台可] 以激活成员资格，以及属性和身份更改，这些更改针对属于为激活选择的区段的用户档案。如果您的目标是激活属性或身份，则必须定义一个全局区段，其中包含所有用户档案，这些属性和身份更新都将发送到该区段。 此时，您可以选择要作为目标配置的一部分激活的区段和所需属性。
* 请注意，批处理目标不支持激活仅属性更改事件。 可以随选定的受众属性一起发送完整或增量的激活成员关系，但您无法通过批处理目标激活仅属性更改事件。

将批处理区段激活到流化目标

* 支持将批量段激活到流目标。 在区段作业完成后，批处理区段作业会将消息放在管道上以进行流激活

将流区段激活为批处理目标

* 支持流式段激活到批处理目标。 批目标计划根据批目标计划导出用户档案段成员关系。 这包括通过流和批处理方法确定的段成员关系。

激活体验事件

* 不支持激活原始体验事件。 要根据体验事件进行激活，必须使用包含或排除体验事件逻辑的必要规则创建区段。 这会创建一个根据体验事件定义的细分，并且可以激活区段成员身份作为激活原始体验事件的代理。 还可考虑使用[!UICONTROL 启动服务器端]激活通过SDK收集的原始体验事件。

## 相关文档

* [目的地文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hans)
* [云存储目标概述](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [HTTP目标](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [实时客户数据平台产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/real-time-customer-data-platform.html)
* [用户档案和细分指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [分段文档](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## 相关视频和教程

* [实时客户数据平台概述](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hans)
* [[!UICONTROL 实时客户数据平台演示]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hans)
* [创建区段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hans)
