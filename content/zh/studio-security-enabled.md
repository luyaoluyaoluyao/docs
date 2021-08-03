---
title: "工作室启用安全时的模型更改"
parent: "安全"
description: "描述在 Mendix Studio 启用安全时项目中的检查和更改。"
tags:
  - "studio pro"
  - "安全"
  - "工作室"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/studio-security-enabled.pdf)。
{{% /报警 %}}

## 1 导言

本文档描述在Mendix Studio启用安全时自动应用的模型更改过程。 关于工作室安全设置的更多信息，请在 *工作室指南*中查看 [安全性，角色 & 权限](/studio8/settings-security)

用户可以启用工作室的安全性。 工作室用户只需点击 **启用 Security** 按钮，结果就可以了。 安全设置为 **Production** 项目并自动执行一些检查和更改(如果有必要)。

## 2 流程概述

当启用安全性时，将在几个层面上进行一些检查和修改。

1. 工作室检查是否启用了安全。 如果安全设置为 **质子类型/演示** 或 **Production**, 进程就会停止。 如果安全被关闭，则执行下面所述的步骤。
2. 如果项目尚未安装 [Mendix SSO](/appstore/modules/mendix-sso) 模块 (关于此过程的更多信息) 见 [模块已设置](#module-set-up) 部分)。 如果Mendix SSO模块已经为此项目安装完毕，进程将停止。
3. 工作室检查并更改 [演示用户](demo-users) , [模块角色](module-security) , 和 [用户角色](user-roles) (关于此过程的更多信息) 请参阅 [模块角色和演示用户设置](#module-roles-and-demo-users) 部分)。
4. 工作室为实体(及其属性和协会)设置访问规则， 如果实体还没有访问规则(关于此过程的更多信息，请参阅 [实体访问设置](#entity-access) 部分)。
5. 工作室检查是否有 *登录。 tml* 文件存在、备份并替换为新版本(关于此进程的更多信息)。 查看 [文件设置](#file-set-up) 部分)。
6. 工作室在 [项目安全](project-security) 级别上检查和更改(如果有必要) (关于此过程的更多信息) 查看 [项目安全等级设置](#project-security-level) 部分)。

{{% alert type="info" %}}

如果安全已设置为 **Prototype/demo** or **Production** in Studio Pro, 这些设置可能与 Studio 角色和权限设置不兼容(太高级)。 在这种情况下，您将无法编辑工作室中的角色和权限。 关于工作室安全设置的更多信息，请在 *工作室指南*中查看 [安全性，角色 & 权限](/studio8/settings-security)

{{% /报警 %}}

## 3个模块设置 {#module-set-up}

当工作室启用安全时，将设置Mendix SSO模块。 此模块用于在您的应用程序中启用单个登录和用户管理。

为了启用单点登录，进行以下检查和更改：

1. Mendix SSO 启动微流程(MendixSSO.MendixSSO_AfterStartup) 已创建。 关于此进程可能结果的更多信息，请参阅 [项目安全等级设置](#project-security-level) 部分。
2. *login.html* 文件已选中并在必要时更改。 欲了解更多信息，请参阅 [文件设置](#file-set-up) 部分。

Mendix SSO模块也将用户管理添加到您的应用中。 通过用户管理，您可以管理应用用户。

{{% alert type="info" %}}If your project already has the Mendix SSO module installed, you will not be able to enable security from Studio. 您只能在Studio Pro 中手动设置安全性，满足以下要求：

* 安全应该设置为 **生产** <br/>
* Mendix SSO模块应设置以启用单个登录

{{% /报警 %}}

## 4个模块角色和演示用户设置 {#module-roles-and-demo-users}

在 **启动后** 微流程设置后，Studio 检查 *管理员* 角色 *用户* 角色，以及 *演示用户* 存在并在必要时创建它们：

1.  工作室检查管理员角色和用户角色是否存在于 **项目** 级。 如果它们不存在，它们将被创建。

    ![](attachments/studio-security-enabled/project-security-user-roles.png)

2.  在此之后， 工作室检查项目每个模块中是否存在管理员和用户角色，以及它们是否与相应的项目角色相联系。

    ![](attachments/studio-security-enabled/module-roles.png)

    此检查的可能结果如下：<br/> a。 如果模型在一个模块中有两个或两个以上的模块角色与管理员项目角色或用户项目角色相关联， 然后工作室将不兼容。 工作室不会改变这些角色，但角色和权限在工作室中不可编辑。<br/> b. 如果模型有一个模块角色关联到管理员项目角色或用户项目角色 工作室检查模块角色的名称是否与项目角色相同。 如果名称不同，Studio会断开此模块角色与项目角色的连接 创建一个与项目角色名称相同的新项目并将其链接到项目角色。<br/> c. 如果模型没有与管理员项目角色或用户项目角色相关联的模块角色，Studio将创建这些角色。 <br/> d. 如果模块角色存在，其名称与项目角色相同。 但它没有链接到这个项目角色，Studio创建一个新的模块角色 名称 *管理员_1* 或 *User_1*并将其链接到相应的项目角色。<br/>

    {{% alert type="info" %}}Studio links the Administrator role from the System module to the Administrator role on the project level. *从工作室创建的其他项目角色* 。 包括原始用户项目角色，将链接到系统模块的用户模块角色。
    {{% /报警 %}}

3. 演播室将管理员在项目一级的作用与MendixSSO.Administrator and Administration.Administrator (如果不存在，Studio 将不进行任何链接)。 项目一级的用户角色连接到 MendixSSO.User 和 Administration.User (如果它们存在，Studio 将不进行任何链接)。 所有其他Mendix Marketplace模块将保持不变。

    在Studio中创建的其他用户角色将被链接到MendixSSO。用户和 Administration.User MendixSSO 以及相应的管理模块。

4. 工作室检查是否存在名为 *demo_administrator* and *demo_user* 的演示用户，如果不存在，工作室是否创建他们。

{{% alert type="warning" %}}

If Administrator and User roles already exist and are [compatible with Studio](#studio-compatible), they will get access to all microflows, nanoflows, pages, and entities (including entities' attributes and associations).

所有新创建的角色都可以访问工作室中的所有页面、微流、纳夫洛和实体(包括其属性和协会)。 但市场网页、微流和实体（及其属性和协会）除外。

此外，所有新网页、微流和微流。 在工作室创建的实体(具有他们的属性和关联)将默认对所有现有的应用程序角色都可以访问。

{{% /报警 %}}

## 5个实体访问设置 {#entity-access}

当您启用安全性时，工作室为没有权限的所有实体 (及其属性和关联) 创建访问规则。 以下访问规则设置已应用：

*   描述已添加到 **文档** 一个 **访问规则** ，其中表示它是由工作室生成的

    ![](attachments/studio-security-enabled/start-up-microflow.png)

*  当前模块中的所有角色，除了匿名角色，获得 *创建* 和 *删除实体的* 权限。 为这些实体的属性和协会制定了下列规则：

  *  当前模块中的所有角色，除了匿名角色，都有 *读取* 和 *写入* 属性访问权限

     {{% alert type="info" %}}There are cases where entities inherit from System.Image or System.FileDocument. 其中一些继承属性不能设置为读/写，因此它们被设置为只读。
     {{% /报警 %}}

* 当前模块中的所有角色，但匿名角色除外。 如果关联实体是关联所有者，则有 *读取* 和 *写入* 对关联的访问

{{% alert type="info" %}}

如果您在 Studio 中创建一个实体，上述规则将被创建。

如果您复制粘贴一个实体，则将尽可能复制原始实体的访问规则。 然而，如果您对某个实体有一个概括性并且您将它复制到另一个项目，则会删除概括。

{{% /报警 %}}

## 6 个文件设置 {#file-set-up}

作为最后一个阶段，Studio在您的项目中应用 *login.html* 文件。

如果存在 *login.html* 文件，Studio 将其备份在同一个文件夹中，名为 *login_backup_year-month-Day_hour-minute。 tml*, 表示备份的日期和时间。 Studio还创建了一个名为 *login.html的新文件*

如果 *login.html* 文件不存在，Studio将其创建于 *login.html*

此程序允许单个登录，并允许现有用户使用Mendix账户自动登录您的应用程序。

## 7 项目安全等级已设置 {#project-security-level}

在 **项目** 级上，Studio 做以下工作：

1. **项目安全** 已设置为 **Production**。

2.  工作室检查 **启动后** 微流程是否存在于 **项目** > **设置** > **运行时间**。

    ![](attachments/studio-security-enabled/start-up-microflow.png)

    此检查可能有两个结果：<br/> a。 如果模型不包含任何 **在启动** microflow后， *MendixSSO.MendixSSO_AfterStartup* microflow 被使用。<br/> b. 如果模型包含 **在启动** 微流程后，Studio 创建 *CallBothStartupMicroflow* 微流程与现有的微流程。 *CallBothStartupMicroflow* 将先调用 *MendixSSO.MendixSSO_AfterStartup* microflow，然后它将调用项目中已存在的microflow。

## 工作室兼容性 {#studio-compatible}

Studio Pro 安全设置与 Studio 兼容(这意味着角色和权限可以在Studio中编辑) 当符合以下所有标准时：

* Mendix SSO 模块已安装
* 安全等级已设置为生产
* 演示用户已启用
* 演示用户必须有正确的名字：与项目角色名称相同，但使用 *demo_* 前缀 (例如，demo_user)
* 演示用户必须只有一个用户角色连接到他们上
* 用户角色必须有一个演示用户连接
* 用户角色必须只有一个模块角色，每个模块连接到他们(Studio不检查系统或市场模块)
* 模块角色中没有多个用户角色被连接

## 9 阅读更多

* [安全性，角色 & 权限](/studio8/settings-security)
* [项目安全](项目安全)
* [模块安全](module-security)
