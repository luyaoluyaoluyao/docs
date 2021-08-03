---
title: "报告网格"
parent: "报告小部件"
menu_order: 10
tags:
  - "studio pro"
---

{{% alert type="info" %}}
这个小部件在版本9.0中被废弃，将在未来的版本中标记为移除。
{{% /报警 %}}
{{% alert type="warning" %}}
本机移动页面不支持报表网格部件。
{{% /报警 %}}

## 1 导言

**报告网格** 显示从数据库检索到的数据组使用 [数据组](data-sets) 以网格格式显示数据。 网格中的每一行显示数据集的单一结果。 每次创建报告时，从数据库中检索数据。

数据网格和报告网格之间的差别是您可以使用数据网格来编辑显示的数据。 报告网格只显示数据。 然而，在报告网格中，当您定义检索数据的数据集时，您可以通过合并和处理属性来创建额外信息。

报告网格显示在结构模式中，数据集源显示在方括号和彩色蓝色。 数据集返回的数据字段显示在报告网格列标题下。 关于如何分配数据字段到列的信息，请参阅 [报告网格列数据源](#column-data-source)。

![在结构模式中报告网格](attachments/report-widgets/report-grid.png)

## 2 报表网格属性

报表网格属性的示例在下面的图像中显示：

{{% image_container width="300" %}}![在结构模式中报告网格](attachments/report-widgets/report-grid-properties.png)
{{% /image_container %}}

报表网格属性由以下部分组成：

* [常用的](#common)
* [数据源](#data-source)
* [设计属性](#design-properties)
* [A. 概况](#general)

报表网格中的每一列也有属性：查看 [报表网格列属性](#column-properties)。

### 2.1 共同部分{#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 数据源部分{#data-source}

#### 2.2.1 数据集

**数据集** 指定了 [数据集](data-sets) 定义了将在报告网格中显示的数据。 从数据集中选定的任何属性或聚合(例如合计或平均值)都可以从 **连接器** 面板拖入数据网格列：见 [报告网格列数据源](#column-data-source)以下：

### 2.3 设计属性部分{#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.4 一般部分{#general}

#### 2.4.1 使用分页

Set **Use paging** to **Yes** if you expect more data than you can display on one page. 这将结果分成几个页。

#### 2.4.2 页大小

**页面大小** 指定了显示在一个页面上的结果数量，如果 **使用页面** 是肯定的话。

#### 2.4.3 缩放 {#zoom}

**缩放** 指定了一个页面，在最终用户双击报告结果时将显示。

如果选定的页面包含一个报表， 本报告各列可以被映射到作为另一页报告基础的数据集参数中。

![缩放配置，显示列作为参数](attachments/report-widgets/report-zoom.png)

#### 2.4.4 列宽度

栏目宽度以基本报告总宽度的百分比表示。 您可以通过以下两种方式编辑此属性：

* 拖动列之间的边框：

    ![拖动列宽度](attachments/report-widgets/drag-column-width.png)

* 通过明确输入百分比

    ![输入列宽度](attachments/report-widgets/enter-column-widths.png)

报表网格中的每一列也有属性：查看 [报表网格列属性](#column-properties)。

每个列的数据源可以从 **连接器** 面板拖入列：参见 [报告网格列数据源](#column-data-source), 以下：

#### 2.4.5 显示导出按钮

设置 **显示导出按钮** 到 **是** 以显示 **导出到 Excel** 按钮到报告网格上的最终用户。

![添加导出到Excel按钮](attachments/report-widgets/export-to-excel.png)

当最终用户点击此按钮时， 报告导出为 `Microsoft Excel 97-2003 Worksheet` ，最终用户可以下载或查看， 取决于他们的浏览器设置。

#### 2.4.6 在页面负载时生成

如果 **在页面负载上生成** 设置为 **否**报告网格不会显示任何数据，除非最终用户按下 [生成报告按钮](report-button)。 如果报表使用应由最终用户首先指定的参数，这样做特别有用。

## 3 报表网格列属性{#column-properties}

报表网格属性的示例在下面的图像中显示：

{{% image_container width="250" %}}![报告网格列属性](attachments/report-widgets/report-grid-column-properties.png)
{{% /image_container %}}

报告网格属性由单个章节组成， [常规的](#column-general)。

### 3.1 一般部分{#column-general}

#### 3.1.1 标题

**标题** 包含显示在报告网格每一列顶部的文本。

#### 3.1.2 对齐

**对齐** 设置此列中显示的标题和数据的对齐。 值为：

* 左侧
* 居中
* 右侧

#### 3.1.3 格式

**格式** 允许您将列中的数值转换为月或日名。 如果列中的值不是数字， **将使用默认** 格式。

可能的数值是：

* 默认 — 数据将以默认字符串格式显示
* 月名称 — 数字值将被解释为月名 (例如， **8** 显示为 **August**)
* 周日名称 — 一个数值将被解释为一周的某一天(例如， **4** 显示为 **星期三**)

#### 3.1.4 可见

如果 **可见** 设置为 **否** 则此列将不会在报告中显示。

这可以用来为报告添加一个值，这个值可以传递到使用 [缩放](#zoom) 指定的页面上的报告，而不会显示它作为报告的一部分。

## 4 报告网格列数据源{#column-data-source}

若要将数据添加到列，请选择列，打开 **连接器** 面板，并将结果之一拖动到列中。 您将需要选择报告网格或它的一部分，看到连接器窗格中数据集的结果。

![从连接器窗格拖动数值到列](attachments/report-widgets/drag-column-value.png)
