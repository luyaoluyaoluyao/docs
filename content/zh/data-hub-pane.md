---
title: "数据枢纽面板"
parent: 视图菜单
menu_order: 15
description: "描述Mendix Studio Pro中的数据中心窗格。"
tags:
  - "studio Pro"
  - "数据中心"
  - "数据中心窗格"
  - "数据枢纽目录"
---

## 1 导言

[Mendix Data Hub](/data-hub/) 能够将来自不同应用程序的可用数据源整合到您的 Mendix 应用中。 这意味着可以使用在 [数据枢纽目录](/data-hub/data-hub-catalog/) 注册的共享数据集创建新应用。 在Studio Pro中，这可以使用数据枢纽目录通过 **数据枢纽** 面板的综合功能。

{{% alert type="info" %}}
您需要许可证才能在 Studio Pro中使用数据中心。 欲了解更多信息，请参阅 [Data Hub License](consumed-odata-service-requirements#license-limitations)。
{{% /报警 %}}

您可以在数据枢纽目录中通过 **数据枢纽** 面板搜索数据源，发现您可以在应用中使用的数据源。 通过这个窗格，您可以将在注册的 OData 服务中曝光的实体添加到您的应用域模型中——在Data Hub中称为 **数据源**。 这些实体被称为 [外部实体](external-entities) 并且是不同的，因为它们能够连接到原始应用中与实体相关的数据。

{{% alert type="info" %}}
在数据枢纽目录， 注册发布的服务被称为 *数据源* ，曝光实体将显示 **实体集** 名称并调用 *数据集。*
{{% /报警 %}}

要显示 **数据枢纽** 面板，请点击 **查看** > **数据枢纽**:

{{% image_container width="300" %}}![data-hub-pane](attachments/data-hub-pane/data-hub-pane-empty.png){{% /image_container %}}

## 2 域模型中的数据枢纽面板

数据枢纽窗格用于搜索数据枢纽目录中可以在您的应用中拖放和使用的实体，以及显示在您当前模型中消耗的外部实体和相关服务

### 2.1 数据中心搜索

{{% image_container width="300" %}}![](attachments/data-hub-pane/data-hub-pane.png){{% /image_container %}}

以下功能可在窗格中使用：

* [搜索](#search) — 输入一个数字字符的搜索字符串，以便在数据集目录中搜索。 将在目录中对服务、实体、属性、协会和描述进行搜索。

* [过滤器](#search) - 默认情况下，搜索将在 **Product** 环境中进行。 点击 **筛选器** 图标来包含所有其他环境，如测试 在搜索中接受和Mendix 免费应用环境 **Sandbox**

* [搜索结果](#viewing) - 搜索结果将显示目录中符合搜索字符串的所有资产。 对于每个“点击”，显示的信息包括服务名称、服务版本， 服务部署到的环境以及匹配搜索字符串的资产。 如果属性或关联符合搜索标准，它们将被显示。 您可以将该实体从搜索结果拖动到您的域模型，它将被显示为 [个外部实体](external-entities)：

  ![](attachments/data-hub-pane/external-entities-in-domain-model.png)

  目前在当前域模型中使用的服务和实体都在搜索结果中带有绿色标记。

### 2.2 数据枢纽应用面板

当在 **数据枢纽** 面板中没有指定搜索字符串时， **App** 部分被显示。 这显示当前项目中使用的服务和外部实体。 消费服务的实体、协会和属性列表显示为搜索结果：

{{% image_container width="300" %}}![Project Section](attachments/data-hub-pane/project-section.png){{% /image_container %}}

若要将实体添加到您的应用模式，请参阅 [将外部实体添加到一个项目](external-entities#adding-external-entities) 项目。

## 正在搜索数据枢纽目录 {#search}

当您输入一个搜索词时，满足搜索字符串的数据集目录中的所有条目都列在搜索结果中。 这将包括服务、实体和属性描述中没有显示在数据集窗格中。 欲了解更多信息，请参阅 [Data Hub CatalogAsset详细信息](/data-hub/data-hub-catalog/search#search-details)。

{{% alert type="info" %}}Services that are set to **not-Discoverable** in the Catalog will not be included in the search results for *any* user including owners of the service. 要消耗这些服务所有者的实体必须确保他们是 [可被发现的](/data-hub/data-hub-catalog/curate#discoverability)。{%/提醒 %}}

### 3.1 野生卡搜索
您可以通过在搜索区域输入 `*` 来执行通配符搜索。

{{% alert type="info" %}}
搜索字符串必须至少 3 个字母数字字符。 标点不能用作搜索术语的一部分，但通配符字符 `*` 才能在数据集目录中进行“空”搜索。 您不能使用通配符和其他字符。 欲了解更多详情，请参阅 [如何搜索注册资产](/data-hub/data-hub-catalog/search)。
{{% /报警 %}}

### 3.2 服务环境
默认情况下，搜索将在 **Production** 环境中进行。 要包括所有其他环境，如测试、接受以及Mendix 免费应用环境， **沙箱** 在搜索中， 点击 **筛选器** 图标并检查 **显示开发环境**:

{{% image_container width="300" %}}![Filter Icon](attachments/data-hub-pane/filter-icon.png){{% /image_container %}}

{{% alert type="info" %}}
选中 **显示开发环境** 时，所有随后的搜索结果也将包括非生产环境中的搜索结果。
{{% /报警 %}}

## 4 搜索结果和应用面板中的信息 {#viewing}

搜索结果显示指定的搜索字符串和环境的所有点击数。 关于数据集目录搜索结果的更多信息，请参阅 [搜索结果](/data-hub/data-hub-catalog/search#search-results)。

每次点击都显示以下信息。

### 4.1 服务

搜索结果和 **项目** 窗格将在服务级别显示以下内容：

* **服务名称**

*  **此服务的应用程序图标** (例如Mendix, SAP, Siemens Teamcenter, 或在上面的屏幕截图中显示, 自定义图标)

* **服务版本**

*  **非生产环境的环境名称**

    {{% alert type="info" %}}Only the names of non-production environments are displayed. **Production** 中的服务将不会显示一个环境名称。 {{% /报警 %}}

* **绿色复选标记** 如果服务或实体在应用中被消耗。 如果您右键单击消费的服务，您可以做以下操作：

  {{% image_container width="250" %}}![info on a Service](attachments/data-hub-pane/data-hub-pane-menu.png){{% /image_container %}}

  * **在 Data Hub 目录中查看** - 点击此处前往 **Data Source Details** 页面
  * **前往连接设置** - 点击此处打开 [耗用的 OData 服务](consumed-odata-service) 文档

* **Blue** **更新服务** 图标以表明数据枢纽中存在另一种已消耗的服务。 单击以更新在应用程序中消费的服务到现在可用的合同：

    {{% image_container width="250" %}}![Data Hub Pane update](attachments/data-hub-pane/project-pane-update-available.png){{% /image_container %}}

    ●{% alert type="info" %}}如果有OData服务更新可用. 然后列出的实体是那些在OData服务中可以找到的实体。 这些实体将被“灰色出”，以表明它们不能被拖入域模型。 因为应用程序中消耗的 *当前的* 合同没有这些实体。 您必须通过点击 **更新** 箭头来更新合同到搜索结果中显示的版本。 {{% /报警 %}}

  {{% alert type="info" %}}The version number that is shown for the OData service is the latest one that is available in the Data Hub Catalog at the service endpoint—in the example above version 1.0.0 of **BikeVehicleService** is currently consumed in the app, but the contract that is available in the Catalog is different to the one currently consumed.{{% /alert %}}

* **信息图标** 以查看服务的更多细节，以及直接到 [服务详细信息](/data-hub/data-hub-catalog/search#search-details) 数据集目录中的屏幕：

  {{% image_container width="250" %}}![Data Hub Pane Information](attachments/data-hub-pane/data-hub-pane-info.png){{% /image_container %}}

### 4.2 实体、属性和协会 {#association-attributes}

符合搜索字符串的实体、属性和社团列在搜索结果中。

对于列表中的任何服务。 您可以点击 **:Show details** 查看该服务的曝光实体和关联及属性的完整列表。

●{% alert type="info" %}}您的 Mendix 模型不支持的关联和属性显示为不可选择(灰度)，当您将它们拖动到域模型时不会被包含。 {% /提醒 %}}

{{% image_container width="250" %}}![Data Hub Pane Information](attachments/data-hub-pane/expand-service-list.png){{% /image_container %}}

### 4.2.1 实体

如果您右键单击实体并在数据集目录</strong>中选择 **查看 它将把您带到 [Data Hub 目录](/data-hub/data-hub-catalog/) 中的实体详细信息页面。</p>

如果你右键单击消费的实体并 **转到实体**, 它将带你到域模型中的实体。

### 4.2.2 协会

在服务中曝光的社团按字母顺序排列在属性之前。 您可以点击 **+** 来查看关联的实体。

**在单个关联之前显示相同实体之间的多重关联**。

在下面的示例中， **客户** 与实体 **订单有多个关联** 这些关联不被支持，不能用于您的模型。”

{{% image_container width="250" %}}![multiple associations](attachments/data-hub-pane/multiple-assocs.png){{% /image_container %}}

### 4.2.3 属性

服务的属性按字母顺序列出。 如果您右键单击消费实体的属性，然后 **转到属性**它将带你到域模型中的属性。

在上述例子中，有两个属性， **地址** and **FavoriteColors** 不支持，因此不会被包含在您的模型中：

{{% image_container width="300" %}}![multiple associations](attachments/data-hub-pane/unsupported-attributes.png){{% /image_container %}}

## 5 阅读更多

* [数据集目录](/data-hub/data-hub-catalog)
* [外部实体](external-entities)
* [消耗的 OData 服务](consumed-odata-service)
* [如何使用注册资产](/data-hub/data-hub-catalog/consume)
