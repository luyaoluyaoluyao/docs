---
title: "报告日期参数"
parent: "报告小部件"
menu_order: 30
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/report-date-parameter.pdf)。
{{% /报警 %}}

## 1 导言

**报告日期参数** 允许最终用户为 [数据集指定日期和时间参数](data-sets) 提供一个 [报告网格](report-grid) 的数据。 该参数用于以不同方式过滤结果，以便相同的报告可以显示不同的数据集。

例如，报告可能显示客户在选定时期的订单数据。 和报表日期参数可以用来指定应选择的时间段。

{{% alert type="info" %}}
您可以添加更多字段到报表日期参数小部件，以使最终用户更容易选择日期范围。 更多信息请参阅 [附加报告日期参数](#additional-fields)。
{{% /报警 %}}

报告日期参数显示在结构模式中，数据集参数名称显示在方括号和彩色蓝色。 **从** 和 **到** 以蓝色显示的日期是示例来表示这些是日期字段。

![在结构模式中报告日期参数](attachments/report-widgets/report-date-parameter.png)

{{% alert type="info" %}}
如果您在页面上有报告日期参数小部件， 您还必须添加 [报告按钮](report-button) 小部件，以便最终用户能够在指定参数后重新生成报告。
{{% /报警 %}}

## 2 个报告日期参数属性

报表日期参数属性的示例在下面的图像中表示：

{{% image_container width="300" %}}![在结构模式中报告日期参数](attachments/report-widgets/report-date-parameter-properties.png)
{{% /image_container %}}

报表日期参数属性由以下部分组成：

* [常用的](#common)
* [设计属性](#design-properties)
* [A. 概况](#general)

### 2.1 共同部分{#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 设计属性部分{#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 一般部分{#general}

#### 2.3.1 参数

**参数** 已设置为类型日期和时间的数据集参数，其值受此部件限制。 相应的数据集必须被页面上的报告小部件所使用。

#### 2.3.2 每行字段

**每行** 个字段指定了多少 [日期范围字段](date-range-field) 可以一行放在彼此旁边。 数据范围字段总是有两行可用的。 更多信息请参阅 [附加报告日期参数](#additional-fields)。

#### 2.3.3 从字幕

**从** 中指定了从</strong> 日期选择器对 **显示的文本。 如果最终用户可以选择报告中应列出数据的起始期。</p>

#### 2.3.4 标题

**到** 指定了显示在 **到** 日期选择器中的文本。 如果最终用户可以选择报告应载列数据的期限的终点。

#### 2.3.5 显示从/到

Set **Show from/to** to **Yes** if the **from** and **to** field results should be shown on the report page.

Set this to **No** if the **from** and **to** field results should not be shown. 在这种情况下，过滤器必须使用 [日期范围字段](date-range-field) 添加到报告日期参数。

#### 2.3.6 最小值。 年份

**最小. 年** 是最终用户可以在 **年** [日期范围](date-range-field) 中选择的最早年份。

{{% alert type="warning" %}}
**分钟内的值。 年** 不会阻止最终用户在 **中选择较早的日期。从** 或 **到** 报表日期参数小部件中的字段。 它仅适用于 *年* 日期范围域。
{{% /报警 %}}

#### 2.3.7 最大值 年

**最大值。 年** 是最终用户可以在 **年** [日期范围](date-range-field) 中选择的最后一年。

{{% alert type="warning" %}}
最大值 ** 年** 不会阻止最终用户在 **中选择稍后日期。从** 或 **到** 报表日期参数小部件中的字段。 它仅适用于 *年* 日期范围域。
{{% /报警 %}}

## 附加报告日期参数{#additional-fields}

您可以添加额外的字段，允许最终用户轻松选择日期范围，而无需同时输入 **从** 和 **到** 日期。 欲了解更多信息，请参阅 [日期范围字段](date-range-field)。
