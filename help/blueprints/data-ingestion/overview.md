---
title: 数据收集和准备
description: 了解在Adobe Experience Platform中摄取和准备数据的方法。
solution: Data Collection
kt: 7204
thumbnail: null
exl-id: 5c3c94b6-c928-4d93-8b38-f8bd2aad2e68
source-git-commit: 60a7785ea0ec4ee83fd9a1e843f0b84fc4cb1150
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 80%

---

# 数据收集和准备Blueprint

数据收集和准备包含准备数据并将其摄入到 Adobe Experience Platform 的所有方法。以及收集数据以Adobe的能力 [!DNL Experience Platform Edge Network] 以及随后通过侧转发将数据转发到企业目标。

数据准备包括将源数据映射到体验数据模型 (XDM) 架构。它还包括对数据执行转换，包括日期格式、字段拆分/串联/转化，以及对记录进行连接/合并/重新设置键。数据准备有助于统一客户数据以提供汇总/筛选的分析，包括报告或准备数据以用于客户档案汇编/数据科学/激活。

| Blueprint | 描述 | Experience Cloud 应用程序 |
|---|---|---|
| **[数据准备和摄入](ingestion.md)** | <ul><li>数据准备和摄入 Blueprint 包含准备数据并将其摄入到 Adobe Experience Platform 的所有方法。</ul></li> | <ul><li> Adobe Experience Platform </ul></li> |
| **[服务器端企业数据收集](server-side-collection.md)** | <ul><li>激活到基于用户档案的已知目的地（如电子邮件提供商、社交网络和广告目的地）。 </li><li>将线下属性和事件（如线下订单、交易、CRM 或忠诚度数据）与线上行为结合使用，实现线上定位和个性化。</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL Real-time Customer Data Platform]</li><li>Adobe Audience Manager（可选）</li></ul> |
