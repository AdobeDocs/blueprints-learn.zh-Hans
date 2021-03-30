---
title: 联机/脱机Audience Activation方案
description: 联机/脱机Audience Activation。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
translation-type: tm+mt
source-git-commit: c4bd4bbd40f2ae6b9ab980c5274a6e2007d976d3
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---


# 联机/脱机Audience Activation方案

将线下属性和事件（如线下订单、交易、CRM或忠诚度数据）与在线行为结合使用，实现在线定位和个性化。

激活对基于用户档案的已知目标（如电子邮件提供商、社交网络和广告目标）的受众。

## 用例

* 受众定位，针对社交和广告目标上的已知受众。
* 具有线上和线下属性的在线个性化。
* 激活对已知渠道（如电子邮件和短信）的受众

## 应用程序

* Adobe Experience Platform
* 实时客户数据平台

## 架构

<img src="assets/onoff.svg" alt="联机/脱机Audience Activation方案的参考体系结构" style="border:1px solid #4a4a4a" />

## 瓜德雷尔

* [用户档案和细分指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* 基于预定计划，每天运行一次批处理段作业。 然后，在计划的目标投放之前运行区段导出作业。 请注意，批处理段作业和目标投放作业分别运行。 批处理段作业和导出作业性能取决于用户档案数、用户档案大小和要评估的段数。
* 在流数据到达用户档案并立即将段成员关系写入用户档案并发送事件以供应用程序订阅时，将在几分钟内评估流数据段作业。
* 流式区段成员资格会立即对流式目标执行，并在单个区段成员事件或微批多个用户档案事件中提供，具体取决于目标的摄取模式。 对于通过计划批处理段投放交付的流中评估的任何段，计划目标将在投放之前从用户档案启动段导出作业。
* 为了将RTCDP区段成员资格共享给Audience Manager，流式区段在几分钟内发生这种情况，批量分段的批量区段评估完成后几分钟内发生这种情况。
* 从Experience Platform到Audience Manager共享的细分在细分实现后的几分钟内即可共享 — 无论是通过流评估还是批评估方法。 在最初创建区段后，AEP和AAM之间会进行初始区段配置同步，约4小时后，AEP区段成员关系即可在AAM用户档案中开始实现。 在配置Experience Platform和Audience Manager受众共享之前或受众元数据从Experience Platform同步到Audience Manager之前实现的受众成员资格在共享“现有”区段成员资格的以下区段作业之前，不会在Audience Manager中实现。
* 批处理区段作业中的批处理或流式目标作业可以共享用户档案属性更新和区段成员关系。
* 到流目标的流分段作业仅共享区段成员资格更新。

## 实施步骤

1. 在Experience Platform中配置模式和数据集。
1. 在模式上配置正确的身份和身份命名空间，以确保摄取的数据可以拼接到统一的用户档案中。
1. 启用模式和数据集以进行用户档案。
1. 将数据引入平台。
1. 为在Experience Platform和Audience Manager之间实时共享客户平台细分，以便在Experience Platform中定义的要共享给Audience Manager的受众。
1. 在Experience Platform中创作区段，以批量或流方式评估。 系统自动确定将段评估为批还是流。
1. 配置目标，以共享用户档案属性和受众成员关系到所需目标。

## 实施注意事项

* 要将用户档案数据共享到目标，您需要在目标有效负荷中包含目标使用的特定标识值。 目标目标所需的任何标识都必须被引入平台并配置为实时客户用户档案的标识。

* 对于从Experience Platform到Audience Manager共享受众的激活情况， [!UICONTROL 实时客户用户档案]中包含的所有标识都共享给Audience Manager。 当所需目标标识包括在[!UICONTROL 实时客户用户档案]中时，或者在[!UICONTROL 实时客户用户档案]中的标识可以与在Audience Manager中链接的所需目标标识相关时，可以通过Audience Manager目标共享来自受众的Experience Platform。

## 相关文档

* [实时客户数据平台产品说明](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [用户档案和细分指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [分段文档](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [目标文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## 相关视频和Tutorials

* [实时客户数据平台概述](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [实时客户数据平台演示](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [创建区段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)