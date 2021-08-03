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

## 2 安全概述 {#overview}

您的应用是否默认启用了安全性， 取决于在Studio Pro中是否启用了安全，以及它在那里的配置方式。 您可以遇到以下案例：

1. Your app security is **off** in Studio Pro. 在这种情况下， 您可以通过 **应用程序设置**>**角色和权限** >启用 **启用安全** 按钮， 或者您将被提示启用安全性，当您尝试 [发布应用程序](publishing-app) 时。

    {{% image_container width="300" %}}![Secure Your App Pop-up Window](attachments/settings-security/security-pop-up.png) {{% /image_container %}}

    {{% alert type="info" %}}When you enable security, it is enabled for the whole app, and there are checks and changes applied to the model that are visible in Studio Pro. 欲了解更多关于这些检查和更改的技术信息，请参阅 [Model Change。当安全在工作室启用](/refguide/studio-security-enabled)。{% /提醒 %}}

2. 安全设置为 **Product** 级，设置与 Studio 兼容。 在这种情况下，您可以在工作室查看和编辑 **角色和权限**。 (更多关于哪些安全设置与Studio兼容的信息) 查看 [Studio 兼容性](/refguide/studio-security-enabled#studio-compatible) 部分 *Model changes when Security is enabled in Studio*.)

    ![](attachments/settings-security/roles-and-permissions-screen.png)

3. 安全性设置为 **Prototype/demo** or **Production** levels in Studio Pro and 设置不兼容 Studio 。 在这种情况下，您只能在工作室查看但不能编辑 **角色和权限**。 (更多与工作室兼容的安全设置信息) 查看 [Studio 兼容性](/refguide/studio-security-enabled#studio-compatible) 部分 *Model changes when Security is enabled in Studio*.)

    ![](attachments/settings-security/security-read-only.png)



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

当创建新页面/microflow/workflow 时, 工作室默认权限被设置为 这意味着应用程序中的所有现有角色都可以访问新创建的文档。

{{% alert type="warning" %}}
当页面/microflow/workflow 复制粘贴时，将为新文档设置默认权限。 我们建议您审查该文档的权限。
{{% /报警 %}}

**角色和权限** 屏幕由以下标签组成：

* 角色
* 页面访问
* 微流程访问
* 工作流访问权限

**角色** 标签列出了所有角色，并指出了页面数量和这些角色可以访问的微流。

**页面访问**,  **微流程访问**, 和 **工作流程访问** 选项卡包含一个表格，所有页面/微流程/工作流程都列在列中，所有角色都放在列中。

您只能允许某些角色访问页面、微流程或工作流程：选择授予角色访问权限的适当框。

要选择/取消选择所有页面、微流或工作流，请点击用户角色旁边的 **更多选项** (椭圆) 图标。

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

2.  点击 **更多选项** (椭圆) 图标并选择 **编辑**。

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

### 3.4 设置访问特定页面/微流程/工作流

在您的应用程序中有两种方式可以更改特定页面/微流程/工作流的访问权限：

1.  若要通过 **角色和权限**设置访问权限，请执行以下操作：
    2.  打开 **角色和权限** > **页面**/**微流程/工作流访问** 选项卡
    3.   查找列中的用户角色，并在页面/microflow/workflow 旁边的方框中勾划该角色以打开它的访问权限。 或取消勾选 — — 以限制访问。 例如，您可以限制用户角色的页面访问权限：

    ![](attachments/settings-security/page-access-example.png)

2.  要设定通过此页面/微流程/工作流程的特性访问页面/微流程，请做以下操作：
    3.  打开页面/microflow/workflow。
    4.  转到 **属性** > 的 **权限** 节和 tick/untick **允许角色** 授予/限制访问权限。

        {{% image_container width="300" %}}![](attachments/settings-security/permissions-section.png){{% /image_container %}}

## 4 个演示用户 {#demo-users}

演示用户是在您的应用程序中存在的每个用户角色的演示。 您可以使用演示用户查看您的应用程序对每个用户角色的外观。 欲了解更多技术信息，见 [演示用户](/refguide/demo-users)。

### 4.1 测试你的角色 {#testing-your-roles}

您可以通过以下方式测试您的应用程序对不同角色的看起来是如何的：

1. [预览您的应用程序](publishing-app)。

2. 点击屏幕右侧的用户图标：

    {{% image_container width="400" %}}![](attachments/settings-security/user-icon.png){{% /image_container %}}

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

特殊服务可以管理您的应用用户。 到2020年4月1日，我们正在以改进的服务取代目前的服务。 当您点击 **自动升级** 时，此升级将自动完成。

无需担心如果您没有自动升级，您的应用将仍然安全并运行， 然而，在升级之前，您将无法发布您的应用的最新版本。

如果自动升级失败，这意味着服务被定制为 Studio Pro， 在这种情况下，只能手动升级Studio Pro。

如果自动升级检测到该服务是由团队成员在 Studio Pro 中自定义的 您将收到通知，应该首先在Studio Pro 进行手动升级。 关于如何升级Studio Pro服务的更多技术信息，见 [从 AppCloudServices 升级到 Mendix SSO](/developerportal/deploy/upgrading-to-mendix-sso-from-acs)。

## 7 阅读更多

* [安全](/refguide/security)
* [工作室启用安全时的模型更改](/refguide/studio-security-enabled)
