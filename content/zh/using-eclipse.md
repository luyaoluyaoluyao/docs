---
title: "使用 Eclipse"
category: "Java 程序"
tags:
  - "studio pro"
---

使用 Eclipse 来写入和调试Mendix 项目中的 Java 操作非常容易。 当部署Mendix 模型时，生成一个 Eclipse 项目文件、类路径文件和启动配置。

在Mendix中，所有文本都保存在UTF-8编码中。 首先请确保你的源代码也保存在UTF-8\中。 这可以通过以下窗口菜单和选择首选项来实现，然后选择下面屏幕截图中显示的 UTF-8。

{{% alert type="info" %}}

![](attachments/java-programming/918120.png) 设置 UTF-8 编码。

{{% /报警 %}}

您还应该安装并选择一个 Java 开发包 (JDK)。

{{% alert type="info" %}}

![](attachments/java-programming/918186.png) 选择默认JDK。

{{% /报警 %}}

请确保您在 Eclipse 中添加一个 JDK 并选择它作为默认值。

要将 Mendix 项目添加到 Eclipse，您可以执行这些步骤：

*   打开文件菜单并点击导入
*   打开“通用”文件夹并选择“现有工程进入工作区”，然后点击下一个
*   使用 '选择根目录'，浏览您的 Mendix 项目文件夹并单击完成

{{% alert type="info" %}}

![](attachments/java-programming/917580.png) 导入现有项目。

{{% /警示%}}!{% alert type="info" %}}

![](attachments/java-programming/917527.png) 导入现有项目步骤2。

{{% /报警 %}}

现在你可以像通常那样愉快地开始编辑你的 Java 动作。

要真正启动该项目，请根据您想要如何运行该项目，前往'调试配置'或'运行配置'。 在左侧菜单上选择 'Java 应用程序' 菜单，您将看到由 Mendix Studio Pro生成的启动配置。 只需点击右边的“调试”或“运行”即可启动应用程序。

{{% alert type="info" %}}

![](attachments/java-programming/917586.png) 查找您的启动配置。

{{% /报警 %}}

启动应用程序后，您将看到M2EE 管理控制台弹出窗口。 这是与您通常在 Mendix Studio Pro 中看到的相同的控制台，如果您要从那里运行这个项目。 您可以关闭控制台来阻止您的应用程序。

{{% alert type="info" %}}

![](attachments/java-programming/917582.png) M2EE 管理控制台。

{{% /报警 %}}
