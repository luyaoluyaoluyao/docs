---
title: "上传到版本控制服务器"
parent: "对话框"
aliases:
  - /refguide7/upload-team-server-dialog.html
---

## 1 导言

使用此对话框，您可以上传一个尚未存储在版本控制服务器中的应用程序。

![](attachments/upload-to-version-control-dialog/upload-to-version-control-server-dialog.png)

要打开 **上传到版本控制服务器** 对话框。 前往 **项目 > 更多版本 > 上传到版本控制服务器**。

![](attachments/upload-to-version-control-dialog/project-more-versioning-upload-to-version-control-server.png)

## 2 我们应该从哪里上传您的应用程序？

使用此设置选择您想要存储应用程序的位置。 这可以是团队服务器、私人服务器(团队服务器以外的SVN服务器)，也可以是本地磁盘。

### 2.1 新 Mendix 团队服务器

在 **应用程序名** 字段中，输入新团队服务器项目和仓库的名称。 After you click **OK**, the new repository will be created in the [Mendix Team Server](team-server) to store your app.

### 2.2 现有Mendix 团队服务器

在 **团队服务器应用程序** 列表中，选择相应的团队服务器应用。 点击 **确定**后，您的应用将被上传到所选的仓库中。

{{% alert type="info" %}}

只有当现有仓库为空时才能使用。

{{% /报警 %}}

### 2.3 私人服务器

在 **应用仓库地址** 字段中，输入你想要上传您的应用到的仓库地址。 After you click **OK**, you app will be uploaded to this repository.

{{% alert type="info" %}}

此选项仅在 [首选项](preferences-dialog#enabled) 对话框中启用对其他服务器的支持时才可用。

{{% /报警 %}}

## 3 阅读更多

* [团队服务器](团队服务器)
