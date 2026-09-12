---
title: 批量摄取
description: 修复映射和数据质量错误时，通过批量摄取将数据湖和配置文件加载客户帐户数据。
doc-type: overview-page
solution: Experience Platform
exl-id: 76830e79-8fc0-4fda-98b1-2c1de19e8158
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# 批量摄取

## 学习目标

在本练习中，您将从基于文件的源连接器将客户帐户数据加载到AEP数据湖，然后加载到用户档案。 您将学习以下内容：

1. 了解直通映射
1. 修复ML生成的直通映射
1. 使用源数据预览检查任何数据质量问题
1. 计划数据流运行
1. 处理因必填字段中缺少值导致的错误
1. 处理由数据类型不匹配错误引起的错误
1. 处理数据引入错误并从此类故障中恢复
1. 反复使用测试数据来生成综合的映射集。

>[!NOTE]
>
>如果您未在之前的Labs中完成客户帐户架构创建，则可以浏览到架构目录并改用&#x200B;**dep：客户帐户**
