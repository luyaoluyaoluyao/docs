---
title: "Java 程序"
description: "描述如何使用 Mendix Java 库并使用 Eclipse 作为环境写入您的 Mendix Java 动作。"
tags:
  - "studio pro"
---

## 1 导言

通过 Java 动作，您可以在微流中很难实现此功能的情况下扩展您应用程序的功能。

要深入了解Mendix的 Java 编程，请查看此视频：

<img
  style="width: 100%; margin: auto; display: block;"
  class="vidyard-player-embed"
  src="https://videoshare.mendix.com/watch/aDNqicHTbTMAqYkQvvxAjc?.jpg"
  data-uuid="aDNqicHTbTMAqYkQvvxAjc?"
  data-v="4"
  data-type="inline"
 />

Studio Pro中关于Java 操作的信息，请参阅 [Java 操作](java-actions)。


## 你的 Java 操作的 .java 文件中写入代码

在 *java* 文件中，您可以在标记之间写入您的 Java 代码：

*   `// BEGIN用户代码` and `// 结束用户代码`
*   `// BEGIN EXTRA Code` and `/ END EXTRA Code`

下文将对此作更详细的解释。

每次部署您的模型时，这些文件中的其他代码都会重新生成。 因此，你对它们的任何修改都会被覆盖。 然而，您的进口将被保存。

{{% alert type="info" %}}

![](attachments/java-programming/917584.png) 由 Mendix Studio Pro生成的 Java 动作。 此 Java 动作没有输入参数，只需返回带有值 `true` 的布尔值。

{{% /报警 %}}

当正在执行 Java 动作时， _执行方法_ 被运行时调用。 行 `// BEGIN USER CODE` and `// END USER CODE`, 您可以写您的自定义代码，在执行操作时总是被调用。 在这种方法中， 您可以在 `// BEGIN EXTRA CODE` and`/ END EXTRA CODE` 之间的部分调用其他方法。

执行动作方法会产生所有异常。 这意味着您可以在调用此 Java 动作的微流程中处理错误。 如果您想在操作中执行自己的错误处理，请使用try/catch 语句。

## 3 使用 Mendix Java 库

在您为您的 Java 操作写入的 Java 代码中，您可以使用 Mendix Java 库。

{{% alert type="info" %}}
您可以在 [apidocs.rnd.mendix 找到Javadoc 。 om](http://apidocs.rnd.mendix.com/8/runtime/index.html) 或在您安装的 Mendix 目录中(例如， *C:\Program Files\Mendix\8.0.0\r取消时间\javadoc*)。
{{% /报警 %}}

当你导入你的项目到 Eclipse 时，这个库会自动添加到你的库中，它被称为 *mxruntime.jar*。

关于使用情况和示例的详细信息，请参阅 [如何使用 Java API](/howto8/logic-business-rules/java-api-tutorial)。

## 4 正在打开 HTTP 连接

大多数云基础设施服务(包括Mendix Cloud使用的服务)如果没有流量几分钟，将自动关闭HTTP连接。 即使您的活动仍在等待回复。 这意味着，如果您的活动调用了一个需要很长时间才能响应的网络服务， 您的活动不会收到响应，连接可能会被关闭， 而是被卡住等待无限期地等待数据到达。

因此，您应该确保您在自定义Java 代码中设置任何连接的超时。

## 5 使用 Eclipse 作为环境写入Mendix Java 操作

关于此主题的详细信息，请参阅 [使用 Eclipse](using-eclipse)。

## 6 个此类别中的主要文档

* [疑难解答](troubleshooting) -- 呈现问题的 JAR 文件和工作区
* [使用 Eclipse](using-eclipse) — 描述如何使用 Eclipse 在您的 Mendix 应用程序中写入和调试Java 操作
