---
title: "保护您的应用并配置访问其功能"
description: "描述如何在 Mendix Studio 中配置安全。"
menu_order: 40
tags:
  - "工作室"
  - "安全"
  - "用户角色"
  - "保护您的应用"
  - "条件可见性"
---

## 1 导言

这个如何解释您如何能够保护您的应用，创建用户角色，并为特定用户角色打开对特定页面和微流程的访问权限。 因此，您的最终用户将只能查看他们可以访问的网页。

**这个教程将教你如何做以下事情：**

* 启用安全
* 创建用户角色
* 设置特定用户角色的访问页面
* 测试您的安全配置

如何描述下面的用例：

有一家汽车租赁公司拥有一部汽车租赁应用程序。 客户可以在那里注册，挑选一辆汽车租赁，并填写汽车租赁表； 前台代理人可获得汽车租赁表和汽车详情。 因此，有两类用户：客户和前台代理人。 您希望他们访问以下信息：

* 客户 — 他们的简况, 有关汽车的详细信息和汽车租金表
* 前台特工——关于一辆汽车和汽车租金表的详细信息

此应用的域模型看起来如下所示：

![域模型](attachments/security-how-to-configure-roles/domain-model.png)

此应用中有以下页面：

* *Home_Web* — — 一个所有角色都应该访问的主页。 主页上的按钮打开相应页面：

    ![首页](attachments/security-how-to-configure-roles/home-page.png)

* *Car_detail* — — 一个列出汽车详细信息的页面

* *Car_Rental_Form* - 租车时填写的表单

* *Personal_Profile* — — 一个客户的个人资料及其详细信息


## 2 个前提条件

在启动此操作之前，请确保您已完成以下前提条件：

* 熟悉页面条款和如何在页面上执行基本功能。 欲了解更多信息，请参阅 [页面](/studio8/page-editor)。
* 熟悉工作室中的安全、角色和权限信息。 欲了解更多信息，请参阅 [安全性，角色 & 权限](/studio8/settings-security)
* 熟悉域模型条款并学习如何执行基本功能。 欲了解更多信息，请参阅 [域模型](/studio8/domain-models)。

## 3 有利的安全

根据您的应用类型和版本，您可能需要先启用安全性。 执行以下操作：

1. 点击应用中的 **应用设置** 图标。

2. 在 **角色和权限** 屏幕中，点击 **启用安全**：

    {{% image_container width="550" %}}![Enable Security](attachments/security-how-to-configure-roles/enable-security.png){{% /image_container %}}

3. 启用安全性后，您可以看到一个带有三个标签的表格： **角色，** **页面**, **微流程**。 默认情况下创建两个角色： **管理员** 和 **用户**。 **管理员** 角色是只读的，意味着您不能删除或重命名它。 由于它已经配置并且可以访问所有功能，您将来可以为您的应用管理员使用这个角色。

    重命名 **用户** 角色 点击 **用户旁边的椭圆图标** 角色并在下拉菜单中选择 **编辑**

    ![用户角色](attachments/security-how-to-configure-roles/user-role.png)

4. 在 **编辑角色** 对话框中，将其重命名为 **客户** 并点击 **保存**。

5. 要为前台代理添加角色，请点击 **添加角色** 按钮。

6. 在 **创建角色** 对话框框中，将角色名称填写为 **Front_Desk** 然后点击 **保存**:

    {{% image_container width="450" %}}![Create Role](attachments/security-how-to-configure-roles/create-role.png){{% /image_container %}}

您现在有三个用户角色：管理员、客户和前台桌面。

![创建角色](attachments/security-how-to-configure-roles/roles-created.png)

## 4 管理角色访问

如果您看到您的用户角色表， 您将会看到默认情况下，他们可以访问您的应用中所有页面和微流。 为了限制进入某些页面，请做以下工作：

1. 点击 **页面访问** 选项卡。 您将看到一个矩阵，列出所有页面的行数和列中的所有角色。

2. 由于前台代理人不能查阅客户的个人简档， 在 **Personal_Profile** 行旁边的 **前台** 列中取消复选框：

    ![前台角色的页面访问](attachments/security-how-to-configure-roles/page-access-front-desk.png)

干得好！ 您已为您的用户角色设置了页面访问权限。

## 5 测试您的用户角色

当您限制访问某个页面或微流程时， 打开此页面或运行此微流程的小部件将自动隐藏到此角色。 例如，由于您没有允许前台代理人访问客户个人档案， 他们也不会看到打开个人资料的相应按钮。

当您设置了页面和微流访问权限后，您可以测试每个用户角色会看到什么。

您可以在预览您的应用程序时测试您设置的 [演示用户](/studio8/settings-security#demo-users) 的角色。 执行以下操作：

1. 点击 **页面** 图标退出 **角色和权限** 屏幕。

2. 点击右上角的 **预览** 按钮到 [预览您的应用](/studio8/publishing-app)

3. 当您的应用预览时，点击屏幕右侧的用户图标：

    ![演示用户图标](attachments/security-how-to-configure-roles/demo-users-icon.png)

4. 在显示的菜单栏中，选择演示用户和应用将从相应角色的角度查看。 点击 **demo_client** 测试哪些功能可以 **customer** 角色视图和访问。

    {{% image_container width="350" %}}![Select Demo User](attachments/security-how-to-configure-roles/select-user.png){{% /image_container %}}

5. 重复步骤3-4来测试 **前台桌面** 角色：

    ![测试角色](attachments/security-how-to-configure-roles/testing-roles.png)

6. 点击 **关闭右上角的预览** 来完成您的测试。

恭喜！ 您已配置了不同用户角色的访问权限。

您可以看到该按钮隐藏在 **前台桌面** 角色中，但容器不是。 您可以使用条件可见性来完全隐藏它。 欲了解更多信息，请参阅 [条件可见部分](/studio8/page-editor-widgets-visibility-section)。

当您预览您的应用时，您可以测试不同的用户角色，同时在发布后测试它。 您可以管理最终用户并将用户角色分配给他们。 欲了解更多信息，请参阅 *Security中的 [管理应用程序用户](/studio8/settings-security#managing-app-users) 部分，角色 & 权限*。

