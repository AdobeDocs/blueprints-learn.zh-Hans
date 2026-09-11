---
title: 使用数据登陆区
description: 安装和配置带有SAS URL的Azure Storage Explorer以连接到Adobe Experience Platform数据登陆区。
doc-type: overview-page
solution: Experience Platform
exl-id: d61bef25-7039-450d-a8e7-01bb12e8df7c
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# 使用数据登陆区

## 先决条件

如果您尚未下载Azure Storage Explorer，请立即下载，因为这是本实验的一项要求。  您可以通过以下链接找到下载内容：

[下载Azure存储资源管理器](https://azure.microsoft.com/en-us/blog/microsoft-azure-data-lake-storage-adls-in-storage-explorer-public-preview/)

1. 安装应用程序
1. 首次启动时接受最终用户许可协议

Azure Storage Explorer](assets/overview-end-user-license-agreement-screen.png "最终用户许可协议屏幕中的![最终用户许可协议屏幕")


## 使用Experience Platform配置Azure存储资源管理器

1. 打开Azure Storage Explorer并单击&#x200B;**选择资源图标**，然后选择&#x200B;**ADLS Gen 2容器或目录**

   ![在Azure Storage Explorer中选择ADLS Gen2容器或目录作为资源](assets/overview-choose-the-resource-as-shown-above.png)



1. 选择&#x200B;**共享访问签名URL (SAS)**&#x200B;并单击&#x200B;**下一步**

   ![选择SAS URL选项作为连接模式](assets/overview-choose-the-sas-url-option-as-the-mode-of-connection.png "选择SAS URL选项作为连接模式")



1. 输入显示名称&#x200B;**数据登陆区域**

   >[!NOTE]
   >
   >在提供SAS URL之前，您无法继续此步骤。  您可以从Experience Platform中获取此代码，这会在下一步中看到。

   ![命名连接数据登录区](assets/overview-name-the-connection.png "命名连接")



1. 转到Adobe Experience Platform ，然后通过执行以下操作导航到数据登陆区：

   - 导航到&#x200B;**源 — >目录**
   - 在源下选择&#x200B;**云存储**
   - 接下来找到&#x200B;**数据登陆区**&#x200B;卡
   - 单击数据登录区卡，然后单击右边栏上的&#x200B;**查看凭据**

   ![Adobe Experience Platform中具有查看凭据选项的数据登陆区域源信息卡](assets/overview-data-landing-zone-view-credentials.png "访问Adobe Experience Platform中的数据登陆区域Source信息卡")



1. 从显示的模式中复制&#x200B;**SASUri**。

   导航回Azure Storage Explorer并将&#x200B;**SASUri值**&#x200B;粘贴到您在上一步中留空的&#x200B;**Blob容器或目录SAS URL**&#x200B;中

   ![将SASUri值从Experience Platform复制到Azure Storage Explorer](assets/overview-copy-sas-uri-into-azure-storage-explorer.png "从Adobe Experience Platform复制SAS URL凭据并将其复制到Azure Storage Explorer")



1. 单击&#x200B;**下一步**&#x200B;继续

   ![将SAS URL凭据复制到连接信息的SAS URL部分](assets/overview-copy-sas-url-into-connection-info.png "将SAS URL凭据复制到连接信息的SAS URL部分")



1. 在“摘要”屏幕上，单击&#x200B;**连接**

![带有“连接”按钮的摘要屏幕](assets/overview-connect-screen.png "连接屏幕")



现在，您应该会看到如下所示的屏幕

![Azure Storage Explorer显示成功连接的数据登录区帐户](assets/overview-successfully-connected-account.png)

>[!TIP]
>
>恭喜！  您已成功配置Azure存储资源管理器
