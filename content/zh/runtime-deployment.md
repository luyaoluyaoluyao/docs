---
title: "运行时部署"
category: "Mendix 运行时间"
description: "Mendix Runtime 如何部署的描述"
menu_order: 30
tags:
  - "运行时间"
  - "部署"
  - "mxbuilding"
  - "运行时服务器"
  - "m2ee"
---

## 1 导言

要将您的 Mendix 模型转换为在云端运行的应用，它需要部署。 本文档描述了你的项目部署背后的概念以及它在云端开始运行的过程。 关于如何部署您的应用的技术详情，请查看开发者门户文档的 [部署](/developerportal/deploy/) 部分。

此部署描述基于云端中运行的应用程序。 您也可以在本地运行 Mendix 进行测试，但这在概念上是一样的。

## 2 Mendix 运行时部署

当你创建了一个没有结构错误的 Mendix 应用程序时，你需要通过部署它来运行它。

下面是一个图表，显示部署您的应用所涉及的过程。 下图说明每一种过程和构成部分。

![如何部署Mendix Runtime](attachments/runtime/runtime-deployment.png)

### 2.1 部署人员

这是由Mendix Cloud Portal发起的，以管理应用程序的部署。

### 2.2 停靠环境

这是用于构建包的停泊环境规格，它以云层式类似方式指定停泊环境。

### 2.3 MPK 项目

这是Studio Pro 或 Studio 创建的项目模式。 Mendix Runtime不能直接解释它。

### 2.4 MX 生成

这将mpk格式的应用程序转换为 mda 格式，Mendix Runtime可以解释。

### 2.5 Cloud Foundry

这是命令行解释器，允许创建云层基金会环境，并且将代码推到环境中。

### 2.6 建筑包

Buildpack 是 Mendix 脚本，它控制着Mendix 模型在云端环境中的部署。 它执行以下任务：

* 识别目标环境和绑定的服务，例如数据库和文件存储
* 如果它收到一个以mpk格式的项目，它将启动 Mxbuild，将其转换为 mda 格式
* 它确定了正确版本的 Java Runtime 环境并推送到环境
* 它识别了Mendix Runtime的正确版本，并使用 m2ee 将Runtime 服务器推送到环境中。 与定义项目的 mda 链接的项目

### 2.7 MDA项目

这是Mendix 应用程序的 Mendix 格式，它定义应用程序的方式可以由 Mendix Runtime 来解释。

### 2.8 CDN

这个数据储存库存储部署过程中的组件，如Mendix Runtime 和 Mx Build。

### 2.9 Java RE

这是用于运行运行运行时服务器的 Java Runtime 环境 (JRE)。 JRE的版本取决于运行时服务器的版本。 例如，Mendix 7 正在运行JRE 8版本，Mendix 8 正在运行JRE 11版本。

### 2.10 M2ee

M2ee 是一个使用 python 编写的辅助工具集，用于部署 Mendix 应用。 它有两种形式：m2ee-tool和m2ee-sidecar，这取决于目标平台。 它启动了 Java RE 并指向相关版本的 Runtime 服务器二进制文件 (jar) 来启动运行时服务器。 一旦启动，m2e将连接到 Runtime 服务器，告诉它需要加载哪个Mendix 应用程序模型。

### 2.11 运行时服务器

这是运行应用程序的解释器。 欲了解更多信息，请访问 [运行时服务器](runtime-server)。

