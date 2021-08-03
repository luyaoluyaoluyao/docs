---
title: "编辑按钮"
parent: "控制栏"
---

{{% alert type="info" %}}

此按钮已在 Mendix 7.17中删除。 使用普通的 [动作按钮](action-button) **显示页面** 动作代替。

{{% /报警 %}}

编辑按钮允许用户编辑或查看在网格或参考设置选择器中选择的对象。

## 共同属性

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 常规属性

{{% snippet file="refguide7/Caption+Property.md" %}}

{{% snippet file="refguide7/Tooltip+Property.md" %}}

{{% snippet file="refguide7/Image+Property.md" %}}

{{% snippet file="refguide7/Button+Style+Property.md" %}}

{{% snippet file="refguide7/Is+default+buton+Property.md" %}}

### 页

此属性指向最终用户点击此按钮时显示的页面。 最终用户可以使用此页面来编辑选定的对象。 此页面应包含一个连接到与网格相同的实体或参考集选择器的数据视图。

查看 [打开页面](opening-pages)。

### 专业化页面

如果连接到网格或参考设置选择器的实体有专业化，您可以选择为每个专业指定页面。 当您编辑数据网格中的一行时，将打开最特定的页面。 对于每个专业，您指定了打开页面，在哪里打开，以及页面的标题。

{{% alert type="info" %}}

让我们说你有一辆实体车辆及其两种专业：自行车和汽车。 还有称作运动车的汽车专业化。 您创建了一个连接到车辆的数据网格。 使用数据网格的页面属性，您可以指定任意车辆打开哪个页面。 对于专业自行车和汽车，您创建单独的页面来编辑它们。 如果您现在编辑一行类型自行车，将打开专为自行车设计的页面。 如果您编辑了汽车，您可以获得汽车页面。 如果您编辑了一个运动车，汽车页面将被打开！ 体育车没有专门的页面(这个例子)，汽车是有一个页面的“最接近”的概括。

{{% /报警 %}}

## 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Extened.md" %}}
