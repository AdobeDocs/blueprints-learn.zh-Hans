---
title: 受众和用户档案激活到企业目标Blueprint
description: 受众和用户档案激活到企业目标
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: 8bcd82eac5e8837c3cd84524174cf5792d73ac6e
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 0%

---

# 受众和用户档案激活到企业目标Blueprint

将用户档案和受众更改复制和更新到企业存储，以用于激活和报告使用案例。

通过客户操作的通知，从实时客户数据平台到企业系统和应用程序，向客户发起销售或支持行动。

## 用例

* 用户档案和受众激活到云存储目标或流目标，以便企业跟踪、存储、分析和激活客户数据和洞察。

## 应用程序

* Adobe Experience Platform 激活

## 架构

<img src="assets/enterprise_destination.svg" alt="企业激活方案的参考体系结构" style="border:1px solid #4a4a4a" />

## 瓜德雷尔

[用户档案和细分指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

延迟和吞吐量阈值：

流细分：

* 流式分段最多需要5分钟，每秒最多可达1500个事件
* 最多11分钟，用于流式激活

批量分段：
每天一次，或通过API手动启动点对点

* 每个作业大约1小时，最大可容纳10 TB的用户档案存储
* 每个作业大约2小时，容量为10 TB到100 TB的用户档案存储

## 实施步骤

1. 为要摄取的数据创建模式
1. 为要摄取的数据创建数据集
1. 在模式上配置正确的身份和身份命名空间，以确保摄取的数据可以拼接到统一的用户档案中。
1. 启用模式和数据集以进行用户档案处理。
1. 配置任何源以获取数据
1. 在Experience Platform中创作区段，以批量或流方式评估。 系统自动确定将段评估为批还是流。
1. 配置目标，以共享用户档案属性和受众成员关系到所需目标。

## 实施注意事项

激活属性和身份

* 实时受众数据平台可以激活客户成员身份以及属性和身份更改，这些更改针对属于已选择用于激活的区段的用户档案。 同样，如果用例是激活属性和/或标识，则必须定义全局区段，该全局区段将包括所有要发送属性/标识更新的用户档案。 在此位置到位后，可选择要激活的区段和所需属性作为目标配置的一部分。
* 请注意，批处理目标不支持仅属性激活更改事件。 受众成员关系可以与选定的激活属性一起发送，但仅属性更改事件无法通过批处理目标激活。

批量区段激活到流目标

* 支持将批量段激活到流目标。 在区段作业完成后，批处理区段作业会将消息放在管道上以进行流激活

将区段激活流化到批处理目标

* 支持流式段激活到批处理目标。 批目标计划将根据批目标计划导出用户档案的段成员关系。 这包括通过流和批处理方法确定的段成员关系。

激活体验事件

* 激活原始体验事件目前不受支持。 要针对体验事件进行激活，必须使用包括/排除要针对的体验事件逻辑的必要规则来创建区段。 这会创建一个根据体验事件定义的细分 — 并且可以激活细分会员资格作为激活原始体验事件的代理。 还可以考虑利用Launch Server端来激活通过SDK收集的原始体验事件。

## 相关文档

* [目标文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)
* [Enterprise Cloud存储目标](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [HTTP目标](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [实时客户数据平台产品说明](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [用户档案和细分指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [分段文档](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## 相关视频和Tutorials

* [实时客户数据平台概述](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [实时客户数据平台演示](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [创建区段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
