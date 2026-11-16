---
title: 筛选行
description: 了解如何通过拆分活动筛选掉已退出的客户行，并使用更改维度将工作流的目标维度与短信渠道配置保持一致。
doc-type: article
solution: Experience Platform
exl-id: fb556a27-5c73-4457-ae98-dba43d445c7f
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 689f227965176096ccd1785699de65046af4f3d3
workflow-type: tm+mt
source-wordcount: '371'
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



## 添加短信活动

1. 在工作流画布上，单击添加的分割条件后面的&#x200B;**+**&#x200B;图标，然后选择&#x200B;**移动消息活动**

   ![在拆分条件后添加移动消息活动](assets/filter-the-lines-add-sms-activity.png)

   ![短信活动已添加到工作流画布](assets/filter-the-lines-sms-activity-on-canvas.png)



2. 在右边栏中，单击编辑移动设备消息按钮以开始配置短信消息

   右边栏中的![编辑移动消息按钮](assets/filter-the-lines-edit-sms-button.png)



3. 在顶部导航中，单击操作菜单项，然后从移动设备消息配置下拉列表中选择您之前创建的渠道。

![短信配置已成功显示所选渠道](assets/filter-the-lines-sms-configuration-selected.png)




## 回顾

您过滤掉了所有因选择退出而不允许使用短信消息进行定位的行，并为允许进行定位的用户添加了短信活动。
