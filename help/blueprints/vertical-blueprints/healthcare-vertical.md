---
source-git-commit: f7104d114a2644a494003bc78eb20768904f652c
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 1%

---
﻿---
title: 医疗保健
description: 了解Healthcare Shield，它是基于平台的应用程序(如Real-Time CDP、Customer Journey Analytics和Adobe Journey Optimizer)的Adobe Experience Platform附加组件。 该附加组件使这些应用程序符合HIPAA和PHI要求。
solution: Experience Platform
---
# 医疗盾

Healthcare Shield是基于Adobe Experience Platform的应用程序(如Real-Time CDP、Customer Journey Analytics和Adobe Journey Optimizer)的Adobe Experience Platform附加组件，旨在使这些应用程序HIPAA准备好满足有关受保护健康信息(PHI)的处理和使用的要求。

## 关于医疗盾的常见问题

以下常见问题解答提供了有关Healthcare Shield的常见问题解答。

### 什么是HIPAA?

HIPAA是《健康保险流通与责任法案》(HIPAA)，这是一项美国法规，它规定了在由HIPAA覆盖的实体或业务关联方(如Adobe客户)创建、接收、维护或传输给业务关联方(如Adobe)时，限制受保护健康信息(PHI)的使用和披露的重要保护。

Adobe已作为业务关联，就特定的HIPAA就绪Adobe解决方案和对HIPAA安全、隐私和违规通知规则的遵守做好了HIPAA准备。

### 什么是业务协理协议(BAA)，为什么它很重要？

当被保护实体或业务Adobe(Adobe客户)使用业务关联方（如客户）的服务来创建、接收、维护或传输某些类型的消费者数据，这些数据是受保护的医疗保健数据(PHI)或ePHI（PHI的电子版本）时，被保护实体和业务关联方需要签订业务关联协议(BAA)。

BAA合同要求Adobe，因为业务协会应遵守HIPAA隐私、安全和违规通知规则的要求，以适当保护PHI。

借助Real-Time CDP的Healthcare Shield附加组件，Adobe现在能够与授权此功能的客户以及Adobe Real-Time CDP B2C和Adobe Real-Time CDP B2P Edition的客户流一起执行BAA。

### 为什么Real-Time CDP的Healthcare Shield（以及未来基于平台的应用程序）只在美国提供？

由于HIPAA是美国法律，因此我们将Healthcare Shield的可用性限制在美国和受HIPAA约束的公司。 Adobe打算将覆盖范围扩大至其他法域，因为我们负责制定当地要求，并相信我们能够满足这些要求。

### Real-Time CDP的医疗保护盾是什么？

Real-Time CDP的Healthcare Shield是面向属于受保实体或业务关联的客户，他们打算在Real-Time CDP中利用PHI进行数据获取、受众创建和跨渠道激活，并且需要Adobe执行BAA。 Covered Entities with HIPAA要求Hearle-Time CDP使用案例，需要Healthcare Shield。

### 为什么Real-Time CDP的医疗前景应该购买Healthcare Shield?

作为Real-Time CDP的附加组件， Healthcare Shield将应用程序升级为“HIPAA就绪”状态。 这意味着，应用程序已经具备了根据HIPAA要求利用PHI的保障措施。 此外，借助Healthcare Shield，Adobe愿意并且能够授权客户将某些类型的允许的敏感个人数据引入HIPAA就绪型应用程序。 Adobe将与许可Healthcare Shield的客户签署业务协作协议(BAA)，以获得基于平台的兼容应用程序。

### 使用Healthcare Shield为Real-Time CDP授权了哪些类型的数据（哪些类型的数据没有）？

借助Healthcare Shield，各品牌可能会将以下PHI引入基于平台的应用程序，例如Real-Time CDP（“允许的敏感个人数据”）：个人的财务信息、医疗或健康信息。 但是，我们明确排除了可用于识别未成年人滥用药物、精神健康、遗传健康记录或健康记录的数据，包括未成年人的完整账号、完整信用卡号、政府标识符（如SSN），以及受任何儿童保护法律保护的儿童的个人信息(如美国儿童在线隐私法(“COPPA”)所定义的个人信息)。

