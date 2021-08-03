---
title: "文本框"
parent: "输入小部件"
---


文本框可以用于显示和/或编辑文本值。

{{% alert type="info" %}}

![](attachments/pages/text-box.png) 此文本框允许最终用户设置客户的名称。

{{% /报警 %}}

文本框必须放置在数据视图或模板网格中，并连接到类型字符串的属性。 已连接的属性以蓝色和文本框内方括号显示。

## 常规属性

{{% snippet file="refguide7/Numeric+Formating+Properties.md" %}}

### 以密码形式显示(仅针对字符串或哈希字符串类型的属性)

| 值  | 描述                                |
| -- | --------------------------------- |
| 错误 | 普通文本框                             |
| 真的 | 输入的字符不会显示给最终用户。 相反，每个类型的字符都会显示星号。 |

_默认值：_ False

### 输入蒙版 (仅在 Web 表单中)

输入掩码限制用户可以在文本框中输入的内容。 “9”表示任何数字，“Z”表示任何字母，“U”表示大写字母，“L”表示小写字母，“*”表示字母或数字。 其它字符将以字面表示。 例如，输入掩码99-LL-9999 匹配24-apr-2008。

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
