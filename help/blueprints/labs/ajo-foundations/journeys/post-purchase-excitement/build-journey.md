---
title: 构建历程
description: 构建响应Order Shipped事件的单一历程，调用装运ETA的自定义操作，并发送个性化电子邮件。
doc-type: article
solution: Experience Platform
exl-id: 4dd15071-51e5-445a-932d-690d9a73a913
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '1061'
ht-degree: 0%

---


# 构建历程

## 学习目标

创建一个以配置的Order Shipped事件开始的统一历程，从外部服务获取ETA并发送电子邮件。

## 创建历程

转到&#x200B;**历程**&#x200B;并单击&#x200B;**创建历程 — 从头开始创建**

![创建历程 — 在Adobe Journey Optimizer中从头开始创建](assets/build-journey-create-journey-from-scratch.png)



## 历程属性

1. 使用以下内容更新右边栏中的历程属性：
   - **名称**： `Order Shipped Journey`
   - **描述**： `Notify customer that order has shipped. Include shipping details.`
   - **标记**： `Default`
   - **历程指标**：*留空*

     >[!NOTE]
     >
     >**空下拉列表？**
     >
     >别担心，继续前进。 在沙盒中创建的第一个历程需要“填充泵”。  发布历程后，此下拉菜单将具有可供选择的选项。

   - **允许重新进入**： `checked`

   - **重新进入等待期：** `5 minutes`

   - **访问标签**： *留空*

   - **时区**： `Your Local timezone`

   - **在等待和条件中使用配置文件时区**： `NOT checked`

   - **开始/结束日期**： *留空*

   - **超时或错误**： `30`

   - **上限规则：** *留空*

   - **优先级**： `0`



2. 如果一切正常，请单击&#x200B;**保存**&#x200B;按钮

历程属性面板的![保存按钮](assets/build-journey-save-journey-properties.png)




## 历程画布

### 添加单一事件

从&#x200B;**事件菜单**&#x200B;下的左窗格，将&#x200B;**orderShipped**&#x200B;事件拖放到画布上，如下所示

![将orderShipped事件从“事件”菜单拖到历程画布上](assets/build-journey-drag-order-shipped-event-onto-canvas.png)



![在历程画布上发出订单事件](assets/build-journey-drag-order-shipped-event-onto-canvas--2.png)





### 添加自定义操作

1. 如果左窗格展开&#x200B;**操作菜单**，然后将&#39;n拖放到画布上，则在orderShipped事件后生成名为&#x200B;**GetShippingDetails**&#x200B;的操作

![将GetShippingDetails自定义操作拖到orderShipped事件之后的画布上](assets/build-journey-drag-getshippingdetails-action-onto-canvas.png)

2. 在右边栏中的访问和隐私配置 — >营销操作下拉列表下，确保将该值设置为&#x200B;**无**

![访问和隐私配置中的“营销操作”下拉列表设置为“无”](assets/build-journey-set-marketing-action-to-none.png)

3. 在“端点配置” — >“查询参数”菜单下，单击orderid旁边的&#x200B;**铅笔图标**

![铅笔图标用于编辑终结点配置中的orderid查询参数](assets/build-journey-edit-orderid-query-parameter.png)

4. 在出现的模式窗口中，展开&#x200B;**Context** -> **orderShipped** -> **Order**，然后选择&#x200B;**Order ID (orderID)**&#x200B;并单击&#x200B;**确定**

![从orderShipped订单上下文字段中选择订单ID (orderID)](assets/build-journey-select-order-id-context-field.png)

5. 返回右边栏，确保“超时”或“错误”的选项为&#x200B;**取消选中**，然后单击&#x200B;**保存按钮**

取消选中![超时或错误选项，并突出显示“保存”按钮](assets/build-journey-uncheck-timeout-or-error.png)



### 添加电子邮件操作

1. 在“操作”菜单下，将“**操作**”操作拖放到画布上的GetShippingDetails操作之后

![将“操作”节点拖到GetShippingDetails操作之后的画布上](assets/build-journey-drag-email-action-onto-canvas.png)

2. 为营销操作选择&#x200B;**电子邮件**，然后选择&#x200B;**添加**。

![选择电子邮件作为营销操作，然后单击“添加”](assets/build-journey-select-email-marketing-action.png)

3. 在右边栏中，单击&#x200B;**配置操作**

右边栏中的![配置操作按钮](assets/build-journey-click-configure-action.png)

4. 将&#x200B;**电子邮件渠道配置**&#x200B;设置为`Profile-Email`，然后单击&#x200B;**编辑内容**

![电子邮件渠道配置设置为使用编辑内容链接的个人资料电子邮件](assets/build-journey-set-profile-email-channel-configuration.png)



### 添加电子邮件正文内容

对于内容，您将保持简单。 就跟愚蠢的简单一样。

1. 将主题行更新为`Order Shipped`，然后单击&#x200B;**编辑电子邮件正文按钮**

