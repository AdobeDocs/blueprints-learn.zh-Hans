---
hold: true
title: 导入API收藏集
description: 导入bootcamp的Postman API收藏集，并验证其环境变量能否针对沙盒正确解析。
doc-type: article
solution: Experience Platform
exl-id: 7562c7f1-0d60-4a3a-8bce-fa42bda08962
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# 导入API收藏集

## 目标

在此步骤中，您将导入API收藏集，其中包含您在整个引导营中需要发出的所有各种请求。  这些API请求依赖于您刚刚导入的环境文件。



## 导入请求集合

1. 下载&#x200B;**AJO引导营(Labs)。postman\_collection.json**&#x200B;文件：

下载文件 — [AJO Bootcamp (Labs)。postman_collection.json](assets/ajo-bootcamp-labs.postman_collection.json)

2. 与以前一样，单击&#x200B;**导入**&#x200B;按钮。
3. 将&#x200B;**AJO Bootcamp (Labs)。postman\_collection.json**&#x200B;文件的本地URL粘贴到导入模式文本框中，或将其拖放到导入对话框中。  这会触发自动导入。
4. 导入过程完成后，单击左侧导航栏中的&#x200B;**收藏集**，展开&#x200B;**AJO Bootcamp (Labs)**&#x200B;文件夹，即可看到新导入的收藏集

![验证postman集合导入](assets/import-api-collection-verify-collection-imported.png)

>[!TIP]
>
>恭喜！  您已成功导入引导营的Postman收藏集



## 验证环境变量

您导入的收藏集包含您在整个bootcamp中实验室所需的所有必要API调用。  每个实验室都组织到一个特定的文件夹中，其中包含它自己的一组请求。

有关每个文件夹的详细信息，请参阅以下内容：

- **配置文件和历程实验室** — 包含用于发送Web事件的一组请求和模拟送货确认的事件。
- **Decisioning Labs** — 包含针对3位访客的请求，这些请求模拟通常可在AEP Web SDK标记的网站上找到的顶部和底部页面调用。

要确保环境和集合一起正常工作，请执行以下步骤。

1. 如有必要，请单击左边栏中的&#x200B;**收藏集**，然后展开&#x200B;**配置文件和历程实验室**&#x200B;文件夹。
2. 单击&#x200B;**创建Web事件**&#x200B;请求，您会看到环境变量为&#x200B;**红色**

![Postman请求显示以红色突出显示的环境变量，因为未选择任何环境](assets/import-api-collection-environment-variables-shown-red.png "验证postman环境变量是否为红色")

3. 单击右上角的&#x200B;**环境下拉列表**，然后选择&#x200B;**AJO引导营**&#x200B;环境。

![选择正确的Postman环境](assets/import-api-collection-select-postman-environment.png)

4. 选择正确的环境后，您会看到EDGE\_REGION变量现在变为较浅的蓝色。 这表示变量现在具有选定环境的值。 DATASTREAM\_CONFIG变量保持红色，因为您尚未创建数据流，因此您还没有该环境变量的值。 将鼠标悬停在EDGE\_REGION上会显示环境值的值。

![Postman EDGE_REGION变量现已填充且不再显示为红色](assets/import-api-collection-environment-works-with-collection.png "验证Postman环境是否可与收藏集配合使用")

## 回顾

您现在已导入环境和收藏集文件并知道如何使用它们。
