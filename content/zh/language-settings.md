---
title: "语言设置"
parent: "可翻译文本"
menu_order: 10
tags:
  - "studio pro"
  - "翻译"
  - "语言"
  - "可翻译文本"
  - "添加语言"
  - "日期格式"
  - "完整性"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/language-settings.pdf)。
{{% /报警 %}}

## 1 导言

Mendix 设计成供用户用多种语言使用。 **项目设置 **语言** 标签，** 允许您选择应用程序将支持哪种语言。

![](attachments/language/01_project_settings.png)

您可以通过以下两种方式到达此选项卡：

1. 选择菜单选项 **语言 > 语言设置…**
2. 打开 **项目 {Name} > 设置** 来自 [工程资源管理器的对话框](project-explorer) 并选择 **语言** 选项卡。

## 2 设置默认语言

必须有默认的应用语言。 从下拉列表中选择 **默认语言**。 这将包含已添加到您的应用程序的所有语言。 建议您在开始开发您的应用时这样做。

设置默认语言有两个函数：

* 它设定了在最终用户与语文实体没有联系的情况下向最终用户展示的语言。 或者如果最终用户的语言未在应用程序中启用
* 它设定了在最终用户语言中没有翻译文本时将使用的语言。 即使应用程序已启用语言

初始默认语言是 *英语、美国*。

## 3 正在添加应用语言

您可以通过点击 **添加**来从支持的语言列表中添加尽可能多的语言 选择所需的语言，并单击 **确定**

![](attachments/language/add-language.png)

大多数语言都将添加空字典，尽管荷兰词典中已经有一些翻译。

## 4 高级语言设置{#advanced}

您可以在您的应用中设置每种语言来设置其他设置。

![编辑语言](attachments/language/edit-language.png)

### 4.1 检查完整性

如果您检查 **完整性** box, 对于在这种语言字典中没有条目的每个文本，您将在 [错误窗格](errors-pane) 中获得警告(或错误)。

如果这是默认语言， **将选中完整性** 复选框，您将无法取消选中它。

### 4.2 自定义日期和时间格式

您可以为以下设置一个自定义格式：

* **日期格式**
* **时间格式**
* **日期和时间格式**

在相关框中输入一个格式字符串，您将看到一个如何在下方格式化日期的示例。

点击 **编辑…** 打开一个对话框，为格式字符串提供完整引用：

![日期编辑对话框](attachments/language/date-format.png)
