---
title: "文本"
parent: "页面编辑器部件"
description: "描述Mendix Studio中的印刷小部件。"
menu_order: 40
tags:
  - "工作室"
  - "页面编辑器"
  - "排版"
  - "文本部件"
  - "小部件"
---

## 1 导言

文本是一组 [小部件](page-editor-widgets) ，由 [文本，段落，标题(H1-H6)](#text-widget)和 [页面标题](#page-title-widget) 组成。 它们用于向最终用户显示文本信息。 例如，您可以显示文本段落：

{{% image_container width="350" %}}![](attachments/page-editor-widgets-text/paragraph-example.png)
{{% /image_container %}}

## 2 文本、段落和标题一般属性 {#text-widget}

您可以使用 **文本**, **段落**, 或 **标题** 小部件向最终用户显示文本。 在 **属性** > **常规**中，您可以输入将显示的文本， 定义是否包含属性值，并设置 [渲染模式](#render-mode)。

### 2.1 内容 {#content}

在 **内容**中，您定义了显示给最终用户的文本。 您也可以在这里显示动态数据：属性值和表达式结果。

当添加属性时，属性值将显示给用户。 选择 **添加** > **属性** 或按 <kbd>Ctrl</kbd> + <kbd>空格</kbd> 来选择属性。  例如，当用户登录到帐户时，可以显示问候消息， *name* and *NumberOfmail* 是属性值：

![](attachments/page-editor-widgets-text/content-example.png)

您也可以配置表达式并显示表达式结果(关于表达式的更多信息，请参阅 [表达式](expressions))。 选择 **添加** > **表达式结果** 以写一个表达式。 例如，您可以显示一个不含增值税的价格，并包含它：

![内容示例表达式](attachments/page-editor-widgets-text/content-example-expression.png)

要编辑 **内容**, 双击页面上的小部件。


### 2.2 渲染模式 {#render-mode}

渲染模式定义了文本向最终用户显示的方式。 基本上， **文本**, **paragraph**, 和 **标题** 小部件是同一部件的不同渲染模式。 渲染模式的可能值见下表。

| 值     | 描述                            |
| ----- | ----------------------------- |
| 文本    | 文本将与页面上的上一个/下一个小部件内嵌渲染。       |
| 第18段  | 案文将作为单独一段                     |
| H1-H6 | 案文将作为标题编排。 H1是最大的标题，H6是最小的标题。 |

## 3 页标题通用属性 {#page-title-widget}

页面标题小部件设置当前页面的标题并显示它。 此标题也作为页面标题出现在您的浏览器标签页。  标题将显示在 **主题定制器** 的 **H1** 风格中。 欲了解详情，请参阅 [主题定制器](theme-customizer)。

如果你想要更改页面的名字，请执行以下操作：

1. Open **Properties** of the widget > the **General** section.
2. 更改 **标题** 字段中的名称。

页面标题已更改。

您在页面属性和小部件中看到的 **标题** 是相同的。 这意味着，如果您更改页面属性中的标题，此更改将显示在小部件中，反之亦然。

![](attachments/page-editor-widgets-text/page-title-interrelation.png)



{{% alert type="info" %}}

您可以在您的页面上放置几个 **标题** 小部件，但它们都会显示相同的文本，不能单独编辑。

{{% /报警 %}}

## 4 条件可见性部分

{{% snippet file="studo/visibility-section-link.md" %}}

## 5 设计科 {#input-elements-design}

关于 **设计** 部分及其属性的信息，请参阅 [设计部分](page-editor-widgets-design-section)。

## 6 阅读更多

* [页 次](page-editor)
* [小部件](页面编辑器部件)
