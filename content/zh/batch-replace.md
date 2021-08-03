---
title: "批量替换"
parent: "可翻译文本"
menu_order: 20
tags:
  - "studio pro"
  - "翻译"
  - "语言"
  - "可翻译文本"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/batch-replace.pdf)。
{{% /报警 %}}

## 1 导言

**批量替换** 适用于当前选中的语言，允许您用新语言替换任何现有文本。

您可能希望这样做有若干原因：

* 同一文本应该出现在应用的不同地方，但是输入不一致。 例如, 有时使用大写字母, 有时不使用 — 如果你在应用程序中重新使用现有文本, 这将提高用户体验
* 如果文本的所有出现都是相同的，你只需要输入一次翻译——这将节省时间并提高一致性。
* 如果您找到了一个共同标签或文本的更好的措辞，您可以用单个命令一次性更改所有的措辞。

![](attachments/language/batch-replace.png)

## 2 使用批量替换

批量替换当前选中语言的工作，因此您应该首先选择您想要使用的语言。 欲了解更多信息，请查看 [在目前选定的语言](translatable-texts#selected-language) 部分中的 *语言菜单* 中。

### 2.1 文件/模块

您可以选择一个或多个您想要用于批量翻译的模块。 例如，您可能想要忽略从默认语言导入的文本和系统模块。 或集中于将系统消息翻译成您选定的语言。

点击 **选择…** 并检查您想要运行的模块。

![模块选择屏幕](attachments/language/batch-replace-modules.png)

默认情况下将在应用程序中的所有模块上工作。

### 2.2 源文本包含

要搜索类似的短语，请输入您想要搜索的内容。

![批量翻译搜索](attachments/language/batch-replace-search.png)

默认情况下，将显示所选模块的所有可翻译文本。

每个找到的文本都会显示在 **文本** 列中。 **#** 列显示它在选定的模块中发生的次数。

如果您选择了一行， 您可以在 **显示情况** 部分查看 **对象** 中包含文本和 **文档** 的内容。 双击或点击 **显示事件** 会打开文档并选择对象，这样您就可以轻松看到上下文了。

{{% alert type="success" %}}
提示：将对话框移动到一边以更好地查看文档。
{{% /报警 %}}

### 2.3 替换为

在 **替换为**，请输入您想要使用的新文本代替现有文本。 点击 **替换** 以确认替换。

![](attachments/language/batch-replace-replace.png)

替代案文和原文将合并为一个条目。

![显示合并条目](attachments/language/batch-replace-replaced.png)

## 3 正在导出 & 导入文本

如果您想要翻译Studio Pro以外的语言，您可以导出可翻译文本到 Microsoft Excel (*)。 lsx*) 格式，进行更改，然后从更新的 Excel 文件中导入更改。

如果您正在多个应用上工作并且已经获得了文本，这将特别有用。 例如，您想要重新使用的系统模块。

### 3.1 出口到Excel

点击 **导出到 Excel…** 将当前显示的文本项导出到Microsoft Excel (*.xlsx*) 格式文件。

文件的格式如下所示：

![Excel文件示例](attachments/language/batch-replace-excel.png)

**第1行** - *过滤：* 表示已导出文件中包含的模块。

**行 2**  — 表示语言。 第一列是当前文本，第二列是 *替换为* 文本。

**行 3+**  - 显示当前文本

如果文件被导入，您可以对B列进行更改。

### 3.2 从Excel 导入

点击 **从 Excel…** 导入正确构建的 Microsoft Excel (*.xlsx*) 格式文件。

这种做法如下：

* 选定的模块在 *筛选器中设置为这些模块：* 行文件
* B栏中空的文本将被忽略
* A栏中与所选模块中可翻译文本不匹配的任何文本将被忽略
* B列中没有被忽略的任何文本都输入 **替换为** 列

只有点击 **替换** 才能进行更改。

{{% alert type="warning" %}}
批量替换和批量翻译的 Excel 文件格式相似。 如果您试图导入批量翻译文件或批量替换文件的语言错误，但如果您忽略警告，您仍然可以导入该文件。
{{% /报警 %}}
