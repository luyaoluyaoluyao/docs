---
title: "认证小部件"
parent: "页面"
menu_order: 55
tags:
  - "身份认证"
  - "小部件"
  - "studio pro"
  - "登录"
  - "密碼"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/authentication-widgets.pdf)。
{{% /报警 %}}

## 1 导言

身份验证小部件用于登录用户并注销它们。

使用 [导航配置](navigation#authentication) 来将用户引导到正确的身份验证页面。

**身份验证小部件** 类别包含以下小部件：

* [登录 ID 文本框](login-id-text-box) - 允许用户提供登录ID进行身份验证

    ![登录 ID 文本框示例](attachments/authentication-widgets/logid-id-example.png)

* [密码文本框](password-text-box) - 允许用户提供验证密码

    ![密码文本框示例](attachments/authentication-widgets/password-text-box-example.png)

* [登录按钮](sign-in-button) - 将用户的登录ID和密码发送到服务器进行身份验证 ![登录按钮示例](attachments/authentication-widgets/sign-in-button-example.png)

* **登出按钮** - 签署当前已登录的用户。 退出按钮是一个按钮，点击事件设置为 **退出**。 关于点击事件的更多信息，见 [点击事件 & 事件部分](on-click-event) 关于按钮属性的详细信息。 查看 [按钮属性](button-properties)。

* [验证消息](validation-message) - 如果有任何验证失败通知用户

    ![验证消息示例](attachments/authentication-widgets/validation-message-example.png)

## 2 执行基本函数

{{% snippet file="refguide8/performancing-basic-functions-widgets.md" %}}

## 3 阅读更多

* [页](page)
* [页 次](页面)