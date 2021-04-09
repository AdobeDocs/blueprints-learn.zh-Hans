---
title: 批处理消息和Adobe Experience Platform Blueprint
description: 使用Adobe Experience Platform作为客户用户档案和细分的中心，执行计划消息和批量消息活动。
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
translation-type: tm+mt
source-git-commit: 37416aafc997838888edec2658d2621d20839f94
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# 批处理消息和Adobe Experience Platform Blueprint

使用Adobe Experience Platform作为客户用户档案和细分的中心，执行计划消息和批量消息活动。

## 用例

* 计划的电子邮件活动
* 入门培训和再营销活动

## 应用程序

* Adobe Experience Platform
* Adobe Campaign Classic或Standard

## 集成模式

* Adobe Experience Platform → Adobe Campaign Classic
* Adobe Experience Platform → Adobe Campaign Standard

## 架构

<img src="assets/aepbatch.svg" alt="批处理消息和Adobe Experience Platform Blueprint的参考架构" style="border:1px solid #4a4a4a" />

## 瓜德雷尔

* 仅支持Adobe Campaign单个组织单位部署
* Adobe Campaign是所有活动用户档案的真相来源，这意味着用户档案必须存在于Adobe Campaign中，而新用户档案不应基于Experience Platform段创建。
* 通过Experience Platform实现的区段成员身份对于批（每天1次）和流（约5分钟）都是潜在的

**[!UICONTROL 实时客户数据平] 台细分共享到Adobe Campaign:**

* 建议20段限额
* 激活限于每24小时
* 仅合并模式属性可用于激活(不支持阵列/映射/体验事件)。
* 每个细分不超过20个属性的建议
* 所有具有“已实现”区段成员资格的用户档案的每个区段有一个文件，或者如果将区段成员资格作为“已实现”和“已退出”用户档案的属性添加
* 支持增量或完整的细分导出
* 不支持文件加密
* Adobe Campaign导出工作流最多每4小时运行一次
* 请参阅[Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)的用户档案和数据摄取护栏

## 实施步骤

### Adobe Experience Platform

#### 模式/数据集

1. 根据客户提供的用户档案，在Experience Platform中配置单个事件、体验和多实体模式。
1. 为broadLog、trackingLog、不可交付地址和用户档案首选项创建Adobe Campaign模式（可选）。
1. 将数据使用标签添加到数据集以进行管理。
1. 创建对目标实施管理的策略。

#### 用户档案/身份

1. 创建任何客户特定的命名空间。
1. 向模式添加身份。
1. 支持模式和用户档案集。
1. 为[!UICONTROL 实时客户用户档案]的不同视图设置合并规则（可选）。
1. 为Adobe Campaign使用创建区段。

#### 源/目标

1. 使用流API和源连接器将数据引入Experience Platform。
1. 配置[!DNL Azure] blob存储目标以与Adobe Campaign一起使用。

#### 移动应用程序部署

1. 为Adobe Campaign Classic实施Adobe Campaign SDK或为Adobe Campaign Standard实施Experience Platform SDK。 如果存在Experience Platform Launch，建议将Adobe Campaign Classic或Adobe Campaign Standard扩展与Experience Platform SDK一起使用。

#### Adobe Campaign

1. 为用户档案、查找数据和相关投放个性化数据配置模式。

>[!IMPORTANT]
>
>此时了解用户档案和事件数据在Experience Platform中包含哪些数据模型至关重要，这样您就能了解Adobe Campaign中需要哪些数据。

#### 导入工作流

1. 将简化的用户档案数据加载并导入Adobe Campaign sFTP。
1. 将业务安排和消息个性化数据加载和收录到Adobe Campaign sFTP上。
1. 通过Experience Platform从[!DNL Azure] blob中摄取工作流段。

#### 导出工作流

1. 每四小时通过工作流将Adobe Campaign日志发送回Experience Platform（broadLog、trackingLog、不可交付的地址）。
1. 每四小时通过咨询构建的工作流将用户档案首选项发送回Experience Platform（可选）。


## 相关文档

* [Adobe Experience Platform文档](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Campaign Classic文档](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Campaign Standard文档](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Experience Platform Launch文档](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Experience Platform Mobile SDK文档](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
