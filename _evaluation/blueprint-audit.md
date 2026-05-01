---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '3505'
ht-degree: 6%

---
# Blueprint审核和建议

此审核将[评估规则](rubric.md)应用于下的每个文档
[TOC.md](../help/blueprints/TOC.md)（第76-133行）的“架构图和Blueprint”部分，以及
建议每个Blueprint是否应成为用例**模式**（架构）
**Diagram**，两者(**Split**)，或标记为现有模式的&#x200B;**重复**。

这仅是审核 — 未移动任何内容。 迁移积压（批处理A-D操作）
将在审查建议后作为一项单独的后续计划起草。

## 摘要

**已审核的文档总数：** 43

| 推荐 | 计数 | 操作 |
| --- | --- | --- |
| 图案 | 8 | 创作新的用例模式；将原始用例修剪为图表。 |
| 复制 | 9 | 现有模式涵盖了范围；将Blueprint简化为图表和交叉链接。 |
| 拆分 | 2 | 提取模式内容；将原始模式简化为图表；交叉链接两者。 |
| 图表 | 16 | 保持为架构图；如果需要，可修剪描述。 |
| 导航 | 8 | 部分登陆页面（overview.md或仅链接）；迁移登陆后重新访问。 |

### 对照组校正

所有6个`experience-platform/`文件都得了Pattern=0、Diagram=3→一致的&#x200B;**Diagram**。
校准评分标准；其他子区域的结果可以信任为已评分。

### 新用例模式类别：B2B激活和营销

新类别`use-case-patterns/b2b/` (显示标签&#x200B;**B2B激活和营销**，目录锚点
建议的`{#b2b-patterns}`)将包含所有B2B特定的模式。 标签镜像现有的
[TOC.md](../help/blueprints/TOC.md)的架构图区域中的“B2B激活和营销”子部分，
使读者看到两个部分之间的对称。

完全填充后，该类别将包含&#x200B;**7模式**：

| Origin | 操作 | 目标路径 |
| --- | --- | --- |
| `use-case-patterns/audience-building-activation/b2b-audience-activation.md` | **重新定位**&#x200B;现有模式 | `use-case-patterns/b2b/account-audience-activation.md` |
| `use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md` | **重新定位**&#x200B;现有模式 | `use-case-patterns/b2b/buying-group-marketing.md` |
| `use-case-patterns/analysis/b2b-analytics.md` | **重新定位**&#x200B;现有模式 | `use-case-patterns/b2b/account-analytics.md` |
| `b2b/b2b-journeys-with-marketo.md` | **创作新** （审核模式行） | `use-case-patterns/b2b/marketo-data-journeys.md` |
| `b2b/ajo-b2b-paid-media-controller.md` | **创作新** （审核模式行） | `use-case-patterns/b2b/paid-media-orchestration.md` |
| `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | **新作者** | `use-case-patterns/b2b/campaign-intake-and-creation.md` |
| `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | **新作者** | `use-case-patterns/b2b/campaign-review-and-approval.md` |

> **初始过渡状态 — 编写器协调门。** 现有的“B2B激活和营销”> [TOC.md](../help/blueprints/TOC.md) （第95-106行） **的体系结构图区域中的子部分保持不变> 在过渡期间**。 每个Blueprint转换和现有模式重新定位都需要> 在迁移内容之前从所属编写器注销。 新的`b2b/`用例模式> 区域与现有Blueprint区域共存，而迁移逐页进行，使用> 它们之间的交叉链接。

当重新定位和新模式都着陆时：

- [TOC.md](../help/blueprints/TOC.md) `Use Case Patterns`部分将获得 `B2B Activation & Marketing{#b2b-patterns}`
subsection（置入待定，供作者使用）。
- [use-case-patterns/overview.md](../help/blueprints/use-case-patterns/overview.md)将获得B2B类别表。
- 将从`audience-building-activation`中删除重新定位的模式，
  `campaign-management-orchestration`和`analysis`概述表；保留其旧URL
在[migration-redirects.csv](migration-redirects.csv)中通过重定向处于活动状态。

