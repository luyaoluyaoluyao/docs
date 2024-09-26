---
title: "导入工程包"
parent: "文件菜单"
menu_order: 40
description: "描述导入项目包进程和导入项目包对话框。"
tags:
  - "studio pro"
  - "导入项目包"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/import-project-package-dialog.pdf)。
{{% /报警 %}}

## 1 导言

要从 Mendix 项目包 (*.mpk*) 创建一个新应用，您需要导入一个项目包。 新应用可以存储在版本控制服务器上，也可以存储在本地磁盘上。

要导入一个项目包，请执行以下操作：

1. 选择顶部栏中的 **文件** 菜单 > **导入项目包**

2. 浏览到您想要导入的 *.mpk* 文件。

3.  在 **导入工程包** 对话框中选择相关的选项并点击 **确定**。 关于您可以选择哪些选项的更多信息，请参阅下面的章节。

    ![导入工程包对话窗口](attachments/file-menu/import-project-package.png)

项目包可以使用 [导出项目包](export-project-package-dialog) 创建。

## 2 我们应该在哪里保存您的应用？

使用此设置选择您想要存储应用程序的位置。 这可以是 [团队服务器](#team-server)， a [私人服务器](#private-server) (团队服务器以外的SVN 服务器)，或 [本地磁盘](#local)。

### 2.1 Mendix 团队服务器 {#team-server}

当将应用程序上传到团队服务器时，您可以选择创建一个新的仓库，或者上传到一个现有的仓库中。

#### 2.1.1 新 Mendix 团队服务器

如果您选择将您的应用存储在新的 Mendix 团队服务器中，将创建一个新的团队服务器项目。 您需要在 **应用程序名称** 字段中输入新团队服务器项目和资源库的名称。

#### 2.1.2 现有Mendix 团队服务器

如果您想要使用现有的仓库，请在 **团队服务器应用程序** 选项中选择应用程序。 请注意，只有当现有的资源库为空时，这才会起作用。

关于Mendix Team Server的更多信息，请参阅 [Team Server](/developerportal/collaborate/team-server)。

### 2.2 私人服务器 {#private-server}

{{% alert type="info" %}}

**私人服务器** 选项仅在启用对其他 SVN 服务器的支持时可用： **编辑** >**首选项** > **高级** > **启用私人版本控制**。

{{% /报警 %}}

在 **应用仓库地址** 字段中，输入您想要上传您的应用到的仓库地址。

### 2.3 本地磁盘上 {#local}

如果您不需要上传新应用到版本控制服务器，请选择此选项。 在这种情况下，它只会被存储在运行Studio Pro的计算机的本地磁盘上。

## 3 项目目录

使用此字段选择要存储应用程序项目文件的目录。 如果启用了版本控制， 建议的名称以 *-main* 结尾，以表明这将是应用程序的主要开发线。

## 4 阅读更多

* [团队服务器](/developerportal/collaborate/team-server)
* [导出工程包](export-project-package-dialog)