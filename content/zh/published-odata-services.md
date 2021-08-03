---
title: "发布的 OData 服务"
parent: "集成"
menu_order: 10
tags:
  - "studio pro"
---

## 1 导言

在 Studio Pro，实体可以通过添加一个新发布的 OData 服务来暴露为 [OData 资源](published-odata-resource)。 您可以在发布的 OData 服务中暴露任何数量的相关资源。 默认情况下，没有资格的实体名称的复数在URI中被用来独特识别它们。 但你也可以覆盖资源的名称。

Mendix 中用于OData的标准是：

* [OData 版本 3](http://www.odata.org/documentation/odata-version-3-0), 它以 Atom XML 格式返回数据。
* [OData 版本 4](http://www.odata.org/documentation), 它以 JSON 格式返回数据。

{{% alert type="info" %}}
OData 版本 4 功能已经引入Studio Pro [9.4.0](/releasenotes/studio-pro/9.4)。
{{% /报警 %}}

该标准并非所有部分都得到执行。 如果此处没有记载，则尚未添加。

本文档描述了您在创建发布的 OData 服务时可用的选项，并且结束时有一些运行时的考虑。

## 2 概况

### 2.1 服务名称

服务名称用于创建 OData 服务唯一的 URI 。 因此，服务名称应该是按照 [RFC 3986](https://tools.ietf.org/html/rfc3986) 和 [RFC 3987](https://tools.ietf.org/html/rfc3987) 格式完善的。

### 2.2 版本

使用 **版本** 字段为服务分配一个版本号。 此号码将显示在 API 文档中。

{{% alert type="info" %}}

建议您对您发布的服务采用语义编号。

{{% /报警 %}}

### 2.3 命名空间

在OData中，命名空间用于指数据类型。 在 **设置** 标签页上，您可以自定义这个命名空间。 您可以将它更改为任何以字母、数字或点开头，最大长度为512个字符的值。

### 2.4 资源

[资源](published-odata-resource) 是一个由一个实体代表并由一个 URI 识别的网络访问数据对象。

## 3 个设置

### 3.1 OData version

您可以在 OData 4 (推荐) 和 OData 3 之间选择。 主要差别之一是OData 4 服务的返回结果产生于JSON，OData 3 服务返回结果产生于XML。

{{% alert type="info" %}}
此设置被引入Studio Pro [9.4.0](/releasenotes/studio-pro/9.4) 中。 在以前的版本中，所有出版的OData服务都是OData 3。
{{% /报警 %}}

### 3.2 协会

您可以选择代表关联的方式。 欲了解更多信息，请参阅 *OData Representation的 [Associations](odata-representation#associations) 部分*。

### 3.3 安全 {#security}

当 [App Security](project-security) 启用时，您可以配置OData服务的安全。

#### 3.3.1 需要身份验证 {#authentication}

选择客户端是否需要身份验证。 选择 _无_ 允许访问资源不受限制。 选择 _是_ 以便能够选择支持哪些认证方法。

即使您选择 _是_，您仍然可以向匿名用户暴露OData资源。 关于允许匿名用户的详细信息，请参阅 [匿名用户角色](anonymous-users)。

#### 3.3.2 认证方法

如果需要身份验证，您可以选择您想要支持的验证方法。

* 选择 **用户名和密码** 以允许客户端在 **授权中使用用户名和密码进行身份验证** (这被称为“基本认证”)
* 选择 **活动会话** 允许您当前应用程序中的 JavaScript 访问
* 选择 **自定义** 来验证微流程(每次用户想访问资源时都调用这个微流程)

检查多个身份验证方法使服务尝试每个方法。 先尝试 **自定义** 身份验证，然后 **用户名和密码**然后 **活动会话**。

##### 3.3.2.1 用户名 & 密码 {#username-password}

可以通过在通话的 HTTP 头中包含基本身份验证来完成身份验证。 为了做到这一点，您需要构建一个叫做 **Authority** 的头，并且其内容应该按以下方式构建：

1.  用户名和密码合并为字符串"username: password"。
2.  生成的字符串然后使用Base64的 [RFC2045-MIME](https://tools.ietf.org/html/rfc2045) 变体编码（但不限于76个字符/线）。
3.  授权方法和单个空格(意思是“基本”，然后放在编码字符串之前)。

这个结果是一个看起来像 `认证：基本的 QWxhZGRpbjpvcGVuIHNlc2FtZQ==` 的标题。

##### 3.3.2.2 有效会议 {#authentication-active-session}

当您选中此身份验证方法时，您的应用程序中的 JavaScript 可以使用当前用户的会话访问REST 服务。

为了防止跨网站请求的伪造，需要在每个请求上设置 `X-Csrf-Token` 标题，例如：

```
var xmlHttp = new XMLHttpRequest();
xmlHttp.open("GET", "http://mysite/odata/myservice/myresource", false);
xmlHttp.setRequestHeader("X-Csrf-Token", mx.session.getConfig("csrftoken");
xmlHttpsend(null);
```

##### 3.3.2.3 自定义 {#authentication-microflow}

指定用于自定义身份验证的微流。

微流可能需要一个 [HttpRequest](http-request-and-response-entities#http-request) 作为参数，所以它可以检查传入的请求。

微流也可以使用 [HttpResponse](http-request-and-response-entities#http-response) 作为参数。 当微流程将此响应的状态代码设置为其他位置时， **200**， 此值已返回，操作将不会被执行。 在响应中设置的任何头都会返回(除非微流程返回一个空用户)。

身份验证microflow 应返回用户。

认证微流有三个可能的结果：

  * 当HttpResponse 参数的状态代码被设置为其它位置则为 **200**此值已返回，操作将不会执行
  * 当产生的用户不是空的时候，操作将在该用户的上下文中执行
  * 当生成的用户为空时，将尝试下一个身份验证方法(当没有其他身份验证方法时) 结果是 **404 找不到**)

#### 3.3.3 允许的角色

允许的角色定义用户必须能够访问服务的 [模块角色](module-security#module-role)。 此选项仅在 **需要身份验证** 设置为 **是** 时才可用。

{{% alert type="warning" %}}
网络服务用户不能访问 OData 服务。
{{% /报警 %}}

## 4 属性

当OData服务文档显示时在属性窗格中， 您可以编辑一些您也可以在 **通用** 标签中设置的值。 例如： **服务名**, **版本**, 和 **命名空间**.

本节描述您可以设置的附加值。

### 4.1 文件

您可以在这里添加服务描述。 此软件可供在本应用上工作的其他用户使用，并且在部署OData服务时不会发布。

### 4.2 替换非法的 XML 字符

一些特殊字符不能在 XML 中使用。 如果您的数据包含这些 个字符，客户端将出现错误。 If you set this setting to *Yes*, those illegal characters are replaced by the DEL character, and the client will not get an error. 然而，客户收到的数据将不是您数据库中存储的 ，因为这些字符已被替换。

此 *替换非法的 XML 字符* 选项在 OData 版本为 OData 4 时不可用 因为OData 4 以 JSON 格式返回数据。

默认值： *否*

### 4.3 公开文件

您可以为使用服务的人写一个 *摘要* 和 *描述*。

## 5 运行时的考虑

### 5.1 概况

一旦您的应用发布， 已发布的 OData 服务将在应用程序的根URL上提供，然后是 `/odata-doc/`。 例如， `http://localhost:8080/odata-doc` 您可以复制并粘贴链接到例如Excel以便在您的 OData 资源和Excel之间建立链接。

{{% alert type="warning" %}}
虽然OData资源的 API 文档默认已启用，但管理员可能会限制对它的访问权限，对正在生产的应用进行限制。
{{% /报警 %}}

关于如何过滤OData响应的详细信息，请参阅 [OData查询选项](odata-query-options)。

关于Mendix 属性如何在 OData中表现的详情，请参阅 [OData Representation](odata-representation)。

当通过 OData曝光实体时，实体将以流媒体方式从 Mendix 数据库中检索，以避免Mendix Runtime中的内存错误。

### 5.2 房地上的部署

有些在主机上的服务器，尤其是那些使用微软IIS的服务器，将从主机头上取消请求。 这意味着您的 OData 服务和文档将在意外的 URL 上发布。

要解决这个问题，您需要确保您的服务器保存主机头。 在 *Microsoft Windows* 部署文档中查看 [保存主机头](/developerportal/deploy/deploy-mendix-on-microsoft-windows#preserve-header) 部分。
