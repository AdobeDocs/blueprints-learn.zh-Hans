---
title: 调试错误
description: 使用预览错误诊断程序来调查失败的数据流运行，并将INGEST格式错误与MAPPER转换警告区分开来。
doc-type: article
solution: Experience Platform
exl-id: beee191b-a860-494c-873f-ab2e407ffbf5
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---


# 调试错误

## 预览错误诊断

几分钟后，您应该会注意到&#x200B;**状态**&#x200B;显示失败。 深入查看失败详细信息以了解导致失败的原因。

1. 单击&#x200B;**数据流运行开始**&#x200B;日期
1. 单击&#x200B;**预览错误诊断**&#x200B;查看每行失败的特定详细信息

![数据流运行状态显示失败](assets/debugging-errors-dataflow-run-failure.png "数据流运行失败")

![在数据流运行详细信息屏幕上预览错误诊断链接](assets/debugging-errors-preview-error-diagnostics-link.png "预览错误诊断")



您现在看到的屏幕显示了有关错误代码含义的众多详细信息，其中包括完整的错误消息和失败的行。

![错误诊断详细信息屏幕，显示错误代码、消息和失败的行](assets/debugging-errors-error-diagnostics-detail-screen.png "错误诊断预览")

>[!NOTE]
>
>滚动到右侧以查看与此错误代码关联的源数据



## 了解错误类型

### INGEST-XXXX-XXX错误

出现此错误是因为&#x200B;**person.birthDayAndMonth**&#x200B;应为两位数月份加两位数日期的格式（即4月27日应设置为04-27格式）

```none
The value (9-27) does not conform to the specified
regex pattern: [0-1][0-9]-[0-9][0-9] in field: 
person.birthDayAndMonth of type: String
```

>[!CAUTION]
>
>请注意，person.birthDayAndMonth不是必填字段，但系统会将不符合正则表达式的情况视为“数据损坏问题”，并视为严重错误。



### MAPPER-XXXX-XXX错误

发生此错误是因为&#x200B;**createDate**&#x200B;的源字段具有`Created on 2022-04-22T19:34:17Z`字符串值。 此值无法自动转换为日期，因为开头的文本： `Created on`。 必须使用计算字段清除数据。

```none
Error transforming data for destination path 
_dep.account.createDate. Details: Unable to convert 
Created on 2023-09-24T10:19:58Z to schema type DATE_TIME
```

&#x200B;> [!NOTE]
>
>此错误并不严重，因为此错误仅会导致映射期间出现警告。 数据流运行不会因此而失败，因此本实验不会修复此错误。
