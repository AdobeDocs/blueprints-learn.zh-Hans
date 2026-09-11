---
title: 设置自定义Personalization目标
description: 配置自定义Personalization目标，以将配置文件属性发送到Edge Network，以供第三方个性化系统实时使用。
doc-type: article
solution: Experience Platform
exl-id: 46073f7c-00f4-4a4f-9fa3-8827ef15ec4a
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---


# 设置自定义Personalization目标

使用[自定义Personalization目标](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization)是一种方法，使受众可在Edge上供第三方使用（通常使用Network Server API）以用于个性化。

本实验配置自定义Personalization目标，以便我们可以向Edge发送配置文件属性。



## 浏览目标目录

>[!NOTE]
>
>要使用Adobe Target进行个性化，我们将使用[Adobe Target目标。](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-target-v2) 该行为与自定义Personalization相同。

1. 在左边栏中，单击&#x200B;**目标**
1. 在顶部边栏中，单击&#x200B;**目录**
1. 接下来，选择&#x200B;**Personalization**&#x200B;的类别
1. 在屏幕中间，您应该会看到标题为&#x200B;**具有属性的自定义Personalization的目标。** 单击该卡片上的&#x200B;**设置**&#x200B;按钮。

![浏览自定义Personalization目标的目标目录](assets/setup-custom-personalization-destination-browse-destination-catalog.png "浏览自定义Personalization目标的目标目录")



## 配置目标

### 设置帐户

命名您的帐户`DEP Labs Custom PZN`，然后单击&#x200B;**连接到目标按钮**

![创建PZN帐户并连接到目标屏幕](assets/setup-custom-personalization-destination-create-pzn-account.png)



### 添加目标详细信息

填写以下目标详细信息：

1. 名称 — > **Edge目标**
1. 集成别名 — > **edgeAlias**
1. 数据流ID -> *选择您之前创建的数据流名称*
1. 完成后，单击&#x200B;**下一步**&#x200B;按钮

![填写目标详细信息](assets/setup-custom-personalization-destination-fill-destination-details.png "填写目标详细信息")

>[!CAUTION]
>
>单击“下一步”后，将无法更改&#x200B;**名称**&#x200B;或&#x200B;**集成别名**。  这些内容将在稍后的Edge Network响应中显示



### 选择治理策略

选择&#x200B;**现场Personalization**，然后单击&#x200B;**创建**&#x200B;按钮

![选择治理策略](assets/setup-custom-personalization-destination-select-governance-policy.png "选择治理策略")

>[!NOTE]
>
>虽然此步骤是可选的，但强烈建议您为您创建的任何目标分配治理策略，以避免错误地激活用户档案



完成后，您应该会看到此屏幕，其中显示了您的成功！

![已成功创建PZN目标](assets/setup-custom-personalization-destination-successful-creation-screen.png "已成功创建PZN目标")



## 激活目标

### 选择受众

通过单击行以突出显示您刚创建的目标，然后单击&#x200B;**下一步**&#x200B;按钮

![选择PZN目标](assets/setup-custom-personalization-destination-select-destination-row.png "选择PZN目标")



选择&#x200B;**所有受众**&#x200B;并单击&#x200B;**下一步**

![选择PZN受众](assets/setup-custom-personalization-destination-select-all-audiences.png "选择PZN受众")



### 映射

按如下方式添加&#x200B;**新映射**：

| Source字段 | 目标字段 |
| ---------------------- | ------------ |
| \_tenantName.plan.name | 计划名称 |

>[!NOTE]
>
>请记住将&#x200B;**\_tenantName**&#x200B;替换为您的租户名称

>[!NOTE]
>
>目标字段允许提供一个可能与XDM名称不同的友好名称



完成后，屏幕应如下图所示。  然后，您可以单击“下一步&#x200B;**”按钮**

![创建PZN映射](assets/setup-custom-personalization-destination-create-mapping.png "创建PZN映射")

>[!NOTE]
>
>由于配置文件属性可能包含敏感数据，因此所有[Edge Network服务器API](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)调用都必须在经过身份验证的上下文中进行，以便在Edge上检索该属性。


### 审核

在最后一个屏幕上，您可以查看配置的详细信息，然后单击“完成”按钮。

![审阅并发布PZN目标](assets/setup-custom-personalization-destination-review-and-publish.png "审阅并发布PZN目标")

>[!NOTE]
>
>这是[自动实施](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/auto-enforcement)将针对您的[数据使用策略](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/policies/overview)检查的位置。 它会使用您创建的规则检查您的营销操作，并引发任何错误。
