---
title: 数据分析和智能 Blueprint
description: 此 Blueprint 展示了 Adobe Experience Platform 内对数据湖中存在的数据执行探索性查询和分析的能力。
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039,a972ea56-d1c8-45da-9044-ed31222a2441
translation-type: tm+mt
source-git-commit: 9fe9d67c5f97b633e45155bd54e2006f1b797332
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 85%

---

# 数据分析和智能 Blueprint

数据分析和智能包括 Adobe Experience Platform 内对数据湖中存在的数据执行探索性查询和分析的能力。

Experience Platform 的[!UICONTROL 查询服务]允许对数据执行 SQL 查询。[!UICONTROL 数据科学工作区]支持对数据执行数据探索、数据科学和机器学习工作负载。

此外，Experience Platform 允许与第三方 SQL 客户端、接口和 Business Intelligence (BI) 工具连接，以使用[!DNL PostgreSQL]协议直接连接、访问和查询 Experience Platform 内的数据。

如 Blueprint 详情中所述，某些护栏适用于查询超时和查询结果中包含的数据量。

## 用例

* 交互式查询和数据聚合
* 对所摄入数据的行和列访问，以便进行探索和验证
* 通过 Business Intelligence 工具实现数据仪表板化和可视化

## 应用程序

* Adobe Experience Platform 

## 架构

<img src="assets/data_exploration.svg" alt="企业数据探索和报告 Blueprint 的参考架构" style="border:1px solid #4a4a4a" />

## 护栏

有关最佳实践和护栏的详细信息，请参阅查询服务产品文档。
[查询服务指南](https://experienceleague.adobe.com/docs/experience-platform/query/best-practices/writing-queries.html?lang=en#best-practices)

## 实施步骤

1. [为要摄入的数据创建架构。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html)
1. [为要摄入的数据创建数据集。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html)
1. [将数据摄入 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
1. 确认数据可用于[!UICONTROL 查询服务]和[!UICONTROL 数据科学工作区]以进行原始访问和查询。
1. 将 Business Intelligence 工具和 SQL 客户端连接到[!UICONTROL 查询服务]，以实现可视化、数据查询和探索。

## 相关文档

* [Adobe Experience Platform 智能产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [[!UICONTROL 查询服务]文档](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=zh-Hans)
