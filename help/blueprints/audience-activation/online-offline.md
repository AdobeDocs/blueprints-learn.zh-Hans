---
title: 联机/脱机Audience Activation蓝图
description: 联机/脱机Audience Activation。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 009a55715b832c3167e9a3413ccf89e0493227df
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 0%

---

# 联机/脱机Audience Activation蓝图

将线下属性和事件（如线下订单、交易、CRM或忠诚度数据）与在线行为结合使用，实现在线定位和个性化。

激活对基于用户档案的已知目标（如电子邮件提供商、社交网络和广告目标）的受众。

## 用例

* 受众定位，针对社交和广告目标上的已知受众。
* 具有线上和线下属性的在线个性化。
* 激活对已知渠道（如电子邮件和短信）的受众

## 应用程序

* Adobe Experience Platform
* [!UICONTROL 实时客户数据平台]

## 架构

<img src="assets/onoff.svg" alt="联机/脱机Audience Activation蓝图的参考体系结构" style="border:1px solid #4a4a4a" />

## 瓜德雷尔

* [用户档案和细分指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* 基于预定计划，每天运行一次批处理段作业。 然后，在计划的目标投放之前运行区段导出作业。 请注意，批处理段作业和目标投放作业分别运行。 批处理段作业和导出作业性能取决于用户档案数、用户档案大小和要评估的段数。
* 在流数据到达用户档案并立即将段成员关系写入用户档案并发送事件以供应用程序订阅时，将在几分钟内评估流数据段作业。
* 流式区段成员资格会立即对流式目标执行，并在单个区段成员事件或微批多个用户档案事件中提供，具体取决于目标的摄取模式。 对于通过计划批处理段投放交付的流中评估的任何段，计划目标将在投放之前从用户档案启动段导出作业。
* 对于将[!UICONTROL 实时客户数据平台]区段成员资格共享到Audience Manager，流化区段在几分钟内发生，批量分段的批量区段评估完成后在几分钟内发生。
* 从Experience Platform到Audience Manager共享的细分在细分实现后的几分钟内即可共享 — 无论是通过流评估还是批评估方法。 在最初创建区段后，Experience Platform和Audience Manager之间会进行初始区段配置同步，约4小时后，Experience Platform区段成员关系可开始在Audience Manager用户档案中实现。 在配置Experience Platform和Audience Manager受众共享之前或受众元数据从Experience Platform同步到Audience Manager之前实现的受众成员资格在共享“现有”区段成员资格的以下区段作业之前，不会在Audience Manager中实现。
* 批处理区段作业中的批处理或流式目标作业可以共享用户档案属性更新和区段成员关系。
* 到流目标的流分段作业仅共享区段成员资格更新。

## 实施步骤

1. 在Experience Platform中配置模式和数据集。
1. 在模式上配置正确的身份和身份命名空间，以确保摄取的数据可以拼接到统一的用户档案中。
1. 启用模式和数据集以进行用户档案。
1. 将数据引入平台。
1. 设置[!UICONTROL 实时客户数据平台]在Experience Platform和Audience Manager之间共享区段，以便在Experience Platform中定义的受众共享给Audience Manager。
1. 在Experience Platform中创作区段，以批量或流方式评估。 系统自动确定将段评估为批还是流。
1. 配置目标，以共享用户档案属性和受众成员关系到所需目标。

## 实施注意事项

* 要将用户档案数据共享到目标，您需要在目标有效负荷中包含目标使用的特定标识值。 对于目标目标，任何必需的标识都必须被引入平台，并配置为[!UICONTROL 实时客户用户档案]的标识。

* 对于从Experience Platform到Audience Manager共享受众的激活情况， [!UICONTROL 实时客户用户档案]中包含的所有标识都共享给Audience Manager。 当所需目标标识包括在[!UICONTROL 实时客户用户档案]中时，或者在[!UICONTROL 实时客户用户档案]中的标识可以与在Audience Manager中链接的所需目标标识相关时，可以通过Audience Manager目标共享来自受众的Experience Platform。

## 相关文档

* [[!UICONTROL 实时客户数据平台产] 品说明](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [用户档案和细分指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [分段文档](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [目标文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## 相关视频和Tutorials

* [[!UICONTROL 实时客户数据平] 台](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [实时客 [!UICONTROL 户数据平台演示]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [创建区段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
