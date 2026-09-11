---
title: 验证历程
description: 通过登入和退出计数、电子邮件投放报告和步骤事件的查询服务数据验证历程执行。
doc-type: article
solution: Experience Platform
exl-id: 2e6e73e5-6bd8-4dde-ba06-29b67f927131
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---


# 验证历程

## 学习目标

验证历程是否已触发并按预期执行。  验证报表是否显示按预期更新的量度。

## 检查您的历程

1. 转至订单已发运历程，如果关闭则将其打开
2. 您至少看到输入了2个配置文件

为历程显示的![个人资料输入计数](assets/validate-journey-profile-entered-count.png)

&#x200B;3. 单击右上方的&#x200B;**查看报告** -> **最近24小时**。
&#x200B;4. 默认情况下，您位于&#x200B;**历程**&#x200B;选项卡中（左边栏上）
   - 您会看到一些进入和退出（数量将取决于您发送的事件数、任何测试、任何错误等）

![历程选项卡报告显示进入和退出](assets/validate-journey-journey-tab-enters-exits.png)

如果一切都已清理完毕，您可以（向下滚动以检查）：

**历程的统计信息**

3已输入配置文件（Henry、You和我们执行的测试）

如果您需要，可以单击顶部的切换开关以&#x200B;**排除测试事件**，并且您会看到这些数字发生变化

3个已退出配置文件（Henry、You和我们执行的测试）

**执行的操作和错误**

6个操作（3封电子邮件，3个GetShippingDetails）

**操作错误原因**

0错误（希望）

**个事件**

3个事件(orderShipped)

3个外部事件

&#x200B;5. 单击&#x200B;**电子邮件**&#x200B;选项卡（左边栏上）
   - **电子邮件 — 发送性能**
     - 您看到了&#x200B;**Delivered**&#x200B;和&#x200B;**Sent**&#x200B;的一些值（计数将取决于您发送的事件数、任何错误等）
     - 希望您没有错误（除非您之前遇到一些问题）
   - **电子邮件 — 统计数据**
     - 电子邮件 — 3个已定向、已发送、已投放

![电子邮件选项卡，显示发送性能和统计数据](assets/validate-journey-email-tab-sending-performance.png)

&#x200B;6. 请前往检查您的&#x200B;**电子邮件收件箱**，查看您是否收到电子邮件（如下所示）
   - *，*&#x200B;您的订单已发货ETA：*10/17/2026*&#x200B;跟踪号：*051009364*

&#x200B;> [!NOTE]
>
>检查AJO促销活动的Spam文件夹[ajo-campaigns@email.dep-labs.com](mailto:ajo-campaigns@email.dep-labs.com)

>[!NOTE]
>
>**为什么缺少名字？**
>
>我们更改了“电子邮件”节点，以查看“事件上下文”中的电子邮件地址。  但个性化中的名字是从\{\{profile.person.name.firstName\}\}中提取的。
>
>当您查找您的电子邮件个人资料时，您是否有名字？



&#x200B;7. *在30-60分钟之后*，您甚至可以通过以下方式在数据湖中检查您的数据集： **查询** -> **创建查询** -> **复制/粘贴SQL** -> **运行**

>[!NOTE]
>
>已流式处理订单发送事件，因此尽管它快速更新了配置文件，但需要一段时间才能更新数据湖。

```sql
SELECT * FROM dep_orders
WHERE timestamp >= CURRENT_DATE
LIMIT 10
```

![查询dep_orders数据集的服务结果](assets/validate-journey-query-service-dataset-results.png)

## 奖励（检查步骤事件）

>[!NOTE]
>
>步骤事件记录用户档案启动历程以及历程中的每个步骤。 注意：将这些事件记录到数据集中可能需要几分钟。



1. 在查询服务中，您可以通过运行此SQL来查看事件数据集正在捕获的步骤事件。 复制以下SQL并将其粘贴到查询中。

```sql
select timestamp,
  identityMap,
  _experience.journeyOrchestration.stepevents.journeyVersionName,
  _experience.journeyOrchestration.stepevents.NodeName,
  _experience.journeyOrchestration.stepevents.*
  from journey_step_events
limit 50
```

结果有超过100个列，可让您了解步骤事件记录的内容。

>[!NOTE]
>
>想知道每个字段的含义，请查看AJO架构词典，并将下拉列表更改为历程步骤事件架构：[https://experienceleague.adobe.com/tools/ajo-schemas/schema-dictionary.html?lang=en](https://experienceleague.adobe.com/tools/ajo-schemas/schema-dictionary.html?lang=en)



## 回顾

历程实例显示在历程报告或日志中，并执行配置的操作