![主题行已更新为“已发送订单，并带有编辑电子邮件正文”按钮](assets/build-journey-update-subject-line-order-shipped.png)

2. 在顶部栏中，单击&#x200B;**从头开始设计**&#x200B;内容块

![在顶部栏中从草稿设计内容块](assets/build-journey-click-design-from-scratch.png)

3. 从结构容器下的左栏将&#x200B;**1:1列**&#x200B;拖放到画布上

![将1:1列结构元素拖动到电子邮件画布上](assets/build-journey-drag-1-1-column-onto-canvas.png)

4. 然后在“内容”容器下，将&#x200B;**Text**&#x200B;组件拖放到您的&#x200B;**1:1列**&#x200B;中

![将文本组件拖入1:1列](assets/build-journey-drag-text-component-into-column.png)

5. 单击进入文本组件并&#x200B;**删除当前文本**，然后单击&#x200B;**添加Personalization**&#x200B;图标

删除默认文本后![添加Personalization图标](assets/build-journey-click-add-personalization-icon.png)

6. 在左边栏中，单击&#x200B;**上下文属性**&#x200B;文件夹，然后导航到&#x200B;**Journey Orchestration** -> **操作**，并选择&#x200B;**GetShippingDetails**

![选择“上下文属性 — Journey Orchestration — 操作”下的GetShippingDetails](assets/build-journey-select-getshippingdetails-contextual-attribute.png)

7. 现在，在电子邮件的主体中&#x200B;**将以下JSON复制并粘贴到** Personalization编辑器中&#x200B;****

```json
{{profile.person.name.firstName}}, your order has shipped
ETA: 
Tracking Number: 
```

8. 按如下方式添加个性化字段（**单击左边栏**&#x200B;上的字段旁边的加号“+”）：
   - **ETA：** `eta`
   - **跟踪号：** `tracking_number`

![ETA和跟踪号码个性化字段已添加到电子邮件](assets/build-journey-add-eta-tracking-number-fields.png)

>[!NOTE]
>
>单击&#x200B;**+符号**&#x200B;以将个性化属性从边栏添加到画布。  它会将其放在光标所在的位置，以确保您正确“对齐”

>[!NOTE]
>
>您的电子邮件将使用上下文属性（ETA和跟踪编号）和配置文件属性（名字）的组合。 如果要添加其他配置文件属性，可以单击“配置文件属性”选项卡并选择您看到的任何内容。
>
>用于添加其他配置文件属性的![配置文件属性选项卡](assets/build-journey-profile-attributes-tab.png)

9. 单击屏幕底部的&#x200B;**验证**&#x200B;按钮，并确保没有错误

![验证按钮，屏幕底部未显示错误](assets/build-journey-click-validate-button.png)

10. 如果一切正常，请单击右上方的&#x200B;**保存按钮**
11. 然后，再次单击右上方的&#x200B;**保存**&#x200B;按钮，然后单击左上方的&#x200B;**\&lt; — 左箭头**

![保存按钮和左上角的向后箭头](assets/build-journey-save-and-back-arrow.png)

12. 最后，单击左上角的&#x200B;**\&lt;返回图标**&#x200B;以返回历程画布

左上角的![返回图标以返回历程画布](assets/build-journey-back-icon-to-journey-canvas.png)

>[!TIP]
>
>然后再次单击“**上一步**”按钮……开玩笑！ 这是此节😜中的最后一个返回按钮



### 覆盖电子邮件参数

返回主历程画布上的“电子邮件”节点，确保您可以看到只读字段（您可能需要单击&#x200B;**显示只读字段**&#x200B;图标）

![历程画布的Email节点上显示的只读字段](assets/build-journey-show-read-only-fields-email-node.png)

1. 向下滚动至&#x200B;**电子邮件参数**&#x200B;并单击&#x200B;**启用参数覆盖**&#x200B;图标

电子邮件参数下的![启用参数覆盖图标](assets/build-journey-enable-parameter-override.png)

2. 单击空文本框，然后在左边栏中向下展开至&#x200B;**Context** -> **orderShipped** -> **\_dep**，然后单击&#x200B;**personalEmail**&#x200B;字段。  然后单击&#x200B;**确定按钮**

![选择orderShipped上下文下的personalEmail字段_dep](assets/build-journey-select-personalemail-context-field.png)

>[!WARNING]
>
>这样做很危险，除非您需要在生产环境中使用。  这将覆盖历程在配置文件上查找以执行消息的默认位置。



3. 单击右上方的&#x200B;**保存按钮**，然后单击左上方的&#x200B;**上箭头** \&lt; — 以&#x200B;**关闭**&#x200B;历程

![保存按钮和后退箭头以关闭历程](assets/build-journey-save-and-close-journey.png)

## 回顾

能够响应Order Shipped事件触发器、从外部服务获取ETA并发送电子邮件的已发布历程。
