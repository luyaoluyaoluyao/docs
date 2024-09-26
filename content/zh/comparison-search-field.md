---
title: "比较搜索字段"
parent: "搜索栏"
---


## 公共属性

{{% snippet file="refguid7/Search+Field+Caption+Property.md" %}}

{{% snippet file="refguid7/Search+Field+Type+Property.md" %}}

{{% snippet file="refguid7/Search+Field+Default+Value+Property.md" %}}

{{% snippet file="refguid7/Search+Field+Custom+Date+Format+Property.md" %}}

{{% snippet file="refguid7/Custom+Date+Format+Tokens.md" %}}

{{% snippet file="refguide7/Search+Field+Placeholder+Property.md" %}}

## 常规属性

{{% snippet file="refguid7/Search+Field+Attribute+Path+Property.md" %}}

{{% snippet file="refguide7/Search+Field+Comparison+Property.md" %}}

### 日期比较和默认值的影响

使用平等来搜索日期属性是可能的。 时间组件属于日期时发生的情况取决于比较搜索字段的默认值。

| 默认值                   | 搜索查询                                  |  | 结果示例 (输入：8月4日, 2100)                           |
| --------------------- | ------------------------------------- |  | ---------------------------------------------- |
| 无                     | 搜索字段为空。 表示从指定日期午夜开始的24小时日期范围。         |  | 搜索8月4日0:00 - 8月5日0:00                          |
| [%CurrentDateTime%]   | 搜索字段显示当前日期。 表示从 _当前时间_ 开始的 24 小时日期范围。 |  | 在8月4日之间搜索 <current time> 和8月5日， <current time> |
| [%BeginOfCurrentDay%] | 搜索字段显示当前日期。 表示从指定日期午夜开始的24小时日期范围。     |  | 搜索8月4日0:00 - 8月5日0:00                          |
