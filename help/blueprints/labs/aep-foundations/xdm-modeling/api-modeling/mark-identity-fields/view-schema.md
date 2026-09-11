---
title: 查看架构
description: 通过UI和API查看架构的身份描述符，并对已解析架构响应和未解析架构响应的“接受”标头选项进行比较。
doc-type: article
solution: Experience Platform
exl-id: 44eedb82-259f-4f7f-84fe-acc2b42376eb
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# 查看架构

## 通过用户界面查看

1. 打开浏览器并导航回`Schema -> Browse`部分。
1. 搜索&#x200B;**客户帐户**&#x200B;架构
1. 请注意，身份已添加到架构

![架构浏览视图显示已添加到架构的标识](assets/view-schema-schema-ui-with-identities.png "架构用户界面视图中的标识")


## 通过API查看

1. 通过单击`Step 3 - Get Customer Account Schema and its descriptors` API将其选中。

![步骤3 — 使用描述符API请求获取客户帐户架构](assets/view-schema-step-3-get-customer-account-schema-w-descriptors.png "步骤3 — 使用描述符获取客户帐户架构")



1. 在请求的URL中，将`<replace me>`替换为您从上一部分（创建架构）保存到调用末尾的`$meta:altId`，如下所示

![带有altId的最后步骤5请求附加到URL](assets/view-schema-final-step-5-request.png "最后步骤5请求")



1. 保存您所做请求的编辑

1. 单击`Send`按钮执行请求

您现在应会看到`200 OK`响应，并能够通过XDM JSON结构的镜头浏览您创建的架构

![显示架构的XDM JSON结构的API响应正文](assets/view-schema-body-of-the-api-response.png "API响应正文")



在API响应中向下浏览以查看您创建的身份描述符

![在API响应中显示的身份描述符](assets/view-schema-descriptors-displayed-in-api-response.png "在API响应中显示的描述符")


## 接受标头

请注意请求中使用的&#x200B;**接受**&#x200B;标头。 此标头告知XDM架构注册表在API响应中返回架构的`$refs`未解析（即显示最小信息量）及其关联的描述符。  Adobe提供了其他&#x200B;**Accept**&#x200B;标头，您可以使用这些标头获取有关架构的各种详细信息。

![在步骤3获取客户帐户架构请求中接受标头字段](assets/view-schema-accept-header.png "步骤3 — 获取客户帐户架构接受标头")

>[!NOTE]
>
>您可以在此处阅读有关各种“接受”标头的更多信息 — > [Experience League架构API端点](https://experienceleague.adobe.com/docs/experience-platform/xdm/api/schemas.html?lang=zh-Hans#lookup)



若要查看此操作的操作，请更改&#x200B;**Accept**&#x200B;标头，以告知架构注册表使用所有`$ref`和`allOf`完全解析（即分离）以及任何关联的描述符进行响应

1. 将`Accept`标头值更新为：
   `application/vnd.adobe.xed-full-desc+json; version=1`
1. 使用`Save`按钮保存您的请求
1. 使用`Send`按钮执行您的请求

现在，您应会看到如下响应：

![显示所有已解析属性的完全爆炸架构响应](assets/view-schema-fully-exploded-schema-showing-all-properties.png "显示所有属性的完全爆炸架构")

>[!NOTE]
>
>请注意，架构的所有属性现在如何在响应中完全显示，而在以前的调用中，您只显示架构的`$ref`值（即它引用的字段组），并且未将任何内容完全解析为各个字段/属性。

>[!NOTE]
>
>了解这一点很重要，因为使用API时，如果您要做的只是获取架构的`$id`或只是检查其组成，则并不总是需要完全解析的响应
