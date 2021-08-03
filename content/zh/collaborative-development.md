---
title: "合作发展"
category: "版本控制"
description: "描述Mendix Studio Pro 和 Mendix Studio 之间的协作开发过程"
tags:
  - "studio pro"
  - "工作室"
  - "合作发展"
  - "同步"
---

## 1 导言

协作开发是一个由多人组成的团队在应用上工作时共享应用模式变化的过程。 协作开发使团队成员能够在Mendix Studio Pro 和 Mendix Studio 的一个应用程序上合作。 并且使用 [版本控制](version-control) 来轻松同步更改。 Studio Pro 可以用于应用的不同分支，而Studio 可以用于这些分支之一。

{{% alert type="info" %}}
如果您在工作室打开您的应用程序时还没有启用 **Mendix Studio。** 消息将在工作室中启用。 请确保您启用了一条开发线。 欲了解更多信息，见 [正在为开发线启用 Studio](#active-branch)。
{{% /报警 %}}

## 2 协作发展概览

Studio Pro 用户可以通过 [版本控制](version-control) 通过 **提交** 和 **更新** 操作进行合作。

Studio Pro 和 Studio 之间的合作发展进程包括以下步骤：

1. 工作室中的每一个更改都自动保存到工作室的副本中。 多个用户可以同时在工作室查看应用程序：一个用户可以编辑它，其他用户则处于只读模式。
2.  Studio Pro 用户打开应用程序时，如果此开发线启用Studio ，他们会收到通知。

    ![协作开发启用通知](attachments/collaborative-development/collaborative-development-enabled-notification.png)

3. Studio Pro 创建本地工作副本，Studio Pro 用户可以使用。
4. 要从团队服务器获取更改，用户需要点击 **更新**。 当Studio Pro 用户点击 **更新**来自 *Studio* 的最新更改在Studio Pro 收到更新之前自动提交给团队服务器。 来自团队服务器的最新版本包含最新的 *Studio* 更改已合并到 Studio Pro的本地工作副本。
5.  Studio Pro 用户在应用程序上工作，一旦用户完成某些功能(例如) 修复错误或创建一个新功能)，他们点击 **提交**。 用户输入提交消息并予以确认。 这会触发一个与更新过程相同的过程(步骤4所述)。 Studio Pro 工作版更新团队服务器的最新版本。<br/>

    这种合并有两种可能的结果：<br/>

    a.   没有冲突，Studio Pro 用户更改将致力于团队服务器。 工作室随后从团队服务器获取最新版本并解锁；工作室专业版用户更改对工作室用户可见。 其他Studio Pro 用户在更新后将得到更改。 <br/> b. 有冲突，Studio Pro 提交进程已停止。 工作室已解锁，但未从 Studio Pro 用户处获取更改。 Studio Pro 用户需要先解决合并冲突，然后才能再次提交。<br/>

{{% alert type="info" %}}
当Studio Pro 用户想要将应用程序部署到云端时，他们点击 **发布** 按钮。 在这个过程中自动完成提交，步骤五已执行。
{{% /报警 %}}

## 3 工作室视图

关于从工作室角度合作开发的信息，见 [Studio 合作开发](/studio/collaborative-development)。

## 4 Studio Pro Perspective

当您连接到已开启协作开发的应用程序时， 您看到哪些开发线(主行或分支线)Studio已启用。

点击下拉菜单选择另一行或点击 **确定** 打开当前选中的行。

![打开应用对话框窗口](attachments/collaborative-development/open-app-dialog.png)

### 4.1 合并最新更改

合并团队服务器中存储的最新更改(来自Studio用户和其他Studio Pro 用户)， 打开 **更改** 并点击 **更新**。

![更新选项](attachments/collaborative-development/update-button.png)

### 4.2 作出最新更改

若要提交您最新的应用更改并将其提供给其他用户，请打开 **更改** 并点击 **提交**。 部署您的应用程序的过程(当您点击 **发布** 按钮时)也会触发提交。

{{% alert type="info" %}}
我们建议您更新您的应用并经常提交更改，以避免在您的应用中发生多次冲突。
{{% /报警 %}}

如果您的应用有冲突，Studio将被解锁，无需收到您的更改。 您需要先解决Studio Pro 中的冲突，才能完成合并并再次提交。

