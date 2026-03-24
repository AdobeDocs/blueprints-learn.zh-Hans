---
title: 汽车用例
description: 了解汽车行业组织如何使用Adobe Experience Platform使车辆购买历程个性化、提高服务保留率和建立所有者忠诚度。
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: ee83c739-0907-481d-ba3f-358af4e03c67
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '1941'
ht-degree: 4%

---

# 汽车用例

汽车企业使用Adobe Experience Platform将来自经销商互动、在线车辆研究、服务记录和联网汽车系统的客户数据统一到每个所有者的单一视图中。 这一基础将在整个所有权生命周期（从最初的车辆研究到购买、服务和忠诚度）中实现个性化体验。

## 用例摘要

| 用例 | 描述 | 商业影响 | 实施模式 |
| --- | --- | --- | --- |
| [车辆购买Personalization](#vehicle-purchase-journey-personalization) | 利用相关的车辆推荐、融资选项和经销商信息，将车辆购买历程（从研究到购买）个性化。 当潜在买家在每个阶段都获得量身定制的指导时，他们会更快更自信地走过销售funnel。 | 提高了从销售线索到购买的转化率，并增强了销售渠道 | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [服务约会提醒](#service-appointment-reminders) | 根据车辆里程数、服务历史记录和客户偏好发送个性化服务提醒。 积极主动的外联活动保持车辆保持畅通，并确保客户返回经销商，而不是寻求第三方提供商。 | 提高服务预约出勤率并增加服务收入 | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [折价促销活动](#trade-in-value-campaigns) | 主动为准备好进行升级的客户提供以旧换新价值评估。 在车主拥有权周期的适当时刻与其接触，加速了购买新车的步伐。 | 提高以旧换新参与度和增加新车销售 | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [部件和附件推荐](#parts-and-accessories-recommendations) | 根据车辆型号、所有权持续时间和客户偏好推荐相关部件、附件和升级。 个性化的售后推荐可带来递增收入，同时帮助所有者从自己的车辆中获得更多回报。 | 零件及配件采购率提升及售后收益增加 | [行为推荐](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| [车辆召回通知](#vehicle-recall-notifications) | 发送带有服务计划选项和安全信息的个性化召回通知。 及时、清晰的召回沟通可保护客户安全，并表明品牌对负责任的所有权支持的承诺。 | 提高了召回响应率和更强的安全合规性 | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [新模型启动促销活动](#new-model-launch-campaigns) | 根据当前车辆、偏好和购买历史记录，定位可能对新车型发布感兴趣的客户。 有针对性的受众定位可最大程度地提高启动的影响力并形成早期订单势头。 | 改进了启动促销活动参与度，增加了新模型的兴趣 | [批出站消息激活](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| [融资和保险优惠](#financing-and-insurance-offers) | 根据信用档案、车辆选择和购买时间表提供个性化的融资和保险优惠。 量身定制的金融产品消除了购买障碍，并帮助客户对自己的条款充满信心。 | 提高融资接受率并增加每次销售收入 | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| [试用计划](#test-drive-scheduling) | 通过经销商推荐和车辆可用性，实现个性化的试驾计划。 让有兴趣的买家轻而易举地后退，加快了购买步伐。 | 提高了试运行完成率和更强的销售转化率 | [事件触发的消息传送](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [所有者忠诚度计划](#owner-loyalty-programs) | 协调经销商、OEM数字和互联汽车渠道之间的忠诚度通信，应用基于分层的资格规则来控制哪些所有者获得独家优惠、提前车辆访问和合作伙伴奖励。 优惠仲裁可防止经销商和OEM渠道的相互冲突的促销活动同时到达同一个所有者。 | 提高了忠诚度计划参与度，增加了重复购买次数 | 使用Decisioning [跨渠道历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [保修和延长服务计划](#warranty-and-extended-service-plans) | 根据车辆使用时间、里程和购买模式，在最佳时间建议保修和延长服务计划。 在工厂保修期到期之前，适时开展的外联活动可以捕捉到收入。 | 改进了延保采用率并增加了服务收入 | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [连接的汽车功能激活](#connected-car-feature-activation) | 根据车辆功能和技术偏好提供个性化的联网汽车功能推荐。 帮助所有者发现未使用的功能可提高满意度并增强数字关系。 | 提高了功能激活率，改善了客户体验 | [多步骤编排历程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [经销商网络协调](#dealer-network-coordination) | 根据客户地点、偏好和经销商库存启用个性化的经销商推荐。 将客户与正确的经销商连接起来可改善购买和服务体验。 | 经销商参与率提高，销售协调性增强 | [已知访客Web/应用程序Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

## 用例的技术注意事项

### 车辆购买历程个性化

- 经销商管理系统的车辆库存数据必须经常集成和更新，以便建议能反映附近经销商的实际可用性。
- 必须捕获整个网站中的客户研究行为（包括车辆配置活动、比较工具使用情况和手册下载），以准确识别购买意向信号。
- 潜在客户评分模型应考虑到在线参与和离线信号（如代理商访问和电话查询），以优先考虑意向最高的潜在客户。
- 一旦潜在客户注册或访问经销商，[!DNL Real-Time Customer Data Platform]用户档案必须将匿名Web研究会话与已知的客户身份合并。

### 服务约会提醒

- 来自连接的汽车系统或经销商服务记录的车辆里程和远程信息数据必须流入客户档案，以在正确的服务间隔触发提醒。
- 提醒消息应包含一键式计划链接，以预先填充客户的车辆信息和推荐的服务项目，从而最大程度地减少预订摩擦。
- 必须集成服务历史记录，以避免推荐最近完成的服务，并使用到期的特定维护项目将提醒个性化。
- [!DNL Journey Optimizer]消息时间应考虑经销商服务能力和营业时间，以确保客户在收到提醒时可以预约约会。

### 折价促销活动

- 来自第三方提供商的车辆估值数据必须整合并定期更新，以确保与客户分享的折价估计准确且具有竞争力。
- 所有权生命周期模型应考虑租赁到期日期、贷款偿还时间表以及按车辆细分的平均所有权持续时间等因素，以确定最佳推广窗口。
- Campaign消息应动态引用客户的当前载体，并根据客户的偏好和预算建议具体的升级选项。
- [!DNL Experience Platform]区段应排除最近购买了车辆或当前存在服务争议的客户，以避免外展时间安排不当。

### 部件和附件推荐

- 产品目录数据必须包含车辆兼容性信息，以便推荐仅显示适合客户特定车辆年份、制造商和型号的部件和附件。
- 季节和区域因素应影响推荐；冬季配件应在较冷的气候中推广，而性能提升可能会在拥有活跃爱好者社区的区域引起更大的共鸣。
- 必须捕获部件和附件页面上的浏览行为并与客户配置文件关联，以根据表达的兴趣来优化推荐。
- [!DNL Experience Platform] Web SDK实施应从经过身份验证的会话中捕获车辆识别号数据，以确保兼容性筛选的准确性。

### 车辆召回通知

- 必须在客户档案中准确维护车辆识别号记录，以便召回通知可到达每个受影响的车主且不会到达未受影响的客户。
- 召回报文传送必须符合针对每个适用市场中的安全通知内容、时间以及传送确认的监管要求。
- 应使用多渠道投放（电子邮件、短信、推送通知和物理邮件）来最大限度地扩大覆盖范围，因为安全关键型通信需要比营销消息更高的投放保证。
- [!DNL Journey Optimizer]应跟踪个人级别的回调响应状态，并向未在定义的时间范围内计划服务的所有者升级跟进通信。

### 新模型启动促销活动

- 启动促销活动的受众区段应考虑当前车辆模型、所有权持续时间、过去模型兴趣信号和人口统计拟合度，以识别最高倾向前景。
- Launch内容应进行个性化以引用客户当前的媒介，并突出显示可解决其可能优先级的特定改进或功能。
- 促销活动时间必须与禁运日期和区域发布计划相协调，以确保客户在适当的时间收到与其市场相关的信息。
- [!DNL Real-Time Customer Data Platform]受众激活应将启动区段同步到广告平台，以便在自有渠道外联之外提供协调的付费媒体支持。

### 融资和保险优惠

- 必须仔细配置金融优惠资格规则，以符合贷款法规，确保向客户提供的优惠符合他们实际可获得的资格。
- 由于金融信息需要遵守更严格的隐私和监管要求，因此信用配置文件数据集成需要安全的处理和严格的访问控制。
- 优惠呈报必须明确披露各适用市场遵守消费金融法规之条款、比率及条件。
- [!DNL Journey Optimizer]决策规则应该将车辆价格、首付和贷款期限偏好设置考虑在内，以便根据相关性而不是简单地根据费率对优惠进行排名。

### 测试驱动器计划

- 必须集成经销商库存系统，以确认客户感兴趣的特定车辆型号和配饰可在推荐的经销商处试运行。
- 基于位置的经销商推荐应考虑客户地址、经销商评级和当前预约可用性，以推荐最方便的选项。
- 试用确认和提醒报文应包括说明、经销商联系信息以及期待信息，降低缺席率。
- [!DNL Experience Platform]行为数据应确定建议进行测试的最佳时机，避免过早联系尚未准备就绪的早期研究人员。

### 所有者忠诚度计划

- 忠诚度等级计算必须包含参与度的多个维度，包括服务访问、部件购买、反向链接和事件出席情况，而不仅仅是车辆购买历史记录。
- 必须在[!DNL Journey Optimizer]决策中配置基于层的资格规则，以控制哪些所有者有资格获得独占优惠、对新车辆的提前访问揭示以及合作伙伴奖励赎回，确保仅符合条件的成员获得每个类别的福利。
- 优惠仲裁逻辑必须在发送任何消息之前评估来自经销商和OEM渠道的待处理通信，抑制低优先级或冲突的促销以防止同一所有者同时接收冲突的优惠。
- 跨渠道协调必须跨经销商CRM系统、OEM数字资产、连接的汽车通知渠道和服务接触点进行，以便无论所有者从事什么活动，忠诚度互动都是一致的。
- 必须集成经销商和服务中心的奖励履行系统，以便在服务点可以无缝地兑现忠诚度福利。
- 通信应根据所有权的生命周期阶段进行调整，在新所有者第一年为其提供不同的价值主张，而长期所有者则接近潜在升级。
- [!DNL Journey Optimizer]历程逻辑应实时检测层变化，并在客户在不同忠诚度级别之间切换时触发祝贺或重新参与消息。

### 保修和延长服务计划

- 必须在客户配置文件中准确跟踪保修到期日期和服务范围详细信息，以便在适当时间（通常在到期前60-90天）触发外联。
- 联网汽车数据或服务记录中的车辆里程和使用模式应告知计划建议，因为高里程驾驶员与低里程所有者相比可从不同的覆盖范围中获益。
- 计划比较内容应清晰且没有术语，以帮助客户准确了解涵盖的内容以及相对于潜在自付维修成本的价值。
- [!DNL Real-Time Customer Data Platform]区段应区分工厂保修即将到期的客户、现有延长计划即将续订的客户，以及当前覆盖范围不存在的客户。

### 连接汽车功能激活

- 必须集成连接的汽车平台数据，以识别每辆汽车上可用的功能以及车主已激活或使用的功能。
- 功能采用跟踪应捕获激活事件、使用频率和参与深度，以个性化功能推荐的顺序和步调。
- 车内通知渠道应与电子邮件和应用程序通知协调，以在与上下文最相关的时刻提供功能提示，例如，当检测到公路旅行时建议导航功能。
- [!DNL Experience Platform]配置文件应存储车辆技术配置数据，包括已安装的软件包和软件版本，以确保功能推荐与所有者的特定车辆兼容。

### 经销商网络协调

- 经销商库存信息源必须经常集成和更新，以确保向客户显示的车辆可用性能够准确反映每个经销商的状况。
- 客户到经销商分配逻辑应考虑邻近性、经销商专业化、语言偏好和任何现有的经销商关系，以提供最佳匹配。
- 潜在客户路由规则必须确保当客户在线表示购买兴趣时，查询会快速到达相应的经销商，并包含有关客户研究活动的完整上下文。
- [!DNL Experience Platform]身份解析必须处理客户与多个经销商进行交互的情况，维护统一的用户档案，同时尊重每个经销商对其自身客户关系的看法。
