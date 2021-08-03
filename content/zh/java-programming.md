---
title: "Java 程序"
description: "描述如何使用 Mendix Java 库并使用 Eclipse 作为环境写入您的 Mendix Java 动作。"
tags:
  - "studio pro"
---

## 1 导言

通过 Java 动作，您可以在微流中很难实现此功能的情况下扩展您应用程序的功能。

Studio Pro中关于Java 操作的信息，请参阅 [Java 操作](java-actions)。

## 你的 Java 操作的 .java 文件写入代码

在 *中。 您的 Java* 文件中的 Java 动作。 方法 `executeAction` 在执行 Java 操作时被Mendix Runtime 调用。 这种方法会产生所有例外情况。 这意味着您可以在调用此 Java 动作的微流程中处理错误。 如果您想要在操作中执行自己的错误处理，请使用 `尝试` / `捕获` 语句。

行 `// BEGIN USER CODE` and `// END USER CODE`, 您可以写自定义代码，在执行操作时总是被调用。 您可以在 `// BEGIN EXTRA CODE` and `/ END EXTRA CODE` 之间的部分调用其他方法。

当你部署你的模型时，每次都会生成块外的代码，因此你对它们所作的任何修改都会被覆盖。 然而，您的进口将被保存。

```java
// 此文件由 Mendix Studio Pro生成。
//
// 警告: 只有以下代码将在重新生成操作时保留：
// - 导入列表
// - BEGIN UER CodDE 和 END USER CodDE 之间的代码
// - BEGIN EXTRA CodE 和 END EXTRA CDE
// 其他代码下次部署项目时会丢失。
/ 在评论中支持特殊字符，例如e2001、oTRIP、aasset等。

package myfirstmodule.actions;

import com.mendix.systemwideinterfaces.core.IContext;
import com.mendix.webui.CustomJavaAction;

public class JavaAction_1 extends CustomJavaAction<java.lang.Void>
{
    public JavaAction_1(IContext context)
    {
        super(context);
    }
    @java.lang.Override
    public java.lang.Void executeAction() throws Exception
    {
        // BEGIN USER CODE
        return true;
        // END USER CODE
    }
    /**
     * Returns a string representation of this action
     */
    @java.lang.Override
    public java.lang.String toString()
    {
        return "JavaAction_1";
    }

    // BEGIN EXTRA CODE
    // END EXTRA CODE
}
```

## 3 使用 Mendix Java 库

您可以在 Java 代码中使用Mendix Java 库，为您的 Java 操作写入。

{{% alert type="info" %}}
您可以在 [Runtime API](/apidocs-mxsdk/apidocs/runtime-api) 或目录Studio Pro 中找到Javadoc (例如) *C:\Program Files\Mendix\9. 0\r非时间\javadoc*
{{% /报警 %}}

当您导入应用程序到 Eclipse 时，这个库会自动添加到您的库中，它被称为 *mxruntime.jar*。

关于使用情况和示例的详细信息，请参阅 [如何使用 Java API](/howto/logic-business-rules/java-api-tutorial)。

## 4 正在打开 HTTP 连接

大多数云基础设施服务(包括Mendix Cloud使用的服务)如果没有流量几分钟，将自动关闭HTTP连接。 即使您的活动仍在等待回复。 这意味着，如果您的活动调用了一个需要很长时间才能响应的网络服务， 您的活动不会收到响应，连接可能会被关闭， 而是被卡住等待无限期地等待数据到达。

因此，您应该确保您在自定义Java 代码中设置任何连接的超时。

## 5 使用 Eclipse 作为环境写入Mendix Java 操作

关于此主题的详细信息，请参阅 [使用 Eclipse](using-eclipse)。

## 6 个此类别中的主要文档

* [疑难解答](troubleshooting) -- 呈现问题的 JAR 文件和工作区
* [使用 Eclipse](using-eclipse) — 描述如何使用 Eclipse 在您的 Mendix 应用程序中写入和调试Java 操作
