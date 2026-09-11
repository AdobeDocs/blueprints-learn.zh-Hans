---
title: Postman安装
description: 在以后的实验室中进行API调用之前，请安装Postman并熟悉其收藏集、环境和工作区界面。
doc-type: article
solution: Experience Platform
exl-id: c277edb5-f758-4955-bcd7-b15a9b9ab949
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---


# Postman安装

## 目标

本实验结束后，您将能够安装Postman，配置基础工作区和环境，以便能够进行未来实验所需的后续api调用。

&#x200B;> [!IMPORTANT]
>
>本课程中的各个实验室均需要Postman。  即使您已安装Postman，也需要完成本实验以确保已安装并正确设置环境文件和API收集。



## 安装Postman

导航到Postman网站并下载Postman应用程序或利用Web版本 — > [https://www.postman.com/download/](https://www.postman.com/download/)

Postman网站上的![Postman下载页面](assets/postman-installation-postman-download.png)

## 创建Postman工作区（可选）

如果您&#x200B;*是Postman的新用户*，并且这是您的第一个安装，则无需创建新工作区。 首次启动时，选择继续而不登录，并且您使用的是不需要工作区的轻型客户端。

如果您&#x200B;*已熟悉Postman*&#x200B;并已安装它，则您可能已登录并具有多个工作区。 如果是这种情况，我们建议您为&#x200B;*此引导营*&#x200B;创建新的工作区。 有关说明，请访问[Postman网站。](https://learning.postman.com/docs/collaborating-in-postman/using-workspaces/create-workspaces/)

## Postman界面

打开Postman并快速熟悉该应用程序的几个方面。 为了与Experience Platform合作，我们实际上只需要关注应用程序的几个关键领域。

![Postman界面概述，侧栏、标题和主工作区标记为](assets/postman-installation-interface-overview.png "Postman界面")

## 侧栏

通过侧栏，您可以在各种Postman元素之间快速导航。 在实验中，您将只使用下面两个项目：

**收藏集** — 可从外部位置导入或自己创建的已保存请求组。

**环境** — 可在Postman请求中引用的一组变量。 在Experience Platform中，您可以将Postman环境视为IMS组织中Adobe沙盒的同义词。我们将使用Postman中的“环境”功能



## 页眉

工作区 — 使您能够将工作组织到各种分组中（即项目、团队等）



## 主要工作区

主要工作区域是您在Postman中工作时将执行大多数工作的区域。 所有API请求都将显示在主工作区内的特定选项卡中。

**右侧边栏** — 根据当前选定的选项卡提供对工具的额外访问权限。 示例包括请求、注释和代码片段的文档，以及一些功能。

**环境选择器** — 允许您在使用API时在不同环境之间快速切换以访问预配置的变量。 在使用Experience Platform时，您将在使用分配的IMS组织内的特定AEP沙盒时利用此功能。



## 页脚

在Postman应用程序的最底部，您会找到一组函数，利用这些函数，您可以快速查看所进行调用的日志、快速访问以查找和替换以及各种其他函数。



## 回顾

您现在应该已安装Postman并了解UI的一些基础知识
