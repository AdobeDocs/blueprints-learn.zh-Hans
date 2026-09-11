---
title: 创建属性
description: 创建具有数据元素和规则的事件转发属性，以将传入体验事件转发到webhook端点。
doc-type: article
solution: Experience Platform
exl-id: eabd5f75-7706-4c96-982e-2512509bdc55
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 0%

---


# 创建属性

我们通常希望将Experience Event转发给第三方（不过没有必要这样做）。 当在特定情况下（例如，将购买事宜通知Google、Meta或TikTok）需要实时提供事件的副本以通知第三方时，通常使用此选项。

>[!NOTE]
>
>提醒：资产包含决定转发内容以及在何处转发内容所需的所有扩展、数据元素和规则

1. 在左边栏中，单击事件转发
2. 然后单击New Property

![突出显示“新建属性”按钮的事件转发部分](assets/create-property-new-property-button.png "创建新的事件转发属性")

3. 使用以下公式更新属性名称： `Event Forward Property SB + [sandbox number]`。 您的最终名称类似于：**事件转发属性SB01**

4. 完成后单击&#x200B;**保存**

![事件转发属性名称字段已填写并突出显示“保存”按钮](assets/create-property-name-property-form.png)

## 安装扩展

1. 单击刚刚创建的事件转发属性

![事件转发属性列表，其中新创建的属性突出显示](assets/create-property-open-new-property.png "打开您的事件属性")



2. 您应该会看到如下所示的屏幕。  单击&#x200B;**扩展**。

![事件转发属性概述屏幕，突出显示“扩展”选项卡](assets/create-property-click-extensions-tab.png)



3. 通过执行以下操作安装Adobe Cloud Connector扩展：

4. 单击顶部导航中的&#x200B;**目录**
5. 单击&#x200B;**Adobe Cloud Connector**&#x200B;卡
6. 在右边栏中，单击&#x200B;**安装**&#x200B;按钮

![带有Adobe Cloud Connector卡和安装按钮的扩展目录突出显示](assets/create-property-install-cloud-connector-extension.png)



单击install后，您应该会在资产的Installed扩展下看到该扩展，如下所示

![已安装的扩展列表显示Adobe Cloud Connector扩展已成功安装](assets/create-property-extension-installed-confirmation.png "完全安装的扩展")

## 创建数据元素

>[!NOTE]
>
>数据元素引用传入事件，并且可以根据需要将其解析为多个单独的组件

1. 在左边栏中，单击&#x200B;**数据元素**



![左侧边栏导航中突出显示了数据元素链接](assets/create-property-navigate-to-data-elements.png "导航到数据元素")



2. 单击&#x200B;**新建数据元素**&#x200B;按钮

显示“创建新数据元素”按钮的![数据元素页面](assets/create-property-create-new-data-element-button.png "创建新数据元素")



3. 使用以下信息配置新数据元素：

| 元素类型 | 要配置的值 |
| ----------------- | ------------------ |
| 名称 | 数据对象 |
| 扩展名 | 核心 |
| 数据元素类型 | 自定义代码 |

![设置了名称、扩展和数据元素类型字段的数据元素配置](assets/create-property-data-element-config-step-1.png "数据元素配置的步骤1")



4. 单击按钮&#x200B;**打开编辑器**&#x200B;以添加以下自定义代码：

![自定义代码的“打开编辑器”按钮突出显示的数据元素设置](assets/create-property-open-custom-code-editor.png "打开编辑器")



5. 将自定义代码添加到编辑器中（如这样）并保存

```none
var xdm = arc?.event || '';
return xdm;
```

![自定义代码编辑器，显示返回传入XDM事件对象的脚本](assets/create-property-custom-code-added.png "自定义代码")

>[!NOTE]
>
>这是在获取整个xdm对象时不会对有效负载进行任何转换。  如果需要，我们可以将XDM对象中的每个单独片段（例如页面名称、购买金额）解析为每个字段一个数据元素。  这样做的原因可能是将结构转换为不同的结构





6. 单击&#x200B;**保存**&#x200B;按钮以保存数据元素。

![突出显示了“保存”按钮的数据元素编辑器](assets/create-property-save-data-element-button.png)



完成后，您应该会看到以下屏幕，确认您的数据元素已添加：

![数据元素列表显示了添加到属性的新保存的数据元素](assets/create-property-data-element-saved-confirmation.png)


## 创建规则

