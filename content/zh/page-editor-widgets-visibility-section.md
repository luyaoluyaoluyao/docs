---
title: "条件可见性部分"
parent: "页面编辑器部件"
description: "描述Mendix Studio小部件属性中的条件可见性部分。"
menu_order: 30
tags:
  - "工作室"
  - "页面编辑器"
  - "小部件"
  - "点击动作"
  - "事件"
---

## 1 导言

小部件属性中的 **条件可见性** 部分只允许您在满足某些条件时显示小部件。 您可以根据以下条件显示部件：

* [基于数据的可视性](#based-on-data)
* [基于角色的可见性](#role-based)

例如， 您有一个网上商店，您不想在交货地址匹配账单地址时两次填写同一个地址。 只有当用户取消对 **账单地址与送货地址** 选项相同时，您才想显示字段来填写账单地址。 在这种情况下，您可以根据 *属性值*显示账单地址字段: 只有当 *BillingAddressame* 取消了勾选时才显示字段 *false*

![可见性示例](attachments/page-editor-widgets-visibility-section/attribute-based-example.png)

您也可以只显示一个小部件到一个 *用户角色*。 例如，您可以显示一个只显示财务经理的工资金额的小部件。

查看已配置条件可见性的部件， 点击眼睛图标是页面左上角的 **显示** 选项： ![显示选项](attachments/page-editor-widgets-visibility-section/highlight-conditional-items.png)

## 2 条件可见性属性

您可以根据 [动态数据](#based-on-data) 和/或 [用户角色](#role-based) 启用条件可见性。 条件可见性属性描述如下。

### 2.1 根据数据可见性 {#based-on-data}

**基于数据** 的可见性允许您根据动态数据结果显示小部件。 例如，您只想为有 **Gold** 级的客户显示一个特殊的报价：

![根据数据可见](attachments/page-editor-widgets-visibility-section/visible-based-on-data.jpg)

### 2.2 条件基于： {#condition}

基于</strong> 属性的 **条件仅在 [基于数据](#based-on-data) 的可见性启用时才显示。 以下选项可用：</p>

* **属性** - 定义条件是否基于属性值。 在这种情况下，只有在与所选属性的某个值匹配时才会显示小部件。
* **表达式** -- 定义条件是否基于表达式。 在这种情况下，只有当表达式返回布尔值 `true` 时才会显示小部件。 关于表达式的更多信息，见 [表达式](expressions)。

### 2.3 属性 {#attribute}

This property is shown only when the expression the [Condition Based on](#condition) is set to **Attribute**. 允许您选择条件将基于的属性。 属性必须是布尔值或枚举类型。

### 2.4 属性值 {#attribute-values}

此属性仅在属性为 [属性](#attribute) 属性被选中时才显示。 **属性值** 允许您选择特定属性值。

如果您只想为有 **Gold** 级的客户显示一个特殊的报价， 您需要在 **属性中选择 *级* 级** 属性和 *金币* 级为 **属性值**：

![基于属性的可见性](attachments/page-editor-widgets-visibility-section/attribute-based-visibility.png)

### 2.5 表达式

此属性允许您创建表达式，并且仅在 [条件基于](#condition) 设置为 **表达式** 时才显示。 表达式应该是布尔型。 关于如何创建表达式的更多信息，见 [表达式](expressions)。

### 2.7 基于角色可见性 {#role-based}

这个小部件可以让仅具有特定用户角色的用户可见. 例如，在出租车预订应用程序， 您想要向客户和管理员显示一个出租车司机评级，但是不显示出租车司机：

![根据角色可见的](attachments/page-editor-widgets-visibility-section/visible-based-on-role.jpg)

{{% alert type="info" %}}

您只能在启用安全性时配置基于角色的条件可见性。 欲了解更多信息，请参阅 [安全性，角色 & 权限](settings-security)

{{% /报警 %}}

### 2.8 角色

**角色** 属性仅在启用 [基于角色的](#role-based) 属性并显示您的应用中可用角色列表时才显示。

## 3 执行基本功能

### 3.1 根据属性值配置可见性

要根据属性值配置可见性，请按下面的步骤：

1. 选择一个只显示特定属性值并转到属性的部件。

2. 在 **条件可见性** 部分中，切换基于数据</strong> 属性的 **可见性。</p></li>

3

基于</strong> 的 **条件默认设置为 **属性**。 点击 **属性** 属性： </p>

    ![](attachments/page-editor-widgets-visibility-section/attribute-based-property.png)</li>

4

在 **选择属性** 对话框中，选择布尔值或枚举类型的属性，然后点击 **选择**。

5

**属性值** 属性现在显示在属性中。 取消不符合您想要设置的条件的值：

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-visibility-section/attribute-values.png){{% /image_container %}} </ol>

基于属性值的条件可见性被设置为小部件。

### 3.2 根据角色配置条件可见性

要配置基于角色的条件可见性，请执行以下操作：

1. 选择一个只显示某些用户角色并转到其属性的部件。

2. 在 **条件可见性** 部分中，切换基于</strong> 属性的 **可见性。</p></li>

3

您应用中可用角色列表显示在 **角色** 属性中。 取消想要隐藏小部件的角色的勾划：

    ![](attachments/page-editor-widgets-visibility-section/role-based-example.png)    </ol>

基于用户角色的条件可见性被设置为小部件。

## 4 阅读更多

* [小部件](页面编辑器部件)
* [安全性，角色 & 权限](settings-security)
