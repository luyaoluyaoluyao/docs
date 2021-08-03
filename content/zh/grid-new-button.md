---
title: "网格创建按钮"
parent: "控制栏"
---


**创建** 按钮允许用户在网格或参考设置选择器中创建新对象。

## 公共属性

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 数据源属性

### 实体

此属性决定此按钮应创建一个实例。 如果连接到网格或参考设置选择器的实体没有专业化， 页面生成器将自动为您设置此属性。 否则，您将不得不选择自己的专业。

{{% alert type="info" %}}

让我们说你有一辆实体车辆和两种专业，即自行车和汽车。 在车辆上的网格中，您必须为创建按钮指定车辆，自行车还是汽车。 您甚至可以有三个创建按钮，每个可能性都有一个。

{{% /报警 %}}

## 常规属性

{{% snippet file="refguide7/Caption+Property.md" %}}

{{% snippet file="refguide7/Tooltip+Property.md" %}}

{{% snippet file="refguide7/Image+Property.md" %}}

{{% snippet file="refguide7/Button+Style+Property.md" %}}

{{% snippet file="refguide7/Is+default+buton+Property.md" %}}

### 编辑位置

| 值      | 描述                                   |
| ------ | ------------------------------------ |
| 在顶部嵌入  | 新实例直接添加在网格顶部或参考设置选择器上，可以在网上编辑。       |
| 底部内联   | 新实例直接添加在网格底部或参考设置选择器上，可以在网上编辑。       |
| 在一个页面中 | 新实例已添加，可以在页面中编辑。 正在编辑此实例的页面可以用页面属性设置 |

_默认值：_ 在一个页面

### 页

如果编辑位置被设置为“在一个页面”，并且它指向最终用户点击此按钮时显示的页面，这个属性是相关的。 最终用户可以在保存之前使用此页面编辑新创建的对象。 此页面应包含一个连接到此网格或参考设置选择器的同一个实体的数据视图。

查看 [打开页面](opening-pages)。

## 可见性属性

{{% snippet file="refguide7/Visible+Property.md" %}}
