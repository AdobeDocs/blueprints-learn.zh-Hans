---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---
# 用例目录行模板

## 行格式

用例目录表中的每一行都遵循以下确切格式：

```
| <img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40"> | [{Use Case Title}]({industry}/{industry}-overview.md#{heading-anchor}) | {One-sentence description} | [!BADGE {Maturity}]{type={Type}} | [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) |
```

### 没有图标的行（在图标尚不可用时使用）

```
| | [{Use Case Title}]({industry}/{industry}-overview.md#{heading-anchor}) | {One-sentence description} | [!BADGE {Maturity}]{type={Type}} | [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) |
```

## 字段引用

| 字段 | 格式化 | 示例 |
| --- | --- | --- |
| industry | kebab-case目录名称 | 零售、金融服务、旅游和酒店业 |
| kebab-name | 图标的kebab-case用例名称 | 弃车，养铅 |
| 替换文本 | 字首大写，短 | 废弃的购物车，领导培养 |
| heading-anchor | 概述中的##标题的键用例 | 放弃的cart-email-recovery |
| 成熟度+类型 | 徽章语法 | `[!BADGE Foundational]{type=Neutral}`, `[!BADGE Emerging]{type=Informative}`, `[!BADGE Advanced]{type=Caution}` |

## 目录中的行业标签标记

目录文件使用此选项卡结构：

- `>[!TAB Retail]`
- `>[!TAB Automotive]`
- `>[!TAB Financial Services]`
- `>[!TAB Healthcare]`
- `>[!TAB Insurance]`
- `>[!TAB Media & Entertainment]`
- `>[!TAB Telecommunications]`
- `>[!TAB Travel & Hospitality]`
- `>[!TAB B2B]`

## 在选项卡中排序

行按成熟度级别排序：

1. **Foundation**&#x200B;行优先(type=Neutral)
2. **新增**&#x200B;行（类型=信息型）
3. 最后&#x200B;**高级**&#x200B;行（类型=警告）

在同一成熟度级别内，在该组的末尾添加新行。
