---
title: "动态标签 (文档模板)"
parent: "文档模板"
aliases:
  - /refguid7/Dynamic+label+(document+template).html
  - /refguide7/dynamic-label-(document-template).html
---


一个动态标签将用于与表单生成器的文本框相同类型的属性。 它可以用来显示文本值。

{{% alert type="info" %}}

![](attachments/819203/918131.png) 链接到客户名称的动态标签。

{{% /报警 %}}

## 外观属性

### 样式

查看 [样式](style)

### 渲染XHTML

如果您设置属性为“渲染XHTML”为true， 连接到此标签的属性被假定为包含 XHTML 并将以此形式呈现。 当您想要在文档模板中包含富文本时，这是有用的。 此属性只适用于类型字符串属性。

内容MUST 是有效的 XHTML 渲染，不存在错误。

_默认值：_ False

### 十进制精度(仅适用于 十进制属性)

值的精确度由用来表示该值的数字数来界定。 此属性表示小数点后的小数点数（小数点后的数字数）将会在小部件中呈现。

_默认值：_ 2

### 组数字 (仅限数字属性)

为了便于阅读，小数点分隔符前面有许多数字的数字可以用分隔符分成组。 此属性定义最终用户是否会看到这些组。

_默认值：_ False

### 日期格式 (仅限日期时间类型的属性)

日期格式决定是否显示日期部分、时间部分或两者。 日期和时间部件的格式取决于用户使用应用程序的本地化。 或者，到2.5.3版本，您可以通过提供日期格式字符串来完全自定义日期和/或时间的格式。

可能的值: '日期', '时间', '日期和时间', 和 2.5.3 '自定义'

_默认值：_ 日期

### 自定义日期格式 (仅限日期时间类型的属性)

如果选择“自定义”作为日期格式(见上文)，自定义日期格式决定日期和/或时间格式. 自定义日期格式是一个遵循 [http://download.oracle.com/javase/6/docs/api/java/text/SimpleDateFormat.html](http://download.oracle.com/javase/6/docs/api/java/text/SimpleDateFormat.html) 中描述的规则的字符串。

{{% alert type="info" %}}

自定义日期格式 `EEEE, MMM d, yy` 导致以下文本 `Wed, Jol 4, 01`

{{% /报警 %}}

## 公共属性

{{% snippet file="refguide7/Name+Property.md" %}}

## 数据源属性

### 属性(路径)

属性(路径)属性指定在动态标签中显示哪个属性。
