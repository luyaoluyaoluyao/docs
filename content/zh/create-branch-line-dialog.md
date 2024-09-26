---
title: "创建分支行"
parent: "分支行管理器对话框"
menu_order: 90
tags:
  - "studio pro"
  - "创建分支线"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/create-branch-line-dialog.pdf)。
{{% /报警 %}}

## 1 导言

使用 **创建分支行** 对话框来创建新的 [分支行](version-control#branches) 通过 **分支行管理器**

![](attachments/version-control-menu/create-branch-line.png)

要查看 **创建分支行** 对话框，请执行以下操作：

1. 打开 **版本控制** > **管理分支行**。
2. 在 **分支行管理器**，点击 **新**。

**创建分支行** 对话框已显示。

For more information on how to manage branch lines, see the [Managing Development Lines in Studio Pro](collaborative-development#managing-branches) section in *Collaborative Development* and [Branch Line Manager](branch-line-manager-dialog). 关于版本控制的信息，请参阅 [版本控制](version-control)。

## 2 从创建分支

**从** 创建分支，允许您选择您想要创建分支的开发线。 您可以选择以下选项之一：

* <a name="main-line"></a>**主行** - 通常你想要选择 *主行* 如果你想要开发一个独立于主行的大功能
* <a name="branch-line"></a>**分支行** - 允许您从另一个分支线创建分支线
* <a name="tagged-version"></a>**标记的版本** - 如果你正在对部署的版本进行维护，你可能想要选择一个 *标记的版本*

## 3 修订版

此设置仅在您选择 [主行](#main-line) 或 [分支行](#branch-line) 在 **从** 创建分支时有效。

选择您想要创建分支行的主要行或分支行的修订内容。 您常常想选择最新版本。

## 4 分支行

此设置只有当您在 **从** 中选择 [分支行](#branch-line) 时才可用。

选择你想要创建另一个分支行的分支行。 我们建议您只从主行创建分支线，但在某些情况下，分支线可能有用。

## 5 个标记版本

此设置仅在您选择 [标签版本](#tagged-version) **从** 创建分支时有效。

选择您想要创建分支行的标签版本。 每次创建一个部署归档标签时，您都可以随时引用项目的那个版本。

## 6 分支名称

输入新分支行的名称。

{{% alert type="warning" %}}
分支名称不能包含特殊字符 (例如， `@`, `$`, `#`).
{{% /报警 %}}

## 7 现有分支行

由于分支行名必须是唯一的，此选项显示了现有分支行数。 这样你不会意外地创建一个具有相同名称的分支线。

## 8 阅读更多

* [版本控制](version-control)
* [合作发展](collaborative-development)
