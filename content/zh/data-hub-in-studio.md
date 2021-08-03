---
title: "工作室中的数据中心"
category: "使用数据"
menu_order: 30
description: "描述Mendix Studio中的数据中心目录使用情况。"
tags:
  - "工作室"
  - "数据中心"
  - "数据枢纽目录"
  - "外部实体"
---

## 1 导言

每个组织都有包含宝贵数据的应用，也可以用于其他应用程序。 [Mendix Data Hub](/data-hub/) 使您能够使用来自其他应用的数据，而不必处理复杂的远离理想的解决方案。 例如输出数据、复制数据或建立复杂的技术一体化。 有了数据枢纽，您需要做的只是搜索数据，选择并使用它。

Mendix Data Hub 是本组织的中心中心，使您能够发现， 在您的组织中连接并使用来自不同应用的共享数据。 它还确保数据在整个组织内得到一致使用。

共享数据在 [数据集目录](/data-hub/data-hub-catalog/) 中注册为 *服务*。 通过 Studio的 **数据枢纽** 标签，您可以访问数据枢纽目录中的数据。 您可以找到来自服务的外部实体。将它们添加到您的应用以及他们的属性和关联，并且在本地使用。 实体、属性和协会的属性将是只读的。

例如，您有一个 *员工上岗应用程序* 包含了哪些设备应该分配给新员工的信息。 您的组织也有一个 *公司的 HR* 应用程序，它拥有所有的员工数据。 Data Hub 函数. 您将能够在您的 *员工在线应用程序* 中使用 *HR 应用程序* 的 (消费) 数据，而不是需要复制数据并手动保持同步。

For more information on how to use data in your app, see the [Selecting External Entities on Pages](#select-external-entities) section.

{{% alert type="info" %}}
如果您的组织拥有数据中心许可，您可以访问数据中心。
{{% /报警 %}}

## 2 在页面上选择外部实体 {#select-external-entities}

通过 Data Hub 目录可用的实体被称为 *外部实体* ，因为它们来自外部来源(*一个源应用程序*)。

您可以选择外部实体作为数据容器的数据源 (数据视图，列表视图或数据网格)。 要选择一个外部实体，请执行以下操作：

1. 打开数据容器的 **属性**。
2. 点击 **实体** 属性。
3. 在 **选择实体** 对话框中，您可以在数据集目录中搜索外部实体并在您的页面上使用它们。 发现实体有两种方法，您可以做以下一种：
    1. **搜索特定服务或实体名称** - 在搜索字段中输入搜索词以找到您想要添加的实体：

        {{% image_container width="400" %}}![Searching for an Entity](attachments/data-hub-in-studio/searching-for-entity.png){{% /image_container %}}

    2. **浏览可用数据** - 点击 **数据中心** 部分并浏览现有服务和实体：

        {{% image_container width="400" %}}![Selecting an Entity](attachments/data-hub-in-studio/selecting-entity.png){{% /image_container %}}

3. 点击 **选择**。

所选外部实体将与所有集成和安全设置一起自动添加到您的域模型。 ![域模型](attachments/data-hub-in-studio/domain-model-example.png)

当你 [发布你的应用程序](publishing-app), 你可以看到来自外部实体的数据显示在你的应用程序中。

当你 [预览你的应用程序](publishing-app), 你会看到来自外部实体的数据。 但需要认证证书的服务中的外部实体除外。 在这种情况下，您必须发布您的应用才能查看数据。

### 2.1 数据枢纽标签

**数据枢纽** 标签 **选择实体** 对话框向您展示了扩展到您组织可用实体列表的服务列表：

![数据枢纽部分图表](attachments/data-hub-in-studio/data-hub-tab-diagram.png)

在 **数据集** 标签中，您可以做以下工作：

* **搜索** - 当您输入一个搜索词时，您将获得一个可供您组织使用的服务和实体列表。 以及您应用中已经使用的实体和服务。

    {{% alert type="info" %}} In Studio, you can discover services that are published to a **Production** environment. {{% /报警 %}}

* **过滤Studio不兼容的服务** — — 一些服务需要与Studio不兼容的身份验证。 您只能在 Studio Pro中使用它们。 您可以查看所有服务，或者只过滤兼容的服务。 在下拉菜单中选择以下选项之一：

    * **所有服务** - 所有服务将显示在 **数据中心** 选项卡。
    * **Studio Compatible Services** - 只有与 Studio 兼容的服务会显示在 **Data Hub** 选项卡中。

* **查看您的应用所使用的服务** - 已经在您的应用中使用的服务被标记为绿色的检查标记。

* **更新服务** - 当有新版本的服务时，您可以更新它。 然而，最好先检查数据枢纽目录中服务的变化。

    {{% image_container width="500" %}}![Update Available](attachments/data-hub-in-studio/service-update.png){{% /image_container %}}

    点击下拉菜单选择以下选项：

    * **现在更新** - 允许您更新服务到新版本。
    * **显示更改** - 将您带到数据中心目录，在那里您可以检查服务中发生了什么变化。

* **查看服务中可用的外部实体** - 您可以扩展服务信息以查看哪些外部实体可用。

* **查看服务** - 服务名称和版本号。 点击信息图标查看服务上的以下信息：

    * **服务名称** — — 在数据集目录中注册的共享数据源的名称。

    * **版本** - 每个服务都有一个版本号。 当您消耗某个服务的数据时，您将消耗某个特定版本的服务发布到环境中。 如果更改，将发布新版本的服务。

    * **上次更新** - 指明上次更新服务的日期。

    * **技术所有者** -- 与服务技术所有者的链接 (默认情况下，这是注册服务的所有者) 但这可以在数据集目录中改变)。

    * **企业所有者** — — 链接到服务连接到的数据的企业所有者。

    * **联系** - 与企业所有者联系。

    * **在数据枢纽目录中查看** - 一个链接到您组织的数据枢纽目录。

        {{% image_container width="300" %}}![Service Information](attachments/data-hub-in-studio/service-information.jpg){{% /image_container %}}