>[!NOTE]
>
>规则包含：
>
>1. 转发条件
>2. 可转换有效负载并定义其发送位置的操作



1. 在左边栏中，单击&#x200B;**规则**

![突出显示了Rules链接的左边栏导航](assets/create-property-navigate-to-rules.png)



2. 然后单击&#x200B;**创建新规则**

显示“创建新规则”按钮的![规则页面](assets/create-property-new-rule-button.png)



3. 使用以下公式更新规则名称： `"EF Rule SB" + [your sandbox number]` （即EF规则SB01）。 您可以在浏览器窗口的右上角找到沙盒编号，如下所示\...

![浏览器窗口右上角显示规则名称中使用的沙盒编号](assets/create-property-sandbox-number-location.png)

4. 完成后单击&#x200B;**保存**

>[!NOTE]
>
>确保您的规则名称遵循`"EF Rule SB" + [sandbox number]`的公式模式

![以EF规则沙盒命名模式填写的规则名称字段](assets/create-property-add-rule-name.png "将名称添加到规则")



5. 通过单击(+)号向规则中添加操作以添加新操作

![突出显示加号图标的规则编辑器以添加新操作](assets/create-property-add-action-button.png "添加操作")

## 获取webhook URL（用于操作）

>[!NOTE]
>
>本实验在此处使用webhook，以便您查看数据是否已到达要发送到的目的地。 在现实场景中，您会登录到该目标，并使用其工具来查看哪些内容已到达。



1. 在浏览器的新选项卡中打开以下链接 — > [https://webhook.site](https://webhook.site/)
2. 复制您看到的唯一URL并将其保存在安全位置

![Webhook.site页面，该页面具有为复制而突出显示的唯一URL](assets/create-property-webhooksite-copy-url.png)



3. 使用以下信息配置您的操作：

| 设置 | 值 |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 扩展名 | Adobe云连接器 |
| 操作类型 | 进行Fetch调用 |
| 方法 | 帖子 |
| URL | 使用您在设置流目标时使用的相同webhook URL。 您可以在浏览器中打开新选项卡并导航到“目标” -> “浏览”找到它 |
| 正文 | 原始 |
| 正文数据 | \{ &quot;data&quot;： \{ &quot;event&quot;： &quot;\{\{数据对象\}\}&quot; } |

>[!NOTE]
>
>此处引用的\{\{Data Object\}\}是您之前创建的数据元素。 在此，下游系统的要求是要将事件封装在带有事件对象的数据对象中。 你可以把任何格式都放在这里。
>
>如果我们已将\{\{Data Object\}\}拆分为多个字段（例如页面名称、购买等），则可以转换JSON结构并将每个字段放置在所需的位置，以便在匹配目标方面赋予我们更多控制权。





完成验证后，您的屏幕类似于下图，然后单击&#x200B;**保留更改**

![使用Adobe Cloud Connector配置的规则操作进行提取调用设置和webhook URL](assets/create-property-configure-action-settings.png "配置操作")



4. 完成后，您应该会看到您的操作已添加到规则中。 单击&#x200B;**保存**&#x200B;以继续。

![规则编辑器显示已配置的操作，并突出显示“保存”按钮](assets/create-property-save-rule-button.png "保存您的规则")

>[!WARNING]
>
>发送体验事件时，发送的是事件，而不是用户档案，也不是其任何属性，包括任何受众资格（即使它是Edge受众）。
>
>这是出于速度目的。



## 发布更改

1. 在左边栏中，单击&#x200B;**发布流**

![突出显示发布流链接的左边栏导航](assets/create-property-navigate-to-publishing-flow.png "导航到发布流")



2. 单击“添加库”按钮&#x200B;****

![用“添加库”按钮突出显示的发布流页面](assets/create-property-add-library-button.png "添加库")



3. 使用以下信息配置库：

- 名称 — > **EF库**
- 环境 — > **开发**
- 单击&#x200B;**添加所有更改的资源**


完成后，您的屏幕应类似于下面的屏幕截图。  如果一切正常，请单击&#x200B;**保存并生成到开发**&#x200B;按钮

![具有名称、开发环境和保存并生成到开发按钮的库配置](assets/create-property-configure-library-save-and-build.png)



4. 然后，您应该会看到开发内部版本变为绿色，表明它已经可以使用

![发布流显示开发生成状态已变为绿色并可以使用](assets/create-property-development-build-ready.png)
