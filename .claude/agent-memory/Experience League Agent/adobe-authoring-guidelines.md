---
name: Adobe Experience League Authoring Guidelines
description: Adobe Experience League Markdown创作规则的完整参考，2026年3月抓取自官方创作指南。
type: reference
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 0%

---


# Adobe Experience League创作准则

Source： https://experienceleague.adobe.com/en/docs/authoring-guide/using/home
抓取：2026-03-15

---

## &#x200B;1. 元数据/前置内容

### 必填字段
| 字段 | 要求 | 规则 |
|---|---|---|
| `title` | 必填 | 最多60个字符（英语）。 字首大写。 除非为了清楚起见，否则不要使用产品名称。 系统附加» | “ProductName”自动。 如果包含冒号或括号，请用引号括起来。 |
| `description` | 必填 | 最多150-160个字符 不能为空/空。 概念从“了解……”开始 任务开始“了解如何……” 或命令动词。 |

### 可选但经常使用的字段
| 字段 | 有效值 | 注释 |
|---|---|---|
| `feature` | 必须匹配功能的YAML值；带空格的标题大小写（例如，“内容片段”） | 每篇文章1-2；显示在主题中 |
| `feature-set` | 必须针对功能YAML进行验证 | 功能的父级应用程序 |
| `role` | 用户、开发人员、负责人、管理员、架构师、数据架构师、数据工程师 | 区分大小写；显示为“Created for” |
| `level` | 初学者，中级，经验丰富 | 如果未指定，则默认为“初学者” |
| `solution` | 必须与解决方案YAML匹配（例如，“Campaign， Campaign Standard v7”） | 允许多个值；用于搜索筛选 |
| `topic` | 必须匹配主题YAML；带空格的字首大写 | 对于跨产品筛选（例如“集成”） |
| `type` | 文档、教程、疑难解答 | 存储库级别；默认为“文档” |
| `short-description` | 一句，最多20字 | 对于描述过长的ExL登陆页面 |
| `badgePremium` | `label="Premium" type="Positive" url="..."` | 页面级徽章 |
| `mini-toc-levels` | 1-6（默认2） | 控制右导航标题显示深度 |
| `hidefromtoc` | true/false | 从左侧导航中排除，但保持URL可访问 |

### 元数据放置
- 文章级别：作为YAML前件的Markdown文件顶部
- TOC级别：在TOC.md文件中
- 存储库级别：在metadata.md文件中

### 关键格式规则
- 用引号括起包含逗号或括号的值
- 多个值之间用逗号分隔
- 根据YAML定义区分大小写进行匹配
- 空/空标记值导致验证失败

### 已弃用的字段
seo-title， seo-description，受众，难度， uuid（来自迁移时代）

---

## &#x200B;2. MARKDOWN语法（ADOBE风格）

### 文本格式
- 粗体： `**text**`
- 斜体： `*text*`
- 粗体+斜体： `***text***`
- 转义特殊字符：在`# { } [ ] * + - . !`之前使用反斜杠`\`
- HTML实体： `&lt;` `&gt;` `&amp;` `&mdash;` `&ndash;`

### 标题
- 使用ATX样式（仅使用`#`语法，从不为下划线/文本文式）
- 每个文档一个H1（通常是与元数据`title`匹配的页面标题）
- 所有后续标题H2 (`##`)或更低
- 标题前后需要空白行（第一个标题除外）
- 最多69个字符（英文）/120个字符（本地化）
- 最多首选~5个词
- 所有标题的句子大小写（仅首词和专有名词使用大写）
- 标题大小写仅用于`title`元数据字段
- 无结尾标点（常见问题标题允许使用问号）
- 自定义锚点ID： `## Title {#custom-id}` — 使用连字符，而不是句点
- 文档中没有重复的标题锚点ID
- 避免使用保留的锚点名称：搜索、结果、彩块化、分页、排序、查询、搜索框、内容、页眉、页脚、主要、导航、侧栏、页面、容器、包装器
- 在每个标题后至少跟随一个正文段落（不要将列表/表格直接放在标题后面）
- 概念标题：名词/名词短语
- 任务标题：祈使动词（非动名词 — “创建区段”而不是“创建区段”）
- 标题级别间的并行结构