## 3 个外部实体属性

外部实体在域模型中彩色 *紫色*

![外部实体](attachments/data-hub-in-studio/external-entity.png)

当您添加外部实体到您的应用程序时，可以对实体进行本地更改，例如更改它的名称。 然而，这些更改是有限的，只适用于您的应用。 外部实体的大多数属性都是只读的，因为它们是在源应用程序中定义的(这确保您不会意外更改源应用程序中的数据)：

![外部实体属性](attachments/data-hub-in-studio/external-entity-properties.png)

### 3.1 外部实体属性

您可以重命名外部实体属性以更好地适应您的应用结构。 它仍将是包含相同数据的属性。 表示此更改将是您的应用的本地且不会影响源应用。 除了 **名称** 属性之外，所有其他属性都是只读的。

![外部实体属性属性](attachments/data-hub-in-studio/external-attribute-properties.png)

外部属性可能有您可以在其属性中看到的限制。 限制由外部服务所有者添加，以表示不支持的功能。 例如，如果对某一属性有限制， 您将无法在页面和微流中过滤和/或排序。

{{% image_container width="250" %}}![Attribute with Limitations](attachments/data-hub-in-studio/attribute-with-limitations.jpg){{% /image_container %}}

{{% alert type="info" %}}

您不能删除外部实体的属性。

{{% /报警 %}}

### 3.2 外部实体协会

如果您从同一服务中添加两个在源应用程序中具有关联的实体，这个关联将自动添加。

您只能在本地实体和外部实体之间创建和编辑关联。 然而，该协会应该始终把 **指向** 外部实体，而不是 **指向** 指向它。 这就是为什么不可能在地方和外部实体之间建立多对多个联系的原因。

例如，您可以创建一个从本地实体 **订单** 到外部实体 **客户** 的关联：

![外部联系示例](attachments/data-hub-in-studio/association-example.png)

您不能更改或删除此关联。 在源应用中没有联系的两个外部实体之间也不可能建立联系。

## 4 阅读更多

* [数据中心](/data-hub/)
* [数据集目录](/data-hub/data-hub-catalog/)
