---
title: 数据收集和准备
description: 此蓝图显示了在Adobe Experience Platform中摄取和准备数据的所有方法。
solution: Experience Platform, Data Collection
kt: 7204
thumbnail: null
exl-id: 5c3c94b6-c928-4d93-8b38-f8bd2aad2e68
translation-type: tm+mt
source-git-commit: ee1d97af9bf58076fbce24fbc8a3f0d50a4b52a0
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# 数据收集和准备

数据收集和准备包括准备数据并将其引入Adobe Experience Platform的所有方法。 此外，还能够通过侧向转发向企业目标收集数据到Adobe Experience Platform的边缘网络，以及随后将数据转发到企业目标。

数据准备包括将源数据映射到体验数据模型(XDM)模式。 它还包括对数据执行转换，包括日期格式、字段拆分/串联/转换，以及对记录进行连接/合并/重新键入。 数据准备有助于统一客户数据以提供汇总/筛选分析，包括报告或准备数据以用于客户用户档案汇编/数据科学/激活。

| Blueprint | 说明 | Experience Cloud应用程序 |
|---|---|---|
| **[数据准备和引入到Experience Platform](ingestion.md)** | <ul><li>数据准备和摄取蓝图包含准备数据并将其引入Adobe Experience Platform的所有方法。</ul></li> | <ul><li> Adobe Experience Platform </ul></li> |
| **[服务器端转发 — 企业集合](server-side-collection.md)** | <ul><li>激活到基于用户档案的已知目标，如电子邮件提供商、社交网络和广告目标。 </li><li>将线下属性和事件（如线下订单、交易、CRM或忠诚度数据）与在线行为结合使用，实现在线定位和个性化。</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL 实时客户数据平台]</li><li>Adobe Audience Manager（可选）</li></ul> |
