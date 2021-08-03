---
title: "图表部件"
parent: "页面"
tags:
  - "图表"
  - "任何图表"
  - "桌面模型"
  - "页 次"
---

## 1 导言

您可以在您的应用页面中添加范围广泛的图表来直观显示数据系列。

[基本图表](#basic-charts) 已经包含在 Mendix 应用程序模板中，基于 Atlas UI 。 他们可以通过从 Mendix Marketplace 下载到其他Mendix 应用程序中：https://marketplace.mendix.com/link/component/105695。

[任意图表](#any-chart) 给予更多的控制，并实现了 [plotly.js](https://plot.ly/) 的所有功能。 [任何图表](/appstore/modules/any-chart) 模块都可以通过从 Mendix 市场下载来包含在您的 Mendix 应用程序中。

## 2 基本图表 {#basic-charts}

使用 Mendix 图表，您可以快速创建美丽的图表。 图表包括：

* **区域** 图表 - 一个填充到X轴的线图
* **条** 图表 - 水平条形状，分组或堆叠的
* **Bubble** 图表 -- 在你的图表中添加一个尺寸尺寸
* **列** 图表 - 垂直条形状，分组或堆叠的
* **热映射** - 在 2D 矩阵中以颜色显示数据值
* **直线** 图表 - 直线或曲线直线，不论是否有标记
* **Pie** 图表 — — 一张Pie或一张坚固的图表
* **时间序列** - 显示按时间排序的数据

小部件包含几个设置，可以在 Moderr 中更改以自定义外观和感受，并提供对点击事件和自定义工具提示的支持。 查看 [海图配置](charts-configuration) 来学习如何配置 Mendix 字符串。

**动态系列图表**

从基本图表的1.4版本中，您可以创建带有可变数系列数据的海图。 关于如何做到这一点的说明，请参阅 [如何创建动态系列图](/howto7/extensibility/charts-dynamic-series)。

## 所有图表 {#any-chart}

使用 *任何图表* 可以构建所有可以使用 Plotly.js 构建的图表类型。 如果你想要构建一个在基本图表中不可用的图表， *任何图表* 都是你的朋友。

绘图图需要基于 JSON 的配置，因此 *任何图表* 都有JSON 作为输入参数。 您可以通过JSON结构文档在您的微流程中动态创建此 JSON ，并在 *任何图表* 配置中使用它。 还可以定义与动态JSON合并的静态JSON配置。

这个模块还包含了一些可以启发和起点的构件。 如果您想要创建一个新的图表，我们建议您签出 plotly.js 网站。

查看 [任何图表小部件](charts-any-configuration) 了解如何配置 *任何图表* 部件。

## 4 阅读更多

* [任何图表配置](charts-any-configuration)
* [任何图表建筑块](charts-any-building-bocks)
* [任何图表作弊表](charts-any-cheat-sheet)
* [基本图表作弊表](charts-advanced-cheat-sheet)
