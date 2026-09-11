---
hold: true
title: 验证配置文件快照
description: 了解如何查询用户档案快照数据集，并了解为什么直到下一次每日批处理作业才会显示新流式处理的用户档案更新。
doc-type: article
solution: Experience Platform
exl-id: 1e7befcf-d952-47a2-86d9-33ef71eec57a
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# 验证配置文件快照

## 学习目标

确认配置文件尚未显示在配置文件快照数据集中。

## 使用配置文件快照数据集

1. 在左侧导航中，单击“数据管理”部分下的&#x200B;**数据集**，然后单击顶部边栏上的&#x200B;**浏览选项卡**

在“数据管理”部分中的![数据集浏览选项卡](assets/validate-profile-snapshot-datasets-browse-tab.png)

2. 在&#x200B;**搜索框**&#x200B;中，键入`profile`，然后&#x200B;**单击标题为“Profile-Snapshot...”的行**。   在右边栏中&#x200B;**复制表名称**&#x200B;并将其粘贴到可在下一步中引用的位置。

> [!NOTE]
>
>如果您没有看到“Profile-Snapshot...”，则可能必须清除任何筛选器 数据集。



配置文件快照数据集的![搜索结果](assets/validate-profile-snapshot-dataset-search.png)

3. 导航回查询编辑器，将以下SQL复制并粘贴到编辑器中

```sql
select
  identityMap,
  segmentID,
  segmentMembershipUps[segmentID] ['lastQualificationTime'],
  segmentMembershipUps[segmentID] ['status'],
  current_timestamp
from
  (
    select
      identityMap,
      explode (map_keys (segmentMembership['ups'])) as segmentID,
      segmentMembership['ups'] as segmentMembershipUps
    from
   
    where
      map_keys (segmentMembership['ups']) is not null
    limit 100
  )
  --where identityMap['email'][0].id = 'henry.creel@emailsim.io'
  limit 50
```

4. 更新表名和电子邮件地址，如下所述：
   - **表名：**&#x200B;第14行复制并粘贴您在`from`和`where`之间的配置文件快照表的表名
   - **电子邮件地址：**&#x200B;现在，在第19行上键入您在网站事件中发送的相同电子邮件地址（除非您更改了此地址，否则我们使用henry.creel\@emailsim.io）。
     - 目前，我们已将此注释掉（请保持原样）。 当查询运行而你查找henry时，你找不到他。

![具有要更新的配置文件快照表名称和电子邮件地址的查询编辑器](assets/validate-profile-snapshot-update-query-table-name.png)

5. 单击左上角的箭头&#x200B;**运行**&#x200B;查询
6. 结果如下（但如果你找henry，你就找不到他）

![查询结果显示快照中的流式处理配置文件不匹配](assets/validate-profile-snapshot-query-results-no-match.png)

>[!NOTE]
>
>**为什么没有针对Henry的结果？**
>
>**提醒**：配置文件快照是在&#x200B;**特定时间点**&#x200B;存在于配置文件中的&#x200B;**反射**&#x200B;或快照。 该作业每天运行&#x200B;**次**，用于下游目的，如AJO。 由于您刚刚在此数据中进行流式处理，因此配置文件快照尚未包含此数据。  明天会的。

## 回顾

了解快照数据集会在计划的批处理过程中更新，而不是立即更新。
