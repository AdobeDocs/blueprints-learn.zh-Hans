---
title: 验证和验证
description: 在UI中预览流式数据集，并运行SQL查询以验证摄取的记录和嵌套架构字段。
doc-type: article
solution: Experience Platform
exl-id: fbdb0b6b-08b6-49b8-b6ab-d59d5941c678
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---


# 验证和验证

## 预览数据集

1. 单击&#x200B;**数据集**
1. **找到**&#x200B;并&#x200B;**单击**&#x200B;您创建的数据集名称。

![在“数据集”窗格中访问创建的数据集](assets/verification-and-validation-access-the-dataset-in-the-datasets-pane.png "在“数据集”窗格中访问数据集")



1. 单击右上角的&#x200B;**预览数据集**

![预览数据集按钮位于数据集屏幕的右上角](assets/verification-and-validation-preview-dataset-button.png "预览数据集位于右上角")



1. **通过单击显示架构层次结构的左窗格，验证**&#x200B;和&#x200B;**验证**&#x200B;您摄取的相同记录。

![使用架构层次结构窗格验证和验证摄取的记录](assets/verification-and-validation-verify-and-validate-the-dataset.png "验证和验证数据集")

>[!NOTE]
>
>**预览数据集**&#x200B;将仅显示数据集的前几行。 数组对象不可查看。



## 查询数据集

1. **关闭**&#x200B;预览
1. 在“数据集”屏幕中，单击&#x200B;**表名称**&#x200B;上的复制图标。 在下面的示例屏幕中，表名称为`customer_account_sm`

![从数据集屏幕复制表名以用于查询](assets/verification-and-validation-copy-the-table-name.png "复制表名")



1. 导航到&#x200B;**查询**&#x200B;部分

1. 单击&#x200B;**创建查询**

![从查询节访问查询编辑器](assets/verification-and-validation-access-the-query-editor.png "访问查询编辑器")



1. 打开&#x200B;**增强型查询编辑器**&#x200B;的切换开关

![已启用增强型查询编辑器切换的查询编辑器界面](assets/verification-and-validation-enhanced-query-editor-toggle.png "查询编辑器界面")



1. 在&#x200B;**编辑器**&#x200B;中复制并粘贴以下SQL查询。 请记得使用您在步骤2中获得的值替换`<table_name>`。

```sql
SELECT * FROM <table_name>
```



1. 按&#x200B;**播放**&#x200B;按钮。

1. **预览**&#x200B;结果。

1. 此外，执行以下SQL查询以检索XDM架构以及数据：

```sql
SELECT to_json(shippingAddress) FROM <table_name>
```



1. 要访问`postalCode` **节点**&#x200B;中的数据，您可以键入：

```sql
SELECT shippingAddress.postalCode FROM <table_name>
```

>[!TIP]
>
>恭喜！  您已成功摄取并创建了一组实时客户配置文件示例
