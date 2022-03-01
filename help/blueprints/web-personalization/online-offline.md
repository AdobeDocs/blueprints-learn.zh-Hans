---
title: 使用线上和线下数据进行 Web/移动个性化
description: 将 Web 个性化与电子邮件和其他已知和匿名渠道的个性化同步。
landing-page-description: 将 Web 个性化与电子邮件和其他已知和匿名渠道的个性化同步。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 05cda4f092b7f0ee54e580124e5349955e353d9c
workflow-type: tm+mt
source-wordcount: '1521'
ht-degree: 48%

---

# 使用线上和线下数据进行 Web/移动个性化

将 Web 个性化与电子邮件和其他已知和匿名渠道的个性化同步。

## 用例

* 登陆页优化
* 行为和线下用户档案定位
* 除线下洞察（如交易、预订、CRM 和忠诚度数据）和模型洞察以外，还基于以前的产品/内容视图、产品/内容关联、环境属性、第三方受众数据和人口统计的个性化
* 使用 Adobe Target 在网站和移动设备应用程序上共享和定位 Real-time Customer Data Platform 中定义的受众。

## 应用程序

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager（可选）：添加了第三方受众数据、基于协作的设备图、在Adobe Analytics中显示Real-time Customer Data Platform受众的功能，以及在Real-time Customer Data Platform中显示Adobe Analytics受众的功能
* Adobe Analytics（可选）：添加了根据历史行为数据和来自 Adobe Analytics 数据的精细分段来构建区段的功能

## 用例方案

<table class="tg" style="undefined;table-layout: fixed; width: 790px">
<colgroup>
<col style="width: 20px">
<col style="width: 276px">
<col style="width: 229px">
<col style="width: 265px">
</colgroup>
<thead>
  <tr>
    <th class="tg-y6fn">#</th>
    <th class="tg-f7v4">用例方案</th>
    <th class="tg-y6fn">功能</th>
    <th class="tg-f7v4">先决条件</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">1</td>
<td class="tg-73oq">对从Real-time Customer Data Platform共享到Target的Edge进行实时区段评估</td>
    <td class="tg-0lax"> - 在 Edge 上实时评估受众以进行同页或下一页个性化。<br> — 此外，任何以流方式或批量方式评估的区段也将投影到边缘网络，以包含在边缘区段评估和个性化中。</td>
    <td class="tg-73oq"> — 实施模式1，如下所述。<br> — 必须实施Web/Mobile SDK。<br> — 请注意，当前不提供基于Mobile SDK和API的实时分段支持<br> — 必须在Experience Edge中配置数据流，并启用Target和Experience Platform扩展，数据流ID将在Target目标配置中提供。<br> — 必须在Real-time Customer Data Platform目标中配置目标。<br>- 与 Target 集成需要与 Experience Platform 实例具有相同的 IMS 组织。</td> 
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-73oq">通过Edge方法从Real-time Customer Data Platform到Target的流式受众和批量受众共享</td>
    <td class="tg-0lax"> — 通过边缘网络将来自Real-time Customer Data Platform的流受众和批量受众共享到Target。 要实时评估受众，需要集成模式 1 中概述的 WebSDK 和实时受众评估。<br> — 此集成通常用于使用传统SDK共享流受众和批量受众，而不是迁移到Edge Collection和WebSDK，后者支持实时受众以及流受众和批量受众，如集成协议1中所述。</td>
    <td class="tg-73oq"> — 实施模式1或2如下所述。<br> — 将流受众和批量受众共享到Target时，不需要Web/Mobile SDK，不过需要它来启用实时边缘区段评估，如集成模式1中所述。 <br> — 如果使用AT.js，则仅支持与ECID标识命名空间的配置文件集成。 <br> — 对于Edge上的自定义身份命名空间查找，需要WebSDK部署，并且必须在身份映射中将每个身份设置为身份。<br> — 数据流必须在Experience Edge中配置，数据流ID将在Target目标配置中提供。<br> — 必须在Real-time Customer Data Platform目标中配置目标。<br>- 与 Target 集成需要与 Experience Platform 实例具有相同的 IMS 组织。</td>
  </tr>
  <tr>
    <td class="tg-0lax">3</td>
    <td class="tg-73oq"><span style="font-weight:400;font-style:normal">通过受众共享服务方法从Real-time Customer Data Platform到Target和Audience Manager进行流式和批量受众共享</span></td>
    <td class="tg-0lax"><span style="font-weight:400;font-style:normal"> — 通过受众共享服务，将流受众和批量受众从Real-time Customer Data Platform共享到Target，并Audience Manager。<br>  — 当需要从第三方数据和Audience Manager中的受众进行额外扩充时，可以利用此集成模式。 否则，首选集成模式1和2。 要实时评估受众，需要集成模式 1 中概述的 WebSDK 和实时受众评估。</span></td>
    <td class="tg-73oq"> — 实施模式1或2如下所述。<br> — 此集成不需要Web/Mobile SDK部署。<br> - 必须配置通过受众共享服务的受众投影。<br>- 与 Target 集成需要与 Experience Platform 实例具有相同的 IMS 组织。<br>- 必须将身份解析为 ECID 才能共享到 Edge，以便 Target 对其执行操作。</td>
  </tr>
</tbody>
</table>

## 场景1和2 — 将实时、流式和批量受众共享到Adobe Target

架构

<img src="assets/RTCDP+Target.png" alt="线上/线下 Web 个性化 Blueprint 的参考架构" style="width:80%; border:1px solid #4a4a4a" />

