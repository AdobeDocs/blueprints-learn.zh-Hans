---
title: 电信行业 — 用于触发式消息传送的Journey Optimizer
description: 实时为客户提供量身定制的交易，同时高效率地载入客户，以实现长期忠诚度。
solution: Experience Platform, Journey Optimizer
kt: 9486
source-git-commit: 7a81ea5d71355323a784e12207542fb7dd6b286b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 12%

---


# 电信行业业务挑战

在实施此Blueprint之前，电信公司的“添加新线路”电子邮件促销活动依赖于用户是否已转换，并且仅在等待7天后才检查此内容。 满足这些标准后，便会启动任何其他接触点。

必须解决这一限制，以便对希望在当前状态7天等待期之前添加线路的用户进行更及时的跟踪。

## Adobe方法

* 用于标识无法转换以添加新行的用户的Adobe Analytics数据将作为数据源包含在Adobe Journey Optimizer中。
* Adobe Journey Optimizer会不时使用一个规则来告知客户，当客户收到自定义的“放弃”消息时，该消息旨在通过向其帐户中添加新行来鼓励客户进行转化。


## 交付的商业价值

| 目标 | 战术 | 值未锁定 |
|---|---|---|
| **提高促销活动转化率&#x200B;**<br></br>**增加年度客户收入**</ul> | <ul><li>为有兴趣添加行但尚未转换的用户近乎实时地创建新区段。</li><li>为未转换客户提供跟踪，为感兴趣的非转换器提供第二个接触点。 </li><li>使用测试策略来测量旅程性能并通过电子邮件优化转化。</li></ul> | <ul><li><strong>高质量、相关的体验：</strong> 在journey orchestration就位后，客户会体验到更相关的消息传送，从而降低电子邮件列表流失率。</li><li><strong>Journey Orchestration:</strong>可以创建一个更加及时的个性化历程，以提高转化率和总收入。</li></ul> |

## 关键Blueprint:使用Experience Cloud应用程序激活和激活受众

<strong>描述</strong>
<ul><li>将 Adobe Experience Platform 用作流式数据、客户档案和分段的中心枢纽，通过 Journey Orchestration 进行流式历程编排和消息投放，执行触发式和流式消息递送</li></ul>

<strong>Experience Cloud 应用程序</strong>
<ul><li>Adobe Journey Optimizer</li></ul> 
<br>

### Blueprint架构

<a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=zh-Hans"><img alt="电信业务的缩略图图像可实时提供量身定制的交易，同时高效地载入客户，以获得长期忠诚度。" src="https://experienceleague.adobe.com/docs/blueprints-learn/assets/journey-optimizer.png?lang=en"/></a>





