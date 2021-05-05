---
title: 跨渠道历程分析
description: 分析客户历程中的客户互动并从中获得洞察。
solution: Experience Platform, Customer Journey Analytics, Data Collection
kt: 7208
exl-id: b042909c-d323-40d5-8b35-f3e5e3e26694
translation-type: tm+mt
source-git-commit: 9fe9d67c5f97b633e45155bd54e2006f1b797332
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 92%

---

# 跨渠道历程分析蓝图

通过统一来自各种 Web、移动和线下属性的数据，获取关于不同渠道客户行为的整合视图。

## 用例

* 分析桌面和移动设备上的客户互动，了解客户行为并提取洞察，以优化数字客户体验。
* 分析渠道之间的客户互动，包括数字和线下渠道（如支持互动和店内购买），以更好地了解和优化客户历程。 

## 应用程序

* Adobe Experience Platform
* Customer Journey Analytics
* Adobe Analytics（可选）

## 集成模式

* Adobe Experience Platform → Customer Journey Analytics
* Adobe Analytics → Adobe Experience Platform → Customer Journey Analytics

## 架构

<img src="assets/CJA.svg" alt="Customer Journey Analytics Blueprint 的参考架构" style="border:1px solid #4a4a4a" />

## 实施步骤

1. [创](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) 建要收录的数据架构。
1. [为要](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) 摄取的数据创建数据集。
1. [将数据引入 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)数据必须先被引入 Platform，然后才能处理到 Customer Journey Analytics 中。
1. 分析要合并分析的跨渠道事件数据集，以确保它们具有通用的命名空间 ID 或通过 Customer Journey Analytics 基于字段的拼接功能重新设置键。 

   >[!NOTE]
   >
   >Customer Journey Analytics 当前不使用 Experience Platform 用户档案或身份服务进行拼接。

1. 对数据执行任何自定义数据准备或使用基于字段的身份拼接，以确保将时间序列数据集中的公共键引入 Customer Journey Analytics。
1. 为查找数据指定可连接到事件数据中某个字段的主 ID。在许可中计为行。
1. 为用户档案数据设置与事件数据的主 ID 相同的主 ID。
1. 配置数据连接，将 Experience Platform 中的数据摄入到 Customer Journey Analytics。数据进入数据湖后，在 90 分钟内即可处理到 Customer Journey Analytics 中。
1. 在连接上配置数据视图，以选择要包含在视图中的特定维度和量度。还在数据视图中配置了归因和分配设置。这些设置在报告时计算。
1. 创建一个项目以便在 Analysis Workspace 内配置仪表板和报告。

## 实施注意事项

### 身份拼接注意事项

* 待统一的时间序列命名空间必须在每个记录上具有相同的 ID 数据。
* 统一不同数据集的合并过程需要跨数据集使用共同的主要人/实体键。
* 目前不支持二级基于键的合并。
* 基于字段的身份拼接过程允许基于后续的瞬时 ID 记录（如验证 ID）对行中的身份重新设置键。这允许将不同记录解析为单个 ID，以便在个人级别而不是设备或 Cookie 级别进行分析。
* 拼接每周进行一次，拼接后重播。

## 常见问题解答

* 数据模型在 Customer Journey Analytics 中对下游有何影响？

   同一 XDM 字段的对象和属性在 Customer Journey Analytics 中合并为一个维度。要将不同数据集中的多个属性合并到同一 Customer Journey Analytics 维度中，数据集应参考相同的 XDM 字段或架构。

## 相关文档

* [Customer Journey Analytics 产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/customer-journey-analytics.html)
* [Customer Journey Analytics 文档](https://experienceleague.adobe.com/docs/customer-journey-analytics.html?lang=zh-Hans)
* [Customer Journey Analytics 教程](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html?lang=zh-Hans)
