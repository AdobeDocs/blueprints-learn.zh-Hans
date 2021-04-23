---
title: 呼叫偏转分析蓝图
description: 在客户联系呼叫中心之前，分析客户行为。
solution: Experience Platform, Customer Journey Analytics
kt: 7209
exl-id: 13593c1c-4c58-4b8a-aa6c-7530fd679a14
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 98%

---

# 呼叫偏转历程分析蓝图

在客户联系呼叫中心之前，分析客户在桌面和移动设备上的行为。通过了解客户尝试完成哪些操作、他们查看哪些内容以及在与客户支持联系之前搜索哪些条款来确定改善客户历程的机会。确定可以改进的内容和自助服务工具，以帮助客户解决问题而无需拨入。

## 用例

* 在客户与支持部门联系之前分析客户行为
* 发现提高自助服务能力的机会

## 应用程序

* Adobe Experience Platform
* Customer Journey Analytics

## 集成模式

* Adobe Experience Platform → Customer Journey Analytics

## 架构

<img src="assets/CJA.svg" alt="Customer Journey Analytics Blueprint 的参考架构" style="border:1px solid #4a4a4a" />

## 护栏

将数据摄入 Customer Journey Analytics 中：

* 数据摄入到数据湖：API ~7 GB/小时，源连接器 ~200 GB/小时，流到数据湖 ~15 分钟，Analytics 源连接器到数据湖 ~45 分钟。
* 在数据发布到数据湖后，处理到 Customer Journey Analytics 可能需要最多 90 分钟。

## 实施步骤

1. 配置数据集和架构
1. 将数据引入 Platform。数据必须先被摄入 Platform，然后才能处理到 Customer Journey Analytics 中。
1. 分析跨渠道事件数据集。合并分析的数据集必须具有通用的命名空间 ID，或通过 Customer Journey Analytics 中基于字段的拼接功能重新设置键。 

   >[!NOTE]
   >
   >Customer Journey Analytics 当前不使用 Experience Platform 用户档案或身份服务进行拼接。

1. 对数据执行任何自定义数据准备或使用基于字段的身份拼接，以确保将时间序列数据集中的公共键引入 Customer Journey Analytics。
1. 为查找数据提供主 ID，它可以加入到事件数据中的字段中。在许可中计为行。
1. 为用户档案数据设置与事件数据的主 ID 相同的主 ID。
1. 配置数据连接，将 Experience Platform 中的数据摄入到 Customer Journey Analytics。数据进入数据湖后，在 90 分钟内即可处理到 Customer Journey Analytics 中。
1. 在连接上配置数据视图，以选择要包含在视图中的特定维度和量度。还在数据视图中配置了归因和分配设置。这些设置在报告时计算。
1. 创建一个项目以便在 Analysis Workspace 内配置仪表板和报告。

## 实施注意事项

### 身份拼接注意事项

* 待统一的时间序列命名空间必须在每个记录上具有相同的 ID 数据。要将呼叫中心数据连接到匿名设备数据，数字 ID 必须与呼叫 ID 绑定。这种绑定可以通过多种可能的机制实现：
   * 拨号是该访客当时唯一的拨号号码，同时有一个查询表来跟踪关系。
   * 要求用户在请求支持之前进行身份验证，并将此身份验证与由呼叫座席确定的标识符（例如，电话号码或电子邮件）绑定。
   * 通过入门伙伴帮助键入与支持请求关联的已知标识符的线上设备标识符。
* 统一不同数据集的合并过程需要跨数据集使用共同的主要人/实体键。
* 目前不支持二级基于键的合并。
* 基于字段的身份拼接过程允许基于后续的瞬时 ID 记录（如验证 ID）对行中的身份重新设置键。此过程允许将不同记录解析为单个 ID，以便在个人级别而不是设备或 Cookie 级别进行分析。
* 拼接每周进行一次，拼接后重播。

## 常见问题解答

* 数据模型在 Customer Journey Analytics 中对下游有何影响？

   同一 XDM 字段的对象和属性在 Customer Journey Analytics 中合并为一个维度。要将不同数据集中的多个属性合并到同一 CJA 维度中，数据集应参考相同的 XDM 字段或架构。

## 相关文档

* [Customer Journey Analytics 产品说明](https://helpx.adobe.com/cn/legal/product-descriptions/customer-journey-analytics.html)
* [Customer Journey Analytics 文档](https://experienceleague.adobe.com/docs/customer-journey-analytics.html?lang=zh-Hans)
* [Customer Journey Analytics 教程](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html?lang=zh-Hans)
