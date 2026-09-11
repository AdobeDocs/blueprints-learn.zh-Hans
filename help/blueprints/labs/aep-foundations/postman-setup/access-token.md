---
hold: true
title: 访问令牌
description: 在Postman中生成OAuth服务器到服务器访问令牌，并了解验证AEP API调用所需的标头。
doc-type: article
solution: Experience Platform
exl-id: e38a1bd4-5a09-40c6-8303-c3770801c864
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---


# 访问令牌

## API安全概述



要建立与Adobe产品的安全API连接，Adobe提供了OAuth服务器到服务器凭据的创建。 为此，您必须首先在Adobe Developer Console中创建开发人员项目。 要访问Developer Console，您必须已在Adobe Admin Console中分配了开发人员权限。 一旦您拥有这些权限，您就可以利用各种Adobe产品相关API来创建开发人员项目。 这就是OAuth服务器到服务器凭据发挥作用的地方。 要生成访问令牌，您必须将一组特定声明传递到Adobe的Identity Management服务(IMS)。 对于OAuth服务器到服务器凭据，调用示例如下所示：

```curl
curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3?client_id={CLIENT_ID}' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'client_secret={CLIENT_SECRET}&grant_type=client_credentials&scope={SCOPE}'
```

>[!NOTE]
>
>您可以在[此处](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens)了解有关使用OAuth服务器到服务器凭据创建开发人员项目的e2e进程的更多信息。 对于bootcamp，我们将“手动”处理序😄的此步骤



## Adobe Experience Platform + Adobe IMS

对任何Adobe服务的每个请求都必须包含授权标头中的访问令牌以及在开发人员项目创建期间生成的客户端密钥。 此外，Experience Platform及其相关应用程序要求每个请求中另外存在两个标头参数。

- `x-gw-ims-org-id` — 此参数指定请求所属的`IMS Org`，并确保请求的处理解析到适当的SaaS环境
- `x-sandbox-name` — 此参数指定在Experience Platform中处理请求的沙盒

现在，您已了解关于Adobe如何保护其API以及使用API所需的内容的一些信息，请立即使用它们。

>[!CAUTION]
>
>未指定`x-sandbox-name`参数不会像您预期的那样使请求失败。 相反，它默认将请求处理到自动为任何Experience Platform环境配置的`default`沙盒中

>[!NOTE]
>
>在此引导营中，我们创建了一个开发人员项目，并向您提供了一个Postman环境文件，其中包含请求`access_token`的所有必要值。 这是您在本实验的前几个步骤中上传的内容

## 使用Postman进行身份验证

1. 启动Postman并导航到名为`IMS Authenticate`的目录，然后单击该目录以打开请求
1. 接下来，在Postman的右上角，您将看到一个环境下拉列表。 从下拉列表中选择`AEP Bootcamp`环境
1. 现在，通过单击“发送”按钮执行调用

发送IMS身份验证调用以生成访问令牌后![Postman请求](assets/access-token-execute-ims-authenticate-request.png)

成功的响应应如下所示：

```none
200 OK Successful Authentication
```

成功响应

```json
{
    "token_type": "bearer",
    "access_token": "<value>",
    "expires_in": 86399979
}
```

`token_type` — 将始终为持有者类型

`access_token` — 验证所有API调用的授权标头中所需的授权和要求

`expires_in` — 访问令牌过期前的毫秒（今天的24小时过期时间）

>[!TIP]
>
>恭喜！ 您已成功进行身份验证，您的access\_token现已保存到您的环境文件



## 常见错误

### 令牌无效

当环境文件中的`private_key`格式不正确或不再有效时，会发生这种情况。 如果看到此消息，请确保已复制整个键，包括换行符

示例：

```none
-----BEGIN PRIVATE KEY----- 
some uber long varchar set is here
-----END PRIVATE KEY----- 
```

```none
400 invalid_token
```

>[!NOTE]
>
>仅适用于使用基于JWT的身份验证时

### IMS\_ORG无效

当您忘记从下拉列表中设置Postman环境时，会发生此错误

未选择Postman环境时，在活动环境中找不到![IMS_ORG错误](assets/access-token-forgot-to-select-postman-environment.png)

>[!NOTE]
>
>执行API调用时，不要忘记设置您的postman环境
>
>![从AEP环境下拉列表中选择Postman Bootcamp环境](assets/access-token-set-postman-environment.png)