### 列表
- 项目符号（未排序）： `*`、`-`或`+` — 在文档中一致使用
- 已排序：每项`1.` （自动编号）
- 列表前后的空白行
- 缩进嵌套的编号项3空格；嵌套的项目符号2空格
- 项目符号标点：在末尾省略分号/逗号/连接符；仅为完整句子添加句点
- 如果所有项目均为≤3个单词或UI标签/标题，请勿添加句点

### 链接
- 外部： `[text](https://url.com)`
- 相对（同一级别）： `[text](file.md)`
- 根相对： `[text](/help/path/file.md)` — 必须以`/`开头
- 深层链接（同一页面）： `[text](#heading-anchor)`
- 跨文档深层链接： `[text](file.md#heading-id)`
- 强制新选项卡： `[text](url){target="_blank"}`
- 空URL：用尖括号`<https://example.com>`括起来，使其可点击
- 引用链接：只有绝对链接才适用于引用样式链接
- 不要通过相对链接将同一文件包含在多个TOC位置
- Windows用户：将反斜杠转换为路径中的正斜杠

### 图像
- 基本： `![alt text](image.png "hover tooltip")`
- 调整大小： `{width="300"}`
- 对齐： `{align="center"}`或`{align="right"}`
- 可缩放： `{zoomable="yes"}`或`{modal="regular"}`
- 最大文件大小：100 MB（建议在5 MB以下）
- 所有图像都需要替换文本（对于SEO和可访问性）
- 图像文件名：带连字符的小写
- 将图像存储在指定的资源文件夹中

### 代码块
- 内联：回退`` `code` ``
- 用于：文件名、URL、用户定义的术语、命令
- 受防护的代码块：带有语言标识符的三重反撇号

  ```
  ```javascript
  code here
  ```

  ```
  
  
- 选项： `{line-numbers="true"}`、`{start-line="7"}`、`{highlight="11-13, 16"}`
- 始终在受防护的代码块中包含语言标识符

### 表
- 分隔符行的每列至少需要3个连字符： `|---|---|---|`
- 对齐方式：左`|---|`，中`|:---:|`，右`|---:|`
- 转义文本管道： `\|`或使用`&vert;`
- 允许HTML表；使用`<table style="table-layout:auto">`或`table-layout:fixed`
- HTML表对齐方式：`<td align="left|center|right">`
- 避免HTML表中的Markdown语法（例如，`[!NOTE]`在HTML表中不起作用）
- 删除边框： `<tr style="border: 0;">`
- Markdown表布局选项：在带有空白行的表后面添加`{style="table-layout:auto"}`
- 由于水平滚动条可见性问题，避免使用非常宽/高的表格

---

## &#x200B;3. 特殊的ADOBE语法扩展

### 标注/告诫

```
>[!NOTE]
>
>Text here.

>[!TIP]
>
>Text here.

>[!IMPORTANT]
>
>Text here.

>[!WARNING]
>
>Text here.

>[!CAUTION]
>
>Text here.

>[!ADMIN]
>[!AVAILABILITY]
>[!PREREQUISITES]
>[!INFO]
>[!ERROR]
>[!SUCCESS]
```
- 严重： `>`和`[!`之间没有空格 — 使用`>[!NOTE]`，而不是`> [!NOTE]`
- 在`>[!NOTE]`和正文文本行之间添加空白行

### 选项卡

```
>[!BEGINTABS]

>[!TAB iOS]
Content here

>[!TAB Android]
Content here

>[!ENDTABS]
```

### 可折叠部分（折叠）

```
+++Click to expand
Content inside
+++
```
注意：不支持嵌套的可折叠部分。

### 阴影框

```
>[!BEGINSHADEBOX "Optional Title"]
Content here
>[!ENDSHADEBOX]
```

### 视频

```
>[!VIDEO](https://video.tv.adobe.com/v/ID/?quality=12&learn=on)
```
为成绩单添加`{transcript=true}`。

