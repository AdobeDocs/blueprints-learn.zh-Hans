---
title: 用户档案扩充的自定义数据科学 Blueprint
description: 了解如何将基于数据科学的见解引入 [!DNL Experience Platform] 以丰富实时客户资料。
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 7f3bc307f74aa88a7a73f3e50cc48bd16f58b37f
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 69%

---

# 用于丰富个人资料的自定义数据科学Blueprint

用于丰富用户档案的自定义数据科学Blueprint说明了如何使用数据来训练、部署和评分模型，从而提供机器学习见解 [!DNL Experience Platform] 和 [!DNL Real-Time Customer Data Platform] 来自数据科学和机器学习工具。

建模的见解可以引入 [!DNL Experience Platform] 以丰富实时客户资料。 机器学习洞察的示例包括存留期值评分、产品和类别亲和力、转化倾向或客户流失倾向。

## 用例

* 从客户数据中提取洞察并发现模式，利用此数据对模型进行训练和评分。
* 利用模型驱动的洞察和属性来丰富[!UICONTROL 实时客户档案]，以实现更精细的个性化并优化历程。
* 对模型进行训练和评分，以确定客户洞察，如客户存留期值、转化或参与倾向、产品和内容关联，以及参与分数。

## 架构

<img src="assets/data_science.svg" alt="用户档案扩充的自定义数据科学 Blueprint 的参考架构" style="width:90%; border:1px solid #4a4a4a" />

## 护栏

* 有关将数据科学结果摄取到的详细护栏和端到端延迟 [!DNL Experience Platform] 和实时客户配置文件请参考中的数据摄取护栏和延迟图，参考请参见 [部署护栏文档](../experience-platform/deployment/guardrails.md).

## 实施步骤

1. 为要摄入的数据[创建架构。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=zh-Hans)
1. 为要摄入的数据[创建数据集。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hans)
1. [引入数据](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hans) 到 [!DNL Experience Platform].

要将模型结果摄入到实时客户档案中，请务必在摄入数据之前执行以下操作：

1. 在架构上[配置正确的身份和身份命名空间](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hans)，以确保摄入的数据可以拼接到统一的用户档案中。
1. [为用户档案启用架构和数据集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hans)。

## 实施注意事项

* 在大多数情况下，模型结果应作为用户档案属性而不是体验事件进行摄入。模型结果可以是一个简单的属性字符串。如果要摄入多个模型结果，建议使用数组或映射类型字段。
* 每日用户档案快照数据集是统一用户档案属性数据的每日导出数据，可用于在用户档案属性数据基础上训练模型。可以在[此处](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=zh-Hans#profile-attribute-datasets)访问用户档案快照数据集文档。
* 用于从提取数据 [!DNL Experience Platform] 可以使用以下方法
   * 数据访问 SDK
      * 数据以原始文件形式提供
      * 用户档案体验事件数据保持其不统一的原始状态。
   * RTCDP 目标
      * 可导出用户档案属性和区段会员资格。

## 相关文档

* [Adobe [!DNL Experience Platform] Intelligence产品描述](https://helpx.adobe.com/cn/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe [!DNL Experience Platform] 查询服务](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=zh-Hans)

## 相关博客帖子

* [内容和商业 AI：通过内容智能个性化您与客户的互动](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [Adobe探查性数据分析初探 [!DNL Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [借助机器学习打通 Adobe 体验产品以提升用户体验](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [Segmentation.AI：Adobe中的自动受众聚类 — 即服务 [!DNL Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)