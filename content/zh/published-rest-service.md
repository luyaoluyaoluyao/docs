---
title: "发布的REST 服务"
parent: "已发布的rest-service"
menu_order: 10
description: "已发布REST 服务的配置选项"
tags:
  - "已发布 REST"
  - "服务"
  - "保留的 URL 前缀"
  - "swagger"
  - "安全"
  - "CORS"
  - "资源"
  - "操作"
  - "如何执行"
---

{{% alert type="info" %}}

**已发布的REST service** 功能已引入7.10.0版本。

{{% /报警 %}}

## 1 导言

使用已发布的 REST 服务来暴露您的实体和微流程到其他应用，使用REST 标准。

本文档描述在桌面模型中打开已发布的 REST 服务时显示的已发布的REST 服务配置选项。

## 2 概况

<a name="service-name"></a>

### 2.1 服务名称

服务名称独特识别应用中的服务。 它也在 [OpenAPI (Swagger) 文档页](open-api) 中显示。

初始创建服务时，服务名称用于创建服务的默认位置。 如果服务名称包含任何空格或特殊字符，它们将被服务位置中的 `_` 字符所取代。

### 2.2 版本

{{% alert type="info" %}}

**版本** 功能是在版本 7.12.0 中引入的。

{{% /报警 %}}

版本用于在 [OpenAPI (Swagger) 文档页](open-api) 中显示版本信息。 您可以在版本字段中设置任何字符串，但是它已被修正以按照 [语义版本](https://semver.org/) 方案进行操作。

默认情况下，版本设置为“1.0.0”。

<a name="location"></a>

### 2.3 地点

{{% alert type="info" %}}

**位置** 是可以在 Mendix 版本的 7.12.0 及以上编辑的。

{{% /报警 %}}

位置显示可以达到服务的 URL。

默认情况下，位置由附加服务名称和“v1”建立到"rest/"前缀。 服务名称将从无效的 URL 字符中删除；如空格和特殊字符。

示例：
```
http//localhost:8080/rest/my_service_name/v1
```

您可以将默认位置更改为几乎任何有效的 URL。

#### 2.3.1 保留前缀

以下URL前缀被保留，不允许在位置使用：

* `ws/`
* `ws-doc/`
* `rest-doc/`
* `odata/`
* `odata-doc/`
* `api-doc/`
* `xas/`
* `p/`
* `reload/`

当您的应用程序正在运行时，您可以点击位置来打开 [交互文档页面](published-rest-services#interactive-documentation)。

<a name="public-documentation"></a>

### 2.3 公开文件

公共文档被用于服务的 [OpenAPI 2.0 (Swagger) 文档](open-api) 中。 您可以使用 [GitHub-flavered markdown](gfm-syntax) 作为丰富文本。

<a name="export-swagger-json"></a>

### 2.5 导出sugger.json

要保存服务的 [OpenAPI (Swagger) 文档](open-api) 在您的机器上的某处， 只需右键点击 **Project Explorer** 中的服务并选择 **导出交换器。 son** (或只需点击 **导出swagger.json** 按钮，取决于您的 Moderr 版本)。 这是一个 [OpenAPI 2.0 文件格式](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md) 中的机器可读文件。 大多数API工具支持此格式。

当应用程序正在运行时，此文件可在 `/rest-doc/servicename/swagger.json` 下使用。

## 3 安全事务

<a name="authentication"></a>

### 3.1 需要认证

{{% alert type="info" %}}

**无身份验证** 功能是在版本 7.11.0中引入的。 在以前的版本中，它总是 **用户名和密码**。

**活动会话** 身份验证是在 7.13.0 版本中介绍的

**自定义** 身份验证是在 7.17.0 版本中介绍的

{{% /报警 %}}

选择客户端是否需要身份验证。

### 3.2 认证方法

如果需要身份验证，您可以选择您想要支持哪些身份验证方法

* 选择 **用户名和密码** 以允许客户端在 **授权中使用用户名和密码进行身份验证** (这被称为“基本认证”)
* 选择 **活动会话** 允许您当前应用程序中的 JavaScript 访问
  * 一旦用户登录到浏览器，您的应用程序中的 JavaScript 可以使用当前用户的会话访问REST 服务
  * 为了防止跨网站请求的伪造，需要在每个请求上设置 `X-Csrf-Token` 标题，例如：

    ```var xmlHttp = new XMLHttpRequest();
    xmlHttp.open("GET", "http://mysite/rest/myservice/myresource", false);
    xmlHttp.setRequestHeader("X-Csrf-Token", mx.session.getConfig("csrftoken");
    xmlHttpsend(null);
    ```
* 选择 **自定义** 来验证微流程。 每当用户想要访问资源时，这个微流程都被调用。

检查多个身份验证方法使服务尝试每个方法。 先尝试 **自定义** 身份验证，然后 **用户名和密码**然后 **活动会话**。 欲了解更多详情，请参阅 [已发布的REST Routing](published-rest-routing)。

<a name="authentication-microflow"></a>

### 3.3 微流

指定用于自定义身份验证的微流。

选择 **参数** 以查看传递给身份验证微流程的 [参数列表](published-rest-authentication-parameter)。 在该窗口中，您可以指出身份验证微流程的参数是来自请求头还是来自查询字符串。

微流可能需要一个 [HttpRequest](http-request-and-response-entities#http-request) 作为参数，所以它可以检查传入的请求。

微流也可以使用 [HttpResponse](http-request-and-response-entities#http-response) 作为参数。 当微流程将此响应的状态代码设置为其他位置时， **200**， 此值已返回，操作将不会被执行。 在响应中设置的任何头都会返回(除非微流程返回一个空用户)。

身份验证microflow 应返回用户。

认证微流有三个可能的结果
  * 当HttpResponse 参数的状态代码被设置为其它位置则为 **200**然后返回此值，操作将不会执行
  * 否则，如果由此产生的用户不是空的，该操作将在该用户的上下文中执行
  * 否则，如果结果的用户为空，则尝试下一个身份验证方法。 当没有其他身份验证方法时，结果是 **404 找不到**。

### 3.4 允许的角色

允许的角色定义用户必须能够访问服务的 [模块角色](module-role)。 此选项仅在 **需要身份验证** 设置为 **是** 时才可用。

{{% alert type="warning" %}}
网络服务用户不能访问REST 服务。
{{% /报警 %}}

## 4 启用 CORS

当您的服务需要在您自己的网站上可用时，请选中此项。

点击 [设置](cors-settings) 按钮以更详细地指定此访问权限(例如，允许哪个网站访问该服务)。

## 5 资源

REST 服务会暴露一些 [资源](published-rest-resource)。 在一个资源上，您可以定义GET、PUT、POST、PATCH、DELETE、HEAD和选项操作。

您可以将实体或消息定义拖动到这个列表上去 [生成完整的资源](generate-rest-resource)。

## 6 业务

当您选择一个资源时，您会看到定义为该资源的 [操作](published-rest-operation)。

资源和操作被附加到 [位置](#location) 以形成一个可以访问他们的URL。

![](attachments/published-rest-service/example-location-url.png)

## 7 个示例

**如何使用Mendix 本地发布REST**

{{% youtube HzrFkv0U4n8 %}}

## 8 阅读更多

欲了解更多关于某个请求URL执行操作的信息，请参阅 [已发布的REST Routing](published-rest-routing)。
