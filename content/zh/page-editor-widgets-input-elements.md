---
title: "输入元素"
parent: "页面编辑器部件"
description: "在 Mendix Studio 中描述输入小部件。"
menu_order: 20
tags:
  - "工作室"
  - "页面编辑器"
  - "输入元素"
  - "输入小部件"
  - "小部件"
---

## 1 导言

**输入元素** 是 [Mendix Studio中通常用于允许最终用户输入或编辑数据的小部件](page-editor-widgets)。 例如，下面的文本框允许用户填写他们的全名：

{{% image_container width="350" %}}![](attachments/page-editor-widgets-input-elements/text-box-example.png)
{{% /image_container %}}

**输入元素** 只能在数据容器内起作用 (数据视图，列表视图，或数据网格)。 You can either place widget in an existing data container; or click **Wrap with a new data view** in **Properties** to create a data view and place an input element inside it automatically.

![](attachments/page-editor-widgets-input-elements/wrap-in-data-view.png)

## 2 输入元素概述

您可以在下表中找到在Studio中可用的输入元素描述：

| 输入元素  | 描述                                                                                                                                                                                                                       |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 文本框   | 文本框用于允许最终用户进入、编辑和显示文本。 例如，最终用户将能够输入自己的名字。                                                                                                                                                                                |
| 文本区域  | 一个文本区域用于输入、编辑和显示一个长文本，可以使用几行，例如产品的描述。                                                                                                                                                                                    |
| 日期选择器 | 一个日期选择器用于允许最终用户在日历中选择一个日期，例如在选择一个日期交付时。                                                                                                                                                                                  |
| 下拉列表  | 下拉小部件用于允许最终用户从预设选项列表中选择一个选项。 例如，用户可以选择产品的颜色。<br />您也可以使用这个小部件来显示和选择关联。 您需要一个域模型中的多对一的关联(详情请参阅 [Associations](domain-models-association-properties))。 例如，如果客户有几个地址，用户可以从它们中选择一个送货地址。 在这个例子中，几个地址可以与一个客户相关联(多对一个社团)。 |
| 复选框   | 一个复选框小部件用于允许用户将一个值标记为真或假值。 例如，用户可以在一个方框中打勾以注册时事通讯。                                                                                                                                                                       |
| 单选按钮  | 单选按钮允许用户从预设选项中选择。 例如，用户可以从几个可能的地点选择订单上下。                                                                                                                                                                                 |

{{% alert type="info" %}}

