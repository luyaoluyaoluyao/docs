---
title: "页"
parent: "页面"
menu_order: 10
tags:
  - "studio pro"
  - "页面"
  - "属性"
---

## 1 导言

{{% alert type="info" %}}

此文档描述了您可以在页面编辑器及其模式中执行的基本功能。 关于哪些页面的详细信息以及哪些小部件可以放置在它们上，参见 [页面](pages)。

{{% /报警 %}}

页面定义Mendix 应用程序的最终用户接口。 每个页面都基于 [布局](layout)。 A page fills the "gaps" defined by a layout with widgets such as the [data view](data-view) and [data grid](data-grid).

## 2 执行基本函数

您可以在页面编辑器中执行以下基本功能：

* 打开页面
* 创建页面
* 删除页面
* 在页面上添加元素
* 查看元素属性
* 在页面上安排元素

### 2.1 打开页

要在 Studio Pro中打开一个页面, 请执行以下操作：

1. 在 [App Explorer](project-explorer)中，打开此页面所在的模块。

2. 在模块中导航到页面的位置。 一个页面可以作为单独元素列出或包含在 **页面** 文件夹中：

    ![](attachments/page/project-explorer-pages.png)

3. 选择一个您想要打开的页面并双击它。

所选页面已打开。

### 2.2 创建页

要创建一个新页面，请执行以下操作：

1.  在 [App Explorer](project-explorer)右键单击模块或您想要创建页面的文件夹，并选择 **添加页面**

    ![](attachments/page/add-page.png)


2.  在 **创建页面** 对话框，填写 **页面名称** 并选择一个 **导航布局**

    ![](attachments/page/create-page.png)

3. Click **OK**.

新页面已创建。

### 2.3 删除页

若要删除一个页面，请执行以下操作：

1. 在 [App Explorer](project-explorer)中，选择一个你想要删除的页面并右击它。
2. 在显示的列表中，点击 **删除** 并通过点击 **删除弹出对话框中的** 来确认您的选择。

所选页面已删除。

### 2.4 在页面上添加元素 {#add-elements}

