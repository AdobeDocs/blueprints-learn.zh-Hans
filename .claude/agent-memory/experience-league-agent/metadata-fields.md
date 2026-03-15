---
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 1%

---
# Adobe Experience League — 批准的元数据字段参考

*源自Adobe ExL Authoring Guide （抓取日期：2026年2月） + blueprint-learn的repo分析。en*

---

## 元数据层次结构

元数据按此顺序层叠（文章覆盖TOC，TOC覆盖repo）：
1. 文章封面事项（最高优先级别）
2. 用户指南中的TOC.md
3. 存储库根中的metadata.md （最低优先级）

---

## 文章级字段

### 必填

| 字段 | 描述 | 格式/约束 |
|-------|-------------|----------------------|
| `title` | SEO页面标题。 显示在搜索结果中。 | 最多~60个字符；标题大小写；将`[!DNL Product]`用于产品名称；除非有意，否则不要完全复制H1 |
| `description` | 搜索引擎和ExL推荐的Meta描述。 | 150-160个字符；最好从“学习如何……”开始 或“了解……”；如果缺少/为空，验证将失败 |
| `exl-id` | 系统分配的唯一标识符。 用于内容跟踪。 | UUID格式（例如`70573eb9-cd69-4fe6-b2ae-dae81665a308`）；复制文件时删除&#x200B;**2} — 将自动分配该文件；从不跨文件复制** |

### 强烈建议

| 字段 | 描述 | 有效值 |
|-------|-------------|--------------|
| `solution` | 本文涵盖的Adobe产品。 用于ExL搜索/筛选和内容推荐。 | 逗号分隔；区分大小写；必须与批准的枚举匹配（请参阅下面的“有效解决方案值”） |

### 可选 — 通用

| 字段 | 描述 | 有效值/注释 |
|-------|-------------|----------------------|
| `kt` | 旧版知识文章JIRA号。 用于分析跟踪。 | 整数（例如`7207`）；可接受空白；`null`可接受 |
| `thumbnail` | recommendations/analytics的缩略图图像引用。 | 文件名字符串、`null`或空白 |
| `version` | 产品版本过滤器。 主要用于AEM和Campaign Blueprint。 | E.g. `Campaign v8`，`Campaign v8 Client Console`；必须匹配version.yml |
| `doc-type` | 存储库/分析中使用的内容分类。 | `blueprint`、`overview-page`、`Video`、`Tutorial`、`Troubleshooting`（首选小写） |
| `feature` | 在ExL页面上显示为“主题”的主题标记。 | 每篇文章1-2；标题大小写；必须匹配feature.yml；逗号分隔 |
| `feature-set` | 用于功能验证的父应用程序。 | 必须匹配feature.yml值 |
| `role` | 目标受众角色。 在ExL上显示为“Created for”。 | `Admin`, `Architect`, `Data Architect`, `Data Engineer`, `Developer`, `Leader`, `User` |
| `level` | 用户体验级别。 在ExL上显示为“Created for”。 | `Beginner`，`Intermediate`，`Experienced` （字首大写） |
| `topic` | 搜索/筛选的跨产品主题。 | 标题大小写；必须匹配topic.yml；逗号分隔 |
| `type` | 指南分类。 | `Documentation` （默认），`Tutorial`，`Troubleshooting` |
| `last-substantial-update` | 在“新增功能”构件中显示内容。 | 格式： `YYYY-MM-DD` |
| `hide` | 从所有搜索和推荐中排除页面；还将index设置为no。 | `yes`或`no` |
| `hidefromtoc` | 从目录导航中删除，但仍可通过直接链接访问页面。 | `yes`或`no` |
| `index` | 控制页面是否显示在外部搜索/站点地图中。 | `yes`/`no`或`y`/`n`；默认值： `no` （已索引） |
| `recommendations` | 控制“有关此功能的更多帮助”构件行为。 | `noDisplay` （禁止显示构件）、`noCatalog` （从推荐池中排除） |
| `internal` | 将页面标记为仅限Adobe内部。 防止内部链接标记。 | `yes` |
| `short-description` | ExL登陆页面的简化描述。 如果省略，则使用`description`。 | 一句话；最多20个词 |
| `activity` | 页面使用情况分类。 | `understand`，`implement`，`troubleshoot`（小写） |
| `sub-product` | 产品子组件。 与解决方案团队合作以获取有效的枚举。 | 小写；例如`search`，`assets`，`sites` |
| `team` | 用于分析的团队分配。 | E.g. `TM` |
| `landing-page-name` | 指向痕迹导航登陆页面的链接。 | E.g. `experience-manager` |
| `landing-page-breadcrumb-title` | 登陆页面链接的痕迹导航文本。 | E.g. `AEM` |
| `auto-video-transcripts` | 默认情况下启用视频转录。 | `true` |
| `badgeType` | 内容状态的徽章。 | 各不相同；例如`informative`、`positive` |
| `badgePremium` | Premium徽章指示器。 | 根据Adobe徽章规范 |
| `badgeLabel` | 徽章标签文本。 | 短字符串 |
| `source-git-url` | Source存储库URL。 | 完整的GitHub URL |
| `cloud` | 文章级别的云类别覆盖。 | 标题大小写；必须匹配cloud.yml |

