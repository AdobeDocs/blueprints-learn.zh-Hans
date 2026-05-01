---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 2%

---
# 迁移状态 — 使用用例模式的Blueprint

本文档捕获了Blueprint重组工作的状态，以便可以跨会话干净地恢复。

**上次更新时间：** 2026-04-29

## 我们目前的处境

**当前暂停于：** `b2b/overview.md` （B2B部分Blueprint#1为10） — 正在等待决定是否保持原样，添加对新B2B激活和营销模式部分的交叉引用，或更新表以列出所有Blueprint +添加交叉引用。

**要继续：**&#x200B;使用&#x200B;**A**（建议保持原样）、**B**（添加交叉引用）或&#x200B;**C**（更新表+添加交叉引用）进行响应。 然后继续使用Blueprint#2(`b2b/b2bactivation.md`)。

## 工作方式

本届会议商定的目前工作模式是：

1. **使Blueprint保持活动状态** — 无弃用。 每个Blueprint都将作为以架构为中心的页面保留在适当位置。
2. **将交叉链接提示**&#x200B;添加到具有相关/重叠用例模式的每个Blueprint，紧接H1之后：

   ```
   >[!TIP]
   >This blueprint is also available as a [use case pattern](<absolute path>) under <Category>.
   ```

3. **迁移图** — 如果Blueprint具有相关模式缺少的架构图，请通过绝对路径将`## Architecture`部分添加到引用同一SVG的模式中。 资产将保留在其原始位置（无文件副本）。
4. 从Blueprint中修剪模式所涵盖的&#x200B;**实施步骤**。 要删除的分区通常包括： `## Implementation steps`、`## Implementation patterns`、`## Implementation considerations`，有时包括`## Prerequisites`。 根据每个Blueprint使用判断。
5. **逐个浏览** — 针对每个Blueprint提出更改，获得用户批准，然后应用。

### 通用规则

- 交叉链接提示措辞一致： `>This blueprint is also available as a [use case pattern](...) under <Category>.`
- 新文件（迁移期间创建的用例模式）**不包括`exl-id`** — Adobe发布分配这些文件。
- 新创作文件中的图像引用使用绝对路径(`/help/blueprints/...`)，而不是相对路径。
- 保留现有页面上的现有`exl-id`值。
- `redirects.csv`中的重定向遵循`source,dest`格式，包含`/en/docs/...`个路径（无`.html`）。

## 阶段A-E（初始结构工作） — 完成

| 阶段 | 结果 |
| --- | --- |
| A | 已创建`B2B Activation & Marketing`用例模式类别。 已重新定位3个现有模式(`b2b-audience-activation` → `b2b/account-audience-activation`，`buying-group-based-marketing` → `b2b/buying-group-marketing`，`b2b-analytics` → `b2b/account-analytics`)。 添加了3个重定向。 |
| B | 已将4个B2B Blueprint复制到`use-case-patterns/b2b/` (`marketo-data-journeys`、`paid-media-orchestration`、`campaign-intake-and-creation`、`campaign-review-and-approval`)。 |
| C | 已复制4个非B2B Blueprint (`real-time-profile-lookup`、`data-science-profile-enrichment`、`edge-profile-access`、`campaign-v8-orchestration`)。 |
| D | 已复制2个拆分Blueprint (`audience-sharing-with-target`， `third-party-messaging`)。 |
| E | 向9个重复分类的Blueprint添加了交叉链接提示。 |

A-E之后的用例模式总数：6个类别中的&#x200B;**26个模式**。

## 逐节演练（进行中）

本节演练将交叉链接/关系图迁移/impl-trim方法单独应用于用户审阅的每个Blueprint。

### ✅受众和配置文件激活 — 8/8完成

| # | Blueprint | 已采取的操作 |
| --- | --- | --- |
| 1 | `audience-manager.md` | 交叉链接提示+图表已迁移到模式(`anonymous-visitor-web-personalization`) +删除了RTCDP实施步骤 |
| 2 | `enterprise-destinations.md` | 交叉链接提示+图表已迁移到模式(`audience-activation-to-destinations`) |
| 3 | `advertising-activation.md` | 删除了Impl步骤（99→35行） |
| 4 | `customer-activity.md` | 已移除实施步骤（51→40行） |
| 5 | `data-science.md` | 删除了Impl注意事项（46→40行） |
| 6 | `real-time-lookup.md` | 已删除先决条件+实施模式/步骤/注意事项（156→73行） |
| 7 | `segment-match.md` | **无更改** （用户选择保持原样） |
| 8 | `rtcdp-target.md` | 删除了实施模式+注意事项（99→74行） |

