---
title: 选项#2 — 使用预先聚合
description: 通过使用上游计算的预聚合使用量属性而不是聚合受众规则中的事件，构建完全流式受众。
doc-type: article
solution: Experience Platform
exl-id: fe6ee041-814f-41c1-91cf-c3473cbca0c2
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# 选项#2 — 使用预先聚合

我们的受众中聚合面临的挑战是，我们的受众（在流式传输时）基于在作为批量受众的受众中完成的聚合。 由于营销部门已确定需要一种更实时的方法，因此我们做了三件事来将此纳入设计：

- 在流式传输数据之前计算聚合

>[!NOTE]
>
>这种情况非常少见，因为大多数流式处理的数据是针对单个事件而不是聚合而设计的

- 使用非规范化计划名称
- 数据流入

## 创建受众

创建其计费数据使用率较高但当前没有最终电话计划的所有用户档案的受众。

1. 创建新受众
1. 在“Attributes not Event”（属性而非事件）选项卡上搜索“Agg”（聚合），并将两个“Aggregate”（聚合）拖到画布上。 为每个设置适当的运算符和值。

   ![为每个聚合设置适当的运算符和值](assets/option-2-use-pre-aggregates-set-operators-and-values.png)



3. 在配置文件中搜索计划名称并将其添加(XDM Individual Profile > Devbc > Plan Details > Plan Name)。 选择不等于“Ultimate”

   ![选择计划名称不等于Ultimate](assets/option-2-use-pre-aggregates-select-does-not-equal-ultimate.png)



4. 提供描述。  验证评估方法是流式的。

5. 将受众另存为“*计费数据使用率高但无Ultimate计划(Agg)*”

>[!NOTE]
>
>请记住，我们将聚合逻辑转移到上游流ETL层中。
>
>这种选择是在具有批处理受众（营销人员控制其中的逻辑与流式受众）和将定义和控制推送到ETL层（其中工程部门必须参与）之间进行权衡。

>[!TIP]
>
>**可选挑战实验室**
>
>提早完成？
>
>我们希望在贵宾购买产品时能实时向他们发送一条特别信息。  创建“VIP”受众。  VIP是指上个月购买超过$1,000的用户。
