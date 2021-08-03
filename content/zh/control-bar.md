---
title: "控制栏"
parent: "格子"
menu_order: 30
tags:
  - "studio pro"
  - "控制栏"
  - "添加按钮"
  - "取消选择所有按钮"
  - "导出到 csv 按钮"
  - "网格动作按钮"
  - "网格新按钮"
  - "删除按钮"
  - "搜索按钮"
  - "选择按钮"
  - "选择所有按钮"
  - "数据网格"
  - "模板网格"
  - "引用设置选择器"
  - "控制栏按钮"
aliases:
  - /refguide/附加按钮.html
  - /refguide/deselect-all-buton.html
  - /refguide/export-to-csv-buton.html
  - /refguide/export-excel-buton.html
  - /refguide/grid-action-buton.html
  - /refguide/grid-new-buton.html
  - /refguide/remove-button.html
  - /refguide/search-button.html
  - /refguide/select-all-buton.html
  - /refguide/select-button.html
---

## 1 导言

[模板网格](template-grid), [数据网格](data-grid), 和 [参考设置选择器](reference-set-selector) 允许您通过按钮操作显示的物体。 默认情况下，这两个网格将使用 [搜索](#search-button), [新](#create-button)和 [编辑](#grid-action-button)和 [删除控制栏中的](#grid-action-button) 按钮：

![数据网格控制栏](attachments/data-widgets/control-bar-example.png)

控制栏还可以包括一些选择选项和电子表格导出按钮，以及自定义动作的微流按钮。

## 2 控件栏按钮

控制栏按钮的大多数属性与按钮部件的属性相同。 关于按钮属性的更多信息，请参阅 [按钮属性](button-properties)。

下面的部分描述了每个控制栏按钮的目的及其特定属性（如果有的话）。

### 2.1 搜索按钮 {#search-button}

**搜索栏切换** 按钮(默认标题 **搜索**)打开或隐藏 [搜索栏](search-bar) 只有当网格的 **显示搜索栏** 属性设置为 *按钮(最初打开)* 或 *按钮(最初关闭)* 时，它才存在。

{{% alert type="info" %}}
在 [引用设置选择器](reference-set-selector) 中，默认将没有设置搜索字段。 查看 [搜索栏](search-bar) 了解更多有关搜索字段的信息。
{{% /报警 %}}

### 2.2 添加按钮 {#add-button}

**添加** 按钮只能在 [参考设置选择器](reference-set-selector) 中使用。 通过此按钮，用户可以选择必须添加到参考集选择器中的对象。

#### 2.2.1 页

**页面** 属性指向用户点击此按钮后显示的页面。 用户可以使用此页面选择必须添加到参考集选择器的对象。 此页面应包含一个数据网格、模板网格或与参考集选择器连接到同一个实体的列表视图。

您可以使用一个现有的页面或者您可以通过以下两者生成相应的页面：

1. 右键单击添加按钮并选择 **生成页面…**
2. 为页面选择 **个新的**。

这两个选项都允许您创建一个具有正确格式的页面供添加按钮使用。 当然，一旦生成，您可以编辑页面以满足您自己的要求。

See the [Show a Page](on-click-event#show-page) section of *On Click Event & Events Section*. 注意选择的页面必须有 [弹出式布局](layout#layout-type)。

### 2.3 创建按钮 {#create-button}

**创建** 按钮(默认标题 **新**) 允许最终用户在网格或参考设置选择器中创建新对象。

#### 2.3.1 实体

**实体** 属性决定了该按钮应该创建一个实例的实体。 如果连接到网格或参考设置选择器的实体没有专业化， 页面编辑器将自动为您设置此属性。 否则，您将不得不选择自己的专业。

例如，您有一个实体 *车辆* 和两个专业： *自行车* 和 *汽车* 在网格中，当您选择 *辆车* 作为数据源， 您必须指定是否有 *车辆*a *自行车* 或 *车* 将在点击 **创建** 按钮时创建。 您甚至可以有三个 **新的** 按钮，每个专业化都有一个。

### 2.4 动作按钮 {#grid-action-button}

动作按钮是一个可以执行各种动作的按钮，如调用微流程或打开一个页面。 **编辑** and **删除** 按钮是默认在数据网格和模板网格控制栏中创建的动作按钮。 关于动作按钮的更多信息，见 [按钮小部件](button-widgets)。

### 2.5移除按钮 {#remove-button}

**删除** 按钮是参考集选择器特定的按钮。 使用此按钮，最终用户可以删除已添加到参考集选择器的对象。 关于参考集选择器的更多信息，请参阅 [参考集选择器](reference-set-selector)。

### 2.6 选择按钮 {#select-button}

**选择** 按钮可以确认当网格用于为参考选择器或参考设置选择器选择对象时对网格行的选择。 For this reason, the **Select** button can only be placed on a grid in a page that is connected to a reference selector or to the **Add** button of a reference set selector.

### 2.7 选择所有按钮 {#select-all-button}

**选择所有** 按钮允许最终用户在网格或参考集选择器中选择所有对象。

#### 2.7.1 选择类型

**选择类型** 属性决定 **选择所有** 按钮是否应该选择当前页面上的对象 或者所有页面上的对象：

| 值           | 描述                 |
| ----------- | ------------------ |
| 选择页面 *(默认)* | 点击此按钮选择当前页面上的所有对象。 |
| 选择所有        | 点击此按钮选择所有对象。       |

{{% alert type="warning" %}}

Due to technical limitations, a button with the **Select all** selection type cannot be combined with [Remove](#remove-button), [Delete](#grid-action-button), or [Select](#select-button) buttons.

**编辑** 按钮总是表现就好像选择类型是 **选择页面**不论 **的实际设置如何，请选择所有用于选择对象的** 按钮。

{{% /报警 %}}

### 2.8 取消选择所有按钮 {#deselect-all-button}

**取消选择所有** 按钮允许用户取消选择网格中的所有行或参考设置的选择器。

### 2.9 导出到Excel按钮 {#export-to-excel-button}

**导出到 Excel** 按钮允许最终用户将网格内容或参考设置选择器导出到 Excel 文件。

{{% alert type="info" %}}

Excel导出函数仅在有 [XPath 数据源](xpath-source) 的列表小部件中可用。

您用于搜索字段和排序的限制也将被导出。

{{% /报警 %}}

#### 2.9.1 行数上限

**最大行** 属性表示导出时数据网格中的最大行数。 防止最终用户出口大量数据，可能会给服务器带来沉重负担。

#### 2.9.2 日期出口格式

**日期导出格式** 属性定义了格式日期将被导出。 可能的备选办法如下：

* **日期值** *(默认)*  - 日期值被导出为实际日期， 这样可以使用 Excel 日期函数，比如排序
* **文本** - 日期值正像数据网格中显示的一样导出

{{% alert type="warning" %}}

选择 **日期值**时，日期将只显示在您的 Windows 账户的时区。 因为Excel不支持定义特定时区。

{{% /报警 %}}

### 2.10 导出到 CSV 按钮 {#export-to-csv-button}

**导出到 CSV** 按钮允许最终用户将网格内容或参考集选择器导出到 CSV 文件。

{{% alert type="info" %}}

导出到 CSV 函数只在包含 [XPath 数据源](xpath-source) 的列表小部件中可用。

您用于搜索字段和排序的限制也将被导出。

{{% /报警 %}}

#### 2.10.1 十进制分隔符

**十进制分隔符** 是一个用于将小数点数值中的分片部分和整个部分分开的字符串。

默认： *。*

#### 2.10.2 小组分隔符

**分组分隔符** 是一个用来分隔大数组数字的字符串。

默认： *,*

#### 2.10.3 分隔符

**分隔符** 是用于在生成的 CSV 文件中对数值进行分隔的字符串。

默认： *;*

#### 2.10.4 行数上限

**最大行** 属性表示导出时数据网格中的最大行数。 防止最终用户出口大量数据，可能会给服务器带来沉重负担。

#### 2.10.5 生成 Excel 分隔符提示

**生成Excel分隔符提示** 属性为CSV文件头添加了一个额外的行，以告知Excel分隔符是什么。 这解决了与 Excel 和本地化的兼容问题。

#### 2.10.6 使用网格日期格式

当 **启用网格日期格式属性** 时，将使用列的日期格式。 当此属性被禁用时，使用 Excel 识别为日期的格式 (yyy-MM-dd)。

## 3 阅读更多

* [按钮属性](button-properties)
* [数据网格](数据网格)
* [模板网格](template-grid)
* [参考设置选择器](reference-set-selector)