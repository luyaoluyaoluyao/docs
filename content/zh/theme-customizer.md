---
title: "主题自定义器"
description: "描述Mendix Studio中的自定义主题。"
menu_order: 80
tags:
  - "工作室"
  - "主题自定义器"
  - "地图集"
---

## 1 导言

**主题定制器** 是一个帮助您在 Mendix Studio 自定义应用程序的工具。 例如，您可以调整颜色，上传一个标志，更改文本风格，从而使您的应用看起来是一致和唯一的。

![默认样式与自定义样式](attachments/theme-customizer/default-vs-customized.png)

要打开 **主题定制器**，请点击左侧菜单栏中的 paintbrush 图标。

![主题自定义图标](attachments/theme-customizer/theme-customizer-icon.png)

左边，主题定制器包含您可以更改的设置以自定义您应用的不同元素。 您所做的更改是在右侧预览的。 有两个预览模式：

* [部件视图](#widget-view) - 预览单个部件的样式

*  [页面视图](#page-view) - 预览页面的样式

    ●{% alert type="info" %}} **页面视图** 特性在贝塔。 这意味着这个功能可能会有改变。 关于测试版功能的更多信息，请参阅 [Mendix Beta 功能](/releasenotes/beta-features/)。
    {{% /报警 %}}

您可以通过点击顶部栏中的相应按钮切换模式：

![预览模式](attachments/theme-customizer/preview-modes.png)

## 2 个设置

您可以使用 **主题自定义器**左侧的不同设置更改您的应用的外观方式， 分为以下各节：

### 2.1 上传徽标

在 **上传徽标** 部分中，您可以上传一张图片作为您应用中的徽标。 您可以上传图片扩展名 png, jpg, jpeg, gif, svg. 关于如何上传标识的更多信息，请查看 [上传徽标](#uploading-logo) 部分。

一旦上传了徽标，就会根据徽标颜色生成一个调色板。 然后您可以在不同设置的颜色选择器中选择 **徽标颜色** 并使您的应用风格与您的标志样式一致：

{{% image_container width="250" %}}![徽标颜色](attachments/theme-customizer/logo-colors.png)
{{% /image_container %}}

关于如何在设置中选择新颜色的更多信息，请参阅 [调整颜色](#adjusting-colors)。

### 2.2 品牌颜色

在 **品牌颜色** 部分中，您可以定义不同样式的颜色： **默认**, **主**, **反转**, **信息**, 等等。 这些样式应用于具有 **风格** 属性的部件，如按钮。 That means, if you selected a green color for the **Success** style, buttons that have *Success* selected in the **Style** property will be green:

![](attachments/theme-customizer/brand-colors-style-dependency.png)

### 2.3 用户界面自定义

在 **UI 定制** 部分中，您可以调整主界面元素的风格和颜色：顶部栏、侧边栏和背景。

### 2.4 打字

在 **类型** 部分中，您可以覆盖您应用的文本风格和文本颜色， 例如您应用中的标题和超文本链接的颜色和大小：

{{% image_container width="250" %}}![小部件视图](attachments/theme-customizer/widget-view.png)
{{% /image_container %}}

## 3 个部件视图 {#widget-view}

**小部件视图** 预览单个小部件或界面元素的样式作为示例。 例如，当你更改 **类型**时，更改将被预览到个别标题和段落。

## 4 页视图 {#page-view}

●{% alert type="info" %}} **页面视图** 特性在贝塔。 这意味着这个功能可能会有改变。 关于测试版功能的更多信息，请参阅 [Mendix Beta 功能](/releasenotes/beta-features/)。
{{% /报警 %}}

在 **页面视图**，您可以从应用中选择任何页面来预览更改内容。 您可以从顶部栏的下拉菜单中选择一个页面。 您也可以切换设备模式以查看您的风格如何出现在 **Phone**上 **平板电脑**, 或 **响应视图**.

![顶栏](attachments/theme-customizer/top-bar.png)

## 5 执行基本操作

### 5.1 上传徽标 {#uploading-logo}

要上传一个标志，请执行以下操作：

1. 打开 **主题定制器**。

2.  在 **上传徽标** 部分中，点击 **选择文件**.

    ![上传您的徽标](attachments/theme-customizer/upload-logo.png)

3. 在对话框中，选择您想要使用的图片作为标志。

4.  所选图片已上传并显示在预览中。

5. 点击 **保存** 以保存更改。

您的应用程序的徽标已更改。

### 5.2 调整颜色 {#adjusting-colors}

您可以覆盖应用中不同元素的默认颜色。 您可以更改在下拉窗口中有颜色选择器的元素的颜色。

要更改颜色，请执行以下操作：

1. 在 **品牌颜色**, **UI 定制** 或 **类型** 部分, 选择一个您想要更改的设置。

2.  单击此设置并通过以下操作之一来选择颜色：

    1. 在调色板中选择一个颜色。
    2. 填写颜色代码。
    3. Selecting the color from **Brand Colors** and **Logo Colors** (**Logo Colors** are only available when you [upload a logo](#uploading-logo)).<br/>
{{% image_container width="200" %}}![品牌颜色和徽标颜色](attachments/theme-customizer/adjusting-color.png)
    {{% /image_container %}}

3. 在预览中查看结果。

4. 点击 **保存** 以保存您的更改。

颜色已应用到您的应用中。

## 6 阅读更多

* [Atlas界面](/howto8/front-end/atlas-ui)
