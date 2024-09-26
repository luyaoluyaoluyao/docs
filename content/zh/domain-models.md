---
title: "域模型"
description: "描述Mendix Studio中的域模型。"
category: "使用数据"
menu_order: 10
tags:
  - "工作室"
  - "域模型"
---

## 1 导言

Mendix 应用程序由 *模块* 组成。 一个模块是一个将您的应用程序的功能分成不同部分的单位。 默认情况下，您在Studio中有一个叫做MyFirstModule的模块。

每个模块都有自己的 *域模型*。 域模型是一个数据模型，以抽象的方式描述您应用程序域中的信息。 它是您应用程序架构的核心。

工作室的域模型包括以下内容：

* [实体](#entity-types)
* [社会联系](domain-models-association-properties)

让我们说你有一个CD集，就像下表中的集合：

| 标题       | 艺人                       |
| -------- | ------------------------ |
| 如何拆除原子弹位 | U2                       |
| Exodus   | Bob Marley & The Wailers |

表格中的行是CD。 因此， *CD* 是一个 *实体*。 A specific CD like "How to Dismantle an Atomic Bomb" of the band U2 is an *object* of the *CD* entity. 这意味着 *对象* 是一个实体的单个实例。 像“标题”和“艺术家”这样的特性是 *属性*。

要在 Studio 中查看您的应用程序的 **域模式** 点击 **域模型** 工作室左侧菜单栏中的图标。

{{% image_container width="350" %}}![](attachments/domain-models/domain-model.png)
{{% /image_container %}}

打开域模型后，您将看到所有实体、属性和关联的概述。 您的域模型的复杂性取决于您的应用的复杂性。

![](attachments/domain-models/domain-overview.png)

左上角组中的 **自动排列** 选项，并通过关联对实体进行配对。 没有关联的实体将被垂直对齐。

## 2 个组件

域模型可以包含以下组件：

* [实体](#entity-types) - 代表一类现实世界对象；实体可以有属性
    * [属性](#attributes) - 描述和/或识别实体
* [关联](#associations) — 描述实体之间的关系

### 2.1 实体及其类型 {#entity-types}

一个实体代表一类现实对象，如客户、发票、工程项目等。 如果我们绘制与数据库平行的图表，实体就是一个表。

您可以将不同类型的实体添加到您的域模型：

* **实体** - 一个能够具有属性、关联和代表一类现实对象的实体。
* **图像实体** — — 一种特殊类型的实体允许您存储图像。 例如，在页面上，用户将能够在图像实体的帮助下查看和上传图像。
* **文件实体** — — 一种特殊类型的实体允许您存储一个文件。 例如，在页面上，用户将能够上传和下载文件 (如： 在文件实体的帮助下，文本文档、pdf、电子表格）。
* **外部实体** - 只有当您的组织启用了数据枢纽功能时才可用。 欲了解更多关于外部实体的信息，请访问 [Studio 数据枢纽](data-hub-in-studio)。

### 2.2 实体财产

实体拥有下列属性：

* **常规** 属性定义了实体名称及其 [持久性](/refguide8/persistability):

    * **名称** — 定义实体名称

    * **可持久** - 定义实体的对象是否存储在数据库中 (关于可持久性的更多信息) 见 [持久性](/refguide8/persistability) 在 *Studio Pro 指南* 中

    ![实体的一般属性](attachments/domain-models/entity-general-properties.png)

* **存储的信息** 属性定义该实体的信息是否存储在数据库中。 如果信息被存储，它可以在稍后检索，并可以在 [页面筛选器](data-filters) 中使用。 例如，您可以添加一个过滤器，只显示当前用户创建的对象。

    您可以切换以下属性：

    * **存储“创建者”** - 启用后，创建实体的用户将存储在数据库中

    * **存储'创建日期'** - 启用时，实体创建的日期和时间被存储在数据库中

    * **存储“最后更改由”**- 启用时, 最后修改实体的用户存储在数据库中

    * **存储'最后更改日期'** - 启用后，实体最后更改的日期和时间将存储在数据库中

        ![保存的实体信息属性](attachments/domain-models/entity-stored-info.png)

        {{% alert type="info" %}}You cannot toggle **Stored Information** properties for Image and File entities.{{% /alert %}}

### 2.3 属性 {#attributes}

属性是描述和/或确定实体的特征。 例如， *客户* 实体通常具有客户名称、电子邮件地址和其他个人信息的属性。 如果我们与数据库平行绘制，属性就是一列。

欲了解更多关于属性类型及其属性的信息，请参阅 [属性](domain-models-attributes)。

### 2.4 社会联系 {#associations}

一个协会描述了实体之间的关系。 在域模式中，一个协会由两个实体之间的一条线表示。 如果我们绘制与数据库平行的数据库，该协会是一个外国钥匙。

欲了解更多关于关联类型及其属性的信息，请参阅 [关联](domain-models-association-properties)。

## 3 添加新实体 {#adding-new-entities}

您可以在 **工具箱** 中添加新实体。

{{% image_container width="300" %}}![](attachments/domain-models/toolbox-entity.png)
{{% /image_container %}}

若要添加实体，请执行以下操作：

1. 打开域模型的 **工具箱** 标签。

2. 选择您想要添加的实体类型，然后拖放工作区域。

3.  填写实体名称并点击 **创建**:

    ![](attachments/domain-models/create-new-entity-dialog.png)

新实体已添加到域模型。

{{% image_container width="250" %}}![](attachments/domain-models/new-entity.png)
{{% /image_container %}}

### 3.1 添加新图像或文件实体 {#adding-image-or-file-entities}

While adding new entities from the **Toolbox** works for all types of entities, you can use a specific way of adding image and file entities to your domain model.

例如， 您有一个名为 *Lapcock* 的实体，您想要能够根据笔记本模型向用户显示特定的图像。 在这种情况下，您需要创建一个图像实体(例如，名字为 *Product_Image*)。 然而，要获取数据并动态地显示每台膝上型计算机模型的正确图像。 *Product_Image* entity 也应该与 *Laptop* 实体有一个特定的连接(关联)。 关于关联及其类型的更多信息，见 [Associations](domain-models-association-properties)。

若要自动创建一个带有关联的新图像/文件实体，请按照下面描述的流程：

1. 选择 *实体* 类型将与新图像或文件实体连接的实体。

2. 点击 **新属性** 按钮。

3.  在 **创建新属性** 对话框中，点击 **在右下角添加图像或文件**

    ![添加图像或文件](attachments/domain-models/add-image-or-file.png)

4. 在 **图像和文件** 对话框中，选择类型或实体 (图像或文件)。

5. 在 **创建新图像/文件实体** 对话框中，指定特殊实体的名称并点击 **创建**。

新的图像或文件实体是默认的 *名称* 和 *大小* 属性和您在第一步选择的实体的关联： ![图像实体示例](attachments/domain-models/image-entity-example.png)

## 4 添加新属性 {#adding-new-attributes}

要在域模式中添加属性，请执行以下操作：

1.  选择一个包含您想要添加属性的实体的块。 **新属性** 选项出现：

    {{% image_container width="250" %}}![](attachments/domain-models/adding-attribute.png)
    {{% /image_container %}}

2.  点击 **新属性** 并指定 **名称** 和 **类型**：

    ![](attachments/domain-models/create-new-attribute-dialog.png)

3. 点击 **创建**。

一个新属性被添加到实体。

{{% image_container width="250" %}}![](attachments/domain-models/new-attribute.png)
{{% /image_container %}}

## 5 添加新关联

在域模式中添加关联有几种方式。 您可以做以下事情之一：

1. 点击出现的点图标，然后做以下一件事：

    ![](attachments/domain-models/adding-association-dot-icon.png)

    1. 要创建一个与现有实体的关联，请将点拖到第二个实体。

    2.  创建一个新实体的关联， 拖动点图标并将其保持几秒钟，直到它变成一个加号图标。 通过丢弃加号图标，您可以从第一个实体创建一个新的实体：

        ![](attachments/domain-models/plus-icon.png)

4. 选择一个与您想要添加一个社团的实体一起执行以下任务的块：

    1.  点击箭头图标：

        {{% image_container width="250" %}}![](attachments/domain-models/adding-association.png)
        {{% /image_container %}}

    2.  从现有实体列表中为新的关联选择第二个实体，然后点击 **选择**。 您也可以从对话框中为关联创建一个新的实体。

        ![](attachments/domain-models/new-association.png)

        模块名称在括号内实体名称旁边标明。

        {{% alert type="info" %}} If you select the entity from another module, you will create a cross-module association. 欲了解更多信息，请参阅 [跨模块关联](domain-models-association-properties#cross-module-associations) 部分 *关联*。 当前模块的实体列在首位。
        {{% /报警 %}}

## 6 个指定属性

在域模型中，您可以在 **属性** 标签上管理实体、属性和关联的属性。

在标签的底部，您可以看到 **删除** 个按钮。

### 6.1 实体属性

您可以管理一个实体的以下属性：

* 实体的 **名称**

* [实体的持久性](/refguide8/persistability)

    ![](attachments/domain-models/entity-properties.png)

要更改实体属性，请单击域模型中的实体。 选定实体的 **属性** 标签被自动显示。

### 6.2 指定属性属性

您可以管理属性的以下属性：

* 属性的 **名称**
* 属性的 [类型](domain-models-attributes)

    ![](attachments/domain-models/attribute-properties.png)

要更改属性属性，请单击域模型中的属性。 所选属性的 **属性** 标签被自动显示。

![](attachments/domain-models/selecting-attribute.png)


{{% alert type="info" %}}

在 **属性中显示的字段** 可能会根据属性的类型而变化。

{{% /报警 %}}

{{% alert type="info" %}}

*name* and *大小* 属性的图像和文件实体属性是只读的，您不能编辑它们。

{{% /报警 %}}

### 6.3 指定协会财产

您可以管理一个关联的以下属性：

*   关联的 **名称**
*   **关联的多重性**
*   删除对象的行为

欲了解更多信息，请参阅 [关联](domain-models-association-properties)。

要更改关联，请点击域模型中的行号。 选定实体的 **属性** 标签被自动显示。

如果关联类型是一对数或多对数的，您可以交换它的方向，点击相应的图标。 欲了解更多信息，请参见 [3 Mulplicity](domain-models-association-properties#multiplicity) in *Associations*。

{{% image_container width="350" %}}![](attachments/domain-models/managing-associations.png)
{{% /image_container %}}

## 7 删除实体、属性或协会

若要删除一个实体、属性或协会，请采取以下行动：

1. 选择您想要删除的实体、属性或关联。

2.  按 **删除** 或点击 **删除** 在 **属性底部的按钮** 选项卡。

    {{% image_container width="300" %}}![](attachments/domain-models/deletion.png)
    {{% /image_container %}}

{{% alert type="info" %}}

您不能删除 *名称* 和 *大小* 图像和文件实体的属性。

{{% /报警 %}}

