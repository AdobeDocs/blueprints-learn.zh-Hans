---
title: 内容模拟
description: 了解如何将Adobe Journey Optimizer的模拟工具与示例配置文件数据结合使用，以验证个性化字段、内容变体和回退行为。
doc-type: article
solution: Experience Platform
exl-id: 3e2b064f-5680-461c-a49e-2a61514e146f
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---


# 内容模拟

**用途：**&#x200B;使用Adobe Journey Optimizer的模拟和验证工具验证个性化、条件逻辑和内容变体。

## 学习目标

在本模块结束时，您将能够：

1. 上传并使用测试配置文件数据进行模拟。
1. 验证个性化字段和变量逻辑。
1. 测试缺少或不匹配数据的回退行为。

## 简介

在本最终模块中，您将使用Adobe Journey Optimizer中的模拟工具通过&#x200B;**两个条件变体**测试电子邮件。
这样，您可以预览不同客户将会如何体验您的个性化消息，确保在启动营销活动之前保持准确性。

您将使用工具包中的示例测试配置文件文件&#x200B;**sample.csv**。

![工具包中的示例测试配置文件文件sample.csv](assets/content-simulation-sample-csv-toolkit-file.png)

## 打开模拟工具

1. 打开您填写好的电子邮件。
1. 单击&#x200B;**模拟内容**。
1. 选择&#x200B;**模拟内容变体**。

![单击“模拟内容”并选择“模拟内容变化”](assets/content-simulation-click-simulate-content-variation.png)

几秒钟后会打开模拟面板。

## 上传测试配置文件数据

1. 从您的Toolkit文件夹中打开&#x200B;**sample.csv**。
   - **Alex** → 40岁以上
   - **Jason**→于40岁
2. 单击&#x200B;**上载输入数据**。

在模拟面板中![上载输入数据按钮](assets/content-simulation-click-upload-input-data.png)

3. 选择&#x200B;**sample.csv**&#x200B;并单击&#x200B;**继续**。

![选择sample.csv并单击“继续”](assets/content-simulation-choose-sample-csv-continue.png)

AJO会处理文件并准备预览。


## 查看变体渲染

AJO会根据上传的用户档案并排显示这两个变体。

**预期结果：**

- **Alex**→看到&#x200B;**变体1**（年龄超过40岁）

![Alex个人资料呈现年龄超过40岁的变体1](assets/content-simulation-variant-1-age-above-40.png)

如果向上滚动，您现在还会看到带有名称的个性化字段，如下所示。

为变体1](assets/content-simulation-personalized-name-field-variant-1.png)中的Alex显示的![个性化名称字段

- **Jason** →看到&#x200B;**变体2** （年龄低于40岁）

![Jason个人资料呈现年龄在40岁以下的Variant 2](assets/content-simulation-variant-2-age-below-40.png)

还有杰森的全名。 太酷了！

在变体2](assets/content-simulation-personalized-name-field-variant-2.png)中为Jason显示了![个性化全名字段



## 验证回退行为

**回退和默认值：**&#x200B;检查您的电子邮件是否正常处理任何丢失的数据或不匹配的情况。 例如，模拟出生年份字段为空的用户档案或不符合任何定向优惠条件的用户档案。 预览应显示默认内容块或合理的占位符，而不是损坏或空的内容。 如果您的模拟显示了一个内容应位于的空部分，这表示您可能需要在设计中配置后备选件或默认文本。


## 回顾

在本模块中，您已成功：

- 使用样本个人资料的模拟个性化内容
- 已验证的变体切换逻辑
- 已确认个性化字段已正确填充

您现在已准备好学习下一模块 — **品牌一致性**，
在这里，您将使用AI根据Connection 5G品牌准则评估电子邮件。
