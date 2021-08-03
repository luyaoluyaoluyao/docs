---
title: "管理员"
parent: "项目安全"
menu_order: 20
tags:
  - "studio pro"
  - "管理员"
  - "应用安全"
  - "安全"
---

## 1 导言

在 **管理员** 标签 **App Security**, 您可以更改管理员用户的默认凭据和用户角色：

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
由于密码的值是一般知识，将其更改为自定义密码是比较安全的。

此密码仅在本地运行 Mendix 时使用。 更改您模型中的密码将不会在您的云端环境中更新密码。 You can change the password for your other licensed [environments](/developerportal/deploy/environments-details) in the Developer Portal.
{{% /报警 %}}

#### 2.2.1 免费应用

当您将您的应用程序作为免费应用程序部署时，MxAdmin用户不会自动创建。 对于授权的环境，当您首次更改密码时将创建 MxAdmin 用户 例如，Mendix Cloud的 [环境详细信息](/developerportal/deploy/environments-details)。

当您的免费App *从未部署过，数据库仍然需要创建*， 您添加到您应用的任何数据快照将被还原到您免费应用的数据库。 您可以通过以下操作将MxAdmin用户添加到您的免费应用：

1. 在 Studio Pro中，转到 **App > Security**
2. **安全等级** 设置为 **Production**, 打开 **管理员** 选项卡。
3. 更改管理员用户的默认密码。
4. 本地运行您的项目。 这将创建一个包含MxAdmin用户的本地数据库。
5. 一旦您的应用在本地运行，就停止它。
6. 打开 **版本控制 > 添加数据快照**
7. 点击 **是** 确认提交新的数据快照。

您的应用现在包含一个数据快照。 如果您首次为免费应用部署此项目，快照将恢复到免费应用的数据库。 如果您的免费应用已经有一个数据库，快照将不会恢复。

或者，您可以通过以下方式作为管理员登录到部署到云端的免费应用：

1. 在 Studio Pro中，转到 **App > Security**
2. **安全等级** 设置为 **Production**, 打开 **演示用户** 选项卡。
3. 设置 **启用演示用户** 到 **是**。
4. 添加演示管理员具有 **用户角色** *管理员*
5. 点击 **发布** 将您的免费应用程序部署到云端环境。
6. 使用演示管理员登录，然后您可以创建一些用户帐户。

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

* [应用安全](项目安全)
* [用户角色](user-roles)
* [演示用户](demo-users)
* [匿名用户](anonymous-users)
* [密码策略](password-policy)