### 更多此类内容

```
>[!MORELIKETHIS]
>* [Article 1](url)
>* [Article 2](url)
```

### 上下文帮助

```
>[!CONTEXTUALHELP]
>id="..."
>title="..."
>abstract="..."
>additional-url="..."
```

### 徽章（内联）

```
[!BADGE Label]{type=Informative url="https://example.com" tooltip="text"}
```
类型： `Informative` （蓝色）、`Positive` （绿色）、`Negative` （红色）、`Neutral` （灰色）、`Caution` （黄色）

### 文本突出显示（预览）

```html
<span class="preview">highlighted text</span>
```

### 包含和代码片段
- 包含整个文件： `{{$include /help/_includes/legal-blurb.md}}`
- 代码片段（无标题）： `{{snippet-id}}`
- 将可重用文件存储在`help > _includes/`文件夹中
- 存储在`help > _includes/snippets.md`中的代码片段
- 包含可以包含标题；代码片段不能包含
- 仅适用于同一存储库（而非跨存储库）
- 在非引用文件中转义`{{`或`}}`个字符

### DNL（不本地化）标记
- `[!DNL ProductName]` — 包装不应翻译的产品/品牌名称
- 在页面中的第一个或突出提及上使用

### UICONTROL标记
- `[!UICONTROL Button Label]` — 封装UI元素文本（按钮、菜单、字段名称）
- 确保从产品数据库而不是机器翻译中提取UI字符串
- UICONTROL标记中没有撇号、引号或标点
- 对步骤中引用的UI元素使用粗体格式

### 不支持的功能
- 任务列表（复选框）
- 表情符号
- 水平线条
- 嵌套的可折叠部分

---

## &#x200B;4. 文件命名和文件夹结构

### 文件命名规则
- 小写文件名（仅带连字符）
- 无大写、下划线、句点或空格
- 描述性的SEO友好名称（例如，`calculated-metric-overview.md`不是`cmo.md`）
- 避免使用文件名中的数字；使用描述性文字
- 避免保留/冲突名称： `metadata.md`，`search.md`
- 重命名实时文件需要重定向管理（URL更改）

### 文件夹结构
- 目录/文件夹名称不影响URL（只有存储库名称和文件名会影响URL）
- TOC.md控制导航层次结构，而不是Git文件夹位置
- 将图像/资产存储在指定的资产文件夹中
- 存储在`help/_includes/`中的可重用包含
- 存储在`help/_includes/snippets.md`中的代码片段

### TOC.md规则
- 每篇文章都必须在TOC.md中列出，才能在Experience League上呈现
- H1格式： `# Guide Title {#anchor-id}` — 锚点生成基本URL路径
- 节标题必须具有锚点ID： `+ Section Name {#section-id}`
- 章节标题（父项目）不能是链接本身
- 文章链接： `+ [Title](path/file.md)`
- 更改部分锚点ID将更改所有嵌套的文章URL（需要重定向）
- 在整个（`+`、`*`或`-`）中使用一致的项目符号样式
- 目录元数据： `user-guide-description`，可选`breadcrumb-title`
- `mini-toc-levels`：控制右侧导航标题显示（1-6，默认2）

---

## &#x200B;5. 内容质量和编辑标准

### 语音和色调
- 主动语音优先于被动语音
- 现在时态与未来时态
- 第二人（“您”），用于指导内容
- 35字以下的句子
- 强而精确的动词 — 避免使用弱副词（“非常”、“极其”）

### 步骤/过程
- 每一步都是一个简洁的命令（一个句子）
- 下一行（在步骤下缩进）会提供额外信息
- 每个步骤以命令动词开始
- 将过程限制为大约7步（最多到10步再进入子任务）
- 将概念信息放在步骤之前
- 在相关步骤之后放置屏幕截图
- 为读取器方向重复页面/选项卡名称
- 步骤中UI元素的粗体UICONTROL格式