序列详细信息

<img src="assets/RTCDP+Target_flow.png" alt="线上/线下 Web 个性化 Blueprint 的参考架构" style="width:80%; border:1px solid #4a4a4a" />

用例情景1和2的概述架构

<img src="assets/personalization_with_apps.png" alt="线上/线下 Web 个性化 Blueprint 的参考架构" style="width:80%; border:1px solid #4a4a4a"/>

### 用例情景1的实施步骤，还支持用例情景2

1. 为您的 Web 或移动应用程序[实施 Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=zh-Hans)
1. [实施 Experience Platform 和[!UICONTROL 实时客户档案]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=zh-Hans)
1. 实施 [Experience PlatformWeb SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hans). Experience PlatformWeb SDK是实时边缘分段所必需的，但将流受众和批量受众从Real-time Customer Data Platform共享到Target时则不需要。 请注意，目前不支持通过Mobile SDK和API进行实时分段。
1. [使用边缘数据流配置边缘网络](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)
1. [在Adobe Target中启用Real-time Customer Data Platform作为目标](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=zh-Hans)

## 场景3 — 通过受众共享服务将受众流和批量共享到Adobe Target和Audience Manager

架构

<img src="assets/audience_share_architecture.png" alt="线上/线下 Web 个性化 Blueprint 的参考架构" style="width:80%; border:1px solid #4a4a4a" />

### 情景3的实施步骤，还支持情景2

1. 为您的 Web 或移动应用程序[实施 Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html)
1. [实施 Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=zh-Hans)（可选）
1. [实施 Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=zh-Hans)（可选）
1. [实施 Experience Platform 和[!UICONTROL 实时客户档案]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html)
1. 实施 [Experience Cloud标识服务](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=zh-Hans)
1. [请求配置Experience Platform与Adobe Target（共享受众）之间的受众共享](https://www.adobe.com/go/audiences) 将受众从Experience Platform共享到Target。
1. （可选） [使用边缘数据流配置边缘网络](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) (仅当集成模式2需要使用此参数时，才需要将受众共享到Audience Manager，或通过Audience Manager受众或数据扩充受众)。
1. （可选） [在Adobe Target中启用Real-time Customer Data Platform作为目标](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en) 与通过受众共享服务和Audience Manager将流受众和批量受众从Real-time Customer Data Platform直接共享到Edge。

## 实施模式

通过多种实施方法支持在线和离线个性化。

### 实施模式1 — 支持用例情景1和2。 使用Web/Mobile SDK的边缘网络（推荐方法）

将边缘网络与Web/Mobile SDK结合使用
<img src="assets/web_sdk_flow.png" alt="特定于应用程序的 SDK 方法的参考架构" style="width:80%; border:1px solid #4a4a4a" />

序列图

<img src="assets/RTCDP+Target_sequence.png" alt="线上/线下 Web 个性化 Blueprint 的参考架构" style="width:80%; border:1px solid #4a4a4a" />

### 实施模式2 — 支持用例情景2和3。 特定于应用程序的SDK

使用传统的特定于应用程序的SDK（例如，AT.js和AppMeasurement.js）
<img src="assets/app_sdk_flow.png" alt="特定于应用程序的 SDK 方法的参考架构" style="width:80%; border:1px solid #4a4a4a" />

## 护栏

[请参阅“Web 和移动个性化 Blueprint 概述”页面上的护栏。](overview.md)

## 实施注意事项

身份先决条件

* 在边缘网络和WebSDK中利用上述实施模式1时，可以利用任何主标识。 首次登录个性化要求个性化请求集主标识与Real-time Customer Data Platform中用户档案的主标识相匹配。 匿名设备与已知客户之间的身份拼合会在中心进行处理，然后投影到边缘。
* 将受众从Adobe Experience Platform共享到Adobe Target时，在使用受众共享服务时，需要使用ECID作为标识，如上面的用例情景3中所述。
* 替代身份也可用于通过Audience Manager将Experience Platform受众共享到Adobe Target。 Experience Platform通过以下受支持的命名空间激活受众以Audience Manager：IDFA、GAID、AdCloud、Google、ECID、EMAIL_LC_SHA256。 请注意，Audience Manager 和 Target 通过 ECID 身份解析受众成员关系，因此要将最终受众共享到 Adobe Target，仍然需要 ECID。

## 相关文档

### 文档

* [用于 Real-time Customer Data Platform 的 Adobe Target 连接](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
* [与 Audience Manager 和其他 Experience Cloud 解决方案共享 Experience Platform 区段](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=zh-Hans)
* [Experience Platform Web SDK 文档](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Experience Cloud ID 服务文档](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=zh-Hans)
* [Experience Platform 分段概述](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hans)
* [实时分段](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html)
* [流式分段](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hans)
* [Experience Platform 区段生成器概述](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html)
* [Audience Manager 源连接器](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=zh-Hans)
* [通过 Adobe Audience Manager 分享 Adobe Analytics 区段](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=zh-Hans)
* [Experience Platform 标记文档](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hans)

### 教程

* [使用 Real-time CDP 和 Adobe Target 实现下一次点击的个性化](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=zh-Hans)

## 相关博客帖子

* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
* [[!DNL Integrating Adobe Experience Platform Decisioning Engine with AEM Websites]](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [[!DNL Adobe Experience Platform’s Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL How Adobe Experience Platform Can Help Customers Personalize Their Mobile Messaging in Real-Time with Journey Orchestration Service and a Mobile Messaging Vendor]](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
