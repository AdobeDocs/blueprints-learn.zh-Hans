---
title: '[!DNL Journey Optimizer] — 触发的消息处理和Adobe Experience Platform Blueprint'
description: 使用 Adobe Experience Platform 作为流式传输数据、客户档案和分段的中心枢纽，执行触发的消息和体验。
solution: Journey Optimizer
exl-id: 70573eb9-cd69-4fe6-b2ae-dae81665a308
TQID: https://experienceleague.adobe.com/MuodOvJ52G9lmUAmsuj06q1aTXkRg7W0Bj6nxLp96N8
product_v2: id: cb954087-f4fc-4456-afb9-e939cabcdc79
feature_v2: id: a653cc2e-bc85-4353-a306-399e5b247978id: d998adac-2f81-400b-a669-d07bb196e4ebid: fe338112-e2ce-4876-8989-fc4d497613f1id: fe96aceb-8194-4a8a-a6b0-75302d02804d
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: e0eb8757-182f-49f3-94a4-1587d16f5094id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 357
ht-degree: 12%

---

# [!DNL Journey Optimizer] - 历程Blueprint

>[!TIP]
>此Blueprint还作为[用例模式](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)在Campaign Management &amp; Orchestration下提供。

历程是实时的事件驱动工作流，可根据个别客户行为提供个性化的多步骤体验。 它们支持广泛的渠道，包括电子邮件、短信、推送通知、应用程序内消息传送、基于代码的体验以及基于自定义API的集成，从而让品牌商能够跨其首选接触点根据上下文吸引客户。

<br>

## 架构

<img src="images/ajo-journeys-architecture.svg" alt="参考架构Adobe Journey Optimizer - 历程 Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 历程的体系结构注意事项

- **个人资料新鲜度**： 历程依赖客户个人资料的实时更新。 确保将馈送到Adobe Experience Platform (AEP)的数据源配置为低延迟摄取，以保持用户档案准确性。
- **可扩展事件处理：**&#x200B;确保基础结构可以处理大量历程触发器和消息传递。
- **模块化集成：**&#x200B;设计API和自定义操作以将AJO与外部系统连接起来以进行动态个性化。
- **身份解析**：跨设备和渠道准确拼接客户身份至关重要。 未对齐身份可能会导致历程中断或定向错误。
- **区段资格计时**：基于受众的历程取决于区段成员资格。 了解评估区段的频率以及该时间对历程进入和个性化有何影响。
- **历程进入条件**：配置文件必须满足特定条件才能进入旅程。 应仔细设计这些条件，以避免意外排除或重叠。
- **受众评估和延迟**：读取受众步骤取决于Adobe Experience Platform中的区段评估，该评估可能不会实时进行。 架构师的历程了解评估频率和延迟，以避免受众资格鉴定延迟，并确保及时个性化。

<br>

## 护栏

[[!DNL Journey Optimizer]护栏产品链接](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[护栏和端到端延迟指导](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

<br>

## 相关文档

- [[!DNL Experience Platform]文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hans)
- [[!DNL Experience Platform]标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)
- [[!DNL Experience Platform Mobile SDK]文档](https://experienceleague.adobe.com/docs/mobile.html)
- [[!DNL Journey Optimizer]文档](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html)
- [[!DNL Journey Optimizer]产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-journey-optimizer.html)
