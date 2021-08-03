---
title: "系统操作"
category: "工作流"
menu_order: 40
tags:
  - "工作流"
  - "工作流"
  - "调用微流"
---

## 1 导言

工作流中的系统动作包括 **调用微流** 动作，用于调用选定的 [微流](microflows)。

![](attachments/workflows-system-actions/call-microflow-example.jpg)

## 2 调用微流程属性

**调用 microflow** 属性的示例在下面的图像中表示：

![调用微流程属性](attachments/workflows-system-actions/call-microflow-properties.jpg)

调用微流程属性由以下部分组成：

* [A. 概况](#general)
* [参数](#parameters)
* [成果](#outcomes)

### 2.1 一般部分 {#general}

**常规** 部分允许您定义一个动作的字幕并选择一个微流。

下表说明了该节属性：

| 财产 | 描述                                              |
| -- | ----------------------------------------------- |
| 标题 | **标题** 描述了这个元素中发生的情况。 它显示在工作流编辑器中，使工作流更容易读取和理解。 |
| 微流 | 这个元素所调用的微流。                                     |

### 2.3 参数部分 {#parameters}

参数传递数据到元素。 当前参数只能在 Studio Pro中选择和配置。 欲了解更多信息，请参阅 [通话微流程](/refguide/call-microflow)。

### 2.2 成果科 {#outcomes}

**结果** 取决于微流程的返回值。 例如，对于布尔值，您有 **真实** 和 **false** 结果。 当计数时 - 每个计数值的结果和未分配值时的空结果。

## 3 阅读更多

* [一般活动](workflows-general-activities)