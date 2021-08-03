---
title: "使用 Eclipse"
category: "Java 程序"
tags:
  - "studio pro"
---

## 1 导言

您可以使用 Eclipse 在Mendix 应用程序中写入和调试 Java 操作。 当部署Mendix 模型时，生成一个 Eclipse 项目文件、类路径文件和启动配置。

## 2 设置 Eclipse

在Mendix中，所有文本都保存在UTF-8编码中。 为了确保您的源代码也保存在UTF-8中，请执行以下操作：

1.  选择 **窗口 > 首选项**。
2.  在新菜单窗口中选择 **工作区**。
3.  选择 **UTF-8**:

    ![设置 UTF-8 编码](attachments/java-programming/eclipse-utf8-encoding.png)

您还应该安装并选择一个 Java 开发包 (JDK)。

![选择一个默认 JDK](attachments/java-programming/eclipse-jdk.png)

请务必添加 JDK 并在 Eclipse 中选择它作为默认值。

## 3 添加Mendix 应用程序

要将 Mendix 应用程序添加到 Eclipse，请执行以下操作：

1.  选择 **文件 > 导入**
2.  打开 **常规** 文件夹，选择 **现有项目到工作区** 并选择 **下一个 >**：

    ![导入现有项目](attachments/java-programming/eclipse-select-import.png)

3.  使用选项 **选择根目录**，浏览您的 Mendix 应用文件夹并选择 **完成**：

    ![选择根目录](attachments/java-programming/import-eclipse-project.png)

## 4 启动Mendix 应用程序

为了启动该项目，采取以下行动：

1.  选择 **运行 > 运行配置...** 或 **运行 > 调试配置...**, 取决于你想如何启动应用程序。
2.  选择 **Java 应用程序** 和由Mendix Studio Pro生成的启动配置将会出现。
3.  选择 **运行** (或 **调试**) 来启动应用程序：

    ![启动配置](attachments/java-programming/eclipse-run-configuration.png)

启动应用程序后， **M2EE 管理控制台** 将会出现。 这是您通常在 Mendix Studio Pro中看到的同一个控制台，如果您将从那里运行该应用程序。 您可以关闭控制台来阻止您的应用程序。

![M2EE 管理控制台](attachments/java-programming/eclipse-debug-log.png)
