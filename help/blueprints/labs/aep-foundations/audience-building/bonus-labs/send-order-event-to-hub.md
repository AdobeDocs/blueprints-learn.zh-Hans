---
title: 将订单事件发送到中心
description: 了解如何通过API将订单事件流式传输到中心、构建流式订单区段、将其激活到目标以及验证配置文件结果。
doc-type: article
solution: Experience Platform
exl-id: d5de39d7-7340-487a-86fa-504344daeab7
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---


# 将订单事件发送到中心

## 流式传输到中心与Edge

在用例#1，我们将事件发送到Edge。  在某些用例中，我们可能有一个后端系统想要在事件中流式传输，但不需要将其发送到Edge。  本实验将展示如何通过将Order事件流式传输到中心来实现这一点。

## 创建订单区段（如果尚未创建）

单击左边栏中的受众，然后单击右上角的创建受众按钮。

![单击左边栏中的受众，然后单击“创建受众”](assets/send-order-event-to-hub-click-create-audience-button.png)

找到“已下订单”事件类型卡片，并将其拖动到画布上。

![将“下订单”事件类型卡片拖到画布上](assets/send-order-event-to-hub-drag-order-placed-event-onto-canvas.png)

## 更新事件规则

对事件规则进行以下更改（您可能需要展开事件才能看到它）

1. 最近
1. 15
1. 分钟
1. 更改流式评估

另存为&#x200B;**订购事件流（在15分钟内）**



![将受众另存为具有流式评估的“订单事件流式传输”（在15分钟内）](assets/send-order-event-to-hub-save-streaming-evaluation-rule.png)

## 激活到目标

如果刚刚创建的受众已关闭，则将其打开。

单击“激活到目标”



![单击订单受众的“激活到目标”](assets/send-order-event-to-hub-click-activate-to-destination.png)

### 目标

选择您之前创建的流目标（流DEP Webhook）



![选择流DEP Webhook目标](assets/send-order-event-to-hub-select-streaming-destination.png)

### 映射

保持映射不变，然后单击下一步

![保持映射不变，然后单击“下一步”](assets/send-order-event-to-hub-leave-mapping-click-next.png)

单击“完成”

## 打开Postman

在计算机上启动postman，并导航到以下API调用：

1. **Postman左侧边栏** —> `Collections`
1. **收藏集** —> `AEP Foundations Bootcamps (labs)`
1. **文件夹** —>配置文件实验室
1. **API请求** —> `Create Order Event`

![在Postman中打开Create Order Event API请求](assets/send-order-event-to-hub-create-order-event-api-request.png)


## 修改API请求

要创建示例API请求，您需要在API请求正文中填写以下部分。

首先，收集以下值：

## 查找帐户流端点

1. 导航到左边栏中的&#x200B;**源**，然后单击顶部导航中的&#x200B;**帐户**
1. 搜索&#x200B;**dep： HTTP API \[raw]**，突出显示该行并复制&#x200B;**流端点**&#x200B;的值并将其保存到以后可以引用的位置

帐户并复制其流端点&rbrack;(assets/send-order-event-to-hub-http-api-raw-streaming-endpoint.png &quot;dep： HTTP API \[raw]&quot;)

## 查找数据流ID

1. 查找&#x200B;**dep： Orders (stream)**&#x200B;的记录，然后单击数据流链接
1. 在右边栏中，复制&#x200B;**数据流ID**&#x200B;值并将其保存到以后可引用的位置

>[!NOTE]
>
>单击行上的空格。  不要单击蓝色链接！

![复制dep：订单（流）数据流的数据流ID](assets/send-order-event-to-hub-orders-stream-dataflow-id.png "Web数据流和数据集ID")

## 创建最终API请求

将您在上一步中保存的值复制到下面高亮显示的位置。

- **红色** —> `Streaming Endpoint URL`
- **绿色** —> `Dataflow ID`

完成后，您的最终API请求应该如下所示

&#x200B;> [!CAUTION]
>
>尚未执行！

![已完成创建订单事件API请求，流终结点和数据流ID已填充](assets/send-order-event-to-hub-final-order-api-request.png)


## 执行API

1. 单击&#x200B;**保存**&#x200B;按钮以保存API调用
1. 单击&#x200B;**发送**&#x200B;按钮执行您的请求

成功的调用应导致以下响应……

发送订单事件后![成功的API响应](assets/send-order-event-to-hub-successful-api-response.png)

## 验证

1. 转到您的个人资料并查看您的个人资料，以查看事件已摄取到个人资料中。  它应以秒为单位显示。
   1. 使用订单中的电子邮件查找配置文件
1. 验证配置文件是否符合区段的条件（可能需要几分钟）。 它应以秒到分钟显示。
   1. 订单事件流（15分钟内）
1. 检查webhook，查看目标是否已通知webhook“已实现”区段。  它应在5-10分钟后显示。
1. 15-30分钟后，您甚至可以使用以下各项检查数据集：
   1. 将下面的表名称更改为沙盒中的表名称。  要查找该数据集，请转到您的数据集列表并在“`dest`”上筛选，打开该数据集并在右边栏上复制表名称。

```sql
SELECT * FROM profile_export_for_destination_merge_policy_xxx
WHERE extSourceSystemAudit.LASTREFERENCEDDATE >= CURRENT_DATE
AND identitymap['email'][0].ID in ('depche.mode@dep.com')
ORDER BY extSourceSystemAudit.LASTREFERENCEDDATE DESC
LIMIT 10
```
