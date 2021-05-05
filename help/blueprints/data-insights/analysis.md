---
title: 数据分析和智能蓝图
description: 此 Blueprint 展示了 Adobe Experience Platform 内对数据湖中存在的数据执行探索性查询和分析的能力。
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039,a972ea56-d1c8-45da-9044-ed31222a2441
translation-type: tm+mt
source-git-commit: 6365fa00a77ba22774b2d6de3e882a3e09dcae0f
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 29%

---

# 数据分析和智能蓝图

数据分析和智能包括Adobe Experience Platform内对数据湖中存在的数据执行探索性查询和分析的能力。

Experience Platform的[!UICONTROL 查询服务]允许对数据执行SQL查询。 [!UICONTROL 数据科] 学工作空间支持对数据执行数据探索、数据科学和机器学习工作负载。

此外，Experience Platform允许与第三方SQL客户端、接口和Business Intelligence(BI)工具连接，以使用[!DNL PostgreSQL]协议直接连接、访问和查询Experience Platform内的数据。

某些护栏适用于查询超时和查询结果中包含的数据量，如蓝图详细信息中所述。

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

1. [创](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) 建要收录的数据架构。
1. [为要](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) 摄取的数据创建数据集。
1. [将数据引入平台](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)。
1. 确认[!UICONTROL 查询服务]和[!UICONTROL 数据科学工作区]可用于原始访问和查询。
1. 将Business Intelligence工具和SQL客户端连接到[!UICONTROL 查询服务]，以实现可视化、查询和探索。

## 相关文档

* [Adobe Experience Platform 智能产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [查询服务文档](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=zh-Hans)
