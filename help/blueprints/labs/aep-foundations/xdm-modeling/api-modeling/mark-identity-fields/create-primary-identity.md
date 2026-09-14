---
title: 创建主要身份
description: 使用架构注册表API为客户帐户架构创建主customerID身份描述符。
doc-type: article
solution: Experience Platform
exl-id: db690081-e857-4875-8bb9-7ac197d73cab
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%
---

# 创建主要身份

1. 单击`XDM Schema Lab -> Create Identity Descriptors`文件夹中的`Step 1 - Create Primary Identity for Customer Account Schema` API请求

   ![步骤1 — 为客户帐户架构Postman请求创建主标识](assets/create-primary-identity-step-1-postman-request.jpeg "步骤1 — 为客户帐户架构创建主标识")

   >[!CAUTION]
   >
   >尚未执行请求



1. 使用从[创建架构](../build-schema/create-schema.md)实验室步骤保存的`$id`更新请求正文中的`xdm:sourceSchema`值

1. 将请求正文中的`xdm:isPrimary`值更新为`true`

   仅示例

   ```json
   {
     "@type": "xdm:descriptorIdentity",
     "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
     "xdm:sourceVersion": 1,
     "xdm:sourceProperty": "/_devbc/customerID",
     "xdm:namespace": "customerID",
     "xdm:property": "xdm:code",
     "xdm:isPrimary": true
   }
   ```

   >[!NOTE]
   >
   >请记住使用您自己的名称更新上面的租户名称(\_devbc)



1. 继续使用`Save`按钮之前保存您的请求

1. 单击`Send`按钮执行API。 您现在看到了`201 Created`响应，如下所示

![201在成功创建主标识描述符后创建了响应](assets/create-primary-identity-201-created-response.png "已成功创建主标识描述符")

>[!SUCCESS]
>
>恭喜！  您在架构中创建了一个主标识描述符