### 已识别的重复项(9)

Blueprint范围已由现有用例模式涵盖。 迁移操作为
**简化为架构图+交叉链接**。

| Blueprint | 现有模式 |
| --- | --- |
| `audience-activation/advertising-activation.md` | `use-case-patterns/audience-building-activation/audience-activation-to-destinations.md` |
| `audience-activation/segment-match.md` | `use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md` |
| `b2b/b2bactivation.md` | `use-case-patterns/audience-building-activation/b2b-audience-activation.md` |
| `b2b/b2b-buying-group-journeys.md` | `use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md` |
| `customer-journey-analytics/b2b-cja.md` | `use-case-patterns/analysis/b2b-analytics.md` |
| `customer-journeys/journey-optimizer/journey-optimizer-journeys.md` | `use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md` |
| `customer-journeys/journey-optimizer/journey-optimizer-campaigns.md` | `use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md` |
| `customer-journeys/decision-management/decision-management-edge.md` | `use-case-patterns/personalization/offer-decisioning.md` |
| `customer-journeys/decision-management/decision-management-hub.md` | `use-case-patterns/personalization/offer-decisioning.md` |

> 注意： `decision-management-edge.md`和`decision-management-hub.md`都映射到同一个> 现有`offer-decisioning.md`模式。 考虑将两个Blueprint整合到一个> 部署 — 选项图，或通过edge-vs-hub部署来扩充现有模式> 变体。 标记写入程序审核。

### 要编写的模式（8个新的+ 2个来自拆分=共10个）

| Source Blueprint | 建议的类别 | 建议的模式标题 |
| --- | --- | --- |
| `audience-activation/customer-activity.md` | audience-building-activation | 支持和销售人员的实时配置文件查找 |
| `audience-activation/data-science.md` | audience-building-activation | 用于扩充用户档案的数据科学模型摄取 |
| `audience-activation/real-time-lookup.md` | 个性化 | 用于Web/移动Personalization的Edge配置文件访问 |
| `b2b/b2b-journeys-with-marketo.md` | **b2b** （新） | 使用Marketo数据集成的B2B帐户历程 |
| `b2b/ajo-b2b-paid-media-controller.md` | **b2b** （新） | 通过Waterfall拆分路径逻辑进行B2B付费媒体编排 |
| `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | **b2b** （新） | Campaign请求接收和自动程序创建 |
| `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | **b2b** （新） | Campaign资产审查和批准工作流 |
| `customer-journeys/campaign-v8/campaign-v8-overview.md` | campaign-management-orchestration | Campaign v8批量编排和事务性消息传递 |
| `audience-activation/rtcdp-target.md` *（拆分）* | 个性化 | 使用Adobe Target实时共享受众 |
| `customer-journeys/journey-optimizer/3rd-party-messaging.md` *（拆分）* | campaign-management-orchestration | 第三方消息传递与Journey Optimizer的集成 |

### 提议的新模式类别

- **`b2b/`** （显示标签&#x200B;**B2B激活和营销**） — 请参阅上面的专用部分。 此
Marketo + Workfront模式(`intake-and-create`， `review-and-approve-blueprint`)已路由
此处而不是单独的`marketing-resource-management`类别，因为它们代表
B2B营销操作的实际应用。 新类别共汇总7个模式：3个已重新定位
以及从Blueprint新创作的4个报表包。

### 迁移重定向

此迁移引入的每个URL更改都会在canonical中添加一行
存储库根目录中的[`redirects.csv`](../redirects.csv)（格式： `source,dest`）。 已确认
重定向存放在[migration-redirects.csv](migration-redirects.csv)中，并合并到
标准文件，因为每个相应的移动实际上都会发生。

**已确认（3个条目，已暂存）：**&#x200B;将现有模式重新定位到`b2b/`。 请参阅
[migration-redirects.csv](migration-redirects.csv)。

