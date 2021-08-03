---
title: "图表配置"
parent: "图表部件"
menu_order: 10
tags:
  - "图表"
  - "小部件"
  - "Studio Pro"
  - "图表配置"
  - "配置"
---

## 1 导言

本指南解释了配置图表部件的选项。 图表小部件包含在 Mendix 应用程序模板中，基于 Atlas UI 。 他们可以从 [Mendix Marketplace](https://marketplace.mendix.com/link/component/105695/) 下载其他Mendix 应用程序。 欲了解更多文档，请参阅 *市场指南* 中的 [海图](/appstore/widgets/charts)。

本指南涵盖下列部件：

* 区域图
* 条形图
* 气泡图
* 列图
* 热度地图
* 行图
* 饼状图
* 时间序列
  * 注意某些应用可能有两个 *时间序列* 小部件。 本文档是指带有此图标的文档： ![正确时间序列部件的图像](attachments/charts/time-series-icon.png)

*任何图表* 小部件的配置都在另一个文档中，这里： [任何图表小部件](charts-any-configuration)。

## 2 常用配置

这里描述了所有图表的共同配置。 图表特定配置见 [下面的图表类型](#configuration-by-chart-type)。

### 2.1 图表属性

![通用图表属性对话框](attachments/charts/line-chart-chart-properties.png)

#### 2.1.1 系列

添加系列并配置其属性，每个系列代表一个数据集。 例如，行图上的一行。

* *Pie 图表* and *Heat Map* 只支持一个包含单一数据集的单个系列

  在这种情况下， **数据源** and **数据点** 在小部件中显示为单独的标签。

  ![Pie 图表对话框显示数据源和数据点的标签](attachments/charts/widget-data-source.png)

  字段与下面 [数据源](#data-source) 和 [数据点](#data-points)中描述的字段相同。

* 支持多个系列数据的图表，例如多行线图，支持多个系列数据

  在这种情况下，可以通过点击 **系列 > 新的** 按钮添加新的序列。 **海图属性** 选项卡。

  ●{% alert type="info" %}}从1.4 个版本的海图，您可以用一个变量的数据序列创建海图。 关于如何做到这一点的说明，请参阅 [如何创建动态系列图表](/howto/front-end/charts-dynamic-series){%/警示%}}

1. 数据源<a name="data-source"></a>

    每个系列的数据可以来自不同的数据来源。 您可以在 **海图属性** 标签中添加额外的数据系列.

    ![编辑系列数据源标签](attachments/charts/series-item-data-source.png)

    * **Static/Dynamic**: 选择是否有固定的数据序列(行数) 例如，数据序列的数量是否可变，将由应用程序决定。

    * **实体**: 将从其中检索数据值的实体

    * **数据源**: 该系列的数据源类型: *数据库*, *微流程* 或 *REST 端点*

    * **REST URL**: 相对或完整的 URL 到REST 端点。 关于设置REST 端点的更多信息，请参阅 [REST Charts](/howto/front-end/charts-basic-rest)

    * **XPath 约束**: 实体数据的约束 (当数据源是数据库时使用)

    * **微流**: 返回带有数据值的列表对象的微流

2. 数据点<a name="data-points"></a>

    数据源中用于绘制值的属性。

    ![编辑系列数据点标签](attachments/charts/series-item-data-points.png)

    * **X-轴数据属性**: 对于数据源的数据库属性在引用上得到支持，最多一个深度。 对于数据源的 Microflow，不支持引用

    * **Y-轴数据属性**: 数据源数据库属性在引用上得到最多一个级别深度。 对于数据源的 Microflow 不支持

    * **X-轴排序属性**: 数据源数据库属性在参考上得到支持，最多为一个深度。 对于数据源的 Microflow 不支持

    * **排序顺序**: 由“X轴排序属性”提供的数据的排序顺序

    * **聚合类型**: 如果这个系列中有两个y值的一个x值（例如如果一个系列中有两个数据点的话）会怎么办: (2), （）和（（2.4））——大多数选择都是不言自明的，例如：
      * 总和：绘制上面示例的两个值 - (2.7)
      * 平均值：绘制两个值的平均值(2.3.5)
      * 无：绘制仅仅第一个数据点(2,3)

3. 外观

    该系列的出现。 每个类型的图表都是自定义的，见：下面每个图表类型</a>

3个配置。</p> 
   
   ![编辑系列外观标签](attachments/charts/series-item-appearance.png)</li> 
   
   4 静态系列
  
  如果是静态序列，则为该系列外观的额外配置。 每个类型的图表都是自定义的，见：下面每个图表类型</a>3个配置。    </p> 
  
  ![数据系列静态系列选项卡](attachments/charts/series-item-static.png)</li> 
  
  5 动态系列
  
  如果是动态系列，则配置该系列。
  
  ![数据系列动态系列选项卡](attachments/charts/series-item-dynamic.png)</ol> 

    * **系列实体**: 定义系列的实体 -- 此实体类型的对象列表将用于构建系列； 每个对象有一个序列号。
      
      每个实体都与将绘制的值相关联，查看 [如何创建动态系列图](/howto/front-end/charts-dynamic-series) 以获取更多信息。

    * **系列名称属性**: 如果图例显示为系列的属性将显示为系列名称

    * **色彩属性**: 定义显示此系列时所使用的 HTML 颜色的系列实体中的属性 - *如果图表允许不同的值，则可能有多个颜色属性 (例如，区域图有单独的行和填充颜色)

    * **系列排序属性**: 允许您按系列实体属性排序系列- *这不支持 **不可持续** 实体. 例如定义REST 数据源时所用的*

    * **系列排序顺序**: *升序* 或 *降序*

6. 事件
   
   如果用户与图表交互，将支持的事件。
   
   ![编辑系列事件选项卡](attachments/charts/series-item-events.png)
   
   {{% alert type="info" %}}The context of the page, microflow, or nanoflow selected for an event or tooltip will be the plotted object from which the point on the chart is drawn. 这意味着您可以显示或使用存储在该对象中的 x 和 y 值、 _和_ 其它值。<br /><br />例如，您可以使用工具提示来显示某点的精确y 值。 附加数据收集时间信息{{% /提醒 %}}

    * **点击**：选择一个数据点的处理方式：
      
            * 不执行任何操作
      * 显示页面
      * 调用微流
      * 呼叫nanoflow
        
        配置相应的设置。

      * **点击页面**: 点击将打开的页面会被点击。 当点击 > 显示页面</strong> 选项被选中时，需要 **</p></li> 
        
              * **以**打开页面：完整页面、弹出窗口或阻止弹出窗口

      * **点击微流**: 点击将执行的微流

      * **点击nanoflow**: 点击即将执行的 nanoflow</ul></li> 

    *     **Tooltip 表单**：当用户悬停在图表点时显示的页面
          </ul> 

7. 高级版 <a name="advanced"></a>

   
   ![编辑高级选项卡](attachments/charts/series-item-advanced.png)

    * **选项**: 使用 JSON 格式的 Plotly *系列选项* ; 这些选项只有在 *小部件* 标签 **高级 > 模式** 被设置为 *高级* 或 *开发者*：查看 [高级](#advanced-mode)， 以下：



#### 2.1.2 外观

**外观** 设置用于设置页面上图表的大小。

![通用图表外观标签](attachments/charts/widget-appearance.png)

* **宽度单位**: 用于 **宽度** 属性的单位类型 - *百分比* 或 *像素*

* **宽度**: 基于 **宽度单位** 设置的图表宽度或百分比

* **高度单位**: 用于 **高度的单位类型** 属性
  
    * **宽度百分比**: 设置宽度比
  * **像素**: 是一个绝对高度
  * **母离子居中**所占百分比：设置部件放置容器的高度
{{% alert type="warning" %}}When using **Percentage of parent** the parent container must have an **absolute** height, else nothing is displayed.{{% /alert %}}

* **高度**: 基于 **高度单位设置的高度或百分比**



#### 2.1.3 REST

将参数添加到REST 请求(见 [数据源](#data-source))。 默认情况下提供上下文ID和序列名称。

![通用图表REST 标签](attachments/charts/widget-rest.png)



#### 2.1.4 高级版 {#advanced-mode}

这个图表基于使用JSON配置图表的受欢迎的框架 plotly.js。 在高级和开发者模式中，您可以指定额外的 JSON ：解锁plotly.js的许多功能。 您也可以通过实时预览来做到这一点。

更多关于 plotly.js 和 options: https://plot.ly/javascript/。

![通用图表高级选项卡](attachments/charts/widget-advanced.png)

* **模式**: 您可以用三种不同的模式使用这些图表：
  
    * **基本**: 快速设置带有各种小部件选项的图表
  * **进阶**: 指定额外的 JSON 配置
  * **开发者**: 这将添加 **切换编辑器** 按钮到运行时的图表中，切换编辑器使用不同的高级配置选项
    
    ![](attachments/charts/toggle-editor.png)

* **布局选项**: 包含 Plotly 布局选项的 JSON
  
    * [示例：](charts-advanced-cheat-sheet#layout-all)
  * [完整引用](https://plot.ly/javascript/reference/#layout)
* **配置选项**: 包含 Plotly 配置选项的 JSON
  
    * [示例：](charts-advanced-cheat-sheet#config-options)
  * [文件](https://plot.ly/javascript/configuration-options/)
  * [完整引用](https://github.com/plotly/plotly.js/blob/master/src/plot_api/plot_config.js)



#### 2.1.5 普通的

这些是许多小部件共有的属性。 欲了解信息，请参阅 [常见于页面编辑器](common-widget-properties#common-properties) 的属性。



## 3 按图表类型配置 {#configuration-by-chart-type}

上面的属性在图表类型中是常见的。 在本节中，所描述的属性是针对图表类型的。



### 3.1 栏目 图

**系列新建或编辑**

1. **静态系列** 标签

    * **系列名称**: 这将在图表上的任何图例中显示

    * **列颜色**: 列中的 HTML 颜色, 例如绿色, #00FF00, rgb(0255,0), rgba(0,255,0, 0.5)



### 3.2 线图

**系列新建或编辑**

1. **外观** 标签

    * **直线模式**: *行* (没有显示数据点所在的标记) 或 *带有标记的行*

    * **行风格**: 用 *直线* 或 *曲线连接数据点 (样条)*

2. **静态系列** 标签

    * **系列名称**: 这将在图表上的任何图例中显示

    * **线性颜色**: 线性的 HTML 颜色, 例如绿色, #00FF00, rgb(0,255,0), rgba(0,255,0, 0.5)



### 3.3 饼状图

**图表属性**

* **图表类型**: 要使用的Pie 图类型，要么 *pie* 要么 *doughnut*

* **显示图例**: 在Pie 图表上显示一个图例

* **颜色**: 包括每个切片的颜色，例如绿色, #00FF00, rgb(0255,0), rgba(0,255,0, 0.5)

* **刷新间隔 (ms)**: 当设置为 0 刷新被禁用时以毫秒为间隔刷新图表



### 3.4 面积图

**系列新建或编辑**

1. **数据源** 标签

    * **系列名称**: 这将在图表上的任何图例中显示

2. **外观** 标签

    * **边框**: 否，是的，是有标记

    * **边框样式**: 海峡、曲线

3. **静态系列** 标签

    * **边框颜色**: 边界的 HTML 颜色，例如绿色, #00FF00, rgb(0255,0), rgba(0,255,0, 0.5)

    * **区域颜色**: 边界内区域的 HTML 颜色，例如绿色, #00FF00, rgb(0255,0), rgba(0,255,0, 0.5)。 默认是透明的边框颜色



### 3.5 条形图

**系列新建或编辑**

1. **静态系列** 标签

    * **系列名称**: 这将在图表上的任何图例中显示

    * **条颜色**: 条形状的 HTML 颜色，例如绿色, #00FF00, rgb(0255,0), rgba(0,255,0, 0.5)



### 3.6 时间系列图表

**系列新建或编辑**

1. **外观** 标签

    * **边框**: 否，是的，是有标记

    * **边框样式**: 海峡、曲线

    * **填充区域**: 数据点和 X轴之间填充区域: 是, 否

2. **静态系列** 标签

    * **系列名称**: 这将在图表上的任何图例中显示

    * **线性颜色**: 线性的 HTML 颜色, 例如绿色, #00FF00, rgb(0,255,0), rgba(0,255,0, 0.5)

    * **区域颜色**: 边界内区域的 HTML 颜色，例如绿色, #00FF00, rgb(0255,0), rgba(0,255,0, 0.5)。 默认是透明的线条颜色



### 3.7 热图

**缩放比例**

* **颜色**: 每个颜色应用的百分比以及相关的颜色。 必须指定至少两个值，否则使用默认颜色

* **显示比例尺**: 在图表上显示比例尺: 是 , 否

* **显示值**: 在图表上显示数据值: 是 , 否

* **字体值颜色**: 热图上显示的值的 HTML 颜色，例如绿色, #00FF00, rgb(0,255,0), rgba(0,255,0, 0.5)

* **X-轴标签**: 将显示在X-轴上的标签

* **Y-轴标签**: 将显示在Y-轴上的标签

* **平滑颜色**: 数据点之间逐步的颜色渐进：是 , 否



### 3.8 泡泡图

**系列新建或编辑**

1. **静态系列** 标签

    * **系列名称**: 这将在图表上的任何图例中显示

    * **系列颜色**[sic]: 气泡的颜色 例如，绿色，#00FF00, rgb(2255,0)



## 4 图表主题

高级JSON设置也可以通过您的 Mendix 应用根目录的主题文件夹在全局环境中添加。

在主题文件夹中添加 *.json* 文件，名为 *com.mendix.chats*。 JSON应采用以下格式：



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


{{% alert type="info" %}}

请谨慎使用，因为这里设置的配置将应用于您应用程序中图表的每个实例。  
只有小部件中设置的高级配置具有更高的优先级。

{{% /报警 %}}
