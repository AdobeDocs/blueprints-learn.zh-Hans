---
title: 查看架构
description: 在Experience Platform UI中以及通过获取架构API调用查看新创建的客户架构。
doc-type: article
solution: Experience Platform
exl-id: 29302546-46dc-4c97-8fd8-deab6977635c
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# 查看架构

## 通过用户界面查看

1. 打开浏览器并导航回`Schema -> Browse`部分。

>[!NOTE]
>
>刷新UI以查看它，因为您刚刚创建了它，并且需要重新查询架构注册表

2. 搜索架构`Sample Customer Schema - <your sandbox number>`

3. 请注意，所需的类和关联的字段组已添加到架构中

![Experience Platform UI中显示的示例客户架构及其类和字段组](assets/view-schema-ui-view-of-sample-customer-schema.png "示例客户架构的UI视图")


## 通过API查看

1. 通过单击`Step 5 - Get Customer Account Schema` API将其选中。
1. 在请求的URL中，将`<replace me>`替换为您从上一部分（创建架构）保存到调用末尾的`$meta:altId`，如下所示
1. 保存您对请求所做的编辑
1. 单击`Send`按钮执行请求

![步骤5 — 获取客户帐户架构API调用](assets/view-schema-step-5-get-customer-account-schema.jpeg "步骤5 — 获取客户帐户架构")



添加`$meta:altId`后最终请求的示例

将带有meta:altId的![Step 5请求附加到URL](assets/view-schema-final-step-5-request.png "Final Step 5请求")



如果您收到了`200 OK`响应，则应该能够直接通过XDM JSON结构的镜头浏览您创建的架构

![200 OK响应显示完整的示例客户帐户架构JSON](assets/view-schema-sample-customer-account-schema.png "示例客户帐户架构")
