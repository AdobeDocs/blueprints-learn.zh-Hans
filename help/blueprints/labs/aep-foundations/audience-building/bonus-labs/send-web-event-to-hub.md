---
hold: true
title: 将Web事件发送到中心
description: 了解如何使用Postman将Web事件直接发送到中心，并验证它是否符合配置文件和流式客户细分的条件。
doc-type: article
solution: Experience Platform
exl-id: a8343499-b4d5-4540-8fe1-7497bc20e437
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---


# 将Web事件发送到中心

## 打开Postman

在计算机上启动postman，并导航到以下API调用：

1. **Postman左侧边栏** —> `Collections`
1. **收藏集** —> `AEP Foundations Bootcamps (labs)`
1. **文件夹** —>配置文件实验室
1. **API请求** —> `Create Web Event`

![在Postman中打开“创建Web事件API”请求](assets/send-web-event-to-hub-create-web-event-api-request.png)


## 修改API请求

要创建示例API请求，您需要在API请求正文中填写以下部分。

首先，收集以下值：



## 查找帐户流端点

1. 导航到左边栏中的&#x200B;**源**，然后单击顶部导航中的&#x200B;**帐户**
1. 搜索&#x200B;**dep： HTTP API \[raw]**，突出显示该行并复制&#x200B;**流端点**&#x200B;的值并将其保存到以后可以引用的位置

帐户并复制其流端点](assets/send-order-event-to-hub-http-api-raw-streaming-endpoint.png &quot;dep： HTTP API \[raw]&quot;)

## 查找Web数据流ID

1. 单击&#x200B;**HTTP API \[raw]**&#x200B;帐户
1. 查找并选择名为&#x200B;**dep： Web （流）**&#x200B;的数据流行
1. 在右边栏中，复制&#x200B;**数据流ID**&#x200B;值并将其保存到以后可引用的位置

>[!NOTE]
>
>单击行上的空格。  不要单击蓝色链接！

![复制dep： Web （流）数据流的数据流ID](assets/send-web-event-to-hub-web-stream-dataflow-id.png "Web数据流ID")

## 创建最终API请求

将您在上一步中保存的值复制到下面高亮显示的位置。

- **红色** —> `Streaming Endpoint URL`
- **绿色** —> `Dataflow ID`

完成后，您的最终API请求应该如下所示

> [!CAUTION]
>
>尚未执行！

![已完成创建Web事件API请求，流终结点和数据流ID已填充](assets/send-web-event-to-hub-final-web-api-request.png)

## 执行API

1. 单击&#x200B;**保存**&#x200B;按钮以保存API调用
1. 单击&#x200B;**发送**&#x200B;按钮执行您的请求

成功的调用应导致以下响应……

发送Web事件后![成功的API响应](assets/send-web-event-to-hub-successful-api-response.png)

## 验证

1. 转到您的个人资料并查看您的个人资料，以查看事件已摄取到个人资料中。  它应以秒为单位显示。
   1. 在呼叫中使用电子邮件查找配置文件
1. 根据自事件中上次发送后经过的时间，您可能不符合新区段的条件。 否则，您可能会看到以下内容或其他：
   1. 任何活动Edge（15分钟内）
      1. 请记住：当流数据传入时，所有通过Edge评估保存的受众也会在中心进行评估
   2. dep：任何事件流（一小时内）
1. 如果没有新区段，您可能无法在webhook中看到任何内容。
1. 事件转发不会发送任何内容。
   1. 为什么？ 此事件转到中心而非Edge，因此，该事件不会显示为要发送的事件“转发”的任何内容，也不会显示在Assurance中。
1. 在至少30分钟后，您甚至可以使用以下各项检查数据集：
   1. 将下面的表名称更改为沙盒中的表名称。  要查找该数据集，请转到您的数据集列表并在“`dest`”上筛选，打开该数据集并在右边栏上复制表名称。

```sql
SELECT * FROM profile_export_for_destination_merge_policy_xxx
WHERE extSourceSystemAudit.LASTREFERENCEDDATE >= CURRENT_DATE
AND identitymap['email'][0].ID in ('depche.mode@dep.com')
ORDER BY extSourceSystemAudit.LASTREFERENCEDDATE DESC
LIMIT 10
```
