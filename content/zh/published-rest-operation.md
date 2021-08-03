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
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/published-rest-operation.pdf)。
{{% /报警 %}}

## 1 导言

已发布的REST 操作是 [已发布REST 资源](published-rest-resource) 的一部分，定义了客户端可以调用到GET的端点， PUT、POST、PATCH或从资源中删除项目。

在 **已发布的REST Service** 文档中，您可以将要包含在服务中的项目添加为 **Resources**：

![发布的REST 服务](attachments/published-rest-operation/publshed-rest-service.png)

## 2 操作定义

当您 **添加** 或 **编辑资源** 时， 您可以在 **操作** 定义对话框中定义选中项的资源如下：

![REST 操作](attachments/published-rest-operation/operation-definition.png)

### 2.1 概况

在 **常规** 标签中，您可以输入此部分描述的操作细节。

#### 2.1.1 方法

该方法指定了通过微流执行的操作类型。 从下拉菜单中您可以选择以下一种：

* **获取** - 在指定位置检索条目或条目
* **PUT** — — 替换在指定位置的条目或条目，如果它们不存在，则创建它们。
* **POST** — — 在指定位置在集合中创建一个条目
* **PATCH** — — 更新 (部分) 条目在指定位置
* **删除** - 删除在指定位置的条目或条目
* **HEAD** - 检索在指定位置的条目或条目信息； 这与 **GET**完全相同，但没有返回消息内容
* **选项** - 返回关于可用通信选项的信息

#### 2.1.2 操作路径{#operation-path}

可以达到操作的位置始于资源的 URL 和 **操作路径** ，指定了操作的其余路径。 您可以留空使用资源的位置。

您可以使用 [路径参数](published-rest-path-parameters) 来捕获部分位置作为微流程参数或导入映射的参数。 在操作路径中指定路径参数，介于 `named@@` and `}` 之间。 路径参数的 URL 中的值将传递到微流或导入映射。

**方法** and **操作路径** 定义了在 [发布的路由](published-rest-routing) 中为给定请求的 URL 执行的操作。

#### 2.1.3 示例位置{#example-location}

**示例位置** 提供了一个可以达到操作的 URL 的示例。

#### 2.1.4 微流

一个操作可以有以下参数：

 * [查询参数](published-rest-query-parameters), 正处于URL结尾的形式 `?name1=value1&name2=value2`
   {{% alert type="info" %}}
   当微流参数不在路径中且不是对象时，它被视为查询参数。
   {{% /报警 %}}
* [路径参数](published-rest-path-parameters)，它是URL 路径的一部分
* 正文参数(可选)，它在请求操作的正文中
   {{% alert type="info" %}}
   **GET**, **HEAD**, 和 **DELETE** 操作没有物体参数。
   {{% /报警 %}}
* 源自请求的 HTTP 头参数
* 一个表单参数(可选)，它是多部分形式请求正文的一部分

一个操作的微流程将这些操作参数作为输入。

包含 *List* 或 *对象* 类型的微流程参数表示一个物体参数。 您可以指定导入映射来转换 JSON 或 XML。 *FileDocument* 类型(或继承自 *FileDocument*)的参数是特殊的：它也可以用于表单参数， 并且不需要导入映射。

