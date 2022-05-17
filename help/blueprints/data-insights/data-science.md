---
title: 用户档案扩充的自定义数据科学 Blueprint
description: 该 Blueprint 展示了 Adobe Experience Platform 的数据科学工作区如何使用 Adobe Experience Platform 中的数据来对模型进行训练、部署和评分以提供机器学习洞察。
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 011f5b247ccd606348b4cbb4210218f28eddbd4c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 70%

---

# 用户档案扩充的自定义数据科学 Blueprint

用于用户档案扩充蓝图的自定义数据科学展示了如何使用Adobe Experience Platform中的数据来训练、部署和评分模型，以便通过数据科学和机器学习工具对Experience Platform和Real-time Customer Data Platform提供机器学习分析。 可以将模型化的分析引入Experience Platform，以丰富实时客户资料。 机器学习洞察的示例包括存留期值评分、产品和类别亲和力、转化倾向或客户流失倾向。

## 用例

* 从客户数据中提取洞察信息并发现模式，从此数据中训练和评分模型。
* 利用模型驱动的洞察和属性来丰富[!UICONTROL 实时客户档案]，以实现更精细的个性化并优化历程。
* 对模型进行训练和评分，以确定客户洞察，如客户存留期值、转化或参与倾向、产品和内容关联，以及参与分数。

## 架构

<img src="assets/data_science.svg" alt="用户档案扩充的自定义数据科学 Blueprint 的参考架构" style="width:90%; border:1px solid #4a4a4a" />

## 实施步骤

1. 为要摄入的数据[创建架构。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 为要摄入的数据[创建数据集。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)
1. [将数据摄入](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans) Experience Platform。

## 相关文档

* [Adobe Experience Platform 智能产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe Experience Platform查询服务](https://experienceleague.adobe.com/docs/experience-platform/query/home.html)

## 相关博客帖子

* [[!DNL Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence]](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [[!DNL Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)