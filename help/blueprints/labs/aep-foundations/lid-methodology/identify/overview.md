---
hold: true
title: 识别
description: 了解LID方法的两部分标识步骤：标记其余的表类型和标识关键标识字段。
doc-type: overview-page
solution: Experience Platform
exl-id: 83657cf0-db35-4d4d-8cfb-1934ff40baca
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---


# 识别

## 学习目标

LID方法中的&#x200B;**识别**&#x200B;步骤分为两个不同的部分：

1. 第1部分 — 剩余表类型 — >标识剩余的未标记表并标记反正规化类型
1. 第2部分 — 关键字段 — >标识主要实体和支持实体的关键字段



它将教导您在关系模型中确定设计Real-time Customer Profile所需的以下项目：

- Bridge表（处理多对多关系的表）
- 需要反正规化的表
- Real-Time Customer Profile中的主要身份
- 主实体类中可用于唯一标识人员的基于人员的标识
- 个人资料/体验事件表和相关查找表之间的关系标识符
- 体验事件架构所需的必填字段
- 个人配置文件和查找架构的推荐字段
