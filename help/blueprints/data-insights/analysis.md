---
title: 企业数据探索和报告蓝图
description: 此蓝图显示了Adobe Experience Platform内对数据湖中存在的数据执行探索性查询和分析的能力。
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039
translation-type: tm+mt
source-git-commit: f5d8b3fea11df0ffaeb59f0b53e93d76426ef252
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# 企业数据探索和报告蓝图

企业数据探索和报告包括Adobe Experience Platform内对数据湖中存在的数据执行探索性查询和分析的能力。

Experience Platform的查询服务允许对数据执行SQL查询。 数据科学工作区支持对数据执行数据探索、数据科学和机器学习工作负载。

此外，Experience Platform允许与第三方SQL客户端、接口和Business Intelligence(BI)工具连接，以使用PostgreSQL协议直接连接、访问和查询Experience Platform中的数据。

某些护栏适用于查询超时和查询结果中包含的数据量，如方案详细信息中所述。

## 用例

* 交互式查询和数据聚合
* 对所摄取数据的行和列访问，以便进行探索和验证
* 通过Business Intelligence工具实现数据仪表板和可视化

## 应用程序

* Adobe Experience Platform

## 场景

| 方案 | 说明 | Experience Cloud Applications/Services |
|---|---|---|
| **数据探索 — 数据的原始查询** | <ul><li>使用交互式查询用户界面或连接的SQL客户端在数据湖中写入和执行SQL查询。 Data Science Workspace还可用于查询和从Experience Platform中的原始数据获得洞察。</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |
| **企业仪表板** | <ul><li>将Business Intelligence工具与Experience Platform连接，以可视化仪表板和报告使用案例的数据。</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |

## 架构

<img src="assets/dataexplore.svg" alt="企业数据探索与报告蓝图的参考体系" style="border:1px solid #4a4a4a" />

## 瓜德雷尔

* 交互式查询的10分钟时限
* 在UI中返回100个记录限制
* 通过SQL连接器返回50,000个记录限制

## 实施步骤

1. 配置数据集和模式，以将数据引入数据湖中。
1. 收录数据。
1. 确认查询服务和数据科学工作区可使用数据进行原始访问和查询。
1. 将Business Intelligence工具和SQL客户端连接到查询服务，以实现可视化、查询和探索。

## 相关文档

* [Adobe Experience Platform Intelligence产品说明](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [查询服务文档](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en)
