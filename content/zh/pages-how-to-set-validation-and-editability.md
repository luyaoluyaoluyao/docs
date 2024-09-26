---
title: "设置字段为只读或必填字段"
category: "页 次"
description: "描述如何在 Mendix Studio 中设置验证和可编辑性。"
menu_order: 20
tags:
  - "工作室"
  - "页面"
  - "形式"
  - "如何处理"
  - "验证"
  - "必填"
  - "只读"
  - "可编辑"
---

## 1 导言

这个如何解释您如何能够按照要求或只读的格式配置字段。

**这个教程将教你如何做以下事情：**

* 设置可编辑性以只读方式配置字段
* 设置验证所需的字段配置

如何描述下面的用例：

您有一个 HR 应用，员工可以查看和编辑有关自己的信息，例如合同细节和个人信息。 您有一个包含雇员详细信息的页面：

{{% image_container width="600" %}}
![](attachments/pages-how-to-set-validation-and-editability/employee-details-page.png)
{{% /image_container %}}

您想要在此页面上填写一些必填项 (必须填写) 和一些只读字段。

域模型在这种情况下的配置方式如下：

{{% image_container width="250" %}}
![](attachments/pages-how-to-set-validation-and-editability/domain-model.png)
{{% /image_container %}}

## 2 个前提条件

在启动此操作之前，请确保您已完成以下前提条件：

* 熟悉页面条款和如何在页面上执行基本功能。 欲了解更多信息，请参阅 [页面](/studio/page-editor)。
* 使自己熟悉输入元素的可编辑性和输入验证属性。 欲了解更多信息，请参阅 [编辑性](/studio/page-editor-widgets-input-elements#editability) and [输入验证部分](/studio/page-editor-widgets-input-elements#validation) 部分在 *输入元素*。
* 熟悉域模型条款并学习如何执行基本功能。 欲了解更多信息，请参阅 [域模型](/studio/domain-models)。

## 将字段设置为只读

您想让以下员工的详细信息只读：

* 员工号码
* 合同类型

要使一个字段只读，请执行以下操作：

1. 打开 **员工详细信息** 页面。

2. 选择 **合同类型** 字段并打开其属性。

    {{% image_container width="600" %}}![](attachments/pages-how-to-set-validation-and-editability/contract-type.png){{% /image_container %}}

3. 在 **常规** 部分中，设置 **编辑性** 属性为只读：

    ![](attachments/pages-how-to-set-validation-and-editability/editability.png)

4. 选择 **员工号码** 字段并打开其属性。

5. 在 **常规** 章节 > **编辑性**你可以看到它已经设置为只读并且不能更改这个属性。 这是因为域模型中的 **员工编号** 属性是 *autonumber* 类型 这意味着这个数字是自动生成的，无法编辑：

    ![](attachments/pages-how-to-set-validation-and-editability/autonumber-read-only.png)

现在 **员工编号** and **合同类型** 是只读字段。 他们已经灰色了，最终用户将无法编辑它们。

{{% image_container width="600" %}}![](attachments/pages-how-to-set-validation-and-editability/read-only-configured.png){{% /image_container %}}

## 需要设置字段

您想要设置以下字段作为员工的必需：

* 名称
* 地址
* 电子邮件地址
* 电话

如需设置字段，请按以下操作：

1. 打开 **员工详细信息** 页面。

2. 选择 **name** 字段并打开其属性。

3. 在 **输入验证** 部分中，将 **验证类型** 属性设置为 **所需**：

    {{% image_container width="250" %}}![](attachments/pages-how-to-set-validation-and-editability/validation-type-required.png){{% /image_container %}}

4. 当员工尝试离开此字段为空时，错误消息将显示在字段下。 在 **消息** 属性中指定此消息：

    {{% image_container width="250" %}}![](attachments/pages-how-to-set-validation-and-editability/validation-message.png){{% /image_container %}}

5. 对 **地址**重复第 2-4 步, **Email**和 **电话** 字段也可以根据需要设置它们。

干得好！ 当员工尝试退出 **name**, **地址**, **电子邮件**或者 **电话** 字段空并试图保存更改 错误消息将会显示在字段中，"必须填写此字段"：

{{% image_container width="600" %}}![](attachments/pages-how-to-set-validation-and-editability/validation-example.png){{% /image_container %}}

只有填写所有必填字段，更改才会被保存。

恭喜！ 您已将字段设置为只读字段，并包含雇员详细信息。

您现在可以预览您的应用并测试您的页面。 关于如何预览您的页面的更多信息，请参阅 [预览 & 发布您的应用程序](/studio/publishing-app)。

您也可以为您的应用添加新功能，例如，允许员工为他们的商务旅行报告附加图像。 欲了解更多信息，请参阅 [如何启用最终用户附加图像](pages-how-to-attach-images)。