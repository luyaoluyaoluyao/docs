---
title: "消耗的 OData 服务"
parent: "消费-odata-服务"
menu_order: 10
tags:
  - "studio pro"
  - "数据中心"
  - "odata服务"
  - "消耗的 odata 服务"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/consumed-odata-service.pdf)。
{{% /报警 %}}

## 1 导言

当一个外部实体通过 [数据枢纽窗格](data-hub-pane)在一个项目模块中使用时 a 消耗的OData服务文件增加具体说明所消耗服务的细节。 这是发布应用的 API 以及与实体相关联的数据。

## 2 消耗OData服务屏幕

添加到项目的 **消耗的 OData 服务** 文档显示以下信息：

![连接标签](attachments/consumed-odata-service/consumed-odata-doc-connection-tab.png)

* 原始应用的源应用程序的服务名称和图标
* 消耗的服务的版本号
* **在数据集目录** 链接到 **服务详细信息** 您可以在那里看到注册的完整服务详细信息
* **更新/更新** - 您可以将消费的服务合同更新到其他版本，在 [Mendix Data Hub](/data-hub/) 中检测到相同的应用和服务； 按键将显示下面的内容，这取决于在数据枢纽中消费的合同返回的内容：
  * **更新** - 此按钮显示为您可以 **更新** 当前消耗的合同(在 **消耗的OData服务** 文档中显示)。 您将收到目前处于服务端的合同。 良好的做法是，只对同一个最终点进行小规模的、没有突破性的改动。
   * **切换** - 如果同一服务的其他注册实例(同名) 则显示此按钮 来自同一应用的数据集可以在不同的端点进行部署（例如）。 到另一个环境或因为更改会破坏现有的消耗上一个版本的应用)

    {{% alert type="info" %}}Studio Pro displays the **Update** option for the **Consumed OData Service** where you can check if an update is available. 在 Data Hub 搜索和 **Project**  面板中， 当在服务端点检测到不同的合约时，将会显示为服务的更新箭头。 欲了解关于更新和切换服务的更多信息，请参阅此文档的 [更新或切换消费的 OData 服务](#updating) 部分。 {{% /报警 %}}

    {{% alert type="info" %}}In the **Data Hub** pane consumed services that have an available **Update** will have an update arrow to indicate this:<br /> ![更新服务数据中心面板](attachments/consumed-odata-service/data-hub-pane-update-available.png)
    {{% /报警 %}}

### 2.1 连接选项卡

**连接** 标签显示消耗的 OData 服务的连接值：

### 2.2 服务网址 {#service-url}

**服务 URL** 显示服务端点的URL：

* 点击 **选择** 来选择另一个 [常量来提供服务](/refguide8/constants)
*  点击 **显示** 以显示 **常量** 显示服务 URL 或端点的对话框：

    ![连接标签](attachments/consumed-odata-service/consumed-service-constant.png)

### 2.3 超时

**超时** 是从服务端点获取数据的响应时间。 如果端点在 **超时秒**之后没有响应，将发生异常。 如果在微流活动中发生这种情况，微流将回滚或进入您的自定义 [错误处理](/howto8/logic-business-rules/set-up-error-handling)。

默认值： *300秒*

### 2.4 代理配置

**代理配置** 允许您配置是否为请求使用代理：

* **使用项目设置** - 使用在项目级别上定义的设置 (默认)
* **覆盖** - 通过指定代理的主机、 端口、 用户名和密码设置来覆盖此操作的项目级别设置
*  **没有代理** - 不为此服务使用代理，即使在项目一级配置了代理服务器

{{% alert type="info" %}}
在大多数情况下，此设置可能被忽略，默认使用 **使用工程设置**。
{{% /报警 %}}

### 2.5 身份验证

**使用HTTP身份验证** 复选框指定是否使用基本身份验证。 如果选中，您必须指定以下详细信息：

* **用户名** - 定义将用于身份验证的用户名
* **密码** - 定义将用于身份验证的密码

除了基本的身份验证，您可以使用自定义身份验证。 欲了解更多信息，请参阅下面 [HTTP 头](#http-headers) 部分。

### 2.6 HTTP 头 {#http-headers}

您可以通过点击 **添加**来指定要传递到此列表中端点的额外的 HTTP 请求头， **编辑**或 **删除** 用于自定义认证的 HTTP 头文件。 每个自定义标题都是一个键值和一个值。

使用 **个来自微流程的**头, 您可以指定一个微流程来创建一个按键和动态值对的值。 microflow 必须返回一个 **System.Httpheader** 对象列表。

{{% alert type="info" %}}
为了更灵活的 HTTP 请求标题，您可以选择返回 **System.Httpheader** 列表的微流程。 这种微流可能会使用类型 **System.HttpResponse** 的参数。 每次提出请求时，微流都被调用。 最初，HTTP响应参数将为空。 如果响应为 **401 未授权**， 微流与HTTP响应调用，并且使用新的 HTTP 头进行另一次调用。
{{% /报警 %}}

{{% alert type="info" %}}
自定义身份验证可以在获取身份验证值的微流中进行(例如SSO)。 关于访问和认证的进一步信息， 查看 [在 *数据中心指南* 中为发布的实体使用自定义 HTTP 头验证](/data-hub/data-hub-catalog/security#http-header-validation)。
{{% /报警 %}}

## 3 Metadata Tab {#metadata}

在 **元数据** 标签中，您可以选择一个元数据文件或使用通过 URL 获取的元数据：

![Metadata Tab](attachments/consumed-odata-service/metadata-tab.jpg)

### 3.1 元数据编辑器

元数据编辑器允许从文件或 URL 中打开 OData合同。 当您已经消费了一个合约，您可以使用此编辑器更新您现有的合约，从文件或 URL 中更新一个新版本。

要打开 **元数据编辑器**，请点击 **编辑**。 在编辑器中，您可以指定元数据的 URL 或文件：

![元数据编辑器](attachments/consumed-odata-service/metadata-editor.jpg)

以下设置是可用的：

* **从** - 选择 **URL** 或 **文件** 获取元数据的位置：
    * **URL** - 点击 **编辑** 以指定元数据的 URL
    * **文件** - 点击 **浏览** 以选择一个 XML 元数据文件

支持基本身份验证已从 [版本 8.16.0](/releasenotes/studio-pro/8.16) 添加。 当从 URL 下载元数据时，服务器可以请求用户名和密码(基本身份验证)。 在这种情况下，对话框会提示您输入您的用户名和密码。 如果元数据文件指的是同一服务器在同一范围内的其他元数据文件，用户名和密码将被重新使用。

{{% alert type="info" %}}
此信息未存储，所以如果您再次从同一服务器下载元数据。 您必须再次输入您的用户名和密码。
{{% /报警 %}}

当您导入元数据时，您可以从 [Data Hub Pane](data-hub-pane) 中添加外部实体。

### 3.2 消耗的OData服务属性

单击消耗的 OData 服务的 **属性** 标签，它显示为 OData 服务文档定义的属性和以下附加属性：

![](attachments/consumed-odata-service/consumed-odata-service-doc-properties.png)

* **实体** - 定义实体和相关数据集的元数据的 URL
* **文档** — — 关于当前应用此服务的附加描述
* **服务名称** — — 已发布的 OData 服务的名称已消耗。
* **服务版本** — — 所消耗的服务版本
* **服务 ID** - 数据集目录中服务的唯一标识符
* **应用程序 ID** - 服务在数据集目录中发布的应用程序唯一标识符
* **元数据** — — 定义服务的元数据文件内容
*  **OData版本** - OData版本：可以是 OData 3 或 OData 4

## 4 更新或切换消耗的OData服务 {#updating}

### 4.1 从服务端点消耗{#consume-service-endpoints}

当您将外部实体添加到您的项目时， 您正在消耗一个特定版本的服务 ( *服务端*)中的实体，并部署到给定的环境。 服务的元数据文件或合约位于此端点。

相同的服务， 部署到不同环境的服务端点将是不同的服务端，这将作为不同的资产在数据枢纽目录中注册。 在下面的例子中， **CustomerApi 服务版本1.1有两个端点。** 部署在生产环境和 **接受环境** 环境：

{{% image_container width="250" %}}![2 endpoints](attachments/consumed-odata-service/same-service-different-endpoints.png){{% /image_container %}}

当您拖动 **客户** 实体从 **CustomerApi 版本 1.0。** 部署到 **接受** 环境进入您的项目 Studio Pro 将从处于端点的合同中检索它所要求的信息。

### 4.2 服务版本语义编号 {#semantic}

重要的是，这些服务的出版商对其出版的OData服务所做的任何修改都采用严格的修订程序，而这些服务是由其他用户消费的。

我们建议在发布服务更新时使用严格的版本系统，例如语义编号。 服务版本应明确说明根据下列准则更新和部署某项服务时所作修改的程度和严重程度。

#### 4.2.1 次要服务更新

*次要的* 服务更新 添加到服务或新操作中的字段不会破坏任何消耗先前版本的应用程序。

如果使用语义编号, 则可以通过版本号的十进制部分的增加来表示对某项服务的小规模/非破碎更改。 例如，1.0.11、1.0.12、1.1、1.2。

小服务更新可以部署到相同的服务端，从而确保所有消耗的应用都消耗最新版本的服务。

#### 4.2.2 主要服务更新

*主要* 服务更新是实体或属性被删除时， 或者输入参数是必需的，这对消费应用是不兼容的，并导致消费应用“断开”。

当对已发布的服务做出重大改动时，我们建议将该服务部署到 *不同的端点* ，新的服务版本号清楚地表明已经发生了重大变化——语义编号的这将是一个整体的递增数。

在这种情况下，新的服务将作为不同的服务注册在数据集目录中。 并作为单独资产在目录中显示。 在下面的示例中， **订单管理服务** 有4次注册发生：

{{% image_container width="250" %}}![4 endpoints](attachments/consumed-odata-service/consume-major-service-update-version.png){{% /image_container %}}

版本号从 **1.0.0** 更改为 **2.0.0** 显示了一个主要的服务更新。 此外，这两个版本也已经部署到 **接受** 上，这也导致数据集目录中的单独注册资产。

{{% alert type="info" %}}
非Mendix OData服务的实体被确定为一个或多个领域的钥匙。 如果在更新服务时更改关键字段，这也将被视为一种突破性的变化。
{{% /报警 %}}

### 4.3 更新或交换机

当在 Data Hub 中检测到消费服务的次要更新和主要更新时，以下选项可在 **消耗的 OData 服务** 屏幕上获得。

#### 4.3.1. 更新

**更新** 选项是可用的，当发布已发布的 OData 服务的新版本时。 并部署到与以前版本相同的端点。 Studio Pro 将承认在项目结束时的合同不同于目前在项目中消费的合同。 更新Studio Pro 后将与端口上的合同相同。

##### 4.3.1.1 项目面板

在 **项目** 窗格中，这将显示如下所示：

![更新服务项目窗格](attachments/consumed-odata-service/project-pane-update-available.png)

- *当前消耗的服务版本* 已显示在这个示例 **1.0.11**
- 蓝色 **更新** - 点击打开 **更新服务** 框并将合同更新到新合同。 Studio Pro 将从 Data Hub 检索新的合同，这个项目将被加载。
- 从当前服务版本消耗的实体列表，这些实体由绿色的检查标记显示

##### 4.3.1.2 数据集搜索结果

在 **数据枢纽** 窗格中，相同消耗的服务的搜索结果显示如下所示：

![更新 dhpane 服务](attachments/consumed-odata-service/data-hub-pane-update-available.png)

- 当前端点的服务版本， **1.0.12**

- 蓝色 **更新** - 点击打开 **更新服务** 框并将合同更新到新合同。 Studio Pro 将从 Data Hub 检索新的合同，这个项目将被加载。

- 显示新版本数据集的实体列表， 包括标有绿色标记的当地消费的实体。 然而，这些实体是： 很灰心地表示它们不能拖入域模型，因为前一版本的合同目前正在消耗。 唯一的选项是点击 **更新** 以检索更新OData服务。

##### 4.3.1.3 更新服务对话框

当您点击 **更新** 到 **消耗的OData服务** 文档或更新图标 **数据中心** 和 **项目** 窗格， 显示 **更新** 对话框。

![更新 dhpane 服务](attachments/consumed-odata-service/update-service-dialog-box.png)

当前在项目中消耗的 OData 服务**1.0。**显示在左边， 您可以点击 **更新** 从数据中心检索新的合同 (**2)。 0**

#### 4.3.2. 交换机

当OData服务发布到不同的端点或不同的环境时，这将意味着它将作为不同的资产在数据中心目录中登记。

在上面服务端点</a> 部分给出的
消耗示例中， 如果您正在从 **接受环境消耗服务** 环境， 消耗的OData服务屏幕将显示 **切换** 按钮以使您能够从 **生产**消耗相同的服务。</p> 



#### 4.3.3 切换消费服务

已发布的 OData 服务部署到多个环境或者发布时有主要的服务更新(因此部署到不同的端点)将作为单独的项目显示在 **数据枢纽** 面板的搜索结果中。

在下面的例子中，部署到生产环境的消费的 **订单管理服务** 版本 **1.0.0** 在应用程序中消费。 然而，在 **接受** 环境中也部署了同样的服务：

![主要变化环境](attachments/consumed-odata-service/consume-major-service-update.png)

要消耗部署到 **接受环境**的服务，请按照以下步骤：

1. 点击  **更新** > **在 **消耗的 OData 服务** 屏幕上切换**
   
   ![主要变化环境](attachments/consumed-odata-service/update-switch.png)

2. 在 **上切换** 对话框，下拉列表中的对话框。 选择您想要消耗的服务，然后点击 **切换**
   
   ![主要变化环境](attachments/consumed-odata-service/switch-environment.png)

3. 消费的服务现在将从新选定的环境中消费。 **消耗的 OData 服务** 屏幕上的信息将显示更改的服务详细信息。 **数据中心** 窗格现在将显示您正在从选定的环境中消费：
   
   {{% image_container width="300" %}}![major change environment dh pane](attachments/consumed-odata-service/switch-new-environment.png){{% /image_container %}}



## 5 阅读更多

* [数据枢纽面板](data-hub-pane)
* [消耗的 OData 服务](consumed-odata-service)
