---
title: 用户档案扩充的自定义数据科学 Blueprint
description: 该 Blueprint 展示了 Adobe Experience Platform 的数据科学工作区如何使用 Adobe Experience Platform 中的数据来对模型进行训练、部署和评分以提供机器学习洞察。
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 56ed25f8ed954126c3291559b7f67f04565c01d4
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 64%

---

# 用户档案扩充的自定义数据科学 Blueprint

用户档案扩充的自定义数据科学 Blueprint 展示了如何使用 Adobe Experience Platform 中的数据来对模型进行训练、部署和评分，以便通过数据科学和机器学习工具为 Experience Platform 和 Real-time Customer Data Platform 提供机器学习洞察。可以将模型化的洞察摄入 Experience Platform，以丰富实时客户档案。机器学习洞察的示例包括存留期值评分、产品和类别亲和力、转化倾向或客户流失倾向。

## 用例

* 从客户数据中提取洞察并发现模式，利用此数据对模型进行训练和评分。
* 利用模型驱动的洞察和属性来丰富[!UICONTROL 实时客户档案]，以实现更精细的个性化并优化历程。
* 对模型进行训练和评分，以确定客户洞察，如客户存留期值、转化或参与倾向、产品和内容关联，以及参与分数。

## 架构

<img src="assets/data_science.svg" alt="用户档案扩充的自定义数据科学 Blueprint 的参考架构" style="width:90%; border:1px solid #4a4a4a" />

## 实施步骤

1. 为要摄入的数据[创建架构。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 为要摄入的数据[创建数据集。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)
1. [将数据摄入](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans) Experience Platform。

要将模型结果摄取到实时客户资料中，请务必在摄取数据之前执行以下操作：

1. 在架构上[配置正确的身份和身份命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)，以确保摄入的数据可以拼接到统一的用户档案中。
1. [为用户档案启用架构和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。

## 实施注意事项

* 在大多数情况下，模型结果应作为用户档案属性而不是体验事件进行摄取。 模型结果可以是一个简单的属性字符串。 如果要摄取多个模型结果，建议使用数组或映射类型字段。
* 每日配置文件快照数据集是统一配置文件属性数据的每日导出数据，可以利用该数据集对配置文件属性数据进行模型培训。 可以访问配置文件快照数据集文档 [此处](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html#profile-attribute-datasets).
* 要从Experience Platform中提取数据，可使用以下方法
   * 数据访问SDK
      * 数据以原始文件形式提供
      * 用户档案体验事件数据保持其不统一的原始状态。
   * RTCDP目标
      * 只能处理用户档案属性和区段成员关系。
   * 查询服务
      * 访问大量原始数据可能会导致查询在10分钟超时。 建议以增量方式查询数据。


## 相关文档

* [Adobe Experience Platform 智能产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe Experience Platform 查询服务](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=zh-Hans)

## 相关博客帖子

* [[!DNL Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence]](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [[!DNL Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)