除了标准输入小部件外，您还可以 [从Mendix Marketplace](https://marketplace.mendix.com/) 下载小部件到您的应用。 For more information, see the [Widgets by Origin](page-editor-widgets#widgets-by-origin) section in *Widgets*.

{{% /报警 %}}

## 3 属性

所有输入元素属性由以下部分组成：

* [类型](#type)
* [数据源](#input-elements-data-source)
* [A. 概况](#input-elements-general)
* [输入验证](#validation)
* [条件可见性](#visibility)
* [设计](#input-elements-design)

日期选择器有一个指定的 [格式](#format) 部分。

### 3.1 类型选择 {#type}

{{% alert type="info" %}}
此选项仅适用于 **文本框**, **文本区域**, **单选按钮**, **勾选框**, 和 **下拉-下移** 部件。
{{% /报警 %}}

**输入** 选项允许您快速将一个输入元素的类型更改为一个相似的元素：您可以将 **文本框** 更改为 **文本区域** 更改为** 文本区域** 然后更改 **单选框** 到 **复选框** 或 **Drop-own** 和 反之亦然：

![类型选项](attachments/page-editor-widgets-input-elements/input-widget-type.jpg)

### 3.2 数据源部分 {#input-elements-data-source}

**输入元素** 需要链接到一个属性以显示数据并允许最终用户编辑它。 不同的输入元素需要 [不同类型的属性](domain-models-attributes)。 您可以在下表中找到输入元素和属性类型之间的对应：

| 输入元素  | 允许的属性类型                                                                |
| ----- | ---------------------------------------------------------------------- |
| 文本框   | 字符串，自动飞行，十进制，Hashed String，Integer，Long                                |
| 文本区域  | 字符串                                                                    |
| 日期选择器 | 日期和时间                                                                  |
| 下拉列表  | 计算、关联                                                                  |
| 参考选择器 | Autonumber, Date and Time, Decimal, Enumeration, Integer, Long, String |
| 复选框   | Boolean                                                                |
| 单选按钮  | Boolean, Enumeration                                                   |

### 3.3 一般部分 {#input-elements-general}

**常规** 部分具有每个输入元素的共同属性，但也可能包含特定的属性。

#### 3.3.1 显示标签 {#show-label}

如果您想要向最终用户显示部件的标签(名称)，请启用此属性。 *此属性默认启用。*

#### 3.3.2 标签

只有在 **启用标签** 时才显示此属性。 指定将显示给最终用户的名称。 当您选择一个属性时，属性的名称以括号显示在标签中。 这意味着该属性的值将显示给最终用户，而不是静态文本。

#### 3.3.3 编辑性 {#editability}

可编辑性表示最终用户是否能够更改部件显示的值。 可能的值如下：

* **可编辑** — — 小部件显示的值是可编辑的。

* **只读** -- 值处于只读模式。

* **条件** - 只有在基于属性值或基于表达式满足了指定条件的情况下才能编辑部件。

    {{%alert type="info" %}} If an attribute set for the widget's data source is of the AutoNumber type, the widget is set into read-only mode by default and the **Editability** setting itself is disabled, because attributes of this type are generated automatically.{{%/alert %}}


##### 3.3.3.1 条件基于： {#condition}

基于</strong> 属性的 **条件仅在 [条件编辑性](#editability) 被选中时才显示。 以下选项可用：</p>

* **属性** - 定义条件是否基于属性值。 在这种情况下，小部件只有在符合所选属性的某个值时才可编辑。 属性必须是布尔值或枚举类型。
* **表达式** -- 定义条件是否基于表达式。 在这种情况下，只有当表达式返回布尔值 `true` 时，小部件才能被编辑。 关于表达式的更多信息，见 [表达式](expressions)。

##### 3.3.3.2 属性 {#attribute}

This property is shown only when the expression the [Condition Based on](#condition) is set to **Attribute**. 允许您选择条件将基于的属性。 属性必须是布尔值或枚举类型。

##### 3.3.3.3 属性值 {#attribute-values}

此属性仅在属性为 [属性](#condition) 属性被选中时才显示。 **属性值** 允许您选择特定属性值。

例如， 只有当用户填写 **国家** 字段时，才可编辑 **City** 字段。 因为您可以向数量有限的国家发送您的产品。 因此，您需要在 **属性中选择 *国家/地区*** 属性和 *荷兰* *Belgium*, *Germany*, *France* in **属性值** property.

##### 3.3.3.4 表达式

此属性允许您创建表达式，并且只在表达式 [基于](#condition) 的条件设置为 **表达式** 时才显示。 表达式应该是布尔型。 关于如何创建表达式的更多信息，见 [表达式](expressions)。

#### 3.3.4 特定属性

以下表格说明了输入要素的具体特性：

| 输入元素 | 财产   | 描述                                                                                                         |
| ---- | ---- | ---------------------------------------------------------------------------------------------------------- |
| 文本区域 | 自动缩放 | 如果启用，文本区域会自动增长，这取决于文本是否填写。 <br />*此属性默认被禁用。*                                                         |
| 文本区域 | 行数   | 此属性仅在 **自动增长** 选项被禁用时才显示。  行数决定文本区域同时显示多少行。 如果文本区域的文本包含更多的行，您将需要使用滚动条来查看所有。 <br />默认值为 **行数量** 选项： 5 |
| 单选按钮 | 方向   | 此属性定义是否在您的应用中水平或垂直显示无线电按钮。 <br />默认值为 **方向**: 水平.                                                    |

### 3.4 格式部分 {#format}

**格式** 部分只适用于 **日期选择器** 的部件。

 **格式** 部分属性在下表中描述：

| 财产   | 描述                                                                              |
| ---- | ------------------------------------------------------------------------------- |
| 类型   | 确定向用户显示日期和/或时间的方式。 此属性的可能值如下： <ul><li>**日期** - 用户只能查看或编辑日期</li>**时间** - 用户只能查看或编辑时间<li></li><li>**日期和时间** - 用户可以查看或编辑日期和时间</li><li>**Custom** - 自定义日期和时间格式只能在Studio Pro 中配置</li></ul><br />**类型**的默认值：日期 |
| 格式示例 | 显示所选格式类型的示例。                                                                    |

### 3.5 输入验证部分 {#validation}

在 **输入验证**, 你可以指定部件的值是否应该被验证。 您可以为输入小部件设置验证类型，并在验证失败时指定最终用户信息。 例如， 您可以标记新客户所需的 **全名** 字段，而且您可以添加一条消息，说：“请指定您的姓名以继续”。

{{% image_container width="350" %}}
![](attachments/page-editor-widgets-input-elements/Validation-type-required.png)
{{% /image_container %}}


**输入验证** 部分属性在下表中描述：

| 财产                          | 描述                                                                                                                              |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| 验证类型                        | 此属性表示是否应该验证小部件中填写的值。 可能的备选办法如下：<br /><ul><li>**无** - 不需要一个值，小部件可以留空</li><li>**必填** - 小部件不能为空，最终用户需要填写一个值</li><li>**Custom** - 只能在 Studio Pro中设置。 然而，如果工作室专业版设置了自定义验证，您可以为自定义验证指定或更改 [message](#validation-message)</li></ul>                                                            |
| <a name="validation-message"></a>留言 | A message that is shown to end-users when **Validation Type** is **Required** or **Custom** and when the validation has failed. |

### 3.6 条件可见性部分 {#visibility}

{{% snippet file="studo/visibility-section-link.md" %}}

### 3.7 设计科 {#input-elements-design}

关于 **设计** 部分及其属性的信息，请参阅 [设计部分](page-editor-widgets-design-section)。

## 4 阅读更多

* [页 次](page-editor)
* [小部件](页面编辑器部件)
