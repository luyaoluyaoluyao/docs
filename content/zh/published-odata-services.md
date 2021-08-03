---
title: "发布的 OData 服务"
parent: "集成"
aliases:
  - /refguide7/consumed-odata-services.html
---

## 1 导言

在模型中，实体可以通过添加一个新发布的 OData 服务来暴露为 [OData 资源](published-odata-resource)。 您可以在发布的 OData 服务中暴露任何数量的相关资源。 默认情况下，在URI中使用非限定的实体名称来独特识别它们。 但你也可以覆盖资源的名称。

## 2 OData Version

Mendix 中用于OData的标准是 [OData 版本 3](http://www.odata.org/documentation/odata-version-3-0)，默认表示设置为 Atom XML。 该标准并非所有部分都得到执行。 如果此处没有记载，则尚未添加。

## 3 查询选项

关于如何过滤OData响应的详细信息，请参阅 [OData查询选项](odata-query-options)。

## 4 支持的类型

关于Mendix 属性如何在 OData中表现的详情，请参阅 [OData Representation](odata-representation)。

## 5 服务名称

服务名称用于创建 OData 服务唯一的 URI 。 因此，服务名称应该是按照 [RFC 3986](https://tools.ietf.org/html/rfc3986) 和 [RFC 3987](https://tools.ietf.org/html/rfc3987) 格式完善的。

## 6 资源

[资源](published-odata-resource) 是一个可通过网络访问的数据对象，代表一个经URI确认的实体。 您可以从 **资源** 选项卡中添加、编辑或删除资源及其独特的标识符。

## 7 个服务命名空间

在OData中，命名空间用于指数据类型。 在 **设置** 标签页上，您可以自定义这个命名空间。 您可以将它更改为任何以字母、数字或点开头，最大长度为512个字符的值。

## 8 业绩

当通过 OData曝光实体时，实体将以流媒体方式从 Mendix 数据库中检索，以避免Mendix 运行时出现内存错误。

## 9个协会

您可以选择代表关联的方式。 欲了解更多信息，请参阅 *OData Representation的 [Associations](odata-representation#associations) 部分*。

## 10 security

能消耗Mendix中的OData， 您需要有两种访问权：访问OData服务的权利以及对您正在检索的特定实体的权利。 只要关联的用户角色同时可以访问OData服务和实体，就可以通过认证或匿名用户授予访问权限。

### 10.1 经认证的访问

可以通过在通话的 HTTP 头中包含基本身份验证来完成身份验证。 为了做到这一点，您需要构建一个叫做 **Authority** 的头，并且其内容应该按以下方式构建：

1.  用户名和密码合并为字符串 "username: password"
2.  生成的字符串然后使用Base64的 [RFC2045-MIME](https://tools.ietf.org/html/rfc2045) 变体编码，但不限于76 个字符/行
3.  授权方法和单个空格(意思是“基本”，然后放在编码字符串之前)。

这个结果是一个看起来像 `认证：基本的 QWxhZGRpbjpvcGVuIHNlc2FtZQ==` 的标题。

### 10.2 匿名访问

启用项目安全后，OData资源仍然可以向匿名用户曝光。 关于允许匿名用户的详细信息，请参阅 [匿名用户角色](anonymous-users)。

### 10.3 项目安全关闭

如果项目安全性被关闭，为了调试目的，您可以检索所有数据，而无需进行身份验证，也无需应用任何安全保障。 这在生产环境中是不可能的。

### 10.4 基于角色的访问

如果启用了安全性，需要配置哪些用户有权访问特定的 OData 服务文档。 可以通过打开特定发布的OData服务文档来做到这一点。 导航到设置选项卡并更改安全部分中允许的角色。 默认情况下，没有选择允许的用户角色。 安全设置在 [模块安全](module-security) 中得到反映。

![](attachments/16713721/16843927.png)

### 10.5 警卫是如何工作的

1.  通常客户端发出初始匿名请求。 然后将匿名请求与OData服务进行验证。 如果不给予相应的OData服务匿名访问， 服务器将返回错误代码401(未经授权)，响应将包含WW-Authenticate 头部指示客户端进行基本身份验证。
2.  如果客户没有提供正确的凭据或根本没有提供基本的身份验证， 服务器返回错误代码 401 (未经授权) 和 WWW-Authenticate 头像上一步一样。
3.  如果客户端被允许访问(要么匿名访问，要么通过基本身份验证)， 客户端访问权限将根据OData资源的安全配置进行检查。 所有可访问的资源都在附加 `/$metadata` 的服务 root URL下可用的元数据XML 文档中描述。
4.  每次客户端调用OData服务，无论是服务描述， 或元数据，或资源，将重新评估认证信息。

### 11 API 文档

一旦您的 OData-enabled 应用程序运行，暴露的 OData 资源的概览就可以在 root URL 上获取，然后是 `/odata-doc/`。 例如， `http://localhost:8080/odata-doc` 您可以复制并粘贴链接到例如Excel以便在您的 OData 资源和Excel之间建立链接。

{{% alert type="warning" %}}
虽然OData资源的 API 文档默认已启用，但管理员可能会限制对它的访问权限，对正在生产的应用进行限制。
{{% /报警 %}}
