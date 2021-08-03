---
title: "菜单"
parent: "页面资源"
menu_order: 50
tags:
  - "studio pro"
  - "菜单"
  - "菜单项"
  - "页面资源"
aliases:
  - /refguide/menu-item.html
---

## 1 导言

菜单文档定义了一个可用于 [菜单小部件](menu-widgets) 的导航菜单。 通常，您的应用程序的主菜单是在设备类型中定义的，而您使用菜单文档作为辅助菜单，例如侧边栏。

菜单包含一个菜单项列表，这些菜单项可选包含子项。 根据小部件允许一些等级。

{{% alert type="info" %}}

如果启用 [security](project-security) ，菜单将只显示用户有权访问的项目。

{{% /报警 %}}

## 2 个菜单项 {#menu-item}

菜单由菜单项组成。 菜单项可以包含数字子项。 菜单栏可以深入到两个深度，导航树 - 三个级别，菜单栏不能有任何子项。

### 2.1 菜单项属性

菜单项或一个分项具有以下一般性属性：

* 标题 - 标题是显示在 [菜单小部件](menu-widgets) 中的文本。 标题是一个可翻译的文本。 (详情请参阅 [语言菜单](translatable-texts)。)
* 图标 - 您可以选择一个 glyphicon (一个在缩放时保持锐化的特殊字体中的字符)，或者在 [菜单小部件中的标题旁边或以上显示的图像](menu-widgets)。
* 替代文本 - 如果没有提供标题，您可以指定替代文本。 这将允许屏幕阅读器发布图标描述。
* 点击时 - 点击项目时要执行的操作。 有分项目的菜单项无法点击事件。

{{% alert type="info" %}}To open a page with a data view on it from a menu item, set a microflow that first retrieves an object for the data view and then opens the page as a target.{{% /alert %}}

## 3 阅读更多

* [页 次](页面)
* [菜单部件](菜单部件)

