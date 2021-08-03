---
title: "布局网格"
parent: "容器部件"
---


布局网格是一个为您的页面提供结构的部件。 布局网格包含一个或多个行, 每个行包含一个至十二列. 每一列都有一个权重，一个从1到12之间的数值，一个列中的列的权重必须增加到12\。 在浏览器中，布局网格是由 Bootstrap 网格实现的。 Reading the official Bootstrap [documentation on the grid system](http://getbootstrap.com/css/#grid) can help you understand what you can build with this widget.

## ![](attachments/pages/layout-grid.png)

## 自动类

布局网格导出为嵌套的 div 元素。 除了您在各种类属性中指定的类外，还自动添加了一些类。

```
<div class="container-fluid">
  <div class="row">
    <div class="col-md-6"> ... </div>
    <div class="col-md-6"> ... </div>
  </div>
  ...
</div> 
```

最远的 `div` 表示整个小部件，并且得到以下类之一：

*   `当宽度设置为全宽时，容器液体`
*   `当宽度设置为固定宽度时，容器`

第二个 `div` 代表一行，并自动得到 `行` 类。 最内核的 `div` 代表一列，自动获得 `col-md-<weight>`

## 组件

### 行

布局网格包含一个或多个行。 每一行都可以使用类和样式属性样式。 行可以通过叫做“可视化”的属性有条件可见性。

反过来，每行都包含列，每行的列数可能不同。

### 列

布局网格中的一行包含一个或多个列。 每个列都可以使用类和样式属性样式。 此外，重量属性决定列的宽度。 行中所有列的权重必须添加到 12\。 有效行的例子是：

*   重量为12列
*   两列，均重量6
*   a 重量第3栏和重量第9栏。

几乎没有一个超过四列的用例。

## 公共属性

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 常规属性

### Width

此属性决定布局网格的宽度。

| 值    | 描述                                                        |
| ---- | --------------------------------------------------------- |
| 全宽度  | 布局网格跨越可用空间的全宽，将伸展和缩小。                                     |
| 固定宽度 | 布局网格有固定宽度，但它仍然响应视图变化。 请注意，宽度不可配置于Modeler，而是由 Bootstrap决定。 |

{{% alert type="warning" %}}

作为布局网格响应视图宽度，而不是其容器的宽度， 固定宽度布局网格只能用于顶级布局。

{{% /报警 %}}

## 可见性属性

{{% snippet file="refguide7/Visible+Property.md" %}}
