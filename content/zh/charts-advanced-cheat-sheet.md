---
title: "海图高级作弊表"
parent: "图表部件"
menu_order: 20
tags:
  - "图表"
  - "高级版"
  - "桌面模型"
  - "布局控制"
  - "数据属性"
  - "系列属性"
---

## 1 导言

此引用描述了图表部件的高级配置设置。

标准图表通过小部件配置提供了最常见的设置。 其他设置可以通过高级设置设置。

这张使用 JSON 代码片段的作弊板将提供一些预设配置的样本。

完整引用可在 [https://plot.ly/javascript/](https://plot.ly/javascript/) 上找到。

当高级配置不足以在应用商店查看 [任意图表](https://marketplace.mendix.com/link/component/106437/Mendix/Any-Chart) 小部件。

## 2 个布局 (所有图表) {#layout-all}

布局控制图的一般外观。 通过将 JSON 属性添加到布局来定制图表。

下面是一个基本配置。

``` json
{
  "font": {
    // font properties
  },
  "title": "CHART TITLE",
  "titlefont": {
    // title font properties
  },
  "hovermode": "closest",
  "showlegend": true,
  "legend": {
    // legend properties
  },
  "hoverlabel": {
    // hover label properties
  },
  "margin": {
    // margin properties
  }
}
```

要使用上面的布局片断，将所有标签为 *// {some text} 属性* 的行替换为特定元素的实际属性。

### 2.1 说明

下面的图解属性被添加到布局配置中，以应用自定义风格。

``` json
您的
  "传奇"：您，
    "showlegend"：true，
    "传说": Power
      "bgcolor": "#fff",
      "边框": "#444",
      "边框": 0,
      "font":□
        "family": "Open Sans, verdana, arial, serif ",
        "size": 12,
        "color": "black"
      },
      "orientation": "v",
      "追踪": "normal",
      "Tracegap": 10,
      "x": -0". ,
      "xanchor": "right"
    }
  }
}
```

您可以通过修改下面显示的属性来更改图例的位置。

**右侧：**

``` json
很抱歉，
  "showlegend"：true，
}
```

**左：**

调整x长系列名称或Y轴条目。

``` json
主席:
  "showlegend": tre,
  "legend":
    "xanchor": "right",
    "x": -0.1
  }
}
```

**顶部：**

``` json
{
  "showlegend": true,
  "legend": {
    "orientation": "h",
    "y": 1.1
  }
}
```

**底部：**

长X轴刻度为 -0.2 。

``` json
主席:
  "showlegend": tre,
  "legend":
    "orientation": "h",
    "y": "auto"
  }
}
```

**输入：**

``` json
主席:
  "showlegend": tre,
  "legend":
    "x": 0
  }
}
```

**无：**

``` json
{
  "showlegend": false
}
```

![图例配置](attachments/pages/charts/advanced-layout-legend.gif)

这里可以找到更多选项： [图例配置](https://plot.ly/javascript/reference/#layout-legend)。

### 2.2 轴

轴属性适用于带x和y轴的海图。 他们可以配置为：

``` json
主席:
  "xaxis": ~
    "gridcolor": "#eaea",
    "title": "X-axis",
    "color": "#0000FF",
    "showgrid": false,
    "固定范围": true ,
    "showline": true
    "side": "bow"
  },
  "yaxis": ~
    "rangemode": "tozero",
    "zeroline": true,
    "zerolinecolor": "#eaeaea",
    "gidcolor": "#eaea",
    "color": "#0000FF",
    "title": "Y-axis",
    "showgrid": true
    "showline": true,
    "固定范围": true
  }
}
```

![轴配置](attachments/pages/charts/axes.gif)

这里可以找到更多选项： [轴配置](https://plot.ly/javascript/reference/#layout-xaxis)。

### 2.3 多个Y 轴

这些属性适用于一个以上Y轴的图表。 他们可以配置为：

``` json
主席:
  "yaxis": ~
    "title": "Y-axis 1",
    "零线": true,
    "color": "#4682B4",
    "showgrid": tre,
    "showline": true
  },
  "yaxis2": Power
    "title": "Y-axis 2",
    "color": "#FF8C00",
    "showgrid": true",
    "showline": true
    "zeroline": true,
    "overlaying": "y",
    "side": "right"
  }
}
```

上面的布局属性应该与对应的 [数据属性一起使用](#multiple-y-axes-data-properties)。

![多轴配置](attachments/pages/charts/multiple-y.gif)

这里可以找到更多选项： [多个Y轴配置](https://plot.ly/javascript/multiple-axes/)。

### 2.4 多个X轴

这些属性适用于一个以上X轴的海图。 他们可以配置为：

``` json
{
  "xaxis": {
    "title": "X-axis 1",
    "color": "#4682B4",
    "showgrid": true,
    "showline": true,
    "zeroline": true
  },
  "xaxis2": {
    "title": "X-axis 2",
    "titlefont": {
      "color": "#FF8C00"
    },
    "tickfont": {
      "color": "#FF8C00"
    },
    "zeroline": true,
    "color": "#FF8C00",
    "showgrid": true,
    "showline": true,
    "overlaying": "x",
    "side": "top"
  }
}
```

上面的布局属性应该与对应的 [数据属性一起使用](#multiple-x-axes-data-properties)。

![多个X轴配置](attachments/pages/charts/multiple-x.gif)

这里可以找到更多选项： [多个X轴配置](https://plot.ly/javascript/multiple-axes/)。

### 2.5 Math LaTeX 公式：

标题、轴和系列可以包含复杂的数学表达式。

![数学公式。](attachments/pages/charts/math-formula.png)

```
$\sqrt{(n_\text{c}(t|{T_\text{early}})})}$
```

在主题的 index.html 中添加以下内容：

``` javascript
<script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_SVG"></script>
```

更多关于 LatTex 语法的信息可在这里查阅：https://en.wikibooks.org/wiki/LaTeX/Mathematics。

### 2.6 标题

标题出现在图表之上。 它可以配置为：

``` json
主席:
  "title": "CHART TITLE",
  "titlefont": format@@
    "family": "Droid Sans, Droid Serif, sans-serif",
    "size": 20,
    "color": "black"
  }
}
```

![标题配置](attachments/pages/charts/title.gif)

在这里可以找到更多选项： [标题配置](https://plot.ly/javascript/reference/#layout-title)。

### 2.7 颜色

设置图形的背景颜色。

``` json
{
  "paper_bgcolor": "#FFF"
}
```

### 2.8 差值

在图表周围创建空间。

``` json
{
  "margin": {
    "l": 70,
    "r": 60,
    "b": 60,
    "t": 60,
    "pad": 10,
    "autoexpand": true
  }
}
```

![ 边际配置 ](attachments/pages/charts/margin.gif)

这里可以找到更多选项： [边际配置](https://plot.ly/javascript/reference/#layout-margin)。

### 2.9 工具提示

当用户将鼠标指针移动到图表数据点时出现的一个小弹出框。

``` json
{
  "hovermode": "text",
  "hovertext": "text",
  "hoverinfo": "all",
  "textposition": "inside",
  "hoverlabel": {
    "bgcolor": "#888",
    "bordercolor": "#888",
    "font": {
      "color": "white"
    }
  }
}
```

![工具提示配置](attachments/pages/charts/tooltip.gif).

这里可以找到更多选项： [Tooltip配置](https://plot.ly/javascript/reference/#layout-hovermode)。

### 2.10 字体

在根层设置一个全局字体，将应用于所有图表元素。 或者为特定元素设置字体。

``` json
{
  "font": {
    "family": "Open Sans,verdana, arial, sans-serif",
    "size": 12,
    "color": "black"
  },
  "legend": {
    "font": {}
  },
  "titlefont": {},
  "hoverlabel": {
    "font": {}
  },
  "xaxis": {
    "titlefont": {},
    "tickfont": {}
  },
  "yaxis": {
    "titlefont": {},
    "tickfont": {}
  }
}
```

### 2.11 范围模式

设置给定坐标轴的显示范围。

**普通：**

根据绘图值设置范围，调整以适应它们。

```json
{
  "yaxis": {
    "rangemode": "normal"
  }
}
```
![范围模式](attachments/pages/charts/normal.gif)

**非负数：**

只显示正值，范围基于绘图的正值。

```json
{
  "yaxis": {
    "rangemode": "nonnegative"
  }
}
```

![范围模式](attachments/pages/charts/nonnegative.gif)

**tozero:**

这是图表中的默认范围模式。 轴的正值和负值范围将从零标记开始。

```json
{
  "yaxis": {
    "rangemode": "tozero"
  }
}
```

![范围模式](attachments/pages/charts/tozero.gif)

{{% alert type="info" %}}
当 **填充** 为系列设置了除 *以外的内容*和 Y轴范围被迫从零开始(*到零*)。 例如：

**布局**

```json
{
  "yaxis": {
    "rangemode": "normal"
  }
}
```

**数据**

```json
{
  "fill": "tonexty"
}
```
{{% /报警 %}}

![范围模式](attachments/pages/charts/rangemode-note.gif)

这里可以找到更多选项： [范围模式配置](https://plot.ly/javascript/reference/#layout-yaxis-rangemode)。

## 3 数据/系列属性 {#data-series}

这些属性仅适用于特定类型的图表。 对于每个图表，数据属性是不同的。 它们使这张图表显示为假定的图表。

### 3.1 行

可以在序列的 **高级** 配置中添加模式和行配置。

![Line styles](attachments/pages/charts/line-styles.png)

``` json
[
  {
    "mode": "markers"
  },
  {
    "mode": "lines+markers"
  },
  {
    "mode": "lines"
  },
  {
    "mode": "lines",
    "line": {
      "dash": "dashdot"
    }
  },
  {
    "mode": "lines",
    "line": {
      "dash": "dot"
    }
  },
  {
    "mode": "lines",
    "line": {
      "dash": "longdash"
    }
  },
  {
    "mode": "lines",
    "line": {
      "width": 5
    }
  }
]
```

### 3.2 合并图表类型

系列的类型可以更改。 例如，您可以将一条条序列变成一条线性序列：

![列图数据属性](attachments/pages/charts/combine-list-bar.gif)

### 3.3 饼状图

显示分为切片的圆形图，以说明数字比例。

``` json
{
  "hole": 0.9
}
```

![Pie 图表数据属性](attachments/pages/charts/pie-chart.png)

这里可以找到更多选项： [Pie 图表数据属性](https://plot.ly/javascript/reference/#pie)。

### 3.4 填充

以颜色填充的线条下方区域显示线条图。

``` json
主席:
  "line":
    "color": "#17202A",
    "shape": "linear",
    "dash": "dot"
  },
  "type": "scatter",
  "fill": "tonexty",
  "fillcolor": "#B2BABB"
}
```

![区域图表数据属性](attachments/pages/charts/area-chart.png)

这里可以找到更多选项： [地区图数据属性](https://plot.ly/javascript/reference/#area)。

### 3.5 时间系列

下面的示例显示您如何设置过滤器按钮按时间过滤图表。

![线条图表数据属性](attachments/pages/charts/time-series-filters.png).

``` json
{
  "xaxis": {
    "rangeslider": {
      "visible": true
    },
    "rangeselector": {
      "buttons": [
        {
          "step": "all",
          "label": "reset"
        },
        {
          "step": "year",
          "stepmode": "backward",
          "count": 1,
          "label": "1 YEAR"
        },
        {
          "step": "year",
          "stepmode": "backward",
          "count": 5,
          "label": "5 YEARS"
        },
        {
          "step": "year",
          "stepmode": "backward",
          "count": 10,
          "label": "10 YEARS"
        },
        {
          "step": "year",
          "stepmode": "todate",
          "count": 1,
          "label": "YTD"
        }
      ]
    }
  }
}
```

在此查看更多属性： [范围选择器](https://plot.ly/javascript/reference/#layout-xaxis-rangeselector)。

### 3.6 多个Y轴数据属性 {#multiple-y-axes-data-properties}

根据数据集的范围显示两个不同的 Y 轴。

``` json
[
  {
    "name": "yaxis2 data",
    "yaxis": "y2",
    "type": "scatter"
  },
  {
    "name": "yaxis data",
    "type": "scatter"
  }
]
```

![多轴属性](attachments/pages/charts/data-multiple-y.png)

### 3.7 多个X轴数据属性 {#multiple-x-axes-data-properties}

显示两个不同的 X 轴，尺寸不同。

``` json
[
  {
    "name": "xaxis data",
    "xaxis": "x",
    "type": "scatter"
  },
  {
    "name": "xaxis2 data",
    "xaxis": "x2",
    "type": "scatter"
  }
]
```

![多个X轴属性](attachments/pages/charts/data-multiple-x.png).

## 4 个配置选项 (所有图形) {#config-options}

以下配置选项可以在所有图表中找到。

```json
主席:
  "displayModeBar": try,
  "displaylogo": false,
  "modeBarButtonsToRemove": [ "sendDataToCloud", "lasso2d", "select2d", "hoverClosestCartesian", "hoverCompareCartesian", "toggleSpikelines"
  "locale": "nl",
  "locales": P,
    "nl": P,
      "dictionary": P,
        "下载绘图作为一个png": "Opslaan als PNG"  
      }
    }
  }
}
```
