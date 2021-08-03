---
title: "登录按钮"
parent: "认证小部件"
tags:
  - "studio pro"
  - "登录按钮"
  - "登录"
  - "身份验证小部件"
  - "身份认证"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/sign-in-button.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}The **Sign-in button** is not supported on native mobile pages.{{% /alert %}}

## 1 导言

**登录按钮** 发送用户的登录ID和密码到服务器进行身份验证：

![登录按钮](attachments/authentication-widgets/sign-in-button.png)

任何错误都会在 [验证消息小部件](#validation-message-widget) 或弹出窗口中显示。

**登录按钮** 应与 [登录ID文本框](login-id-text-box) 和 [密码文本框](password-text-box) 一起放入一个页面。

## 2 属性

下面的图像显示了登录按钮属性的示例：

{{% image_container width="250" %}}![登录按钮属性](attachments/authentication-widgets/sign-in-button-properties.png)
{{% /image_container %}}

登录按钮属性由以下部分组成：

* [常用的](#common)
* [设计属性](#design-properties)
* [A. 概况](#general)
* [可见性](#visibility)

### 2.1 共同部分 {#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 设计属性科 {#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 一般部分 {#general}

登录按钮的大多数属性与按钮部件的属性相同。 关于 **常规** 部分中按钮属性的更多信息，见 [常规部分](button-properties#general) *按钮属性*。

#### 2.3.1 验证信息部件 {#validation-message-widget}

**验证消息小部件** 是登录按钮的特定属性。 它定义了 [验证消息小部件](validation-message) ，该小部件在页面上显示验证失败消息。 如果在此属性中没有选择小部件, 认证失败消息将显示在弹出窗口中: ![验证失败](attachments/authentication-widgets/validation-failure.png)

默认： *无*

### 2.4 可见性科 {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 阅读更多

* [页](page)
* [登录 ID 文本框](login-id-text-box)
* [密码文本框](password-text-box)
* [验证消息](validation-message)