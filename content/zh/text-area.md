---
title: "文本区域"
parent: "输入小部件"
---


文本区域可以用于显示和/或编辑一个长文本值，可以拆分到几行。

{{% alert type="info" %}}

![](attachments/pages/text-area.png)

此文本区域允许最终用户设置产品描述。

{{% /报警 %}}

文本区域必须放置在数据视图或模板网格中，并连接到类型字符串的属性。 已连接的属性用蓝色和文本区域内括号显示。

## 常规属性

### 自动缩放

这个属性决定了文本区域是否自动增长取决于其中的文本数量。

_默认值：_ 否

### 行数

行数决定文本区域同时显示多少行。 如果文本区域的文本包含更多的行，您将需要使用滚动条来查看所有。 这个属性仅在自动放大后才显示

_默认值：_ 5

### 计数器消息

这是在文本区域输入时显示的文本。 这个文本有两个占位符。 第一个占位符显示已经输入的字符数，第二个占位符显示最大字符数。

{{% alert type="info" %}}

您已经使用了 {1} 个允许字符的 {2} 个字符。

{{% /报警 %}}

### 文本太长消息

当输入的字符数高于允许的最大字符数时，这是显示的文本。

### 最大长度

此属性表示可以在此文本框中输入的最大字符数。

| 值    | 描述                 |
| ---- | ------------------ |
| 属性长度 | 最大字符数与连接属性的最大长度相同。 |
| 无限制  | 最大字符数是无限的。         |
| 自定义  | 最大字符数由用户设定。        |

_默认值：属性长度_

### 占位符文本

当尚未输入文本时，将显示占位符文本。 它可以用来向用户提示应输入哪种文本。

## 验证属性

{{% snippet file="refguide7/Widget+Validation.md" %}}

## 数据源属性

{{% snippet file="refguide7/Attribute+Path+Property.md" %}}

{{% snippet file="refguid7/Label+Property.md" %}}

## 编辑属性

{{% snippet file="refguide7/Editable+Property.md" %}}

{{% snippet file="refguide7/Read+Only+Style.md" %}}

{{% snippet file="refguide7/Condition+Property.md" %}}

## 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Simple.md" %}}

## 事件属性

{{% snippet file="refguide7/On+Change+Event.md" %}}

{{% snippet file="refguid7/On+Enter+event.md" %}}

{{% snippet file="refguide7/On+Leave+Event.md" %}}

## 公共属性

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

{{% snippet file="refguide7/Tab+index+Property.md" %}}

## 阅读更多

*   [数据视图](data-view)
*   [属性](attributes)
