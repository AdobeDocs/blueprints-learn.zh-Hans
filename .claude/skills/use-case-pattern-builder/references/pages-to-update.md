---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---
# 添加用例模式时要更新的页面

创建新的用例模式时，必须更新以下页面，确保模式可发现并正确链接。

## 所需更新

### 1. TOC.md
- **文件：** `/help/blueprints/TOC.md`
- **操作：**&#x200B;在正确的类别部分下添加新条目
- **格式：** `    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)`
- **位置（按类别）：**
   - Audience Building &amp; Activation：在第47行之后（在该部分中的现有条目之后）
   - Personalization：第52行之后
   - 营销活动管理和编排：第58行之后
   - 分析：在第61行之后
   - 对话体验：第63行之后

#### 类别到目录映射

| 类别概要 | 目录章节标题 | 锚点 |
| --- | --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation` | `{#audience-building-activation}` |
| `personalization` | `+ Personalization` | `{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration` | `{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis` | `{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience` | `{#conversational-experience-patterns}` |

#### 缩进规则

- 类别标题使用两个空格+ `+`（例如，`  + Personalization{#personalization-patterns}`）
- 模式条目使用四个空格+ `+` （例如， `    + [Pattern Title](path)`）

### &#x200B;2. 用例模式概述
- **文件：** `/help/blueprints/use-case-patterns/overview.md`
- **操作：**&#x200B;向正确的类别表添加新行
- **格式：** `| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |`
- 概览中的&#x200B;**类别：**
   - Audience构建和激活（第18行）
   - Personalization （第29行）
   - 营销活动管理和编排（第40行左右）
   - 分析（第52行）
   - 对话体验（第61行）

#### 行格式示例

```
| [Event-Triggered Messaging](campaign-management-orchestration/event-triggered-messaging.md) | Listen for a real-time behavioral or system event, then deliver a contextual message to the triggering profile | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
```

## 验证核对清单

- [ 在正确的类别目录中创建]模式Markdown文件
- [ ] Frontmatter包括标题、描述、解决方案和exl-id
- [ ] TOC.md条目已添加到正确的类别下
- [ 在正确的类别下添加了] Overview.md表行
- [ ]所有业务目标链接指向现有文件
- [ ]文件使用kebab大小写命名约定
- [ ]所有Experience League链接都是有效的URL
- [ ]个Adobe产品名称使用`[!DNL ...]`语法
- [ ]函数链使用` > `分隔符格式
- [ ]模式文件包含所有必需部分（请参阅pattern-template.md）
