---
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---
# Experience League Agent内存

## 此存储库中的密钥引用文件
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/metadata.md` — 存储库级别的元数据默认值
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/help/blueprints/TOC.md` — 指南级元数据
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/.cursor/skills/blueprint-document-reference/reference.md` — Blueprint创作模式

## 元数据规则（请参阅metadata-fields.md获取完整参考）
- 需要文章前置内容： `title`、`description`、`exl-id`
- 强烈建议使用文章封面内容： `solution`
- `exl-id`必须为有效的UUID；复制文件时，请删除/保留为空（由系统自动分配）
- `description`应以“学习如何……”开始 或“了解……” 根据Adobe准则
- SEO最多可有`title`个~60个字符；在标题中为产品名称使用`[!DNL ProductName]`
- `solution`值区分大小写，且必须与批准的枚举匹配（请参阅metadata-fields.md）
- `thumbnail: null`或`thumbnail:` （空白）都被使用；空是可接受的
- `kt:`是旧版字段（知识文章JIRA号）；在此存储库中仍可看到；可接受空白
- 使用的目录文件： `user-guide-title`、`breadcrumb-title`、`user-guide-description`、`product`、`mini-toc-levels`、`role`
- 存储库级别`metadata.md`使用： `cloud`、`solution`、`product`、`type`、`doc-type`、`mini-toc-levels`、`git-repo`、`index`

## 此存储库中的常见模式(blueprint-learn.en)
- 大多数Blueprint文件具有： `title`、`description`、`solution`、`exl-id`
- 某些旧文件还包括： `kt`、`thumbnail`
- 某些文件使用`version` (Campaign v8 Blueprint)
- 概述页面使用`doc-type: overview-page`
- `solution`通常包含多个逗号分隔值：例如`Real-Time Customer Data Platform, Campaign`
- 如果存在`exl-id`，则没有`solution`的文件仍通过验证

## 此存储库中使用的Adobe Markdown扩展
- `>[!NOTE]`, `>[!TIP]`, `>[!IMPORTANT]`, `>[!WARNING]`, `>[!CAUTION]`
- 选项卡式内容的`>[!BEGINTABS]` / `>[!TAB Name]` / `>[!ENDTABS]`
- `[!DNL ProductName]` — 不本地化产品名称的标记
- `[!UICONTROL Label]` — UI控件引用
- `{zoomable="yes"}` — 图像缩放属性
- `{width="1000"}` — 图像宽度属性
- `{target="_blank"}` — 外部链接目标

## 详细引用
- 完整的元数据字段引用： `metadata-fields.md`
- 创作指南抓取：https://experienceleague.adobe.com/en/docs/authoring-guide-exl/using/home （2026年2月）
