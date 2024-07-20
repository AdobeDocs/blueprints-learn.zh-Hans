---
title: 审查和批准 Blueprint
description: 审查和批准 Blueprint - Marketo Engage 和 Workfront 集成 Blueprint
exl-id: a446faab-7db4-42a2-b4b9-395725c49c9f
source-git-commit: 3d6a2416cdb9956e59be4b2918ba19f88cd2150b
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 87%

---

# 审查和批准 Blueprint {#review-and-approve-blueprint}

确保营销资产和营销活动满足业务的期望和标准，而不仅仅是为适当的受众提供适当的内容和消息。在启动新的营销方案时，组织还要负责坚守内部政策、行业法规，甚至还要遵守法律先决条件。通过将审查和批准步骤纳入营销活动开发流程中，营销团队可确保内容和消息传递准确无误且符合其行业标准，这在金融、医疗保健和制药等行业中尤为重要。

借助 Workfront 和 Marketo Engage，营销团队有机会打造紧密互联的营销系统，让消息传递准确无误且符合标准。

## 通过 Workfront 为 Marketo Engage 解锁验证和高级审批 {#unlock-proofing-and-advanced-approvals}

在考虑构建营销活动时，我们必须考虑到有多个系统在支持所涉及的不同步骤，包括：规划、构建、审查、反馈、批准和执行。借助 Workfront 和 Marketo Engage，各个团队拥有所需的所有工具，能完成从规划到启动新营销活动的端到端流程。此外，团队还可以进一步简化其审查和批准流程，在确保准确性和合规性达到最高标准的同时，提高营销活动的开发速度。

### 查看和批准使用Marketo Engage和Workfront解锁的用例 {#review-and-approve-use-cases-unlocked-with-marketo-engage-and-workfront}

* 利用 Workfront 对 Marketo Engage 资产的注释和评论功能，消除不一致的反馈并增进集中式协作。

* 通过 Workfront 审批工作流在 Marketo Engage 中触发审批来集中处理审批。

* 将 Workfront 的高级审批功能用于 Marketo Engage 资产，从而支持并简化营销资产的复杂审批工作流。

* 以编程方式将 Marketo 资产引入 Workfront 以供多个利益相关者审查，实现营销草稿的大众化访问。

* 通过在 Workfront 中集中处理 Marketo Engage 资产的所有审查和验证工作，跟踪更改并创建书面记录。

## 规划验证和审批工作流程 {#planning-your-proof-and-approval-workflow}

在 Marketo Engage 和 Workfront 之间设置验证和审批集成之前，请考虑以下方面：

* 哪些资产需要审查和批准？
* 需要让谁成为审批者？
* 在营销资产上线之前，是否需要多位审批者？
* 将在营销活动开发过程的哪个阶段组合营销资产并准备好进行审查？

回答这些问题将帮助您得出一个基准，以确定审批流程的大致情况以及如何开始考虑配置 Workfront 实例。

## 构建 Marketo Engage 和 Workfront 之间的验证和审批工作流程 {#building-a-proof-and-approval-workflow}

为了简化 Workfront 和 Marketo Engage 之间的验证和批准流程，您可以使用 Workfront Fusion 集成这两个解决方案。Workfront Fusion 提供了一个工作流程界面，用于在 Workfront 和 Marketo Engage 实例之间触发操作和传递信息。

为此，请考虑将以下步骤作为集成审查和批准体验流程的一部分。

1. 使用“准备审查”任务配置您的 Workfront 项目。
1. 触发您的 Marketo Engage 电子邮件以通过任务状态更改同步到 Workfront。
1. 在 Workfront 中将 Marketo Engage 电子邮件文件转换为可审查的验证。
1. 使用Workfront校对通过注释和批注进行协作。
1. 批准 Workfront 验证以触发 Marketo Engage 中的资产批准，然后将任务标记为完成。

### 使用“准备审查”任务配置 Workfront 项目 {#configure-a-workfront-project-with-a-ready-for-review-task}

