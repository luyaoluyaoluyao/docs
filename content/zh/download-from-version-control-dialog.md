---
title: "从版本控制服务器对话框下载"
parent: "对话框"
aliases:
  - /refguide7/download-from-team-server-dialog.html
---

## 1 导言

使用 **从 Version Control Server** 对话框下载应用，从SVN 版本控制服务器下载应用。

![](attachments/download-from-version-control-server-dialog/download-from-version-control-server-dialog-original.png)

{{% alert type="info" %}}

您可以使用 [打开App](open-app-dialog) 对话框从团队服务器下载并打开一个应用程序。 然而，仍然存在着这种情况。 如果您想要下载您已经在磁盘上的应用程序(和开发线)的第二个副本，您将需要使用此选项。

{{% /报警 %}}

要打开 **从版本控制服务器** 对话框中下载 前往 **项目 > 更多版本 > 从版本控制服务器下载**。

## 2 您的应用存放在哪里？

使用此设置选择您应用存储的位置。 您可以在团队服务器或团队服务器以外的 SVN 服务器之间选择。

### 2.1 Mendix 团队服务器

在 **团队服务器应用程序** 下拉列表中，选择您想要打开的团队服务器应用程序。 然后选择你想要下载的 **开发行** 下拉列表

![](attachments/download-from-version-control-server-dialog/download-from-version-control-server.png)

关于Mendix Team Server的更多信息，请参阅 [Team Server](team-server)。

欲了解更多有关开发行的信息，请参阅 [版本控制概念](version-control)。

### 2.2 私人服务器

在 **应用仓库地址** 字段中 输入您想要打开的应用的仓库地址，然后点击 **Connect** 从仓库中加载开发行。 然后选择你想要在 **开发行** 下拉列表中下载的开发行。

![](attachments/download-from-version-control-server-dialog/download-from-private-server.png)

{{% alert type="info" %}}

此选项仅在 [首选项](preferences-dialog#enabled) 对话框中启用对其他服务器的支持时才可用。

{{% /报警 %}}

## 3 磁盘位置

在 **项目目录** 字段中，选择您想要存储下载应用的目录。 建议的名称包括开发线的名称(**主** 或分支线的名称)。
