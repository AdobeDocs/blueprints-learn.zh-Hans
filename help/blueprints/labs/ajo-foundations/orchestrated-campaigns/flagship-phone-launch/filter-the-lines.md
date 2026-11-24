---
title: 筛选行
description: 了解如何通过拆分活动筛选掉已退出的客户行，并使用更改维度将工作流的目标维度与短信渠道配置保持一致。
doc-type: article
solution: Experience Platform
exl-id: fb556a27-5c73-4457-ae98-dba43d445c7f
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 8d5a87f094e2fba7abd7f5a9acf8e9e775d9b534
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%
---

# 筛选行

## 目标

在接下来的步骤中，您将过滤掉实际上不允许使用短信消息定向的所有行，因为这些行在行级别被禁用。  在此不能依赖配置文件同意，因为这是行级目标。



## 设置拆分活动

1. 单击“分支”活动底部过渡处的&#x200B;**+**&#x200B;图标，然后在弹出窗口中选择&#x200B;**Split**&#x200B;活动。

   ![向底部分支添加拆分活动](assets/filter-the-lines-add-split-activity.png)



2. 在右边栏中，更新标签以声明以下内容： `Filter out opt'd out lines`

   ![拆分活动标签设置为筛选退出选择退出行](assets/filter-the-lines-set-split-label.png)



3. 在右边栏中，展开默认区段&#x200B;**子集**&#x200B;部分，然后单击&#x200B;**创建过滤器**&#x200B;按钮

   ![子集部分中的“创建过滤器”按钮](assets/filter-the-lines-create-filter-button.png)



4. 添加条件以确保您删除所有选择禁用短信消息的客户行，然后单击&#x200B;**确认**。

   ![条件删除选择退出短信的客户行](assets/filter-the-lines-sms-optin-condition.png)

   >[!NOTE]
   >
   >您需要了解如何创建条件，但最终结果与上面的屏幕快照匹配。  你搞定了！



5. 单击右上角的“保存”按钮以保存您所做的工作。  你的画布现在看起来好像\...

保存拆分活动后![工作流画布](assets/filter-the-lines-canvas-after-split-save.png)



## 添加更改维度

1. 在工作流画布上，单击添加的分割条件后面的&#x200B;**+**&#x200B;图标，然后选择&#x200B;**更改维度**&#x200B;活动

   ![在拆分条件后添加更改维度活动](assets/filter-the-lines-add-change-dimension-activity.png)

2. 更新如下所述的更改维度的属性，然后单击&#x200B;**确认**：
标签： `Convert Line to Account`
新目标维度： `dep-rel: Customer Account`

   ![编辑目标维度](assets/filter-the-lines-add-edit-target-dimension.png)

   ![编辑目标维度](assets/filter-the-lines-add-select-target-dimension.png)



## 添加短信活动

1. 在添加的“更改”维度后单击&#x200B;**+**&#x200B;图标，然后选择&#x200B;**手机消息活动**

   ![在拆分条件后添加移动消息活动](assets/filter-the-lines-add-sms-activity.png)

   ![短信活动已添加到工作流画布](assets/filter-the-lines-sms-activity-on-canvas.png)



2. 在右边栏中，单击&#x200B;**编辑移动设备消息**&#x200B;按钮以开始配置短信消息

   右边栏中的![编辑移动消息按钮](assets/filter-the-lines-edit-sms-button-only.png)



3. 在顶部导航中，单击操作菜单项，然后从移动设备消息配置下拉列表中选择您之前创建的渠道。

![短信配置下拉列表显示无结果错误](assets/filter-the-lines-sms-configuration-no-results.png)

>[!CAUTION]
>
>哦，不🫨！  为什么没有结果？  您尚未设置短信渠道吗？  产品是否损坏？
>
>吓坏了!!!!!!!!!



## 惊慌时刻

短信的渠道配置已由您预先设置，当前看起来是……

![在配置SMS渠道实验室期间设置的执行详细信息配置](assets/configure-sms-channel-final-execution-details.png)

**阅读方式如下：**

- 针对在辅助维度（即客户行）中找到的相关记录数，为每个目标维度（即客户帐户）投放一条消息
- 使用在次要维度（即客户线路）中找到的手机号码执行每次短信投放

这种将许多消息发送到一个用户档案的独特功能是编排营销活动的主要功能之一，使其与历程有所不同。 但是，您进入移动消息活动的过渡设置为“客户帐户”。 这样，您就可以在发送时将它加入Real-time Customer Profile，以便将消息中的投放和跟踪信息归因于用户档案。


那么你怎样才能让这个运作起来呢？ 更改消息执行的目标以匹配您的渠道配置😀



## 更改Target并完成短信消息配置

1. 单击短信编辑屏幕上的返回按钮

   ![用于退出短信编辑屏幕的“上一步”按钮](assets/filter-the-lines-exit-sms-editor.png)



2. 选择移动设备消息活动后，在右边栏中，首先将Target选项从每个配置文件一个消息的默认选项更改为&#x200B;**每个辅助维度一个消息**&#x200B;选项，然后单击返回&#x200B;**编辑移动设备消息**

   ![更改目标，然后在右边栏中单击“编辑移动消息”按钮](assets/filter-the-lines-edit-sms-button.png)



3. 在顶部导航中，单击&#x200B;**操作**&#x200B;菜单项，然后从移动消息配置下拉列表中选择您之前创建的渠道。

   ![短信配置已成功显示所选渠道](assets/filter-the-lines-sms-configuration-selected.png)



## 回顾

您过滤掉所有因选择退出而不允许使用短信消息进行定位的行，将维度从行更改为帐户，并最终为允许进行定位的用户成功配置了短信活动。
希望您也了解了一件非常重要的事情 — **您的目标必须与要使用的渠道配置相匹配**
