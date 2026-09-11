---
title: 为配置文件配置
description: 了解如何使用AEP Profile personalEmail.address属性为历程和编排的营销活动配置电子邮件渠道。
doc-type: article
solution: Experience Platform
exl-id: bb85e0aa-554e-4527-bf91-e7fd4f69ce71
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 8%

---


# 为配置文件配置

## 目标

在接下来的步骤中，您将使用`personalEmail.address` AEP配置文件属性创建一个包含历程和编排营销活动的电子邮件渠道配置

## 创建渠道配置

1. 导航到菜单&#x200B;**管理→渠道→常规设置**&#x200B;下找到的&#x200B;**渠道配置**
2. 单击&#x200B;**创建配置**&#x200B;按钮

   ![创建渠道配置](assets/configure-for-profile-create-configuration-button.png)

3. 在创建向导中设置以下值：
   - **名称：** `Profile-Email`
   - **频道：** `Email`
   - **营销操作：** `Email Targeting`

![渠道配置详细信息](assets/configure-for-profile-channel-configuration-name-values.png)

>[!NOTE]
>
>选择电子邮件作为渠道时，将显示一个新部分&#x200B;**电子邮件设置**。

## 配置电子邮件类型

将&#x200B;**电子邮件类型**&#x200B;设置为&#x200B;**营销**

![电子邮件类型](assets/configure-for-profile-set-email-type-marketing.png)

## 配置子域

从&#x200B;**子域**&#x200B;下拉列表中，选择&#x200B;**email.dep-labs.com**

![已选择email.dep-labs.com的子域下拉列表](assets/configure-for-profile-select-email-subdomain.png "配置子域")

## 配置IP池详细信息

从&#x200B;**IP池**&#x200B;下拉列表中，选择&#x200B;**营销**

![已选择营销的IP池下拉列表](assets/configure-for-profile-select-marketing-ip-pool.png "IP池详细信息")

## 配置列表取消订阅

1. 确保为列表取消订阅启用&#x200B;**切换**
1. 在“列出取消订阅”首选项区域下，确保所有复选框都已&#x200B;**选中**
1. 在链接管理下，确保选中&#x200B;**Adobe managed**
1. 对于同意级别，请确保将此级别设置为&#x200B;**渠道**

![配置列表取消订阅](assets/configure-for-profile-configure-list-unsubscribe-settings.png)

## 配置标头参数

1. 按以下方式设置以下字段：
   - **发件人姓名：** `DEP Labs`
   - **来自电子邮件前缀：** `dep`
   - **回复姓名：** `DEP Labs Support`
   - **回复电子邮件：**`reply@email.dep-labs.com`
   - **错误电子邮件前缀：** `error`

![标头参数](assets/configure-for-profile-email-header-parameters.png)

## 配置密件抄送电子邮件

将此留空

>[!NOTE]
>
>您可以通过将电子邮件发送到密件抄送收件箱，保留所发送电子邮件的副本。 输入您选择的电子邮件地址，这样发送的每封电子邮件都会被密送至此密件抄送地址。 请注意，密件抄送地址域必须不同于委派给 Adobe 的任何子域。 此功能为可选项。 *如何对电子邮件使用密件抄送*

## 配置电子邮件重试参数

保留默认设置&#x200B;**小时**&#x200B;设置为&#x200B;**84**

## 配置URL跟踪参数

保留默认设置

## 执行详细信息

1. 完成&#x200B;**执行详细信息**&#x200B;部分。 在&#x200B;**历程和操作**&#x200B;选项卡 — > **执行维度**&#x200B;下，选择&#x200B;**配置文件**&#x200B;作为&#x200B;**Source**，然后单击&#x200B;**执行地址**&#x200B;部分下&#x200B;**投放地址**&#x200B;的编辑图标

   ![执行详细信息](assets/configure-for-profile-execution-details-journey-tab.png)

2. 单击标题为&#x200B;**个人电子邮件**&#x200B;的文件夹以将其打开

   ![交货地址](assets/configure-for-profile-personal-email-folder.png)

3. 单击`Address`字段上的&#x200B;**复选框**，然后单击&#x200B;**选择**&#x200B;按钮

   ![个人电子邮件作为传递地址](assets/configure-for-profile-select-address-checkbox-journeys.png)

4. 对于&#x200B;**配置文件**，`personalEmail.address`现在配置为&#x200B;**执行地址**&#x200B;部分下的&#x200B;**投放地址**

   ![已配置传递地址](assets/configure-for-profile-delivery-address-configured-journeys.png)

5. 单击“编排的营销活动”选项卡，然后&#x200B;**选中**“已启用”复选框。

   ![协调的活动配置](assets/configure-for-profile-enable-orchestrated-campaign-tab.png)

6. 在执行维度标题下，配置以下内容：
   - **为每**&#x200B;发送一封邮件`Target Dimension`
   - **配置文件目标Dimension：** `dep-rel: Customer Account - customer_id`

   ![定位Dimension](assets/configure-for-profile-target-dimension-settings.png)

7. 在执行地址下，配置以下内容：
   - **Source：** `Profile`
   - **交货地址：** `click on the Edit icon`

   ![执行地址](assets/configure-for-profile-execution-address-source-profile.png)

8. 搜索并单击`Personal Email`文件夹以将其打开

   ![个人电子邮件配置文件属性](assets/configure-for-profile-search-personal-email-folder.png)

9. 选择“个人电子邮件”文件夹中的`Address`字段，然后单击&#x200B;**选择**

   ![个人电子邮件作为传递地址](assets/configure-for-profile-select-address-field-orchestrated.png)

10. 对于&#x200B;**编排的营销活动**，**dep-rel：客户帐户 — customer\_id**&#x200B;配置为&#x200B;**执行维度**&#x200B;的&#x200B;**配置文件目标Dimension**，其中&#x200B;**执行地址**&#x200B;的&#x200B;**Source**&#x200B;为&#x200B;**配置文件**，而`personalEmail.address`为&#x200B;**投放地址**

![执行维度已配置](assets/configure-for-profile-orchestrated-execution-dimension-configured.png)

>[!NOTE]
>
>对于编排的营销活动，您可通过电子邮件定位客户帐户，因此您只需为每个用户档案&#x200B;*发送*&#x200B;封邮件。  您使用的执行地址来自配置文件本身（即存储在AEP配置文件的&#x200B;**personalEmail.address**&#x200B;属性下的内容）


## 查看并保存

1. 再次查看所有详细信息以确保它们相匹配。
1. 向上滚动并单击&#x200B;**提交**。

>[!NOTE]
>
>据观察，处理电子邮件渠道配置最多需要2小时！  天啊！
>
>在等待处理此渠道配置期间，请继续进行下一个练习。

>[!TIP]
>
>🚀一旦电子邮件渠道配置状态为&#x200B;**活动**，它即已准备就绪，现在可以直接在编排的营销活动的&#x200B;**电子邮件活动**&#x200B;中选择。

## 回顾

现在，您已了解如何创建电子邮件渠道配置，以便将AEP配置文件属性用于历程和编排的营销活动。
