---
title: 用户档案扩充蓝图的自定义数据科学
description: 此蓝图显示Adobe Experience Platform的数据科学工作区如何使用Experience Platform中的数据来训练、部署和评分模型，从数据中提供机器学习洞察。
solution: Experience Platform, Data Collection
kt: 7203
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---


# 用户档案扩充蓝图的自定义数据科学

此Blueprint显示了Data Science Workspace如何使用Adobe Experience Platform中的数据来培训、部署和评分模型以提供机器学习洞察。 这些模型可以直接输出到启用实时客户用户档案的数据集。 机器学习洞察的示例包括终身价值、产品和类别关联、转化倾向或客户流失倾向。

## 用例

* 从Experience Platform中的客户数据中提取洞察并发现模式。 根据这些数据对模型进行培训和评分。
* 利用模型驱动的洞察和属性丰富实时客户用户档案，实现更精细的个性化和优化的旅程优化。
* 培训和评分模型以确定客户洞察，如客户终身价值、转化或参与倾向、产品和内容关联，以及互动分数。

## 场景

| 方案 | 方案描述 | Experience Cloud应用程序 |
|---|---|---|
| 探索性数据科学 | <ul><li>发现信号、完整性、数据正确性</li><li>使用数据科学工具发掘新洞察</li></ul> | <ul><li>Experience Platform智能</li></ul> |
| 用户档案扩充(AI/ML<br>) — 批处理 | <ul><li>发现、创作、培训、部署、评分和操作模型。</li><li>将模型预测推送到用户档案或数据湖，以实现基于批量的激活。</li></ul> | <ul><li>Experience Platform智能</li></ul> |

## 架构

<img src="assets/datascience.svg" alt="用户档案扩充蓝图的定制数据科学参考体系" style="border:1px solid #4a4a4a" />

## 实施步骤

1. 创建模式和数据集。
1. 将数据引入Experience Platform。
1. 创建DSW笔记本。
1. 选择语言。 支持Python和PySpark。
1. 在笔记本中创作模型。
1. 训练模型。
1. 对模型进行评分，以使用目标数据生成预测。
1. 如果将模型结果推送到实时客户用户档案，则启用模型结果数据集以进行用户档案。

## 相关文档

* [Adobe Experience Platform Intelligence产品说明](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [数据科学工作区文档](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en)
* [数据科学工作区教程](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/understanding-data-science-workspace.html)

## 相关博客帖子

* [使用Adobe平台体验简化数据科学生命周期](https://medium.com/adobetech/simplifying-the-data-science-lifecycle-with-adobe-platform-experience-8ea4f056d82f)
* [内容和商务AI:通过内容智能实现与客户的个性化互动](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [更深入地了解使用数据科学工作区的客户流失](https://medium.com/adobetech/gaining-a-deeper-understanding-of-churn-using-data-science-workspace-18a2190e0cf3)
* [理解Adobe Experience Platform中的数据科学](https://medium.com/adobetech/understanding-data-science-in-adobe-experience-platform-5bce5a17b42)
* [介绍性查看Adobe Experience Platform上的探索性数据分析](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [通过机器学习切换Adobe体验产品，提升用户体验](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [在Adobe Experience Platform上大规模建模数据科学的XDM数据](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7)
* [Segmentation.AI:Adobe Experience Platform中的自动受众群集即服务](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)
* [为企业规模重塑Jupyter笔记本](https://medium.com/adobetech/reimagining-jupyter-notebooks-for-enterprise-scale-8bc6340d504a)
* [利用Adobe Experience Platform Data Science Workspace加快智能洞察](https://medium.com/adobetech/accelerate-intelligent-insights-with-adobe-experience-platform-data-science-workspace-89538bacbbea)
* [时间序列预测预览与Adobe Experience Platform](https://medium.com/adobetech/preview-of-time-series-forecasting-with-adobe-experience-platform-38a2fc778e89)
* [通过机器学习切换Adobe体验产品，提升用户体验](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)


