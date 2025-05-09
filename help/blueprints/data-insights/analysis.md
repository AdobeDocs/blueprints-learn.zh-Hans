---
title: 数据分析和智能 Blueprint
description: 使用Adobe [!DNL Experience Platform] (AEM)对数据湖中存在的数据执行探索性查询和分析。
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: a972ea56-d1c8-45da-9044-ed31222a2441
source-git-commit: 7f3bc307f74aa88a7a73f3e50cc48bd16f58b37f
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 59%

---

# 数据分析和智能Blueprint

数据分析和智能包括在[!DNL Experience Platform]内对存在于数据湖中的数据执行探索性查询和分析的能力。

[!DNL Experience Platform]的[!UICONTROL 查询服务]允许对数据执行SQL查询。

[!DNL Experience Platform]允许与第三方SQL客户端、接口和Business Intelligence(BI)工具的连接使用[!DNL PostgreSQL]协议直接连接、访问和查询[!DNL Experience Platform]中的数据。

## 用例

* 交互式查询和数据聚合
* 对所摄入数据的行和列访问，以便进行探索和验证
* 通过 Business Intelligence 工具实现数据仪表板化和可视化

[查询服务用例](https://experienceleague.adobe.com/docs/experience-platform/query/use-cases/abandoned-browse.html?lang=zh-Hans)这里概述了查询服务的其他常见用例

## 应用程序

* Adobe [!DNL Experience Platform]

## 架构

<img src="assets/data_exploration.svg" alt="企业数据探索和报告 Blueprint 的参考架构" style="width:90%; border:1px solid #4a4a4a" />

## 护栏

有关最佳实践和护栏的详细信息，请参阅查询服务产品文档。
[查询服务指南](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=zh-Hans)

## 实施步骤

1. 为要摄入的数据[创建架构。](https://experienceleague.adobe.com/?lang=zh-hans&recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=zh-Hans)
1. 为要摄入的数据[创建数据集。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)
1. [将数据摄取](https://experienceleague.adobe.com/?lang=zh-hans&recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans)到[!DNL Experience Platform]。
1. 确认数据可用于[[!UICONTROL 查询服务]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=zh-Hans)。
1. [将 Business Intelligence 工具和 SQL 客户端连接到[!UICONTROL 查询服务]](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=zh-Hans)，以实现可视化、数据查询和探索。

## 相关文档

* [Adobe [!DNL Experience Platform] 智能产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [[!UICONTROL 查询服务]文档](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=zh-Hans)
