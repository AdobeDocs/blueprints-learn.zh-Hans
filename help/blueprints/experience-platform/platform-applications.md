---
title: Experience Platform (AEP)和应用程序架构图
description: 查看架构图，其中显示了Adobe Experience Platform (AEP)与其他Experience Cloud应用程序和应用程序服务的关联方式。
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: 495a2480828e2c6b4caa41226f4fe67437b081c1
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 10%

---

# Adobe Experience Platform和应用程序架构图

这些架构图显示了Experience Platform (AEP)与其他Experience Cloud应用程序和应用程序服务的关联方式。

>[!MORELIKETHIS]
>
>Experience Cloud应用程序集成的[集成配置](https://experienceleague.adobe.com/docs/integrations-learn/experience-cloud/overview.html?lang=en)。


## 架构图

此架构图展示了 Adobe Experience Platform 与 Adobe Experience Cloud 应用程序和应用程序服务之间的关系。

<img src="assets/aep+apps.svg" alt="Experience Platform 和应用程序" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## 概述图

<img src="assets/aep+apps_overview.svg" alt="Experience Platform 和应用程序" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## 详细的架构图

<img src="assets/aep+apps_detailed.svg" alt="Experience Platform 和应用程序" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

>[!VIDEO](https://video.tv.adobe.com/v/32456/?quality=12&learn=on)

## AEP和Experience Cloud应用程序集成

| 应用程序 | 从 Experience Platform 到应用程序 | 从应用程序到 Experience Platform |
|------------------------------|-----------------------------------|-----------------------------------|
| **Ad Cloud** |  — 可以将在Real-time Customer Data Platform中定义的受众共享到Ad Cloud，以便通过Audience Manager进行定位。 |  — 当前无集成 |
| **Analytics** |  — 通过Web/移动SDK收集的数据可转发到Adobe Analytics。 | - Analytics收集的数据可发送到Experience Platform数据湖和配置文件存储。 [Analytics Data Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=zh-Hans) |
| **Audience Manager** |  — 可以将在Real-time Customer Data Platform中定义的受众共享到Audience Manager，以激活到第三方Cookie目标。 |  — 可以将从Audience Manager收集和评估的数据以及受众成员资格共享到Experience Platform数据湖和配置文件存储。 [Audience Manager 源连接器](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=zh-Hans) |
| **Adobe Campaign** |  — 可以将在Real-time Customer Data Platform中定义的受众共享到Campaign Classic以启动营销活动。 |  — 由Campaign收集的交互和营销活动数据可引入Experience Platform以供进一步用于受众构建、Customer Journey Analytics和查询服务。 |
| **Campaign Standard** |  — 可以将在Real-time Customer Data Platform中定义的受众共享到Campaign Standard以启动营销活动。 |  — 由Campaign收集的交互和营销活动数据可以引入Experience Platform以供进一步使用。 |
| **Customer Journey Analytics** |  — 在Customer Journey Analytics中可处理收集并摄取到Experience Platform数据湖中的数据。 <br> — 可以将来自Real-time Customer Data Platform的个人资料和受众数据摄取到CJA中。 [RTCDP与CJA的集成](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/ingest-aep-segments.html?lang=zh-Hans) |  — 在CJA中构建受众并将受众结果共享到Real-time Customer Data Platform。 [CJA 受众发布](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=zh-Hans) |
| **Experience Manager** |  — 可在服务器端访问Experience Platform配置文件，以便在Experience Manager中提供个性化体验。 |  — 当前无集成，通过Experience Platform Web和Mobile SDK收集在Experience Manager网站上执行的交互。 |
| **Journey Optimizer** |  — 摄取到Experience Platform的数据事件和配置文件将可用于Journey Optimizer。 | - Journey Optimizer生成的交互和营销活动数据将收集到Experience Platform以供进一步使用。 |
| **Adobe Commerce** |  — 在Real-time Customer Data Platform中构建的用户档案和受众可用于在Adobe Commerce中进行个性化。 |  — 可以通过Adobe Commerce源连接器将Adobe Commerce本地的数据发送到Experience Platform。 |
| **Marketo** |  — 可以将在Real-time Customer Data Platform中定义的受众共享到Marketo以启动营销活动并更新对象。 | - Marketo帐户、联系人和营销活动数据将引入Experience Platform以供进一步分析。 [Marketo Engage连接器](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=zh-Hans) |
| **Real-Time CDP** |  — 摄取到Experience Platform的数据是实时客户档案的来源，这些档案为实时客户数据平台提供强大功能。 |  — 受众和个人资料量度将发送到Experience Platform数据湖以供洞察。 |
| **Target** |  — 可以将来自Real-time Customer Data Platform的受众和配置文件属性共享到Target以进行个性化。 |  — 为Target体验收集的数据可以发送到Experience Platform以构建受众和分析。 |
