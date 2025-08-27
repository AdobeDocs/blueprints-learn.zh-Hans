---
title: '[!DNL Journey Optimizer] — 触发的消息处理和Adobe Experience Platform Blueprint'
description: 使用 Adobe Experience Platform 作为流式传输数据、客户档案和分段的中心枢纽，执行触发的消息和体验。
solution: Journey Optimizer
source-git-commit: 0a3ebcbc6029df46bd988cb8f15ecf838f80c3c9
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 9%

---

# [!DNL Journey Optimizer] - 历程Blueprint

Adobe Journey Optimizer历程是实时的事件驱动工作流，可根据个别客户行为提供个性化的多步骤体验。 它们支持广泛的渠道，包括电子邮件、短信、推送通知、应用程序内消息传送、基于代码的体验以及基于自定义API的集成，从而让品牌商能够跨其首选接触点根据上下文吸引客户。

<br>

## 架构

<img src="images/ajo-journeys-architecture.svg" alt="参考架构Adobe Journey Optimizer - 历程 Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 历程的体系结构注意事项

- **个人资料新鲜度**： AJO历程依赖客户个人资料的实时更新。 确保将馈送到Adobe Experience Platform (AEP)的数据源配置为低延迟摄取，以保持用户档案准确性。
- **可扩展事件处理：**&#x200B;确保基础结构可以处理大量历程触发器和消息传递。
- **模块化集成：**&#x200B;设计API和自定义操作以将AJO与外部系统连接起来以进行动态个性化。
- **身份解析**：跨设备和渠道准确拼接客户身份至关重要。 未对齐身份可能会导致历程中断或定向错误。
- **区段资格计时**：基于受众的历程取决于区段成员资格。 了解评估区段的频率以及该时间对历程进入和个性化有何影响。
- **历程进入条件**：配置文件必须满足特定条件才能进入旅程。 应仔细设计这些条件，以避免意外排除或重叠。
- **受众评估和延迟**：读取受众步骤取决于Adobe Experience Platform中的区段评估，该评估可能不会实时进行。 架构师的历程了解评估频率和延迟，以避免受众资格鉴定延迟，并确保及时个性化。

<br>

## 护栏

[[!DNL Journey Optimizer] 护栏产品链接](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[护栏和端到端延迟指导](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

<br>

## 相关文档

- [[!DNL Experience Platform] 文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
- [[!DNL Experience Platform] 标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
- [[!DNL Experience Platform Mobile SDK] 文档](https://experienceleague.adobe.com/docs/mobile.html)
- [[!DNL Journey Optimizer] 文档](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html)
- [[!DNL Journey Optimizer] 产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)