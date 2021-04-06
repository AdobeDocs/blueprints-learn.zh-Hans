---
title: 客户活动中心蓝图
description: 实时客户用户档案查找，为代理协助支持和销售提供上下文。
solution: Experience Platform,Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c,4f15aa5d-9ee3-4d92-8012-3e2f0c0d615f
translation-type: tm+mt
source-git-commit: 98d44067a1640dc8b695cb0d25f69ec26be647e1
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# 客户活动中心蓝图

Customer 活动 Hub Blueprint显示外部应用程序如何访问Adobe Experience Platform的实时客户用户档案。

外部应用程序可以通过API用户档案请求访问实时客户GET。 然后，存储在用户档案中的属性、事件、区段成员关系和模型驱动功能可以用于这些外部非Adobe应用程序。

利用此功能，您可以在客户呼叫呼叫中心时显示丰富的上下文。 例如，支持代理可以了解客户的终身价值、客户流失倾向或营销活动暴露情况。 销售代理还可以从更多情境中受益，或从中洞察客户。

>[!NOTE]
>
>用户档案查找API支持的当前延迟约为500毫秒，因此此方法不适合将用户档案与实时决策引擎（如同页Web或移动个性化）集成。

## 用例

* 为代理支持的交互（如支持和销售体验）提供更深入的消费者情境。 通过对用户档案的查找，工程师可以接收消费者的更多情境，例如最近购买、活动交互、倾向、受众会员资格，以及存储在实时客户用户档案中的其他属性和洞察。

## 架构

<img src="assets/cah.svg" alt="客户活动中心蓝图的参考体系结构" style="border:1px solid #4a4a4a" />

## 瓜德雷尔

* [实时客户用户档案数据的保证](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## 实施步骤

1. 配置数据集和模式。
1. 配置[!UICONTROL 实时客户用户档案]:为[!UICONTROL 实时客户用户档案]配置模式和数据集，并设置合并策略和标识。
1. 将数据引入平台并处理到[!UICONTROL 实时客户用户档案]。
1. 使用实体API从记录实体或体验用户档案实体中查找事件属性。

## 相关文档

* [Adobe Experience Platform 激活产品说明](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform0.html)
* [实时客户用户档案文档](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=en)
* [用户档案瓜德雷尔](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [用户档案查找API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
