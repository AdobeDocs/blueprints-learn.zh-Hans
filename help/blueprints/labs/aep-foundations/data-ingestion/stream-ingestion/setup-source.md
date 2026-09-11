---
title: 设置源
description: 创建HTTP API流帐户并配置数据流以将客户帐户JSON数据流式传输到启用了配置文件的数据集。
doc-type: article
solution: Experience Platform
exl-id: a5c02337-8af3-45dc-82a0-fa9731892fe4
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# 设置源

## 导航到流源

1. 转到Adobe Experience Platform UI并导航到&#x200B;**源**
1. 单击顶部导航中的&#x200B;**目录**
1. 从源列表中选择&#x200B;**流**（确保选中“所有源”单选按钮）
1. 单击HTTP API的&#x200B;**设置** / **添加数据**

![创建新HTTP API源帐户的步骤顺序](assets/setup-source-sequence-of-steps-to-create-a-http-api-account.png)



## 创建HTTP API帐户

您需要做的第一件事是创建新帐户。 此帐户包含有关如何处理身份验证以及流传入的数据是否与XDM兼容（即已匹配基础XDM架构的结构）的详细信息

执行以下任务：

1. 选择&#x200B;**新帐户**&#x200B;并添加以下详细信息：
   - 帐户名称 — > `Streaming Ingestion - <Your Initials>`
1. 保留&#x200B;**启用身份验证**&#x200B;的切换开关已禁用
1. 取消选中&#x200B;**XDM兼容**&#x200B;的复选框
1. 单击&#x200B;**连接到源**&#x200B;按钮以继续

>[!CAUTION]
>
>请勿打开&#x200B;**启用身份验证**&#x200B;或选中&#x200B;**XDM兼容**&#x200B;的框。 这会破坏实验室

屏幕应如下所示：

单击新HTTP API帐户的“连接到源”后![屏幕](assets/setup-source-connect-to-source-screen.png)



现在，您应该会看到一个绿色复选框，其中显示消息“已连接”。 单击右上角的&#x200B;**下一步**&#x200B;按钮继续设置数据流：

在设置HTTP API帐户后，![带有已连接消息的绿色复选框](assets/setup-source-green-checkbox-with-connected-message.png "您应该看到带有已连接的绿色复选框")



## 上传示例数据

>[!NOTE]
>
>如果尚未下载，请确保下载[示例文件](../sample-files.md)



1. 在屏幕的Source数据架构部分中，从您从上一个实验室下载的本地文件系统上传JSON文件&#x200B;**Lab\_Single\_Customer\_sample.json**。
1. 上传文件后，预览如下所示。 单击右上角的&#x200B;**下一步**&#x200B;按钮继续。 观察birth_Date字段的格式(YYYY-MM-DD)与之前在批量摄取实验室中看到的MM/DD/YYYY格式有何不同。

![管道设计和验证的上传Lab_Single_Customer_sample.json记录预览](assets/setup-source-sample-customer-record-for-pipeline-design-and-validation.png)

>[!NOTE]
>
>JSON示例文件包含用于设计和验证管道的单个记录。 如果要滚动，则必须单击XDM节点以滚动节点。



## 配置数据流详细信息

在此屏幕中，您将创建一个特定数据流，以便利用您设置的HTTP API帐户。  每个帐户可以有多个数据流。  在此方案中，您需要为流式处理客户帐户数据创建一个数据流。 数据流需要源帐户、具有关联架构的数据集以及配置详细信息之间的关联。

执行以下步骤：

1. 创建新数据集并将其命名为 — > `Customer Account Stream - <Your Initials>`
1. 选择&#x200B;**架构**&#x200B;作为 — >`dep: Customer Account`
1. 确保&#x200B;**配置文件数据集**&#x200B;切换为&#x200B;**已启用**。  如果没有&#x200B;**启用**，则将其启用。
1. 更新&#x200B;**数据流名称**，如下所示：
   - `Customer Account Stream - <Your Initials>`
1. 单击&#x200B;**下一步**&#x200B;按钮继续

![正在为客户帐户流数据集配置数据流详细信息](assets/setup-source-configuring-a-dataflow.png)

>[!NOTE]
>
>如果您没有为配置文件启用数据集，则数据仅会流入数据湖。 您在配置文件或身份图中看不到流事件。
