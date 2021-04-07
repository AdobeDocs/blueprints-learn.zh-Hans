---
title: 呼叫偏转分析蓝图
description: 在客户联系呼叫中心之前分析客户行为。
solution: Experience Platform, Customer Journey Analytics
kt: 7209
exl-id: 13593c1c-4c58-4b8a-aa6c-7530fd679a14
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# 呼叫偏转历程分析蓝图

在联系呼叫中心之前，分析客户在桌面和移动设备上的行为。 通过了解客户尝试完成哪些操作、他们视图哪些内容以及在与客户支持联系之前搜索哪些条款来确定改善客户旅程的机会。 确定可以改进的内容和自助服务工具，以帮助客户解决问题而无需拨入。

## 用例

* 在客户与支持部门联系之前分析客户行为
* 发现提高自助服务能力的机会

## 应用程序

* Adobe Experience Platform
* Customer Journey Analytics

## 集成模式

* Adobe Experience Platform → Customer Journey Analytics

## 架构

<img src="assets/CJA.svg" alt="Customer Journey Analytics Blueprint的参考架构" style="border:1px solid #4a4a4a" />

## 瓜德雷尔

Customer Journey Analytics中的数据摄取：

* 数据摄取到湖泊：API ~ 7 GB/小时，源连接器~ 200 GB/小时，流到湖泊~ 15分钟，Analytics源连接器到湖泊~ 45分钟。
* 在数据发布到数据湖后，处理到Customer Journey Analytics可能需要90分钟。

## 实施步骤

1. 配置数据集和模式。
1. 将数据引入平台。
在引入Customer Journey Analytics之前，必须将数据引入平台。
1. 分析跨渠道事件数据集。
在合并中分析的命名空间集必须具有通用的Customer Journey AnalyticsID，或通过基于字段的拼接功能重新进行键控。 

   >[!NOTE]
   >
   >Customer Journey Analytics当前不使用Experience Platform用户档案或身份服务进行拼接。

1. 对数据执行任何自定义数据准备或使用基于现场的身份拼接，以确保将时间序列数据集中的公共密钥引入Customer Journey Analytics。
1. 为查找数据提供主ID，它可以连接到事件数据中的字段。 在许可中计为行。
1. 为用户档案数据设置与事件数据的主ID相同的主ID。
1. 配置数据连接，将Experience Platform中的数据收录到Customer Journey Analytics。 数据进入数据湖后，在90分钟内即可处理为Customer Journey Analytics。
1. 在连接上配置视图，以选择要包含在视图中的特定维度和量度。 还在数据视图中配置了归因和分配设置。 这些设置在报告时计算。
1. 创建一个项目以在Analysis Workspace内配置仪表板和报表。

## 实施注意事项

### 身份拼接注意事项

* 要统一的时间序列命名空间必须在每个记录上具有相同的id数据。 要将呼叫中心数据连接到匿名设备数据，数字ID必须与呼叫ID绑定。 这种绑定可以通过多种可能的机制实现：
   * 拨号是该访客在该时间的唯一拨号号，以及跟踪关系的查找表。
   * 要求用户在请求支持之前进行身份验证，并将此身份验证与由呼叫代理确定的标识符（例如，电话号码或电子邮件）绑定。
   * 使用入门伙伴帮助键入与支持请求关联的已知标识符的在线设备标识符。
* 统一不同数据集的合并过程需要跨数据集使用共同的主要人/实体密钥。
* 目前不支持辅助基于密钥的合并。
* 基于字段的身份拼接过程允许基于后续的瞬时ID记录（如验证ID）重新键入行中的身份。 此过程允许将不同记录解析为个人级别（而非设备级或cookie级别）的分析的单个ID。
* 缝合每周进行一次，缝合后重播。

## 常见问题解答

* 数据模型在Customer Journey Analytics中对下游有何影响？

   同一XDM字段的对象和属性在Customer Journey Analytics中合并为一个维。 要将不同数据集中的多个属性合并到同一CJA维度中，数据集应引用相同的XDM字段或模式。

## 相关文档

* [Customer Journey Analytics产品说明](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Customer Journey Analytics文档](https://experienceleague.adobe.com/docs/customer-journey-analytics.html)
* [Customer Journey Analytics教程](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html)
