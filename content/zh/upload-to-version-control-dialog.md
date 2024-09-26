---
title: "上传到版本控制服务器"
parent: "版本控制-菜单"
menu_order: 70
tags:
  - "studio pro"
aliases:
  - /refguide8/upload-to-team-server-dialog.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/upload-to-version-control-dialog.pdf)。
{{% /报警 %}}

## 1 导言

使用此对话框上传一个尚未存储在版本控制服务器中的应用程序。

![上传到版本控制服务器菜单选项](attachments/upload-to-version-control/upload-to-version-control-server.png)

## 2 个位置

使用此设置选择您想要存储应用程序的位置。 以下有三种选择。

### 2.1 新 Mendix 团队服务器

您可以在 [Mendix 团队服务器](/developerportal/collaborate/team-server) 上创建一个新的应用程序。

* 选择 **新Mendix 团队服务器**
* 在 **应用程序名称** 字段中输入新的团队服务器项目和资源库

    ![输入新Mendix 团队服务器的应用程序名称](attachments/upload-to-version-control/new-team-server-app.png)

### 2.2 现有Mendix 团队服务器

{{% alert type="warning" %}}
如果仓库当前为空，您只能上传到现有的存储库
{{% /报警 %}}

* 选择 **现有Mendix 团队服务器**
* 从列表中选择 **团队服务器应用程序**

    ![选择现有的mendix 团队服务器](attachments/upload-to-version-control/existing-team-server-app.png)

### 2.3 私人服务器

此选项仅在启用对其他服务器的支持时才可在 **编辑** > **首选项** > **高级** > [启用私有版本控制](preferences-dialog#enable))。

![在高级首选项中启用私密版本控制](attachments/upload-to-version-control/enable-private-version-control.png)

<a name="private-server"></a>如果您选择了 **个私人服务器**， 输入您想要上传应用程序的仓库地址到 **应用程序仓库地址** 字段。

![在高级首选项中启用私密版本控制](attachments/upload-to-version-control/private-server-app.png)

## 3 阅读更多

* [如何与前提版本控制服务器合作](/howto8/collaboration-requirements-management/on-premises-svn-howto)
