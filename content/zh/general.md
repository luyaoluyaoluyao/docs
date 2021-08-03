---
title: "常规信息"
description: "描述Mendix Studio的各种功能。"
menu_order: 10
tags:
  - "工作室"
  - "studio pro"
---

## 1 导言 {#studio-overview}

Mendix Studio是您可以创建、查看和编辑Mendix 应用程序而不需要进入技术细节的地方。 为此目的，您可以随时使用 [Studio Pro](/refguide/modeling) 和 [与Studio Pro 用户](general-collaborative-development) 一起开发应用。

通过 Studio 您可以在您的浏览器中创建和编辑应用程序，而无需在您的 PC 上安装软件。

下面的图片显示Studio界面的组件：

![](attachments/general/home-page.png)

## 2 个打开工作室

You can open Mendix Studio [via Developer Portal](#opening-studio-via-dev-portal) or [via Studio Pro](#opening-via-studio-pro).

### 2.1 通过开发者门户打开工作室 {#opening-studio-via-dev-portal}

您可以在 [开发者门户](https://home.mendix.com) 中打开您的应用程序并点击 **在Studio** 中编辑Mendix Studio：

![](attachments/general/edit-app.jpg)

If you do not see **Edit in Studio**, go to [General Settings](/developerportal/collaborate/general-settings) in the Developer Portal and [enable Studio](/developerportal/collaborate/general-settings#web).

### 2.2 通过Studio Pro 打开工作室 {#opening-via-studio-pro}

您也可以通过 Studio Pro在Studio 中打开您的应用程序。 执行以下操作：

1. 在 Studio Pro，打开您想要在Studio 查看的应用程序。

2.  点击右上角的地球图标 (仅当启用工作室时可用)。

    ![](attachments/general/globe-icon.png)

应用程序在 Studio 中打开

## 3个工作室升级

点击 **在 Studio 中编辑** 后，您可能需要将您的应用程序升级到最新版本。

{{% image_container width="350" %}}![](attachments/general/upgrade.png)
{{% /image_container %}}

{{% alert type="info" %}}
当您升级工作室中的应用程序到最新的 Mendix 版本时， 您需要将您的应用程序升级到Studio Pro 的同一版本。

如果你正在与其他人一起工作, 最好是与您的团队成员一起检查是否每个人都可以将应用程序升级到最新的 Mendix 版本。 原因是，一旦您更新Studio，您也需要更新Studio Pro。

{{% /报警 %}}

## 4 切换应用模式

打开工作室后，应用程序的主页打开.

您可以通过点击相应的图标将页面视图更改为不同的视图：

*  移动设备
*  平板电脑
*  响应(桌面)

    {{% image_container width="350" %}}![](attachments/general/view.png)
    {{% /image_container %}}

## 5 左菜单栏

左侧菜单栏提供以下选项：

{{% image_container width="350" %}}![](attachments/general/left-menu-bar.png)
{{% /image_container %}}

| 菜单项                        | 快捷方式         | 描述                                                                                                                                                                                                         |
| -------------------------- | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mx 标志                      | 无            | Mx 徽标是返回应用程序的 [开发者门户](https://home.mendix.com) 的返回按钮。                                                                                                                                                      |
| [页 次](page-editor)         | 1            | 显示应用程序中所有页面的列表。 在您选择一个页面后，它会在 Studio 中打开。                                                                                                                                                                  |
| [域模式](域名模型)                | 2            | 显示应用程序的域模型。                                                                                                                                                                                                |
| [微型流动](微流)                 | 3            | 在应用程序中显示所有微流列表。  点击微流程后，它将在工作室中打开                                                                                                                                                                          |
| [导航文档](navigation)         | 4            | 以导航树的形式显示一个配置的菜单。 您可以将导航树的菜单结构扩展到两个级别，无限页数。                                                                                                                                                                |
| 搜索(放大眼镜) 图标                | <kbd>/</kbd> | 帮助您通过微流程、实体和页面搜索。 开始输入您正在寻找的项目的名称，搜索功能将返回它发现的匹配项， 使用精确匹配以及基于输入的字符的模糊匹配。 <br />您也可以使用 "/" 快捷键搜索您的应用。                                                                                                  |
| [设置](设置)                   | 无            | **设置** 包含 **角色和权限** 和 **部件概述**. <br />通过 **[角色和权限](settings-security)** 您可以为不同类型的用户管理对您应用程序的访问。  <br /> [**小部件概述**](settings-widget-overview) 为您提供了所有小部件及其状态的概述。 小部件是用于构建页面的用户界面元素(提醒、按钮、图表等)。 |
| [主题自定义器](theme-customizer) | 无            | 您可以在这里用自定义品牌、颜色和排版来样式设计您的应用程序。                                                                                                                                                                             |

## 6 工具箱，属性和 Buzz

工作室的顶部右侧菜单包括 **工具箱**, **属性** 和 **Buzz** 选项卡。

![](attachments/general/toolbox-properties-buzz.png)

| Tab | 描述                                    |
| --- | ------------------------------------- |
| 工具箱 | 显示当前编辑器可用的工具。                         |
| 属性  | 显示选中项的属性。                             |
| 布兹斯 | 允许应用开发团队对不同页面、微流、域模型和导航布局发表评论，并且相互交互。 |

## 7 顶栏

顶部栏提供以下选项：

![](attachments/general/top-bar.png)

| 顶栏项目                   | 描述                                                                                                                                |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| 状态图标                   | 显示Studio的互联网连接状态。 如果状态为绿色，工作室将被连接。 当灰色时，Studio离线。                                                                                 |
| 撤销/重做操作                | 撤销或重做最后一个操作。 您也可以相应使用 Ctrl+Z 和 Ctrl+Y 快捷方式。                                                                                       |
| 最近文档下拉菜单               | 您正在查看的文档将在此选项中显示。 当您点击下拉菜单时，您最近查看的文档会显示在列表中。 您可以点击文档来打开它。                                                                         |
| [发布按钮](publishing-app) | 部署和运行应用程序。 更新您的应用程序来部署您在 Studio 中所做的最新更改。 一旦部署，点击 **查看** 来查看您的应用正在操作。 欲了解更多信息，请参阅 [发布您的应用](publishing-app)                        |
| [检查按钮](检查)             | 显示当前应用中的错误和警告。 如果应用程序中有任何错误，您将无法发布您的应用，直到您解决这些错误。 关于错误的更多信息，请参阅 [一致性错误](consistency-errors)。<br />您也可以使用 C 快捷键查看 **检查** 面板。 |
| 信息图标                   | 您可以在这里找到以下信息：<ul><li>**关于** - 显示[Studio 版本和 Mendix 版本](通用版本) </li><li>**键盘快捷键** - 打开工作室快捷键列表</li><li>**参加产品旅游** - 开始导游带领产品的导览，并在Studio周围展示你</li><li>**询问社区** - 一个链接到[Mendix Forum](https://forum.mendixcloud.com/index4.html)，您可以在那里提问并探索整个Mendix 社区提供的知识<li>**检查文档** - 链接到[Studio 7 Guide](index)</li><li>**联系Mendix Support** - 链接到[Mendix Support Portal](https://support.mendix.com/hc/en-us)<li>**Mendix Academy** - 链接到[Mendix Academy](https://academy.mendix.com)</li><li>**Mendix Assists 是否正常** - 启用/禁用[Mendix Assist](mx-assist)</li><li>**在Studio Pro中编辑** - 在 Studio Pro中打开您的应用程序</li></ul>                                                                                            |

## 8 剪切/覆盖/粘贴函数

剪切/复制/粘贴函数可以在工作室的所有编辑器中使用：页面、微流、域模型和导航。 要剪切/复制/粘贴，您可以使用 <kbd>Ctrl</kbd> + <kbd>Z</kbd> /  <kbd>Ctrl</kbd> + <kbd>C</kbd> / <kbd>Ctrl</kbd> + <kbd>V</kbd> 或  <kbd>Cmn</kbd> + <kbd>Z</kbd> /  <kbd>Cmd</kbd> + <kbd>C</kbd> / <kbd>Cmd</kbd> + <kbd>V</kbd>.

当使用cut/cop/paste时，显示以下特征：

* 您可以在一个编辑器中剪切/复制/粘贴元素； 这意味着您可以在一页或在Studio中剪切/复制/粘贴元素。 在一个微流或其他微流中复制微流活动
* 如果工作室中的不同应用有相同的 Mendix 版本，您可以剪切/复制/粘贴元素到不同的应用
* 您不能复制/粘贴页面或微流程，只能是页面或微流程的元素
* 您不能从工作室剪切/复制/粘贴到工作室Pro

## 9 阅读更多

* [域模型](域名模型)
* [微型流动](微流)
* [页 次](page-editor)
