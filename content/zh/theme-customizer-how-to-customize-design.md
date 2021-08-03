---
title: "自定义您的应用程序的设计"
description: "这个方法描述了如何在Mendix Studio中更改和自定义设计。"
tags:
  - "工作室"
  - "主题自定义器"
  - "如何处理"
  - "自定义大小"
  - "设计"
---

## 1 导言

这个如何解释如何在 Mendix Studio 中自定义您的应用并使用您的公司徽标，更改其颜色，字体，调整标题大小。

**这个教程将教你如何做以下事情：**

* 上传您的公司徽标
* 自定义小部件的颜色
* 自定义您的顶部栏、侧边栏和背景
* 更改字体和标题

如何描述下面的用例：

您想要自定义您的应用设计：上传公司标识，更改应用程序的颜色，更改字体，并使标题更大些。

## 2 个前提条件

在启动此操作之前，请确保您已完成以下前提条件：

* 熟悉主题定制器。 欲了解更多信息，请参阅 [主题定制器](/studio8/theme-customizer)。
* 熟悉页面条款。 欲了解更多信息，请参阅 [页面](/studio8/page-editor)。

## 正在上传您公司的徽标

要上传一个标志，请执行以下操作：

1. 点击左边菜单栏中的 painintbrush 图标打开 **主题定制器**。

2. 在 **上传徽标** 部分中，点击 **选择文件**.

    ![选择徽标文件](attachments/theme-customizer-how-to-customize-design/select-logo.png)

3. 在对话框中，请使用您的公司徽标选择图像。

4. 查看预览中上传并显示的选中图像：

    ![Logo 预览](attachments/theme-customizer-how-to-customize-design/logo-preview.png)

5. 在 **UI 定制** 部分中，使徽标更大：设置 **徽标宽度** 和 **徽标高度** 到 40 PX。

6. 在右上角，选择 **页面视图** 来检查您的徽标在页面上的外观：

    ![页面视图按钮](attachments/theme-customizer-how-to-customize-design/page-view-button.png)

干得好！ 您已上传您公司的徽标。

## 4 更改您的应用颜色

您可以在 **品牌颜色** 部分自定义您的应用颜色。 一旦您上传了标志，就会根据徽标颜色生成色板。

要自定义您的应用颜色，请执行以下操作：

1. 点击左边菜单栏中的 painintbrush 图标打开 **主题定制器**。

2. 在 **品牌颜色** 部分。 点击 **默认** 选项并在 **Logo 颜色** 中选择标记为 ** 的颜色：

    ![实现徽标颜色，默认选项](attachments/theme-customizer-how-to-customize-design/implementing-logo-colors-default.png)

3. 点击 **主** 选项并在 **Logo 颜色** 中选择标记为 ** 的颜色：

    ![实现徽标颜色，主要选项](attachments/theme-customizer-how-to-customize-design/implementing-logo-colors-primary.png)

4. 在右上角，选择 **页面视图** 查看您的更改如何应用于页面。 您更改过的颜色将应用于具有 **风格** 属性的部件，如按钮和文本。

    ![页面视图](attachments/theme-customizer-how-to-customize-design/page-view.png)

5. 在顶部栏中选择不同的页面，以确保您喜欢如何在应用的所有页面实现新颜色：

    ![选择页面](attachments/theme-customizer-how-to-customize-design/selecting-pages.png)

6. 在 **品牌颜色** 部分。 通过填充通常由设计师提供的 HEX 或 RGB 代码来选择颜色。 点击 **信息** 选项并填写十六进制颜色代码 `#B056EF`：

    ![使用颜色代码](attachments/theme-customizer-how-to-customize-design/hex-color-code.png)

7. 重复步骤5以确保颜色符合您应用中的所有页面。

8. 点击 **在右上角保存** 以实现您的更改。

您已更改了应用程序中的颜色。

## 5 自定义顶栏、侧边栏和背景

您可以通过更改顶栏、侧边栏和背景的颜色和字体来改变应用布局的外观。

执行以下操作：

1.  打开主题定制器。

2.  在 **UI 自定义** 部分 >**顶栏**, 点击 **背景** 选择颜色 *5* 在 **Logo 颜色**

3.  在右上角，选择 **页面视图** 查看您的更改如何应用于页面。 您现在可以看到顶部条是浅蓝色。

4. 点击 **边框** 设置并填写HEX颜色代码 `#989393`。 你可以看到顶部条的边框现在是灰色的。

    ![主题栏颜色](attachments/theme-customizer-how-to-customize-design/topbar-colors.png)

5.  要更改徽标大小，请执行以下操作：

    1. 点击 **徽标宽度** 设置，并将它从 30 PX 更改为 100 PX。
    2.  点击 **徽标高度** 设置，并将它从 30 PX 更改为 100 PX。

6. 要更改您的侧边栏背景深蓝色， 在 **侧边栏** 部分中点击 **背景** 填写HEX颜色代码 `#0D3A7A`

7. To change the background of your app to very light grey, click the **Defaults** setting in the **Background** section and choose fill in the HEX color code `F5F5F5`.

8. 点击 **在右上角保存** 以实现您的更改。

干得好！ 您自定义了您的顶栏、侧边栏、徽标大小和背景颜色。

## 6 更改字体和自定义标题

The **Typography** section of the **Theme Customizer** allows you to manage text elements in your app, such as page headers or text in widgets. 要更改字体和自定义标题，请执行以下操作：

1. 打开 **主题定制器**。

2. 在 **类型** 部分中，点击 **基础字体组** 然后将其更改为 **Bitt**。

3. 要使基本元素的字体(例如小部件中的文本) 更大， 更改 **基本字体大小** 从 *14* 到 *16*.

4.  你想要让所有的头都变得更大，请做以下事情：

    1. 设置 **H1 大小** 至 40。

    2. 设置 **H2 大小** 至35。

    3. 设置 **H3 大小** 至30。

    4. 设置 **H4 大小** 至 22：

        ![头部大小](attachments/theme-customizer-how-to-customize-design/header-size.png)

5. 在右上角，选择 **页面视图** 查看您的更改如何应用于页面。

6. 点击 **在右上角保存** 以实现您的更改。

恭喜！ 您已经自定义了您的应用风格。 您现在可以 [预览您的应用程序](/studio8/publishing-app) 来测试更改看起来像样的更改。  