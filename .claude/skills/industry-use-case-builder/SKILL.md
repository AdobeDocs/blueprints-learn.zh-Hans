---
name: industry-use-case-builder
description: 指导为Adobe Experience Platform Blueprint存储库创建新的行业用例。 当用户想要向行业垂直领域（零售、汽车、医疗保健、金融服务、保险、媒体和娱乐、电信、旅游和酒店业、B2B）添加新用例时，或者更新用例目录时，请使用此技能。 处理整个工作流：收集用例详细信息、评估成熟度级别、生成内容、更新行业概述页面和用例目录，以及调用用例图标生成器技能来创建图标。
source-git-commit: ed8928687806b619e95d8d320478d27c13722a80
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 1%

---


# 行业用例生成器

该技能可指导Adobe Experience Platform Blueprint存储库创建新的行业用例。 按顺序执行每个阶段。 在开始之前读取引用文件：

- `references/use-case-template.md` — 用例部分的确切模板
- `references/catalog-row-template.md` — 目录表行的确切格式
- `references/maturity-criteria.md` — 成熟度评估的详细规则

## 第1阶段：信息收集

在生成任何内容之前访问用户以收集所有必需的详细信息。

### 必填字段

1. **垂直行业** — 必须是以下之一：
   - 汽车
   - b2b
   - 金融服务
   - 医疗保健
   - 保险
   - 媒体 — 娱乐
   - 零售
   - 电信
   - 旅游 — 招待

2. **用例名称** — 清楚的描述性标题（例如，“放弃的购物车电子邮件恢复”、“药物遵守促销活动”）。

3. **描述** — 1-2句描述业务情景及其重要原因。

4. **业务影响** — 通过特定量度量化结果（例如，“点进率提高20-30%”，“再填充率提高15-25%”）。

5. **用例模式** — 必须映射到以下现有模式之一：
   - Audience Activation到目标
   - 具有区段匹配的受众Collaboration
   - 事件转发
   - B2B Audience Activation
   - 匿名访客Web Personalization
   - 已知访客Web/应用程序Personalization
   - Offer Decisioning
   - 行为推荐
   - 批量出站消息激活
   - 事件触发的消息传递
   - 多步协调历程
   - 使用Decisioning进行跨渠道历程
   - 购买基于群组的营销和历程管理
   - Customer Analytics和Insight生成
   - B2B分析
   - Brand Concierge对话体验

6. **技术注意事项** — 4-8个要点，涵盖数据要求、集成、法规/合规性需求、性能注意事项和体系结构说明。

在继续之前询问任何缺少的字段。 请勿假设或虚构详细信息。

## 第2阶段：成熟度评估

阅读`references/maturity-criteria.md`以了解完整评分标准。 指定以下三个到期级别之一：

- **基础** `[!BADGE Foundational]{type=Neutral}` — 单步或事件触发的模式（事件触发的消息传递、批量出站）、直接的数据要求、最小的AI/ML、标准集成。
- **新兴** `[!BADGE Emerging]{type=Informative}` — 多步骤历程、行为数据、推荐模型、已知访客个性化、中等集成复杂性。
- **高级** `[!BADGE Advanced]{type=Caution}` — 跨渠道决策、AI支持的预测、Offer Decisioning、复杂编排、多系统集成。

### 评估工作流程

1. 确定用例映射到哪个用例模式。
2. 查看成熟度标准中的“典型模式”列表以快速匹配。
3. 如果模式未明确指示成熟度，请评估数据复杂性、AI/ML要求和集成范围。
4. 通过推理向用户呈现评估：“基于模式映射({pattern})和{key factors}，我会将此分类为{level}，因为{reasoning}。”
5. 在继续生成内容之前，请等待用户确认或覆盖。

## 阶段3：内容生成

生成或更新两个文件中的内容。

### A.行业概述文件

**文件路径：** `/help/blueprints/industry-use-cases/{industry}/{industry}-overview.md`

首先阅读现有文件以了解当前结构和内容。 然后，在来自`references/use-case-template.md`的完全相同的模板后添加新部分：

```markdown
## {Use Case Title}

{1-2 sentence description of the business scenario and why it matters}

### Business impact

{Quantified business outcomes, e.g., "Retailers typically see a 20-30% increase in click-through rates..."}

### How to implement

Use the [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) pattern. {1-2 sentence explanation of why this pattern applies}

### Technical considerations

- {4-8 bullet points covering data integration, regulatory, performance, or architectural considerations}
```

将新节放在现有用例节之后，并保持一致的格式。

### B.用例目录

**文件路径：** `/help/blueprints/industry-use-cases/use-case-catalog.md`

首先读取现有目录文件。 在正确的行业选项卡中添加新行。 目录使用带`>[!TAB {Industry}]`个标记的选项卡式结构。 每个选项卡都包含一个包含以下列的表：

| 列 | 内容 |
| --- | --- |
| 图标 | `<img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40">` （如果还没有图标，则留空） |
| 用例 | `[{Use Case Title}]({industry}/{industry}-overview.md#{anchor})`，其中锚点是kebab-case中的标题 |
| 描述 | 一句摘要 |
| 成熟度 | 已分配级别的徽章语法 |
| 图案 | `[{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md)` |

**放置规则：**&#x200B;在每个行业选项卡中，行按成熟度按以下顺序分组：基础型、新兴型、高级。 将新行放置在正确的成熟度组的末尾。

模式文件路径为：
- `audience-building-activation/audience-activation-to-destinations.md`
- `audience-building-activation/audience-collaboration-segment-match.md`
- `audience-building-activation/event-forwarding.md`
- `audience-building-activation/b2b-audience-activation.md`
- `personalization/anonymous-visitor-web-personalization.md`
- `personalization/known-visitor-web-app-personalization.md`
- `personalization/offer-decisioning.md`
- `personalization/behavioral-recommendation.md`
- `campaign-management-orchestration/batch-outbound-message-activation.md`
- `campaign-management-orchestration/event-triggered-messaging.md`
- `campaign-management-orchestration/multi-step-orchestrated-journey.md`
- `campaign-management-orchestration/cross-channel-journey-with-decisioning.md`
- `campaign-management-orchestration/buying-group-based-marketing.md`
- `analysis/customer-analytics-insight-generation.md`
- `analysis/b2b-analytics.md`
- `conversational-experience/brand-concierge-conversational-experience.md`

## 阶段4：图标生成

创建内容后，调用`use-case-icon-generator`技能以生成新用例的图标规范。 通过以下方式提供技能：
- 用例名称
- 垂直行业
- 用例的简要描述

用户获得生成的图标文件后，更新目录行以包含图标引用：

```
<img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40">
```

## 阶段5：验证

完成之前，请验证以下所有内容：

1. **模板合规性** — 行业概述部分完全遵循模板（##标题、描述、###业务影响、###如何实施、###技术注意事项）。
2. **目录位置** — 目录行位于正确的行业选项卡和正确的成熟度组中（依次为“基础”、“新兴”和“高级”）。
3. **模式链接有效性** — 概述和目录中的模式链接都使用上述列表中的有效模式文件路径。
4. **锚点一致性** — 目录链接中的锚点（例如，`#abandoned-cart-email-recovery`）与转换为kebab-case的概述文件中的`##`标题匹配。
5. **图标路径约定** — 图标路径遵循`assets/use-case-icons/{industry}/icon-{kebab-name}.png`。

报告验证期间发现的任何问题，并在完成之前修复这些问题。
