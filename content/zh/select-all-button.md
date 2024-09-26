---
title: "选择所有按钮"
parent: "控制栏"
---

选择所有按钮允许最终用户在网格中选择所有对象，或参考设置选择器。 使用选择类型属性，您可以确定此按钮是否应该选择当前页面上的对象，或者选择所有页面上的对象。

## 公共属性

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 常规属性

{{% snippet file="refguide7/Caption+Property.md" %}}

{{% snippet file="refguide7/Tooltip+Property.md" %}}

{{% snippet file="refguide7/Image+Property.md" %}}

{{% snippet file="refguide7/Button+Style+Property.md" %}}

{{% snippet file="refguide7/Is+default+buton+Property.md" %}}

### 选择类型

| 值    | 描述                  |
| ---- | ------------------- |
| 选择页面 | 点击此按钮可选择当前页面上的所有对象。 |
| 选择所有 | 点击此按钮选择所有对象。        |

{{% alert type="warning" %}}

由于技术限制，选择类型“全选”的按钮不能与删除、删除或选择按钮合并。 编辑按钮总是表现为选择类型为“选择页” 不论用于选择对象的“选择全部”按钮的实际设置。

{{% /报警 %}}

_默认值：_ 选择页面

## 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Simple.md" %}}
