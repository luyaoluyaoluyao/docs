---
title: "验证消息"
parent: "认证小部件"
tags:
  - "studio pro"
  - "验证消息"
  - "身份验证小部件"
  - "身份认证"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/validation-message.pdf)。
{{% /报警 %}}

●{% alert type="warning" %}}本机移动页面不支持验证信息小部件。{{% /提醒 %}}

## 1 导言

**验证消息** 小部件在页面上显示验证失败消息：

![验证消息部件](attachments/authentication-widgets/validation-message.png)

 它只在满足以下两项条件时显示给最终用户：

1.  在登录按钮的 **验证消息小部件** 属性中选择的验证消息。 欲了解更多关于此属性的信息，请参阅 *登录按钮* 中的 [验证信息小部件](sign-in-button#validation-message-widget) 部分。
2.  认证失败，即最终用户输入无效凭据。

## 2 属性

下面的图像是验证消息属性的示例：

{{% image_container width="300" %}}![验证消息属性](attachments/authentication-widgets/validation-message-properties.png)
{{% /image_container %}}

验证消息属性由以下部分组成：

* [常用的](#common)
* [设计属性](#design-properties)

### 2.1 共同部分 {#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 设计属性科 {#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

## 3 阅读更多

* [页](page)
* [登录 ID 文本框](login-id-text-box)
* [密码文本框](password-text-box)
* [登录按钮](sign-in-button)