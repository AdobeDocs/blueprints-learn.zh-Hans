---
hold: true
title: 获取计划架构ID
description: 查询租户架构注册表API以查找并保存计划查找架构的$id，以便在关系描述符中使用。
doc-type: article
solution: Experience Platform
exl-id: f66e0483-b5b3-4493-b752-c4e00211a8bd
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---


# 获取计划架构ID

## 列出所有租户架构

1. 单击`XDM Schema Lab -> Create Relationship Descriptors`文件夹中的`Step 1 - Get Lookup Schemas` API请求
1. 通过单击`Send`按钮执行API

![步骤1 — 获取查找架构API请求](assets/get-plan-schema-id-step-1-get-lookup-schemas.jpeg "步骤1 — 获取查找架构")

>[!NOTE]
>
>此GET调用获取架构注册表的“租户”部分中存在的所有架构（即自定义创建的架构）。 我们只需要搜索&#x200B;**计划**&#x200B;架构，以便将其与客户帐户架构相关联。



## 标识计划架构

1. 在调用响应中搜索`dep: Plan [Lookup] `架构
1. 复制架构的`$id`并将其保存到某个位置以供将来引用

![位于API响应中的dep：计划查找架构$id](assets/get-plan-schema-id-dep-lookup-plan-schema-sid.png "dep：查找计划架构$id")

>[!NOTE]
>
>应该已在沙盒中预部署此架构

>[!WARNING]
>
>在将`$id`的架构保存到某个位置之前，请勿继续。  稍后需要创建关系描述符
