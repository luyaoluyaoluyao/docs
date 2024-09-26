---
title: "项目菜单"
parent: "menus"
description: "在Studio Pro中描述项目菜单。"
menu_order: 30
tags:
  - "Studio Pro"
  - "项目菜单"
  - "顶栏"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/project-menu.pdf)。
{{% /报警 %}}

## 1 导言

在 **工程** 菜单中，您可以查看和/或操纵与您的工程和部署相关的设置。 例如，您可以创建一个部署包。

{{% image_container width="300" %}}![项目菜单](attachments/project-menu/project-menu.png)
{{% /image_container %}}

## 2 个工具

在 **项目** > **工具**下，您可以在更新小部件时找到设置 按钮图标和布局，检查小部件，并将类转换为 **设计** 属性。

![工具](attachments/project-menu/tools.png)

### 2.1 批量更新按钮图标

**批量更新按钮图标** 选项允许您在单批处理过程中更新许多按钮图标。

### 2.2 批量更新布局

**批量更新布局** 选项允许您在单个批量更新过程中更新多个页面的布局。

### 2.3 更新部件 {#update-widgets}

**更新小部件** 选项提供了您在应用中使用的小部件的当前版本， 小部件的最新版本以及更新选项。

### 2.4 检查小部件

**检查小部件** 选项检查您在应用程序中实现的小部件是否已经正确构建。

### 2.5 将类转换为设计属性

**转换类为设计属性** 选项允许您将小部件中的类转换为设计属性，以帮助更改小部件风格。 获取更多信息，请参阅 [如何实现本地移动样式](/howto8/mobile/native-styling)

## 3 同步项目目录

**同步项目目录** 选项可在项目目录中创建文件夹(资源、小部件、主题等)。 它还读取了当前小部件文件夹中的小部件包。 例如，如果您将小部件添加到小部件文件夹， 您需要同步项目目录才能出现在 **Toolbox** 中。

快捷键： <kbd>F4</kbd>

## 4 在资源管理器中显示项目目录

**在 Explorer** 选项中显示项目目录显示包含项目文件的目录(*)。 pr*) 和 Windows Explorer 中的资源和 Java 动作等其他资产。 默认情况下，目录位于 **MyDocuments** 部分。

项目目录下面的目录有助于自定义应用风格和添加自定义小部件和 Java 动作：

* **主题** — — 存储 *.css* 可以用来样式应用程序的文件
* **javasource** — — 存储JavaScript 操作
* **小部件** — — 存储小部件

## 5 用于Eclipse 的部署

用于Eclipse</strong> 选项的 **部署项目部署到部署目录。 生成了 Java 根块，以便您可以在 Eclipse 中开始编辑。 此操作不编译 Java 操作。 如果您正在写入 Java 动作，您想要通过 Eclipse 编译和调试这些动作，请使用它。</p>

快捷键： <kbd>F6</kbd>

## 6 创建部署包

**创建部署包** 选项创建一个 Mendix 部署包(*)。 da*包含运行项目所需的所有文件。 如果您想要在Windows服务器上或自定义Mendix Cloud上部署您的项目，就可以使用此功能。

快捷键：  <kbd>F7</kbd>

关于创建部署包对话框中显示的设置的更多信息，请参阅 [创建部署包](create-deployment-package-dialog)。

## 7 清洁部署目录

**清理部署目录** 选项清除部署目录。

## 8 部署到许可云节点 {#deploy}

**部署到 Licensed 云节点** 选项会将团队服务器项目的最新版本部署到相关的 Mendix 云节点。

快捷键：  <kbd>Ctrl</kbd> + <kbd>F5</kbd>

{{% alert type="warning" %}}
[Mendix Studios 目标](/developerportal/deploy/studio-deployment-settings#target) 需要设置，部署用户需要有传送到设定目标的权限。
{{% /报警 %}}

关于使用此选项的更多信息，请参阅 [部署到云端](deploy-to-the-cloud-dialog)。

## 9 阅读更多

* [Studio Pro Overview](studio-pro-overview)
* [部署](/developerportal/deploy)