使用[项目模板](https://experienceleague.adobe.com/docs/workfront/using/manage-work/projects/create-and-manage-project-templates/project-template-overview.html?lang=zh-Hans){target="_blank"}捕获与组织中项目关联的大多数可重复流程、信息和设置。您可以在模板中定义任务、队列主题，创建自定义表单以及附加文档。

在 Workfront 的项目模板中，加入用于审查营销活动所含资产的任务。此外，您还可以添加审批流程来处理单个审批或更复杂的多级别审批。

如果要启动新的电子邮件营销活动，您使用的项目模板应该包括审查电子邮件的任务，以及可确保电子邮件在发送之前获得利益相关者批准的审批流程。

![任务屏幕](assets/review-and-approve-blueprint-1.png){zoomable="yes"}

### 触发您的 Marketo Engage 电子邮件以通过任务状态更改同步到 Workfront {#trigger-your-marketo-engage-email-to-sync-to-workfront}

在审查过程中，您需要能够在电子邮件准备好供营销团队审查后，将电子邮件同步到您的 Workfront 项目。为此，我们建议使用设置一个“准备审查”任务，并用[任务状态](https://experienceleague.adobe.com/docs/workfront/using/manage-work/projects/update-work-on-a-project/update-task-status.html?lang=zh-Hans){target="_blank"}来表示何时可以审查电子邮件。在此示例中，我们向任务添加了“审查 Marketo 电子邮件”状态，可在电子邮件草稿可供利益相关者审查时选择此状态。

在 Workfront 项目中准备好此状态后，您可以将 Workfront Fusion 场景配置为监听“准备审查”任务以更新为“审查 Marketo 电子邮件”。更新后，您的场景可以检索 HTML 文件格式的 Marketo Engage 电子邮件，将其压缩，并在 Workfront 项目文档中保存其副本以供审查。

![准备好进行审核屏幕](assets/review-and-approve-blueprint-2.png){zoomable="yes"}

### 在 Workfront 中将 Marketo Engage 电子邮件转换为可审查的验证 {#convert-your-marketo-engage-email-to-reviewable-proof-in-workfront}

将“准备审查”任务移至“审查 Marketo 电子邮件”状态并在 Workfront 中保存 Marketo Engage 电子邮件后，您可以配置 Workfront Fusion 场景以将电子邮件转换为 Workfront 验证。

### 使用Workfront校对通过注释和批注进行协作 {#use-workfront-proofing-to-collaborate}

[Workfront的校对](https://experienceleague.adobe.com/docs/workfront/using/review-and-approve-work/proofing/proofing-overview/proofing-basics.html){target="_blank"}功能允许您的营销团队获取新资源（如图像或电子邮件），并通过评论和批注进行协作。 一旦验证准备好上线，决策者就可以批准验证工具中的资产。

![转换电子邮件屏幕](assets/review-and-approve-blueprint-3.png){zoomable="yes"}

### 批准Workfront Proof并在Marketo Engage中触发资源批准，将任务标记为完成 {#approve-workfront-proof-and-trigger-asset-approval-in-marketo-engage}

Workfront Fusion可以检测电子邮件何时获得利益相关者的批准，并向Marketo Engage发送请求，以在Marketo中批准电子邮件。

经过合适的团队成员审核/批准的电子邮件，即可在Marketo Engage中上线！

## Fusion 场景模板 {#fusion-scenario-templates}

为帮助您简化在自己的 Workfront 和 Marketo Engage 实例中开发审查和批准工作流程的过程，我们构建了 Fusion 模板以帮助您开始进行集成。您可以在 Fusion 的“公共模板”部分中搜索“Marketo”并将模板下载到实例中，从而利用这些模板。

### 在 Workfront 中查看 Marketo Engage 电子邮件草稿的电子邮件验证 {#review-an-email-proof-of-your-marketo-engage-email-draft-in-workfront}

以下 Fusion 场景将引导您完成审查和批准流程的上半部分，在这部分流程中，可以从 Marketo Engage 中提取电子邮件草稿并将其另存到 Workfront 中作为验证。将其另存为 Workfront 项目文档中的验证后，营销利益相关者可进行审查，并在审查过程中添加评论和注释。

![融合方案审阅和批准流程](assets/review-and-approve-blueprint-4.png){zoomable="yes"}

### 在 Workfront 中批准触发 Marketo Engage 中资产审批的电子邮件 {#approve-an-email-in-workfront-that-triggers-approval}

以下 Fusion 场景可用于检测 Workfront 中的验证何时获得批准，并将该批准路由到 Marketo Engage 以更新电子邮件草稿，使其在 Marketo Engage 项目中上线并准备好使用。

![融合场景验证审批](assets/review-and-approve-blueprint-5.png){zoomable="yes"}

这两种场景结合起来可以创造出双向路径，既能将营销资产从 Marketo Engage 拉入 Workfront 强大的审查和批准工作流程中，也能将批准从 Workfront 推送回 Marketo Engage。
