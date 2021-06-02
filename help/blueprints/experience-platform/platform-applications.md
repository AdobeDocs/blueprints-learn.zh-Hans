---
title: Adobe Experience Platform 和应用程序架构图
description: 此架构图展示了 Adobe Experience Platform 与其他 Adobe Experience Cloud 应用程序和应用程序服务之间的关系。
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Offer Decisioning, Real-time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: 6c4b72159d4ba2a171215678e4e4842956d82745
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 11%

---

# Adobe Experience Platform 和应用程序

## Adobe Experience Platform 和应用程序架构图

此架构图展示了 Adobe Experience Platform 与 Adobe Experience Cloud 应用程序和应用程序服务之间的关系。

<img src="assets/aep+apps_vertical.svg" alt="Experience Platform 和应用程序" style="border:1px solid #4a4a4a; width:80%;" />

>[!VIDEO](https://video.tv.adobe.com/v/32456/?quality=12&learn=on)

## Adobe Experience Platform 和应用程序详细架构图

<img src="assets/aep+apps_horizontal.svg" alt="Experience Platform 和应用程序" style="border:1px solid #4a4a4a; width:80%;" />

## Adobe Experience Platform和Experience Cloud应用程序集成

<table class="relative-table wrapped" style="width: 100%;" >
   <colgroup>
    <col style="width: 16.0202%;"/>
    <col style="width: 29.3423%;"/>
    <col style="width: 33.5582%;"/>
    <col style="width: 21.0793%;"/>
  </colgroup>
  <tbody>
    <tr>
      <th>应用程序</th>
      <th>Experience Platform到应用程序</th>
      <th>应用程序到Experience Platform</th>
      <th>相关蓝图</th>
    </tr>
    <tr>
      <td colspan="1">Ad Cloud</td>
      <td colspan="1">
        <ul>
          <li>实时客户数据平台中定义的受众可以共享到Ad Cloud，以便通过Audience Manager进行定位。</li>
        </ul>
      </td>
      <td colspan="1">当前无集成</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">匿名受众激活</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">线上/线下受众激活</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Experience Platform和应用程序激活</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Analytics</td>
      <td>当前无集成</td>
      <td>
        <ul>
          <li>Analytics收集的数据可以发送到Experience Platform数据湖和配置文件存储。 <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en">Analytics Data Connector</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-data-flow.html?lang=en">Experience Platform数据流</a>
          </li>
        </ul>
        <p>
          <br/>
        </p>
      </td>
    </tr>
    <tr>
      <td>Audience Manager</td>
      <td>
        <ul>
          <li>可以将实时Audience Manager数据平台中定义的受众共享到客户，以便激活到第三方Cookie目标。</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>可以将收集和评估的受众成员资格数据共享到Experience Platform数据湖和用户档案存储。 <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=en">Audience Manager 源连接器</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">匿名受众激活</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">线上/线下受众激活</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Experience Platform和应用程序激活</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Classic</td>
      <td colspan="1">
        <ul>
          <li>可以将实时Campaign Classic数据平台中定义的受众共享为启动促销活动的受众。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Campaign收集的交互和促销活动数据可作为Experience Platform数据源引入，以供在通过实时客户数据平台构建受众以及通过Customer Journey Analytics和Experience Platform查询服务和数据科学工作区进行分析时进一步使用。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/batch-messaging.html?lang=en">批量消息传送</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Standard</td>
      <td colspan="1">
        <ul>
          <li>可以将实时Campaign Standard数据平台中定义的受众共享为启动促销活动的受众。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Campaign收集的交互和促销活动数据可作为Experience Platform数据源引入，以供在通过实时客户数据平台构建受众以及通过Customer Journey Analytics和Experience Platform查询服务和数据科学工作区进行分析时进一步使用。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/batch-messaging.html?lang=en">批量消息传送</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Customer Journey Analytics</td>
      <td colspan="1">
        <ul>
          <li>收集并摄取到Experience Platform数据湖中的数据可用于处理到Customer Journey Analytics中。 </li>
        </ul>
      </td>
      <td colspan="1">当前没有可用的集成。 路线图上提供了从Customer Journey Analytics将受众结果共享到Experience Platform的功能。</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=en">Customer Journey Analytics</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Experience Manager</td>
      <td colspan="1">
        <ul>
          <li>可以直接在服务器端访问Experience Platform配置文件，以提供通过Experience Manager提供的个性化体验。 请注意，个性化活动通常通过Target集成通过Experience Manager提供。 </li>
        </ul>
      </td>
      <td colspan="1">不会通过Experience PlatformWeb SDK和Mobile SDK直接收集当前在Experience Manager网站上执行的集成、行为和交互。</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">线上/线下受众激活</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Journey Optimizer</td>
      <td colspan="1">
        <ul>
          <li>Journey Optimizer可以使用摄取到Experience Platform的数据事件和配置文件来启动Journey Optimizer中的旅程并为其提供支持。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Journey Optimizer生成的交互和促销活动数据会收集到Experience Platform中，以便在通过实时客户数据平台构建受众以及通过Customer Journey Analytics、Experience Platform查询服务和数据科学工作区进行分析时进一步使用。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/triggered-messaging.html?lang=en">触发消息</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Magento</td>
      <td colspan="1">当前无集成</td>
      <td colspan="1">当前无集成</td>
      <td colspan="1">当前无集成</td>
    </tr>
    <tr>
      <td colspan="1">Marketo</td>
      <td colspan="1">
        <ul>
          <li>实时客户数据平台中定义的受众可以作为受众共享给Marketo，以启动Marketo促销活动和更新Marketo对象。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Marketo帐户、联系人和机会数据，以及Marketo生成的交互和促销活动数据，都被摄取到Experience Platform中，以便通过B2B-CDP在受众构建中进一步使用，以及通过Customer Journey Analytics、Experience Platform查询服务和数据科学工作区进行分析。 <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=en">Marketo Engage连接器</a>
          </li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>B2B激活 — 正在开发中</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Real-time CDP</td>
      <td colspan="1">
        <ul>
          <li>摄取并收集到Experience Platform中的数据是用于汇编实时客户用户档案的数据源，可支持实时客户数据平台。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>受众和配置文件量度会发送到Experience Platform数据湖，以增强配置文件分析报表功能板。</li>
          <li>数据湖中的受众和用户档案数据可用于通过查询服务、数据科学工作区和Customer Journey Analytics进一步分析。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">线上/线下受众激活</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Experience Platform和应用程序激活</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Target</td>
      <td colspan="1">
        <ul>
          <li>实时客户数据平台中定义的受众可以共享到Target，并用于Target提供的个性化和定位体验。 </li>
          <li>路线图中提供了与Target的直接Experience Edge集成，以便实时获取区段成员资格和配置文件属性访问权限。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>可以通过Experience PlatformWeb SDK收集为Target体验和交互收集的数据以进行Experience Platform。 此数据可用于通过实时客户数据平台构建受众以及通过Customer Journey Analytics进行分析，  Experience Platform查询服务和数据科学工作区。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">线上/线下受众激活</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Experience Platform和应用程序激活</a>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
