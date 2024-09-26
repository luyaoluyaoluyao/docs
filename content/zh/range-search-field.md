---
title: "范围搜索字段"
parent: "搜索栏"
---


给一个包含范围的实体，这个搜索字段用于查找范围与指定值相重叠的所有实体。

例子：给了一个实体“节日”，它有一个“开始”和一个“结束”日期，在X天是什么样的节日？

此搜索字段支持的数据类型为：Integer, Currency, Decimal, DateTime, Float, AutoNumber, Long。

您可以使用低和高绑定运营商指定范围边界是包含的还是排他的。

## 公共属性

{{% snippet file="refguid7/Search+Field+Caption+Property.md" %}}

{{% snippet file="refguid7/Search+Field+Type+Property.md" %}}

{{% snippet file="refguid7/Search+Field+Default+Value+Property.md" %}}

{{% snippet file="refguid7/Search+Field+Custom+Date+Format+Property.md" %}}

{{% snippet file="refguid7/Custom+Date+Format+Tokens.md" %}}

{{% snippet file="refguide7/Search+Field+Placeholder+Property.md" %}}

## 常规属性

### 下边框

此属性 (路径) 决定范围的下限。

### 下限操作符

下限操作员决定与下限的比较是否包含(>=) (>)。 它可以是“更大的”，也可以是“更大的或者平等的”。

_默认值_: 绿.

### 上边框

此属性 (路径) 决定范围的上限。

### 上边界运算符

上限的操作者决定与上限的比较是否兼容(<=) (<)。 它可以是“小人”，也可以是“小人和平等人”。

_默认值_: 较小的
