---
title: "关联标签属性"
parent: "关联"
menu_order: 15
tags:
  - "域模型"
  - "关联"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/association-member-properties.pdf)。
{{% /报警 %}}

## 1 导言

有两种方法来编辑 [关联](associations) 的属性。 此文档描述了您可以从实体属性中的 **关联** 标签中编辑的属性。 如果您想要编辑 [关联属性](association-properties)中描述的关联， 您可以点击 **编辑** 打开关联属性对话框。

欲了解更多关联信息，请参阅 [关联](associations)。

## 2 属性

实体属性的 **关联** 标签的示例在下面的图像中表示：

![](attachments/associations/edit-entity-association.png)

协会标签中的社团具有以下属性：

* [名称](#name)
* [类型](#type)
* [所有者](#owner)
* [父母/儿童](#parent-child)

您可以通过单击列标题来排序这些属性的关联列表 (升序或降序)。

### 2.1 名称 {#name}

社团名称被用来引用。 例如，在形式或微流方面。

{{% alert type="info" %}}
您不能在关联选项卡中更改此名称。 要更改名称，请点击 **编辑** (或双击协会名称) 打开 [关联属性](association-properties)。
{{% /报警 %}}

### 2.2 类型 {#type}

此属性定义了一个社团是参考(单一)还是参考集(复数)。

| 值          | 描述                        |
| ---------- | ------------------------- |
| 参考 *(默认值)* | 单一：拥有实体的物体是指另一实体的零或一个物体。  |
| 参考集        | 多元化：拥有实体的物体系指另一实体的零或更多物体。 |

{{% alert type="info" %}}
这种财产的例子与下面的所有者财产的例子结合在一起。
{{% /报警 %}}

### 2.3 所有者 {#owner}

这种财产确定一个协会是拥有一个还是两个业主。 如果有一个拥有者，则所有者位于箭头的开头。

| 值         | 描述               |
| --------- | ---------------- |
| 默认 *(默认)* | 只有一个实体是所有者(母公司)。 |
| 两者都是      | 这两个实体都是业主。       |

所有权很重要，因为它界定了一个协会的两个方面：

* 信用度 (许多或一个) 是如何控制的
* 社团记录的地方

{{% alert type="info" %}}
外部实体不能是外部实体与当地实体之间的联系的所有者。
{{% /报警 %}}

#### 2.3.1 卡片性

Cardinity指的是计算对象可以拥有的社团数目。 为了确保对象能够计算某个社团的发生，它需要拥有该社团的所有权。

因此，对于一个一对一的关联， *许多* 结束时拥有该关联，以确保它只能与 *一个* 对象关联。 对于一对一的社团，两者都结束该社团。 对于多对多的关系而言，信用证并不重要。

#### 2.3.2 协会记录

一个社团被记录到拥有它的对象中。 如果两个对象都拥有该协会，则将这两个对象都记录下来。 您可以看到关联记录在 [关联示例](associations#examples) *关联部分* 中的示例。

关联被记录的地方，对您的应用程序中的参考和参考设置选择器的用户有重要影响。 选择器只能在包含 _所有_ 对象的数据视图中。 这是因为只有当您提交了拥有对象时，才会记录该关联的记录。

例如，想象您有一个多对多的协会， **Customer_Group**, 在 **Customer** 和 **组** 之间, 由客户实体拥有。 您可以放置一个输入参考集选择器，从客户数据视图中选择组。 However you _cannot_ put an input reference set selector to select Customers from within a Group data view.

![在客户数据视图中通过输入参考集选择器选择组对象](attachments/associations/input-reference-set-selector.png)

如果两者都结束了关联，您可以克服这个限制。 然而，这种情况必须兼顾与必须使所有登记协会的实体作出承诺有关的间接费用。 因此，建议由 **默认** 实体拥有多对多的关系。 除非有很强的商业理由需要在您的 Mendix 应用程序的任何结尾添加关联。

{{% alert type="info" %}}
只在其中一个实体上录制关联并不影响您从两端导航关联的能力。 然而，从无产权的端口航行可能较慢。
{{% /报警 %}}

### 2.4 类型 & 所有者与多重关系 & 导航能力 {#types}

**输入** and **所有者** 实体的属性与 [多重性](association-properties#multiplicity) 和 [导航性](association-properties#navigability) 关联的属性。 当您更改 **键入** 或 **所有者**时，您更改了 **多重性** 和 **导航性**。

您可以在下面的表格中找到 **类型**/**所有者** 和 **多重性**/**导航能力** 之间的对应。

| **多重性** | **导航能力**     | 类型  | 所有者  |
| ------- | ------------ | --- | ---- |
| 一对一的    | —            | 参考  | 两者都是 |
| 一对多的    | —            | 参考  | 默认设置 |
| 多对多     | X 对象指向Y 对象   | 参考集 | 默认设置 |
| 多对多     | X 和 Y 对象相互引用 | 参考集 | 两者都是 |

欲了解更多关于多重性和导航性的信息，请参阅 [Multicipity](association-properties#multiplicity) and [Navigability](association-properties#navigability) section in *Association Properties*。

## 3 名父母/子女 {#parent-child}

父和子项设置显示关联的方向。 家长定义了社团开始的实体，儿童定义了社团结束的实体。

## 4 阅读更多

* [关联属性](association-properties)
* [实体](实体)
