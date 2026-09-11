---
hold: true
title: 重试失败的数据流
description: 重试失败的数据流运行，以便根据新数据流中更新的映射规则重新处理源数据。
doc-type: article
solution: Experience Platform
exl-id: 83ecf037-e524-4887-b833-5ed96af40419
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---


# 重试失败的数据流

要重试工作流，请执行以下操作：

1. 导航到&#x200B;**源 — >数据流 — > \[数据流名称] -> \[运行失败]**
1. 突出显示无法显示右边栏的数据流运行。
1. 单击&#x200B;**重试**。 重试将获取与失败运行关联的数据的副本，并且现在将新映射规则应用于该副本

![从右边栏重试失败的数据流运行](assets/retry-a-failed-dataflow.png)

>[!NOTE]
>
>请注意，重试失败的数据流时，将创建并执行新数据流。 它将显示在数据流列表的顶部
