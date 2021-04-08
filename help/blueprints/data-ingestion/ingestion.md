---
title: 数据准备和摄取蓝图
description: 此蓝图显示了在Adobe Experience Platform中摄取和准备数据的所有方法。
solution: Experience Platform,Data Collection
kt: 7204
thumbnail: null
exl-id: 21f8a73e-6be7-448e-8cd3-ebee9fc848e1,5c3c94b6-c928-4d93-8b38-f8bd2aad2e68
translation-type: tm+mt
source-git-commit: cd98c46d948af9026449c947496df82fd1be6718
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 0%

---

# 数据准备和摄取蓝图

数据准备和摄取蓝图包含准备数据并将其引入Adobe Experience Platform的所有方法。

数据准备包括将源数据映射到体验数据模型(XDM)模式。 它还包括对数据执行转换，包括日期格式、字段拆分/串联/转换，以及对记录进行连接/合并/重新键入。 数据准备有助于统一客户数据以提供汇总/筛选分析，包括报告或准备数据以用于客户用户档案汇编/数据科学/激活。

## 架构

<img src="assets/dataingest.svg" alt="数据准备和摄取蓝图的参考体系结构" style="border:1px solid #4a4a4a" />

## 数据摄取方法

| 摄取方法 | 说明 |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Web/Mobile SDK | 延迟：<ul><li>实时 — 对Edge Network的同一页面集合</li><li>流式接收到用户档案 ~ 1分钟</li><li>向数据湖流式摄取（微批量~ 15分钟）</ul>文档： <ul><li>[Web SDK](https://experienceleague.corp.adobe.com/docs/web-sdk.html)</li><li>[Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=en)</li></ul> |
| 流源 | 延迟：<ul><li>实时 — 对Edge Network的同一页面集合</li><li>流式接收到用户档案 ~ 1分钟</li><li>向数据湖流式摄取（微批量~ 15分钟）</li></ul>[文档](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en#connectors) |
| 流API | 延迟：<ul><li>实时 — 对Edge Network的同一页面集合</li><li>流式接收到用户档案 ~ 1分钟</li><li>向数据湖流式摄取（微批量~ 15分钟）</li><li>7 GB/小时</li></ul>[文档](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html?lang=en#what-can-you-do-with-streaming-ingestion%3F) |
| ETL工具 | 使用ETL工具在引入到Experience Platform之前修改和转换企业数据。<br><br>延迟：<ul><li>根据外部ETL工具的调度进行定时，然后基于摄取方法应用标准摄取保证。</li></ul> |
| 批源 | 从源<br>计划提取延迟：~ 200 GB/小时<br><br>[文档](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en#connectors)<br>[视频Tutorials](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/overview.html) |
| 批处理API | 延迟：<ul><li>根据大小和流量负载，向用户档案批量摄取约45分钟</li><li>根据大小和流量负载对数据湖进行批处理</li></ul>[文档](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/overview.html?lang=en#batch) |
| Adobe Application Connectors | 自动摄取来自Adobe Experience Cloud应用程序的数据<ul><li>Adobe Analytics:[文档](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en#connectors)和[视频教程](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-adobe-analytics.html)</li><li>Audience Manager:[文档](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=en#connectors)和[视频教程](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-aam.html)</li></ul> |


## 数据准备方法

| 数据准备方法 | 说明 |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 数据科学工作区 — 数据准备 | 模型驱动的转换，脚本转换。<br>[文档](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en) |
>[!NOTE]
>
>|外部ETL工具（[!DNL Snaplogic]、[!DNL Mulesoft]、[!DNL Informatica]等） |在ETL工具中执行复杂转换，并使用标准Experience Platform源API或连接器来收集结果数据。                                                                                                                                                               |

|查询服务 — 数据准备                                  |将连接、拆分、合并、转换、查询和筛选数据转换为新数据集。 使用创建表作为选择(CTAS)<br>[文档](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en#sql)                                                                       |
| XDM映射器和数据准备功能（流和批处理）     |在Experience Platform获取过程中，将CSV或JSON格式的源属性映射到XDM属性。<br>在摄取数据时对数据计算函数；即数据格式化、拆分、串联等。<br>[文档](https://experienceleague.adobe.com/docs/experience-platform/data-prep/home.html?lang=en) |

## 相关博客帖子

* [在Adobe Experience Platform Journey Orchestration中利用外部数据平台](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17?source=your_stories_page-------------------------------------)
* [高吞吐量摄取（冰山）](https://medium.com/adobetech/high-throughput-ingestion-with-iceberg-ccf7877a413f?source=your_stories_page-------------------------------------)
* [Adobe Experience Platform中的查询服务技巧(编写查询和存储派生数据集)](https://medium.com/adobetech/query-service-tricks-in-adobe-experience-platform-writing-queries-and-storing-derived-datasets-eaee0d6d683e?source=your_stories_page-------------------------------------)
* [深入挖掘Adobe Experience Platform的体验数据模型，更全面地了解实时客户用户档案的强大功能](https://medium.com/adobetech/digging-into-adobe-experience-platforms-experience-data-model-to-more-fully-understand-the-power-3e109271e04f?source=your_stories_page-------------------------------------)
* [介绍性查看Adobe Experience Platform上的探索性数据分析](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a?source=your_stories_page-------------------------------------)
* [在Adobe Experience Platform上大规模建模数据科学的XDM数据](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7?source=your_stories_page-------------------------------------)
