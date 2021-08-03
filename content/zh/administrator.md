---
title: "管理员"
parent: "项目安全"
menu_order: 20
tags:
  - "studio pro"
  - "管理员"
  - "项目安全"
  - "安全"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/administrator.pdf)。
{{% /报警 %}}

## 1 导言

在 **管理员** **项目安全**标签中 您可以更改管理员用户的默认凭据和用户角色：

![](attachments/administrator/project-security-administrator.png)

## 2 管理员属性 {#administrator-properties}

在 **管理员** 标签中，以下属性是可用的：

* [用户名](#user-name)
* [密码](#password)
* [用户角色](#user-role)

### 2.1 用户名 {#user-name}

用户名用于以管理员身份登录应用程序。

默认： *MxAdmin*

{{% alert type="info" %}}
由于这是一般知识，更安全的做法是将其改为自定义用户名。
{{% /报警 %}}

### 2.2 密码 {#password}

密码用于以管理员身份登录应用程序。 点击 **显示密码** 查看密码。

默认： *1*

{{% alert type="info" %}}
此密码仅在本地运行 Mendix 时使用。 您可以在开发者门户中更改您的其他 [环境](/developerportal/deploy/environments-details) 密码。
{{% /报警 %}}

{{% alert type="info" %}}
由于这是一般知识，更安全地将其改为自定义密码。
{{% /报警 %}}

### 2.3 用户角色 {#user-role}

分配给管理员的用户角色。 欲了解更多信息，请参阅 [用户角色](user-roles)。

Default: *Administrator*

{{% alert type="info" %}}
系统管理员总是创建的，默认情况下具有系统管理员角色。 系统管理员角色允许您的应用程序的用户被管理。

免费应用程序， 创建应用程序的用户默认也自动具有这个角色，因此您可以在这个环境中使用它来管理您的用户。

如果您已经超过了用户许可限制，此角色可能会很有帮助，在这种情况下，您可以使用拥有此系统的任何用户。 负责登录以管理您的用户。
{{% /报警 %}}

{{% alert type="warning" %}}
当您的应用程序不是本地部署的，例如部署到Mendix Cloud， 更改管理员帐户的用户角色将在管理员密码修改后才能应用。 See the [actions](/developerportal/deploy/environments-details#actions) section of *Environment Detail* for instructions on changing the admin password.
{{% /报警 %}}

## 3 阅读更多

* [项目安全](项目安全)
* [用户角色](user-roles)
* [演示用户](demo-users)
* [匿名用户](anonymous-users)
* [密码策略](password-policy)
