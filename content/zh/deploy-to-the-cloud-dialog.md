---
title: "部署到云"
parent: "项目菜单"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/deploy-to-the-cloud-dialog.pdf)。
{{% /报警 %}}

## 1 导言

此菜单选项对话框创建一个版本化的部署包，并将其部署到您的 Mendix Cloud 环境中。

![部署到云对话框](attachments/project-menu/deploy-to-the-cloud.png)

## 2 发展线

选择你想要创建部署包的 **开发行**。 这可以是主线或任何分支线。 例如，如果你想要在网上修复你的操作，你可以从维护分支线创建一个包。 或者您从主行创建一个部署包，因为您准备好部署下一个大版本的应用程序。

## 3 修订版

Choose the **Revision** of the selected development line for which you want to create a deployment package. 您可能不想要更新的一个原因是如果您想排除一些最近开发的功能。

## 4 个新版本

为部署包选择一个 **新版本**。 该版本由四个数字组成：主要版本、次要版本、补丁和订正。 修订版本由您选择的 **修订版** 固定和决定。

您可以自由选择其它数字，但是最好用约定来进行编号。 主要版本通常含有主要的新特征或重写现有特征。 一个小版本包含小的新功能和修复。 补丁解决了一些小问题，不应更改应用程序的数据模型。 补丁发布应该可以与另一个补丁发布互换，但数据没有变化。

Studio Pro 将向您展示您创建软件包的最新版本(如果有的话)。 您可以根据您使用的约定，增加主要、次要或补丁。

## 5 个描述

您可以为这个部署包输入一个自定义 **描述**。 它纯粹是为了您自己的参考，以便您可以快速识别一个包。 开发者门户将向您展示此描述以及版本号。

## 6 个应用程序

这将在 Mendix Cloud 中显示 **应用** 部署包。 这只是为了提供信息，您不能在这里更改目标。

## 7 个许可证用户

这将显示此授权节点的 **许可协议**。
