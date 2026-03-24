---
title: 技术用例
description: 了解技术组织如何使用Adobe Experience Platform统一数据收集、实时转发事件，以及支持跨数字产品的分析和激活。
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: a1b2c3d4-e5f6-7890-abcd-ef1234567890
source-git-commit: 77908fd8a9f4309cbe66063cd33f065424697e55
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# 技术用例

技术组织使用Adobe Experience Platform来集中从Web、移动设备和产品表面收集的数据，并将实时事件分发到支持其产品和营销项目的分析、数据仓库和激活目标。 通过在边缘整合事件收集，技术团队降低了客户端的复杂性，提高了数据质量，并确保所有下游系统都从单个权威来源接收一致的行为数据。

## 实时事件转发

将通过Edge Network收集的实时行为事件转发到第三方分析、数据仓库和合作伙伴平台，以进行扩充和激活。 在边缘集中事件收集并转发到多个目标可减少客户端标记开销，提高数据质量，并确保所有下游系统都从单个权威源接收一致的事件数据。

### 商业影响

实施实时事件转发的技术组织可减少客户端标记负载和相关性能开销，同时提高事件数据在分析、数据仓库和激活目标之间的一致性。 服务器端转发还可以减少页面重量并改善加载性能，直接受益于用户体验量度。

### 实施方式

使用[事件转发](/help/blueprints/use-case-patterns/audience-building-activation/event-forwarding.md)模式将Adobe Experience Platform Web SDK收集的事件通过Edge Network路由到配置的服务器端目标。 当目标是从单个收集点进行服务器到服务器的事件分发时，这是一种正确的模式，而不是为客户端上的每个目标管理单独的标记，这会增加页面权重并造成跨系统的数据不一致。

### 技术注意事项

- Edge Network事件转发需要将事件收集迁移到Adobe Experience Platform Web SDK或Mobile SDK；在配置转发目标之前，必须评估现有的基于标记的实施是否兼容。
- 转发规则必须配置为仅发送每个目标所需的字段 — 避免将完整的XDM有效负载转发到只需要一小部分字段子集的目标，因为这会增加数据传输成本并产生合规性风险。
- 目标连接器必须正确地处理故障；事件转发管道应该对变得不可用的目标实施重试逻辑和警报，以防止在中断期间丢失数据。
- 必须审查每个转发目标的数据治理策略，以确保在转发配置中遵循在边缘捕获的用户同意首选项。
