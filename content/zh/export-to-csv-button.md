---
title: "导出到 CSV 按钮"
parent: "控制栏"
---


此按钮允许最终用户将网格内容或参考设置选择器导出到CSV文件。 请注意通过搜索字段和排序的限制也将被导出。

csv 导出功能依赖于特定的数据检索方法。 因此，它只能在列表小部件中使用 XPath 数据源。

## 共同属性

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 格式化属性

### 小数分隔符

该字符串用来将分部分从浮动、货币和小数值中的整个部分分开。

_默认值：_。

### 分组分隔符

该字符串用来分隔大批数字的组数。

_默认值：_，

### 分隔符

用于在生成的 CSV 文件中分隔值的字符串。

_默认值：_;

## 常规属性

{{% snippet file="refguide7/Caption+Property.md" %}}

{{% snippet file="refguide7/Tooltip+Property.md" %}}

{{% snippet file="refguide7/Image+Property.md" %}}

{{% snippet file="refguide7/Button+Style+Property.md" %}}

{{% snippet file="refguide7/Is+default+buton+Property.md" %}}

### 最大行数

指示导出时数据网格中的最大行数。 有助于防止用户导出大量数据，可能会给服务器带来沉重的负荷。

### 生成 Excel 分隔符提示

如果为 true，则在 CSV 文件头中添加一个额外的行，通知Excel 是什么分隔符。 这解决了与 Excel 和本地化的兼容问题。

### 使用网格日期格式

如果为 true，则使用列的日期格式，否则使用 Excel 识别为日期的格式 (yyy-MM-dd)。

## 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Simple.md" %}}
