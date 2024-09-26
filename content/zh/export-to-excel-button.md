---
title: "导出到Excel按钮"
parent: "控制栏"
---


此按钮允许最终用户将网格内容或参考设置选择器导出到excel文件。 请注意通过搜索字段和排序的限制也将被导出。

Excel导出功能依赖于特定的数据检索方法。 因此，它只能在列表小部件中使用 XPath 数据源。

## 共同属性

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 常规属性

{{% snippet file="refguide7/Caption+Property.md" %}}

{{% snippet file="refguide7/Tooltip+Property.md" %}}

{{% snippet file="refguide7/Image+Property.md" %}}

{{% snippet file="refguide7/Button+Style+Property.md" %}}

{{% snippet file="refguide7/Is+default+buton+Property.md" %}}

### 最大行数

指示导出时数据网格中的最大行数。 有助于防止用户导出大量数据，可能会给服务器带来沉重的负荷。

### 日期导出格式

定义如何导出日期。 当选择 _日期值_ 时，日期值将被导出为实际日期， 这样可以使用 Excel 日期函数，如排序。 当选择 _文本_ 时，日期值将按数据网格中显示的方式导出。

_默认值：_ 日期值

{{% alert type="warning" %}}

选择 _日期值_时，日期将只显示在您的 Windows 账户的时区。 因为Excel不支持定义特定时区。

{{% /报警 %}}

## 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Simple.md" %}}
