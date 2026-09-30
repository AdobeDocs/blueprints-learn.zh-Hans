---
title: 修复CreateDate的MAPPER错误
description: 排除并解决因格式错误的createDate值转换为空字段而导致的MAPPER错误。
doc-type: article
solution: Experience Platform
exl-id: e3f7ef23-6fd1-4f7a-8dc7-db82445322b0
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%
---

# 修复CreateDate的MAPPER错误

在本练习中，您将需要了解如何删除我们在批量摄取实验室中看到的MAPPER错误。 该错误需要修复，因为即使createDate不是必填字段，但由于格式错误的日期转换为空字段，因此仍会摄取记录。

![createDate值格式无效，导致MAPPER错误](assets/fix-mapper-errors-for-createdate-invalid-format-mapper-error.png)
