---
hold: true
title: 沙盒访问
description: 在启动Labs之前，验证您的Postman环境能否成功检索您分配的Experience Platform沙盒。
doc-type: article
solution: Experience Platform
exl-id: c841e497-a695-4d3f-85e6-d653478cad1e
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---


# 沙盒访问

在继续之前，请仔细检查您的访问权限是否合法。 执行以下步骤：

1. 打开标题为`Check Sandbox Access`的文件夹并单击标题为`Retrieve Your Sandbox`的调用
1. 在Postman的右上角，您会看到一个“环境”下拉框。  确保选择`AEP Bootcamp`环境
1. 通过单击`Send`按钮执行调用

![Postman请求窗格，用于在发送之前检索您的沙盒调用](assets/sandbox-access-check-sandbox-request.png "检索您的沙盒API调用")



成功的响应如下所示：

![200 OK响应确认已成功检索分配的沙盒](assets/sandbox-access-successful-response.png "200 OK成功的沙盒请求")

>[!NOTE]
>
>**name**&#x200B;值应与您的Postman环境中的sandbox\_name变量匹配

>[!TIP]
>
>恭喜！  您已准备好开始使用Experience Platform API
