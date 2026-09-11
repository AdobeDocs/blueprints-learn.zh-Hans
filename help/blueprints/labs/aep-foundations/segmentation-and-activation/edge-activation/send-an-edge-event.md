---
hold: true
title: 发送Edge事件
description: 通过Postman将未经身份验证的Web事件发送到Edge，并验证它是否通过事件转发、配置文件摄取和边缘受众资格进行传输。
doc-type: article
solution: Experience Platform
exl-id: 8d6e9552-1fa0-4f12-928c-03f836c1652e
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---


# 发送Edge事件

现在一切都已配置，请将事件发送到Edge以查看它是否正常工作。

为此，请使用Postman将Web事件发送到您创建的数据流。

这会发送一个没有OAuth令牌&#x200B;**的事件**&#x200B;来模拟从Web进入Edge的页面查看。  请确保在计算机上打开了Postman以执行本实验操作。

>[!NOTE]
>
>由于您未传入经过身份验证的令牌，因此不会返回任何属性。

## 实验室期望

1. 用于点击Edge的体验事件
1. 数据流配置以使用事件转发服务
1. 事件转发以将事件发送到webhook
1. 数据流配置以使用AEP服务
   1. 要运行的Edge Audience
   1. 将事件发送到中心
1. Postman响应以包含Edge Audience（但没有属性）
1. 用于接收事件并添加事件配置文件片段的配置文件存储
1. 用于添加关系的身份存储
1. 用于接收数据并存储在Data Lake中的数据集



## 导航到呼叫

1. **Postman左侧边栏** ->收藏集
1. **收藏集** -> AEP Foundation Bootcamp （实验室）
1. **文件夹** ->配置文件实验室
1. **API请求** ->创建Web事件Edge（无身份验证）

![Postman侧边栏导航到“配置文件实验室”文件夹中的“创建Web事件”Edge（无身份验证） API请求](assets/send-an-edge-event-navigate-to-the-postman-call.png)

## 修改API请求

在执行API请求之前，您需要向请求添加一些其他信息。 首先，收集以下值：

## 收集数据流ID

1. 在左边栏中，单击&#x200B;**数据流**（在数据收集标题下）
1. 选择您的数据流并复制&#x200B;**数据流ID**&#x200B;值

![用于复制的数据流ID值高亮显示的数据流列表](assets/send-an-edge-event-gather-datastream-id.png)

## 更新Postman查询参数

1. 在请求中单击&#x200B;**参数**
1. 使用上一步的数据流ID更新&#x200B;**值**
1. 单击&#x200B;**保存**&#x200B;按钮保存您的更新

将数据流ID值粘贴到“值”字段中的![Postman Params选项卡](assets/send-an-edge-event-update-datastream-id-param.png "更新dataStreamId")



将电子邮件更改为电子邮件

![Postman请求正文，其中显示的电子邮件值已更新为测试人员自己的电子邮件地址](assets/send-an-edge-event-change-email-param.png "将电子邮件更改为电子邮件")

## 执行API

单击&#x200B;**发送**&#x200B;按钮执行您的请求。

单击![Postman发送按钮以执行创建Web事件Edge请求](assets/send-an-edge-event-execute-request.png)

您应会看到响应中返回的是一个核心内容：

- 200 OK响应表示Edge Network已成功发送并接受数据

>[!NOTE]
>
>任何流区段和批处理区段只有在首先在中心评估之后才会显示

## 验证事件转发

在webhook.site上，您应该会立即看到通过Postman请求发送的相同有效负载正文。

![Webhook.site显示从事件转发接收的转发事件有效负载](assets/send-an-edge-event-webhook-payload.png)

>[!NOTE]
>
>请注意，有效负载已添加您在设置边缘设置中使用的数据流时请求的地理查找信息

## 查找配置文件

在Adobe Experience Platform中，查找您刚刚从刚刚发送到Edge Network的事件中发送的配置文件。 导航到“配置文件” — >“浏览”，使用下列信息执行查找：

- 合并策略 — >默认基于时间
- 身份命名空间 — >电子邮件
- 身份值 — > edge-email\@dep.com
  - 注意：请更改此项以匹配您在上面的&#x200B;*更新Postman查询参数*&#x200B;步骤中使用的电子邮件

1. 单击&#x200B;**查看**&#x200B;查找配置文件
1. 单击&#x200B;**配置文件ID**&#x200B;以打开配置文件

![使用查看链接浏览搜索结果以打开匹配的配置文件](assets/send-an-edge-event-lookup-profile.png "查找配置文件")

1. 单击顶部导航中的&#x200B;**事件**，您就可以看到刚刚发送的事件

![显示刚发送到Edge的Experience事件的“配置文件事件”选项卡](assets/send-an-edge-event-view-profile-event.png "查看配置文件事件")

1. 通过查看顶部导航中的Audience Membership选项卡，验证配置文件是否符合受众条件。 您应会看到以下内容：

- 任何活动Edge（15分钟内）
- dep：任何事件流（一小时内）

![“受众成员资格”选项卡，显示任何事件Edge和依赖：任何事件流受众的资格](assets/send-an-edge-event-any-event-streaming-within-the-last-hour.png)

## 如何解释检查

1. 在Postman中检查200响应（有效负载格式正确）
1. 检查webhook是否具有事件（正确配置的事件转发）
1. 检查配置文件中是否包含事件（正确配置的AEP服务、中心上接收和处理的事件）
1. 检查配置文件在几分钟后是否具有两个身份（标识图已在中心上链接）
1. 检查配置文件是否符合受众的条件（正确定义的受众）
1. 检查Data Lake是否有事件。
