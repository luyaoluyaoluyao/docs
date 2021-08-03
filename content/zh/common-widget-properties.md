---
title: "常见小部件属性"
parent: "普通小部件"
---

这些是许多小部件共享的属性。 完整的属性列表，查看相关部件。

## 行为属性

### 需要(仅在网页格式中)

此属性表示此部件是否必须由最终用户填写。 如果设置为 true，此部件不能留空，如果最终用户按“保存”按钮，将显示一条消息。

_默认值：_ False

### 需要的消息 (仅在网页形式中)

此属性决定了在部件为空且设置为真的“必填”属性时向终端用户显示的消息。 这是一个可翻译的文本。 查看 [可翻译文本](translatable-texts)。

{{% alert type="info" %}}

例如，如果地址字段是必需的。 地址文本框所需的消息可以是像“地址是必需的”

{{% /报警 %}}

## 公共属性 {#common-properties}

### 标签索引(仅以网页形式)

标签索引影响最终用户使用标签键通过表单导航的顺序。 默认标签索引为零，标签顺序由客户系统自动确定。 减一个(-1)的值意味着当触摸表单时将跳过小部件。

_默认值：_ 0

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 数据源属性

{{% snippet file="refguide7/Attribute+Path+Property.md" %}}

## 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Simple.md" %}}

## 编辑属性

{{% snippet file="refguide7/Editable+Property.md" %}}

### 条件

可以根据附件数据视图的属性值编辑部件。 属性必须是布尔值或枚举的类型。 对于每个值，您指定部件是否可以编辑。 当输入表单和更改条件属性时，将更新小部件的编辑状态。

例如：如果最终用户表示他或她没有结婚，你不必询问结婚日期。
