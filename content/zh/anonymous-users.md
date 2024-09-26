---
title: "匿名用户"
parent: "项目安全"
menu_order: 40
tags:
  - "studio pro"
  - "匿名用户"
  - "项目安全"
  - "安全"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/anonymous-users.pdf)。
{{% /报警 %}}

## 1 导言

您可以使用匿名用户来允许最终用户访问您的应用程序，而无需登录。 您可以通过赋予匿名用户角色来限制用户可以查看和访问的数据。

## 2 个匿名用户属性

打开 **工程安全** > **匿名用户** 选项卡访问属性：

![](attachments/anonymous-users/anonymous-users-tab.png)

匿名用户的属性见下表：

| 财产     | 描述                                                                                        |
| ------ | ----------------------------------------------------------------------------------------- |
| 允许匿名用户 | 当选择 **是** 时，允许匿名用户。 最终用户无需登录才能访问应用程序。 <br />如果选择了 **否** ，不允许匿名用户。 最终用户必须登录才能访问应用程序。 |
| 匿名用户角色 | 您的应用程序的最终用户在未登录时具有的用户角色。 这将告诉应用程序应该自动应用于访问应用程序的匿名用户。 **允许匿名用户** 属性应该设置为 **是** 来选择匿名用户角色。  |

## 3 阅读更多

* [项目安全](项目安全)
* [用户角色](user-roles)
* [管理员](管理员)
* [演示用户](demo-users)
* [密码策略](password-policy)




