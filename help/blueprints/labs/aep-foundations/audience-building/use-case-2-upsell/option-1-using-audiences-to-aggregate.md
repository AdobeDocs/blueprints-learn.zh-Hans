---
title: 选项#1 — 使用受众进行聚合
description: 构建对计费使用事件和非标准化计划数据使用受众内总和平均聚合的受众，以启用流评估。
doc-type: article
solution: Experience Platform
exl-id: da019755-07a3-406c-8ac7-7878325a14bf
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---


# 选项#1 — 使用受众进行聚合

通过受众中的聚合，我们可以在受众规则中聚合事件。 但是，由于我们每次只能执行一个聚合，因此我们需要将这两个聚合从用例中拆分。

## Audience #1 — 过去6个月的计费数据使用情况> 140 GB

在此受众构建中，您确定过去6个月的总计费数据使用量> 140 GB。 为此，请执行以下步骤：

1. 创建新受众。  使用帐单事件卡。

   ![使用帐单事件卡创建新受众](assets/option-1-using-audiences-to-aggregate-new-audience-billing-statement-card.png)

   >[!NOTE]
   >
   >良好的事件类型结构使用户易于使用和理解。  请花些时间跨您的架构开发标准化方法。
   >
   >这有助于解决拼写错误的问题。
   >
   >您始终可以回退到事件类型字段并手动键入内容。



2. 单击右下角规则中的“椭圆”，然后选择“聚合”。 单击“Select an Attribute（选择属性）”并键入“Usage（用法）”。 选择“计费数据使用情况”字段。



   ![选择属性并选择“计费数据使用情况”字段](assets/option-1-using-audiences-to-aggregate-select-billing-data-usage-field.png)



   在属性列表![&#128279;](assets/option-1-using-audiences-to-aggregate-select-billing-data-usage-field--2.png)中选择了计费数据使用情况字段



3. 将“等于”更改为“大于” ，并将值更改为140。

4. 将事件卡上方的时间从“任何时间”更改为“最近”，将值更改为6，并将天更改为月

   ![将事件时间窗口更改为过去6个月](assets/option-1-using-audiences-to-aggregate-change-time-to-last-6-months.png)



5. 提供描述并保存。

6. 为受众指定名称“*计费使用总和> 140 GB（过去6个月）*”

>[!NOTE]
>
>只能将聚合受众另存为批次

>[!NOTE]
>
>可通过两种方式在受众中使用聚合。
>
>- Sum/Count/Min/Max/Average（如上所示）
>- 仅计数（每个事件计为1）
>
>![仅计算聚合模式将每个事件计为1](assets/option-1-using-audiences-to-aggregate-counts-only-aggregate-mode.png)
>
>如果需要，两者可以一起使用
>
>![只对一起使用的聚合模式进行求和和计数](assets/option-1-using-audiences-to-aggregate-both-can-be-used-together.png)

## Audience #2 — 连续6个月平均 每月数据使用量>= 20 GB

1. 请不要单击超链接，而是在受众列表UI中选择行，以便该行突出显示我们刚刚创建的行。 突出显示后，单击“复制”。

   ![选择受众行并单击复制](assets/option-1-using-audiences-to-aggregate-select-row-and-click-copy.png)



2. 单击副本并编辑它。  单击事件卡并将总和更改为平均值。 将大于更改为大于或等于，并将值更改为20。 将伪代码复制到描述中。

   ![将伪代码复制到受众描述中](assets/option-1-using-audiences-to-aggregate-copy-pseudo-code-into-description.png)



3. 为受众指定名称“*计费使用平均> 20 GB（过去6个月）*”

## Audience #3 — 没有最终电话计划

1. 创建新受众
1. 在属性中，搜索计划名称
1. 添加计划名称（计划名称）
1. 选择“Ultimate”。  更改为不等于

   >[!NOTE]
   >
   >还记得我们的前期工作吗？ 它在我们的查找维度上使用字段：
   >
   >XDM Individual Profile > Devbc >计划详细信息>计划ID属性> **计划名称（计划名称）**

   ![选择Ultimate并将运算符更改为“不等于”](assets/option-1-using-audiences-to-aggregate-select-ultimate-does-not-equal.png)



&#x200B;5. 单击“受众” — >“Experience Platform”。 将“计费使用总和”>“140 GB”和“计费使用平均”>= 20 GB拖动到“计划名称”旁边。

   ![将计费使用情况受众拖动到计划名称旁边](assets/option-1-using-audiences-to-aggregate-20-gb-next-to-plan-name.png)



&#x200B;6. 将伪代码复制到描述中

&#x200B;7. 选中“可以流”。 **它不能是流式传输**。 进行一些更改：

   >[!NOTE]
   >
   >只要使用查找数据集，就会创建一个多实体受众，并在批量中进行评估。  我们在受众中使用了一个字段：
   >
   >XDM Individual Profile > Devbc >计划详细信息>计划ID属性>计划名称（计划名称）



&#x200B;8. 将&#x200B;**计划名称（计划名称）**&#x200B;替换为： XDM个人资料> Devbc >计划详细信息> **计划名称**

   ![将计划名称（计划名称）替换为非规范的计划名称字段](assets/option-1-using-audiences-to-aggregate-replace-denormalized-plan-name.png)

   >[!NOTE]
   >
   >请记住， LID反标准化步骤会将计划名称添加到用户档案。 这样，您就可以在受众中引用它。 因此，这将删除对查找的联接，并使评估方法流式处理。
   >
   >这里的取舍是，我们将此逻辑上游移动到预先数据摄取，而不是在受众评估期间。
   >
   >如果计划名称发生更改，我们现在还必须更新任何配置文件。
   >
   >不过这样做的好处是，我们现在可以实时做出反应。



&#x200B;9. 验证您现在是否可以将其另存为流式传输。 将受众另存为“计费数据使用率较高，但没有Ultimate计划&#x200B;*”*

>[!NOTE]
>
>虽然此评估方法是流式的，但它基于两个批量受众进行受众资格鉴定。

>[!NOTE]
>
>虽然此方法有效，但我们现在具有使用批处理受众（每24小时运行一次）的流受众（实时）。 如果这适用于我们的用例和数据加载，那么这是一个很好的选择（例如，也许我们的计费数据是每天或每月加载的，这很有可能，但并非所有用例都会这样）。 如果不能，一种常见的方法是在发送到AEP之前聚合数据。 如果您需要一种更实时的方法，请另外考虑一种选择。
