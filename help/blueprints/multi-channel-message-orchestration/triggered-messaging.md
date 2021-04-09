---
title: 触发式消息和Adobe Experience Platform Blueprint
description: 使用Adobe Experience Platform作为集中中心流数据、客户用户档案和细分执行触发式消息和体验。
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
translation-type: tm+mt
source-git-commit: 2404d871a852df8fed3adb97a79cc15e994db762
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 1%

---

# 触发式消息和Adobe Experience Platform Blueprint

使用Adobe Experience Platform作为集中中心流数据、客户用户档案和细分执行触发式消息和体验。

## 用例

* 触发消息
* 注册确认
* 放弃购物车和应用程序表单
* 位置触发的消息

## 架构

<img src="assets/triggered.svg" alt="触发消息和Adobe Experience Platform方案的参考架构" style="border:1px solid #4a4a4a" />

## 集成模式

* Adobe Experience Platform -> Journey Orchestration

## 先决条件

* Adobe Experience Platform
* Journey Orchestration

## 瓜德雷尔

### Journey Orchestration

* 有关限制](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en#starting-with-journeys)的更多详细信息，请参阅链接[
* 可通过API设置进行限制，以确保目标系统未达到故障点饱和。 限制表示超过上限的消息将完全丢弃且从不发送。 仍不支持限制。
   * 最大连接数：目标可处理的http/s连接的最大数
   * 最大呼叫数：periodInMs参数中要发出的最大调用数
   * periodInMs:时间（以毫秒为单位）
* 区段会员发起的旅程可以以两种模式运行：
   * 批区段（每24小时刷新一次）
   * 流细分（&lt;5分钟资格鉴定）
* 批区段：确保您了解合格用户的日常数量，并确保目标系统能够处理每个旅程以及所有旅程中的突发吞吐量
* 流细分：确保可以处理初始的用户档案资格批次，以及每个旅程和所有旅程的每日流资格鉴定批次
* 最终目标必须支持REST API和JSON有效负荷
* 当前不支持Offer decisioning
* 请参阅[Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)的用户档案和数据摄取护栏

### Campaign Standard

* 吞吐量仅支持14 tp（每小时50k）
* 不支持由区段成员发起的旅程
* 支持对事务性消息打开/点击的反应事件在Journey Orchestration中。
* 事务性消息日志当前未本机同步到Experience Platform，需要手动配置。 建议最多每四小时导出一次日志。


## 实施步骤

### Adobe Experience Platform

#### 模式/数据集

1. 根据客户提供的数据在Experience Platform中配置单个用户档案、体验事件和多实体模式。
1. 创建以下活动模式:broadLog、trackingLog、不可交付的地址和用户档案首选项（可选）。
1. 将数据使用标签添加到数据集以进行管理。
1. 创建策略以对目标实施管理。

#### 用户档案/身份

1. 创建任何客户特定的命名空间。
1. 向模式添加身份。
1. 支持模式和用户档案集。
1. 为[!UICONTROL 实时客户用户档案]的不同视图设置合并规则（可选）。
1. 为活动使用创建区段。

#### 源/目标

1. 使用流API和源连接器将数据引入Experience Platform。
1. 配置[!DNL Azure] blob存储目标以与活动一起使用。

#### 移动应用程序部署

1. 实施活动 SDK for Campaign Classic或Experience Platform SDK for Campaign Standard。 如果存在Experience Platform Launch，建议将Campaign Classic/Standard扩展与Experience Platform SDK一起使用。


### Journey Orchestration

1. 用于启动客户旅程的流数据必须首先在Journey Orchestration中配置，才能获得业务流程ID。 然后，此业务流程ID将提供给开发人员以与摄取一起使用。
1. 配置外部数据源。
1. 配置自定义操作。

### Campaign Standard

1. 使用适当的个性化设置配置消息传递模板。
1. 配置导出工作流，导出事务消息日志。 建议最多每四小时运行一次。


## 相关文档

* [Adobe Experience Platform文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Journey Orchestration文档](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=en)
* [Campaign Classic文档](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Campaign Standard文档](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Experience Platform Launch文档](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Experience Platform Mobile SDK文档](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
