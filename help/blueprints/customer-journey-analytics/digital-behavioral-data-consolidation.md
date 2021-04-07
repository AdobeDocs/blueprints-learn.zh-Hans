---
title: 数字行为数据整合蓝图
description: 分析客户旅程中的客户互动并从中获得洞察。
solution: Experience Platform, Customer Journey Analytics, Data Collection
kt: 7208
exl-id: b042909c-d323-40d5-8b35-f3e5e3e26694
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# 数字行为数据整合蓝图

通过统一来自各种Web、移动和线下属性的视图，统一不同渠道中的客户行为。

## 用例

* 分析桌面和移动设备上的客户互动，了解客户行为并提取洞察，以优化数字客户体验。
* 分析渠道之间的客户互动，包括数字和线下渠道（如支持互动和店内购买），以更好地了解和优化客户旅程。 

## 应用程序

* Adobe Experience Platform
* Customer Journey Analytics
* Adobe Analytics（可选）

## 集成模式

* Adobe Experience Platform → Customer Journey Analytics
* Adobe Analytics→ Adobe Experience Platform → Customer Journey Analytics

## 架构

<img src="assets/CJA.svg" alt="Customer Journey Analytics Blueprint的参考架构" style="border:1px solid #4a4a4a" />

## 瓜德雷尔

Customer Journey Analytics中的数据摄取：

* 数据摄取到湖泊：API ~ 7 GB/小时，源连接器~ 200 GB/小时，流到湖泊~ 15分钟，Adobe Analytics源连接器到湖泊~ 45分钟。
* 在数据发布到数据湖后，处理到Customer Journey Analytics可能需要90分钟。

## 实施步骤

1. 配置数据集和模式。
1. 将数据引入平台。
在处理到Customer Journey Analytics之前，数据必须被引入平台。
1. 分析要在合并中分析的跨渠道事件数据集，以确保它们具有通用的命名空间ID或通过基于字段的Customer Journey Analytics拼接功能重新键入。 

   >[!NOTE]
   >
   >Customer Journey Analytics当前不使用Experience Platform用户档案或身份服务进行拼接。

1. 对数据执行任何自定义数据准备或使用基于现场的身份拼接，以确保将时间序列数据集中的公共密钥引入Customer Journey Analytics。
1. 为查找数据指定可连接到事件数据中某个字段的主ID。 在许可中计为行。
1. 为用户档案数据设置与事件数据的主ID相同的主ID。
1. 配置数据连接，将Experience Platform中的数据收录到Customer Journey Analytics。 数据进入数据湖后，在90分钟内即可处理为Customer Journey Analytics。
1. 在连接上配置视图，以选择要包含在视图中的特定维度和量度。 还在数据视图中配置了归因和分配设置。 这些设置在报告时计算。
1. 创建一个项目以在Analysis Workspace内配置仪表板和报表。

## 实施注意事项

### 身份拼接注意事项

* 要统一的时间序列命名空间必须在每个记录上具有相同的ID数据。
* 统一不同数据集的合并过程需要跨数据集使用共同的主要人/实体密钥。
* 目前不支持辅助基于密钥的合并。
* 基于字段的身份拼接过程允许基于后续的瞬时ID记录（如验证ID）重新键入行中的身份。 这允许将不同记录解析为个人级别而不是设备或Cookie级别的分析的单个ID。
* 缝合每周进行一次，缝合后重播。

## 常见问题解答

* 数据模型在Customer Journey Analytics中对下游有何影响？

   同一XDM字段的对象和属性在Customer Journey Analytics中合并为一个维。 到  将不同数据集中的多个属性合并到同一Customer Journey Analytics维度中，数据集应引用相同的XDM字段或模式。

## 相关文档

* [Customer Journey Analytics产品说明](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Customer Journey Analytics文档](https://experienceleague.adobe.com/docs/customer-journey-analytics.html)
* [Customer Journey Analytics教程](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html)