操作微流也可能需要一个 [HttpRequest](http-request-and-response-entities#http-request) 参数。 如果您想要查看请求的 URL 和头部，您可以添加此参数。

要设置状态代码、理由短语和信头， 添加 [HttpResponse](http-request-and-response-entities#http-response) 对象参数并设置该对象的属性，或返回 *HttpResponse*。

微流的结果是操作的结果，可包括：

1. **返回** ***列表*** **或一个** ***对象***- 您必须指定导出映射才能将其转换为 XML 或 JSON
2. **返回原始** - 当微流程返回值时，例如： 一个字符串，整数或布尔值，然后对操作的响应将是这个值。
   {{% alert type="info" %}}
   如果返回来自微流的非空值，则忽略 *HtpResponse* 对象的 *内容* 属性。 If an empty value from the microflow is returned, then the *Content* of the *HttpResponse* is taken as the result.
   {{% /报警 %}}
3.  **返回一个文件** - 当你想要返回一个文件的数据(例如PDF或图片), 然后，微流程返回文件文档。
4. **返回** [HttpResponse](http-request-and-response-entities#http-response) - 在 *HttpResponse*您可以设置状态代码、理智短语和内容(作为字符串)。 例如，您可以用另一个源的映射或字符串的结果来填充内容。 您也可以在响应中添加头部。
   {{% alert type="info" %}}
   要设置的一个重要标题是 *Content-Type*。 不返回 *空* *HttpResponse* ，因为这将永远导致错误。
   {{% /报警 %}}

如果微流程丢失了一个未处理的异常，响应是 **500: 内部服务器错误**。

当启用安全性时，微流需要至少配置一个角色才能访问。

#### 2.1.5 废弃的

选中此框以标记该操作在服务的 OpenApi (Swagger) 文档页面中已被废弃，正如 [发布的REST 服务](published-rest-services) 部分 [描述的](published-rest-services#interactive-documentation)。 这通知客户端不再使用它。

#### 2.1.6 参数

您可以 **添加**， **更新** 或 **删除** [发布的REST 操作参数](published-rest-operation-parameter)

##### 2.1.6.1 进口映射 {#import-mapping}

对于实体参数，您可以选择一个 [导入映射](import-mappings) 将请求的正文转换为对象。 除文件外，所有对象和列表参数必须选择导入映射。

若要选择导入映射，请双击参数或在选择参数后点击 **编辑网格中的**。 当选择导入映射时，您也可以选择映射的提交行为：您可以选择要么提交， 不提交事件或不提交导入的对象。

您可以选择一个不需要参数的导入映射，或者一个导入映射使用原始参数(例如字符串、整数)。 If you select an import mapping with a primitive parameter, you need to have exactly one [path parameter](published-rest-path-parameters) with the same type. 该路径参数将传递到导入映射中。

You can indicate what should happen **if no object was found** when the import mapping has checked the box **decide this at the place where the mapping gets used**.

如果您选择同时支持 XML 和 JSON 的导入映射(例如) 一个基于消息定义的映射，然后该操作将能够同时处理XML和JSON请求。

有效请求必须包含 *Content-Type* header。 请参阅 [公认的介质类型](#table1) 以获取导入映射所理解的介质类型列表。 如果使用不支持的内容类型，操作将产生一个 "**400 错误请求**" 响应。

导入映射也用于生成操作响应的对象方案在 [OpenAPI (Swagger) 文档页](published-rest-services#interactive-documentation) 基于 [JSON Schema](published-rest-service-json-schema)

#### 2.1.7 答复
这定义了操作的响应。 您可以指定微流结果的类型以及对它的导出映射(如果有的话)。

##### 2.1.7.1 Type
这显示微流的结果类型。

##### 2.1.7.2 出口映射
当微流程返回对象或对象列表时，您必须指定此结果如何映射到 JSON 或 XML。 选择导出映射，将微流结果作为输入。

如果您选择同时支持 XML 和 JSON 的导出映射(例如，基于消息定义的映射)， 然后输出取决于微流是否有类型 *System的参数。 ttpResponse* 并添加 *Content-Type* 标题。 可能出现的情况如下：

* When the microflow sets the *Content-Type* header parameter with a media type that is XML, then the operation returns XML as given in the table below.

    <a name="table1">**识别的媒体类型**</a>

    | 媒体类型           | 公认为  |
    | -------------- | ---- |
    | *应用程序/xml*     | XML  |
    | *text/xml*     | XML  |
    | *+xml* 结尾的任何内容 | XML  |
    | *应用程序/json*    | JSON |
    | 任何结尾为 *+json*  | JSON |

* 当微流设定 *Content-Type* 头到其他东西时，操作返回JSON。

* 当微流没有设置 *Content-Type* header, 然后通过检查 *接受请求中的* 页眉来决定输出。 被识别为 XML 或 JSON 的第一个媒体类型(如上文表中给出的那样)决定了操作结果： *Content-Type* 是 *application/xml* (当它是 XML) 或 *application/json* (当它是 JSON 时)。

* 当没有 *时，接受* 头或 *接受* 头不包含可识别的媒体类型 然后操作返回 JSON ， *Content-Type* 为 *application/json*

导出映射也用于生成操作响应在 [OpenAPI (Swagger) 文档页](published-rest-services#interactive-documentation) 基于 [JSON schema](published-rest-service-json-schema) 的对象方案。

### 2.2 公开文件

在 **公开文档** 标签页中，您可以指定将用于服务 [OpenAPI (Swagger) 文档页面](published-rest-services#interactive-documentation) 的文档。

#### 2.2.1 Summary {#summary}
提供操作的简短说明。

#### 2.2.2 描述 {#description}
输入操作的完整概述。 您可以使用 [GitHub-flavered markdown](gfm-syntax) 语法来风格文本。

## 3 个示例

**如何在Studio Pro 8中发布REST**

{{% youtube Ff_P84NOcZk %}}

