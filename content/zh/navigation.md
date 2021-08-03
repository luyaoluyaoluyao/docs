---
title: "导航文档"
description: "描述Mendix Studio中的导航菜单。"
menu_order: 40
tags:
  - "工作室"
  - "navigation"
  - "菜单项"
  - "navigation item"
  - "应用菜单"
---

## 1 导言

Mendix Studio中的 **导航文档** 以树的形式显示您已配置的应用菜单。 您可以在导航中创建项目和分项。

![](attachments/navigation/navigation-vs-app.png)

要打开 **导航文档**，请点击左侧菜单栏中的相应图标。

![导航文档图标](attachments/navigation/navigation-icon.png)

**导航文档** 由允许最终用户导航您的应用程序或执行某些操作的菜单项组成。 例如，您可以配置一个菜单项来打开一个特定页面或将最终用户从他们的个人资料中登录。 关于您可以分配给菜单项的动作的更多信息，请参阅 [事件部分](#events-section-navigation)。

您也可以将一个分项目添加到菜单项中。 注意到您不能将动作分配给包含子项目的菜单项。

要创建一个新的菜单项，请执行以下操作：

1. 点击左边菜单栏中的 **导航文档** 图标打开 **导航**。

2. 点击导航树底部的加号来创建一个菜单项。 或者点击现有导航项旁边的加号来创建其分项

   ![](attachments/navigation/adding-navigation-items.png)

3. 如果需要指定创建项目的属性(详细信息，请参阅 [菜单项属性](#properties-of-menu-items))。

新菜单项或一个分项添加到导航中。

{{% alert type="info" %}}

在工作室中，您正在查看和编辑一个响应式类型的导航配置文件，而在Studio Pro中则有更多类型的配置文件。 关于Studio Pro的更多信息 在 *Navigation* 在 *Studio Pro 指南* 中查看 [配置文件](/refguide/navigation#profiles) 部分。

{{% /报警 %}}

关于如何在您的应用中配置导航的更多信息，请参阅 [如何配置导航栏](/studio-how-to/navigation-how-to-configure)。

## 2 个导航编辑器属性

在导航编辑器属性中，您可以设置 [默认主页](#default-home-page) 和 [特定主页](#role-specific-home-page)。

### 2.1 默认主页 {#default-home-page}

您可以设置一个页面或微流程为默认主页：

![默认主页](attachments/navigation/default-home-page.jpg)

**默认主页** 部分由以下属性组成：

* **页面** - 允许您设置在最终用户打开应用程序时打开的页面。
* **微流** - 允许您设置当最终用户打开应用程序时执行的微流。 微流可用于执行某些逻辑或收集应传递到主页的特定数据。

主页图标显示在页面列表或微流列表中，而主页则设置为主页：

![首页图标](attachments/navigation/home-icon.jpg)

### 2.2 特定角色主页 {#role-specific-home-page}

特定角色的主页是一个覆盖 [默认主页](#default-home-page) 的主页，并且只对具有指定角色的用户开放。 您可以为每个角色设置一个单独的主页。 关于角色和如何创建它们的更多信息，见 [安全性，角色 & 权限](settings-security)

例如，管理员角色可以将 **Admin_Dashboard** 页面作为其主页， 当其他用户打开应用程序时将打开默认主页：

![特定角色主页](attachments/navigation/role-specific-home-page.jpg)

当添加或编辑角色特定主页时，您可以设置以下属性：

* **角色** -- 定义什么角色有一个专用的主页。

* **输入** — 定义用户打开应用程序时是否打开/执行一个页面或微流程。 以下类型可用：

  * **页面** - 一个页面被设置为首页。
  * **Microflow** — 微流程被设置为主页，即当用户打开应用程序时执行微流程。 微流可用于执行某些逻辑或收集应传递到主页的特定数据。

* **页面** - 此属性仅在 **类型** 设置为 **页面** 时才可用。 允许您设置一个为选定角色打开的专用主页。

* **Microflow** - 此属性仅在 **类型** 设置为 **Microflow** 时才可用。 允许您设置一个微流程，当用户使用所选角色打开应用程序时执行。

    ![](attachments/navigation/role-specific-home-page-properties.jpg)

特定角色的主页图标显示在页面列表或微流列表中，而设置为主页的页面或微流：

![特定角色首页图标](attachments/navigation/role-specific-home-page-icon.jpg)

### 2.3 添加角色特定主页

若要添加一个专门角色的主页，请做以下操作：

1. 请确保您的 [安全](settings-security) 已经启用和配置。

2. 打开导航编辑器 > 导航编辑器属性。

3. 在 **个特定角色首页** 中，点击 **添加特定角色首页**

4. 在 **角色** 下拉菜单中，选择一个具有专用主页的角色：

    ![选择角色](attachments/navigation/selecting-role.jpg)

5. Select the **Type** of the home page: a page or a microflow.

6. 取决于选定的类型 选择一个页面或一个微流程，当所选角色的用户打开应用程序时打开或执行。

指定角色的主页已设置。

## 3 菜单项属性 {#properties-of-menu-items}

菜单项的属性由以下部分组成：

* [事件](#events-section-navigation)
* [A. 概况](#general-section-navigation)

![](attachments/navigation/navigation-properties.png)

### 3.1 活动科 {#events-section-navigation}

您可以在 **事件** 部分中选择 **点击动作**。 **点击动作** 定义了当用户点击菜单项时执行什么操作。

{{% alert type="info" %}}
如果菜单项有子项，不能为它配置动作。
{{% /报警 %}}

现有行动见下表：

| 行 动  | 描述                                                                                                                             |
| ---- | ------------------------------------------------------------------------------------------------------------------------------ |
| 无    | 没有采取任何行动。                                                                                                                      |
| 页    | 已打开指定页面。                                                                                                                       |
| 微流   | 已执行所选微流。                                                                                                                       |
| 保存更改 | 保存当前打开页面中的所有更改并关闭页面。                                                                                                           |
| 取消更改 | 回滚当前打开页面中的所有更改并关闭页面。                                                                                                           |
| 关闭页面 | 关闭弹出窗口(用于弹出页面)或导航到先前访问的页面。 请注意，如果任何更改不被保存，此操作将关闭页面和更改。 为此目的使用 **保存更改**。                                                        |
| 登出   | 当前用户已登出应用程序。                                                                                                                   |
| 打开链接 | 触发基于链接类型的动作： <ul><li>**Web** - 导航到一个网站 </li><li>**电子邮件** - 撰写电子邮件</li><li>**Phone 通话** - 开始电话</li><li>**文本消息** - 发送文本消息</li></ul>**注意** 当您配置 **Email**和 **电话通话** 或 **消息** 选项， 触发动作时将在设备上打开相应的默认应用， 例如，默认的电子邮件客户端将被打开来撰写消息。 |

{{% alert type="info" %}}

如果菜单项有一个子项， **点击动作** 应该是 **没有**。

{{% /报警 %}}

### 3.2 概述 {#general-section-navigation}

可以在 **常规** 部分中配置的属性如下：

* **标题** - 允许您填写菜单项的名称。
* **图标** - 允许您设置菜单项的图标。

## 4 阅读更多

* [如何配置导航栏](/studio-how-to/navigation-how-to-configure)
* [常规信息](general)
* [导航一致性错误](consistency-errors-navigation)
