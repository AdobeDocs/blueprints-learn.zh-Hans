---
hold: true
title: 导入环境文件
description: 导入Postman环境文件，并设置整个bootcamp中的API调用所需的全局变量，如EDGE_REGION。
doc-type: article
solution: Experience Platform
exl-id: a5d45656-e3f5-4207-823c-ad33d4ef26a4
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# 导入环境文件

## 目标

在此页面上，您将导入Postman环境文件。  此文件包含大量全局变量，这些变量将用于您将在整个bootcamp中的其他实验室中进行的各种API调用。

## 导入环境文件

1. 下载&#x200B;**AJO Bootcamp.postman\_environment.json**&#x200B;文件：

下载文件 — [AJO Bootcamp.postman_environment.json](assets/ajo-bootcamp.postman_environment.json)

2. 在本地计算机上启动Postman。
3. 如有必要，请切换到您用于这些实验室的Workspace（如果您完全使用Workspace），然后单击&#x200B;**导入**&#x200B;按钮。

![Postman开始导入](assets/import-environment-file-click-import-button.png)

4. 将&#x200B;**AJO Bootcamp.postman\_environment.json**&#x200B;文件的本地URL粘贴到导入模式文本框中，或将其拖放到导入对话框中。  这应该会触发自动导入

![Postman导入对话框，其中显示用于通过URL粘贴文件URL的选项](assets/import-environment-file-import-button-overlay.png "Postman导入")

![Postman导入对话框接受通过拖放方式删除的文件](assets/import-environment-file-drag-and-drop-import.png "Postman通过拖放方式导入")

5. 导入后，单击左侧边栏中的&#x200B;**环境**&#x200B;选项卡以验证环境是否存在。 您会看到现在可以使用AJO Bootcamp环境。

![验证环境导入](assets/import-environment-file-validate-environment-imported.png)

## 设置环境变量

Postman专为测试和与API交互而设计。 但是，我们将其用于模拟来自浏览器的AEP Web SDK点击或服务器端实时数据收集调用。 虽然从最严格的意义上说，这些仍是API调用，但它们不是典型的API调用，需要标头中的授权令牌等。 这些实验室中的环境变量主要用于URL路径中的变量（标头中使用了变量）。

1. 如有必要，请单击Postman左侧边栏中的&#x200B;**环境**&#x200B;选项卡
2. 单击&#x200B;**AJO引导营**&#x200B;环境文件。 您会看到一些需要填写的值

![需要填写的具有空值的Postman环境变量](assets/import-environment-file-values-need-filling-in.png "验证环境中的邮递员变量")

3. 暂时跳过DATASTREAM\_CONFIG值。 您将在稍后的实验中创建数据流配置。
4. 使用最接近此引导营实际所在位置的区域代码更新&#x200B;**EDGE\_REGION**&#x200B;字段，并使用下表作为查找。

| **地区** | **地区代码** |
| ---------- | --------------- |
| 美国西部 | 或2 |
| 美国东部 | va6 |
| 欧洲 | irl1 |
| 澳大利亚 | 澳大利亚3 |
| 日本 | jpn3 |
| 亚洲 | spg3 |

完成后，您的环境文件应类似于以下内容：



![验证Postman区域变量](assets/import-environment-file-region-variable-set.png)

5. 您现在需要保存环境变量；但是，Postman UI中没有保存按钮。 使用Windows或Mac热键进行保存（例如，在Windows上按Ctrl+S）。 当您在Postman UI的右下角看到&#x200B;**保存的更改**&#x200B;消息时，您知道您的更改已保存：

![验证已保存的更改](assets/import-environment-file-changes-saved-confirmation.png)

>[!TIP]
>
>恭喜！ 您已完成Postman环境文件
