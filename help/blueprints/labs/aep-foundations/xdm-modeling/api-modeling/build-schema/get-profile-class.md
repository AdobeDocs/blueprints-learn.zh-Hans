---
hold: true
title: 获取配置文件类
description: 调用全局架构注册表API以检索和保存XDM Individual Profile类的$id以便在自定义架构中使用。
doc-type: article
solution: Experience Platform
exl-id: d87c21a2-dad4-4666-b917-cdf8e16058d4
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# 获取配置文件类

## 执行步骤3 — 获取配置文件类

1. 单击`XDM API Lab -> Create Schema`文件夹中的`Step 3 - Get Profile Class`请求
1. 通过单击`Send`按钮执行

![步骤3 — 获取配置文件类API请求](assets/get-profile-class-step-3-api-request.jpeg "步骤3 — 获取配置文件类API请求")

>[!NOTE]
>
>请注意，在GET请求中，`global`路径： .../schemaristry/**global**/classes。 请记住，使用`global`会告知架构注册表，我们只想返回Adobe标准XDM对象


## 查找并保存类$id

执行API请求后，执行以下步骤以查找并保存XDM个人配置文件类的`$id`。

1. 在响应中搜索`XDM Individual Profile`类
1. 复制`XDM Individual Profile`类的`$id`并将其保存在稍后可引用的位置。

位于API响应中的![XDM Individual Profile类](assets/get-profile-class-xdm-individual-profile-class.png "XDM Individual Profile类")

>[!WARNING]
>
>在将`$id`保存到某个位置之前，请勿继续。  稍后需要创建客户帐户架构
