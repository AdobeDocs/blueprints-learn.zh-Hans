---
title: 验证和计划数据流
description: 验证完整的订单映射集，预览输出，并计划数据流每15分钟运行一次。
doc-type: article
solution: Experience Platform
exl-id: b7f0c43b-092c-45ba-b95b-27cb4a49d110
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 7%

---


# 验证和计划数据流

## 双重检查映射集

| # | Source列 | XDM列 |
| -- | ------------------------------------------- | -------------------------------------------------------- |
| 1 | orderStatus | 事件类型 |
| 2 | lastOrderStatusUpdate | 时间戳 |
| 3 | orderID | order.orderID |
| 4 | orderDate | order.orderDate |
| 5 | orderTotal | order.priceTotal |
| 6 | paymentType | order.payment.paymentType |
| 7 | paymentamount | order.payment.paymentAmount |
| 8 | paymentCurrencyCode | order.payment.currencyCode |
| 9 | paymentTransactionId | order.payment.transactionID |
| 10 | plan.ID | order.\_devbc.plan.planID |
| 11 | 客户ID | \_devbc.customerID |
| 12 | 个人电子邮件 | \_devbc.personalEmail |
| 13 | storeID | store.storeID |
| 14 | shippingStreetAddress | shipping.address.street1 |
| 15 | shippingCity | shipping.address.city |
| 16 | shippingState | shipping.address.state |
| 17 | shippingZip | shipping.address.postalCode |
| 18 | shippingMethod | shipping.shippingMethod |
| 19 | shippingAmount | shipping.shippingAmount |
| 20 | shippingDestination | shipping.shippingDestination |
| 21 | billingStreetAddress | billing.address.street1 |
| 22 | billingcity | billing.address.city |
| 23 | billingState | billing.address.state |
| 24 | billingZip | billing.address.postalCode |
| 25 | 产品\[\*] | productListItems\ |
| 26 | 产品\[\*].productID | - productListItems\[\*].\_id - productListItems\[\*].SKU |
| 27 | products\[\*].make | productListItems\[\*].\_devbc.make |
| 28 | products\[\*].model | productListItems\[\*].\_devbc.model |
| 29 | products\[\*].price | productListItems\[\*].priceTotal |
| 30 | concat(orderID， &quot;-&quot;， lastOrderStatusUpdate) | \_id |
| 31 | &quot;inStore&quot; | order.\_devbc.acqSource |



## 预览映射输出

1. 预览映射输出。 滚动浏览所有属性，确保右侧的任意属性旁边没有红色感叹号。

   ![预览映射屏幕在任何映射属性上没有错误](assets/verify-and-schedule-dataflow-preview-mapping-screen.png "预览映射屏幕将如下所示")

1. 在“预览”的左侧导航中，选择&#x200B;**productListItems**&#x200B;对象数组。 右侧将更新为仅显示该对象数组中的属性。

>[!NOTE]
>
>请注意，将自动填充&#x200B;**productListItems.currencyCode**&#x200B;和&#x200B;**productListItems.quantity**（即使在删除映射之后）。 发生此情况是因为作为父对象的&#x200B;**productListItems**&#x200B;已映射。

删除重复覆盖后![已完成productListItems的映射屏幕](assets/verify-and-schedule-dataflow-completed-mapping-screenshot.png "完成的映射将与以下屏幕快照类似")

## 计划运行

1. 通过将频率设置为分钟和间隔设置为15，将计划设置为每15分钟运行&#x200B;**&#x200B;**。 查看流，然后单击“完成”。

   >[!CAUTION]
   >
   >确保将计划设置为15分钟。 如果计划以&#x200B;**运行一次**&#x200B;运行，则即使稍后对映射进行了更改，也无法再次运行。

1. 数据流执行不会立即开始，并且需要几分钟的时间。 因此，上次数据流运行状态设置为&quot;*没有运行*&quot;。

1. 几分钟后，数据流成功。 请注意&#x200B;**上次数据流运行状态**&#x200B;和&#x200B;**上次数据流运行日期**。

1. 单击数据流名称以获取数据流运行的列表。 应摄取10条记录。

1. 单击数据流运行开始时间可查看错误诊断详细信息。

1. 在左侧导航栏中，转到Platform中的数据集，然后单击&#x200B;**订单 — 您的姓名此处**

1. 单击&#x200B;**预览数据集。**
