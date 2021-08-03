---
title: "配置导航栏"
description: "这个操作可以描述在 Mendix Studio 中配置导航栏的过程。"
menu_order: 15
tags:
  - "工作室"
  - "navigation"
  - "如何处理"
  - "导航栏"
---

## 1 导言

如何为您的应用配置导航栏，如创建菜单项和子项。

**这个教程将教你如何做以下事情：**

* 设置页面为主页
* 创建新的菜单栏项目和项目

如何描述下面的用例：

您想要为您的应用配置一个菜单栏。

在Studio中，导航栏是在大多数页面模板中构建的，可以作为侧边栏或顶栏在页面上使用。 已配置的菜单栏将显示以下方式：

![配置菜单](attachments/navigation-how-to-configure/navigation-previewed.png)

目前您有一个叫做 **Home_Web** 的页面被设置为默认主页，并且也被设置为主菜单项。 您的导航文档目前看起来如下方式：

![导航默认](attachments/navigation-how-to-configure/navigation-default.png)

您有好几个您想要添加到导航的页面：

* **员工** - 一个列出您公司中所有员工的页面，并且应该是默认主页

* **新员工** — — 创建一个新员工的页面

* **Job_Detail** — — 包含雇员的位置、部门和收入等详细信息的列表； 您想要将此页面与以下一个菜单项下面列出的其他两个页面保持在一起，这个菜单项叫做  **Employeee_Detail**

* **Personal_Info** — 包含一个包含个人信息的列表，如全名、紧急联系人、地址； 应该是 **Employeee_Detail** 菜单项的菜单项

* **文档** — 包含雇员档案的列表，如就业合同、医疗保险； 应该是 **Employeee_Detail** 菜单项的菜单项

## 2 个前提条件

在启动此操作之前，请确保您已完成以下前提条件：

* 熟悉页面条款和如何在页面上执行基本功能。 欲了解更多信息，请参阅 [页面](/studio/page-editor)。
* 熟悉导航文档条款。 欲了解更多信息，请参阅 [导航文档](/studio/navigation)。
* 熟悉域模型条款并学习如何执行基本功能。 欲了解更多信息，请参阅 [域模型](/studio/domain-models)。

## 3 创建菜单项和子项

### 3.1 将员工页面设置为默认主页 {#employees-page}

目前 **Home_web** 页面被设置为您的应用的主页。 然而，你想把 **员工** 页面设置为主页。 执行以下操作：

1. 点击左侧菜单栏中的 **导航文档** 图标。

2. 打开导航编辑器属性 > **默认主页**。

3. 点击 **页面** 属性来选择一个不同的页面：

    ![默认主页](attachments/navigation-how-to-configure/default-home-page.png)

4. 在 **选择页面** 对话框中，选择 **员工** 然后点击 **选择**。

5. Now you need to set the **Employees** page for the **Home** menu item otherwise it will not show in your navigation tree. 点击 **首页** 菜单项并打开其属性。

6. 点击 **页面** 属性：

    ![主菜单项](attachments/navigation-how-to-configure/home-menu-item.png)

7. 在 **选择页面** 对话框中，选择 **员工** 然后点击 **选择**。

您已设置 **员工** 页面为您的应用的新的默认首页。

### 3.2 为新员工页面创建一个菜单项

**新员工** 页面包含一个包含新员工详细信息的表单， 这意味着它包含一个需要 *员工* 对象的数据视图。 因此，在为其创建菜单项时，您需要通过此对象。

要为 **新员工** 页面创建菜单项，请做以下操作：

1. 点击导航树底部的加号来创建菜单项：

    ![添加菜单项](attachments/navigation-how-to-configure/adding-menu-item.png)

2. 打开新菜单项属性，执行以下操作：

    1.  将 **单击动作** 设置为 **页面**。

    2. 切换 **创建对象** 选项来将 *员工* 对象传递到页面。

    3. 点击 **实体** 属性来设置所需的实体。

        ![创建对象](attachments/navigation-how-to-configure/create-object.png)

    4. 在 **选择实体** 对话框中，选择 **员工** 然后点击 **选择**。

    5. 点击 **页面** 属性。

    6. 在 **选择页面** 对话框框中，选择 **新员工** 页面并点击 **选择**。

    7. 在 **标题** 属性中，删除 *导航项* 标题和类型 *新员工*.

    8. 点击 **图标** 属性来设置菜单项的图标。

    9. 在 **选择图标** 对话框中，搜索 *加* 图标并点击 **选择**

         ![选择 Plus 图标](attachments/navigation-how-to-configure/plus-icon.png)

干得好！ 您已将 **新员工** 页面的菜单项添加到您的导航中：

![创建新菜单项](attachments/navigation-how-to-configure/new-menu-item-created.png)

点击 **在右上角预览** 到 [预览您的应用程序](/studio/publishing-app) 并测试导航菜单的形式： ![预览菜单项](attachments/navigation-how-to-configure/previewed-menu-items.png)

### 3.3 为Employeee_Detail页面创建一个菜单项并配置其子项

您想要放置 **Job_Detail**, **Personal_Info**, 和 **文档** 页面在一个菜单项下，名称为 **员工详细信息**这意味着它们将被菜单项打开。

首先，您需要创建包含三个菜单子项的菜单项。 执行以下操作：

1. 点击导航树底部的加号来创建菜单项。

2. 打开新菜单项属性，执行以下操作：

    1. 在 **标题** 属性中，删除 *导航项* 标题和类型 *员工详细信息*。
    2. 点击 **图标** 属性来设置菜单项的图标。
    3. 在 **选择图标** 对话框中，搜索 *用户* 的图标并点击 **选择**。

3. Click a plus *next to* the **Employee Details** menu item to create a sub-item for it:

    ![创建菜单子项](attachments/navigation-how-to-configure/creating-menu-sub-item.png)

4. 打开其属性并执行以下操作：

    1. 将 **单击动作** 设置为 **页面**。

    2. 点击 **页面** 属性。

    3. 在 **选择页面** 对话框框中，选择 **Job_details** 页面并点击 **选择**。

    4. 在 **标题** 属性中，删除 *导航项* 标题和类型 *作业详细信息*

        ![作业细节菜单项的属性](attachments/navigation-how-to-configure/job-details-menu-item-properties.png)

    5. 重复步骤1-4来创建一个菜单分项，打开 **Personal_Info** 页面并命名此分项 *个人信息*。

    6. 重复步骤1-4来创建一个菜单分项，打开 **文档** 页并命名此分项目 *文档*

    7. 分项目的顺序如下所示： **文档**, **个人信息**, **作业详细信息**。 拖放它们以以下方式重新排列顺序： **作业详细信息**， **个人信息**, **文档**.

您配置了 **员工详细信息** 菜单项的子菜单项。

恭喜！ 您为您的应用创建和配置了导航：

![已配置导航](attachments/navigation-how-to-configure/configured-navigation.png)

[预览您的应用程序](/studio/publishing-app) 以查看导航菜单是如何显示的：

![预览导航](attachments/navigation-how-to-configure/navigation-previewed.png)

