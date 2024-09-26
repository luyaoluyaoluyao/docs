---
title: "安全性，角色 & 权限"
category: "设置"
description: "描述Mendix Studio中的安全以及角色和权限。"
menu_order: 10
tags:
  - "工作室"
  - "安全"
  - "角色和权限"
---

## 1 导言

安全是控制您应用访问权限的一种方式。 例如，您可以决定谁可以访问您的应用。

[角色和权限](#roles-and-permissions) 是安全的一个重要部分——你可以用来限制或授予对应用的不同部分的访问权限， 例如页面和微流。

## 2 有利于安全 {#enabling-security}

您的应用是否默认启用安全性，取决于应用的类型和版本。 您可以遇到以下案例：

1. 如果您的应用程序已经在 Developer Portal 中使用 Mendix 版本 7.23 创建。 或以上, 您可以启用工作室的安全性并查看和编辑 [角色和权限](#roles-and-permissions)。 关于版本的更多信息，请参阅 [Studio Ranges & Mendix 版本](general-versions)

2. 如果您的应用程序已经在开发者门户创建，版本低于7.23。 ，或被标记为私人内容，或由您的团队专门为您的公司定制， 安全状态取决于Studio Pro：<br/> a。  如果工作室专业版的安全性被关闭，您可以启用工作室的安全。 在这种情况下，当你试图 [发布应用程序](publishing-app)时，你将被提示启用安全性。 <br/>

    {{% image_container width="400" %}}![Secure Your App Pop-up Window](attachments/settings-security/security-pop-up.png)
 {{% /image_container %}}<br/>

    b. 会议文件。 如果安全设置为 **Production** level in Studio Pro 并且设置与 Studio 兼容。 您可以在工作室查看和编辑 **角色和权限** (更多关于哪些安全设置与Studio兼容的信息) 查看 [Studio 兼容性](/refguide8/studio-security-enabled#studio-compatible) 部分 *Model changes when Security is enabled in Studio*.)

    ![](attachments/settings-security/roles-and-permissions-screen.png)

    b. 会议文件。 如果安全设置为 **Prototype/demo** or **Production** level in Studio Pro and 设置不兼容 Studio 您可以在工作室查看(未编辑) **角色和权限** (更多与工作室兼容的安全设置信息) 查看 [Studio 兼容性](/refguide8/studio-security-enabled#studio-compatible) 部分 *Model changes when Security is enabled in Studio*.)

    ![](attachments/settings-security/security-read-only.png)


如果您需要启用安全性，请执行以下操作之一：

* 点击 **在上述弹出式对话框中启用安全** ，安全将自动为您设置。 之后，您可以通过 [角色和权限](#roles-and-permissions) 来限制或授予您对您应用的访问权限。

*  打开 **应用程序设置** > **角色和权限** 然后点击 **启用安全**。

    ![角色和权限屏幕](attachments/settings-security/enabling-security.png)

{{% alert type="info" %}}
当您启用安全性时，它已为整个应用启用， Studio Pro中可以看到的模型的检查和更改。 欲了解更多关于这些检查和更改的技术信息，请参阅 [Model Changes when Security is enabled in Studio](/refguide8/studio-security-enabled)。
{{% /报警 %}}

## 3 角色和权限 {#roles-and-permissions}

{{% alert type="info" %}}
在 Studio Pro，高级安全设置可以应用。 在这种情况下，您将无法编辑工作室中的角色和权限。
{{% /报警 %}}

角色是一组您可以分配给用户的权限。 例如，您可能想要给予 *管理员* 对所有页面和微流的完全访问。 对于其他用户，您可能只允许访问某些页面，并限制微流访问权限。

在通过开发者门户创建的应用程序中，有两个应用程序角色：

* 管理员
* 用户

{{% alert type="warning" %}}
当启用安全性时，这两个应用程序的角色将可以完全访问您的应用程序。 我们建议您审查用户角色的权限。
{{% /报警 %}}

欲了解更多管理应用用户的信息，请参阅 [管理应用用户](#managing-app-users) 部分。

**角色和权限** 屏幕由三个标签组成：

* 角色
* 页面访问
* 微流程访问

**角色** 标签列出了所有角色，并指出了页面数量和这些角色可以访问的微流。

**页面访问** and **微流程访问** 选项卡包含一个表格，所有页面/微流程都以行列出， 和所有角色都放在列中。

您只能允许某些角色访问页面或microflow：选择适当的框来授予角色对页面或microflow的访问权限。

要选择/取消选择所有页面或微流，请点击用户角色旁边的椭圆图标。

因此，您将获得每个角色的特定矩阵。

![页面访问选项卡示例](attachments/settings-security/page-access-tab.png)

### 3.1 创造新的作用

要创建一个新的应用程序角色，请执行以下操作：

1. 打开 **角色和权限** > the **角色** 选项卡。

2.  点击 **在右角添加角色**。

    ![](attachments/settings-security/add-role-button.png)

3.  在 **创建角色** 对话框中指定新角色的名称并点击 **创建**。

    ![创建角色对话框](attachments/settings-security/create-role-dialog.png)

新角色已创建。

### 3.2 编辑现有角色

要编辑一个现有的角色，请执行以下操作：

1.  打开 **角色和权限** > the **角色** 选项卡。

2.  点击 **更多选项** 图标并选择 **编辑**。

    ![](attachments/settings-security/edit-role-option.png)

3.  在 **编辑角色** 弹出式对话框执行更改，然后点击 **保存**。

    ![](attachments/settings-security/edit-role-dialog.png)

角色已被编辑。

### 3.3 删除角色

要删除现有的角色，请做以下工作：

1.  打开 **角色和权限** > the **角色** 选项卡。

2.  点击 **更多选项** 图标并选择 **删除**。

    ![](attachments/settings-security/delete-role-option.png)

3.  在弹出对话框中确认删除。

    ![](attachments/settings-security/delete-role-dialog.png)

角色已被删除。

{{% alert type="info" %}}

您不能删除或编辑管理员角色。

{{% /报警 %}}

### 3.4 设置访问特定页面/微流

您的应用有两种方式设置特定页面/微流访问权限：

1.  要通过 **角色和权限**设置访问权限，请执行以下操作：<br/> 1。 打开 **角色和权限** > **页面**/**微流程访问** 选项卡<br/> 1。 查找列中的用户角色，然后在页面/微流旁边的框中勾画它来打开访问权限。 或取消勾选 — — 以限制访问。 在下面的示例中，我们有限制用户访问页面的权限。<br/>

    ![](attachments/settings-security/page-access-example.png)

2.  要设置通过此页面/微流程特性访问页面/微流程，请执行以下操作： <br/> 2.1 打开页面/微流程。<br/> 2.2. 转到 **属性** > 的 **权限** 节和 tick/untick **允许角色** 授予/限制访问权限。<br/>

    ![](attachments/settings-security/permissions-section.png)

## 4 个演示用户 {#demo-users}

演示用户是在您的应用程序中存在的每个用户角色的演示。 您可以使用演示用户查看您的应用程序对每个用户角色的外观。 欲了解更多技术信息，见 [演示用户](/refguide8/demo-users)。

### 4.1 测试你的角色 {#testing-your-roles}

您可以通过以下方式测试您的应用程序对不同角色的看起来是如何的：

1. [预览您的应用程序](publishing-app)。

2. 点击屏幕右侧的用户图标：

    ![](attachments/settings-security/user-icon.png)

4. 在显示的菜单栏中，选择演示用户和应用将从相应角色的角度查看。

    ![](attachments/settings-security/select-user.png)

## 5 个管理应用程序用户 {#managing-app-users}

您可以为您的应用分配默认或自定义的用户角色给使用 Mendix 账户的最终用户。 这些被称为 **应用用户** 并且一旦授权，他们可以访问您已发布的应用来使用它，测试并提供反馈。

{{% alert type="info" %}}
您只能在发布您的应用程序后管理应用用户。
{{% /报警 %}}

若要管理应用程序用户，请打开 **角色和权限** 并点击 **在屏幕右上角管理用户**：

![](attachments/settings-security/manage-users-button.png)

您将被带到开发者门户中的 [应用用户管理](/developerportal/collaborate/general-settings#managing-app-users) 页面 在哪里您可以邀请人们加入您的应用并管理他们的用户角色。

{{% alert type="info" %}}
被邀请加入开发者门户网站的人不会自动添加为应用用户， 如有必要，您需要邀请您的团队成员。
{{% /报警 %}}

{{% alert type="info" %}}
如果您在 **角色和权限** 页面上创建了一个新的用户角色， 您需要首先发布应用程序才能在开发者门户中看到和分配此角色。
{{% /报警 %}}

## 6 自动升级到新服务 {#upgrade}

当您试图发布您的应用时，您可能会收到以下通知：需要升级保护您的应用的服务：

{{% image_container width="300" %}}
![需要升级](attachments/settings-security/upgrade.png)
{{% /image_container %}}

特殊服务可以管理您的应用用户。 当您点击 **自动升级** 时，此服务的最新版本将自动为您完成。

如果自动升级失败，这意味着服务被定制为 Studio Pro， 在这种情况下，只能手动升级Studio Pro。

如果自动升级检测到该服务是由团队成员在 Studio Pro 中自定义的 您将收到通知，应该首先在Studio Pro 进行手动升级。

## 7 阅读更多

* [安全](/refguide8/security)
* [工作室启用安全时的模型更改](/refguide8/studio-security-enabled)
