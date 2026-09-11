---
title: 验证数据湖上的事件
description: 了解如何查询数据湖以验证流式传输Web事件是否已写入正确的数据集。
doc-type: article
solution: Experience Platform
exl-id: 14445089-aa3c-4cce-9d33-80032b6f9868
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---


# 验证数据湖上的事件

## 学习目标

验证Web事件是否已写入Experience Platform数据湖。

## 验证事件

&#x200B;> [!NOTE]
>
>最终，数据将显示在数据湖中。  **这可能需要60分钟**。  我们知道已为配置文件启用数据集，因此事件将创建配置文件片段。
>
>您可以查找和查询Web数据集。

1. 转到&#x200B;**查询**&#x200B;和&#x200B;**创建查询**

![在查询节中创建查询屏幕](assets/validate-event-on-data-lake-create-query.png)

&#x200B;2. 复制此SQL并将其粘贴到查询中

```sql
SELECT identityMap['email'][0].id, * FROM dep_web
where identityMap['email'][0].id = 'henry.creel@emailsim.io'
```

&#x200B;3. **运行**&#x200B;查询

&#x200B;> [!NOTE]
>
>**记住**：最终数据将显示在数据湖中。  **这可能需要60分钟**。
>
>您无需等待它出现。 欢迎您返回此步骤并稍后查看。



![在数据湖中显示流式传输Web事件的查询结果](assets/validate-event-on-data-lake-query-results.png)

## 回顾

事件记录将显示在相应的数据集中。
