---
hold: true
title: 定义关系
description: 了解关系描述符如何通过API将客户模式链接到XDM模式注册表中的查找模式。
doc-type: overview-page
solution: Experience Platform
exl-id: be672c84-09ac-4941-b40e-da7bd3fd6704
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# 定义关系

## 关系描述符

要创建从一个架构到另一个架构的关系，您需要在架构注册表中创建关系描述符。 架构描述符正文的示例如下所示：

一对一描述符

```json
{
  "@type": "xdm:descriptorOneToOne",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:destinationSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7",
  "xdm:destinationVersion": 1
}
```

引用身份描述符

```json
{
  "@type": "xdm:descriptorReferenceIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:identityNamespace": "planID"
}
```

## 您的目标

为客户帐户架构创建关系标识。 执行下一部分中的步骤后，您的架构应如下所示。

![显示关系和引用标识描述符的客户帐户架构](assets/overview-schema-with-relationship-identities.png)