### 借助Healthcare Shield，Real-Time CDP客户能否使用任何类型的PHI来构建受众并激活受众？

即使客户可能将允许的敏感个人数据引入平台本机应用程序，客户也需要了解，他们完全有责任遵守所有适用的法规，并从消费者处获得以预期方式使用数据的适当权限、同意、许可和授权。

### 使用非HIPAA就绪型Adobe应用程序获取和激活客户数据有何细微差别？

客户授权Healthcare Shield不得使用、摄取、收集、共享允许的敏感个人数据，或将其与任何非HIPAA就绪型Adobe应用程序和服务相集成。 例如，客户不应激活在Audience Manager、Adobe Target和Adobe Analytics等应用程序中包含PHI的区段。 授权Healthcare Shield的客户可以将允许的敏感个人数据或授权的PHI摄取到HIPAA就绪型Adobe应用程序中，而不管数据源是否认为HIPAA就绪。

### 使用非HIPAA就绪型非Adobe应用程序获取和激活客户数据有何细微差别？

客户授权Healthcare Shield应使用正确的判断来确定他们在何处激活在Adobe应用程序之外包含PHI的区段。 Adobe不控制第三方提供商，也不负责由客户发送给第三方提供商的数据，可能不支持根据客户模式中的Adobe数据使用标签进行数据处理。 此外，Adobe无法为我们的客户提供法律建议。

## 关键医疗保健用例

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

