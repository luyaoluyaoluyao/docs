---
title: "发布的REST 操作"
parent: "已发布的rest-service"
menu_order: 10
description: "配置已发布的 REST 操作的选项。"
tags:
  - "发布的REST"
  - "操作"
  - "方法"
  - "路径"
  - "示例位置"
  - "映射"
  - "操作参数"
  - "如何处理"
---

{{% alert type="info" %}}

这个功能是在版本7.10.0中引入的。

{{% /报警 %}}

## 1 导言

已发布的REST 操作是 [已发布REST 资源](published-rest-resource) 的一部分，定义了客户端可以调用的端点， 计算、发布、修补或删除资源中的项目。

此文档描述了通过 *添加资源* 弹出对话框配置REST 操作时的选项。

## 2 概况

### 2.1 方法

方法指定了微流程执行的操作类型：

* 'GET' - 操作在指定位置检索条目或条目
* 'PUT' - 该操作在指定位置替换条目或条目，如果它们不存在，它将创建它们。
* 'POST' - 该操作在指定位置的收藏中创建一个条目
* 'PATCH' - 在指定位置的操作更新(部分)
* 'DELETE' - 操作会删除在指定位置的条目或条目
* 'HEAD' - 操作检索关于在指定位置输入或条目的信息； 这与 _GET_, 除非它不返回消息内容
* '选项' - 操作返回关于可用通信选项的信息

### <a name="operation-path"></a>2.2 操作路径

可以到达操作的地点从资源的位置开始。

操作路径指定了操作的剩余位置。 您可以留空使用资源的位置。

您可以使用 [路径参数](published-rest-path-parameters) 来捕获部分位置作为微流程参数或导入映射的参数。 在 '{' and '} '之间的操作路径中指定路径参数。 路径参数位置的 URL 中的任何内容都会传递到微流程或导入映射。

方法和操作路径确定 [为给定请求 URL](published-rest-routing) 执行了哪些操作。

### <a name="example-location"></a>2.3 示例位置

示例位置提供了一个可以达到操作的 URL 的示例。 它显示路径参数和查询参数值作为'{' and '} '之间的占位符。

### 2.4 微流

{{% alert type="info" %}}

在这些微流程中支持 **文件文档** 是在版本 7.13.0 中引入的。

{{% /报警 %}}

一个操作有不同的参数：

 * [路径参数](published-rest-path-parameters), 它们是URL路径的一部分
 * [查询参数](published-rest-query-parameters)，其形式为 `的 URL 末尾？ ame1=value1&name2=value2` (当微流程参数不在路径中且不是对象时，它被视为查询参数)
 * 源自请求的 HTTP 头参数
 * 正文参数(可选)，它在操作的请求正文中 (“GET”) 'HEAD'和'DELETE'操作没有物体参数)。 只有实体参数可以有 *List* 或 *对象* 类型。

一个操作的微流程将这些操作参数作为输入。

一个 *list* 或 *对象* 类型的微流程参数表示一个物体参数。 您可以指定导入映射来转换 JSON 或 XML。 如果参数是文件或从文件继承，则不需要导入映射。

