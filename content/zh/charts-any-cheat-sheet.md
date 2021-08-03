---
title: "任何图表作弊表"
parent: "图表部件"
description: "以示例显示如何使用任何图表小部件配置最常见的图表类型"
menu_order: 50
tags:
  - "任何图表"
  - "示例："
  - "图表"
  - "小部件"
  - "studio pro"
---

## 1 导言

此 *作弊表* 列出了最常见的图表类型，以及一个视觉示例和创建它们所需的json。 更多图表类型可以在 [https://plot.ly/javascript/](https://plot.ly/javascript/) 中找到。

## 2 基本图表

### 2.1 线图 {#line-chart}

![线性图属性](attachments/charts/line-chart2.png)

``` json
[
  {
    "x": [ 1, 2 ],
    "y": [ 1, 2 ],
    "type": "scatter"
  },
  {
    "x": [ 3, 4 ],
    "y": [ 9, 14 ],
    "type": "scatter"
  }
]
```

### 2.2 泡泡泡图

![BubbleChart属性](attachments/charts/bubble-chart.png)

``` json
[ 主席:
  "x": [ 1, 2, 3 ],
  "y": [ 1, 2, 2 3],
  "marker": *
    "color": [ "red", "蓝色", "绿色" ],
    "大小": [ 20, 50, 80 ]
  },
  "模式": "标记"
} ]
```

### 2.3 散列图

![散列图属性](attachments/charts/scatter-plot.png)

``` json
[ 主席:
  "x": [ 1, 2, 3 ],
  "y": [ 1, 2. 3],
  "案文": [ "A", "B", ", "C" ,
  "textposition": "left center",
  "mode": "markers+text"
} ]
```

### 2.4 热图

![热映射属性](attachments/charts/heat-map2.png)

``` json
[ {
  "z": [ [ 1, 2 ], [ 3, 4 ] ],
  "type": "heatmap"
} ]
```

### 2.5 条形图

![条形图属性](attachments/charts/bar-chart2.png)

``` json
[ 主席:
  "y": [ "giraffe", "elephant" ],
  "x": [ 2, 4],
  "type": "bar",
  "orientation": "h"
} ]
```

### 2.6 列图

![列图属性](attachments/charts/column-chart2.png)

``` json
[ 主席:
  "x": [ "giraffe", "elephant" ],
  "y": [ 2, 4],
  "type": "bar",
  "orientation": "v"
} ]
```

### 2.7 饼图

![PiChart属性](attachments/charts/pie-chart2.png)

``` json
[ 主席:
  "values": [ 10, 20, 30],
  "labels": [ "Uganda", "Netherlands", "US" ,
  "type": "pie"
} ]
```

### 2.8 坚固图

![GooughNutChart属性](attachments/charts/doughnut-chart.png)

```json
[ 主席:
  "values": [ 10, 20, 30],
  "labels": [ "Uganda", "Netherlands", "US" ],
  "hole": 0.4,
  "type": "pie"
} ]
```

### 2.9 面积图

![区域图表属性](attachments/charts/area-chart2.png)

``` json
[ 主席:
  "x": [ 1, 2, 3 ],
  "y": [ 1, 2, 3 ],
  "模式": "散列",
  "填充": "tonexty"
}
```

## 3 统计图

### 3.1 Histograms

![直方图属性](attachments/charts/histogram.png)

``` json
[ 主席:
  "x": [ 0, 2, 1, 3, 4, 2 ],
  "type": "histogram"
} ]
```

### 3.2 方框图

![BoxPlot属性](attachments/charts/box-plot.png)

``` json
[ 主席:
  "x": [ 1, 2, 3, 4, 5 ],
  "type": "box"
} ]
```

### 3.3 2D 直方图

![2DHistogram属性](attachments/charts/2d-histogram.png)

``` json
[ {
  "x": [ 1, 2, 3, 4, 5 ],
  "y": [ 1, 2, 3, 4, 5 ],
  "type": "histogram2d"
} ]
```

## 4 个地图

### 4.1 泡泡图

![BubleMap属性](attachments/charts/bubble-map.png)

``` json
[ 主席:
  "lon": [ 100, 400 ],
  "lat": [ 0, 0 ],
  "type": "scattergeo",
  "marker": □
    "color": [ "red", "蓝色" ],
    "大小": [ 20, 50 ]
  },
  "模式": "标记"
} ]
```

### 4.2 Choropleth地图

![ChoroplethMapProperties](attachments/charts/choropleth-map.png)

#### 4.2.1 Choropleth地图数据

``` json
[ 主席:
  "locations": [ "AZ", "CA", "VT" ],
  "locationmode": "USA-states",
  "z": [ 10, 20, 40 ],
  "type": "scattergeo"
} ]
```

#### 4.2.2 Choropleth地图布局

``` json
主席: 
  "geo": format@@ 
    "scope": "usa" 
  }
}
```

### 4.3 散列地图

![散列地图属性](attachments/charts/scatter-map.png)

``` json
[ 主席:
  "lon": [ 12, 22 ],
  "lat": [ 42, 39 ],
  "类型": "scattergeo",
  "text": [ "Rome", "Greece" ],
  "mode": "marker"
} ]
```

## 5 3D 图表

### 5.1 3D 表面图表

![3DSurfacePlot属性](attachments/charts/3d-surface-plot.png)

``` json
[ 主席:
  "colorscale": "Viridis",
  "z": [ 3, 5, 7, 9 ], [ 21, 13, 8, 5 ],
  "类型": "surface"
} ]
```

### 5.2 3D 线图

![3DLineChartities](attachments/charts/3d-line-chart.png)

``` json
[请注意，
  "x"：[ 9, 8, 5, 1 ],
  "y": [ 1, 2, 4, 8 ],
  "z": [ 11, 8, 15, 3 ],
  "模式": "lines",
  "type": "scatter3d"
} ]
```

### 5.3 3D 散列图

![3DScatterPlot属性](attachments/charts/3d-scatter-plot.png)

``` json

  "x": [ "9", "8", "5", "1" ],
  "y": [ "1", "2", "4", "8" ], 
  "z": [ "11", "8", "15", "3" ],
  "模式": "markers",
  "type": "scatter3d"
} ]
```

## 6 个其他图表

### 6.1 等深图

![连接属性](attachments/charts/contour.png)

``` json
[ 主席:
  "z": [ 2, 2, 4, 11 ], [ 5, 14, 8, 11 ] ],
  "类型": "等候"
} ]
```

### 6.2 时间系列

![时间序列属性](attachments/charts/time-series2.png)

``` json

  "type": "scatter",
  "mode": "lines",
  "x": [ "2018-09-04", "2018-10-04", "2018-11-04", "2018-12-04", "2018-12-04",
  "y": [ 5, 2, 7, 10 ]
}
```

### 6.3 按图表

![群组字典属性](attachments/charts/group-by-chart.png)

``` json

    "type": "scatter",
    "x": [ "Arthur","Jolly","Daphine","Arthur","Jolly", 奶粉],
    "y": [ 1, 6, 2, 5, 8, 1],
    "模式": "标记"
} ]
```

### 6.4 对称错误栏

![错误栏属性](attachments/charts/error-bar.png)

``` json

  "x": [ 0, 1, 2],
  "y": [ 6, 10, 2],
  "error_y":
    "type": "data",
    "数组": [ 4, 2, 3 ]
  },
  "type": "scatter"
} ]
```

### 6.5 极地图

![极地图属性](attachments/charts/polar-chart.png)

``` json
[ 主席:
  "type": "scatterdial",
  "r": [ 34, 11, 39, 37, 34],
  "theta": [ "A", "B", "C", "D", "A" ],
  "fill": "toself"
} ]
```

### 6.6 Ternary Plots

![TernaryPlotProperties](attachments/charts/ternary-plot.png)

#### 6.6.1 实用绘图数据

``` json
[□
    "type": "scatterternary",
    "mode": "markers",
    "a": [ 5, 4, 5, 2, 10 ],
    "b": [ 2, 1, 15, [20, 8],
    "c": [ 1, 20, 5, 15, 10 ],
    "text":[ "point 1", "点2", "点3", "点4", "点5"]
}]
```

#### 6.6.2 实用布局布局

```json
{
  "ternary": {
    "sum":100
  }
}
```

## 7 阅读更多

* 完整的图表文档在这里： [https://plot.ly/javascript/](https://plot.ly/javascript/)
* [任何图表部件](charts-any-configuration)
* [如何使用任何图表](/howto/front-end/charts-any-usage)
