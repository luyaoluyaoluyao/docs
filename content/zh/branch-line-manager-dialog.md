---
title: "分支行管理器"
parent: "版本控制-菜单"
menu_order: 80
tags:
  - "studio pro"
  - "管理分支行"
  - "分支行管理器"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/branch-line-manager-dialog.pdf)。
{{% /报警 %}}

## 1 导言

**分支行管理器** 用于管理 [分支行](version-control#branches) 存储在版本控制服务器上的应用程序：

![分支行管理器](attachments/version-control-menu/branch-line-manager.png)

要查看 **分支行管理器** 对话框，打开 **版本控制** > **管理分支行**。

分界线允许独立于其他发展线的发展。 创建分支线有两个主要原因：
1. 在正在生产中的应用程序版本上进行维护开发。 您可以在主行继续开发，同时修复分支行中的问题。
2. 如果您正在开始开发一个非常大的功能，开发将需要一天以上的时间。 通过在分支行中这样做，您可以在不扰乱主行中的其他发展的情况下进行半实现功能(甚至可能有错误)。

## 2 个位置

使用此设置选择您应用存储的位置。 这可以是 [团队服务器](#team-server-app) 或 [另一个 SVN 服务器](#other-svn-server-app)。

{{% alert type="warning" %}}

此选项仅在首选项对话框中启用对其他 SVN 服务器的支持时有效。

{{% /报警 %}}

### 2.1 团队服务器应用 {#team-server-app}

选择您想要管理分支行的团队服务器应用程序。 如果您在 Studio Pro 中有一个应用程序打开，它将被自动选择。 然而，您也可以管理分支行，而不需要先打开一个应用，在这种情况下不会选择任何应用程序。

关于Mendix Team Server的更多信息，请参阅 [Team Server](/developerportal/collaborate/team-server)。

### 2.2 其他 SVN 服务器应用程序 {#other-svn-server-app}

在 **SVN 仓库地址字段**， 输入您想要管理的应用程序的地址并单击 **Connect** 从资源库中加载可用分支。

## 3 管理分支行

在 **分支行管理器**，您可以创建和删除分支行，启用并禁用项目的 Mendix Studio 。 关于如何执行这些行动的更多信息 在Studio Pro</a> 部分查看
管理开发线 *Collaborative Development* </p> 



## 4 阅读更多

* [版本控制](version-control)
* [合作发展](collaborative-development)
