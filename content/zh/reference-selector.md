---
title: "参考选择器"
parent: "输入小部件"
menu_order: 70
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/reference-selector.pdf)。
{{% /报警 %}}

## 1 导言

一个 **参考选择器** 用于显示并且可选的。 允许最终用户通过选择关联对象选择一对一或一对一 [association](associations) 的值。

引用选择器必须放置在 [数据小部件](data-widgets) 中。 从这个数据小部件检索到的对象必须在一对多的关联的 *多* 末端， 或在一对一的协会的任何一端。

例如，如果你有一名雇员，他们将为一家公司工作。 一个公司可能有许多雇员。 实体 **员工** and **Company** 有一个一对多的关联， **员工公司**, 您可以通过推荐选择一个公司从员工中选择。

![](attachments/reference-selector/reference-selector-domain-model.png)

在参考选择器中，将显示的关联对象属性的名称将显示在参考选择器中。 在方括号内的方括号内的方括号内的方括号内的方括号内的方括号内的方括号内的方括号内的方括号。

例如，下列提及使最终用户能够看到和看到组合。 通过选择 **公司名称** 为当前的 **员工** 选择关联 **员工公司**。

![](attachments/reference-selector/reference-selector.png)

{{% alert type="info" %}}
如果您只想 _显示_ 信息，您也可以使用 [文本框](text-box)。 这具有额外的优势，您可以从一个通过多个关联步骤链接的对象中选择一个属性。
{{% /报警 %}}

## 2 属性

下面的图像是参考选择器属性的示例：

{{% image_container width="400" %}}![](attachments/reference-selector/reference-selector-properties.png)
{{% /image_container %}}

参考选择器属性由以下部分组成：

