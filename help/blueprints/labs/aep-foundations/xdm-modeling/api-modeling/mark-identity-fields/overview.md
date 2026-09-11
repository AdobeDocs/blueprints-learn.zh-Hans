---
hold: true
title: 标记标识字段
description: 了解身份描述符如何使用XDM架构注册API将架构字段标记为主要或非主要身份。
doc-type: overview-page
solution: Experience Platform
exl-id: f6498584-0f4d-4baf-86b5-b00cc78e2ba7
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# 标记标识字段

## 身份描述符

要将字段标记为标识，您需要在架构注册表中创建标识描述符。 架构描述符正文的示例如下所示：

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

- **@type** ->始终设置为`xdm:descriptorIdentity`
- **xdm\：sourceSchema** ->字段所在的架构的`$id`
- **xdm\：sourceVersion** ->始终为1
- 架构中字段的&#x200B;**xdm\：sourceProperty** ->路径
- **xdm\：namespace** ->应存储字段的标识命名空间代码
- **xdm\：property** ->始终为`xdm:code`
- **xdm\：isPrimary** ->如果为主要身份，则`true`，否则为`false`


## 您的目标

为客户帐户架构创建主标识和非主标识。 执行下一部分中的步骤后，您的架构应如下所示。

创建主要和非主要标识描述符后![客户帐户架构](assets/overview-schema-with-primary-and-non-primary-identities.png)
