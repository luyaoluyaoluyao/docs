---
title: "报告参数"
parent: "报告小部件"
menu_order: 20
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/report-parameter.pdf)。
{{% /报警 %}}

## 1 导言

A **Report parameter** allows the end-user to select a parameter for the [data set](data-sets) that supplies the data for a [Report grid](report-grid). 该参数用于以不同方式过滤结果，以便相同的报告可以显示不同的数据集。

例如， 报表可以显示客户的订单数据，报告参数可以用来指定客户的数据应该显示。

报告参数显示在结构模式中，数据集参数名称（如果参数是对象，则显示属性）显示在方括号和彩色蓝色。

![在结构模式中报告参数](attachments/report-widgets/report-parameter.png)

{{% alert type="info" %}}
**报表参数** 不能用于类型 **日期和时间的数据集参数**。 日期和时间参数必须使用 [报告日期参数](report-date-parameter) 小部件过滤。

如果你在页面上添加报告参数小部件, 你还必须添加 [报告按钮](report-button) 小部件。 这使最终用户能够在指定参数后重新生成报告。
{{% /报警 %}}

## 2 报告参数属性

下面的图像显示了报告参数属性的示例：

{{% image_container width="300" %}}![在结构模式中报告参数](attachments/report-widgets/report-parameter-properties.png)
{{% /image_container %}}

报告参数属性由以下部分组成：

* [常用的](#common)
* [设计属性](#design-properties)
* [A. 概况](#general)

### 2.1 共同部分{#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 设计属性部分{#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 一般部分{#general}

#### 2.3.1 参数

**参数** 已设置为数据集参数，其值受此部件限制。 相应的数据集必须被页面上的报告小部件所使用。

#### 2.3.2 显示的属性

**只有当数据集参数是对象时，显示属性** 才可用。 显示属性指定在下拉选择中显示相应实体的属性。
