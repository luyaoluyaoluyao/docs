---
title: "一致性错误"
parent: "errors-pane"
menu_order: 10
description: "描述Mendix Studio Pro 中的一致性错误以及解决这些错误的方法。"
tags:
  - "Studio Pro"
  - "一致性错误"
  - "检查"
  - "错误"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/consistency-errors.pdf)。
{{% /报警 %}}

## 1 导言

为了确保您的应用始终一致且构建得当，Studio Pro 在构建您的应用时会检查是否一致。

当不符合一致性检查时，Studio Pro 将通过 [错误窗格](errors-pane) 的一致性错误通知您。 将突出强调页面、微流、域模型和文件模板中的错误：

![Errors Pane](attachments/consistency-errors/errors-pane.png)

如果您看不到 **错误** 面板，您可以从菜单选项 **查看 > 错误列表** 启用它。

为了让您能够快速找到您的错误，每个错误都会显示您：

* 错误唯一的 **错误代码**
* 描述错误的 **消息**
* 页面 **元素** 的名称导致错误
* 此元素所在的 **文档**
* 文档所在的 **模块**

双击错误将直接将您带到导致错误的元素。

需要解决错误才能部署您的应用程序。 Studio Pro的以下编辑器或功能可能出现一致性错误：

* [页 次](consistency-errors-pages)
* [Navigation](consistency-errors-navigation)
* [微型流动](微流)
* [域模型](域名模型)
* [集成](integration)
* [安全](安全)

## 2 次阅读更多

* [页面编辑器一致性错误](consistency-errors-pages)
* [导航一致性错误](consistency-errors-navigation)
* [Errors Pane](errors-pane)
* [页 次](页面)
* [微型流动](微流)
* [Mendix 导航](navigation)
