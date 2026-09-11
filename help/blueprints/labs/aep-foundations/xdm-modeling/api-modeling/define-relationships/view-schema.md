---
title: 查看架构
description: 通过架构UI和获取架构API查看客户帐户架构与计划架构的查找关系。
doc-type: article
solution: Experience Platform
exl-id: dae48ef4-f762-4173-8564-c1ad40c0109b
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# 查看架构

## 通过用户界面查看

1. 打开浏览器并导航回`Schema -> Browse`部分。
1. 搜索架构`Sample Customer Schema - <your sandbox number>`
1. 请注意，已定义与`dep: Plan [Lookup]`的关系

![Experience Platform UI中的示例客户架构显示了dep： Plan Lookup关系](assets/view-schema-relationship-to-plan-lookup-schema.png)


## 通过API查看

1. 通过单击选择`Step 4 - Get Customer Account Schema and its descriptors` API

![步骤4 — 获取客户帐户架构及其描述符API调用](assets/view-schema-step-4-get-schema-and-descriptors.png "步骤4 — 获取客户帐户架构及其描述符")



&#x200B;2. 在请求的URL中，将`<replace me>`替换为您在上一节[创建架构](../build-schema/create-schema.md)中保存的`$meta:altId`，如下所示

将带有meta:altId的![Step 4请求附加到URL](assets/view-schema-final-step-4-request.png "Final Step 4请求")



&#x200B;3. 使用`Save`按钮保存请求

&#x200B;4. 单击`Send`按钮执行请求

您现在应该会看到`200 OK`响应，并且您应该能够浏览到您创建的架构的结尾，以通过XDM JSON结构的镜头查看身份



在客户帐户架构JSON中可见的![关系描述符](assets/view-schema-relationship-descriptor.png "关系描述符")



![在客户帐户架构JSON中可见的引用身份描述符](assets/view-schema-reference-identity-descriptor.png "引用身份描述符")
