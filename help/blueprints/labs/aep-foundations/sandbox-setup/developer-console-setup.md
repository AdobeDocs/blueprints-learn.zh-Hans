---
title: 开发人员控制台设置
description: 创建具有OAuth服务器到服务器凭据的Adobe Developer Console项目，以便DEP CLI对您的沙盒进行身份验证。
doc-type: article
solution: Experience Platform
exl-id: 4a7c9e2b-1d3f-4a6e-8b9c-2d5e7f1a3c6b
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---


# 开发人员控制台设置

>[!NOTE]
>
>只有在您按照自己的进度在实验室中工作时，才需要使用此功能。 如果您正在参加实时培训课程或活动，则已为您部署了沙盒。

DEP CLI使用Adobe Developer Console项目中的OAuth服务器到服务器凭据对沙盒进行身份验证。 本页将介绍如何创建该项目。 您只需执行此操作一次 — 只要添加下面描述的两个API，相同的凭据即可跨AEP基础和AJO架构基础两个跟踪运行。

>[!NOTE]
>
>如果您已拥有一个带有Adobe Experience Platform凭据的Developer Console项目（如果需要，还有Adobe Journey Optimizer），请跳过此部分，直接转到[部署说明](deployment-instructions.md)。

## 先决条件

- 具有组织开发人员访问权限的Adobe ID
- 空的Adobe Experience Platform沙盒，类型为`dev`
- 具有为该沙盒授予的所有权限的Adobe Experience Platform角色（如果您不确定，请咨询您的系统管理员）

## 创建项目

1. 转到[Adobe Developer Console](https://developer.adobe.com/console)并登录
1. 如果您有权访问多个组织，请使用右上角的组织切换器来选择正确的组织
1. 选择&#x200B;**创建新项目**
1. 将项目重命名为稍后可识别的名称（例如，`DEP Sandbox`）

## 添加Experience Platform API

1. 从项目概述中，选择&#x200B;**添加API**
1. 选择&#x200B;**Adobe Experience Platform**&#x200B;产品图标，然后选择&#x200B;**Adobe Experience Platform API**
1. 选择&#x200B;**下一步**
1. 选择&#x200B;**OAuth服务器到服务器**&#x200B;作为身份验证类型，然后选择&#x200B;**下一步**
1. 为凭据提供一个名称并选择&#x200B;**下一步**
1. 选择与您将使用的沙盒匹配的产品配置文件，然后选择&#x200B;**保存配置的API**

## 收集您的值

打开凭据的&#x200B;**OAuth服务器到服务器**&#x200B;概述页面。 CLI的环境文件需要四个值：

| **开发控制台值** | **环境文件字段** |
| --------------------- | ------------------------------- |
| 客户端ID | `API_KEY` |
| 客户端密码 | `CLIENT_SECRET` |
| 组织ID | `IMS_ORG` （以`@AdobeOrg`结尾） |
| 范围 | `SCOPES` |

>[!NOTE]
>
>复制凭据页面上显示的默认范围 — 无需手动添加任何内容。 如果您添加了以上两个API，则范围列表会自动包含这两个API。

保持此页面处于打开状态，或将这四个值复制到安全的位置。 您将在跟踪设置指南的下一步中将它们粘贴到CLI的环境文件中。
