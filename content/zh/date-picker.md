---
title: "日期选择器"
parent: "输入小部件"
---

## 1 导言

日期选择器是一个 [输入小部件](input-widgets) ，可用来显示和编辑日期/时间属性。 它考虑到显示本地化日历的语言设置。

{{% alert type="info" %}}

![](attachments/pages/date-picker.png) 此日期选择器允许最终用户确定客户的出生日期。

{{% /报警 %}}

## 2 个一般属性

### 2.1 日期格式

日期格式决定日期选择器是否显示日期、时间、日期和时间，或关联属性的自定义变化。 这并不影响数据的储存方式；在所有情况下，日期和时间都将被记录。 它仅仅影响数据的显示方式。 日期和/或时间的格式取决于查看数据的用户的本地化。

这些是可能的价值：

* **日期** (这是默认)
* **时间**
* **日期和时间**
* **自定义** (详情见下面)

### 2.2 自定义日期格式

如果选择“自定义”作为日期格式(见上文)，此属性将决定如何格式化属性。 自定义日期格式是一个字符串，允许下面表格中的任何符号组合。 任何标点都将以字面形式呈现。

{{% snippet file="refguid7/Custom+Date+Format+Tokens.md" %}}

{{% alert type="info" %}}
即使一个具有自定义日期格式的日期选择器是可以编辑的(到 Mendix 7.21)。 ), 如果自定义格式不代表整个日期, 则不会显示日历下拉按钮(意思, 年 [`y`-`yyy`], 月 [`M`-`MMMM`], 月份或月份的日期 [`d`-`dd`] 标记缺少自定义格式中的标记。
{{% /报警 %}}

### 2.3 占位符文本

如果日期属性为空，则显示占位符文本。 它可以用来向最终用户说明预期的格式。 注意：如果本地日期选择器可用（例如，iOS 和 Android 4.0及以上版本），占位符文本将无法工作。

## 3 个验证属性

{{% snippet file="refguide7/Widget+Validation.md" %}}

## 4 数据源属性

{{% snippet file="refguide7/Attribute+Path+Property.md" %}}

{{% snippet file="refguid7/Label+Property.md" %}}

## 5 编辑属性

{{% snippet file="refguide7/Editable+Property.md" %}}

{{% snippet file="refguide7/Read+Only+Style.md" %}}

{{% snippet file="refguide7/Condition+Property.md" %}}

## 6 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Simple.md" %}}

## 7 个事件属性

{{% snippet file="refguide7/On+Change+Event.md" %}}

{{% snippet file="refguid7/On+Enter+event.md" %}}

{{% snippet file="refguide7/On+Leave+Event.md" %}}

## 8 个公共属性

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

{{% snippet file="refguide7/Tab+index+Property.md" %}}

## 9 阅读更多

*   [数据视图](data-view)
*   [属性](attributes)