---

## TOC.md字段

| 字段 | 描述 | 注释 |
|-------|-------------|-------|
| `user-guide-title` | ExL痕迹导航和登陆页面中显示的指南名称。 | 目录文件需要 |
| `breadcrumb-title` | 用户指南标题过长时痕迹导航的较短指南名称。 | 可选 |
| `user-guide-description` | ExL登陆页面的指南摘要。 | 一句话；最多建议20个词 |
| `product` | 指南的Analytics跟踪。 仅限单个值。 | 必须匹配product.yml（请参阅有效的产品值） |
| `mini-toc-levels` | 右导航小型目录中所显示的标题级别数。 | 整数1-6；默认值2 |
| `role` | 指南的默认受众角色。 | 与文章`role`的值相同；逗号分隔 |
| `index` | 是否对指南编制索引。 | `yes`/`no` |

---

## 存储库级别metadata.md字段

| 字段 | 注释 |
|-------|-------|
| `cloud` | 存储库中所有文章的默认云类别 |
| `solution` | 所有文章的默认解决方案 |
| `product` | 分析跟踪的默认产品 |
| `type` | 默认参考线类型 |
| `doc-type` | 默认文档类型 |
| `mini-toc-levels` | 默认迷你目录级别 |
| `git-repo` | GitHub存储库URL；启用“编辑此页面”和“日志问题”按钮 |
| `index` | 默认索引设置 |

---

## 有效的解决方案值（区分大小写）

此存储库中使用的常用值：
- `Experience Platform`
- `Real-Time Customer Data Platform`
- `Journey Optimizer`
- `Journey Optimizer B2B Edition`
- `Customer Journey Analytics`
- `Campaign`
- `Campaign v8`
- `Campaign Classic v7`
- `Campaign Standard`
- `Audience Manager`
- `Target`
- `Analytics`
- `Data Collection`
- `Commerce`
- `Marketo Engage`
- `Experience Cloud`
- `Journey Orchestration`

多个值：逗号分隔，如`Real-Time Customer Data Platform, Campaign`

---

## 有效的产品值（针对`product`字段 — analytics跟踪）

请参阅系统提示以获取完整列表。 键值：
- `adobe experience platform` / `experience platform` / `aem`
- `adobe analytics` / `analytics` / `aa`
- `adobe journey optimizer` / `journey optimizer` / `jo`
- `adobe customer journey analytics` / `customer journey analytics` / `cja`
- `adobe real time customer data platform` / `real time cdp` / `rtcdp`
- `adobe marketo` / `marketo` / `amk`
- `adobe campaign` / `campaign` / `ac`
- `adobe target` / `target` / `at`

---

## 有效的角色值

- `Admin`
- `Architect`
- `Data Architect`
- `Data Engineer`
- `Developer`
- `Leader`
- `User`

---

## 关键验证规则

1. 切勿在复制的文件中保留具有相同UUID的`exl-id` — 请删除它并让系统分配一个新的文件。
2. 可接受空白/空`thumbnail`和`kt`；它们是旧版字段。
3. `solution`值必须与批准的枚举完全匹配 — 区分大小写。
4. 如果缺少或null，则`description`验证失败；请始终提供有意义的值。
5. 如果`title`值包含冒号、括号或前导特殊字符，请用引号括起来。
6. 多个`solution`值在单个字符串值中以逗号分隔。
7. `product`仅是单值（用于Analytics跟踪）；请勿使用逗号分隔的值。
8. 要请求新的枚举值，请提交具有“内容标记”组件的UGP JIRA票证。
