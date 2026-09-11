---
hold: true
title: 创建数据流
description: 使用新数据集配置批次源数据流，启用配置文件和部分摄取，并上传一个示例客户帐户CSV文件。
doc-type: article
solution: Experience Platform
exl-id: 70145966-d6c0-4741-8216-903de0d61e1d
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---


# 创建数据流

## 导航到源

1. 在Adobe Experience Platform UI中，导航到以下位置：\
   **源** -> **目录** -> **本地系统**
1. 下一步单击&#x200B;**本地文件上传**&#x200B;卡的&#x200B;**添加数据**&#x200B;按钮

![为源目录中的本地文件上传卡添加数据按钮](assets/create-dataflow-local-file-upload-add-data.png "访问数据登录区")



## 设置数据流

1. 在数据流详细信息屏幕中，选择&#x200B;**新建数据集**。
1. 将输出数据集命名为&#x200B;**客户帐户 — \&lt;您的首字母>**
1. 从下拉列表中选择&#x200B;**dep： Customer Account**&#x200B;架构。
1. 打开&#x200B;**配置文件数据集**切换框。
（如果未打开此功能，则配置文件存储区将无法监视是否有新数据进入此数据集，因此不会将此数据摄取到配置文件中）
1. 打开&#x200B;**启用部分摄取**。
（如果不打开此功能，则当只有一个记录出错时，整个摄取可能会失败）
1. 将数据流名称设置为&#x200B;**客户帐户批次 — \&lt;您的首字母>**
1. 打开所有警报&#x200B;**源数据流启动/成功/失败**

![数据流详细信息屏幕，已配置新数据集、配置文件和部分摄取设置](assets/create-dataflow-new-dataset-flow-details.png "数据流详细信息")

>[!NOTE]
>
>**启用部分摄取**&#x200B;指定错误数（**INGEST**&#x200B;和&#x200B;**DCVS**），以在整个数据流声明失败之前可以失败的记录总数的百分比表示。

>[!CAUTION]
>
>在继续之前，请确保已为配置文件和部分摄取启用了&#x200B;**数据集**！

1. 如果一切正常，请单击屏幕右上角的&#x200B;**下一步**&#x200B;按钮继续下一步。



## 上传样本文件

1. 从[样本文件](../sample-files.md)下载样本文件，以供本实验使用
1. 在UI中拖放和/或上传&#x200B;**Lab\_Customer\_Account.csv**&#x200B;文件。  完成后，您的屏幕应如下所示。

![在源数据屏幕中预览已上传的客户帐户CSV文件](assets/create-dataflow-uploaded-csv-preview.png "访问Adobe Experience Platform中的Azure存储资源管理器文件")

1. 在预览窗格中，查看以下属性并注意以下事项：

- **sms\_optIn**&#x200B;是同意字段，缺少几个值（在预览中显示为 — ）
- **account\_create\_date**&#x200B;没有正确的日期格式。 它在一个字符串中包含字符串值以及日期和时间值。
- **account\_end\_date**&#x200B;具有正确的日期格式。



![预览显示sms_optIn字段缺少多个同意值](assets/create-dataflow-sms-optin-missing-values.png "sms_optin")



![预览显示不一致格式的account_create_date和account_end_date字段值](assets/create-dataflow-account-create-end-date-preview.png "account_create_date &amp; account_end_date")

>[!NOTE]
>
>在本实验后面的映射步骤中，您将需要处理缺少的值、日期以及格式不正确的字段

1. 单击屏幕右上角的&#x200B;**下一步**&#x200B;按钮以继续下一步