**待处理 — 当Blueprint为&#x200B;*已删除*时添加（在缩减为就地关系图时添加）：**，如果
以后将完全删除模式、拆分或重复行的Blueprint，请从添加重定向
指向规范模式URL的Blueprint URL。 默认迁移方法（简化图表）
使Blueprint URL保持活动状态，**不需要**这些重定向。 下面列出了
如果任何Blueprint完全停用，则表示完整性：

```
# Pattern blueprints — if deleted, redirect to the new pattern URL
# (slugs are placeholders; finalize when each pattern is authored)
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/customer-activity → use-case-patterns/audience-building-activation/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/data-science → use-case-patterns/audience-building-activation/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/real-time-lookup → use-case-patterns/personalization-patterns/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2b-journeys-with-marketo → use-case-patterns/b2b-patterns/marketo-data-journeys
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/ajo-b2b-paid-media-controller → use-case-patterns/b2b-patterns/paid-media-orchestration
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/marketo-engage-and-workfront-integration-blueprint/intake-and-create → use-case-patterns/b2b-patterns/campaign-intake-and-creation
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint → use-case-patterns/b2b-patterns/campaign-review-and-approval
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/campaign-v8/campaign-v8-overview → use-case-patterns/campaign-orchestration-patterns/<new-pattern-slug>

# Duplicate blueprints — if deleted, redirect to the existing pattern URL
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/advertising-activation → use-case-patterns/audience-building-activation/audience-activation-to-destinations
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/segment-match → use-case-patterns/audience-building-activation/audience-collaboration-segment-match
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2bactivation → use-case-patterns/b2b-patterns/account-audience-activation  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2b-buying-group-journeys → use-case-patterns/b2b-patterns/buying-group-marketing  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journey-analytics/b2b-cja → use-case-patterns/b2b-patterns/account-analytics  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/journey-optimizer/journey-optimizer-journeys → use-case-patterns/campaign-orchestration-patterns/event-triggered-messaging
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/journey-optimizer/journey-optimizer-campaigns → use-case-patterns/campaign-orchestration-patterns/batch-outbound-message-activation
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/decision-management/decision-management-edge → use-case-patterns/personalization-patterns/offer-decisioning
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/decision-management/decision-management-hub → use-case-patterns/personalization-patterns/offer-decisioning

# Optional one-off — if customer-journey-analytics/analysis.md is relocated to experience-platform/
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journey-analytics/analysis → architecture-diagrams/architecture-overview/analysis
```

将以上任何内容转换为活动重定向行时，请设置逗号分隔格式 `source,dest`
具有完整`/en/docs/...`路径（无`.html`后缀），与中的现有模式匹配
[`redirects.csv`](../redirects.csv).

### 重定向创建策略（持久性规则）

对于每个迁移步骤，请遵循以下规则：

1. **已移动或重命名文件**，→添加从旧URL到新URL的重定向。
2. **已删除文件**（蓝图已替换；未保留图表）→将重定向从已删除的URL添加至
规范替换URL。
3. **就地简化的文件** （URL未更改）→无重定向。
4. 已重命名&#x200B;**TOC锚点**（例如，章节标题更改），→为下面的每个页面添加重定向
那个锚点，因为URL发生了变化。

### 为作者提出问题

1. **决策管理边缘与中心** — 两者均映射到同一现有 `offer-decisioning.md`
模式。 使用部署变体合并到单个关系图中，或将其视为单独的
两个图都交叉链接到同一模式？
2. **Journey Optimizer历程与事件触发的消息传递** — 代理标记了此重复项
分类不确定。 在减少Blueprint之前验证范围一致性。
3. **`customer-journey-analytics/analysis.md`** — 内容实际上与Experience Platform有关
查询服务，而不是CJA。 考虑重新定位到`experience-platform/`文件夹。 (一个重定向
将被添加 — 请参阅[migration-redirects.csv](migration-redirects.csv)。)
4. **Campaign v7（已弃用）** — 三个已弃用的v7文件被分类为图表/
导航。 确认是完全迁移、保持原样还是从目录中完全删除。
5. **`customer-success-stories.md`** — 仅链接引用页面（不是`overview.md`）。
分类为导航。 确认或重新分类。
6. **B2B节TOC锚点** — 建议的`{#b2b-patterns}`。 其他模式子部分使用
   `-patterns`后缀(`{#personalization-patterns}`， `{#analysis-patterns}`，
   `{#campaign-orchestration-patterns}`). 在创作重定向之前确认或选取另一个锚点。