### 🟡 B2B激活和营销 — 1/10正在进行中

| # | Blueprint | 状态 |
| --- | --- | --- |
| 1 | `b2b/overview.md` | **已暂停** — 等待决定A/B/C（请参阅上面的“我们现在所处的位置”） |
| 2 | `b2b/b2bactivation.md` | 待定 — 阶段E重复；添加了交叉链接；需要查看关系图+实施修剪 |
| 3 | `b2b/b2b-account-activation.md` | 待处理 — 图表分类；需要交叉链接到`b2b/account-audience-activation.md` +图表迁移注意事项 |
| 4 | `b2b/b2b-buying-group-journeys.md` | 待定 — 阶段E重复；添加了交叉链接；需要审查 |
| 5 | `b2b/b2b-journeys-with-marketo.md` | 待定 — 阶段B复制；模式为副本；需要执行步骤修剪 |
| 6 | `b2b/ajo-b2b-paid-media-controller.md` | 待定 — 阶段B复制；需要执行步骤修剪 |
| 7 | `b2b/marketo-engage-and-workfront-integration-blueprint/overview.md` | 待处理 — 区域登陆页面 |
| 8 | `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | 待定 — 阶段B复制；需要执行步骤修剪 |
| 9 | `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | 待定 — 阶段B复制；需要执行步骤修剪 |
| 10 | `b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md` | 待定 — 仅链接页面（标记为导航的审核） |

### ⚪ Customer Journey Analytics — 尚未开始0/5

文件： `overview.md`、`b2b-cja.md`（阶段E重复，已添加交叉链接）、`cja-rtcdp.md`（组2 — 建议交叉链接到`customer-analytics-insight-generation`）、`cja-ajo.md`（组2 — 相同）、`analysis.md`（组3，可能重定位到experience-platform/）。

### ⚪客户历程— 0/14尚未开始

文件： `overview.md`；`journey-optimizer/` （4个文件：概述，历程[阶段E]，营销活动[阶段E]，第三方消息传送[阶段D]）；`decision-management/` （3个文件：概述，边缘[阶段E]，中心[阶段E]）；`campaign-v8/` （3个文件：概述[阶段C]，rtcdp-and-v8，ajo-and-v8）；`campaign-v7/` （3个已弃用的文件）。

### ⚪ Experience Platform — 0/6尚未开始

文件： `experience-cloud.md`、`platform-applications.md`、`platform-data-flow.md`、`guardrails.md`、`deployment/websdk.md`、`deployment/appsdk.md`。 在审核中，所有得分均为仅图表，且带有0个模式信号。 **可能所有“无更改”** — 它们是与没有用例模式重叠的基础架构。

## 引用文件

| 文件 | 用途 |
| --- | --- |
| [blueprint-audit.md](blueprint-audit.md) | 每个Blueprint的审核表（43行）带有建议 |
| [rubric.md](rubric.md) | 用于对Blueprint进行分类的评分规则 |
| [migration-redirects.csv](migration-redirects.csv) | 从迁移分步重定向 |
| [重定向.csv](../redirects.csv) | 规范重定向文件（在阶段A中添加了3行） |

## 仍未解决的问题（来自审核）

1. **决策管理Edge +中心** — 当前均交叉链接到`offer-decisioning`。 考虑整合到单个部署选项图中？
2. **`journey-optimizer-journeys.md`** — 标记为不确定的`event-triggered-messaging`重复项；在修剪前验证范围。
3. **`customer-journey-analytics/analysis.md`** — 内容与Experience Platform查询服务有关，与CJA无关；请考虑重新定位到`experience-platform/`。
4. **Campaign v7（3个已弃用的文件）** — 是否从目录中迁移、离开或删除？
5. **`customer-success-stories.md`** — 仅链接页面；确认导航分类。
6. 新B2B节的&#x200B;**TOC锚点**&#x200B;为`{#b2b-patterns}` — 在任何生产重定向创建之前进行确认。

## 如何恢复

在此存储库中打开新的Claude代码会话，并说：

> 让我们继续进行Blueprint迁移。 阅读`_evaluation/migration-status.md`以了解我们中断的时间。

下一个具体步骤：响应`b2b/overview.md`决定(A/B/C)。 然后，继续使用Blueprint#2(`b2b/b2bactivation.md`)，并依次完成B2B部分、Customer Journey Analytics、客户历程和Experience Platform。
