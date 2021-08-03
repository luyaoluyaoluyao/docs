---
title: "外部实体"
parent: "域名模型"
menu_order: 15
tags:
  - "域模型"
  - "实体"
  - "实体"
  - "属性"
  - "外部实体"
  - "甚至处理器"
  - "访问规则"
  - "studio pro"
  - "消耗的 OData 服务"
---

## 1 导言

外部实体可以通过 [数据枢纽窗框](data-hub-pane) 添加到域模型。 他们在 Domain Model 中被显示为 *紫色* 实体容器。 外部实体代表通过 [Mendix Data Hub](/data-hub/) 注册的共享数据源提供的数据集链接。 数据来源是在OData服务中公布的各实体集集集（称为数据集）。

数据集在源应用程序中维护和更新。 You can integrate or *consume* these datasets through external entities in your app development, and any changes to the data in the originating app is automatically updated in the consuming apps.

然而，外部实体可以与地方实体一起使用。 因为数据集是在源应用程序中保存的，因此不是所有属性都可以在消耗应用程序中更改。

要关注如何从 **数据枢纽** 窗格中添加外部元素，请参阅 [添加外部实体](#adding-external-entities)。

{{% alert type="info" %}}
使用Mendix Data Hub 并通过在您的应用中消费的 OData 服务连接到外部数据源是必需的。
{{% /报警 %}}

## 将外部实体添加到应用程序 {#adding-external-entities}

若要将外部实体添加到您的应用模型，请遵循以下步骤：

1. 在您的域模型中，应用模型在 **Data Hub** 窗格中搜索您想要在应用中使用的实体或数据源。

    ●{% alert type="info" %}}在 [Data Hub 目录](/data-hub/data-hub-catalog/search), 一种OData服务可能是多次注册，有不同的版本号或部署到不同的环境， 所有曝光您可能想要使用的实体 (数据集)) 首先搜索数据集目录，然后找到与您应用的要求最相关的。{%/提醒 %}}

3. 拖放域模型中的实体。

4. 实体及其属性然后添加到您的应用，并且在 **App Explorer** 中添加了两个文档：

    * **消耗的OData服务** 文档包含OData服务的详细信息和元数据； 所显示的徽标识别了服务的原始应用
    * 指定服务位置常量的 **OData 位置**

    ![ 虚拟实体和 OData 服务文件](attachments/external-entities/consumed-service-docs.png)

