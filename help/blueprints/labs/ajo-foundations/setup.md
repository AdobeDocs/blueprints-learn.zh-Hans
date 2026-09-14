---
title: 设置
description: 在启动Postman基础实验室之前，完成所需的沙盒部署和AJO配置步骤。
doc-type: article

solution: Experience Platform
exl-id: 7c1a9e3d-5b8f-4a2e-9c6d-3f7b0e4a8c2d
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 1%
---

# 设置

在启动AJO基础实验室之前，请完成以下设置步骤。 您需要采取哪些步骤取决于您如何参加训练营。

## 沙盒设置

>[!NOTE]
>
>如果您正在参加实时培训课程或活动，则已为您部署沙盒 — 请跳过此部分，直接转到下面的Postman设置。

如果您还没有部署了实验室资产的工作沙盒，请完成以下步骤：

- [Developer Console设置](sandbox-setup/developer-console-setup.md)
- [部署说明](sandbox-setup/deployment-instructions.md)

## Postman设置

本课程中的labs需要Postman，无论沙盒如何配置。 请先完成以下操作，然后再继续：

- [Postman安装](postman-setup/postman-installation.md)
- [导入环境文件](postman-setup/import-environment-file.md)
- [导入API收藏集](postman-setup/import-api-collection.md)

## 渠道先决条件

在本次训练营的后面两个实验室取决于外部帐户，只有自控进度的学习者才需要安排 — 如果您参加实时培训课程或活动，则这些已为您配置。

### 已委派的子域

[配置电子邮件渠道](data-stores/configure-email-channels/overview.md)实验室 — 以及依赖它的所有内容（[正在运行的消息投放](orchestrated-campaigns/message-delivery-in-action/overview.md)、[购买后兴奋](journeys/post-purchase-excitement/overview.md)和[AJO Brands](content-authoring-with-ai/overview.md)） — 需要委派给Adobe的子域来发送电子邮件。 如果您还没有域，请向任何域注册机构（例如，Namecheap）注册一个域。 然后，要将其子域（例如`email.yourdomain.com`）委派给Adobe，请按照Adobe的[子域委派说明](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/delegate-subdomains/delegate-subdomain)操作。

>[!NOTE]
>
>子域委派可能需要一段时间才能传播。 在您计划访问配置电子邮件渠道实验室之前，请早点开始此委派。

### 短信凭据

[旗舰手机发布](orchestrated-campaigns/flagship-phone-launch/overview.md)实验室通过Twilio配置SMS渠道。 不会发送任何消息，但您需要工作凭据才能完成配置。 最简单的选项是免费的[Twilio试用帐户](https://www.twilio.com/try-twilio) — 请参阅Twilio的[入门指南](https://www.twilio.com/docs/usage/tutorials/how-to-use-your-free-trial-account)，了解如何注册并查找帐户SID和身份验证令牌。
