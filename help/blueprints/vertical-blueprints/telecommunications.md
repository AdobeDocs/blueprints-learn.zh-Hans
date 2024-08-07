---
title: 电信行业 — 用于触发式报文传送的Journey Optimizer
description: 实时为客户提供量身定制的交易，同时高效完成客户注册，以提升长期忠诚度。
solution: Journey Optimizer
kt: 9486
exl-id: fa4a6569-3972-4b97-91f1-7ca8ffd3c5b3
source-git-commit: cf7721ea01579182fdb200aad448be6fc94b34cf
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 85%

---

# 电信行业业务挑战

在实施此蓝图之前，电信公司的“添加新行”电子邮件营销活动取决于用户是否已经转化，并且仅在等待七天后检查是否已经转化。 满足这些标准后，将启动任何其他接触点。

必须解决这一限制，才能对希望在当前状态 7 天等待期之前添加线路的用户进行更及时的跟进。

## Adobe 方法

* Adobe Analytics 数据可标识未能转化为添加新线路的用户，该数据将作为数据源供 Adobe Journey Optimizer 使用。
* Adobe Journey Optimizer 会使用规则来指定客户何时收到自定义的“放弃”消息，该消息旨在鼓励客户通过为其帐户添加新线路来实现转化。

## 提供的商业价值

| 目标 | 战术 | 解锁的价值 |
|---|---|---|
| **提高营销活动转化率&#x200B;**<br></br>**增加年度客户收入**</ul> | <ul><li>近乎实时地为有兴趣添加线路但尚未转化的用户创建新区段。</li><li>促进对未转化客户的跟进，为感兴趣的未转化者提供额外接触点。 </li><li>使用测试策略来测量历程效果并通过电子邮件优化转化。</li></ul> | <ul><li><strong>高质量的相关体验：</strong>部署 Journey Orchestration 后，客户会得到更密切相关的消息体验，从而降低电子邮件列表流失率。</li><li><strong>大规模的 Journey Orchestration：</strong>可以打造更加及时的个性化历程，以提高转化率和总收入。</li></ul> |

## 主要Blueprint：使用Experience Cloud应用程序进行Audience和Activation

### 描述

<ul><li>将 Adobe Experience Platform 用作流式数据、客户档案和分段的中心枢纽，通过 Journey Orchestration 进行流式历程编排和消息投放，执行触发式和流式消息递送</li></ul>

### Experience Cloud 应用程序

<ul><li>Adobe Journey Optimizer</li></ul>

### Blueprint 架构

<a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=zh-Hans"><img alt="可实时提供量身定制的交易，同时高效完成客户注册以提升长期忠诚度的电信公司图像。" src="https://experienceleague.adobe.com/docs/blueprints-learn/assets/ajo-architecture.svg"/></a>
