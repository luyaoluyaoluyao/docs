---
title: "Java 程序"
description: "描述如何使用 Mendix Java 库并使用 Eclipse 作为环境写入您的 Mendix Java 动作。"
---

## 1 导言

通过 Java 动作，您可以在微流中很难实现此功能的情况下扩展您应用程序的功能。

关于Modeler中的 Java 操作的信息，请参阅 [Java 操作](java-actions)。

## 你的 Java 操作的 .java 文件中写入代码

在 *java* 文件中，您可以在标记之间写入您的 Java 代码：

*   `// BEGIN用户代码` and `// 结束用户代码`
*   `// BEGIN EXTRA Code` and `/ END EXTRA Code`

下文将对此作更详细的解释。

每次部署您的模型时，这些文件中的其他代码都会重新生成。 因此，你对它们的任何修改都会被覆盖。 然而，您的进口将被保存。

{{% alert type="info" %}}

![](attachments/819203/917584.png) 由 Mendix 桌面模型生成的 Java 动作。 此 Java 动作没有输入参数，只需返回带有值 `true` 的布尔值。

{{% /报警 %}}

当正在执行 Java 动作时， _执行方法_ 被运行时调用。 行 `// BEGIN USER CODE` and `// END USER CODE`, 您可以写您的自定义代码，在执行操作时总是被调用。 在这种方法中， 您可以在 `// BEGIN EXTRA CODE` and`/ END EXTRA CODE` 之间的部分调用其他方法。

执行动作方法会产生所有异常。 这意味着您可以在调用此 Java 动作的微流程中处理错误。 如果您想在操作中执行自己的错误处理，请使用try/catch 语句。

## 3 使用 Mendix Java 库

在您为您的 Java 操作写入的 Java 代码中，您可以使用 Mendix Java 库。

{{% alert type="info" %}}
您可以在 [apidocs.rnd.mendix 找到Javadoc 。 om](http://apidocs.rnd.mendix.com/7/runtime/index.html) 或在您安装的 Mendix 目录中(例如， *C:\Program Files\Mendix\7.0.0\r未定时\javado*)。
{{% /报警 %}}

当你导入你的项目到 Eclipse 时，这个库会自动添加到你的库中，它被称为 *mxruntime.jar*。

关于使用情况和示例的详细信息，请参阅 [如何使用 Java API](/howto7/logic-business-rules/java-api-tutorial)。

## 4 使用 Eclipse 作为环境写入您的 Mendix Java 操作

关于此主题的详细信息，请参阅 [使用 Eclipse](using-eclipse)。

## 5 个此类别中的主要文档

* [故障排除](故障排除)
* [使用 Eclipse](using-eclipse)
