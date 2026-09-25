---
source-git-commit: 2ed15399073fce5ebd1c2ba07b1cf70ec706452c
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 2%
---
# 迁移状态a€&grave; Blueprint到用例模式

本文档捕获了Blueprint重组工作的状态，以便可以跨会话干净地恢复。

**上次更新时间：** 2026-09-24

## 我们目前的处境

B2B部分不再暂停。 其发布的架构范围现在仅限于受众/个人资料和帐户激活页面，已停用的页面将被重定向到类别概述。

**当前状态：** B2B架构清理已完成。 受众/配置文件和帐户激活页面仍保留在architecture-diagrams类别中；其他B2B architecture页面已停用，并已重定向到类别概述。

## 工作方式

> 以下工作方法是历史性的；B2B部分此后已被移位，如上所述。

本届会议商定的目前工作模式是：

1. **使Blueprint保持活动状态** a€”无弃用。 每个Blueprint都将作为以架构为中心的页面保留在适当位置。
2. **将交叉链接提示**&#x200B;添加到具有相关/重叠用例模式的每个Blueprint，紧接H1之后：

   ```
   >[!TIP]
   >This blueprint is also available as a [use case pattern](<absolute path>) under <Category>.
   ```

3. 如果Blueprint具有相关模式缺少的架构图，请将`## Architecture`部分添加到通过绝对路径引用同一SVG的模式中。 **&#x200B;**&#x200B;资产将保留在其原始位置（无文件副本）。
4. 从Blueprint中修剪模式所涵盖的&#x200B;**实施步骤**。 要删除的分区通常包括： `## Implementation steps`、`## Implementation patterns`、`## Implementation considerations`，有时包括`## Prerequisites`。 根据每个Blueprint使用判断。
5. **逐一进行** a €建议每个Blueprint的更改，获得用户批准，然后申请。

### 通用规则

- 交叉链接提示措辞一致： `>This blueprint is also available as a [use case pattern](...) under <Category>.`
- 新文件（迁移期间创建的用例模式）**不包含`exl-id`** a€“Adobe发布分配这些文件。
- 新创作文件中的图像引用使用绝对路径(`/help/blueprints/...`)，而不是相对路径。
- 保留现有页面上的现有`exl-id`值。
- `redirects.csv`中的重定向遵循`source,dest`格式，包含`/en/docs/...`个路径（无`.html`）。

## 阶段Aa€“E”（初始结构工作） A€“完成

| 阶段 | 结果 |
| --- | --- |
| A | 已创建`B2B Activation & Marketing`用例模式类别。 已重新定位3个现有模式(`b2b-audience-activation` a†“`b2b/account-audience-activation`，`buying-group-based-marketing` a†“`b2b/buying-group-marketing`，`b2b-analytics` a†“`b2b/account-analytics`”)。 添加了3个重定向。 |
| B | 已将4个B2B Blueprint复制到`use-case-patterns/b2b/` (`marketo-data-journeys`、`paid-media-orchestration`、`campaign-intake-and-creation`、`campaign-review-and-approval`)。 |
| C | 已复制4个非B2B Blueprint (`real-time-profile-lookup`、`data-science-profile-enrichment`、`edge-profile-access`、`campaign-v8-orchestration`)。 |
| D | 已复制2个拆分Blueprint (`audience-sharing-with-target`， `third-party-messaging`)。 |
| E | 向9个重复分类的Blueprint添加了交叉链接提示。 |

Aa€&quot;E之后的用例模式总数：6个类别中的&#x200B;**26个模式**。

## 逐节演练（进行中）

本节演练将交叉链接/关系图迁移/impl-trim方法单独应用于用户审阅的每个Blueprint。

### aoe... Audience &amp; Profile Activation a€&quot; 8/8完成