|**RTCDP B2C版标准用例**|**描述**| | :- | :- | |流数据收集|<p> — 在Adobe连接和非Adobe连接中均可使用标准化、灵活的数据模型</p><p> — 为B2C营销而设计的基于人员和帐户的数据模式</p><p> — 标签管理和事件转发实时收集和分发事件级别的数据。</p><p> — 优化了用户档案，可加快体验交付时间</p>| |受信任的配置文件管理|<p> — 包含消费者属性、行为和首选项数据的统一配置文件</p><p> — 数据治理框架灵活、透明，并应用于具有策略创建和自动执行功能的统一用户档案，以防止数据滥用。 </p>| |实时激活|<p> — 专为B2C营销人员设计的拖放分段</p><p> — 针对跨渠道激活的个人和帐户级别身份解析和配置文件扩充</p><p> — 通过跨渠道和环境(Adobe和非Adobe)的受众编排和实时激活，提供一致的客户体验</p>| |客户获取|<p> — 分析如何将未验证用户转换为已识别/已验证用户</p><p> — 鼓励未注册的用户注册成员资格。</p><p> — 增加和/或赢回订阅</p><p> — 分析客户用户档案以了解倾向(例如，. 比较高价值区段与性能不佳的区段，并优化客户获取) </p>| |客户参与|<p> — 根据消费者行为新近度和对选件执行频率操作（在线和离线）来定位选件</p><p> — 统一连接体验的数字属性（例如，鼓励移动设备应用程序下载并使用跨渠道的区段激活来连接体验）</p>| |按比例个性化|<p> — 在边缘上评估区段以进行实时同一页面和下一页个性化</p><p> — 通过向在历程中放弃会话的访客提供独特且有针对性的体验（例如放弃购物车、重复无法转化的访客）来提高参与度。</p><p> — 统一并连接离线和在线行为，以优化和吸引用户</p>| |交叉销售/追加销售|<p> — 在保持与用户现有关系的同时留住客户</p><p> — 通过跨业务部门/品牌/选件实现客户生命周期价值，从而创造新的收入流</p><p> — 跨产品和SKU深入了解AOV（例如，频繁的捆绑包、价格敏感性）</p>| |客户维系/忠诚度|<p> — 重新激活消费者以提高忠诚度并避免客户流失</p><p> — 根据偏好和倾向为高价值客户组织个性化产品推荐</p><p> — 为忠诚消费者的参与度和特惠活动创建标准频度</p><p> — 链接在线和离线首选项以优化跨渠道的选件</p>| |数据协作|<p> — 在UI中创建握手以构建数据协作工作流。</p><p>-(利用跨行业的第一方数据重叠，以制定明智的战略业务决策和宣传活动。</p><p> — 划分数据孤岛并了解整体客户历程</p><p> — 尊重首选项和按用例的同意</p>| |媒体/营销效率和优化|<p> — 通过在一个记录系统中集中和维护客户数据和激活渠道来提高组织效率</p><p> — 支持抑制活动以提高媒体支出/效率</p><p> — 通过治理和政策执行与IT政策保持一致</p><p> — 根据需要实时提供数据访问，以支持及时的营销活动</p>|

## **3.相关技术能力**
![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

**差异**:

||**开箱即用**|**医疗盾**| | :- | :- | :- | |加密|AEP中的数据加密 [官方文档](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/encryption.html?lang=en)|<p>AEP中的数据加密 [官方文档](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/encryption.html?lang=en)</p><p>+</p><p>客户管理的密钥 </p>| |数据卫生|<p>**基础**:允许客户管理数据生命周期的自助服务工具。 这包括客户数据删除、字段</p><p>级别更新并设置数据集的数据过期时间，以在过期后删除数据。</p><p>限制 **10,000个删除请求** 每月 </p><p>2个数据集TTL的限制</p>|<p>**Premium**:扩展数据卫生功能的每日容量/阈值，以便在更短的时间内管理较大的数据集。</p><p>限制 **2,000,000个删除请求** 作为医疗盾的一部分</p><p>20个数据集TTL的限制</p>| |同意|<p>**基础**:通过向受众分段手动添加同意和首选项相关属性来细化同意和首选项。</p><p></p>|<p>**Premium**:根据同意和偏好创建并自动实施有关如何使用客户数据的策略。</p><p></p>|

### **治理：**
- **数据卫生**
   - [**数据卫生概述**](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-hygiene/overview.html?lang=en)
   - [**Adobe Experience Platform数据卫生**](https://experienceleague.adobe.com/docs/experience-platform/hygiene/home.html?lang=en)
- **策略执行**
   - [**数据管理概述**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/home.html?lang=en)
   - [**数据使用策略概述**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/policies/overview.html?lang=en)
   - [**Adobe Experience Platform中的管理、隐私和安全**](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/overview.html?lang=en#consent)

### **隐私：**
- **同意**
   - [**自动策略执行**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/enforcement/auto-enforcement.html?lang=en#consent-policy-evaluation)

### **安全性：**
- **访问控制**
   - [**基于属性的访问控制概述**](https://experienceleague.adobe.com/docs/experience-platform/access-control/abac/overview.html)
- **用户活动审核**
   - [**审核日志**](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/audit-logs/overview.html)
- **增强加密**
   - [**Adobe Experience Platform安全概述**](https://www.adobe.com/content/dam/cc/en/security/pdfs/AEP_SecurityOverview.pdf)
   - [**加密值**](https://experienceleague.adobe.com/docs/experience-platform/tags/api/guides/encrypting-values.html?lang=en)
   - [**Adobe Experience Platform中的数据加密**](https://experienceleague.adobe.com/docs/experience-platform/catalog/data-protection.html)
   - [**数据准备映射函数 — 哈希处理**](https://experienceleague.adobe.com/docs/experience-platform/data-prep/functions.html?lang=en#hashing)
- [**Adobe Real-time Customer Data Platform和医疗盾 | Adobe Experience Cloud**](https://experienceleague.adobe.com/docs/customer-data-management-voices-events/events/healthcare-shield.html?lang=en)

实现体验承诺，并减少数据访问。 无论您是广告商、出版商还是代理商，此网络研讨会都将帮助您解锁

- [**审核日志概述 | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/audit-logs/overview.html "https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/audit-logs/overview.html")

了解您如何借助审核日志看到谁在 Adobe Experience Platform 中执行了哪些操作。

- [**数据卫生概述 | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/hygiene/home.html?lang=en)

Adobe Experience Platform数据卫生功能允许您通过更新或清除过时或不准确的记录来管理数据的生命周期。

- [**自动策略实施 | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/enforcement/auto-enforcement.html?lang=en)

本文档介绍了在将区段激活到Experience Platform中的目标时如何自动强制实施数据使用策略。

- [**基于属性的访问控制概述 | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/access-control/abac/overview.html "https://experienceleague.adobe.com/docs/experience-platform/access-control/abac/overview.html")

本文档提供了有关Adobe Experience Platform中基于属性的访问控制的信息
## **4- HIPAA和Adobe产品和服务**
Adobe不断创新和调整以满足医疗保健行业客户的需求，以满足其特定的隐私和安全需求。 

以下是 [详细信息](https://www.adobe.com/trust/compliance/hipaa-ready.html).
## **5 — 高级营销架构图**
已准备好HIPAA（而非）的产品：

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

[https://lucid.app/lucidchart/8a795213-3bfa-43f3-a542-f0de56123afd/edit?invitationId=inv_d3183739-8c07-4ca2-bfd1-16d819b911a6&amp;page=0_0#](https://lucid.app/lucidchart/8a795213-3bfa-43f3-a542-f0de56123afd/edit?invitationId=inv_d3183739-8c07-4ca2-bfd1-16d819b911a6&amp;page=0_0)

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)
## **6 — 方法：**
### **实施阶段：**
![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

在每个步骤中要考虑的方面：

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

本节概述了要遵循的一些最佳实践，并分为三个阶段：
### **访谈阶段：**
与利益相关方的面谈过程是了解以下方面的关键：

- 目标：用例类型 — 转化、潜在客户、参与度等
- 性能：任何服务级别目标期望
- 数据源：Web/Analytics、离线/在线、CRM、忠诚度等
- 数据量
- SLT/SLA要求
- 身份 — 身份数量、已验证数据处理与匿名数据处理
- 数据格式：JSON、CSV等
- 数据质量，需要进行数据转换
- 与合作伙伴进行区段匹配（共享）的任何计划 
- 要导入的任何外部受众
- 加密：默认密钥与客户管理密钥
- 数据的混合：被视为e-PHI
- 同意数据收集 — OneTrust、同意SDK
- 目标需求：频率、延迟和访问控制要求
- 访问控制
- 数据清理要求
- 数据更新要求
- 警报需求
- API访问

### **设计阶段：**
设计阶段将根据面试流程处理以下问题。 不用说，设计文档需要审核和签署。 设计文档可涵盖以下方面：

- 数据值：
   - 卷 — 摄取的数据量
   - 时间跨度 — 摄取的数据应存留的时长
   - 保真度 — 用户档案的丰富度
- 考虑AEP护栏以及SLT/SLA要求 
- 许可证使用情况
- 数据隔离需求 — 单个或多个组织中的多个沙箱
- 数据过滤
- 数据卫生要求（数据量和频率）
- 满足数据删除/更新要求的流程和方法 
- 数据转换需求 — 上游、数据准备、查询服务
- 了解并确定主标识和其他标识
- [XDM架构设计](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en)
- 确定已分析与未分析的数据集的数量
- 合并策略设计
- 同意数据管理
- 治理：角色、标签、策略、营销操作和访问控制
- [用户档案扩充](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hans)
- 边缘/流/批处理的分段设计要求
- 预期目标和激活计划。 仅考虑HIPAA就绪型目标需求
- Analytics计划
- 警报
- 添加API访问要求

### **实施阶段：**
审查并签署设计文档后，实施阶段可以开始处理以下方面：

- 所需沙箱数量：开发/测试/生产
- 对沙箱的访问控制
- 部署方法
- TTL需求和频率（数据卫生）
- XDM架构和访问控制
- 同意执行
- 治理：角色、标签、策略和营销操作 
- 分段
- 数据集和访问控制
- 数据卫生设置
- 目标设置和访问控制
- 设置警报
- 实施API访问要求
- 使用模拟数据端到端测试

