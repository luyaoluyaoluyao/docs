---
title: "输入部件"
parent: "页面"
menu_order: 30
description: "可以添加到页面以查看和编辑对象属性的部件。"
tags:
  - "studio pro"
  - "输入小部件"
  - "小部件"
  - "参考选择器"
  - "引用集"
  - "关联"
  - "编辑"
  - "data input"
---

## 1 导言

输入小部件将数据显示给最终用户，选择允许他们编辑数据。

输入部件需要链接到实体的属性才能运行。 因此，它们必须放在一个包含该实体类型对象的数据部件中。

例如，输入小部件可以放置在 [数据视图](data-view) 中：

![包含小部件的数据视图](attachments/input-widgets/data-view.png)

有几个不同的输入小部件，这些小部件用于不同的 [数据类型](data-types) 和不同类型的 [关联](associations)。 输入小部件类别包含以下部件：

*   [文本框](text-box) - 显示并且可选的 允许最终用户从 *数字* 或 *字符串类* 属性添加或编辑文本数据：

    ![包含名称属性的文本框](attachments/input-widgets/text-box.png)

*   [文本区域](text-area) - 显示并且可选择允许最终用户从 *字符串中添加或编辑长文本数据* 属性：

    ![含有笔记属性的文本区域](attachments/input-widgets/text-area.png)

*   [Drop-own](drop-down) — — 显示当前的值，并可选地显示 允许最终用户在 *枚举* 属性中从选项列表中选择一个选项：

    ![下拉包含区域属性](attachments/input-widgets/drop-down.png)

*   [勾选框](check-box) — — 显示当前的值，并可选的 允许最终用户设置 *布尔值* 属性为 `true` 或 `false`：

    ![显示个人属性的复选框](attachments/input-widgets/check-box.png)

*   [单选按钮](radio-buttons) — — 显示当前值，并可选. 允许最终用户从选项列表中选择一个选项，在 *枚举* 属性或一个 *布尔值的值* 属性：

    ![显示首选联系时间和个人属性的单选按钮](attachments/input-widgets/radio-buttons.png)

*   [日期选择器](date-picker) - 展示并且可选择允许最终用户选择 *日期和时间* 从日历中选择的属性：

    ![显示最后联系的属性的日期选择器](attachments/input-widgets/date-picker.png)

*   [参考选择器](reference-selector) — — 演示并且可选的 允许最终用户选择 *一对一* 或 *一对数* 关联，使用一个 *字符串* *数字*, *枚举*, 或 *日期和时间* 相关对象的属性：

    ![关联公司的公司名称属性的参考选择器](attachments/input-widgets/reference-selector.png)

*   [参考集选择器](reference-set-selector) — — 包含一个或多个属性并且可选的列表 允许最终用户添加和删除关联对象通过 *多到多个* 关联：

    ![引用设置选择器显示相关产品的详细信息](attachments/input-widgets/reference-set-selector.png)

*   [输入参考集选择器](input-reference-set-selector) — — 显示属性并可选. 允许用户添加和删除关联对象通过 *多到多个* 关联的对象：

    ![输入参考集选择器显示关联产品的名称属性](attachments/input-widgets/input-reference-set-selector.png)

{{% alert type="info" %}}
欲了解更多关于数据类型的信息，见 [数据类型](data-types)。

关于关联及其属性的更多信息，请参阅 [关联](associations)。
{{% /报警 %}}

## 2 执行基本函数

{{% snippet file="refguide/performancing-basic-functions-widgets.md" %}}

## 3 阅读更多

* [页](page)
* [页 次](页面)
* [数据类型](data-types)
* [社会联系](关联)
  