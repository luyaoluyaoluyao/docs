---
title: "关联 & 他们的属性"
parent: "域名模型"
tags:
  - "域模型"
  - "关联"
---

## 1 导言

一个协会描述了实体之间的关系。 在域模型中，一个协会由两个实体之间的一条线或箭头来表示。

The value of the association can only be viewed or edited from the object of the entity that is the _[owner](associations#owner)_ of the association. 一个实体或两个实体都可以成为该协会的所有者。 如果一个实体是业主，则有一个从业主到另一个实体的箭头。 如果这两个实体都是业主，两个实体之间就有一条线。

一个社团的 [多重性](#multiplicity) (或所指对象的数量) 在社团的任何一侧都以编号1 (`1`)或星号(`*`表示出来。

在下面的示例中，箭头表示 **订单** 是该协会的所有者。 和 `1` 和 `*` 表示一个客户与许多订单相关联：

![](attachments/domain-model-editor/918217.png)

{{% alert type="info" %}}

可持久实体和不可持久实体之间的关联必须从不可持续实体中启动并拥有所有者 **默认值**。 关于可持久性和不可持久性实体的更多信息，见 [可持久性](persistability)。

{{% /报警 %}}

## 2 个关联属性

如果你双击一个关联，它的属性将被打开。

![关联属性](attachments/association-properties/dm-association-properties.png)


协会有下列财产：

* [名称](#name)
* [文件](#documentation)
* [多重性](#multiplicity)
* [导航能力](#navigability)
* [删除行为](#delete-behavior)

### 2.1 名称 {#name}

协会的名称用来指它的表格、微流等形式。

### 2.2 文件 {#documentation}

您可以在此字段中写入此元素的注释和文档。

### 2.3 多重性 {#multiplicity}

多重性定义了可能推荐对象的数量。 它在关联的任何一侧由数字 (`1`)或星星(`*`表示.

多重性可以是以下类型：

* 一对一——一个X对象与一个Y对象关联
* 一对多——一个X对象与多个Y对象关联
* 多对多——多个X对象与多个Y对象关联

多重性显示社团的所有者和方向，如果社团是一对多或多对多类型。 如果该协会是一对一的，两个实体都是业主。 欲了解更多关于所有权的信息，请参阅 [4 所有者](associations#owner) in *Associations*。

### 2.4 Navigability {#navigability}

导航功能会改变多个关联的所有者。 导航功能有以下选项：

* X 对象指的 Y 对象 - 该协会的所有者是 X
* X 和 Y 对象相互引用 - 两个实体都是所有者

### 2.5 删除行为 {#delete-behavior}

删除行为定义删除对象时相关对象应发生的情况。 以下选项可以为每一结尾的关联配置。

| 值                                                       | 描述                       |
| ------------------------------------------------------- | ------------------------ |
| 删除 {name of entity} 对象，但保留 {name of other entity} 对象(s) | 当一个对象被删除时，关联对象不会被删除。     |
| 删除 {entity> 对象和 {name of other entity} 对象的名称            | 当一个对象被删除时，关联对象也会被删除。     |
| 删除 {实体> 对象名称仅在它没有与 {name of other entity} 对象相关联时才能删除    | 一个对象只能在与任何其他对象无关的情况下被删除。 |

* *默认值*: 删除 {name of entity} 对象，但保留 {name of other entity} 对象(s)

This delete behavior is used if you want to delete any associated **Profile** when a **Customer** is deleted:

![](attachments/domain-model-editor/918143.png)

如果您想要能够删除 **客户** 只在它与任意 **订单没有关联的情况下才使用此删除行为**：

![](attachments/domain-model-editor/918146.png)

## 3 阅读更多

* [社会联系](关联)