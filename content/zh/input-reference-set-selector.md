---
title: "输入参考集选择器"
parent: "输入小部件"
menu_order: 90
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/input-reference-set-selector.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}The **input reference set selector** widget is not supported on native mobile pages.{{% /alert %}}

## 1 导言

**输入参考集选择器** 用于允许最终用户通过选择相关对象来显示或选择多到多个(参考集) [关联的值](associations)。

必须将输入参考集选择器放置在 [数据小部件](data-widgets) 中。

例如，您可以将客户分组成群，每个客户可以属于几个群组。 每个组可以有许多客户。 **客户** **组** 的实体具有多对多(参考集)关系。 可以使用输入参考设置选择器来选择客户所属的组。

您可以对输入参考集选择器做什么取决于关联的 **所有者**。 在下面的示例域模型中 **所有者** 已设置为 **默认** (在关联属性 **'客户' 对象指的是'组' 对象**)。

![输入参考值的域模型在客户(父)与所有者为默认值的群组之间设置选择器(如： 客户引用到群组)](attachments/input-reference-set-selector/domain-model-owner-default.png)

您可以在客户数据视图中放置一个输入参考集选择器，允许用户选择客户所属的组。 然而，由于客户是协会的所有者， 您不能在组数据视图中放置一个输入参考集选择器来选择组中的客户。

允许您将一个组添加到客户，并将一个客户添加到一个客户组， 您需要将关联的所有权设置为 **这两者都是**。

![输入参考值的域模型在客户(父级)和所有者都是“两者”的组之间设置选择器(如： 客户和组相互参照)](attachments/input-reference-set-selector/domain-model-owner-both.png)

在输入参考集选择器中，要显示的属性路径(关联、关联实体) 显示在输入参考集选择器中，方括号和彩色蓝色。

例如，使用上述域模型。 以下输入参考设置选择器允许最终用户通过设置关联 **Customer_Group** 来将客户与一个或多个组联系起来。 这是通过选择 **组的 **名称**(s) 进行的，**(s) 与当前的 **客户** 相关联。

![](attachments/input-reference-set-selector/input-reference-set-selector.png)

## 2 属性

以下图像是输入参考集选择器属性的示例：

{{% image_container width="250" %}}![](attachments/input-reference-set-selector/input-reference-set-selector-properties.png)
{{% /image_container %}}

参考集选择器属性由以下部分组成：

* [常用的](#common)
* [数据源](#data-source)
* [设计属性](#design-properties)
* [编辑性](#editability)
* [事件](#events)
* [A. 概况](#general)
* [标签](#label)
* [可选对象](#selectable-objects)
* [可见性](#visibility)

### 2.1 共同部分 {#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 数据源部分 {#data-source}

{{% snippet file="refguide8/data-source-section-link.md" %}}

属性路径指定了关联实体的哪个属性在参考集选择器中显示。 路径必须遵循一个关联，类型参考集，从数据视图的实体开始。

### 2.3 设计财产科 {#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.4 可编辑部分 {#editability}

{{% snippet file="refguide8/editability-section-link.md" %}}

### 2.5 事件部分 {#events}

更改属性指定了离开部件时要执行的动作， 通过使用 <kbd>Tab</kbd> 键，或点击另一个部件，在值被更改后再点击。

{{% snippet file="refguide8/events-section-link.md" %}}

### 2.6 一般财产 {#general}

#### 2.6.1 选择页 次

选择页面属性决定当输入参考选择器被点击时显示哪个页面。 此页面可以用于从可选对象列表中选择关联的对象。 此页面应包含一个数据网格、模板网格或与输入参考集选择器连接到同一个实体的列表视图。

如果输入参考集选择器永远不能编辑，则不需要选择页面。

See the [Show a Page](on-click-event#show-page) section of *On Click Event & Events Section*. 注意选择的页面必须有 [弹出式布局](layout#layout-type)。

{{% alert type="info" %}}
您可以通过右键点击小部件并选择 **生成选择页面…** 来生成一个新页面以显示。
{{% /报警 %}}

### 2.7 标签部分 {#label}

{{% snippet file="refguide8/label-section-link.md" %}}

### 2.8 可选物体部分 {#selectable-objects}

可选对象部分中的属性决定了最终用户可以从中选择的对象。 您可以添加 **XPath 约束**，或使用</strong> 路径约束的 **路径。</p>

欲了解更多信息，请参阅 *参考选择器* 的 [XPath](reference-selector#xpath-constraints) 部分。

{{% alert type="info" %}}
您不能在输入参考集选择器中使用微流来定义可选择的对象。
{{% /报警 %}}

### 2.9 可见性科 {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}
