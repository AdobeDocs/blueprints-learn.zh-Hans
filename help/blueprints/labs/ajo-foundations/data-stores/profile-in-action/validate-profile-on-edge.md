---
title: 在Edge上验证配置文件
description: 了解如何检查Edge配置文件存储区和“Audience Membership”选项卡，以确认配置文件在Edge网络上的状态。
doc-type: article
solution: Experience Platform
exl-id: f82ceba7-6916-49ff-8776-2d0238560df8
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---


# 在Edge上验证配置文件

## 学习目标

确认Edge网络配置文件存储中不存在该配置文件。

## 查看Edge配置文件

1. 单击&#x200B;**属性**&#x200B;选项卡和&#x200B;**Edge**&#x200B;单选按钮以查看Edge配置文件

在“属性”选项卡上显示的![Edge配置文件](assets/validate-profile-on-edge-attributes-tab.png)

>[!NOTE]
>
>根据所经过的时间，您可能会看到配置文件的“剥离”版本，该版本仅包含身份。



2. 单击“受众成员资格”选项卡。  它将为&#x200B;**空白**。

Edge配置文件上的![空受众成员资格选项卡](assets/validate-profile-on-edge-empty-audience-membership-tab.png)

>[!NOTE]
>
>**为什么没有Edge会员资格？**
>
>我们是否应该看到&#x200B;**dep：任何事件Edge（一小时内）**&#x200B;符合条件？
>
>即使我们有一个已进行Edge评估的受众，但该受众并不存在于Edge上，因为我们还没理由去那里……
>
>如果我们使用该受众（例如Decisioning或Destinations），则受众规则将被推送到Edge，并且下次将事件流式传输到Edge时，将会评估该受众。
>
>此外，我们还未启用Edge分段服务。



## 回顾

Edge上不存在该配置文件（尚）
