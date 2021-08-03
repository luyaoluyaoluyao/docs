---
title: "布局网格"
parent: "容器部件"
menu_order: 10
tags:
  - "studio pro"
  - "布局网格"
  - "容器部件"
  - "列"
  - "行"
  - "网格"
  - "布局"
---

## 1 导言

布局网格是一个为您的页面提供结构的部件。

布局网格由 [行](#rows) 和 [列](#columns) 组成： ![布局网格示例](attachments/container-widgets/layout-grid.png)

在浏览器中，布局网格基于 Bootstrap 网格系统。 关于Bootstrap 网格系统的更多信息，请参阅 [官方Bootstrap 文档](http://getbootstrap.com/css/#grid)。

{{% alert type="info" %}}

如果您的应用有 [Atlas UI 资源](/appstore/modules/atlas-ui-resources) 版本2.4.0 或以上, 下面描述的行和列属性是可用的。

关于行和列属性的更多信息，请参阅 [行及其属性](#rows) 和 [列及其属性](#columns) 部分。

{{% /报警 %}}

## 2 布局网格属性

下面的图像是布局网格属性的示例：

{{% image_container width="250" %}}![布局网格属性](attachments/container-widgets/layout-grid-properties.png)
{{% /image_container %}}

布局网格属性由以下部分组成：

* [常用的](#common)
* [设计属性](#design-properties)
* [A. 概况](#general)
* [可见性](#visibility)

### 2.1 共同部分 {#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 设计属性部分{#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.3 一般部分 {#general}

#### 2.3.1 Width

**常规** 部分包含 **宽度** 属性，它决定了布局网格的宽度。

| 值    | 描述                                                             |
| ---- | -------------------------------------------------------------- |
| 全宽度  | 布局网格跨越可用空间的全宽，将伸展和缩小。                                          |
| 固定宽度 | 布局网格有固定宽度，但它仍然响应视图变化。 请注意，宽度在 Studio Pro 中不可配置，但由 Bootstrap决定。 |

{{% alert type="warning" %}}

作为布局网格响应视图宽度，而不是其容器的宽度， 固定宽度布局网格只能用于顶级布局。

{{% /报警 %}}

### 2.4 可见性科 {#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 行及其属性 {#rows}

布局网格可以包含一个或多个行。 每行包含 [列](#columns) ，每行的列数可能不同。

下面的图像是布局网格行属性的示例：

{{% image_container width="300" %}}![行属性](attachments/container-widgets/row-properties.png)
{{% /image_container %}}

行属性由以下部分组成：

* [常用的](#row-common)
* [A. 概况](#row-general)
* [可见性](#row-visibility)

### 3.1 共同部分 {#row-common}

{{% snippet file="refguide/common-section-link.md" %}}

### 3.2 一般部分 {#row-general}

行的 **常规** 部分包含以下属性：

* **列** - 设置列中的列数

* **垂直对齐列** - 此属性垂直对齐所有列的垂直对齐。 您可以选择以下选项：

  * **未设置** - 对齐方式未设置

  * **顶部** — — 列对齐到布局格的顶端

  * **居中** — 列对齐到布局网格的中心

  * **底部** - 列对齐到布局格底端

●{% alert type="info" %}}这个设置可以被单独列的 **垂直对齐** 设置所覆盖。
{{% /报警 %}}

* **列之间的间距** - 当设置为 *是*时，增加列之间的间距

### 3.3 可见性部分 {#row-visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 4列及其属性 {#columns}

列组成布局网格的一行。

 下面的图像是布局网格列属性的示例：

{{% image_container width="300" %}}
![列属性](attachments/container-widgets/column-properties.png)
{{% /image_container %}}

布局网格列属性由以下部分组成：

* [常用的](#column-common)
* [A. 概况](#column-general)

### 4.1 共同部分 {#column-common}

{{% snippet file="refguide/common-section-link.md" %}}

### 4.2 一般科 {#column-general}

#### 4.2.1 **Width** {#column-width}

此属性允许您定义列宽度。

对于 *web* 页面，它被分成 **桌面宽度**, **平板宽度**, nd **电话宽** 允许您定义每个设备类型的列宽度。

对于 *原生* 页面，您将看到一个名为 **宽度** 的属性。

**宽度** 属性包含以下选项：

* **自动填充** — — 需要一个列的可用空间 (例如，如果有一个列， 它将跨越整个行的列，对于两列，它将在它们之间平均分空格)
* **自动适合内容** — — 自动使列大小与它的内容匹配
* **手动** - 允许您手动设置列大小

列宽度可以用于使您的布局更加灵活，更适合不同类型的设备。

例如，您有一个布局网格，一个列和两个列：一个图片在一个列， 还有一个详细的文本在另一个地方。

对于 *桌面* and *平板*, 您可能想要将第一列的图片设置为 **自动适合内容** ，而第二列设置为 **自动填充**， 这样，第一列将根据图片的大小进行调整，而第二列将占用行的其余部分：

![布局示例桌面](attachments/container-widgets/layout-example-desktop.png)

对于 *电话*, 最好把两个列放在另一个列下。 设置它们为 **手动** 宽度为 *12* (关于列大小属性的更多信息) 请参阅 [大小](#column-size) 部分)。 在这种情况下，第二列将被自动包装到另一行：

 {{% image_container width="300" %}}
![布局示例电话](attachments/container-widgets/layout-example-phone.png)
{{% /image_container %}}

在下面的图片上，您可以看到上述两列的设置：

![](attachments/container-widgets/column-settings-example.png)

#### 4.2.2 **大小** {#column-size}

**大小** 选项仅在 [宽度](#column-width) 设置为 **手册** 时才显示。

此设置允许您手动设置桌面、平板电脑的列大小， 或通过使用相应的属性电话: **桌面大小**, **平板块大小**, **电话大小**

#### 4.2.3 垂直对齐

**垂直对齐** 属性会覆盖 **垂直对齐列** 行上的属性，并为单个列设置对齐。

## 5 执行基本操作

### 5.1 添加新行或列

若要添加新行，请执行以下操作：

1. 在布局网格中选择一个现有行。

2. Right-click and select **Insert row above** or **Insert row below**:

    ![添加新行](attachments/container-widgets/adding-row.png)

3. 选择列布局 (行中应该有多少列，重量列应该有多少)。

布局网格添加了一个新行。

若要添加新一栏，请执行：

1. 选择您想要添加一个新列的旁边。
2. 右键点击并选择 **左侧添加列** 或 **右侧添加列**。

添加了一个新列，权重1自动为其设定。

### 5.2 在行上执行其他操作

添加到新行时，您可以在右键单击行时执行以下操作：

* **Move up** – moves a row up in the layout grid, you can use a shortcut for it  <kbd>Ctrl</kbd> + <kbd>↑</kbd>
* **向下移动** — — 在布局网格中向下移动一行 您可以对它使用快捷键  <kbd>Ctrl</kbd> + <kbd>Macro</kbd>

### 5.3 在列上采取其他行动

添加到新列时，当右键单击列时，您可以执行以下操作：

* **左移** - 移动一列左边, 您可以使用快捷键  <kbd>Ctrl</kbd> + <kbd>+</kbd>
* **向右移动** - 行中的一列, 您可以使用快捷键  <kbd>Ctrl</kbd> + <kbd>→</kbd>
* **行** - 允许您在列中执行操作

## 6 阅读更多

* [页](page)
* [容器部件](容器部件)
* [小部件常见的属性](common-widget-properties)
