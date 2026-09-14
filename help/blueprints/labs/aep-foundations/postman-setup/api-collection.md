---
title: API收藏集
description: 下载并导入bootcamp的Postman API收藏集，其中包含整个AEP基础实验室使用的请求。
doc-type: article
solution: Experience Platform
exl-id: 18d820c5-56ad-46b8-a9cf-f725555d2db3
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%
---

# API收藏集

## Postman API收藏集文件

下载文件 — [AEP Foundation Bootcamp (Labs)。postman_collection.json](assets/aep-foundations-bootcamp-labs.postman_collection.json)



## 导入API收藏集

1. 单击文件，在浏览器中打开上面的`Postman API Collection File`
1. 将文件的URL复制到剪贴板
1. 在本地计算机上启动Postman，然后单击工作区中的`Import`按钮
1. 将`Postman API Collection File`的URL粘贴到导入模式文本框中。 这会触发自动导入

![单击Postman工作区中的“导入”按钮以导入API集合](assets/api-collection-click-import-button.png "导入按钮")



![将API收藏集文件URL粘贴到Postman导入模式文本框中](assets/api-collection-import-modal-paste-url.png "导入按钮模式文本框")

现在，您会在左侧边栏的`Collections`选项卡下看到一个名为`AEP Foundations Bootcamp`的集合已填充



![AEP Foundation Bootcamp集合填充在Postman Collections侧边栏选项卡下](assets/api-collection-imported-collection-in-sidebar.png)

## AEP Foundation Bootcamp收藏集概述

您导入的API集合包含您在整个bootcamp中实验室所需的所有必要API调用。  每个实验室都组织到一个特定的文件夹中，其中包含其自己的一组API。  在您本周完成实验时，请注意此文件夹结构。

有关每个文件夹的详细信息，请参阅以下内容：

- **IMS身份验证** — 包含单个请求以生成使用任何Adobe Experience Platform API时所需的access\_token
- **XDM架构实验室** — 包含一组请求，用于创建为实时客户配置文件构建和配置架构所需的XDM组件
- **数据摄取实验室** — 包含一组将数据流式传输到Experience Platform的请求
- **配置文件实验室** — 包含一组查看实时客户配置文件特征和行为的请求

>[!SUCCESS]
>
>恭喜！  您已成功导入引导营的Postman收藏集
