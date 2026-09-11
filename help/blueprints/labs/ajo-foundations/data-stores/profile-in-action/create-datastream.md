---
hold: true
title: 创建数据流
description: 了解如何使用Adobe Experience Platform、Offer Decisioning和Journey Optimizer服务创建和配置数据流以启用Edge事件处理。
doc-type: article
solution: Experience Platform
exl-id: 37873340-476a-4303-886d-de4835bba8df
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# 创建数据流

## 学习目标

使用所需的服务创建和配置数据流，以启用Edge事件处理。

数据流定义将利用它的服务。

- 将数据发送到Edge时，您可以指定要使用的数据流
- 发送到这些数据流的数据随后可以根据配置的服务采取操作
  - Adobe Experience Platform

## 创建新数据流

1. 在左边栏中的&#x200B;**数据收集**&#x200B;下，单击&#x200B;**数据流**
1. 然后单击&#x200B;**新建数据流**&#x200B;以创建一个数据流

![突出显示了“新建数据流”按钮的数据流列表](assets/create-datastream-new-datastream-button.png)

## 配置数据流

使用以下信息配置数据流：

1. 名称 — > **数据流SB + \&lt;沙盒名称> （即数据流SB01）**
1. 映射架构 — > **dep： Web**
1. 如果要捕获此信息，请将&#x200B;**地理位置和网络查找**&#x200B;下的所有选项切换为&#x200B;**开启**。
1. 完成后单击&#x200B;**保存**&#x200B;按钮

>[!WARNING]
>
>请勿单击“保存并添加映射”。  如果你不小心做到了，就取消吧

![具有名称和映射架构字段的数据流配置表单](assets/create-datastream-configure-datastream-form.png "配置数据流")



保存数据流后，您会看到以下屏幕：

保存新数据流后![确认屏幕](assets/create-datastream-created-confirmation.png "数据流创建了最终屏幕")

## 添加Adobe Experience Platform服务

这样，您就可以将数据发送到中心，并在此数据流接收的数据集中登陆。

1. 单击屏幕中间出现的蓝色&#x200B;**添加服务**&#x200B;按钮

数据流配置屏幕上的![添加服务按钮](assets/create-datastream-add-service-button.png)

2. 配置以下项目：
   - **服务** -> `Adobe Experience Platform`
   - **事件数据集** -> `dep: Web`
   - **配置文件数据集** -> `dep: Customer Account`
   - **选择复选框** -> `Offer Decisioning`
   - **选择复选框** -> `Adobe Journey Optimizer`
3. 完成后，单击&#x200B;**保存**

![带有事件和配置文件数据集字段的Adobe Experience Platform服务配置对话框](assets/create-datastream-configure-aep-service.png)

您会看到该服务现已添加到数据流

![Adobe Experience Platform服务已添加到数据流](assets/create-datastream-aep-service-added.png "Adobe Experience Platform服务中，该服务已添加到数据流中")

**复制**&#x200B;和&#x200B;**将**&#x200B;数据流ID **保存**&#x200B;到您的本地计算机（我们稍后将在Postman中使用它）

![要复制并保存以供以后使用的数据流ID字段](assets/create-datastream-copy-datastream-id.png)

## 回顾

您应该有一个正常工作的数据流，并且配置了Adobe Experience Platform服务。
