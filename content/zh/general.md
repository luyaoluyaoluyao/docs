---
title: "常规信息"
description: "描述Mendix Studio的各种功能。"
menu_order: 10
tags:
  - "工作室"
  - "studio pro"
aliases:
  - /howto/tutorials/index.html
  - /howto/tutorials/mendix-tutorials.html
---

## 1 导言 {#studio-overview}

Mendix Studio是您可以创建、查看和编辑Mendix 应用程序而不需要进入技术细节的地方。 为此目的，您可以随时使用 [Studio Pro](/refguide/modeling) 和 [与Studio Pro 用户](collaborative-development) 一起开发应用。

通过 Studio 您可以在您的浏览器中创建和编辑应用程序，而无需在您的 PC 上安装软件。

下面的图片显示Studio界面的组件：

![工作室图表](attachments/general/home-page.png)

## 2 个打开工作室

您可以通过 [开发者门户](#opening-studio-via-dev-portal) 或 [Studio Pro 打开Mendix Studio](#opening-via-studio-pro)

### 2.1 通过开发者门户打开工作室 {#opening-studio-via-dev-portal}

您可以在 [开发者门户中打开](https://home.mendix.com) 来编辑Mendix Studio 中的应用程序，并点击 **在Studio** 中编辑：

{{% image_container width="350" %}}
![在工作室中编辑](attachments/general/edit-app.jpg)
{{% /image_container %}}

If you do not see **Edit in Studio**, go to [General Settings](/developerportal/collaborate/general-settings) in the Developer Portal and [enable Studio](/developerportal/collaborate/general-settings#web).

### 2.2 通过Studio Pro 打开工作室 {#opening-via-studio-pro}

您也可以通过 Studio Pro在Studio 中打开您的应用程序。 执行以下操作：

1. 在 Studio Pro，打开您想要在Studio 查看的应用程序。
2.  点击右上角的地球图标 (仅当启用工作室时可用)。

    ![全球图标](attachments/general/globe-icon.png)

应用程序在 Studio 中打开

## 3 升级工作室

点击 **在 Studio 中编辑** 后，您可能需要将您的应用程序升级到最新版本。

{{% image_container width="350" %}}![升级](attachments/general/upgrade.png)
{{% /image_container %}}

您也可以看到顶部条建议升级到下一个Mendix 版本。 关于工作室升级和 Mendix 版本的更多信息，见 [工作室范围 & Mendix 版本](general-versions)

{{% alert type="info" %}}
当您升级工作室中的应用程序到最新的 Mendix 版本时， 您需要将您的应用程序升级到Studio Pro 的同一版本。

如果你正在与其他人一起工作, 最好是与您的团队成员一起检查是否每个人都可以将应用程序升级到最新的 Mendix 版本。

{{% /报警 %}}

## 4 切换应用模式

打开工作室后，应用程序的主页打开.

您可以通过点击相应的图标将页面视图更改为不同的视图：

* 移动设备
* 平板电脑
* 响应(桌面)

    {{% image_container width="300" %}}![设备模式](attachments/general/view.png)
    {{% /image_container %}}

## 5 左菜单栏

左侧菜单栏允许您在工作室访问页面、域模型、微流、工作流和导航文档。 在您的应用中搜索不同的元素，打开设置并自定义您的应用外观：

{{% image_container width="250" %}}
![左菜单栏](attachments/general/left-menu-bar.png)
{{% /image_container %}}

左侧菜单栏的所有项目在下表中描述：

| 菜单项                        | 快捷方式         | 描述                                                                                                                                                                                                 |
| -------------------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [页 次](page-editor)         | 1            | 显示应用程序中所有页面的列表。 选择一个页面来打开它。                                                                                                                                                                        |
| [域模式](域名模型)                | 2            | 显示应用程序的域模型。                                                                                                                                                                                        |
| [微型流动](微流)                 | 3            | 在应用程序中显示所有微流列表。 选择一个微流程来打开它。                                                                                                                                                                       |
| [工作流](workflows)           | 无            | 在应用程序中显示所有工作流列表。 选择要打开的工作流。                                                                                                                                                                        |
| [导航文档](navigation)         | 4            | 以导航树的形式显示一个配置的菜单。 您可以将导航树的菜单结构扩展到两个级别，无限页数。                                                                                                                                                        |
| 搜索(放大眼镜) 图标                | <kbd>/</kbd> | 帮助您通过微流程、实体和页面搜索。 开始输入您正在寻找的项目的名称，搜索功能将返回它发现的匹配项， 使用精确匹配以及基于输入的字符的模糊匹配。 <br />您也可以使用 "/" 快捷键搜索您的应用。                                                                                          |
| [主题自定义器](theme-customizer) | 无            | 允许您用自定义品牌、颜色和排版来样式应用程序。                                                                                                                                                                            |
| [设置](设置)                   | 无            | **设置** 包含 **角色和权限** 和 **部件概述**. <br />通过 [角色和权限](settings-security) 您可以为不同类型的用户管理访问您的应用的权限。  <br /> [小部件概述](settings-widget-overview) 为您提供了所有小部件及其状态的概述。 小部件是用于构建页面的用户界面元素(提醒、按钮、图表等)。 |

## 6 工具箱，属性和 Buzz

工作室的顶部右侧菜单包括 **工具箱**, **属性** 和 **Buzz** 选项卡：

![工具箱，属性，Buzz](attachments/general/toolbox-properties-buzz.png)

下表介绍了 **工具箱**, **属性** , 和 **Buzz** 选项卡：

| Tab                       | 描述                                     |
| ------------------------- | -------------------------------------- |
| 工具箱                       | 显示当前编辑器可用的工具。                          |
| 属性                        | 显示选中项的属性。                              |
| [布兹斯](collaboration-buzz) | 允许应用开发团队对不同页面、微流、域模型和工作室布局发表评论，并且相互交互。 |

## 7 顶部菜单栏

顶部菜单栏允许撤销或重做操作，查看您最近的文档，预览或发布您的应用，并在您的应用中查看检查。 您也可以访问帮助和学习，并在顶部菜单栏查看各种信息。

![顶部菜单栏](attachments/general/top-bar.png)

顶部菜单栏项目在下表中描述：

| 菜单项                    | 描述                                                                                                                                     |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **切换到** 菜单             | **切换到** 菜单允许您切换到 Mendix 平台的其他部件。 此菜单包含以下选项： <ul><li>**Mendix Home** - 带你到[开发者门户](/developerportal/index)</li><li>**Studio** - 在开发者门户中打开 **我的应用程序** 屏幕</li><li>**Get Studio Pro** - 下载最新版本的 Mendix Studio Pro</li><li>**Academy** - 链接到[Mendix Academy](https://gettingstarted.mendixcloud.com)</li><li>**Docs** - 链接到[Mendix Documentation](https://docs.mendix.com/)</li></ul>                                                                   |
| 撤销/重做操作                | 有按钮撤销或重做最后一个操作。 您也可以相应使用 <kbd>Ctrl</kbd>+<kbd>Z</kbd> 和 <kbd>Ctrl</kbd>+<kbd>Y</kbd> 快捷键。                                              |
| 最近文档下拉菜单               | 您正在查看的文档将在此选项中显示。 当您点击下拉菜单时，您最近查看的文档会显示在列表中。 单击文档以打开它。                                                                                 |
| [预览按钮](publishing-app) | 显示您的应用在发布后会看起来像是什么。                                                                                                                    |
| [发布按钮](publishing-app) | 您可以使用此按钮发布您的应用。 点击 **发布** > **更新** 以发布您在工作室中所作的最新更改。 欲了解更多信息，请参阅 [预览 & 发布您的应用程序](publishing-app)                                       |
| [检查按钮](检查)             | 显示一致性错误(如果有的话)，阻止您的应用被预览和发布。 关于错误的更多信息，请参阅 [一致性错误](consistency-errors)。<br />您也可以使用 <kbd>C</kbd> 快捷键查看 **检查** 面板。                |
| 帮助图标                   | 打开 **帮助 & 学习** 侧菜单， 您可以在哪里找到即时帮助 -- 视频和如何在当前任务中向您提供解释和指导。 例如，当在域模型工作时，您将看到视频和如何在域模型上看到。 将实体和属性作为向你推荐的主题。 然而，您也可以浏览覆盖工作室所有主要功能的类别和其他主题。 |
| **更多选项** 图标            | 提供额外信息。 您可以找到以下内容：<ul><li>**关于** - 显示[Studio 版本和 Mendix 版本](通用版本) </li><li>**键盘快捷键** - 打开工作室快捷键列表</li><li>**参加产品旅游** - 开始导游带领产品的导览，并在Studio周围展示你</li><li>**联系Mendix Support** - 链接到[Mendix Support Portal](https://support.mendix.com/hc/en-us)</li><li>**Mendix Assists 是否正常** - 启用/禁用[Mendix Assist](mx-assist)</li><li>**Open App Buzz** - 带你去开发者门户的[App Buzz](/developerportal/collaborate/buzz#app-buz)</li><li>**在Studio Pro中编辑** - 在 Studio Pro中打开您的应用程序</li></ul>                                                                                            |

## 8 剪切/覆盖/粘贴函数

您可以复制并粘贴页面和微流。 您也可以剪切、复制和粘贴分开的元素，如部件或微流程活动。

### 8.1 复制/粘贴工作流、页面、微流和枚举数 {#copy-paste-documents}

工作流、页面、微流和枚举可以复制到剪贴板，然后粘贴到不同的工作室应用程序。 您也可以将它们复制并粘贴到同一应用程序，但有 **重复的** 选项可以用于此目的。 关于如何复制、粘贴或重复工作流、页面、微流和枚举的更多信息，请参阅 [Workflow](workflows)， [页面](page-editor), [Microflow](microflows), 和 [枚举](domain-models-enumeration)

在复制和粘贴页面、微流和枚举时如下所示：

* 您只能复制/粘贴工作流、页面、微流和枚举到拥有相同Mendix 版本的工作室应用
* 您只能在同一浏览器的实例之间复制/粘贴工作流、页面、微流和枚举记录
* You *cannot* copy/paste from Studio to Studio Pro or vice versa

### 8.2 Cut/Copy/Paste 独立元素

剪切/复制/粘贴功能可在工作室的所有编辑器中获取：页面、微流、工作流、域模型和导航文档。 要剪切/复制/粘贴，您可以使用 <kbd>Ctrl</kbd> + <kbd>X</kbd> /  <kbd>Ctrl</kbd> + <kbd>C</kbd> / <kbd>Ctrl</kbd> + <kbd>V</kbd> 或  <kbd>Cmd</kbd> + <kbd>X</kbd> /  <kbd>Cmd</kbd> + <kbd>C</kbd> / <kbd>Cmd</kbd> + <kbd>V</kbd>.

当使用cut/cop/paste时，显示以下特征：

* 您可以在一个视觉编辑器中剪切/复制/粘贴元素； 这意味着您可以在一页或在Studio中剪切/复制/粘贴元素。 在一个微流或其他微流中复制微流活动
* 如果工作室中的不同应用有相同的 Mendix 版本，您可以剪切/复制/粘贴元素到不同的应用
* 您不能复制/粘贴页面，微流或工作流，只能是页面或微流的元素
* 您不能从工作室剪切/复制/粘贴到工作室专业版，反之亦然。

## 9 个此类别中的主要文档

* [工作室范围 & Mendix 版本](general-versions) - 解释工作室版本如何与Mendix 版本相关联。

