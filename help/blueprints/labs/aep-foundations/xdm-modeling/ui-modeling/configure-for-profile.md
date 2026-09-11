---
title: 为配置文件配置
description: 标记主要和人员标识字段，构建架构关系，为实时客户个人资料启用架构，并查看个人资料合并架构。
doc-type: article
solution: Experience Platform
exl-id: 52cfc0d2-ba8c-4f81-9e03-c5c2c5e276b7
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 0%

---


# 为配置文件配置

## 概述

为了将架构用于Real-time Customer Profile，您需要首先确保其配置正确。 这意味着将您在LID实验室中识别的内容作为主/人员身份、关系身份等，并确保对每个架构进行这些配置。 完成所有操作后，您可以“翻转开关”并启用架构以用于用户档案。

查看Connection 5G ERD上的XDM ，您会看到以下有关客户帐户架构的信息。  这是为了利用Real-Time Customer Profile中的架构而剩下的工作。



![Connection 5G XDM on Paper客户帐户架构及其相关查找表](assets/configure-for-profile-connection-5g-erd-customer-account-schema.jpeg "Connection 5G XDM on Paper客户帐户架构及其相关查找表")


## 标记主要标识字段

如果要与实时客户档案一起使用，则每个架构都需要主标识字段。 请按照以下步骤将字段标记为主要标识。

1. 打开您创建的&#x200B;**客户帐户**&#x200B;架构
1. 通过单击架构中的字段选择&#x200B;**\_\&lt;tenant-name>.customerID**&#x200B;字段
1. 在右边栏中，选中&#x200B;**标识**&#x200B;和&#x200B;**主标识**&#x200B;复选框
1. 从下拉列表中选择&#x200B;**customerID**&#x200B;命名空间
1. 完成后，单击右边栏中的&#x200B;**应用**&#x200B;按钮，然后&#x200B;**保存**&#x200B;您的更改。

![将customerID字段标记为主要标识](assets/configure-for-profile-mark-customerid-as-primary-identity.png "将_dxp.customerID标记为主要标识")

>[!NOTE]
>
>单击应用后，验证您的字段中是否显示指纹，如下所示
>
>将字段标记为标识后显示的![指纹图标](assets/configure-for-profile-identity-thumbprint-icon.png)
>
>

>[!NOTE]
>
>另请注意，您现在应在左边栏中看到以下项目。 此处将显示身份（主要或非主要），**主要**&#x200B;身份也标记为必填字段。
>
>
>
>左边栏中的![标识部分显示主要和非主要标识字段](assets/configure-for-profile-identities-list-in-left-rail.png)



## 标记人员身份字段

请记住，要与Real-time Customer Profile **一起使用的每个架构都可以包含**&#x200B;其他人员标识字段。 要将字段标记为人员标识，请对您之前创建的客户帐户架构执行以下操作。

1. 选择&#x200B;**personalEmail.address**&#x200B;字段
1. 选中右边栏中的&#x200B;**标识**&#x200B;复选框
1. 从下拉列表中选择&#x200B;**Email**&#x200B;身份命名空间
1. **应用并保存**&#x200B;您的更改

![将personalEmail.address字段标记为身份](assets/configure-for-profile-mark-personal-email-as-identity.png "将personalEmail.address标记为身份")

>[!NOTE]
>
>单击应用后，验证指纹是否显示在字段中



## 创建架构关系

要按照ERD中的概述将Plan架构与客户帐户架构相关联，您需要定义一种关系。 按照以下步骤在客户帐户和计划（查找）架构之间创建架构关系。

### 添加关系

1. 选择Plan对象中的&#x200B;**planID**&#x200B;字段，如下所示
1. 在右边栏中，单击&#x200B;**添加关系**&#x200B;图标

![添加在planID字段上选定的关系图标](assets/configure-for-profile-add-relationship-to-planid-field.png "将关系添加到planID字段")



### 定义关系

1. 在类型选择框中，选择&#x200B;**一对一**&#x200B;选项
1. 在“引用架构”选择框中，选择名为&#x200B;**dep： Plan \[Lookup]**&#x200B;的架构（这是为您预先创建的）
1. 单击&#x200B;**应用**&#x200B;和&#x200B;**保存**

![正在定义与计划[查找]架构的一对一关系](assets/configure-for-profile-define-one-to-one-relationship.png)



### 确认关系

完成后，您应该会看到您创建的关系，如下面的屏幕快照中所示。

![确认已创建客户帐户与计划架构之间的关系](assets/configure-for-profile-relationship-created-confirmation.png "已创建关系")



## 配置配置配置文件的架构

Real-time Customer Profile将合并来自不同来源的数据，以构建每个客户的完整视图。 如果希望架构捕获的数据参与此过程，则必须配置架构以在配置文件中使用。 为此，您需要执行以下步骤：



1. 打开新创建的&#x200B;**客户帐户 — \[您的缩写]**&#x200B;架构
1. 从左边栏中单击架构的标题
1. 通过切换右边栏中的&#x200B;**ON**&#x200B;配置文件切换来配置配置配置文件的架构
1. 在出现的模式窗口中，单击&#x200B;**启用**&#x200B;按钮
1. 完成时，不要忘记&#x200B;**保存**&#x200B;您的架构！

在右边栏中为客户帐户架构启用了![配置文件切换](assets/configure-for-profile-schema-profile-toggle.png "架构配置文件切换")

在切换配置文件开关后显示的模式窗口中显示![启用按钮](assets/configure-for-profile-enable-profile-modal.png)

>[!TIP]
>
>恭喜！  您刚刚创建了一个要与Real-time Customer Profile一起使用的架构。



## 查看配置文件合并架构

如前所述，XDM和实时客户档案的强大功能是能够将个人的各种片段及其行为组合在一起。  这称为客户的“联合视图”。  在以下步骤中，您会预览为实时客户配置文件配置的每个XDM类的合并外观

1. 在左边栏中导航到&#x200B;**配置文件**
1. 选择顶部菜单中的&#x200B;**合并架构**&#x200B;选项卡
1. 从下拉列表中选择&#x200B;**XDM Individual Profile**&#x200B;类

浏览XDM Individual Profile类，然后花些时间查看其他类，如XDM ExperienceEvent或Plan类。

XDM个人资料类的![个人资料合并架构视图](assets/configure-for-profile-profile-union-schema-view.png "个人资料合并架构视图")

>[!NOTE]
>
>请注意，显示的架构是沙盒中所有启用配置文件的架构的聚合合并视图。 层级XDM结构中的类似字段会合并在一起，而具有不同名称和/或层级的字段会添加到整体视图中。

>[!NOTE]
>
>只有基于XDM个人资料的类才能在类似命名的字段之间执行合并。
