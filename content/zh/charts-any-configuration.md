---
title: "任何图表部件"
parent: "图表部件"
description: "用于传递正确值以绘制的任何图表部件配置参考指南。 这将使您可以绘制各种图表"
menu_order: 30
tags:
  - "任何图表"
  - "参考指南"
  - "备选方案"
  - "配置"
  - "图表"
---

## 1 导言

使用 **任意图表**, 你可以构建任何图表类型的 Plotly.js 支持。 所以，如果你想要构建一个不能作为标准图表部件的图表， 例如3D图表，任何图表都是你的朋友。

此图表类型的配置是复杂的。 For help, you can look at the **building blocks** that are delivered in the [Any Chart](/appstore/modules/any-chart) module from the Mendix Marketplace. 或者，使用 [如何使用任何海图](/howto7/extensibility/charts-any-usage) 或 [任何海图作弊板](charts-any-cheat-sheet) 快速开始。

任何图表都使用JSON **数据** 数组和 **布局** 对象配置。 可以通过 **源属性** 和 **示例数据** 静态设置配置。

可以动态创建或从数据库检索的 JSON 布局。 将合并到静态设置并覆盖任何常见属性。

样本数据是为了演示目的。 它是在运行时显示的，当没有选择源属性时，当图表渲染到模组预览时。

## 2. 任何图表部件的位置

任何图表部件都必须放置在 **数据视图** 的背景下。 数据视图包含一个实体对象，它具有 **源属性** (无限长度字符串)，其中包含您想要绘制的数据的 JSON 表示。 与基本图表小部件不同的是，任何图表小部件都不能直接在您的域模型中的数据上工作。 您必须将您想要绘制的数据转换成任何图表所期望的 JSON 格式。 请参阅 [如何使用任何图表](/howto7/extensibility/charts-any-usage) 以了解如何做到这一点。

## 3 数据

