---
title: 配置短信渠道
description: 了解如何配置基于Twilio的短信渠道及其执行维度，以便在编排的营销活动中使用。
doc-type: article
solution: Experience Platform
exl-id: 63c994f2-4b6b-42e9-aa82-cb6697390a08
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---


# 配置短信渠道

## 目标

在接下来的步骤中，您将配置短信渠道。 这是必需的，这样您以后在构建营销活动时，便可以向各个线路持有人发送消息。



## 导航到渠道

1. 在Adobe Journey Optimizer中，转到&#x200B;**管理** -> **渠道**&#x200B;菜单。
1. 选择&#x200B;**SMS设置** → **API凭据**。
1. 单击&#x200B;**创建API凭据**。

![在管理渠道菜单“导航到SMS设置”中导航到SMS设置和API凭据](assets/configure-sms-channel-navigate-to-sms-settings.png "导航到SMS设置")



## 定义SMS API凭据

首先，创建AJO将用于发送出站SMS请求的API连接器。

1. 在SMS供应商下，选择&#x200B;**Twilio**。
1. 使用您自己的[Twilio试用帐户](https://www.twilio.com/try-twilio)输入以下API凭据详细信息：
   - **名称：** `DEP SMS`
   - 在您的Twilio控制台仪表板上找到&#x200B;**帐户SID：**
   - 在您的Twilio控制台仪表板上找到&#x200B;**身份验证令牌：**（单击&#x200B;**查看**&#x200B;以显示它）
1. 单击&#x200B;**提交**&#x200B;注册API凭据

>[!NOTE]
>
>在开始此步骤之前，您需要一个带已验证电话号码的免费Twilio试用帐户。 在[twilio.com/try-twilio](https://www.twilio.com/try-twilio)注册，然后在Twilio控制台功能板上找到您的帐户SID和身份验证令牌。

Twilio供应商的![SMS API凭据字段](assets/configure-sms-channel-enter-api-credentials.png)



## 创建短信渠道配置

现在，您将将此API凭据映射到历程和营销活动可以使用的渠道配置。

1. 导航到&#x200B;**渠道** → **常规设置** → **渠道配置**。

   ![导航到“常规设置”下的渠道配置](assets/configure-sms-channel-navigate-channel-configurations.png)



2. 单击&#x200B;**创建渠道配置**。

   ![创建渠道配置按钮](assets/configure-sms-channel-click-create-configuration.png)



3. 使用下列值填写短信渠道配置设置：
   - **名称：** `Relational-SMS-Multi-Entity`
   - **频道：** `Mobile Message`
   - **营销操作：** `SMS Targeting`

>[!NOTE]
>
>如果您收到错误消息表明用户没有权限，请忽略该权限并继续。

## 短信设置

选择“渠道”作为移动消息时，将显示一个名为“短信设置”的新部分。 请填写以下详细信息：

- **移动消息类型：** `Marketing`
- **移动消息配置：** `DEP SMS`
- **发件人号码：** `01234567890`
- **子域：** `leave blank`
- **选择退出号码：** `leave blank`

![具有发件人号码和移动消息类型的短信设置](assets/configure-sms-channel-sms-settings-fields.png)



## 执行详细信息

1. 在执行详细信息下，单击选项卡&#x200B;**编排的营销活动**

   在执行详细信息下![编排的活动选项卡](assets/configure-sms-channel-execution-details-tab.png)



2. 确保选中&#x200B;**已启用**&#x200B;复选框

   ![为编排的活动选中了](assets/configure-sms-channel-enabled-checkbox.png)启用复选框



3. 在子部分&#x200B;**执行维度**&#x200B;下的下一个部分，请确保按如下方式设置以下内容：
   - **根据以下日期传递消息：** `Target + Secondary Dimension`
   - **配置文件目标Dimension：** `dep-rel: Customer Account - customer_id`
   - **辅助Dimension：** `Customer Line`

   ![具有目标和辅助维度的执行维度设置](assets/configure-sms-channel-execution-dimension-setup.png)

   在执行维度设置“次要Dimension”](assets/configure-sms-channel-secondary-dimension-detail.png "次要Dimension")中，将![次要Dimension设置为客户行

   >[!NOTE]
   >
   >这告知编排的营销活动，当它发送消息时，应该为每个记录投放一条与Profile Target Dimension匹配的消息。



4. 在执行地址标题下，确保选择&#x200B;**辅助Dimension**&#x200B;的单选按钮，然后单击&#x200B;**短信执行字段**&#x200B;上的编辑按钮

   ![使用编辑字段将执行地址设置为辅助Dimension](assets/configure-sms-channel-execution-address-selection.png)



5. 在弹出窗口中，单击架构&#x200B;**dep-rel： Customer Line**&#x200B;并选择&#x200B;**移动电话**。

   dep-rel： Customer Line架构的![架构弹出窗口](assets/configure-sms-channel-customer-line-schema-popup.png)

   ![从依赖：客户线路架构“手机字段”中选择的“手机”字段](assets/configure-sms-channel-mobile-phone-field-selected.png "手机字段")



6. 确认最终执行详细信息部分与以下内容匹配

![与所需设置匹配的最终执行详细信息配置](assets/configure-sms-channel-final-execution-details.png)



## 提交和审查

1. 您可以单击&#x200B;**提交**&#x200B;按钮以完成配置并看到一条成功消息

   提交通道配置后![成功消息](assets/configure-sms-channel-submit-success-message.png)



2. 在渠道配置清单页面上，请确保状态显示为&#x200B;**活动**，然后再继续

   ![渠道配置状态显示为“活动”](assets/configure-sms-channel-active-status.png)

   >[!CAUTION]
   >
   >等到状态变为&#x200B;**活动**&#x200B;为止，否则将来的实验室步骤将严重失败



3. 当状态变为“活动”时，表示您已完成！

>[!TIP]
>
>🚀博耶！ 您的短信渠道现已上线，准备就绪！



## 回顾

您现在已了解如何成功配置短信渠道。  请注意，这是一个基于API的短信，因此根据您的提供商，他们可能会使用其他方法进行身份验证。

如有需要，您可以在[此处](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)阅读更多内容。
