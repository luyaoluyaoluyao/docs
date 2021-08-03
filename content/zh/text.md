---
title: "文本"
parent: "普通小部件"
---


文本小部件显示可选包含参数的文本。 每个参数被替换为它提到的属性的值。 文本小部件是推荐向用户显示文本的方式。

{{% alert type="info" %}}

![](attachments/pages/text.png)

文本部件放置在数据视图中，显示给用户的问候消息。

{{% /报警 %}}

如果您开始在任何空容器中键入，Modeler将自动生成一个文本小部件以显示您的文本。

## 常规属性

### 文本模板

文本模板定义将显示的文本。 模板可以包含以数字写在括号之间的参数，例如 {1}。 第一个参数有数字1，第二个字符串。 注意，如果要使用模板参数，小部件必须放置在实体的上下文中 例如，在 [数据视图](data-view) 或 [列表视图](list-view) 中。

### 参数

对于模板中的每个参数，您定义了一个上下文实体或一个被引用的实体的属性，这些属性的值将插入到参数的位置。

### 渲染模式

渲染模式决定如何在网页浏览器中显示文本。

| 值    | 描述                                              |
| ---- | ----------------------------------------------- |
| 文本   | 文本将与页面上的上一个/下一个文本呈现为内嵌(HTML中的`<span>` 标签) |
| 第18段 | 文本将呈现为单独的一段(`<p>` 标签在 HTML)               |
| 标题1  | 文本将呈现为一个大标题(`<h1>` 标签在 HTML)              |
| ...  | ...                                             |
| 标题6  | 文本将呈现为一个小标题(`<h6>` 标签在 HTML)              |

_默认值：_ 文本

## 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Simple.md" %}}

## 共同属性

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}