拟绘制的数据以数组方式说明。 此数组的元素是要在选定的图表类型上绘制的点数(散射或条形) 例如， [完整引用](https://plot.ly/javascript/reference) 中记录的)。

### 静态的

JSON数组 (基于 https://plot.ly/javascript/reference/) 其中包含 *静态* 图表描述部分。 这些是图表的默认描述，可能是您想要绘制的图表类型。

### 源属性

这是一个无限的字符串属性，它是一个构成数据视图上下文的实体的属性，在这个视图中， **任何图表** 小部件都被放置在这个属性。

In the image below, the **Source attribute** is the *data* attribute of the *ChartContext* entity which is the data view context in which the Any Chart widget is placed.

![](attachments/pages/charts/any-chart-page-placement.png)

**源属性** 包含一个 JSON 结构，它将与 **静态** 数据合并并覆盖。 通常，这包含你想要绘制的数据，但它也可以覆盖其他静态元素，如图表类型， 线条颜色或条形图中条形状的方向。

### 示例数据

图表预览数据。 这将会在建模器中与 **静态数据** 合并，或在运行时没有 **源属性** 被选中。

### 模式

**在运行应用程序时开发** 模式为图表添加了一个按钮。 此按钮用于切换用于测试高级配置选项的在线编辑器。

**生成** 模式将删除此按钮，以便用户在设计图表时看到它。

## 4 布局选项

绘图的布局——与数据无关的视觉属性，如标题、注释等。 — — — 在 JSON 对象中的描述，该描述在 [完整引用](https://plot.ly/javascript/reference/#layout) 中。

### 静态的

基于 https://plot.ly/javascript/reference/描述图表默认布局的 JSON 对象。

### 源属性

这是实体的一个无限长度字符串属性，它构成了数据视图的上下文，在这个视图中， **任意图表** 小部件。 它包含一个 JSON 结构，它将与 **静态** 布局合并并覆盖。 这使您能够动态地从应用内部更改布局信息。

### 示例布局

预览布局选项。 当没有 *源属性* 被选中时，它将被合并到模组中的 *静态* 布局中。

## 5 个配置选项

JSON包含绘图的高级配置选项，如滚动/缩放/悬停行为。 这些高级配置选项在这里被记录：https://plot.ly/javascript/configuration-option。

The difference between **config** and **layout** is that layout relates to the content of the plot, whereas config relates to the context in which the plot is being shown. **任何图表** 部件都不允许在您的应用程序中动态更改配置选项。

## 6 个外观

外观设置用于设置图表的尺寸。

### 宽度单位

用于 **宽度** 属性的单位类型： *百分比* 或 *像素*

### Width

图表的宽度，以像素或百分比为基础，基于 **宽度单位** 设置。

### 高度单位

**宽度** 的百分比允许您更改宽度。 **像素** 是一个绝对的度量。 和 **上级的百分比** 允许您设置上级容器的高度值。

{{% alert type="warning" %}}
Warning: When using **Percentage of parent** the parent container must have an absolute height, else nothing is displayed.
{{% /报警 %}}

### 高度

基于 **高度单位** 设置的高度（以像素为单位）或百分比为单位。

## 7 个事件

**任何图表** 小部件支持两种类型的事件，与图表上绘制的点相关：

* **悬停**: 那些被解析为 *工具提示* 请求
* **点击**: 什么样的解析为 *点击* 事件

{{% alert type="info" %}}
事件将因悬停或点击图表上绘制的点而触发。 点击图表的其他部分不会触发事件。
{{% /报警 %}}

事件发生时，绘图将返回这里描述的 JSON 对象：https://plot.ly/javascript/plotlyjs-events/#event-data. 此 JSON 数据存储在实体对象的字符串属性中，传递到 **任意数据**。 JSON载有已绘制的图表的原始数据，例如该点的x坐标和y坐标。 并且需要在事件触发的微流中进行解释。

### 事件实体

用于从绘图接收事件数据的实体。 这需要包含一个包含事件数据的字符串属性。

### 事件数据属性

存储来自图表事件的 JSON 数据的字符串属性。

### 点击微流

点击图表上的数据点时将执行的微流。 这将有 **事件实体** 作为上下文.

### 点击nanoflow

点击图表上的数据点时将执行的 nanoflow 这将有 **事件实体** 作为环境

### 工具提示表单实体

当 **Tooltip microflow** 是由一个绘图悬停事件触发的， 它需要返回一个实体对象，这个实体构成 **Tooltip 表单的上下文**

此处指明了通过工具提示微流返回的实体。 它不必是 **事件实体** ，这是 **Tooltip microflow** 的背景。 开发者可以根据工具提示表单显示的数据和悬停事件在 **事件实体** 中提供的信息，来确定和融入实体的属性和关联性。

### 工具提示微流

这里指明的微流被从地皮上收到的悬停事件调用。 它收到了类型为 **事件实体类型的** 的事件对象，包含 **事件数据属性** 包含JSON 事件数据。 数据应该被解释并返回类型 **Tooltip 表单实体** 的对象。 这将形成 **Tooltip form** 的背景。

### 工具提示表单

显示用户在图表点上悬停时的表格。 它有上下文 **Tooltip实体**。 当鼠标悬停在图表上绘制的点上时，表单会显示。 当鼠标不在绘图点上时，它会自动关闭。

## 8 图表主题

也可以通过您的 mendix 项目根目录的主题文件夹在全局环境中添加高级JSON 设置。

在主题文件夹中添加 `.json` 文件，名为 *com.mendix.chats*。 JSON应采用以下格式：

``` json
{
  "layout": {
    // Add shared layout options here (for all charts)
  },
  "configuration": {
    // Add shared configuration options here (for all charts)
  },
  "charts": {
    "LineChart": {
      "layout": {
        // Add line chart only layout options here
      },
      "data": {
        // Add line chart only data options here
      },
      "configuration": {
          // Add line chart only configuration options here
      }
    },
    "AreaChart": {
      // Same arrangement as the line chart
    },
    "BubbleChart": {
      // Same arrangement as the line chart
    },
    "TimeSeries": {
      // Same arrangement as the line chart
    },
    "ColumnChart": {
      // Same arrangement as the line chart
    },
    "BarChart": {
      // Same arrangement as the line chart
    },
    "PieChart": {
      // Same arrangement as the line chart
    },
    "HeatMap": {
      // Same arrangement as the line chart
    }
  }
}
```

关于如何设置图表主题的指南见： [如何使用图表主题](/howto7/extensibility/charts-theme)。

{{% alert type="info" %}}

请谨慎使用，因为这里设置的配置将应用于您应用程序中的每个图表。 只有小部件中设置的高级配置具有更高的优先级别。

{{% /报警 %}}
