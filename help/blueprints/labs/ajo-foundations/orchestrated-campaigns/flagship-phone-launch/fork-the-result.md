---
title: 创建结果分支
description: 了解如何向编排的活动添加分支活动，以分支保存受众和发送短信消息的结果。
doc-type: article
solution: Experience Platform
exl-id: 8f1d0839-e4ca-4b7c-bc97-4e271a457296
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---


# 创建结果分支

## 目标

此步骤非常简单，因为您只需添加一个分支活动，以便您可以复制结果，并在后续步骤中对其执行两项不同的操作：

1. 保存受众以供其他人用于广告或跨渠道目的
1. 向各行发送短信消息。



## 创建分支

1. 在工作流画布上，在生成受众活动后单击&#x200B;**+** **图标**，然后选择&#x200B;**分支活动**

   ![在生成受众活动后添加分支活动](assets/fork-the-result-add-fork-activity.png)



2. 通过单击过渡并指定名称（如下所述），更新分支中每个过渡的名称：
   - **前** —> `Save Audience`
   - **底部** —> `SMS`

   ![已将分支过渡重命名为保存受众和短信](assets/fork-the-result-rename-transitions.png)



   完成后，您的画布现在看起来应该像这样……

   添加分支活动后![工作流画布](assets/fork-the-result-final-canvas.png)

   >[!NOTE]
   >
   >实际上，分支活动只是将上一个活动的结果复制到两个独立的分支中



3. 单击工作流画布顶部的&#x200B;**保存**。

工作流画布工具栏上的![保存按钮](assets/fork-the-result-click-save.png)

>[!TIP]
>
>那很难，不是吗😁



## 回顾

请注意，您创建了结果的分支（即复制结果），这允许您明确指示分支处理保存受众，而另一个分支可用于短信发送。

>[!NOTE]
>
>特别是当您计划将受众另存为保存受众活动不允许活动关注时，您需要使用Forks。
