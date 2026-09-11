---
title: 配置映射
description: 从批处理摄取实验室导入映射集，并更新计算日期字段以匹配流源的日期格式。
doc-type: article
solution: Experience Platform
exl-id: c05792af-5eab-4e62-a26e-a54478a988a8
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# 配置映射

> [!NOTE]
>
>仅当您成功完成批量摄取实验室时，才应遵循此部分。  否则，请按照在批处理摄取实验室中找到的[映射数据](../batch-ingestion/mapping-data/overview.md)步骤操作。

## 导入映射集

如果您完成了批量摄取实验室，则可以重复使用在该实验室创建的映射集😄🎉

执行以下步骤：

1. 单击映射屏幕上的&#x200B;**导入映射**&#x200B;按钮

映射屏幕上的![导入映射按钮](assets/configure-mapping-import-mapping-button.png)



1. 选择您在“批量摄取”部分中创建的数据流，然后选择它。  其名称应类似于&#x200B;**客户帐户批次v2 - \&lt;您的缩写>.**

![选择批处理摄取数据流以从](assets/configure-mapping-choose-batch-ingestion-dataflow.png)导入其映射集



导入后，您将看到出现错误。  这是因为示例文件中用于birth\_Date字段的日期格式已更改。

- 使用的批处理示例文件 — > mm/dd/yyyy
- 使用的流示例文件 — > yyyy-mm-dd

使用&#x200B;**date**&#x200B;函数的计算字段需要更新，以便考虑使用的日期格式中的更改。

导入批处理摄取映射集后显示的![映射错误](assets/configure-mapping-mapping-after-the-import.png)



## 更新计算字段

只需单击每个计算字段旁边的箭头图标即可更新每个计算字段，然后验证您的映射

![单击箭头图标以编辑计算字段的公式](assets/configure-mapping-arrow-to-edit-calculated-field-formula.png)

| 目标字段 | 新建计算字段 |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| person.birthYear | date\_part(&quot;yyyy&quot;，date(birth\_Date，&quot;yyyy-M-d&quot;)) |
| person.birthDayAndMonth | concat(date\_part(&quot;mm&quot;， date(birth\_Date， &quot;yyyy-M-d&quot;))。toString()， &quot;-&quot;， date\_part(&quot;dd&quot;， date(birth\_Date， &quot;yyyy-M-d&quot;))。toString()) |