* [常用的](#common)
* [数据源](#data-source)
* [设计属性](#design-properties)
* [编辑性](#editability)
* [事件](#events)
* [格式化](#formatting)
* [A. 概况](#general)
* [标签](#label)
* [可选对象](#selectable-objects)
* [验证](#validation)
* [可见性](#visibility)

### 2.1 共同部分{#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 数据源部分{#data-source}

{{% snippet file="refguide8/data-source-section-link.md" %}}

属性路径指定关联实体的属性在参考选择器中显示。 路径必须遵循一个类型引用关联，从数据视图实体开始。

### 2.3 设计属性部分{#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.4 可编辑性部分{#editability}

{{% snippet file="refguide8/editability-section-link.md" %}}

### 2.5 事件部分{#events}

更改属性指定了离开部件时要执行的动作， 通过使用 <kbd>Tab</kbd> 键，或点击另一个部件，在值被更改后再点击。

{{% snippet file="refguide8/events-section-link.md" %}}

### 2.6 格式化部分{#formatting}

格式化部分仅适用于数字属性的显示方式。 这些是以下数据类型的属性：

* 小数
* 整数
* 长

{{% snippet file="refguide8/numeric-form-link.md" %}}

### 2.7 一般部分{#general}

#### 2.7.1 选择使用{#select-using}

{{% alert type="warning" %}}The **Select using** property is not shown for native mobile pages. 本机移动页面仅支持 **下拉** 选择方法{{% /提醒 %}}

参考选择器允许最终用户使用下拉菜单或弹出页面选择对象。 如果您选择使用一个页面， 下拉功能将被窗口右侧打开页面选择弹出窗口的按钮替换。

| 值             | 描述           |
| ------------- | ------------ |
| **下拉** *(默认)* | 使用下拉菜单选择参考。  |
| **页**         | 使用弹出页面选择参考值。 |

* 使用 [下拉](#drop-down) 选择的优点是，它效率很高——最终用户可以使用较少的按键进行选择， 因为所有信息在同一页面
* 使用 [页面](#page) 选择的优点是最终用户可以搜索物体。 关于每个对象的更多信息可以显示——如果有很多对象要从中选择（例如，） 超过 20, 建议使用一个页面进行选择

{{% alert type="warning" %}}
**下拉** 参考选择器和 **页面** 参考选择器之间的功能差异很小。 当更改一个同时包含在第二个下拉菜单或页面中的链接列表的参考选择器项时， **页面** 参考选择器未被清除，因为它有 **下拉** 参考选择器。
{{% /报警 %}}

#### 2.7.1.1 下移 {#drop-down}

下拉引用选择器类似于枚举的 [下拉](drop-down) 除非它允许用户从可以与当前对象相关联的对象列表中选择， 而不是从枚举中列出的值。

参考选择器显示可以通过关联关联链接到当前实体的对象的属性。 所选属性对于每个可以关联的对象都应该是唯一的，否则最终用户将难以选择正确的属性。 例如， 您应该显示公司 _name_ (最好是唯一的) 而不是公司 _区域_ (这可能不是公司唯一的)

#### 2.7.1.2 导 言 {#page}

选择使用一个页面，将按钮链接到小部件右侧的弹出页面，用于进行选择。 您必须选择要显示的页面使用 [选择页面](#select-page) 属性。

#### 2.7.2 空选项标题

{{% alert type="info" %}}
只有在 [选择使用](#select-using) 设置为 **下拉** 时才显示这一点。
{{% /报警 %}}

此属性在下拉引用选择器显示给最终用户的空选项中指定了标题。 这是一个 [个可翻译的文本](translatable-texts)。

填写空选项的标题可以提高应用程序的用户体验。 它还帮助最终用户使用屏幕阅读器轻松地操作应用程序。

#### 2.7.3 选择页面{#select-page}

{{% alert type="info" %}}
只有使用 [选择使用](#select-using) 设置为 **页面** 时才显示这一点。 因此，本机移动页面不支持选择页面。
{{% /报警 %}}

选择页面属性决定在使用选择页面按钮时打开哪个页面。

此页面可以用来从所有可能的对象列表中选择一个关联的对象。 此页面应包含一个数据网格、模板网格或与输入参考集选择器连接到同一个实体的列表视图。

建议您通过右键单击小部件和选择 **生成选择页面…** 来生成一个新页面。 如果需要，您可以编辑生成的页面。

![通过右键单击小部件生成一个选择页面](attachments/reference-selector/generate-select-page.png)

See the [Show a Page](on-click-event#show-page) section of *On Click Event & Events Section*. 注意选择的页面必须有 [弹出式布局](layout#layout-type)。

**页面标题**

{{% alert type="info" %}}
**页面标题** 仅在 **属性** 对话框中可用，而不是 **属性** 面板。
{{% /报警 %}}

您可以覆盖您打开的页面的标题，例如指明从哪里打开它。

通过检查 **重写页面标题** 复选框来激活这个功能。

#### 2.7.4 转到页 次

本机移动页面不支持本机页面{% alert type="warning" %}}Go-to 页面。{{%/提醒 %}}

转到页面使终端用户能够快速访问当前选中对象的更详细的概览。

此属性决定向用户显示哪个页面。 页面应该包含数据源 **类型** 设置为 **Context** 和 **Enty (path)** 设置为参考选择器选择的数据。

建议您通过右键单击小部件并选择 **生成转入页面…** 如果需要，您可以编辑生成的页面。

**页面标题**

{{% alert type="info" %}}
**页面标题** 仅在 **属性** 对话框中可用，而不是 **属性** 面板。
{{% /报警 %}}

您可以覆盖您打开的页面的标题，例如指明从哪里打开它。

通过检查 **重写页面标题** 复选框来激活这个功能。

### 2.8 标签部分{#label}

{{% snippet file="refguide8/label-section-link.md" %}}

### 2.9 可选对象部分{#selectable-objects}

可选对象部分中的属性决定了最终用户可以从中选择的对象。

**源** 属性设置使用了三种方法来定义可选对象：

* 数据库 *(默认)*
* XPath
* 微流

#### 2.9.1 数据库

数据库是可选对象的默认源。 默认情况下，正确实体类型的所有数据库对象都可以选择。

**制约因素**

您可以通过添加约束来限制提交给最终用户的对象。 在 **编辑约束** 对话框中，您将被引导：

![编辑约束对话框](attachments/reference-selector/database-constraints.png)

See the [constraints](database-source#constraints) section of *Database Source* for more information.

**排序顺序**

排序顺序指定了参考选择器中项目的显示顺序。 您可以在两个方向排序多个属性 (升序和降序)。 如果指定 **(默认)** 排序顺序，则显示属性上的参考选择器排序。

#### 2.9.2 XPath{#xpath-constraints}

如果来源是XPath, 对象列表也将从数据库中取出。 但显示的对象由 XPath 约束选择。

**XPath 约束**

XPath 约束限制了可以选择的对象列表。

例如， 产品参考选择器的 XPath 约束 `[Instock = true()]` 将确保只有库存中的产品是可以选择的。

更多关于 XPath 约束的信息，请参阅 [XPath 约束](xpath-constraints)。

**约束者**

参考选择器可以受到一个或多个路径的限制。 这通常用于使一个参考选择器依赖另一个参考选择器。 解释这一点的最佳途径是树立一个榜样。

想象您有一个订购系统，在该系统中，产品按类别进行排序——例如，食品和饮料产品。 在您可以编辑订单行的页面上，产品选择器可以受到类别选择器的限制。 在选择类别 (*food*, 例如), 产品选择器受此类别的限制，只显示该类别中的产品。

_示例域模式_ ![](attachments/reference-selector/orderline-domain-model.png)

在域模型中，订单行在类别和产品上都有多个对应的关联。 这些社团可以使用参考选择器进行编辑。 第三个协会，从产品到产品类别，描述了这两个实体之间的关系——即每个产品都有一个相关类别。

{{% alert type="info" %}}
域模型的这种三角形部分是可能使用 **受到** 限制的原因。
{{% /报警 %}}

在表单上，您有两个参考选择器：一个用于 **类** 类，一个用于 **产品** 类。

![](attachments/reference-selector/orderline-reference-selectors.png)

没有限制，参考集选择器将提供所有产品：

![所有产品、食品和饮料列表](attachments/reference-selector/orderline-no-constraint.png)

然而，由于域模型的结构问题。 您可以添加一个约束，它意味着只选择先前选择的类别的产品。 这是由 **约束的** 个属性设置的。

![](attachments/reference-selector/orderline-constrained-by.png)

现在最终用户将只看到所选类别中的产品：

![饮料类别中的纯商品列表](attachments/reference-selector/orderline-with-constraint.png)

**排序顺序**

排序顺序指定了参考选择器中项目的显示顺序。 您可以在两个方向排序多个属性 (升序和降序)。 如果指定 **(默认)** 排序顺序，则显示属性上的参考选择器排序。

#### 2.9.3 微流

{{% alert type="warning" %}}
只有在选择使用下拉菜单时才能使用微流。
{{% /报警 %}}

如果选择源微流，则调用微流，并返回参考选择器将显示的对象列表。

**微流**

微流程指定返回对象列表的运行微流程。

**微流程设置**

在微流程设置中，您可以指定传递给微流程的参数，具体取决于微流程本身中指定的参数。

### 2.10 验证部分{#validation}

{{% snippet file="refguide8/widget-validation-link.md" %}}

### 2.11 可见性部分{#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 阅读更多

*   [数据视图](data-view)
*   [实体](实体)
*   [社会联系](关联)
