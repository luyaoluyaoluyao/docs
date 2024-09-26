---
title: "动态标签 (文档模板)"
parent: "文档模板"
tags:
  - "studio pro"
aliases:
  - /refguid8/Dynamic+label+(document+template).html
  - /refguide8/dynamic-label-(document-template).html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/dynamic-label-document-template.pdf)。
{{% /报警 %}}

## 1 导言

动态标签用于与页面编辑器的文本框相同的属性。 它可以用来显示文本值。

{{% alert type="info" %}}

![](attachments/document-templates/918131.png)

链接到客户名称的动态标签。

{{% /报警 %}}

## 2 外观属性

### 2.1 样式

欲了解详情，请见 [样式](style)。

### 2.2 渲染XHTML

如果您设置属性为“渲染XHTML”为true， 连接到此标签的属性被假定为包含 XHTML 并将以此形式呈现。 当您想要在文档模板中包含富文本时，这是有用的。 此属性只适用于类型字符串属性。

内容MUST 是有效的 XHTML 渲染，不存在错误。

默认： *False*

### 2.3 十进制精度(仅适用于十进制属性)

值的精确度由用来表示该值的数字数来界定。 此属性表示小数点后的小数点数（小数点后的数字数）将会在小部件中呈现。

默认： *2*

### 2.4 组数字 (仅限数字属性)

为了便于阅读，小数点分隔符前面有许多数字的数字可以用分隔符分成组。 这种财产确定最终用户是否会看到这些团体。

默认： *False*

### 2.5 日期格式 (仅针对类型 **日期和时间** 的属性)

日期格式决定是否显示日期部分、时间部分或两者。 日期和时间部件的格式取决于用户使用应用程序的本地化。

这些是可能的价值：

* **日期** *(默认)*
* **时间**
* **日期和时间**
* **自定义** (详情见下面)

### 2.6 自定义日期格式 (仅针对类型 **日期和时间** 的属性)

如果您选择 **自定义** 作为日期格式(见上文)，此属性将决定如何格式化属性。 自定义日期格式是一个字符串，允许下面表格中的任何符号组合。 任何标点都将以字面形式呈现。

{{% snippet file="refguide8/custom-date-form-tokens.md" %}}

## 3 个公共属性

{{% snippet file="refguide8/name-property.md" %}}

## 4 数据源属性

### 4.1 属性(路径)

属性(路径)属性指定在动态标签中显示哪个属性。
