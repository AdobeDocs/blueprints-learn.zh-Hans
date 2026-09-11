---
title: 浏览架构
description: 了解如何在Adobe Experience Platform中浏览关系架构和查看实体关系图，以了解营销活动中使用的架构关系。
doc-type: article
solution: Experience Platform
exl-id: ac0e6743-4a83-4a8b-9bc6-f012b636312e
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---


# 浏览架构

## 目标

在接下来的步骤中，您将导航UI以查看架构及其关系。  熟悉构建营销活动时可用的架构和关系很重要。

## 查看架构

已为您构建了Connection 5G关系数据模型。 您可以通过导航到UI中的&#x200B;**架构 — >浏览**&#x200B;页面来自行查看架构。

在搜索框中输入`dep-rel`以查看所有架构。

![显示所有dep-rel关系模式的搜索结果](assets/browse-schemas-search-results.png)

>[!NOTE]
>
>请注意，所有架构的类型为&#x200B;*关系*



## 查看关系图

使用关系XDM架构，您可以通过选择任意架构并单击“查看关系图”按钮轻松查看实体关系图(ERD)。

执行以下操作：

1. 单击&#x200B;**关系**&#x200B;选项卡，然后单击&#x200B;**查看关系图**&#x200B;按钮

   ![带有“查看关系图”按钮的“关系”选项卡](assets/browse-schemas-relationships-tab.png)



2. 单击&#x200B;**选择架构**
3. 从弹出窗口中，选择`dep-rel: Customer Account`，然后单击&#x200B;**确认**

   ![选择架构弹出窗口，相关说明：已选择客户帐户](assets/browse-schemas-select-schema-popup.png)



4. 在ERD上，单击&#x200B;**3个点**&#x200B;并选择&#x200B;**显示相关实体**

   ![在ERD上下文菜单中显示相关实体选项](assets/browse-schemas-show-related-entities.png)



5. 查看ERD以及与dep-rel：客户帐户直接相关的所有表。 或者，您可以将ERD下载为PNG文件。

![实体关系图显示与客户帐户相关的表](assets/browse-schemas-erd-diagram.png)

>[!TIP]
>
>真酷?!

## 回顾

您现在已了解在架构和关系UI中导航是多么容易。  您可以选择特定架构并导航以查看关系，帮助了解并在活动编排中使用数据。

如有需要，您可以在[此处](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/data-management/get-started-schemas)阅读更多内容。
