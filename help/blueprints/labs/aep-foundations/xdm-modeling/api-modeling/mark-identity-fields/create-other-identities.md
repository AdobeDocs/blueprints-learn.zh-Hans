---
hold: true
title: 创建其他标识
description: 使用架构注册表API为客户帐户架构创建非主电子邮件地址标识描述符。
doc-type: article
solution: Experience Platform
exl-id: 22c40299-fb93-4d41-a23b-f8629df3e7b9
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# 创建其他标识

1. 单击`XDM Schema Lab -> Create Identity Descriptors`文件夹中的`Step 2 - Create Email Address Identity for Customer Account Schema` API调用

>[!CAUTION]
>
>尚未执行请求

![步骤2 — 为客户帐户架构Postman请求创建电子邮件地址标识](assets/create-other-identities-step-2-postman-request.jpeg "步骤2 — 创建电子邮件地址标识描述符")



1. 使用从[创建架构](../build-schema/create-schema.md)实验室步骤保存的`$id`更新请求正文中的`xdm:sourceSchema`值

1. 将请求正文中的`xdm:isPrimary`值更新为`false`

仅示例

```json
{
  "@type": "xdm:descriptorIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/personalEmail/address",
  "xdm:namespace": "Email",
  "xdm:property": "xdm:code",
  "xdm:isPrimary": false
}
```

>[!NOTE]
>
>请记住使用您自己的名称更新上面的租户名称(\_devbc)



1. 继续使用`Save`按钮之前保存您的请求

1. 单击`Send`按钮执行API。 您现在应会看到如下的`201 Created`响应

![201在成功创建电子邮件地址标识描述符后创建了响应](assets/create-other-identities-201-created-response.png "成功的电子邮件地址标识描述符")
