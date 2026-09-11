---
title: 创建计划引用标识
description: 使用架构注册表API在查找架构上创建引用身份描述符，以便将其用于批量分段。
doc-type: article
solution: Experience Platform
exl-id: b3b8f480-af3b-4bf8-b74e-3842f59691b6
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# 创建计划引用标识

1. 单击`XDM Schema Lab -> Create Relationship Descriptors`文件夹中的`Step 3 - Reference Descriptor for Plan` API请求

>[!CAUTION]
>
>尚未执行请求

![步骤3 — 计划架构API请求的引用描述符](assets/create-plan-reference-identity-step-3-descriptor-request.jpeg "步骤3 — 计划架构的引用描述符")



&#x200B;2. 在API调用的正文中更新以下属性。

- 将`xdm:sourceSchema`属性的值更新为您从[创建架构](../build-schema/create-schema.md)步骤保存的`Customer Account`架构的`$id`
- 从`Customer Account`架构中将`xdm:sourceProperty`的值更新为`planID`字段的路径

>[!NOTE]
>
>使用`dep: Lookup Plan`架构中`planId`字段的点表示法值并将`.`替换为`/`
>
>不要忘记前导`/` 😄

仅示例

```json
{
  "@type": "xdm:descriptorReferenceIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:identityNamespace": "planID"
}
```

>[!NOTE]
>
>请记住使用您自己的名称更新上面的租户名称(\_devbc)



&#x200B;3. 继续使用`Save`按钮之前保存您的请求

&#x200B;4. 通过单击`Send`按钮执行API

您现在应会看到如下的`201 Created`响应

![201在创建dep：计划查找引用标识描述符之后创建了响应](assets/create-plan-reference-identity-dep-plan-descriptor-result.png "dep：计划查找引用标识描述符")

>[!NOTE]
>
>引用身份描述符始终在查找架构（即sourceSchema）上定义

>[!NOTE]
>
>从架构UI创建关系时，将在后端自动创建引用身份描述符。 **在使用API创建架构时，您只需要显式创建它们**

>[!TIP]
>
>太棒了！ 您刚刚创建了将`dep: Lookup Plan`架构与`Customer Account`架构关联的所有所需描述符，并允许在批处理分段期间引用这些描述符
