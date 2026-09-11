---
title: 保存受众
description: 了解如何从编排的活动工作流更改维度、删除重复项并将受众保存到受众门户。
doc-type: article
solution: Experience Platform
exl-id: 6422ea8d-146b-4fc7-86e6-491f77590ca1
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# 保存受众

## 目标

在接下来的几步中，您将创建的受众保存回Audience Portal，以便Adobe Experience Platform及其应用程序中的其他解决方案可以将其用于自己的用例。



## 更改维度

1. 在工作流画布上，单击&#x200B;**保存受众**&#x200B;分支上的&#x200B;**+** **图标**，然后从活动列表中选择&#x200B;**更改维度**&#x200B;活动

![在“保存受众”分支上添加“更改维度”活动](assets/save-the-audience-add-change-dimension.png)



&#x200B;2. 更新更改维度的属性，如下所述：
   - **标签：** `Convert Line to Account`
   - **新目标维度：** `dep-rel: Customer Account`

![更改维度标签和新目标维度字段](assets/save-the-audience-change-dimension-label.png)

![客户帐户已选为新的目标维度](assets/save-the-audience-select-customer-account.png)

>[!NOTE]
>
>**您问：**  请记住，要加入Real-time Customer Profile（这是您保存受众的位置），您必须使用您配置的配置文件目标映射，该映射仅来自部门：客户帐户架构的加入。



&#x200B;3. 完成后，这是您的画布的外观。  保存您所做的工作！

添加更改维度活动后![工作流画布](assets/save-the-audience-canvas-after-change-dimension.png)



## 删除重复结果

1. 在更改维度活动后单击&#x200B;**+** **图标**，然后从活动列表中选择&#x200B;**重复数据删除**&#x200B;活动

![在更改维度后添加重复数据删除活动](assets/save-the-audience-add-deduplication-activity.png)



&#x200B;2. 将重复数据删除活动的标签更新为`Dedup customer id`

![重复数据删除活动标签设置为重复数据删除客户ID](assets/save-the-audience-deduplication-label.png)



&#x200B;3. 现在单击&#x200B;**+添加属性**&#x200B;按钮，并从标题为&#x200B;**客户ID**&#x200B;的架构中选择字段

删除重复项活动![添加属性按钮](assets/save-the-audience-add-attribute-button.png)

从架构中选择的![客户ID字段](assets/save-the-audience-select-customer-id-field.png)



&#x200B;4. 在“重复数据删除”设置下，确保您具有以下设置：
   - **要保留的重复项：** `1`
   - **重复数据删除方法：** `Random selection`

![要保留的重复项删除重复项设置和方法](assets/save-the-audience-deduplication-settings.png)

>[!NOTE]
>
>利用重复数据删除的其他选项，可指定您自己的自定义逻辑。  大多数情况下，如果您需要删除重复项，将使用表的主键进行删除。



&#x200B;5. 完成后，您的画布将如下所示。 在继续之前，单击右上角的&#x200B;**保存**&#x200B;按钮。

![已在画布上完全配置重复数据删除活动](assets/save-the-audience-deduplication-configured.png)



## 添加“保存受众”活动

1. 在重复数据删除活动后单击&#x200B;**+**&#x200B;图标，然后选择&#x200B;**保存受众**&#x200B;活动

![在重复数据删除后添加保存受众活动](assets/save-the-audience-add-save-audience-activity.png)

&#x200B;2. 在右边栏中，将活动的属性设置为以下内容：
   - **受众标签**： `Apple Upgrade Eligible Customer Accounts`
   - **配置文件映射字段**： `dep-rel: Customer Account - customer id`

![保存受众标签和配置文件映射字段设置](assets/save-the-audience-label-and-profile-mapping.png)

>[!NOTE]
>
>“配置文件映射字段”是您之前设置的字段，以便关系存储可以联接到实时客户配置文件。  该用户档案已建模为客户帐户级别，因此您要将受众保存在同一层中。  因此，需要更改维度和重复数据删除。



## 受众字段映射

默认情况下，定向维度的主键（即客户ID）将作为字段添加到受众。 如果您查看右侧并展开字段，则可以看到此内容。  需要注意两点：

- **Source受众字段** —>引用来自关系架构的字段
- **目标受众字段** —>将作为受众保存的一部分创建的字段的名称

![默认客户ID字段已添加到保存受众活动](assets/save-the-audience-default-field-added.png)

>[!NOTE]
>
>请注意，目标受众字段的名称是`Dep_rel_customer_account_Customer_id`。  你应该把它变更为营销人员更容易理解的东西，不要找借口。



## 修复默认受众字段

1. 将默认的“目标受众”字段重命名为&#x200B;**Customer\_ID**，如下所示：

![目标受众字段已重命名为Customer_ID](assets/save-the-audience-field-renamed.png)

>[!TIP]
>
>现在您有了人类可辨认的字段名称🎉



&#x200B;2. 单击&#x200B;**开始**&#x200B;按钮以运行工作流。 您的工作流现在看起来像这样，您会看到如下计数：
   - 生成受众： `65`
   - 将行转换为帐户： `65`
   - 重复数据删除客户ID： `46`

![显示生成、转换和重复数据删除计数的工作流测试运行](assets/save-the-audience-test-run-counts.png)

>[!NOTE]
>
>保存受众活动将仅在发布工作流时创建受众，而不是仅在工作流刚启动时创建。 创建受众后，该受众将包含您添加到它的所有属性，并将在下次计划每日运行分段服务作业期间加入实时客户档案。

>[!CAUTION]
>
>不要发布您的工作流！



## 挑战

如果在保存受众之前不进行重复数据删除，会发生什么情况？  受众将存储所有65条记录还是仅存储46条？

![提前保存受众挑战方案但不进行重复数据删除“提前保存具有重复数据删除活动的受众”](assets/save-the-audience-challenge-without-dedup.png "提前保存具有重复数据删除活动的受众")



## 回答

受众将存储所有65条记录，但读取受众活动将根据连接条件😁在导入时删除这些记录







## 回顾

现在，您应该很好地了解“保存受众”的工作方式以及重复数据删除重要的原因。  请记住，您始终需要定义配置文件目标映射，因为关系存储数据必须知道如何联接到实时客户配置文件。  配置文件目标映射为连接条件🙂
