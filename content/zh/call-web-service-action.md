---
title: "呼叫网络服务"
parent: "一体化活动"
tags:
  - "studio pro"
  - "集成活动"
  - "呼叫网络服务"
menu_order: 20
---

{{% alert type="warning" %}}
 此活动只能在 **微流** 中使用。
{{% /报警 %}}

## 1 导言

**调用 web service** 活动可以调用 [导入的 web 服务](consumed-web-services) 操作。 您可以指定是否使用身份验证， 请求应该是什么样的，以及应该如何处理网络服务的反应。

## 2 属性

下面的图像显示了通话网络服务属性的示例：

![调用 web 服务属性](attachments/integration-activities/call-web-service-properties.png)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

通话服务属性面板由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动部分{#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

属性对话框由五个标签组成：

* [操作](#operation)
* [HTTP 头](#http-headers)
* [SOAP 请求标题](#request-header)
* [SOAP 请求机构](#request-body)
* [SOAP 响应](#response)

## 4 操作选项卡{#operation}

![](attachments/integration-activities/operation-tab.png)

### 4.1 行动

**操作** 定义了被调用的 web 服务的哪些操作。

### 4.2 覆盖位置

**覆盖位置** 定义是否覆盖调用网页服务的位置。

{{% alert type="info" %}}

当使用呼叫网络服务活动调用网络服务时，网络服务的位置确定如下：

1.  如果该位置在通话网络服务活动中被覆盖，则使用该操作中指定的位置。
2.  如果定义操作的服务有一个位置常量定义，则使用该常量的值。
3.  否则，就使用了进口网络服务WSDL中指定的地点。

{{% /报警 %}}

### 4.3 地点

**位置** 定义了如果您覆盖位置的 web 服务地址。 位置需要使用 [表达式](expressions) 输入，结果是一个有效的 URL 字符串。

### 4.4 请求时使用超时

当连接后网络服务需要太长时间才能响应时，这可以用来抛出异常。 一定时间后，将会抛出异常，微流将会回滚或进入您的自定义错误处理器。

默认值： *是*

{{% alert type="warning" %}}
建议您将此设置为 **是**。 大多数云基础设施服务(包括Mendix Cloud使用的服务)如果没有流量几分钟，将自动关闭HTTP连接。 即使您的活动仍在等待回复。 这意味着，如果您的活动调用了一个需要很长时间才能响应的网络服务， 您的活动不会收到回复，连接可能会被关闭。 在这种情况下，如果 **根据请求** 使用超时设置为 **no**, 您的活动将被卡住，无限期等待数据到达。
{{% /报警 %}}

默认： *否*

### 4.5 超时

**超时** 以秒为单位指定超时值。

默认值： *300*

### 4.6 针对WSDL验证

**校验wsdl** 是否指定调用行动是否应该验证传入和传出的 XML 是否与WSDL 相对。 请注意，Mendix 生成正确的 XML ，但应用程序数据可能会导致XML 不正确(例如不能为空的字段在您正在发送的数据中是空的)。

设置此设置为是可以大大降低性能！

{{% alert type="warning" %}}
当消耗使用编码的 WSDL 时，开启验证会导致一致性错误，因为它不符合WS-I 。
{{% /报警 %}}

配置 [消费的 web 服务](consumed-web-service) 作为附件发送二进制数据时不支持Schema 验证。

默认： *否*

### 4.7 代理配置

在几乎所有情况下，您都可以忽略此设置。 **使用应用设置** 是一个好的默认值。

如果想要，您可以配置是否为请求使用代理人。 这些选择是：

* **使用应用设置** - 使用在应用级别上定义的任何设置 (默认)
* **覆盖** - 此操作的应用级别设置
* **没有代理** - 即使在应用级别上配置了代理，也不使用代理服务器

当您选择 **覆盖**，您可以动态地配置是否使用代理人。 然后您为代理提供主机、 端口、 用户名和密码设置。

### 4.8 客户端证书{#client-certificate}

在几乎所有情况下，您都可以忽略此设置。 **使用应用设置** 是一个好的默认值。

然而，您可以选择 **覆盖** 来指定用于请求的客户端证书。

这些备选办法是：

* **使用应用设置**(默认) - 使用在应用级别上定义的设置
* **覆盖** - 此操作的应用级别设置

当您选择 **覆盖**，您可以配置将使用哪些客户端证书。 点击 **编辑** 以指定 **客户端证书标识符**。 这个标识符可以在不同的地方设置，取决于您在哪里部署应用程序：

* 当您在 Mendix 云中部署应用程序时， 将 **客户端证书标识符** 设置为所需 **WEB SERVICE CALL NAME** 设置为 [固定客户端证书](/developerportal/deploy/certificates#outgoing-client-certificates)
* 当您在其他地方部署应用时，标识符将设置在自定义设置 [ClientCertificateUsages](custom-settings#ca-certificates) 中。 对于本地测试，这可以在 [配置](configuration#custom) 中设置为自定义服务器设置。

当这个标识符没有设置为您的应用部署的环境(不是固定的就是不存在于 _ClientCertificateUsages_中) 默认设置将被使用(如 **使用应用程序设置** 被选中)。

## 5 HTTP 头选项卡{#http-headers}

![](attachments/integration-activities/http-headers-tab-call-web-service.png)

### 5.1 使用 HTTP 身份验证

使用 HTTP 身份验证定义是否应使用基本身份验证。

### 5.2 用户名

用户名定义了将用于通过 HTTP 身份验证的用户名。 用户名需要使用 [表达式](expressions) 输入. 微流程表达式应产生一个字符串。

### 5.3 密码

密码定义将用于通过 HTTP 身份验证的密码。 密码需要使用 [表达式](expressions) 输入. 微流程表达式应产生一个字符串。

### 5.4 自定义 HTTP 头

这些自定义头已添加到 HTTP 请求头中。 每个自定义头都是一个键值和一个值(微流程表达式)。

## 6 个SOAP 请求头标签 {#request-header}

对于请求标题，Studio Pro 在下拉菜单中提供一些常见的 XML 结构。

## 7 SOAP 请求正文选项卡 {#request-body}

![](attachments/integration-activities/soap-request-body-tab.png)

请求部件的 XML (标题和物体) 可以多种方式生成。 以下各节将通过该页顶部的下拉列表来选择。

### 7.1 为整个请求导出映射

使用此选项可以使用单独的 [导出映射](export-mappings) 来生成请求部件的 XML。 您可以选择用于请求部分的导出映射，如果适用的话。 您想要用作映射参数的对象或列表。

### 7.2 每个请求参数的简单表达式

当请求部件的所有子元素的子元素最多发生一次并且是原始值时，可以使用此选项。 如果不是这样，此选项将被禁用，无法使用。

使用此选项需要为原始类型的所有元素(参数)提供一个参数值。 参数值需要使用 [表达式](expressions) 输入，结果产生与参数相同的数据类型。

![](attachments/integration-activities/request-parameter-option.png)

对于没有导出映射的原始参数 (可选参数和 nilble) 您可以选择通过设置 **将空值** 发送至 **是无效的** 来发送空值。

### 7.3 每个请求参数导出映射

当请求部件的 XML 元素的所有子元素最多发生一次时，此选项可以使用。 您需要为请求的所有顶级元素提供一个参数值 (参数)。 对于简单的参数，您可以输入微流表达式，对于复杂的参数，您可以定义一个映射。

{{% alert type="warning" %}}

如果原始请求参数既是可选的，也是不可靠的，那么您需要选择是否发送空值。

*默认值*: 不发送空值。

{{% /报警 %}}

### 7.4 自定义请求模板

此选项允许您使用模板为请求部分生成XML。 模板在纯文本中定义请求部分的 XML 结构。

#### 6.4.1 字符串模板{#string-template}

XML 请求的模板可以包含以数字写在括号中的参数 (例如， `{1}`)。 第一个参数的数字是 `1`, 第二个 `2`, 等等。 You can escape the opening brace (`{`), by using a double opening brace (`{{`).

#### 6.4.2 参数

对于模板中的每个参数，您可以使用 [微流程表达式](expressions) 来指定其值，并产生一个字符串值。 此值将插入参数的位置。

## 8 SOAP 响应选项卡{#response}

![](attachments/integration-activities/soap-response-tab.png)

如果数据类型是一个复杂的 XML 结构，它可以映射到使用 [导入映射](import-mappings) 的实体。 如果它是原始数据，它可以立即存储在一个变量中。 这个响应不一定要使用；如果你不感兴趣，它也可以被忽略。

### 8.1 映射

如果您正在使用复杂的 XML 结构，您可以选择 [导入映射](import-mappings) ，用于将XML 转换为对象。

### 8.2 如果没有找到对象

You can indicate what should happen **if not object was found** when the import mapping has checked the box **decide this at the place where the mapping gets used**.

### 8.3 参数

如果选中的映射需要一个参数，您可以在此选择它。

### 8.4 提交

指示是否应将所产生的对象投入数据库，以及是否应触发事件处理程序。

| 选项      | 描述                                                     |
| ------- | ------------------------------------------------------ |
| 否       | 对象已保存在数据库中，触发了 [事件处理程序](event-handlers)。               |
| 是的，没有事件 | 对象已保存在数据库中，但 [事件处理程序](event-handlers) 未触发(默认)。         |
| 否       | 对象创建时没有保存到数据库中。 您将需要 [提交操作](committing-objects) 来保存它们。 |

### 8.5 范围(如果绘图返回一个清单)

范围决定有多少对象被映射并返回.

| Range | 含义                                      |
| ----- | --------------------------------------- |
| 所有的   | 映射并返回所有对象。                              |
| 第一页   | 映射并只返回第一个对象。 该动作的结果将是单个对象而不是列表。         |
| 自定义   | 映射并返回给定数量的对象(限制)。 限制是一个微流程表达式，必须产生一个数字。 |

### 8.6 存放在变量中

选择是否将操作结果存储在一个变量、 对象或列表中。

### 8.7 类型

输出类型。

### 8.8 姓名

将保持操作结果的输出名称。

## 9 Common Section{#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}
