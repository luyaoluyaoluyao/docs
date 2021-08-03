---
title: "域模型"
description: "描述Mendix Studio中的域模型。"
menu_order: 20
tags:
  - "工作室"
  - "域模型"
---

## 1 导言

域模型是一个数据模型，以抽象的方式描述您应用程序域中的信息。 它是您应用程序架构的核心。

工作室的域模型包括以下内容：

* [实体](#entity)
* [社会联系](domain-models-association-properties)

{{% alert type="info" %}}

让我们说你有一个CD集，就像下表中的集合。

| 标题       | 艺人                       |
| -------- | ------------------------ |
| 如何拆除原子弹位 | U2                       |
| Exodus   | Bob Marley & The Wailers |

表格中的行是CD。 两行的类型是“CD”，这是实体名称。 一个 U2 频带的 "如何拆除原子弹" 特定的 CD 称为"CD" 实体的对象。 像“标题”和“艺术家”这样的特性被称为属性。

{{% /报警 %}}

要在 Studio 中查看您的应用程序的 **域模式** 点击 **域模型** 工作室左侧菜单栏中的图标。

{{% image_container width="350" %}}![](attachments/domain-models/domain-model.png)
{{% /image_container %}}

打开域模型后，您将看到实体的所有实体、属性和协会的概览。

![](attachments/domain-models/domain-overview.png)

{{% alert type="info" %}}

您的域模型的复杂性取决于您的应用的复杂性。

{{% /报警 %}}

**自动在域模型组上方排列** 选项，并通过关联对实体进行配对。 没有关联的实体将被垂直对齐。

## 2 个组件

| 域名模型组件                                     | 描述                                                                          | 属性                                                                                                                                             |
| ------------------------------------------ |:--------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| 实体<a name="entity"></a>                | 一个实体代表一类现实对象，如客户、发票、工程项目等。 <br />如果我们绘制一个与数据库平行的图表，实体就是一个表。           | 名称<br />[持久性](/refguide/persistability)                                                                                                  |
| [属性](domain-models-attributes)             | 属性是描述和/或确定实体的特征。 例如， *客户* 实体通常具有客户名称、电子邮件地址和其他个人信息的属性。 如果我们与数据库平行绘制，属性就是一列。 | 名称<br />类型                                                                                                                               |
| [协会](domain-models-association-properties) | 一个协会描述了实体之间的关系。 在域模型中，一个协会由两个实体之间的线/箭头代表。 如果我们绘制与数据库平行的数据库，该协会是一个外国钥匙。      | 名称<br />[多重性](domain-models-association-properties#multiplicity)<br />[删除行为](domain-models-association-properties#delete-behavior) |

欲了解示例和更多技术详情，请参阅 [域模式](/refguide/domain-model), [实体](/refguide/entities), [属性](/refguide/attributes)和 [关联 *Studio Pro 指南* 中](/refguide/associations)

## 3 添加新实体 {#adding-new-entities}

您可以在 **工具箱** 中添加新实体。

{{% image_container width="250" %}}![](attachments/domain-models/toolbox-entity.png)
{{% /image_container %}}

若要添加实体，请执行以下操作：

1. 打开域模型的 **工具箱** 标签。

2. 拖拽 **新实体** 到工作区。

3.  填写名称并点击 **创建**:

    ![](attachments/domain-models/create-new-entity-dialog.png)

新实体已添加到域模型。

{{% image_container width="250" %}}![](attachments/domain-models/new-entity.png)
{{% /image_container %}}

## 4 添加新属性 {#adding-new-attributes}

要在域模式中添加属性，请执行以下操作：

1.  选择一个包含您想要添加属性的实体的块。 **新属性** 选项出现：

    {{% image_container width="250" %}}![](attachments/domain-models/adding-attribute.png)
    {{% /image_container %}}

2.  点击 **新属性** 并指定 **名称** 和 **类型**：

    ![](attachments/domain-models/create-new-attribute-dialog.png)

3. 点击 **创建**。

新属性已添加到实体。

{{% image_container width="250" %}}![](attachments/domain-models/new-attribute.png)
{{% /image_container %}}

## 5 添加新关联

若要在域模型中添加关联，请执行以下操作：

1. 选择一个与您想要添加关联的实体的块。
2.  点击显示的箭头图标：

    {{% image_container width="250" %}}![](attachments/domain-models/adding-association.png)
    {{% /image_container %}}

3.  从现有实体列表中为新的关联选择第二个实体，然后点击 **选择**。 您也可以从对话框中为关联创建一个新的实体。

    ![](attachments/domain-models/new-association.png)

{{% alert type="info" %}}

该模块在括号内实体名称旁边标明。 如果您从另一个模块中选择实体，您将创建一个交叉模块关联。 欲了解更多信息，请参阅 [5个交叉模块关联](domain-models-association-properties#cross-module-associations) *关联属性*。 当前模块的实体列在首位。

{{% /报警 %}}

## 6 个指定属性

在域模型中，您可以在 **属性** 标签上管理实体、属性和关联的属性。

在标签的底部，您可以看到 **删除** 个按钮。

### 6.1 实体属性

您可以管理一个实体的以下属性：

* 实体的 **名称**

* [实体的持久性](/refguide/persistability)

    ![](attachments/domain-models/entity-properties.png)

要更改实体属性，请单击域模型中的实体。 选定实体的 **属性** 标签被自动显示。

### 6.2 指定属性属性

您可以管理属性的以下属性：

*   属性的 **名称**
*   属性的 [**类型**](domain-models-attributes)

    ![](attachments/domain-models/attribute-properties.png)

要更改属性属性，请单击域模型中的属性。 所选属性的 **属性** 标签被自动显示。

![](attachments/domain-models/selecting-attribute.png)


{{% alert type="info" %}}

在 **属性中显示的字段** 可能会根据属性的类型而变化。

{{% /报警 %}}

### 6.3 指定协会财产

您可以管理一个关联的以下属性：

*   关联的 **名称**
*   **关联的多重性**
*   删除对象的行为

欲了解更多信息，请参阅 [关联属性](domain-models-association-properties)。

要更改关联，请点击域模型中的行号。 选定实体的 **属性** 标签被自动显示。

如果关联类型是一对数或多对数的，您可以交换它的方向，点击相应的图标。 欲了解更多信息，请参见 [3 Mulplicity](domain-models-association-properties#multiplicity) in *Association Properties*。

{{% image_container width="350" %}}![](attachments/domain-models/managing-associations.png)
{{% /image_container %}}

## 7 删除实体、属性或关联

若要删除实体、属性或协会，请做以下操作：

1. 选择您想要删除的实体、属性或关联。

2.  按 **删除** 或点击 **删除** 在 **属性底部的按钮** 选项卡。

    {{% image_container width="300" %}}![](attachments/domain-models/deletion.png)
    {{% /image_container %}}

## 8 阅读更多

* [属性类型](domain-models-attributes)
* [关联属性](domain-models-association-properties) 
