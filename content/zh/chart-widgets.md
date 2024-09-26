---
title: "图表部件"
parent: "页面"
menu_order: 70
tags:
  - "图表"
  - "任何图表"
  - "Studio Pro"
  - "页 次"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/chart-widgets.pdf)。
{{% /报警 %}}

## 1 导言

图表小部件允许您在应用页面上视觉显示数据序列，图表范围很广。

[基本图表](#basic-charts) 已经包含在 Mendix 应用程序模板中，基于 Atlas UI 。 他们可以通过从 Mendix Marketplace 下载到其他 Mendix 应用程序中(详细信息，请参阅 [Charts](/appstore/widgets/charts))。 基本图表以绘图1.47.4为基础。

[任何图表](#any-chart) 提供了更多的控制，并允许更灵活地使用 [plotly.js](https://plot.ly/) 的功能。 [任何图表](/appstore/modules/any-chart) 小部件都可以包含在您的应用中。 查看小部件文档以了解支持哪个版本的 plotly.js。

## 2 基本图表 {#basic-charts}

使用 Mendix 图表，您可以快速创建美丽的图表。 图表包括：

* **区域** 图表 - 一个填充到X轴的直线图 * ower{% image_container width="200" %}}![Sample Area Chart](attachments/charts/sample-area-chart.png){{%/image_container %}}
* **Bar** chart – horizontal bars, grouped or stacked {{% image_container width="200" %}}![Sample Bar Chart](attachments/charts/sample-bar-chart.png){{% /image_container %}}
* **Bubble** 图表 - 添加一个尺寸尺寸尺寸到您的图表 然后无法{% image_container width="200" %}}![Sample Bubble Chart](attachments/charts/sample-bubble-chart.png){{%/image_container %}}
* **Column** chart – vertical bars, grouped or stacked {{% image_container width="200" %}}![Sample Column Chart](attachments/charts/sample-column-chart.png){{% /image_container %}}
* **热映射** — — 在 2D 矩阵中显示以颜色表示的数据值。\n{% image_container width="200" %}}![Sample Heat Map](attachments/charts/sample-heat-map.png){{% /image_container %}}
* **第** 行图表——直线或曲线直线，不论是否有标记 ●{% image_container width="200" %}}![Sample Line Chart](attachments/charts/sample-line-chart.png){{%/image_container %}}
* **Pie** 图表 — — 一张Pie 或 doughnut图。**{% image_container width="200" %}}![Sample Pie Chart](attachments/charts/sample-pie-chart.png){{% /image_container %}}</li>
* **时间序列** — — 显示数据订单时序，按时间 Power{% image_container width="200" %}}![Sample Time Series](attachments/charts/sample-time-series.png){{%/image_container %}}</ul>

小部件包含几个设置，可以在 Studio Pro 中更改以自定义外观和感受，并且提供对点击事件和自定义工具提示的支持。 查看 [海图配置](charts-configuration) 来学习如何配置 Mendix 字符串。

如果标准图表设置不足以满足您的目的， 查看 [海图高级作弊Sheet](charts-advanced-cheat-sheet) 获取关于您基本图表高级配置的信息。

请注意，配置图表时只能使用多达1.47.4个版本的 plotly.js。

**动态系列图表**

从基本图表的1.4版本中，您可以创建带有可变数系列数据的海图。 关于如何做到这一点的说明，请参阅 [如何创建动态系列图](/howto8/front-end/charts-dynamic-series)。

## 所有图表 {#any-chart}

使用 *任何图表* 您都可以构建所有可以通过Ploty 实现的图形类型。 s 到小部件支持的版本(更多细节请参阅“应用市场”中的小部件描述)。 如果你想要构建一个在基本图表中不可用的图表， *任何图表* 都是你的朋友。

{{% image_container width="400" %}}![Sample Contour Chart made with Any Chart](attachments/charts/contour.png){{% /image_container %}}

绘图图需要基于 JSON 的配置，因此 *任何图表* 都有JSON 作为输入参数。 您可以通过JSON结构文档在您的微流程中动态创建此 JSON ，并在 *任何图表* 配置中使用它。 还可以定义与动态JSON合并的静态JSON配置。

This module also contains several [building blocks](charts-any-building-blocks) for inspiration and as starting point. 如果您想要创建一个新的图表，我们建议您签出 plotly.js 网站。

查看 [任何图表小部件](charts-any-configuration) 了解如何配置 *任何图表* 部件。

[任何海图作弊模式](charts-any-cheat-sheet) 列出了最常见的图表类型以及在任何图表中创建图表所需的 JSON。

## 4 正在执行基本函数

{{% snippet file="refguide8/performancing-basic-functions-widgets.md" %}}

## 5 本部分的文件

以下文件解释如何更详细地使用图表：

* [图表配置](charts-configuration)
* [海图高级作弊表](charts-advanced-cheat-sheet)
* [任何图表部件](charts-any-configuration)
* [任何图表建筑块](charts-any-building-blocks)
* [任何图表作弊表](charts-any-cheat-sheet)
