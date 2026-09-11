---
hold: true
title: 检查最终映射集
description: 将流式摄取映射与预期的最终直通和计算字段映射集进行比较。
doc-type: article
solution: Experience Platform
exl-id: 8802aaca-f566-4972-8bd6-41aca9fae9bf
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---


# 检查最终映射集

## 直通映射

&#x200B;> [!NOTE]
>
>在继续之前，请确保最终映射与下面显示的内容相匹配。

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



## 计算映射

>[!NOTE]
>
>请注意，由于日期的格式，`birth_Date`的映射与批量摄取实验室映射不同。  批处理使用斜杠`/`，而流式处理使用短划线`-`

| 计算字段 | XDM字段 |
| ----------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| iif（sms\_optIn == null或sms\_optIn == &quot;&quot;， &#39;n&#39;， sms\_optIn） | consents.marketing.sms.val |
| concat(date\_part(&quot;mm&quot;， date(birth\_Date， &quot;yyyy-M-d&quot;))。toString()， &quot;-&quot;， date\_part(&quot;dd&quot;， date(birth\_Date， &quot;yyyy-M-d&quot;))。toString()) | person.birthDayAndMonth |
| date\_part(&quot;yyyy&quot;，date(birth\_Date，&quot;yyyy-M-d&quot;)) | person.birthYear |

&#x200B;> [!NOTE]
>
>在继续之前，请确保最终映射与下面显示的内容匹配



## 完成数据流

完成后，单击&#x200B;**下一步**&#x200B;按钮，然后单击“完成”按钮，使用新的映射逻辑更新数据流。

![在单击“完成”保存数据流之前查看数据流详细信息](assets/check-final-mapping-set-review-and-finish-dataflow.png)



现在，您应该会看到一个屏幕，其中显示您创建的HTTP API帐户以及使用该帐户的所有关联数据流。 此时还应显示您创建的数据流。
