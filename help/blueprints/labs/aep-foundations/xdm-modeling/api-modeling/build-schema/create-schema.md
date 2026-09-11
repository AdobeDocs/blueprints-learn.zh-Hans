---
hold: true
title: 创建架构
description: 使用架构注册表API根据用户档案类以及标准和自定义字段组引用汇编客户架构。
doc-type: article
solution: Experience Platform
exl-id: 78ebc5b8-d088-48e9-857f-87085a87a280
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# 创建架构

## 修改API的正文

>[!CAUTION]
>
>**尚未执行调用……1&rbrace;**

1. 单击`XDM Schema Lab -> Create Schema`文件夹中的`Step 4 - Create Customer Account Schema` API调用。

![步骤4 — 在Postman集合中创建客户帐户架构API调用](assets/create-schema-click-on-the-step-4-create-customer-account-schema.png)



&#x200B;2. 打开调用的正文并查看架构定义方式的结构。 请记住，架构始终仅由一(1)个类以及一个或多个字段组组成。

&#x200B;3. 使用以下内容填充架构正文中的`title`和`description`字段：

- 标题 — > `Sample Customer Schema - <your sandbox number>`
- 描述 — > `Sample Customer Schema - <your sandbox number>`

&#x200B;4. 在`$ref`字段中填充您从之前完成的实验室部分保存的`$ids`：[创建自定义字段组](./create-custom-field-groups.md)和[获取配置文件类](./get-profile-class.md)。 您应该为以下每个项目都设置$id：

- 类 — > XDM个人资料
- 字段组 — >人口统计详细信息
- 字段组 — >个人联系人详细信息
- 字段组 — >同意和偏好设置详细信息
- 字段组（自定义） — >客户帐户详细信息

在添加类和字段组引用之前![架构请求正文为空](assets/create-schema-empty-schema-api-body.png "架构API正文为空")



&#x200B;5. 请查阅您的最终正文，并确保它类似于以下内容

![已完成架构请求正文，并填充了标题、描述和所有$ref值](assets/create-schema-example-of-final-body-payload.png "最终正文有效负载示例")

>[!NOTE]
>
>`$refs`的顺序无关紧要，`title`和`description`在正文中的位置也不重要。



## 执行API

1. 在继续之前，请保存您对API请求所做的修改。
1. 通过单击`Send`按钮执行API

创建架构的成功响应应该会导致`201 Created`状态，并且应该类似于以下图像

>[!WARNING]
>
>如果成功，请不要再次执行请求

![201在通过步骤4 API成功创建架构后创建了响应](assets/create-schema-sample-response-from-executing-the-step-4-api.png "执行步骤4 API的示例响应")


## 找到并保存架构$id

1. 执行API请求后，从响应中复制`$id`和`$meta:altId`
1. 将值保存到某处，以便以后重复使用

>[!WARNING]
>
>在将`$id`和`$meta:altId`保存到某个位置之前，请勿继续。  在未来的实验步骤中需要用到它们

>[!TIP]
>
>**恭喜！ 您刚刚仅使用API创建了架构**
