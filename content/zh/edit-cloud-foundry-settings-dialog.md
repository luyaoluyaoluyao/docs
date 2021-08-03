---
title: "编辑Cloud Foundry 设置"
parent: "运行菜单"
tags:
  - "Cloud Foundry"
  - "部署"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/edit-cloud-foundry-settings-dialog.pdf)。
{{% /报警 %}}

## 1 导言

**编辑Cloud Foundry 设置** 菜单选项允许您指定将您的应用程序部署到云端基金会实例所需的信息。

![编辑Cloud Foundry 设置菜单项](attachments/run-menu/edit-cf-settings.png)

{{% alert type="info" %}}
关于部署到Cloud Foundry的更多信息可在 [Cloud Foundry：部署](/developerportal/deploy/cloud-foundry-deploy) 中找到。
{{% /报警 %}}

## 2 个正在进入凭据

为云端基金会部署配置配置配置应用程序的第一步是输入您想要使用的云端基金会账户信息。

![输入Cloud Foundry 凭据](attachments/run-menu/cloud-foundry-credentials.png)

输入屏幕上的详细信息，如下所述，然后点击 **下一个** 验证指定的凭据并显示下一个配置步骤。

### 2.1 API Endpoint

定义云端基金会平台的 **API 端点** 的URL，将用于部署。

### 2.2 用户名

The **User name** of your Cloud Foundry account.

### 2.3 密码

您的云端Foundry账户的 **密码**。

## 3 选择云端创始应用程序

第二步允许您在云端基金会组织中选择一个现有的应用或创建一个新的应用程序。 您的 Mendix 应用程序将在这里部署。

![输入云端Foundry应用的设置](attachments/run-menu/cloud-foundry-app-settings.png)

### 3.1 组织

选择您想要使用的 **组织**。 如果没有组织可用，您将需要在您的云端基金帐户中配置一个组织； 无法从 Mendix Studio Pro内部创建一个新的。

### 3.2 空间

选择您想要使用的 **空间**。 请注意，您想要使用的空间必须已经在您的云端账户中配置； 无法从 Mendix Studio Pro内部创建一个新的。

### 3.3 应用

如果您想要使用现有的应用环境，请 **选择现有的应用** 或 **如果您想要创建一个新的应用环境，则创建新的应用**

#### 3.3.1 选择现有应用

如果您 **选择现有的应用程序** ，您将能够从下拉列表中选择正确的应用程序。

#### 3.3.2 创建新应用

如果您 **创建新的应用程序** ，您需要做以下工作：

1. 选择应用程序将从下拉列表运行的 **域**。
2. 为应用程序输入 **应用程序名称**。

您的应用程序的 URL 将是 {App name}.(Domain)。

### 3.4 建筑包

在这里您可以输入您想要在云端基金会应用程序中使用的 **Buildpack** 的 URL。 仅当您不想使用默认的 Mendix 构建包时才更改此设置。
