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

* [小部件的属性值](#attribute-based)
* [用户角色在您的应用程序](#role-based)

例如， 您有一个网上商店，您不想在交货地址匹配账单地址时两次填写同一个地址。 只有当用户取消对 **账单地址与送货地址** 选项相同时，您才想显示字段来填写账单地址。 在这种情况下，您可以根据 *属性值*显示账单地址字段: 只有当 *BillingAddressame* 取消了勾选时才显示字段 *false*

![](attachments/page-editor-widgets-visibility-section/attribute-based-example.png)

您也可以只显示一个小部件到一个 *用户角色*。 例如，您可以显示一个只显示财务经理的工资金额的小部件。

查看已配置条件可见性的部件， 点击眼睛图标是页面左上角的 **显示** 选项： ![](attachments/page-editor-widgets-visibility-section/highlight-conditional-items.png)

## 2 条件可见性属性

您可以根据选定的属性值和/或用户角色启用条件可见性。 条件可见性属性描述如下。

### 2.1 基于属性 {#attribute-based}

**基于属性的** 可见性允许您只在小部件符合所选属性的特定值时才显示小部件。

{{% alert type="info" %}}

属性必须是布尔值或枚举类型。

{{% /报警 %}}

{{% alert type="info" %}}

当一个部件放入数据容器：数据视图或列表视图时，您只能配置基于属性的条件可见性。

{{% /报警 %}}

### 2.2 属性值

此属性仅在选择 [属性](#attribute-based) 属性时才显示。 **属性值** 允许您选择特定属性值。

例如，您只想为有 **Gold** 级的客户显示一个特殊的报价。 在 **基于属性** 属性中选择 *级* 级， *Gold* 级为 **属性值**：

{{% image_container width="300" %}}
![](attachments/page-editor-widgets-visibility-section/attribute-based-visibility.png)
{{% /image_container %}}

### 2.3 以角色为基础 {#role-based}

小部件可以显示给您应用中可用的特定用户角色。 如果启用，此设置将使所有链接到所选用户角色的用户可见小部件。

{{% alert type="info" %}}

您只能在启用安全性时配置基于角色的条件可见性。 欲了解更多信息，请参阅 [安全性，角色 & 权限](settings-security)

{{% /报警 %}}

### 2.4 角色

**角色** 属性只有在基于 [角色的](#role-based) 属性启用时才会显示出来，并显示您应用中可用的角色列表。 选择您想让小部件可见的角色。 例如，在出租车预订应用程序， 您想要向客户和管理员显示一个出租车司机评级，但是不显示出租车司机：

{{% image_container width="300" %}}
![](attachments/page-editor-widgets-visibility-section/role-based-visbility.png)
{{% /image_container %}}

## 3 执行基本功能

### 3.1 配置基于属性的条件可见性

要配置基于属性的可见性，请执行以下操作：

1. 选择一个只显示特定属性值并转到属性的部件。

2. 在 **条件可见性** 部分中，点击 **属性** 属性：

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-visibility-section/attribute-based-property.png){{% /image_container %}}

3. 在 **选择属性** 对话框中，选择布尔值或枚举类型的属性，然后点击 **选择**。

4. **属性值** 属性现在显示在属性中。 取消不符合您想要设置的条件的值：

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-visibility-section/attribute-values.png){{% /image_container %}}

基于属性的条件可见性是为小部件设置的。

### 3.2 禁用基于属性的条件可见性

要禁用基于属性的可见性，请遵循以下步骤：

1. 选择一个您想要禁用基于属性的可视性并转到它的属性的部件。

2. 在 **条件可见性** 部分中，点击 **属性** 属性。

3. 在 **选择属性** 对话框中，点击 **清除**：

    {{% image_container width="400" %}}![](attachments/page-editor-widgets-visibility-section/clear-attribute-based-visibility.png){{% /image_container %}}

基于属性的条件可见性已为小部件清除。

### 3.3 配置基于角色的条件可见性

要配置基于角色的条件可见性，请执行以下操作：

1. 选择一个只显示某些用户角色并转到其属性的部件。

2. 在 **条件可见性** 部分中，切换基于 **角色** 属性。

3. 您应用中可用角色列表显示在 **角色** 属性中。 取消想要隐藏小部件的角色的勾划：

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-visibility-section/role-based-example.png){{% /image_container %}}


基于角色的条件可见性设置为小部件。

### 3.4 禁用基于角色的条件可见性

要禁用基于角色的条件可见性，请遵循以下步骤：

1. 选择一个您想要禁用基于角色的可见性并转到其属性的部件。
2. 在 **条件可见性** 部分中，禁用 **基于角色的** 属性。

基于角色的条件可见性被禁用为小部件。

## 4 阅读更多

* [小部件](页面编辑器部件)
* [安全性，角色 & 权限](settings-security)
