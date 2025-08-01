---
title: 用户档案扩充的自定义数据科学 Blueprint
description: 了解如何将基于数据科学的见解引入 [!DNL Experience Platform] 以丰富实时客户档案。
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 63%

---

# 用于丰富个人资料的自定义数据科学Blueprint

用于丰富个人资料的自定义数据科学Blueprint说明了如何使用数据来训练、部署和评分模型，以便通过数据科学和机器学习工具提供对[!DNL Experience Platform]和[!DNL Real-Time Customer Data Platform]的机器学习见解。

模型化的见解可以引入[!DNL Experience Platform]以丰富实时客户档案。 机器学习洞察的示例包括存留期值评分、产品和类别亲和力、转化倾向或客户流失倾向。

## 用例

* 从客户数据中提取洞察并发现模式，利用此数据对模型进行训练和评分。
* 利用模型驱动的洞察和属性来丰富[!UICONTROL 实时客户档案]，以实现更精细的个性化并优化历程。
* 对模型进行训练和评分，以确定客户洞察，如客户存留期值、转化或参与倾向、产品和内容关联，以及参与分数。

## 架构

<img src="assets/data_science.svg" alt="用户档案扩充的自定义数据科学 Blueprint 的参考架构" style="width:90%; border:1px solid #4a4a4a" />

## 护栏

* 有关将数据科学结果摄取到[!DNL Experience Platform]和实时客户个人资料的详细护栏和端到端延迟，请参阅[部署护栏文档](../experience-platform/guardrails.md)中引用的数据摄取护栏和延迟图。

## 实施注意事项

* 在大多数情况下，模型结果应作为用户档案属性而不是体验事件进行摄入。模型结果可以是一个简单的属性字符串。如果要摄入多个模型结果，建议使用数组或映射类型字段。
* 每日用户档案快照数据集是统一用户档案属性数据的每日导出数据，可用于在用户档案属性数据基础上训练模型。可以在[此处](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=zh-Hans#profile-attribute-datasets)访问用户档案快照数据集文档。

## 相关文档

* [Adobe [!DNL Experience Platform] Intelligence产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe [!DNL Experience Platform] 查询服务](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=zh-Hans)

## 相关博客帖子

* [内容和商业 AI：通过内容智能个性化您与客户的互动](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [在Adobe上初步了解探索数据分析 [!DNL Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [借助机器学习打通 Adobe 体验产品以提升用户体验](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [Segmentation.AI：Adobe中的自动受众群集即服务 [!DNL Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)