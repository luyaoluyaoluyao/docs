---
title: "导航文档"
description: "描述Mendix Studio中的导航菜单。"
menu_order: 40
tags:
  - "工作室"
  - "navigation"
  - "应用菜单"
---

## 1 导言

Mendix Studio中的导航文档以树的形式显示您的应用的已配置菜单。 您可以在导航中创建项目和分项。

![](attachments/navigation/nagigation-wm-vs-app.png)

点击左侧菜单栏中对应的图标打开 **导航文档**。

{{% image_container width="300" %}}![](attachments/navigation/navigation-icon.png)
{{% /image_container %}}

{{% alert type="info" %}}

在工作室中，您正在查看和编辑一个响应式类型的导航配置文件，而在Studio Pro中则有更多类型的配置文件。 关于Studio Pro的更多信息，请参阅 [2 Profiles](/refguide/navigation#profiles) in *Navigation in Mendix 7 。 & 以上* in *Studio Pro Guide*

{{% /报警 %}}

## 2 个菜单项属性 {#properties-of-menu-items}

菜单项的属性由以下部分组成：

* [事件](#events-section-navigation)
* [A. 概况](#general-section-navigation)

{{% image_container width="300" %}}![](attachments/navigation/navigation-properties.png)
{{% /image_container %}}

### 2.1 事件科 {#events-section-navigation}

您可以在 **事件** 部分中选择 **点击动作**。 **点击动作** 定义了当用户点击菜单项时执行什么操作。 现有行动见下表：

| 行 动  | 描述                                                                                                                             |
| ---- | ------------------------------------------------------------------------------------------------------------------------------ |
| 无    | 没有采取任何行动。                                                                                                                      |
| 页    | 已打开指定页面。                                                                                                                       |
| 微流   | 已执行所选微流。                                                                                                                       |
| 保存更改 | 保存当前打开页面中的所有更改并关闭页面。                                                                                                           |
| 取消更改 | 回滚当前打开页面中的所有更改并关闭页面。                                                                                                           |
| 关闭页面 | 关闭弹出窗口(用于弹出页面)或导航到先前访问的页面。 请注意，如果任何更改不被保存，此操作将关闭页面和更改。 为此目的使用 **保存更改**。                                                        |
| 登出   | 当前用户已登出应用程序。                                                                                                                   |
| 打开链接 | 触发基于链接类型的动作： <ul><li>**Web** - 导航到一个网站 </li><li>**电子邮件** - 撰写电子邮件</li><li>**Phone 通话** - 开始电话</li><li>**文本消息** - 发送文本消息</li></ul>**注意** 当您配置 **Email**和 **电话通话** 或 **消息** 选项， 触发动作时将在设备上打开相应的默认应用， 例如，默认的电子邮件客户端将被打开来撰写消息。 |

{{% alert type="info" %}}

如果菜单项有一个子项， **点击动作** 应该是 **没有**。

{{% /报警 %}}

### 2.2 概况 {#general-section-navigation}

可以在 **常规** 部分中配置的属性在下面的表格中描述。

| 财产    | 描述                                   | 依赖于                                                                                       |
| ----- | ------------------------------------ | ----------------------------------------------------------------------------------------- |
| 标题    | 填写菜单项的名称。                            | 无                                                                                         |
| 图标    | 在此设置菜单项的图标。                          | 无                                                                                         |
| 设置为主页 | 允许您将菜单图标设置为主页，就像在用户打开您的应用程序时所看到的第一页。 | **点击动作**, 只有当页面或微流被选为 **点击动作** 时才可用。 欲了解更多信息，见 [Events Sect](#events-section-navigation)。 |

## 3 创建菜单项

要创建一个新的导航项，请执行以下操作：

1. 点击左边菜单栏中的 **导航文档** 图标打开 **导航**。

2.  点击导航树末尾的加号来创建一个菜单项。 或者点击现有导航项旁边的加号来创建其分项

    ![](attachments/navigation/adding-navigation-items.png)

3. 如果需要指定创建项目的属性(详细信息，请参阅 [菜单项属性](#properties-of-menu-items))。

## 4 阅读更多

* [常规信息](general)
