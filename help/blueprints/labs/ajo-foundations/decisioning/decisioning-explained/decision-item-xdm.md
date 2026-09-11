---
hold: true
title: 决策项XDM
description: 了解每个决策项共享的预建XDM架构以及如何将自定义属性嵌套在租户命名空间下。
doc-type: article
solution: Experience Platform
exl-id: c42503a2-24e7-4a5d-98bf-38c16fe69733
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# 决策项XDM

## 学习目标

在本课程结束时，您将能够：

- 识别用于每个决策项的预建XDM架构
- 说明自定义属性在架构中的位置以及适用于这些属性的上限
- 识别父对象下的嵌套属性如何支持重用

## 所需材料

- 至少12个便笺（如果犯错则更多）

## 讲座

在视频播放过程中，您将暂停在12个便笺的顶部写下四个属性名称 — 您将在下一课程中填写实际值。

>[!VIDEO](https://video.tv.adobe.com/v/3502206/)

## 主要要点

- 每个决策项目使用相同的预建架构：个性化优惠项目 — experience decisioning
- \_experience节点下的所有内容都是系统必需的，无法编辑
- 自定义属性位于贵组织的租户命名空间下，并且每个架构的上限为100
- 每个决策项目只有一个架构 — 没有重复项或替代版本