{{% alert type="info" %}}
当您从同一服务中拖动一个与实体关联的实体时，已经在您的域模式中， 社团将在实体之间显示和建立。 欲了解更多关于外部实体之间关联的信息，请参阅 [Associations](#properties)。
{{% /报警 %}}

欲了解更多信息，请参阅 [消耗的OData服务](consumed-odata-service)。

在 **App** **Data Hub** 的部分中，列出了当前应用程序中所消费的实体：

![ 虚拟实体和 OData 服务文件](attachments/external-entities/data-hub-app.png)

{{% alert type="info" %}}
如果有新版本的消费服务可以在数据枢纽Catlog中获取， 这将在 **数据枢纽** 面板中通过更新的箭头与服务名称相匹配。 欲了解更多信息，请参阅 *消费的 OData 服务* 中的 [更新或切换消费的 OData 服务](consumed-odata-service#updating) 部分。
{{% /报警 %}}

您可以对外部实体的属性进行本地更改，这只会影响数据在消费应用程序中的使用和显示方式。 所有其他属性都在源应用程序中定义，不能更改。 当同一OData服务的多个外部实体被用于模块或应用程序时， 实体间的关联(创建于源应用程序中)将自动在本地模块中。

{{% alert type="info" %}}
如果您从域模式中删除外部实体， 服务文档仍然留在应用探索器列表中，服务仍然被列入数据集应用窗口。 如果您不再使用消费服务中的任何实体，您可以删除这两个服务文档。
{{% /报警 %}}

更多关于通过数据中心目录使用已发布的OData服务和实体的信息 查看 [如何消耗注册资产](/data-hub/data-hub-catalog/consume) 在 *数据中心指南* 中。

## 外部实体的属性 {#properties}

与地方实体相比，外部实体的财产数量有限，可以改变。 属性的其余部分在原始应用程序中定义，因此是只读的。

{{% alert type="info" %}}
对外部实体的特性所作的更改只在消费中进行。 原始应用不会受到更改的影响。
{{% /报警 %}}

### 2.1 概况

此选项卡显示外部实体的一般属性。 在原始应用程序中定义的值被显示但不能编辑。 可以编辑的值只适用于本地应用：

![外部实体属性](attachments/external-entities/external-entity-properties.png)

* **名称** - 本地应用中的实体名称
* **原名** - 这是只读的，并显示消耗的 OData 服务中定义的实体名称
* **摘要** - 这是一个只读字段，并在原始应用程序中显示实体的描述

### 2.2 属性 {#attributes}

外部实体OData服务中暴露的 [属性](attributes) 在此列出。 所有对属性和属性列表的更改都适用于实体的本地实例。 他们在消费时， 这些变化不会影响该实体所接触的消费服务的元数据或该实体在原始应用中的属性。

{{% alert type="info" %}}In the [Data Hub Pane](data-hub-pane#association-attributes) the associations and attributes that are not supported in your Mendix model are shown as non-selectable (gray) and will not be included when you drag them into the domain model or be included in the entity properties. 欲了解更多信息，请查看 [数据枢纽面板](data-hub-pane#association-attributes){{% /提醒 %}}

以下操作可以在显示的属性列表中完成：

* **添加** - 添加实体OData服务中暴露并先前为这个本地实例移除的属性
* **编辑** - 从 [编辑属性](#edit-attribute) 表单中编辑选定的属性
* **删除** - 从列表中删除一个属性

#### 2.2.1 编辑属性 {#edit-attribute}

**编辑属性** 框可以用于指定属性的本地名称并添加本地描述。

![编辑属性](attachments/external-entities/edit-attributes.png)

* **常规标签**
    * **名称** -- 可以指定属性的本地名称。
    * **原始名称** - 这是一个只读的值，显示原始应用程序中给出的属性的原始名称
    * **摘要** — 一个只读的摘要，显示原始应用中属性的描述； 要输入本地描述，请在 [文档选项卡中添加](#documentation)
    * **输入** — **类型** 和 **长度** 和 **最大只读卷。 原始应用定义的属性长度**
* **文档** - 显示给当前应用用户的属性描述

### 2.3 社会联系 {#associations}

此选项卡显示外部实体与在同一服务中暴露的其他实体以及与当地实体建立的任何协会之间的联系。 关于Studio Pro 中关联属性的详细信息，请参阅 [Association Tab Properties](association-member-properties)。

![编辑属性](attachments/external-entities/external-entity-associations.png)

以下内容适用于外部实体的所有社团：

**名称** -- 当前应用程序显示的关联名称 **类型** -- 两个外部实体之间的关联只读 **所有者** -- 两个外部实体之间的关联只读 **父** -- 两个外部实体之间的关联只读 **子** -- 两个外部实体之间的关联只读**</p>

您可以 **添加** and **编辑** 关联到具有本地实体的外部实体。 However, the association cannot be made *from* an external entity to a local entity: the local entity must be the owner of the association.

如果您在应用中使用外部实体且此实体与您应用中相同的 OData 服务的其他外部实体相关联， 关联将自动添加到域模型并在此列出。

{{% alert type="info" %}}
**可以删除** 个外部实体之间已被自动添加的域模型中的关联。 如果在稍后阶段，您想要恢复此社团， 您可以在域模型中通过右键单击外部实体之一并点击 **添加** > **关联** 来做到这一点。
{{% /报警 %}}

{{% alert type="info" %}}
如果您想要连接两个没有连接到原始应用的外部实体， 这是不可能的，因为与数据的关系不能受到局部影响。 然而，考虑增加一个地方实体，并将这个地方实体与两个外部实体联系起来。 在这种情况下，地方实体必须是这两个协会的所有者。
{{% /报警 %}}

### 2.3.1 关联财产

当您 **编辑** 一个包含在同一OData服务中的两个实体的关联 以下属性被显示，而本地唯一可以做出的更改是本地名称：

![编辑外部关联](attachments/external-entities/association-properties.png)

* **名称** - 协会的本地名称
* **原始名称** -- 原始应用程序给它的只读关联名称
* **摘要** - 原始应用程序中只读的关联描述
* **多重性** - 只读的原始应用的多重性值
* **文档** - 到此选项卡添加外部实体关联的本地描述

### 2.3.2 连接两个外部实体

如果您想要连接两个没有连接到原始应用的外部实体， 这是不可能的，因为与数据的关系不能受到局部影响。 然而，您可以添加本地实体并将这个本地实体与两个外部实体连接起来。 在这种情况下，地方实体必须是这两个协会的所有者。

### 2.4 文件 {#documentation}

您可以在此选项卡中添加任何关于外部实体的本地信息。

## 3 外部实体限制

外部实体是已发布OData服务中从原始应用定义的终点。 当外部实体通过 **数据枢纽** 面板使用时，消耗的 OData 服务文档显示服务元数据的值。 对外部实体的限制是，它们是只消费的实体。 与实体相关联的数据集保存在原始应用中。

欲了解更多关于消耗服务和暴露实体的详细情况，包括可在外部实体上进行的业务， 查看 [如何消耗注册资产](/data-hub/data-hub-catalog/consume) 在 *数据中心指南* 中。
