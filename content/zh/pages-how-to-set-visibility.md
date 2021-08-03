---
title: "仅在某些条件达到时显示字段"
category: "页 次"
description: "描述如何在 Mendix Studio 中设置条件可见性。"
menu_order: 30
tags:
  - "工作室"
  - "页面"
  - "如何处理"
  - "可见性"
  - "可见"
---

## 1 导言

这个如何解释您只在满足某些条件时才向最终用户显示字段，这可以通过设置条件可见性来实现。

**这个教程将教你如何做以下事情：**

* 仅当最终用户选择特定属性值时才显示字段
* 只对某个用户角色显示字段
* 查看字段仅在特定条件下可见

如何描述下面的用例：

您有一个网上商店，您只想在客户取消对 **帐单地址与送货地址** 选项相同时显示一个带有帐单地址的字段 (默认选中):

![账单地址与交货地址相同](attachments/pages-how-to-set-visibility/billing-address-same.png)

您还有一个叫做 **产品概述** 的页面列出了产品，您想要在列表中显示 **编辑** 按钮，只有管理员和销售管理员才能看到：

{{% image_container width="450" %}}

![产品列表](attachments/pages-how-to-set-visibility/list-of-products.png)

{{% /image_container %}}

域模型看起来如下方式：

{{% image_container width="550" %}}

![域模型](attachments/pages-how-to-set-visibility/domain-model.png)

{{% /image_container %}}

您有以下用户角色：

![用户角色](attachments/pages-how-to-set-visibility/user-roles.png)

关于如何启用安全和配置用户角色的更多信息。 查看 [如何保护您的应用并配置访问其功能](security-how-to-configure-roles)。

## 2 个前提条件

在启动此操作之前，请确保您已完成以下前提条件：

* 熟悉页面条款和如何在页面上执行基本功能。 欲了解更多信息，请参阅 [页面](/studio8/page-editor)。
* 熟悉自己有条件可见度。 欲了解更多信息，请参阅 [条件可见部分](/studio8/page-editor-widgets-visibility-section)。
* 启用安全性并将用户角色添加到您的应用中。 欲了解更多信息，请参阅 [如何保护您的应用并配置访问其功能](security-how-to-configure-roles)。
* 熟悉域模型条款并学习如何执行基本功能。 欲了解更多信息，请参阅 [域模型](/studio8/domain-models)。

## 3 设置账单地址条件

*条件可见性* 是一组属性，允许您只在满足某些条件时才显示小部件。

帐单地址的可见度取决于客户是否检查帐单地址是否不同于交货地址。 在您的域模型中，您有一个布尔型的属性，名为 **BillingAddressame**， 所以当它被设置为 *false*时，账单地址应该是可见的。 这意味着账单地址的可见性取决于 **BillingAddressame** 属性的值。 这样条件可见性为 *属性基于*。

{{% alert type="info" %}}

基于属性的条件可见性只能为数据容器内的部件设置(数据视图，列表视图或数据网格)。

{{% /报警 %}}

要设置 **计费地址** 字段的条件可见性，请做以下操作：

1. 打开客户指定详细信息的页面：

    ![客户详细信息](attachments/pages-how-to-set-visibility/customer-page.png)

2. 选择 **计费地址** 字段并转到其属性。

3. 在 **条件可见性** 部分中，点击 **属性** 属性：

    {{% image_container width="250" %}}![Conditional Visibility Section](attachments/pages-how-to-set-visibility/conditional-visibility-section.png){{% /image_container %}}

4. 在 **选择属性** 对话框中，选择 **BillingAddressame** 属性，然后点击 **选择**。

5. **属性值** 属性现在显示在属性中。 撤销 *True* 值，因为它不符合您想要设置的条件。 并退出 **错误** 选中的值：

    {{% image_container width="250" %}}![Attribute-Based Visibility](attachments/pages-how-to-set-visibility/attribute-based-visibility-set.png){{% /image_container %}}

干得好！ 如果您 [预览您的应用程序](/studio8/publishing-app)， 您将会看到只有当您取消  **账单地址与送货地址相同** 选项时才显示账单地址。

## 仅向某些用户角色显示元素

 您有一个 **编辑** 按钮的产品列表。 您的应用程序中有三个用户角色： **管理员**, **Sales_Managers**, 和 **客户**, 您只想向管理员和销售管理员显示此按钮，将其隐藏在客户端。 关于如何创建用户角色的更多信息，请参阅 [如何保护您的应用并配置访问其功能](security-how-to-configure-roles)。

要将元素仅显示给某个用户角色，请执行以下操作：

1. 打开产品列表的 **产品概述** 页面并选择 **编辑** 按钮：

    {{% image_container width="450" %}}![List of Products](attachments/pages-how-to-set-visibility/list-of-products.png){{% /image_container %}}

2. 打开其属性并且在 **条件可见性** 部分切换基于 **角色的** 属性：

    {{% image_container width="250" %}}![Role-Based Property](attachments/pages-how-to-set-visibility/role-based-property.png){{% /image_container %}}

3. 您应用中可用角色列表显示在 **角色** 属性中。 撤销 **客户** 角色：

    {{% image_container width="250" %}}![Unselected Roles](attachments/pages-how-to-set-visibility/unselected-roles.png){{% /image_container %}}

干得好！ 现在 **编辑** 按钮将只显示给 **管理员** 和 **Sales_Manager** 用户角色。

## 有条件可见性的 3 视野字段

要轻松地找到您页面上的哪些元素有条件可见性，您可以高亮显示它们。 要显示有条件可见性的小部件，请执行以下操作：

1. 打开页面。

2. 点击页面左上角的眼睛图标：

    {{% image_container width="250" %}}![Eye Icon](attachments/pages-how-to-set-visibility/eye-icon.png){{% /image_container %}}

有条件可见性的部件突出显示：

![突出显示小部件](attachments/pages-how-to-set-visibility/highlighted-widget.png)

恭喜！ 您为您的小部件设置了几个条件，您学会了如何在页面上查看这些小部件以便于找到它们。

您现在可以预览您的应用并测试您设置的条件：当账单地址显示时，以及哪些用户角色可以查看 **编辑** 按钮。 关于如何预览您的页面的更多信息，请参阅 [预览 & 发布您的应用程序](/studio8/publishing-app)。
