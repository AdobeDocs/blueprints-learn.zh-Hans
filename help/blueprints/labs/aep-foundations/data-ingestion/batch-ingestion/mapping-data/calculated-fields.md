---
hold: true
title: 计算字段
description: 创建计算字段表达式以回填缺少的短信同意值，并将出生日期拆分为天、月和年字段。
doc-type: article
solution: Experience Platform
exl-id: ea5d006b-11c5-439c-af01-bc00b919851f
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---


# 计算字段

## 概述

sms\_optIn字段是客户帐户架构中的必填字段。 问题是，我们的流源中的sms\_optIn字段可以发送&#x200B;*null*&#x200B;值，因此需要一个计算字段来解决该问题；否则，将跳过摄取这些记录，这将造成损失。

![目标架构中显示的consents.marketing.sms.val字段](assets/calculated-fields-consents-marketing-sms-val-schema-field.png "架构中显示的consents.marketing.sms.val字段")



## 创建计算字段

1. 通过单击&#x200B;**新建字段类型**&#x200B;图标创建计算字段，然后选择&#x200B;**添加计算字段**。 对于所有缺少的值，假定未提供同意并标记为&#x200B;**&quot;n&quot;**。 请注意，计算字段显示在左列，因为通过计算字段的转换是此新映射的输入。

![已选择“添加计算字段”选项的新字段类型图标菜单](assets/calculated-fields-add-a-calculated-field.png "添加计算字段")



1. 在“创建计算字段”对话框中，添加以下表达式，然后单击&#x200B;**预览**

```none
iif(sms_optIn == null or sms_optIn == "", 'n', sms_optIn)
```

![使用sms_optIn表达式和预览结果创建计算字段对话框](assets/calculated-fields-sms-optin-calculated-field.png "sms_optIn计算字段")



1. 您应该会在黑框的右上角看到一个绿色复选标记，指示表达式的有效性，数据预览应仅显示&#x200B;**&quot;n&quot;**&#x200B;或&#x200B;**&quot;y&quot;**&#x200B;作为值。 如果一切正常，请单击&#x200B;**保存**。



## 映射到目标

新字段将添加到映射屏幕中，但具有未映射的目标字段路径。

![新的sms_optin计算字段已添加到映射屏幕，且未映射目标字段](assets/calculated-fields-sms-optin-unmapped.png "sms_optin未映射")

1. 在您创建的新计算字段中单击&#x200B;**映射目标字段**
1. 在右侧窗格中，您现在会看到目标架构面板处于打开状态。 在搜索框中键入&#x200B;**短信**
1. 选择&#x200B;**val**&#x200B;字段

![为计算字段映射选择sms.val字段的目标架构面板](assets/calculated-fields-map-calculated-field-to-target-xdm-field.png)



最终映射应当如下所示：

![带有映射到目标架构的sms_optin计算字段的最终映射屏幕](assets/calculated-fields-final-mapping-screen.png)



1. 验证您的映射以确保它看起来正常

![确认sms_optin映射有效的验证按钮](assets/calculated-fields-validate-mappings.png)

>[!NOTE]
>
>摄取期间，任何没有有效SMS值的行都会被拒绝。 如果未启用部分摄取，则在本例中，此行的摄取失败会导致整个批次或文件的摄取失败。 启用部分摄取后，会拒绝具有缺少值的必填字段的行，但会摄取其他行。



## 处理生日

需要将出生日期、月份和年份划分成单独的字段，以便下游活动中不得使用其中的某些字段。 您需要创建两个计算字段来解决此问题。

### 创建出生日期和月份映射

1. 添加新的计算字段以捕获用户档案的出生日期和月份
1. 对计算字段使用以下代码：

>[!NOTE]
>
>尝试通过单独执行代码段来了解所发生的情况，而不是仅复制上述代码，因为不允许在一行中创建多行内容，从而了解其构成方式，以创建更复杂的计算字段。 尝试以下操作：
>
>1. `date(birth_Date,"M/d/yyyy")`
>2. `date_part("day", date(birth_Date,"M/d/yyyy")).toString()`
>3. `date_part("month", date(birth_Date,"M/d/yyyy")).toString()`
>4. `concat(date_part("month", date(birth_Date,"M/d/yyyy")).toString(),`
>   `"-", date_part("day", date(birth_Date,"M/d/yyyy")).toString())`



1. 单击预览，您应该会看到以下结果。 如果一切正常，请单击&#x200B;**保存**

![出生日期和月份计算字段表达式的预览结果](assets/calculated-fields-birth-day-month-preview.png)



1. 将计算字段映射到&#x200B;**person.birthDayAndMonth**

1. 验证映射



### 创建出生年份映射

1. 使用以下代码创建新的计算字段以捕获用户档案的出生年份

```none
date_part("yyyy",date(birth_Date,"M/d/yyyy"))
```

1. 将计算字段映射到&#x200B;**person.birthYear**&#x200B;的目标位置

1. 验证映射

>[!NOTE]
>
>请注意，日期格式为&#x200B;**MM/DD/YYYY**，但示例中的&#x200B;**birth\_Date**&#x200B;数据在日期和月份中不是单位数字就是双位数字。 若要使&#x200B;**date**&#x200B;函数正常工作，必须指定数据的输入格式，例如&#x200B;**M/d/yyyy**，以便您可以为月份和日期计算1到2位数。 如果没有指定此日期输入格式，这些映射的验证将失败。