操作微流也可能需要一个 [HttpRequest](http-request-and-response-entities#http-request) 参数。 如果您想要查看请求的 URL 和标题，您可以添加此参数。

要设置状态代码、理由短语和信头， 您应该添加 [HttpResponse](http-request-and-response-entities#http-response) 对象参数，并设置该对象的属性， 或返回 *HttpResponse*

微流的结果是操作的结果。 你在这里有几个选项，这些选项描述如下。

第一个选项是 ***返回一个 *邮件列表* 或一个 ***对象******。 您需要指定导出映射才能转换为 XML 或 JSON 。

第二个选项是 **返回一个原始的**。 当您的微流程返回一个字符串、整数、Boolean等时，对操作的响应将是这个值。 如果您从microflow返回一个非空值, *HtpResponse* 对象的 *内容* 属性将被忽略。 If you return an empty value from the microflow, then the *Content* of the *HttpResponse* is taken as the result.

第三个选项是 **返回一个文件文档**。 当你想要返回一个文件的数据(例如PDF或图片), 然后，您可以让您的微流程返回一个文件文档。

最后一个选项是 **返回一个 [HttpResponse](http-request-and-response-entities#http-response)**。 在 *HttpResponse*中，您可以设置状态代码、理由短语和内容(作为字符串)。 例如，您可以用另一个源的映射或字符串的结果来填充内容。 您也可以在响应中添加头部。 要设置的一个重要标题是 *Content-Type*。 不返回 *空* *HttpResponse*，因为这将永远导致错误。

如果微流程丢失了一个未处理的异常，响应是 **500: 内部服务器错误**。

如果启用了安全性，那么微流程需要至少配置一个角色才能访问。

### 2.5 废弃的

如果选中此框，操作将在服务的 [OpenApi (Swagger) 文档页](published-rest-services#interactive-documentation) 中标记为已弃用。 这让客户不再使用它。

### 2.6 参数

{{% alert type="info" %}}

这项功能是在第7.12.0版中引入的。

7.17.0 版本引入了编辑参数的能力

{{% /报警 %}}

In this list, you can add, update or delete the [parameters of the operation](published-rest-operation-parameter).

<a name="import-mapping"></a>

### 2.6.1 进口映射

{{% alert type="info" %}}

这一特点在第7.14.0版中引入。 使用导入映射参数在 7.17.0 版本中引入了导入映射。

{{% /报警 %}}

对于实体参数，您可以选择一个 [导入映射](import-mappings) 将请求的正文转换为对象。 除了文件外，所有对象和列表参数都必须选择导入映射。 若要选择导入映射，请双击参数或在选择参数后点击 **编辑网格中的**。 当选择导入映射时，您也可以选择映射的提交行为。 您可以选择提交、提交或不提交导入对象。

您可以选择一个不需要参数的导入映射，或者一个导入映射使用原始参数(字符串、整数、等)。 If you select an import mapping with a primitive parameter, you need to have exactly one [path parameter](published-rest-path-parameters) with the same type. 该路径参数将传递到导入映射中。

You can indicate what should happen **if no object was found** when the import mapping has checked the box **decide this at the place where the mapping gets used**.

如果您选择同时支持 XML 和 JSON 的导入映射(e.g. 一个基于消息定义的映射，然后该操作将能够同时处理XML和JSON请求。

有效请求需要包含 *Content-Type* 标题。 请参阅下面 [表 1: 已识别的介质类型](#table1) , 以了解导入映射的介质类型列表。 如果使用不支持的内容类型，操作将导致一个“400个错误请求”响应。

导入映射也用于生成操作响应的对象方案在 [OpenAPI (Swagger) 文档页](published-rest-services#interactive-documentation) 基于 [JSON Schema](published-rest-service-json-schema)

### 2.7 答复

{{% alert type="info" %}}

对 **导出映射和模型的 OpenAPI (Swagger)** 的支持已在 7.14.0 中添加。

{{% /报警 %}}

这显示有关操作响应的信息。 您可以看到微流结果的类型以及应用到它的导出映射(如果有)。

#### 2.7.1 Type

这显示微流的结果类型。

#### 2.7.2 出口映射

当微流程返回对象或对象列表时，您需要指定此结果如何映射到 JSON 或 XML。 选择导出映射，将微流结果作为输入。

如果您选择同时支持 XML 和 JSON 的导出映射（例如，基于消息定义的映射）， 然后输出取决于微流是否有类型 *System的参数。 ttpResponse* 并添加 *Content-Type* 标题。 这些都是可能出现的情况：

* 当microflow 设置为 *Content-Type* header的媒体类型为 XML (见 [Table 1: Recognized media types](#table1)), 然后操作返回 XML
* 当微流设定 *Content-Type* 头到其他东西时，操作返回 JSON
* 当微流没有设置 *Content-Type* header, 然后通过检查 *接受请求中的标题* 来确定输出：第一个媒体类型被理解为XML或JSON(见 [表1：公认的媒体类型](#table1)) 决定操作结果， 和 *内容类型* 为 *application-xml* (当它是 XML) 或 *application-json* (当它是 JSON)
* 当没有 *时，接受* 头或 *接受* 头不包含可识别的媒体类型 然后操作返回 JSON ， *Content-Type* 为 *application/json*

| 媒体类型           | 已确认为 |
| -------------- | ---- |
| *应用程序/xml*     | XML  |
| *text/xml*     | XML  |
| *+xml* 结尾的任何内容 | XML  |
| *应用程序/json*    | JSON |
| 任何结尾为 *+json*  | JSON |

<a name="table1"></a>**表1: 公认的媒体类型**

导出映射也用于生成操作响应在 [OpenAPI (Swagger) 文档页](published-rest-services#interactive-documentation) 基于 [JSON schema](published-rest-service-json-schema) 的对象方案。

## 3 公开文档

公共文档被用于服务的 [OpenAPI (Swagger) 文档页](published-rest-services#interactive-documentation) 中。

### <a name="summary"></a>3.1 Summary

摘要简要介绍了操作的情况。

### <a name="description"></a>3.2 描述

描述提供了操作的完整概览。 您可以使用 [GitHub-flavered markdown](gfm-syntax) 作为丰富文本。

## 4 个示例

**如何使用Mendix 本地发布REST**

{{% youtube HzrFkv0U4n8 %}}
