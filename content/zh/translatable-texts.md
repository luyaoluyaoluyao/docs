---
title: "语言菜单"
parent: "menus"
menu_order: 50
tags:
  - "studio pro"
  - "翻译"
  - "语言"
  - "可翻译文本"
---

## 1 导言

Mendix 的设计是为了便于向有不同语言要求的用户提供相同的信息。 为了支持这一点，向最终用户提交的所有案文都可以翻译成不同的语文。

这些 *可翻译文本* 包含以下内容：

* [按钮](button-widgets) 标题
* [数据网格](data-grid) 列
* [标签](标签)
* [菜单项](menu#menu-item)
* [消息](show-message) 来自 [微流](microflows)
* [文本](文本)

## 2 在当前选中的语言{#selected-language} 中工作

您可以看到当前在屏幕右下方工作的语言。

{{% image_container width="350" %}}

![语言状态](attachments/language/language-status.png)

{{% /image_container %}}

当您在应用中设置多种语言时，您可以选择一种语言，进行以下操作：

* 从 **语言 > 当前语言** 菜单中选择它
* 在Studio Pro的主窗口右下角使用下拉列表
* 使用 <kbd>Ctrl</kbd>+<kbd>L</kbd> 或 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>L</kbd> 键盘快捷键组合， 通过配置语言的生理周期

当使用非默认语言时，您可以识别尚未翻译的文本。 这些显示方括号之间的默认文本。 例如， `<Name>`。 您可以用适当的翻译替换文本，它将被替换为当前选中的语言。

如果您编辑您的应用以添加新的小部件而不是默认语言， 这些部件的任何可翻译文本都将添加到当前语言中。 默认语言中的文本将留空，或者为小部件提供占位符文本。

所有未翻译文本将在您运行应用程序时以默认语言显示。

{{% alert type="info" %}}
如果缺少默认语言文本，最终用户将会看到 `[没有翻译]`。 如果您希望文本为空，请将默认语言文本设置为空格而不是空格。
{{% /报警 %}}

## 3 语言菜单

**语言** 菜单允许您管理其他语言和您的应用的翻译。 这包括一些功能，可以帮助您翻译所有地方的文本，只需单独更改，而无需单独更改每个事件：

![语言菜单](attachments/language/language-menu.png)


### 3.1 菜单项概览

下面的表格描述了 **语言** 菜单项：

| 菜单项                          | 描述                          | 快捷键                                               |
| ---------------------------- | --------------------------- | ------------------------------------------------- |
| **当前语言**                     | 从 **语言设置中设置的一种语言中选择当前语言…**  | *无*                                               |
| **选择上一种语言**                  | 在 **语言设置中选择的语言列表中选择上一种语言…** | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>L</kbd> |
| **选择下一个语言**                  | 在 **语言设置中选择的语言列表中选择下一种语言…** | <kbd>Ctrl</kbd> + <kbd>L</kbd>                    |
| [语言设置…](language-settings)   | 选择应用支持哪种语言，并配置日期和时间设置。      | *无*                                               |
| [批量替换…](batch-replace)       | 更改所有选定的可翻译文本在当前语言相同的地方。     | *无*                                               |
| [批量翻译…](batch-translate)     | 添加和编辑所选源语言的翻译到所选目标语言        | *无*                                               |
| [语言操作…](language-operations) | 操作语言之间的翻译 (例如复制)            | *无*                                               |

## 4 设置最终用户语言

显示给最终用户的语言是由 **语言** 对象决定的，它与 **用户** 对象通过关联的当前最终用户 **用户语言** 相关联。

如果相关的语言不是应用程序中设置的语言之一，那么最终用户将看到默认语言的页面。

如果最终用户与某一语言无关，例如他们是匿名用户， 使用的语言取决于用户的浏览器或操作系统设置。 如果所请求的语言没有出现在应用中，则应用的默认语言将被使用。 3. 请求使用的语文如下：

* 适用于 web 应用 - 根据浏览器偏好的语言顺序在应用程序中匹配语言集的第一种语言
* 为移动应用程序——操作系统语言

![用户和语言的系统域模型](attachments/language/user-language-domain-model.png)

如果您允许最终用户更改应用程序中的显示语言，更改将不会立即应用。 这是因为应用程序的可翻译文本已经设置为最终用户的原始语言。

有两种选择来确保语言被更改：

1. 请最终用户手动操作
    * 登出并重新登录
    * 使用浏览器的刷新命令
2. 强制Mendix 重新加载页面 - 例如:
    1. 在您的应用中添加支持的部件 [HTML / JavaScript 代码片段](https://marketplace.mendix.com/link/component/56/)。
    2. 创建弹出页面。
    3. 将HTMLSnippet 小部件放置在弹出页面上。
    4. 添加 **JavaScript** 内容 `mx.reloadWidState();` 到小部件。
    5. 当您想要切换用户语言时，从微流中打开您的新弹出页面。

    ![用户和语言的系统域模型](attachments/language/reload-with-state.png)

{{% alert type="info" %}}
The above only applies to pages *within* your Mendix application (meaning, pages that are created in Studio Pro). 静态页面的标签(例如 *index.html* 和 *登录。 当您使用应用程序的默认语言创建部署包时，将生成tml* 主题 **中的页面** 文件夹。 这些页面上的标签对于不同的用户不会改变，它们将永远是相同的。
{{% /报警 %}}

## 5 阅读更多

* [如何翻译您的应用内容](/howto/collaboration-requirements-management/translate-your-app-content) -- 一个添加翻译的工作示例
* [如何使用可翻译验证消息](/howto/logic-business-rules/translatable-validation-messages)
* [通过点击链接](https://forum.mendixcloud.com/link/questions/91821) 来更改语言——在 Mendix 论坛上的解释和想法以便在语言被更改时刷新页面
* [匿名用户外观](https://forum.mendixcloud.com/link/questions/91676) — — 在Mendix 论坛上讨论为匿名最终用户切换语言问题
