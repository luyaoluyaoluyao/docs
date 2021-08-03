---
title: "错误事件"
parent: "事件"
menu_order: 3
tags:
  - "studio pro"
  - "错误事件"
  - "事件"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/error-event.pdf)。
{{% /报警 %}}

{{% alert type="info" %}}
此事件只能在 **微流** 中使用。
{{% /报警 %}}

## 1 导言

一个错误事件定义了微流将停止哪里并抛出之前发生的错误。 如果您调用微流，您可能想知道微流中是否发生任何错误。 这个事件再次造成错误，微流的呼叫者可以捕获它们。 您可以控制当前事务中所有数据库操作是否将被回滚。

For more information on error handlers and their settings in microflows, see the [Error Handlers](#errorhandlers) subsection of [Handling Errors in Microflows](#errors-in-microflows), below. 更多关于 nanoflows 错误处理程序及其设置的信息在 [处理错误的 [错误处理程序](#errorhandlers-nano) 分节中在 Nanoflows](#errors-in-nanoflows)和 以下：

链接一个错误事件和一个带有 [序列流程](sequence-flow) 设置的错误处理器的活动。

{{% alert type="warning" %}}
您只能在范围内发生错误时使用错误事件：Studio Pro 不接受，如果您将正常执行流连接到一个错误事件， 因为回到呼叫者时不会有错误。
{{% /报警 %}}

在此示例中，将对象提交数据库时发生错误。 它已被抓住，流量将继续到错误传回微流调用者时的错误事件。 所以您可以在多个级别实现您的错误处理。

![](attachments/events/error-event.png)

{{% alert type="info" %}}
在添加一个错误事件时，您需要在错误事件之前添加一个 [错误处理程序](#errorhandlers) 。 并选择 **设置为错误处理程序** 作为序列流程。
{{% /报警 %}}

## 2 处理微流{#errors-in-microflows}

当微流发生错误时，对对象的所有更改都会回滚，微流被中止。 Optionally, you can [handle errors](/howto8/logic-business-rules/set-up-error-handling) in the microflow itself by configuring different error handling settings. 您甚至可以通过查看预定义的对象 `$latestError` 和 `$latestSoapFault` 查看错误的细节。

### 2.1 错误处理 {#errorhandlers}

错误处理程序可以设置在微流程活动、决策或循环上。

对于一个活动或决定，您有三个选项：

*   **Rollback** (default)
*   **自定义回滚功能**
*   **自定义但不回滚。**

对于后两个选项，您可以从方块中绘制额外的流程，并将此流程标记为错误处理流程。 当选择“自定义回滚”时，当发生错误时它会触发此路径，然后继续回滚。 “自定义无回滚”选项不会回滚对象。 当您选择一个流程作为错误处理程序后，它将显示在下面的图像中。 错误处理仅为单个操作指定的。 The "without rollback" in the **Custom without rollback** option is only targeted at the action itself, not the error handling. 因此在 **带回滚** 和 **之间存在着轻微的差异，不带回滚的自定义** 抛出相同的异常或在错误处理器中的另一个异常。 在后一种情况下，您仍然可以访问您创建的数据库对象，直到错误处理程序结束。

![](attachments/events/custom-without-rollback-microflows.png)

在一个循环中，你会得到两个选项：

*   Rollback (default)
*   继续

继续选项意味着当发生错误时，循环将继续进行下一次迭代。 它将在循环的退出流程中以连续图标显示。

![](attachments/events/error-event-loop.png)

### 2.2 检查错误

当微流中发生错误时，当发生错误时，产生了 Java 异常，其中含有发生错误的信息。 在自定义错误处理程序内(如在错误处理流程之后)， 您可以检查此 Java 异常的类型以及其他一些属性。 每个微流都包含两个预定义的错误对象， `$latestError` 和 `$latestSoapFault`。 `$latestError` 是实体系统错误的对象, `$latestSoapFault` 是实体系统的对象, 是系统错误的专业化.

在一个自定义错误处理程序中，错误发生后执行， `$latestError` 被设置为包含错误信息的对象。 如果错误是一个 SOAP 故障（因网络服务通话而发生的错误）， `$latestSoapFault` 设置为包含更多关于SOAP 错误的具体信息的对象。 否则， `$latestSoapFault` 是 `空的`。

{{% alert type="info" %}}
您可以通过检查 `$latestSoapFault` 为 `空的` 来确定一个错误是否为 SOAP 错误。
{{% /报警 %}}

下表显示System.Error 和 System.SoapFault的属性。

| 实体               | 属性        | 类型  | 描述               |
| ---------------- | --------- | --- | ---------------- |
| 系统错误             | ErrorType | 字符串 | 发生错误的 Java 异常类型。 |
| 系统错误             | 留言        | 字符串 | Java 异常的消息。      |
| 系统错误             | 堆栈跟踪      | 字符串 | Java 异常的堆栈。      |
| System.SoapFault | 代码        | 字符串 | SOAP 错误代码元素。     |
| System.SoapFault | 原因        | 字符串 | SOAP 错误的原因。      |
| System.SoapFault | 节点        | 字符串 | SOAP 错误的节点元素。    |
| System.SoapFault | 作用        | 字符串 | SOAP 的角色元素错误。    |
| System.SoapFault | 细节        | 字符串 | SOAP 错误的详细元素。    |

Click [here](http://www.w3.org/TR/soap12-part1/#soapfault) for more information on SOAP faults.

{{% alert type="warning" %}}
在应用实体访问权限的微流中，出于安全原因无法检查错误对象的属性。 您可以将错误对象传递给不应用实体访问并检查其属性的子微流程。
{{% /报警 %}}

## 3 处理Nanoflows{#errors-in-nanoflows}

当赤纬发生错误时，对对象所作的更改不会回滚，nanoflow 被中止。 可选，您可以通过配置一个错误处理器来处理nanoflow本身的错误。 您可以通过查看 `$latestError` 预定义变量查看错误的细节。

### 3.1 错误处理 {#errorhandlers-nano}

除网关和循环外，所有nanoflow 元素都支持错误处理程序。 有两个错误处理选项：

*  **中止** (这是默认值)
*  **自定义但不回滚。**

使用 **自定义无回滚** 选项。 您可以从方块中绘制额外的流程，然后将此流程标记为错误处理流程。 **不带回滚** 选项不会回滚物体。 当您选择一个流作为错误处理程序后，它将以此方式出现：

![选择的错误处理程序](attachments/events/custom-without-rollback-nanoflows.png)

### 3.2 错误检查

在错误发生后执行的自定义错误处理器中， `$latestError` 变量设置为错误信息的消息。 `$latestError` 变量类型是 `字符串`，不像于 [微流](microflows) 错误类型是 `System.Error` 实体。

`$latestSoapFault` 变量在 nanoflow 中不可用。
