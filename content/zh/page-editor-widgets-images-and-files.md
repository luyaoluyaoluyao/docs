---
title: "图像 & 文件"
parent: "页面编辑器部件"
description: "在 Mendix Studio 中描述图像和文件部件。"
menu_order: 30
tags:
  - "工作室"
  - "页面编辑器"
  - "图片"
  - "图像部件"
  - "小部件"
  - "文件"
  - "文件管理器"
  - "文件上传器"
  - "文件下载器"
---

## 1 导言

**图像 & 文件** 是允许最终用户查看、下载和上传图像或文件的小部件。 例如，通过图像上传，最终用户将能够上传个人资料图片：

{{% image_container width="350" %}}![](attachments/page-editor-widgets-images-and-files/image-uploader-example.png)
{{% /image_container %}}

Mendix Studio中有以下图像和文件部件：

* **图像** - 允许您在应用程序中显示静态(无更改) 图像

*  **动态图像** - 允许您显示动态图像 (例如) 在您的应用中，相关的个人资料图片对每个客户不同)

*  **图像上传器** - 允许最终用户上传图像

*   **文件管理器** - 允许最终用户上传或下载文件 **工具箱**您看到预配置的文件管理器： **文件上传器** 和 **文件下载器**)

    {{% image_container width="350" %}}![](attachments/page-editor-widgets-images-and-files/images-and-files.png)
    {{% /image_container %}}

## 2 个图像和动态图像属性

图像和动态图像部件允许您从文件中(静态)或数据库(动态)显示图像。

您可以在属性中从一个小部件切换到另一个小部件：

![](attachments/page-editor-widgets-images-and-files/static-and-dynamic-image.png)

### 2.1 一般部分 {#image-general}

在 **常规** 部分中，您可以在静态和动态图像之间切换，选择一个图像，配置其宽度和高度等。

Before configuring settings in the **General** section for the **Dynamic Image**, keep in mind that it can only function inside a data container (a list view or a data view). 您可以在现有数据容器中放置部件； 或点击 **用新的数据视图** 在 **属性** 自动创建数据视图并放置输入元素。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-images-and-files/dynamic-image-data-view.png)
{{% /image_container %}}

**静态图像** 和 **动态图像** 可用的设置在下表中描述：

