---
title: 检查最终映射集
description: 将客户帐户架构的简单和计算字段映射与预期的最终映射集进行比较。
doc-type: article
solution: Experience Platform
exl-id: d1521d08-1ccb-405f-b728-a2777598cb9f
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# 检查最终映射集

>[!NOTE]
>
>如果您来自流式摄取实验室，请单击以下链接以继续该实验室的下一步：
>
>[流式摄取实验室 — 检查最终映射集](../../stream-ingestion/check-final-mapping-set.md)



## 简单映射

>[!NOTE]
>
>将\&lt;tenant-name>替换为沙盒中的值

| Source字段 | 目标字段 |
| ------------------------- | --------------------------------- |
| account\_create\_date | \&lt;租户名称>.account.createDate |
| account\_end\_date | \&lt;租户名称>.account.endDate |
| customer\_id | \&lt;租户名称>.customerID |
| plan\_name | \&lt;租户名称>.plan.name |
| plan\_id | \&lt;租户名称>.plan.planID |
| billing\_city | billingAddress.city |
| billing\_zip\_code | billingAddress.postCode |
| billing\_state | billingAddress.state |
| billing\_street\_address | billingAddress.street1 |
| email\_optIn | consents.marketing.email.val |
| mobile\_phone | mobilePhone.number |
| 名字 | person.name.firstname |
| 姓氏 | person.name.lastName |
| 电子邮件 | personalemail.address |
| createDate | repo.createDate |
| modifyDate | repo.modifyDate |
| shipping\_city | shippingAddress.city |
| shipping\_zip\_code | shippingAddress.postalCode |
| shipping\_state | shippingAddress.state |
| shipping\_street\_address | shippingAddress.street1 |

>[!NOTE]
>
>在继续之前，请确保最终映射与下面显示的内容相匹配。



## 计算映射

| 计算字段 | XDM字段 |
| ------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| iif（sms\_optIn == null或sms\_optIn == &quot;&quot;， &#39;n&#39;， sms\_optIn） | consents.marketing.sms.val |
| concat(date\_part(&quot;month&quot;， date(birth\_Date，&quot;M/d/yyyy&quot;))。toString()， &quot;-&quot;， date\_part(&quot;day&quot;， date(birth\_Date，&quot;M/d/yyyy&quot;))。toString()) | person.birthDayAndMonth |
| date\_part(&quot;yyyy&quot;，date(birth\_Date，&quot;M/d/yyyy&quot;)) | person.birthYear |

>[!NOTE]
>
>在继续之前，请确保最终映射与下面显示的内容匹配