| # | Blueprint | 已采取的操作 |
| --- | --- | --- |
| 1 | `audience-manager.md` | 交叉链接提示+图表已迁移到模式(`anonymous-visitor-web-personalization`) +删除了RTCDP实施步骤 |
| 2 | `enterprise-destinations.md` | 交叉链接提示+图表已迁移到模式(`audience-activation-to-destinations`) |
| 3 | `advertising-activation.md` | 删除了Impl步骤（99 a†&#39; 35行） |
| 4 | `customer-activity.md` | 已移除实施步骤（51 a†&#39; 40行） |
| 5 | `data-science.md` | 删除了Impl注意事项（46 a†&#39; 40行） |
| 6 | `real-time-lookup.md` | 已删除先决条件+实施模式/步骤/注意事项（156 a†&#39; 73行） |
| 7 | `segment-match.md` | **无更改** （用户选择保持原样） |
| 8 | `rtcdp-target.md` | 删除了实施模式+注意事项（99 a†&#39; 74行） |

### oÿ ¡B2B激活和营销a€” 1/10正在进行中

| # | Blueprint | 状态 |
| --- | --- | --- |
| 1 | `b2b/overview.md` | 已完成 — B2B类别概述已更新 |
| 2 | `b2b/b2bactivation.md` | 已停用 — 替换为架构图受众/配置文件页面 |
| 3 | `b2b/b2b-account-activation.md` | 保留 — 迁移到体系结构图B2B类别 |
| 4 | `b2b/b2b-buying-group-journeys.md` | 已弃用 |
| 5 | `b2b/b2b-journeys-with-marketo.md` | 已弃用 |
| 6 | `b2b/ajo-b2b-paid-media-controller.md` | 已弃用 |
| 7 | `b2b/marketo-engage-and-workfront-integration-blueprint/overview.md` | 已弃用 |
| 8 | `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | 已弃用 |
| 9 | `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | 已弃用 |
| 10 | `b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md` | 已弃用 |

### asCustomer Journey Analytics a €&quot; 0/5尚未开始

文件： `overview.md`、`b2b-cja.md`（阶段E重复，已添加交叉链接）、`cja-rtcdp.md`（组2 a ！建议交叉链接到`customer-analytics-insight-generation`）、`cja-ajo.md`（组2 a ！相同）、`analysis.md`（组3，可能重定位到experience-platform/）。

### 当ª客户历程报废清理完成时；保留页面迁移待定

文件： `overview.md`；`journey-optimizer/` （4个文件：概述，历程[阶段E]，营销活动[阶段E]，第三方消息传送[阶段D]）；`campaign-v8/` （3个文件：概述[阶段C]，rtcdp-and-v8，ajo-and-v8）。 `decision-management/`和`campaign-v7/`已完全停用；其历史条目保留在审核中，其URL重定向到批准的概述页面。

### asExperience Platform a €&quot; 0/6尚未开始

文件： `experience-cloud.md`、`platform-applications.md`、`platform-data-flow.md`、`guardrails.md`、`deployment/websdk.md`、`deployment/appsdk.md`。 在审核中，所有得分均为仅图表，且带有0个模式信号。 **可能所有“无变化”** a €它们是不与用例模式重叠的基础架构。

决策管理和Campaign v7报废决策已完成。 他们的相关未完成问题
仅供历史参考，不应妨碍其余的迁移工作。

## 引用文件

| 文件 | 用途 |
| --- | --- |
| [blueprint-audit.md](blueprint-audit.md) | 每个Blueprint的审核表（43行）带有建议 |
| [rubric.md](rubric.md) | 用于对Blueprint进行分类的评分规则 |
| [migration-redirects.csv](migration-redirects.csv) | 从迁移分步重定向 |
| [重定向.csv](../redirects.csv) | 规范重定向文件（在阶段A中添加了3行） |

## 仍未解决的问题（来自审核）

&#x200B;2. **`journey-optimizer-journeys.md`** a €标记为不确定的`event-triggered-messaging`重复项；在裁切之前验证范围。
&#x200B;3. “**`customer-journey-analytics/analysis.md`** a€”内容与Experience Platform查询服务有关，与CJA无关；请考虑重新定位到`experience-platform/`。
&#x200B;4. **`customer-success-stories.md`** a€”仅链接页面；确认导航分类。
&#x200B;5. 历史TOC — 锚点问题被已完成的B2B体系结构配置所取代。

## 如何恢复

在此存储库中打开新的Claude代码会话，并说：

> 让我们继续进行Blueprint迁移。 阅读`_evaluation/migration-status.md`以了解我们中断的时间。

B2B架构清理已完成。 验证后，继续下一个计划的体系结构类别。