| 财产    | 该属性适用于： | 描述                                                                                                                                                                  |
| ----- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 图像来源  | 静态和动态图像 | 在静态(从文件) 和动态(从数据库) 图像之间切换。                                                                                                                                          |
| 实体    | 动态图像    | 指定在动态图像中显示哪个实体。 您只能为动态图像设置一个实体，如果它是图像实体。 For more information on image entities, see the [Types of Entities](domain-models#entity-types) section in *Domain Model*. |
| 图片    | 静态图像    | 设置将显示给最终用户的图像。                                                                                                                                                      |
| 默认图像  | 动态图像    | 如果存储在数据库中，这是显示的图像。                                                                                                                                                  |
| 宽度单位  | 静态和动态图像 | 图像宽度可以通过以下方式指定：  <br /><ul><li>**自动** ——使用给定图像的宽度。</li><li>**Pixels** - 以若干像素指定宽度。 如果您同时指定宽度和高度，图像将自动缩放：比例将保持，图像将不会被拉伸。</li><li>**百分比** - 以原始宽度的百分比指定宽度。 它可以大于原来的宽度，在这种情况下，图像会被拉伸。</li></ul><br />Default value for **Width Unit**: Auto                                                            |
| Width | 静态和动态图像 | **宽度** 选项仅在 **像素** 或 **为 **宽度单位** 选择百分比** 时才显示。 它以像素或百分比指定图像宽度。                                                                                                     |
| 高度单位  | 静态和动态图像 | 图像的高度可以通过以下方式指定：  <br /><ul><li>**自动** ——使用给定图像的高度。</li><li>**Pixels** - 以多个像素来指定高度. 如果您同时指定宽度和高度，图像将自动缩放：比例将保持，图像将不会被拉伸。</li><li>**百分比** - 高度以原始高度的百分比指定。 它可以大于原来的高度，在这种情况下，图像会被拉伸。</li></ul><br />**高度单位**的默认值：自动                                                                                  |
| 高度    | 静态和动态图像 | **高度** 选项仅在 **像素** 或 **** 被选定为 **高度单位** 时才显示。 它指定图像的像素高度或百分比。                                                                                                       |

### 2.2 活动科

您可以在 **事件** 部分中选择 **点击动作**。 **点击动作** 定义用户点击图像时执行什么操作。

#### 2.2.1 共同财产

The static image and the dynamic image share the properties in the **Events** section, except for one property that is [specific for the dynamic image](#events-dynamic-image).

欲了解更多关于 **事件** 部分的静态和动态图像，请参阅 [小部件中的事件部分](page-editor-widgets-events-section)

#### 2.2.2 动态图像特定属性 {#events-dynamic-image}

动态图像有一个特定的点击操作 **放大点击**。 当用户点击时将显示全尺寸的图像。 此属性覆盖其他点击动作。

### 2.3 条件可见性部分

{{% snippet file="studo/visibility-section-link.md" %}}

### 2.4 设计部分

关于 **设计** 部分及其属性的信息，请参阅 [小部件中的设计部分](page-editor-widgets-design-section)。

## 3 个图像上传器和文件管理器属性

**图像上传器** 允许最终用户上传图像到您的应用，并生成上传图像的缩略图。 例如，用户可以为自己的个人资料上传图片。

图像上传器必须放置在数据视图或列表视图中，其中的图像实体是他们的数据源。  For more information on image entities, see the [Types of Entities](domain-models#entity-types) section in *Domain Model*.

**文件管理器** 允许最终用户上传和/或下载文件。 例如，用户可以下载带有必要数据的电子表格。

文件管理器必须放置在数据视图或列表视图中，其中包含一个文件实体作为他们的数据源。  For more information on file entities, see the [Types of Entities](domain-models#entity-types) section in *Domain Model*.

可上传/下载的文件和图像的默认最大尺寸是 5 MB。 您可以更改Studio Pro中的最大尺寸。 关于Studio Pro中属性的更多信息，见 [文件管理器](/refguide/file-manager) and [图像上传器](/refguide/image-uploader)。

所有文件扩展名都允许图像上传器和文件管理器使用，除非工作室专业版另有规定。 关于Studio Pro中属性的更多信息，见 [文件管理器](/refguide/file-manager) and [图像上传器](/refguide/image-uploader)。

### 3.1 数据源科

**数据源** 部分由 **上下文实体** 选项组成。 **Context Entity** 使用文件实体(如果您使用了一个文件管理器)或图像实体(如果您使用了一个图像上传器)，则使用周围数据视图或列表视图。 **上下文实体** 是自动设置的，是只读的。

### 3.2 一般部分

**常规** 章节属性描述如下。

#### 3.2.1 显示标签

如果您想要向最终用户显示部件的标签(名称)，请启用此属性。 *此属性默认启用。*

#### 3.2.2 标签

只有在 **启用标签** 时才显示此属性。 指定将显示给最终用户的名称。 当您选择一个属性时，属性的名称以括号显示在标签中。 这意味着该属性的值将显示给最终用户，而不是静态文本。

#### 3.2.3 编辑性 {#editability}

可编辑性表示最终用户是否能够更改部件显示的值。 可能的值如下：

* **可编辑** — — 小部件显示的值是可编辑的。

* **只读** -- 值处于只读模式。

* **条件** - 只有在基于属性值或基于表达式满足了指定条件的情况下才能编辑部件。

    {{%alert type="info" %}} If an attribute set for the widget's data source is of the AutoNumber type, the widget is set into read-only mode by default and the **Editability** setting itself is disabled, because attributes of this type are generated automatically.{{%/alert %}}

#### 3.2.4 条件基于： {#condition}

基于</strong> 属性的 **条件仅在 [条件编辑性](#editability) 被选中时才显示。 以下选项可用：</p>

* **属性** - 定义条件是否基于属性值。 在这种情况下，小部件只有在符合所选属性的某个值时才可编辑。 属性必须是布尔值或枚举类型。
* **表达式** -- 定义条件是否基于表达式。 在这种情况下，只有当表达式返回布尔值 `true` 时，小部件才能被编辑。 关于表达式的更多信息，见 [表达式](expressions)。

#### 3.2.5 属性 {#attribute}

此属性仅在表达式 [条件基于](#condition) 设置为 **属性** 时才显示。 允许您选择条件将基于的属性。 属性必须是布尔值或枚举类型。

#### 3.2.6 属性值 {#attribute-values}

此属性仅在属性为 [属性](#condition) 属性被选中时才显示。 **属性值** 允许您选择特定属性值。

例如，您只允许用户在他们的 *电子邮件验证时上传图片*。 因此，您需要在 **属性** 中选择 *电邮验证* ， *true* 在 **属性** 属性。

#### 3.2.7 表达式

此属性允许您创建表达式，并且只在表达式 [基于](#condition) 的条件设置为 **表达式** 时才显示。 表达式应该是布尔型。 关于如何创建表达式的更多信息，见 [表达式](expressions)。

### 3.3 管制科

{{% alert type="info" %}}

**Controls** 部分仅用于 **文件管理器**。

{{% /报警 %}}

**显示按钮为** 选项指定最终用户是否能够上传和/或下载文件并有以下选项：

* **上传** - 最终用户能够上传一个文件
* **下载** - 最终用户能够下载文件
* **都** - 最终用户能够上传和下载文件

### 3.4 条件可见性部分

{{% snippet file="studo/visibility-section-link.md" %}}

### 3.5 设计科

关于 **设计** 部分及其属性的信息，请参阅 [小部件中的设计部分](page-editor-widgets-design-section)。

## 4 阅读更多

* [页 次](page-editor)
* [小部件](页面编辑器部件)
