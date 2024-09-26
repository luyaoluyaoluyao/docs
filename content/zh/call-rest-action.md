---
title: "通话REST 服务"
parent: "一体化活动"
tags:
  - "studio pro"
  - "集成活动"
  - "呼叫休息服务"
menu_order: 10
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/call-rest-action.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动只能在 **微流** 中使用。
{{% /报警 %}}

## 1 导言

**通话REST 服务** 活动可用来调用REST 端点。 您可以指定应如何处理REST 调用响应的位置。

## 2 属性

下面的图像显示了呼叫休息动作属性的示例：

![调用休息动作属性](attachments/integration-activities/call-rest-action-properties.png)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

呼叫休息动作属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动部分{#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

属性对话框由四个标签组成：

* [A. 概况](#general)
* [HTTP 头](#http-headers)
* [请求](#request)
* [答复](#response)

## 4 个常规标签 {#general}

![](attachments/integration-activities/general-tab.png)

### 4.1 地点

**位置** 属性定义了要调用的 REST 端点。

该位置需要输入一个字符串模板，该字符串必须导致一个有效的 URL 字符串。

#### 4.1.1 字符串模板{#string-template}

位置模板可以包含以数字写在括号之间的参数 (例如， `{1}`)。 第一个参数的数字是 `1`, 第二个 `2`, 等等。 You can escape the opening brace (`{`), by using a double opening brace (`{{`).

#### 4.1.2 参数

对于模板中的每个参数，您可以使用 [微流程表达式](expressions) 来指定其值，并产生一个字符串值。 此值将插入参数的位置。

### 4.2 HTTP方法

**HTTP 方法** 属性定义了调用REST 端点时要使用的 HTTP 方法。 可能的值是：GET、POST、PUT、PATCH、DELETE、HEAD和OPTIONS。

### 4.3 应请求使用超时

设置 **在请求时使用超时** 到 **是的，** 可以指定通话REST 活动应该等待多长时间才能响应REST 端点。

{{% alert type="warning" %}}
建议您将此设置保持为 **是**。 大多数云基础设施服务(包括Mendix Cloud使用的服务)如果没有流量几分钟，将自动关闭HTTP连接。 即使您的活动仍在等待回复。 这意味着，如果您的活动调用了一个需要很长时间才能响应的网络服务， 您的活动不会收到回复，连接可能会被关闭。 在这种情况下，如果 **根据请求** 使用超时设置为 **no**, 您的活动将被卡住，无限期等待数据到达。
{{% /报警 %}}

默认值： *是* (as of Studio Pro [8.5.0](/releasenotes/studio-pro/8.5#850); 在较早的版本中，默认值为 否)

### 4.4 超时时间

如果REST 端点在 **超时秒数(s)**之后还没有响应， 将发生异常，微流将回滚或转到您的自定义错误处理器。

默认值： *300秒* (as of Studio Pro [8.5)](/releasenotes/studio-pro/8.5#850); 在较早的版本中， **请求时使用时间值** 否)

### 4.5 代理配置

在几乎所有情况下，您都可以忽略此设置。 **使用工程设置** 是一个好的默认值。

如果想要，您可以配置是否为请求使用代理人。 这些选择是：

* **使用项目设置** - 使用项目一级定义的任何设置 (默认)
* **覆盖** - 此操作的项目级别设置
* **没有代理** - 即使在项目一级配置了代理，也不使用代理服务器

当您选择 **覆盖**，您可以动态地配置是否使用代理人。 然后您为代理提供主机、 端口、 用户名和密码设置。

### 4.6 客户证书

{{% alert type="warning" %}}
此功能在 Mendix 8.18.0 及以后可用。
{{% /报警 %}}

在大多数情况下，默认使用 **使用工程设置**。

然而，您可以单击 **覆盖** 来指定用于请求的客户端证书。 从以下选择之一：

* **使用工程设置**(默认) - 使用项目级别上定义的设置
* **覆盖** - 此操作的项目级别设置

当您选择 **覆盖**，您可以配置将使用的客户端证书。 点击 **编辑** 以指定 **客户端证书标识符**。 这个标识符可以在不同的地方设置，取决于您在哪里部署应用程序：

* 当你将应用程序部署到Mendix 云端时，当 [固定客户端证书](/developerportal/deploy/certificates#outgoing-client-certificates) 时设置了标识符
* 当您在其他地方部署应用时，标识符将设置在自定义设置 [ClientCertificateUsages](custom-settings#ca-certificates)

当此标识符未被设置(在 _ClientCertificateUsages_中未置顶或不存在) 默认设置将被使用(如 **使用项目设置** 被选中)。

## 5 HTTP 头标签 {#http-headers}

![](attachments/integration-activities/http-headers-tab.png)

### 5.1 使用 HTTP 身份验证

**使用 HTTP 身份验证** 复选框定义了是否应使用基本身份验证。

### 5.2 用户名

**用户名** 属性定义了将用于认证HTTP的用户名。 用户名需要使用 [微流程表达式](expressions) 输入. 微流程表达式应产生一个字符串。

### 5.3 密码

**密码** 属性定义了将用于通过 HTTP 身份验证的密码。 密码需要使用 [表达式](expressions) 输入. 微流程表达式应产生一个字符串。

### 5.4 自定义 HTTP 头

这些信头已添加到 HTTP 请求头中。 每个自定义头都是一个键值和值(微流程表达式)。

## 6 个请求选项卡 {#request}

![](attachments/integration-activities/request-tab.png)

下面的部分描述了下拉菜单中生成请求的选项。

{{% alert type="info" %}}
只能为 HTTP 方法 POST、PUT、PATCH和OPTIONS 生成请求。
{{% /报警 %}}

### 6.1 整个请求的导出映射

此选项允许您为请求的正文使用单个 [导出映射](export-mappings)。

#### 6.1.1 映射

选择您想要应用的映射。

#### 6.1.2 参数类型

如果 [导出映射](export-mappings) 需要输入，此字段显示输入的类型。

#### 6.1.3 参数

如果 [导出映射](export-mappings) 需要输入，您可以选择正确类型的参数。

#### 6.1.4 内容类型

如果 [导出映射](export-mappings) 基于消息定义，它可以导出XML 或 JSON 。 选择您想要的输出类型。

{{% alert type="info" %}}
**Content-Type 标题** 未设置为默认值。 要设置它，请使用 **自定义 HTTP 头** 标签。
{{% /报警 %}}

### 6.2 整个请求的二进制文件

此选项允许您发送二进制数据(例如，文件文档的内容)。

### 6.3 表单数据

此选项允许您为多个部分生成多部分/表单数据请求。 每个部件都是配对的键值和值(微流程表达式)。

当在微流程表达式中用作变量时，此选项也支持文件和图像。

#### 6.3.1 Content Type

为表格数据请求设置 **Content-Type 标题** 将导致一致性错误， 因为它将自动设置为 **multipart/form-data**

FileDocument 部件的内容类型是 **application/ octet-stream**。

### 6.4 自定义请求模板

此选项允许您使用字符串模板生成请求。 模板以纯文本定义请求的结构。

更多关于从模板构建字符串的信息，请参阅上面 [字符串模板](#string-template)。

## 7 响应选项卡 {#response}

![](attachments/integration-activities/response-tab.png)

### 7.1 反应处理

这些是下拉菜单中处理响应的选项：

* **应用导入映射** - 如果响应是 JSON 或 XML， 它可以通过 [导入映射](import-mappings)直接转换为对象。 您可以在此选择的字段在 [导入映射操作](import-mapping-action) 中描述
* **存储在 HTTP 响应** - 任何成功的 HTTP 响应都可以直接存储在 [HtpResponse](http-request-and-response-entities#http-response) 对象中， 并且 [$latestHttpResponse](#latesthttpresponse) 变量也被更新
* **存储在文件** - 如果响应包含二进制内容 (例如) a PDF, 它可以存储在继承自 `System的实体类型的对象。 文件`
* **存储在字符串** - 如果响应是字符串(例如，CSV)，它可以直接存储在字符串变量中
* **不要存储变量** - 当调用没有返回任何有用的情况下使用此选项

### 7.2 类型

**类型** 字段定义了输出类型。

### 7.3 变量

**变量** 字段定义了操作结果的名称。

### 7.4 存储消息正文在 $latestHttpResponse 变量中 {#latesthttpresponse}

如果HTTP 响应状态代码不成功(例如， `[4xx]` 或 `[5xx]`), 流程将在一个 [错误处理器](error-event#errorhandlers) 中继续。

{{% alert type="warning" %}}
您应该始终为 [调用 REST 服务](/refguide8/call-rest-action) 行动添加一个错误处理程序。
{{% /报警 %}}

## 8 通用部分{#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}
