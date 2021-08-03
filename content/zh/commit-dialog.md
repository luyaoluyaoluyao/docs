---
title: "提交"
parent: "版本控制-菜单"
menu_order: 20
tags:
  - "studio pro"
---

## 1 导言

提交对话框用于提交对团队服务器的更改。 您可以输入一条消息，如果适用，请选择相关的故事。

![版本控制菜单](attachments/version-control-menu/commit-dialog-stories.png)

## 2 分支

在对话框的顶端，您将看到您提交的分支。 这将是以下内容之一：

| 分支描述                                                          | 注          |
| ------------------------------------------------------------- | ---------- |
| ![版本控制菜单](attachments/version-control-menu/commit-main.png)   | 您正在提交主行    |
| ![版本控制菜单](attachments/version-control-menu/commit-branch.png) | 您正在提交指定的分支 |

## 3 條消息

输入描述您所做更改的消息。 此消息可能包含多行。 如果您想要使用键盘提交，您可以按 <kbd>Ctrl</kbd>+<kbd>输入</kbd>。

## 4 个提交标签

### 4.1 相关故事 {#stories}

![版本控制菜单](attachments/version-control-menu/commit-dialog-stories.png)

勾选与您的提交相关的故事旁边的方框。 我们建议每次进行少量的更改，因此通常只有一个相关的故事。

### 4.2 模式的更改

![版本控制菜单](attachments/version-control-menu/commit-dialog-model-changes.png)

如果模型中有更改，此选项卡将显示这些更改的摘要。 在 Studio Pro中如何报告更改的描述，请参阅 [Changes Pane](changes-pane)。

### 4.3 磁盘上的更改

![版本控制菜单](attachments/version-control-menu/commit-dialog-disk-changes.png)

如果磁盘上有更改，此页将显示这些更改的摘要。 点击 **打开包含文件夹** 以打开包含所选文件的 Windows Explorer 文件夹。

如果没有磁盘更改，标签页将被隐藏。 经常有模型更改，但是磁盘上唯一的更改是反映这些模型更改的应用程序文件(*.mpr*)。 在这种情况下，它也会被隐藏，因为它没有增加有用的信息。