您在页面上添加元素的方式取决于您正在编辑页面的模式。 关于模式的更多信息，请参阅 [页面编辑模式](#page-editor-modes) 部分。

在 **结构模式**, 有几种方式在页面上添加元素：

1.  通过 **工具箱**:

    1. 打开 **工具箱** 并选择 **小部件** 或 **建筑块** 选项卡。

        ![](attachments/page/toolbox.png)

    2. 选择一个你想要添加和拖放此元素的元素到你的页面。

2. 通过页面顶部的菜单：

    1. 做以下一件：

        一. 导言 选择经常使用的部件(数据视图，数据网格，模板网格，或列表视图)。

        ii. 点击 **添加小部件**  或 **添加建筑块**, 在列表中找到一个元素, 然后点击 **选择**。

        ![](attachments/page/top-menu.png)

    2. 点击一个页面上的投放区域来放置元素。

3. 通过右键单击下拉区：<br/>

    a. 右键点击你想要插入一个元素的下拉区域。<br/>

    b. 会议文件。 在添加小部件或构建块之间进行选择。<br/>

    {{% image_container width="400" %}}![](attachments/page/adding-widget-in-drop-zone.png)
 {{% /image_container %}}<br/>

    b. 会议文件。 点击 **选择** 来选择一个要添加和确认您选择的元素。

在 **设计模式**，您可以通过工具箱添加元素。 执行以下操作：

1. 打开 **工具箱** 并选择 **小部件** 或 **建筑块** 选项卡。
2. 选择一个你想要添加和拖放此元素的元素到你的页面。

### 2.5 视图元素属性 {#view-properties}

要查看某个元素的特性，请执行以下之一：

1. 选择一个元素并打开 **属性** 窗格以查看其属性。
2. Right-click an element and select **Properties** from the list of options that opens.
3. 双击一个元素。

### 2.6 安排页面上的元素 {#arrange-elements}

要剪切/复制/粘贴，您可以使用以下快捷方式：

* <kbd>Ctrl</kbd> + <kbd>Z</kbd> /  <kbd>Ctrl</kbd> + <kbd>C</kbd> / <kbd>Ctrl</kbd> + <kbd>V</kbd>
* <kbd>Cmd</kbd> + <kbd>Z</kbd> /  <kbd>Cmd</kbd> + <kbd>C</kbd> / <kbd>Cmd</kbd> + <kbd>V</kbd>

{{% alert type="info" %}}

如果Studio Pro 中的不同应用拥有相同的 Mendix 版本，您可以在页面上剪切/复制/粘贴元素。 然而，您不能剪切/复制/粘贴整个页面。

您不能从Studio Pro 剪切/复制/粘贴到Studio。

{{% /报警 %}}

从页面删除元素， 选择此元素并按 <kbd>删除</kbd> 或右键单击某个元素并选择 **在下拉菜单中删除**

## 3 页编辑器模式 {#page-editor-modes}

编辑您的页面有两种不同的方式：

* [结构模式](#structure-mode)，默认编辑器清楚显示页面元素之间的关系，以及关于每个元素的附加信息
* [设计模式](#design-mode), A WYSIWYG (**W**hat **Y**ou **S**ee **I**s **W**hat **Y**ou **G**et) 编辑，这些编辑更好地反映了当页面发布时它将看起来像的

您可以通过点击页面编辑器中的 **设计模式** 按钮从默认编辑器切换到 WYSIWYG 编辑器。 您可以通过点击 **结构模式** 返回到结构编辑器。

![设计模式和结构模式按钮](attachments/page/design-mode.png)

这两种模式允许您通过以下方式编辑您的页面：

* 从 **工具箱** 窗格拖动部件到页面
* 拖动小部件及其内容，从页面上的一个地方到另一个地方
* 在 **属性** 窗格中查看和编辑每个部件的属性
* 当你右键单击小部件时，从菜单中打开 **属性** 对话框

### 3.1 结构模式 {#structure-mode}

在 **结构模式**</strong> 中，页面小部件已经被放置，这样就很容易看到它们之间的逻辑关系。 它有下列在设计模式中不可用的功能：

* 您可以在页面右上角使用 **缩放** 下拉菜单缩放页面

* 小部件可以轻松看到更多的信息——例如，数据视图的数据源和分配给列的宽度

    ![常用部件](attachments/page/structure-mode-info.png)

* 每个小部件之前/上面和之后/下都有一个拖放区域——这使得当小部件在设计模式下关闭时更容易正确地放置这些小部件

* 右键单击一个拖放区域允许您将一个部件插入它

* 数据部件页面顶部有一个菜单——这些不能拖动， 但在选择小部件后通过单击拖放区域

    ![常用部件](attachments/page/frequently-used.png)

* 小部件显示时不适用于它们的样式。 但你可以看到哪些小部件通过类或样式属性应用了样式，点击 **显示样式** 按钮(仅供网页模板和布局使用)。

    ![显示样式按钮](attachments/page/show-styles.png)

### 3.2 设计模式 {#design-mode}

在 **设计模式**， 这个页面将在发布时出现，这样就很容易看到各个要素之间的空间关系。

例如，上面 [结构模式](#structure-mode)的示例页面将在 **桌面设计模式** 中看起来就像这样：

![平板电脑上显示的设计模式页面](attachments/page/design-mode-example.png)

它有以下功能在 **结构模式** 中不可用：

* 小部件将显示在页面上 — — 例如，在结构模式下垂直布局的两个文本小部件可能在应用程序发布时被水平布局， 这将会在设计模式中显示
* 页面布局可以用于不同的设备模式 — — 例如手机或浏览器，点击适当的设备模式按钮：

    ![显示样式按钮](attachments/page/design-factor.png)

* 小部件有设计属性和 CSS 类和样式应用于它们，这样你就可以看到它们看起来像样的
* 切换显示顶部栏中有条件可见的部件：

    ![显示条件可见性](attachments/page/conditional-visibility.jpg)


## 4 阅读更多

* [页 次](页面)
* [页面属性](page-properties)
