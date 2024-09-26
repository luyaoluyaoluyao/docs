---
title: "从版本控制服务器下载"
parent: "版本控制-菜单"
menu_order: 60
tags:
  - "studio pro"
aliases:
  - /refguide8/download-from-team-server-dialog.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/download-from-version-control-dialog.pdf)。
{{% /报警 %}}

## 1 导言

使用 **从版本控制服务器下载…** 菜单项从SVN 版本控制服务器下载应用 (例如) [团队服务器](/developerportal/collaborate/team-server) 如果您正在编辑应用程序， 此项目将被关闭(在提示保存任何更改后)，新下载的应用程序将使用当前版本Studio Pro打开.

{{% alert type="info" %}}
如果已下载的应用程序是用不同版本的 Mendix 创建的，您将被问及是否可以转换为当前版本。

您也可以使用 [打开应用对话框](open-app-dialog) 从团队服务器下载并打开一个应用程序。 然而，仍然存在着这种情况。 如果您想要下载您已经在磁盘上的应用程序(和开发线)的第二个副本，您将需要使用此选项。
{{% /报警 %}}

![从版本控制服务器对话框下载](attachments/version-control-menu/download-from-version-control-server.png)

## 2 您的应用存放在哪里？

如果 **启用私有版本控制** 设置于项目 [首选项](preferences-dialog#enable)您可以在 **Mendix 团队服务器** 或 **私人服务器** 之间选择。 如果未启用，您将只能从Mendix 团队服务器中选择一个应用程序。

### 2.1 Mendix 团队服务器

使用 **团队服务器应用程序** 下拉菜单选择您想要下载的应用程序。

关于Mendix Team Server的更多信息，请参阅 [Team Server](/developerportal/collaborate/team-server)。

### 2.2 私人服务器

在 **应用程序存储库地址** 中输入您私有的 SVN 服务器的 URL，并点击 **连接**。

![从版本控制服务器对话框下载](attachments/version-control-menu/download-from-private-server.png)

## 3 发展线

选择您想要下载的 **开发行**。

欲了解更多有关开发行的信息，请参阅 [版本控制](version-control)。

## 4个项目目录

选择您想要下载应用程序的 **项目目录**。 建议的名称包括开发行的名称(*主* 或分支行的名称)， 但如果你想要的话，你可以更改这个。