### 界面术语
- **打开/关闭**：应用程序和程序
- **转到**：菜单、选项卡或用户界面位置
- **选择**：文本、单元格或列表中的选项
- **单击**：鼠标操作（除非必需，否则请避免指定控件类型）
- **下拉菜单**（不是“下拉列表”）

### 产品名称
- 不要将产品名称添加到标题/标题，除非清楚明了
- 在产品名称前省略“the”
- 在指南级别第一次提及时包含“Adobe”（商标要求）
- 除非法律要求，否则在次要提及中放置“Adobe”
- 对产品名称使用DNL标记以防止误解

### 强调和格式化
- 粗体：UI元素和键盘操作
- 斜体：错误消息、外来词、强调
- 代码（反撇号）：文件名、URL、用户定义的术语
- UI元素周围没有引号（请改用UICONTROL标记）

### 大写
- 标题、导航、副标题的句子大小写
- 仅适用于`title`元数据字段的标题大小写
- 专有名词始终大写

---

## &#x200B;6. SEO最佳实践

- 每页一个H1 — 必须简明扼要，描述性强，并告知用户该页面的内容
- 顺序标题层次结构（h1 → h2 → h3，从不跳过级别）
- 在H1中包括关键字、正文文本和元数据（不是`keywords` meta标记 — Google会忽略它）
- 避免关键词填充（意图>频率）
- 标题：最多50-60个字符；系统自动附加“| Adobe产品名称”
- 描述：150-160个字符；应该是call to action，而不是内容的重复
- 向所有图像添加描述性替换文本
- 包括视频成绩单（搜索引擎只能读取文本）
- 从战略上链接到相关页面（避免孤立页面）
- 包括结构化元素：编号列表、子标题、代码块
- 使用AnswerThePublic、Google Trends等工具研究关键词
- 内容应显示E-E-A-T（经验、专业知识、权威性、可信度）

---

## &#x200B;7. 本地化

### 机器翻译优先
- 英语源内容自动生成本地化版本
- 支持的语言：德语、法语、日语、意大利语、西班牙语、巴西葡萄牙语、简体中文、繁体中文、韩语、荷兰语、瑞典语

### 写入以进行本地化
- 整个过程中术语保持一致
- 短句和主动语态
- 标准英语单词顺序（主语→动词→对象）
- 使用相对代词（“那”、“那”）
- 避免：幽默、成语、行话、地区短语、隐喻、不必要的词语

### 本地化标记
- `[!UICONTROL Label]` — 确保从产品数据库中提取UI字符串，而不是机器翻译
- `[!DNL ProductName]` — 阻止翻译产品/品牌名称
- “不本地化”文件夹中的图像将从本地化中排除

---

## &#x200B;8. 内容类型

- **指南**：在线收集目录中引用的页面；涵盖官方最佳实践
- **教程**：针对特定用例的说明内容（视频或文本）；已在学习存储库中发布
- **参考指南**：开发人员API/SDK；通常为表格式；已发布到developer.adobe.com
- **课程**：针对特定用户角色的专家策划的课程集合
- **知识库文章**：简短、临时相关的故障排除内容
- **登陆页面/主页**：单独管理(SCCM)

---

## &#x200B;9. 要避免的常见验证错误

- 缺少或空白`title`或`description`元数据
- `description`不以“了解……”开头 或“学习如何……”
- 标注语法中介于`>`和`[!`之间的空格（`> [!NOTE]`而不是`>[!NOTE]`）
- 粗体标记中的空格： `**text **` （尾随空格破断粗体）
- HTML表中的Markdown语法（例如，此处无法使用标注）
- 文档中的标题锚点ID重复
- 包含句点的锚点ID（请改用连字符）
- 使用保留的锚点名称（搜索、结果、页眉、页脚等）
- 不符合YAML定义的`role`、`level`、`feature`、`topic`值
- 栈叠标题，标题之间无正文文本
- H1在每个文档中使用了多次
- 跳过的标题级别（例如，H1→H3）
- 使用大写、下划线或空格命名文件
- 图像上缺少替换文本
- Gerund任务标题(“正在创建……” 而不是“创建……”)
