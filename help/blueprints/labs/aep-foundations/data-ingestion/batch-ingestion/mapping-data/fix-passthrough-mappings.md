---
hold: true
title: 修复直通映射
description: 在验证之前，识别并更正错误的AI/ML直通映射，例如重复或不匹配的目标字段分配。
doc-type: article
solution: Experience Platform
exl-id: b06cc091-661e-4ff4-b6e5-f16bc5128b6b
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# 修复直通映射

## 删除特定映射

您需要使用计算字段处理的一些源数据。  要解决这些问题，请将它们从映射中删除，然后重新验证映射。

1. 从映射中删除以下源数据：
   - birth\_日期
   - 源
   - sms\_optIn
1. 单击validate按钮以重新验证映射

![Validate按钮用于在删除字段后重新验证映射](assets/fix-passthrough-mappings-re-validate-mappings-using-validate-button.png "使用validate按钮重新验证映射")

>[!NOTE]
>
>单击“验证”后，可能仍会出现错误



## 错误映射示例

虽然AI/ML推荐很有帮助，但它们有时是错误的。  如果检查推荐，您可能会发现需要修复的此类错误

>[!NOTE]
>
>以下是您可能在自己的沙盒中看到的一些无效映射示例。 您还可能会看到其他错误。

## 复制映射

在此方案中，您看到AI/ML推荐程序将两个不同的源字段映射到相同的目标字段&#x200B;**person.name.lastName**



![映射到同一个目标字段person.name.lastName](assets/fix-passthrough-mappings-person-lastname-mapped-twice.png "person.name.lastName的两个不同的源字段在此映射中被映射两次")

![涉及plan_name字段的重复直通映射示例](assets/fix-passthrough-mappings-plan-name-duplicate-mapping.png)



## 错误映射

此映射正确无误，但在仔细检查时，**电子邮件**&#x200B;与&#x200B;**电子邮件格式**&#x200B;不同

![错误映射了电子邮件而不是emailFormat的映射](assets/fix-passthrough-mappings-email-mapped-incorrectly.png "电子邮件似乎已正确映射，但根据要求不正确")

**email\_optIn**&#x200B;错误地映射到错误的同意对象

![email_optIn错误地映射到错误的同意对象](assets/fix-passthrough-mappings-email-optin-wrong-consent-object.png "email_optIn似乎已正确映射，但根据要求不正确")



## 修复直通映射

要修复错误指向错误目标字段的直通映射，请执行以下步骤。

### 示例

1. 从无效的映射开始，然后单击目标字段框。 例如，在下面的映射中，字段&#x200B;**person.name.lastName**&#x200B;未正确映射，已映射到&#x200B;**planName**
1. 在右侧打开的目标架构面板中，选择相应的目标字段并选择&#x200B;**\_devbc.plan.name**
1. 目标字段现在应在目标字段框中更新
1. 修复每个此类错误后，应按&#x200B;**验证**&#x200B;按钮，以便确保减少此类错误而不引入新错误。



![正在处理映射列表以修复每个映射错误](assets/fix-passthrough-mappings-work-through-mapping-errors.png "正在处理映射并修复映射错误")



![用于选择正确字段以修复直通映射的目标架构面板](assets/fix-passthrough-mappings-choose-correct-target-field.png "选择正确的目标字段并验证它是否与直通要求匹配")

>[!WARNING]
>
>在解决所有映射错误之前，请勿继续执行下一步
