---
title: Adobe Experience Platform 和应用程序架构图
description: 此架构图展示了 Adobe Experience Platform 与其他 Adobe Experience Cloud 应用程序和应用程序服务之间的关系。
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Real-time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: 83f1f5e0e508d35d6711710cdb4d367f67e4f715
workflow-type: ht
source-wordcount: '917'
ht-degree: 100%

---

# Adobe Experience Platform 和应用程序

## Adobe Experience Platform 和应用程序架构图

此架构图展示了 Adobe Experience Platform 与 Adobe Experience Cloud 应用程序和应用程序服务之间的关系。

<img src="assets/aep+apps_vertical.svg" alt="Experience Platform 和应用程序" style="border:1px solid #4a4a4a; width:90%;" />

## Adobe Experience Platform 和应用程序详细架构图

<img src="assets/aep+apps_horizontal.svg" alt="Experience Platform 和应用程序" style="border:1px solid #4a4a4a; width:90%;" />

>[!VIDEO](https://video.tv.adobe.com/v/32456/?quality=12&learn=on)

## Adobe Experience Platform 和 Experience Cloud 应用程序集成

<table class="relative-table wrapped" style="width: 100%;">
<colgroup>
<col style="width: 16.0202%;" />
<col style="width: 29.3423%;" />
<col style="width: 33.5582%;" />
<col style="width: 21.0793%;" />
</colgroup>
<tbody>
<tr>
<th>应用程序</th>
<th>从 Experience Platform 到应用程序</th>
<th>从应用程序到 Experience Platform</th>
<th>相关蓝图</th>
</tr>
<tr>
<td colspan="1">Ad Cloud</td>
<td colspan="1">
<ul>
<li>Real-time Customer Data Platform 中定义的受众可以共享到 Ad Cloud，以便通过 Audience Manager 进行定位。</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>当前无集成</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=zh-Hans">匿名受众激活</a></li>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=zh-Hans">已知客户激活</a></li>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html?lang=zh-Hans">通过 Experience Platform 和应用程序进行激活</a></li>
</ul>
</td>
</tr>
<tr>
<td>Analytics</td>
<td>
<ul>
<li>当前无集成</li>
</ul>
</td>
<td>
<ul>
<li>Analytics 收集的数据可以发送到 Experience Platform 数据湖和用户档案存储。 <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=zh-Hans">Analytics 数据连接器</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-data-flow.html?lang=zh-Hans">Experience Platform 数据流</a></li>
</ul>
</td>
</tr>
<tr>
<td>Audience Manager</td>
<td>
<ul>
<li>可以将 Real-time Customer Data Platform 中定义的受众共享到 Audience Manager，以便激活到第三方 Cookie 目的地。</li>
</ul>
</td>
<td>
<ul>
<li>可以将收集和评估的受众会员资格数据共享到 Experience Platform 数据湖和用户档案存储。 <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=zh-Hans">Audience Manager 源连接器</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=zh-Hans">匿名受众激活</a></li>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=zh-Hans">已知客户激活</a></li>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=zh-Hans">通过 Experience Platform 和应用程序进行激活</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Campaign Classic</td>
<td colspan="1">
<ul>
<li>可以将 Real-time Customer Data Platform 中定义的受众共享至 Campaign Classic，作为启动营销活动的受众。</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>Campaign 收集的交互和营销活动数据可作为数据源引入 Experience Platform，以供在通过 Real-time Customer Data Platform 构建受众时，以及通过 Customer Journey Analytics、Experience Platform 查询服务进行分析时进一步使用。</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/overview.html?lang=zh-Hans">客户历程</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Campaign Standard</td>
<td colspan="1">
<ul>
<li>可以将 Real-time Customer Data Platform 中定义的受众共享至 Campaign Standard，作为启动营销活动的受众。</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>Campaign 收集的交互和营销活动数据可作为数据源引入 Experience Platform，以供在通过 Real-time Customer Data Platform 构建受众时，以及通过 Customer Journey Analytics、Experience Platform 查询服务进行分析时进一步使用。</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/overview.html?lang=zh-Hans">客户历程</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Customer Journey Analytics</td>
<td colspan="1">
<ul>
<li>收集并摄入 Experience Platform 数据湖中的数据可用于处理到 Customer Journey Analytics 中。 </li>
</ul>
</td>
<td colspan="1">
<ul>
<li>在 Customer Journey Analtyics 中构建受众，并将受众结果共享到 Real-time Customer Data Platform。<a href="https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=zh-Hans">CJA 受众发布</a></li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=zh-Hans">Customer Journey Analytics</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Experience Manager</td>
<td colspan="1">
<ul>
<li>可以直接在服务器端访问 Experience Platform 用户档案，以支持通过 Experience Manager 提供的个性化体验。请注意，个性化活动通常通过 Target 集成在 Experience Manager 内提供。 </li>
</ul>
</td>
<td colspan="1">
<ul>
<li>不会通过 Experience Platform Web 和 Mobile SDK 直接收集当前在 Experience Manager Sites 上执行的集成、行为和交互。</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=zh-Hans">已知客户激活</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Journey Optimizer</td>
<td colspan="1">
<ul>
<li>Journey Optimizer 可以使用摄入 Experience Platform 的数据事件和用户档案来启动 Journey Optimizer 中的历程并为其提供支持。</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>Journey Optimizer 生成的交互和营销活动数据会收集到 Experience Platform 中，以便在通过 Real-time Customer Data Platform 构建受众时，以及通过 Customer Journey Analytics 和 Experience Platform 查询服务进行分析时进一步使用。</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=zh-Hans">Journey Optimizer</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Magento</td>
<td colspan="1">
<ul>
<li>当前无集成</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>Magento 的本机数据可通过 Magento 源连接器发送到 Experience Platform。 </li>
</ul>
</td>
<td colspan="1">当前无集成</td>
</tr>
<tr>
<td colspan="1">Marketo</td>
<td colspan="1">
<ul>
<li>Real-time Customer Data Platform 中定义的受众可以作为受众共享给 Marketo，以启动 Marketo 营销活动和更新 Marketo 对象。</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>Marketo 帐户、联系人和机会数据，以及 Marketo 生成的交互和营销活动数据，都会被摄入 Experience Platform 中，以便在通过 B2B-CDP 构建受众时，以及通过 Customer Journey Analytics 和 Experience Platform 查询服务进行分析时进一步使用。 <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=zh-Hans">Marketo Engage 连接器</a></li>
</ul>
</td>
<td colspan="1">
<ul>
<li>B2B 激活 - 正在开发中</li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Real-time CDP</td>
<td colspan="1">
<ul>
<li>摄入并收集到 Experience Platform 中的数据是用于组合实时客户用户档案的数据源，可支持 Real-time Customer Data Platform。</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>受众和用户档案量度会发送到 Experience Platform 数据湖，以支持用户档案洞察报告仪表板。</li>
<li>数据湖中的受众和用户档案数据可用于通过查询服务和 Customer Journey Analytics 获取进一步洞察。</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=zh-Hans">已知客户激活</a></li>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=zh-Hans">通过 Experience Platform 和应用程序进行激活</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Target</td>
<td colspan="1">
<ul>
<li>Real-time Customer Data Platform 中定义的受众和用户档案属性可以共享到 Target，并用于 Target 提供的个性化和定位体验。</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>可以通过 Experience Platform Web/Mobile SDK 将为 Target 体验和交互收集的数据收集至 Experience Platform。此数据可用于通过 Real-time Customer Data Platform 构建受众以及通过 Customer Journey Analytics 和 Experience Platform 查询服务进行分析。</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=zh-Hans">已知客户激活</a></li>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=zh-Hans">通过 Experience Platform 和应用程序进行激活</a></li>
</ul>
</td>
</tr>
</tbody>
</table>