如果没有冲突，您的更改将自动发送到Studio。 关于工作室合作开发进程的更多信息，见 [Studio 合作开发](/studio/collaborative-development)。

### 4.3 查看承诺历史

您可以通过 **版本控制** > **历史记录** 看到对当前开发行的所有修改：

![历史对话框](attachments/history-dialog/history-dialog.png)

## 5 发展线上的管理工作室 {#managing-studio}

在 Studio Pro，您可以启用或禁用开发行(主行或分支行)。 为了协作开发，您需要启用工作室为开发行之一(仅适用于团队服务器应用)。

### 5.1 为开发线启用工作室 {#active-branch}

若要在Studio 和 Studio Pro之间共享您的模型更改，您需要启用Studio 作为开发线之一。

Studio是否默认启用开发线取决于您的应用：

* 在以下情况下默认启用主线工作室：
    * 通过开发者门户创建的新应用
    * 对于已启用Studio的现有应用
* 在以下情况下，工作室没有为任何开发线启用：
    * 用于通过Studio Pro 创建的新应用
    * 对于没有启用工作室的现有应用

若要启用Studio开发线或切换到另一条开发线，请执行以下操作：

1.  点击 **版本控制** > **管理分支行**. 在 **分支行管理器** 对话框中 您可以看到工作室启用的开发行(如果有的话)在第一列中用地球图标标记。

    ![分支行管理器中的球形图标](attachments/collaborative-development/globe-icon.png)

2.  选择您想要启用工作室的行，并点击 **为工作室启用**。

    ![分支行管理器 - 启用另一分支](attachments/collaborative-development/enable-another-branch.png)

工作室的开发线已被选中。

当您切换工作室到另一条开发线时，工作室在此过程中会被锁定几分钟。 一个弹出式对话框向用户显示Studio Pro 用户正在更改Studio 的行号。 来自Studio的所有更改都致力于当前的发展线，并且只是在该线改变之后。

### 5.2 为开发线禁用工作室

如果工作室为开发行启用，您可以禁用它。

{{% alert type="info" %}}
如果您禁用了开发行的Studio，它已被启用，不要为任何其他开发行启用它。 您将无法使用协作开发。
{{% /报警 %}}

要禁用工作室，请执行以下操作：

1. 选择为Studio启用的分支。
2.  点击 **为 Mendix Studio** 按钮：

    ![Mendix Studio禁用](attachments/collaborative-development/disable-for-studio.png)

工作室已禁用您的应用。

## 6 管理发展线 {#managing-branches}

您可以创建和删除分支行。

### 6.1 创建新分支线

要创建一个新的分支，请执行以下操作：

1. 点击 **版本控制** > **管理分支行**.
2.  在 **分支行管理器** 对话框中，您看到了现有开发行的列表。 点击 **新的** 来创建一个分支线。 <br/>

    ![创建新分支](attachments/collaborative-development/creating-new-branch.png)<br/>

3.  在 **创建分支行** 对话框中，设置以下内容： <br/>

    a. 您正在创建一条新行：主行、分支行或标签版本。 欲了解更多关于这些概念的信息，请参阅 *版本控制* 中的 [概念](version-control#concepts) 部分。 <br/> b. 如果需要，选择 **版本**。 <br/> c. 输入新行的名称。<br/>

    *  这是SVN的对话框：

        ![创建 SVN 分支行对话框](attachments/collaborative-development/create-branch-dialog.png)

    *  这是 [Git](create-branch-line-git-dialog) 的对话框：

        ![创建 Git 分支行对话框](attachments/collaborative-development/create-git-branch-dialog.png)

4.  在您配置了所有设置后，点击 **确定**。

您已经创建了一个新的分支线。

### 6.2 删除分支线

若要删除分支，请执行以下操作：

1. 点击 **版本控制** > **管理分支行**.
2.  在 **分支行管理器** 对话框中，选择您想删除的分支，单击 **删除** 并确认删除。

    ![删除分支](attachments/collaborative-development/deleting-branch.png)

您已删除此分支。

{{% alert type="info" %}}
您不能删除启用的工作室分支。 如果您需要删除此分支，请启用工作室作为另一行，然后删除分支。
{{% /报警 %}}

## 7 阅读更多

* [版本控制](version-control)
* [D. 排除合作发展问题](collaborative-development-troubleshooting)
* [合作开发工作室](/studio/collaborative-development)
