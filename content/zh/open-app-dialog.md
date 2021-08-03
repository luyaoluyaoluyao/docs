---
title: "打开项目"
parent: "文件菜单"
menu_order: 20
description: "描述打开项目 (应用程序) 流和打开应用程序对话框"
tags:
  - "studio pro"
  - "打开应用"
  - "打开工程"
aliases:
  - /refguide8/open-project-dialog.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/open-app-dialog.pdf)。
{{% /报警 %}}

## 1 导言

要在 Mendix Studio Pro中打开一个项目，请执行以下操作之一：

* 在顶部栏中打开 **文件** 菜单 > **打开项目**
*  点击 **在 Studio Pro 登陆页面上打开**

**打开应用程序** 对话框将打开，您可以在那里选择应用位置：

![打开应用程序](attachments/file-menu/open-app.png)

欲了解更多关于应用位置的信息，请查看 [您的应用商店在哪里？](#location) 部分

应用可以位于团队服务器、另一个SVN服务器或本地磁盘上。 当从团队服务器或另一个SVN服务器打开应用时，Studio Pro 将检查您是否已经下载过此应用程序。 如果是这样，它将只是打开它。 如果没有，应用程序将先从版本控制服务器下载。

## 2 您的应用存放在哪里？ {#location}

使用此设置选择您应用存储的位置。 这可以是 [团队服务器](#team-server), [私人服务器](#private-server), 这是团队服务器以外的 SVN 服务器，或是一个 [本地磁盘](#local)。 磁盘上的应用也可以存储在团队服务器或另一个SVN服务器中。 在这种情况下，使用 **团队服务器**/**私人服务器** 选项和 **本地磁盘上** 选项打开它没有区别。

### 2.1 Mendix 团队服务器 {#team-server}

选择您想要打开的团队服务器应用，然后选择开发线。

关于Mendix Team Server的更多信息，请参阅 [Team Server](/developerportal/collaborate/team-server)。

欲了解更多有关开发行的信息，请参阅 [版本控制](version-control)。

### 2.2 私人服务器 {#private-server}

{{% alert type="info" %}}

**私人服务器** 选项仅在启用对其他 SVN 服务器的支持时可用： **编辑** >**首选项** > **高级** > **启用私人版本控制**。

{{% /报警 %}}

在 **应用仓库地址** 字段中 输入您想要打开的应用程序的地址，然后按 **Connect** 按钮从资源库中加载开发行。 然后选择你想要开始开发的开发线。

### 2.3 本地磁盘上 {#local}

要打开您已经在磁盘上的应用，只需指向项目文件。

## 3 阅读更多

* [导入工程包](import-project-package-dialog)