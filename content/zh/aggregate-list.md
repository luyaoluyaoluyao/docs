---
title: "聚合列表"
parent: "列表活动"
menu_order: 1
tags:
  - "studio pro"
  - "聚合"
  - "Sum"
  - "平均值"
  - "计数"
  - "最小值"
  - "最大值"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/aggregate-list.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。
{{% /报警 %}}

## 1 导言

**聚合列表** 活动可以用来计算对象列表中的合计值。 这项活动支持的总值是：

* 平均值
* 计数
* 最大值
* 最小值
* sum

## 2 属性

汇总列表属性的示例在下面的图像中显示：

![汇总列表属性](attachments/list-activities/aggregate-list-properties.png)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

汇总列表属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动部分{#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 名单

要汇总的列表名称。

### 3.2 职能

定义应用哪一种聚合。

| 值   | 描述             |
| --- | -------------- |
| 平均值 | 对象列表中所有属性的平均值。 |
| 计数  | 列表中对象的总数。      |
| 最小值 | 对象列表中属性的最小值。   |
| 最大值 | 对象列表中所有属性的最大值。 |
| Sum | 对象列表中所有属性的值之和。 |

### 3.3 属性

定义列表中对象的哪个属性用于汇总。 这必须是一个数值属性(Long, Integer 或 Decimal)。

{{% alert type="info" %}}
当使用“计数”函数时，没有必要选择一个属性，因为它只是计算列表中的对象数量。
{{% /报警 %}}

### 3.4 变量名称

存储聚合结果的变量名称。 此变量将有一个数字数据类型，取决于所选函数。

## 4 通用部分{#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}