7. 在目录&#x200B;**中放置** B2B节 — 建议位于`+ Use Case Patterns{#use-case-patterns}`下。
兄弟姐妹之间的顺序(Audience Building &amp; Activation、Personalization、Campaign Management)
和编排、分析、B2B激活和营销、对话体验)是
写字人的电话。
8. **拥有者协调** — 每个Blueprint转换和现有模式重定位
内容移动前需要编写器注销。 审计表是目标状态，而不是
排序计划；在协调后的后续迁移计划中执行排序。

## 审核表

| 路径 | 标题 | 摘要 | 占优类型 | 推荐 | proposed_pattern_category | proposed_pattern_title | proposed_diagram_title | 重复_of | pattern_score | diagram_score | 注释 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| help/blueprints/experience-platform/experience-cloud.md | Adobe Experience Cloud 架构图 | 企业架构，用于显示Experience Cloud应用程序和服务如何在AEP基础上集成。 | 图表 | 图表 |  |  | Experience Cloud架构概述 |  | 0 | 3 | 覆盖3（无业务目标）。 三个互补图（市场结构、集成、企业环境）。 对照组：如预期。 |
| help/blueprints/experience-platform/platform-applications.md | Adobe Experience Platform和应用程序架构图 | 显示Experience Platform与其他Experience Cloud应用程序的关联的架构图。 | 图表 | 图表 |  |  | AEP与应用程序架构 |  | 0 | 3 | 覆盖3. 两个概述/详细图表；无实施指南。 集成学习文档的交叉链接。 对照组：如预期。 |
| help/blueprints/experience-platform/platform-data-flow.md | Adobe Experience Platform 数据流架构图 | 数据流架构图显示了Experience Platform的传入和传出路径。 | 图表 | 图表 |  |  | AEP数据流架构 |  | 0 | 3 | 覆盖3. 引用数据收集文档的单个数据流图。 纯建筑工件。 对照组：如预期。 |
| help/blueprints/experience-platform/guardrails.md | Experience Platform 和应用程序护栏 | AEP和应用程序的系统限制、性能期望和延迟防护。 | 图表 | 图表 |  |  | AEP和应用程序护栏和延迟 |  | 0 | 3 | 覆盖3. 延时图和参考表。 面向架构师（边缘与中心）。 约束文档，而不是操作方法。 对照组：如预期。 |
| help/blueprints/experience-platform/deployment/websdk.md | Experience Platform Web SDK和Edge Network架构图 | 显示数据收集流程的Web SDK和Edge Network部署架构。 | 图表 | 图表 |  |  | Web SDK和Edge Network部署 |  | 0 | 3 | 覆盖3. 两个图表（流程和顺序）。 引用教程，但没有文档中的操作方法。 以建筑师为中心。 对照组：如预期。 |
| help/blueprints/experience-platform/deployment/appsdk.md | 特定于应用程序的 SDK 部署架构图 | 特定于应用程序的SDK集成路径和数据收集架构图。 | 图表 | 图表 |  |  | 特定于应用程序的SDK部署 |  | 0 | 3 | 覆盖3. 具有最少叙述的单个部署图。 纯建筑工件。 对照组：如预期。 |
| help/blueprints/audience-activation/advertising-activation.md | Audience Activation到Social和Advertising目标 | 通过具有身份配置和目标设置的RTCDP，在Facebook和Google广告网络中激活受众。 | 图案 | 复制 |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md | 4 | 1 | 现有模式涵盖此范围。 重复覆盖。 操作：简化为纯图表和交叉链接。 |
| help/blueprints/audience-activation/audience-manager.md | Device Based — 使用Audience Manager进行匿名受众定位 | 使用Audience Manager或RTCDP进行匿名受众激活，以便跨渠道进行基于设备的定位。 | 图表 | 图表 |  |  | 匿名基于设备的受众定位 |  | 1 | 2 | 极少的叙事。 给出了架构图、系统拓扑图。 无业务目标框架；部署SDK和中心/边缘概念。 |
| help/blueprints/audience-activation/customer-activity.md | 支持和销售方案的实时配置文件访问 | 通过用户档案查找API启用支持和销售代理实时客户上下文。 | 图案 | 图案 | audience-building-activation | 支持和销售人员的实时配置文件查找 |  |  | 3 | 1 | 框架业务结果（代理上下文）。 具有先决条件核对清单；实施步骤>30行。 独特用例：中心配置文件访问（不是边缘个性化）。 与现有个性化模式不同。 |
| help/blueprints/audience-activation/data-science.md | 用户档案扩充的自定义数据科学 Blueprint | 将机器学习模型得分摄取到RTCDP以丰富用户档案以进行个性化和分段。 | 图案 | 图案 | audience-building-activation | 用于扩充用户档案的数据科学模型摄取 |  |  | 3 | 1 | 框架业务成果（扩充以进行个性化）。 具有用例和注意事项；实施注意事项>30行。 关注数据科学工作流，而非消息传送/激活。 |
| help/blueprints/audience-activation/enterprise-destinations.md | 受众和用户档案激活到企业目的地 | 将配置文件和受众更改流式或批量传输到面向销售、支持和分析的云存储和企业应用程序。 | 图表 | 图表 |  |  | Enterprise Audience and Profile Activation |  | 1 | 2 | 没有业务目标框架。 稀疏实现指南。 云存储/企业应用程序的架构图+系统拓扑。 视觉主导。 |
| help/blueprints/audience-activation/real-time-lookup.md | 适用于Web和移动Personalization的实时Edge配置文件访问 | 访问边缘位置的统一配置文件（以毫秒为单位），以实现实时Web和移动个性化。 | 图案 | 图案 | 个性化 | 用于Web/移动Personalization的Edge配置文件访问 |  |  | 5 | 2 | 强大的业务框架（低延迟个性化）。 两种实施模式（Web SDK与Edge API）。 广泛的先决条件和步骤（超过30行）。 隐含的KPI（延迟、吞吐量）。 |
| help/blueprints/audience-activation/rtcdp-target.md | 已知客户Personalization与Target | 与Adobe Target共享RTCDP受众和配置文件，以实现已知访客Web和移动个性化。 | 混合 | 拆分 | 个性化 | 使用Adobe Target实时共享受众 | Target集成架构 | help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md | 3 | 2 | 与现有已知访客模式重叠，但范围较小（仅限Target）。 三种集成模式。 考虑体系结构图+边缘部署。 模式内容+图表实质上→是拆分。 |
| help/blueprints/audience-activation/segment-match.md | 具有区段匹配的受众Collaboration | 通过带有隐私控制的区段匹配实现安全的合作伙伴受众协作。 | 图案 | 复制 |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md | 4 | 1 | 现有模式完全涵盖了这一点。 重复覆盖。 要在图表中保留的独特内容：详细的RBAC/同意/治理配置和程序化广告工作流。 |
| help/blueprints/b2b/overview.md | B2B Analytics、激活和营销Blueprint | 导航页面列出了B2B分析、受众激活、购买群组、Marketo和Workfront Blueprint。 | 导航 | 导航 |  |  |  |  |  |  | 覆盖1：名为overview.md的文件。 已从迁移中排除。 |
| help/blueprints/b2b/b2bactivation.md | B2B 受众和用户档案激活 Blueprint | 使用帐户和配置文件数据跨Web、电子邮件和广告渠道激活基于帐户的B2B受众。 | 图案 | 复制 |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md | 3 | 1 | 覆盖2：存在对等模式。 Blueprint是更窄的以架构为中心的子集。 |
| help/blueprints/b2b/b2b-account-activation.md | B2B帐户激活到Advertising目标和文件目标 | 通过LinkedIn以及使用帐户受众创建和激活的云存储目标定位B2B帐户。 | 图表 | 图表 |  |  | B2B帐户Audience Activation |  | 1 | 2 | 最少的商业框架，无KPI，最少的叙述。 给出了架构图；描述了LinkedIn/云存储拓扑。 以图形式保留。 |
| help/blueprints/b2b/b2b-buying-group-journeys.md | 购买基于群组的营销和历程管理Blueprint | 设计客户历程，使潜在客户有资格购买具有定义角色和解决方案兴趣的群组。 | 图案 | 复制 |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md | 5 | 2 | 覆盖2：存在对等模式。 Blueprint具有丰富的模式内容，而现有的模式更加全面。 |
| help/blueprints/b2b/b2b-journeys-with-marketo.md | 使用Marketo Data Blueprint的B2B历程 | 使用Journey Optimizer B2B edition数据部署Marketo，以编排购买团体历程和客户参与。 | 图案 | 图案 | b2b | 使用Marketo数据集成的B2B帐户历程 |  |  | 4 | 1 | 强大的业务框架。 列出了KPI；多个实施选项；广泛的注意事项（30行以上）。 通过Marketo数据集成深度（XDM配置、身份拼接、字段阻止）与现有模式区分开来。 路由到新的b2b/类别。 |
| help/blueprints/b2b/ajo-b2b-paid-media-controller.md | AJO B2B — 帐户Journey Orchestration — 付费媒体控制者 | 使用瀑布式逻辑编排B2B付费媒体营销活动，将帐户分配给营销活动并激活到目标。 | 图案 | 图案 | b2b | 通过Waterfall拆分路径逻辑进行B2B付费媒体编排 |  |  | 4 | 2 | 强大的业务框架。 明确KPI；多个实施选项；先决条件；超过30行的叙述。 不同于现有的购买群体模式（侧重于付费媒体优先化，而不是培养）。 路由到新的b2b/类别。 |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md | Marketo Engage 和 Workfront 集成 Blueprint 概述 | 使用Marketo Engage和Workfront与Fusion实现活动计划到执行自动化的概述。 | 导航 | 导航 |  |  |  |  |  |  | 覆盖1：名为overview.md的文件。 已从迁移中排除。 |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md | 接收和创建 Blueprint | 使用Workfront表单和Marketo Engage项目模板自动创建B2B营销活动请求摄取。 | 图案 | 图案 | b2b | Campaign请求接收和自动程序创建 |  |  | 4 | 1 | 强大的业务框架提高了营销活动速度。 隐式KPI（减少错误/返工）；工作流步骤>30行；准备清单。 通往新b2b/类别的路由（Marketo+Workfront运营运营主要包括B2B）。 |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md | 审查和批准 Blueprint | 使用Fusion自动化将Workfront验证和审批工作流与Marketo Engage电子邮件资源集成。 | 图案 | 图案 | b2b | Campaign资产审查和批准工作流 |  |  | 3 | 2 | 强大的合规性和准确性业务框架；隐式KPI（审批速度）；叙述>30行；工作流计划部分。 路由到新的b2b/类别。 |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md | 客户成功案例 | 指向展示Marketo与Workfront集成结果的客户案例研究和网络研讨会的链接。 | 导航 | 导航 |  |  |  |  |  |  | 最小内容（6个超链接）。 无业务框架、KPI、架构或叙述。 被视为导航。 作者应确认。 |
| help/blueprints/customer-journey-analytics/overview.md | Customer Journey Analytics Blueprint | 统一和分析来自各种渠道的客户数据和行为，以创建基于历程的视图。 | 导航 | 导航 |  |  |  |  |  |  | 覆盖1： overview.md。 目录样式登陆页面。 已从迁移中排除。 |
| help/blueprints/customer-journey-analytics/b2b-cja.md | B2B Customer Journey Analytics Blueprint | 针对使用帐户作为主数据模型的B2B组织，提供基于帐户的CJA报表和分析。 | 图案 | 复制 |  |  |  | help/blueprints/use-case-patterns/analysis/b2b-analytics.md | 4 | 2 | 覆盖2：等效模式涵盖使用CJA B2B edition的B2B帐户级别分析。 操作：简化为图表、交叉链接。 |
| help/blueprints/customer-journey-analytics/cja-rtcdp.md | 带有Real-time Customer Data Platform Blueprint的Customer Journey Analytics | 创建受众并将其从CJA发布到RTCDP以进行定位和个性化。 | 图表 | 图表 |  |  | CJA到RTCDP受众发布集成 |  | 1 | 3 | 强大的架构重点（系统到系统集成、部署形状）。 极少的叙事。 独特内容： CJA受众发布延迟护栏。 |
| help/blueprints/customer-journey-analytics/cja-ajo.md | Customer Journey Analytics和Journey Optimizer Blueprint | 在CJA中分析AJO交付和交互数据；将CJA受众发布到AJO。 | 图表 | 图表 |  |  | CJA与AJO的集成和分析 |  | 1 | 3 | 强大的架构重点。 极少的叙事。 唯一内容：双向CJA-AJO数据共享模式。 |
| help/blueprints/customer-journey-analytics/analysis.md | 数据分析和智能 Blueprint | 使用Experience Platform查询服务对数据湖数据进行探索性分析。 | 图表 | 图表 |  |  | Experience Platform查询服务与BI工具集成 |  | 1 | 3 | 涵盖查询服务，而不是特定于CJA。 可能放错在CJA文件夹中；请考虑重新定位到experience-platform/。 强大的架构师受众（PostgreSQL、BI工具）。 |
| help/blueprints/customer-journeys/overview.md | 客户历程 Blueprint | 现代营销平台支持事件驱动的历程和品牌发起的跨渠道营销活动。 | 导航 | 导航 |  |  |  |  |  |  | 覆盖1： overview.md。 历程子类别的目录；介绍Journey Optimizer和Campaign定位。 |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md | Journey Optimizer Blueprint | 跨渠道的事件驱动的1:1配置文件编排和基于受众的品牌通信。 | 导航 | 导航 |  |  |  |  |  |  | 覆盖1： overview.md。 登陆页面，其中包含用例选项卡和集成模式。 |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md | Journey Optimizer — 触发的消息处理和Adobe Experience Platform Blueprint | 实时事件驱动型工作流根据客户行为提供个性化的多步体验。 | 图案 | 复制 |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md | 4 | 2 | 覆盖2但有注意事项：代理标记为可能重复但不确定。 先验证范围是否一致，然后再缩小。 架构考虑因素可能独一无二（配置文件新鲜度、区段资格计时），值得在图中保留。 |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md | Journey Optimizer - Campaign编排 | 跨出站渠道（电子邮件、短信、推送、直邮）计划基于受众的多步通信。 | 图案 | 复制 |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md | 3 | 2 | 覆盖2：等效模式。 多个体系结构图；保留为图。 独特内容：关系数据库/受众门户/瘦配置文件架构详细信息。 |
| help/blueprints/customer-journeys/journey-optimizer/3rd-party-messaging.md | Journey Optimizer - 第三方消息传递 blueprint | 演示Journey Optimizer与第三方消息传递系统的集成，以实现编排式通信。 | 混合 | 拆分 | campaign-management-orchestration | 第三方消息传递与Journey Optimizer的集成 | 第三方报文传送架构 |  | 2 | 2 | 平分→打分。 图（系统到系统拓扑）加上模式内容（实施步骤、集成约束：承载身份验证、无静态IP、速率限制）。 值得保留两者。 |
| help/blueprints/customer-journeys/decision-management/decision-management-overview.md | 决策管理 Blueprint | 通过集中式优惠库和决策引擎，在客户历程中提供个性化优惠。 | 导航 | 导航 |  |  |  |  |  |  | 覆盖1： overview.md。 介绍决策管理组件以及边缘与中心部署方法。 |
| help/blueprints/customer-journeys/decision-management/decision-management-edge.md | 边缘决策管理 Blueprint | 在边缘网络上以次秒的延迟提供实时Web和移动体验的个性化优惠。 | 混合 | 复制 |  |  |  | help/blueprints/use-case-patterns/personalization/offer-decisioning.md | 2 | 3 | 覆盖2：映射到offer-decisioning。 Edge部署变量 — 考虑将与hub blueprint整合为单个部署 — 选项图。 |
| help/blueprints/customer-journeys/decision-management/decision-management-hub.md | 中心决策管理 Blueprint | 跨渠道提供个性化优惠，包括信息亭、代理辅助体验和出站投放。 | 混合 | 复制 |  |  |  | help/blueprints/use-case-patterns/personalization/offer-decisioning.md | 2 | 3 | 覆盖2：映射到offer-decisioning。 中心部署变量 — 考虑将与Edge Blueprint整合到一个部署 — 选项图中。 |
| help/blueprints/customer-journeys/campaign-v8/campaign-v8-overview.md | Campaign v8 Blueprint、Campaign和平台 | 新一代批处理营销活动管理平台，具有ETL、分段和事务性消息传递功能。 | 图案 | 图案 | campaign-management-orchestration | Campaign v8批量编排和事务性消息传递 | Campaign v8架构部署模型 |  | 4 | 3 | 独特的技术方法（Campaign v8原生，而不是AJO）。 多体系结构图；业务框架；护栏中隐含的KPI（20M msg/hr批量，1M/hr实时）。 现有模式目录中无等效项。 注意：得分也符合拆分的条件 — 建议使用模式，但作者可能希望保留图表。 |
| help/blueprints/customer-journeys/campaign-v8/rtcdp-and-campaign-v8.md | Real-Time CDP 与 Adobe Campaign v8 集成模式 | 展示RTCDP受众和配置文件与Campaign v8的集成，以进行个性化对话。 | 图表 | 图表 |  |  | RTCDP - Campaign v8受众和配置文件交换 |  | 1 | 2 | 集成连接器Blueprint，而不是独立的用例。 图表+简短的先决条件/护栏。 面向架构师。 |
| help/blueprints/customer-journeys/campaign-v8/ajo-and-campaign-v8.md | Journey Optimizer 与 Adobe Campaign v8 Blueprint | 演示了使用Campaign v8事务性消息传送AJO编排，以实现1:1个体验。 | 图表 | 图表 |  |  | Journey Optimizer - Campaign v8事务性消息传递集成 |  | 1 | 2 | 集成连接器。 图表+实施步骤+技术限制（4,000毫秒/5分钟调节，仅限事件启动）。 AJO和Campaign v8模式的交叉链接。 |
| help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md | Campaign v7 Blueprint | 已弃用：基于批次的消息传递、入门、再营销、直邮、简单事务型消息传递。 | 导航 | 导航 |  |  |  |  |  |  | 已弃用的产品（frontmatter链接到v8）。 最小内容（仅限体系结构图）。 请勿迁移。 |
| help/blueprints/customer-journeys/campaign-v7/rtcdp-and-campaign-v7.md | Real-Time CDP与Campaign v7和Campaign Standard集成模式 | 展示RTCDP和Real-Time Customer Profile与Campaign v7/Standard的集成，以进行个性化对话。 | 图表 | 图表 |  |  | RTCDP - Campaign v7/Standard受众和配置文件交换 |  | 1 | 2 | 已弃用。 集成连接器。 图表+全面的实施步骤。 不要迁移到新模式；请保持原样。 |
| help/blueprints/customer-journeys/campaign-v7/ajo-and-campaign-v7.md | Journey Optimizer 与 Adobe Campaign v7 Blueprint | 演示了使用Campaign v7事务性消息传送AJO编排，以实现1:1个体验。 | 图表 | 图表 |  |  | Journey Optimizer - Campaign v7事务性消息传递集成 |  | 1 | 2 | 已弃用。 集成连接器。 图表+实施步骤+约束。 请勿迁移；请保持原样。 |
