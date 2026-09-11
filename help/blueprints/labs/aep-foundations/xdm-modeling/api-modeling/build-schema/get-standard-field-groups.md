---
hold: true
title: 获取标准字段组
description: 查询全局架构注册API以查找并保存构建客户配置文件架构所需的标准XDM字段组的$id。
doc-type: article
solution: Experience Platform
exl-id: 62017ece-eef2-4785-afed-5c690c00ed02
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# 获取标准字段组

>[!NOTE]
>
>**“字段组”**&#x200B;以前称为&#x200B;**“Mixin”**，因此这些术语可在整个API请求和指南中互换使用。



## 请求XDM标准字段组

1. 单击`XDM Schema Lab -> Create Schema`文件夹中的`Step 1 - Get XDM Standard Field Groups` API调用
1. 通过单击`Send`按钮执行调用



**请求**

![步骤1 — 获取XDM标准字段组API请求](assets/get-standard-field-groups-step-1-request.jpeg "步骤1 — 请求")

>[!NOTE]
>
>请注意在下面的请求URL中使用`global`值：
>
>https\：//platform.adobe.io/data/foundation/schemaristry/**global**/mixins
>
>`global`用于仅请求XDM标准组件（在本例中是字段组/mixin）。 Experience Platform XDM注册表中有两种类型的所有者：Adobe和租户（即自定义）。
>
>- Adobe创建的对象在任何XDM列表或查找请求中始终使用`global`一词
>- 租户创建的对象（即自定义）在任何XDM列表或查找调用中始终使用`tenant`一词



**响应**

列出XDM标准字段组的![API响应](assets/get-standard-field-groups-step-1-response.png "步骤1响应")


## 确定所需的XDM标准字段组

架构始终由一个或多个字段组和类组成。  对于Connection 5G Individual Profile架构，请查找该架构所需的标准XDM字段组。

- 人口统计详细信息
- 个人联系人详细信息
- 同意和偏好设置详细信息



1. 在呼叫响应中搜索`Demographic Details`字段组
1. 复制字段组的`$id`并将其保存到某个位置以供将来引用
1. 对上面列出的其他两个字段组重复步骤1和2

![位于API响应中的人口统计详细信息字段组](assets/get-standard-field-groups-demographic-details-field-group.png)

>[!WARNING]
>
>在某处保存了所有三(3) `$ids`之前，请勿继续。  稍后将需要他们来创建客户帐户架构
