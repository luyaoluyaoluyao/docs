---
title: "分支行管理器"
parent: "版本控制-菜单"
menu_order: 80
tags:
  - "studio pro"
  - "管理分支行"
  - "分支行管理器"
---

## 1 导言

**分支行管理器** 用于管理 [分支行](version-control#branches) 存储在版本控制服务器上的应用程序。 SVN 和 Git 版本控制的对话框看起来相同，只是一些小的差异：

*  SVN对话框：

    ![SVN 分支行管理器](attachments/version-control-menu/branch-line-manager.png)

*  Git的对话框：

    ![Git 分支行管理器](attachments/version-control-menu/git-branch-line-manager.png)

要查看 **分支行管理器** 对话框，打开 **版本控制** > **管理分支行**。

分界线允许独立于其他发展线的发展。 创建分支线有两个主要原因：

* 在正在生产中的应用程序版本上进行维护开发。 您可以在主行继续开发，同时修复分支行中的问题。
* 开始开发一个非常庞大的功能，需要一天以上的时间。 通过在分支行中做到这一点，您可以在不扰乱主行中的其他发展的情况下进行半实现功能(甚至可能有错误)。

## 2 个位置

使用此设置选择您应用存储的位置。 这可以是 [团队服务器](#team-server-app) 或 [私有的 SVN 或 Git 仓库](#byo-server-app)。

{{% alert type="warning" %}}
此选项仅在 [首选项](preferences-dialog) 启用私有的 SVN 或 Git 服务器时有效。
{{% /报警 %}}

### 2.1 团队服务器应用 {#team-server-app}

选择您想要管理分支行的团队服务器应用程序。 如果您在Studio Pro中打开了一个应用程序，它将被自动选择。 然而，您也可以管理分支行，而不需要先打开一个应用，在这种情况下不会选择任何应用程序。

关于Mendix Team Server的更多信息，请参阅 [Team Server](/developerportal/collaborate/team-server)。

### 2.2 带给您自己的 (BYO) SVN 或 Git 服务器应用程序 {#byo-server-app}

在 **应用仓库地址** 字段中 输入您想要管理的应用程序的地址并单击 **Connect** 从资源库中加载可用分支。

## 3 管理分支行

在 **分支行管理器**，您可以创建和删除分支行，并启用和禁用应用程序的 Mendix Studio 。 关于如何执行这些行动的更多信息 查看 [管理工作室发展线](collaborative-development#managing-studio) 和 [管理发展线](collaborative-development#managing-branches) 部分在 *合作发展*

## 4 阅读更多

* [版本控制](version-control)
* [合作发展](collaborative-development)
