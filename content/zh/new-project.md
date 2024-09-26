---
title: "新建项目"
parent: "文件菜单"
menu_order: 10
description: "此文档描述了新项目 (新应用程序) 流和应用设置对话框。"
tags:
  - "studio pro"
  - "创建应用"
  - "新应用"
  - "新项目"
  - "创建新应用"
aliases:
  - /refguide8/app-settings-dialog.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/new-project.pdf)。
{{% /报警 %}}

## 1 导言

您可以在 Mendix Studio Pro中创建一个新项目。

要创建一个新项目，请遵循以下步骤：

1. 做以下一件：
   1. 在顶部栏中打开 **文件** 菜单 > **新项目**.
   2. 在Studio Pro 登陆页面点击 **新应用**

2. 在 **我的应用程序** 标签中，选择一个起点--一个应用模板。

3.  点击 **使用此应用程序**。
4. 在 **应用程序设置** 对话框中，选择您项目的设置并点击 **创建应用程序**。 欲了解更多关于应用设置的信息，请参阅 [应用设置](#app-settings) 部分。

新项目已创建并开启。

## 2 款应用设置 {#app-settings}

创建新应用时， **应用设置** 对话框将打开，您可以在那里指定一个应用名称 是否启用Mendix Platform 提供的在线服务， 默认语言和存储您应用的项目文件的磁盘位置：

![应用设置](attachments/file-menu/app-settings-dialog.png)

### 2.1 名称

您的新应用的名称。 此名称用作磁盘上项目目录和文件的名称。 如果您启用此应用的在线服务， 该名称也用于团队服务器仓库和 **我的应用程序** 中的相应应用程序。

### 2.2 启用在线服务

Mendix Platform 提供在线服务，如 [版本控制](version-control), [云端部署](/developerportal/deploy/), 以及 [协作](collaborative-development)。 启用时，这将在开发者门户网站和相应版本控制库中创建一个项目。

如果您选择 *否*，您将创建一个只存储在您本地磁盘上的应用程序。 稍后您仍然可以决定将此本地应用上传到版本控制服务器，并享受版本控制带来的好处。

### 2.3 默认语言

默认语言是您项目的用户界面的语言。 选择您最初在表单和其他用户界面元素中使用的语言。 您随时可以在以后添加额外的语言到您的项目。

### 2.4 项目目录

指定您应用的文件存储的项目目录。 如果您为新应用启用在线服务， 你会看到后缀 *-main* 将自动附加到目录名称。 这是为了表明目录包含您项目的主要分支行。 在你的应用上工作时，你可以创建新分支并将它们下载到其他目录。 关于分支行管理的更多信息，见 [分支行管理器](branch-line-manager-dialog)。

## 3 阅读更多

* [版本控制](version-control)
* [打开项目](open-app-dialog)