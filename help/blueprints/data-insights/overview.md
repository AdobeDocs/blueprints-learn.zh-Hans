---
title: 数据分析、智能和AI/ML
description: 此蓝图显示了Adobe Experience Platform内对数据湖中存在的数据执行探索性查询和分析的能力。
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039
translation-type: tm+mt
source-git-commit: f5d8b3fea11df0ffaeb59f0b53e93d76426ef252
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# 数据分析、智能和AI/ML

企业数据探索和报告包括Adobe Experience Platform内对数据湖中存在的数据执行探索性查询和分析的能力。

Experience Platform的查询服务允许对数据执行SQL查询。 数据科学工作区支持对数据执行数据探索、数据科学和机器学习工作负载。

此外，Experience Platform允许与第三方SQL客户端、接口和Business Intelligence(BI)工具连接，以使用PostgreSQL协议直接连接、访问和查询Experience Platform中的数据。

某些护栏适用于查询超时和查询结果中包含的数据量，如方案详细信息中所述。

## Blueprint

| Blueprint | 说明 | Experience Cloud应用程序 |
|---|---|---|
| **[数据分析和智能](analysis.md)** | <ul><li>数据准备和摄取蓝图包含准备数据并将其引入Adobe Experience Platform的所有方法。</ul></li> | <ul><li> Adobe Experience Platform </ul></li> |
| **[用户档案扩充蓝图的自定义数据科学](data-science.md)** | <ul><li>激活到基于用户档案的已知目标，如电子邮件提供商、社交网络和广告目标。 </li><li>将线下属性和事件（如线下订单、交易、CRM或忠诚度数据）与在线行为结合使用，实现在线定位和个性化。</li></ul> | <ul><li>Adobe Experience Platform</li><li> 实时客户数据平台</li><li>Adobe Audience Manager（可选）</li></ul> |
