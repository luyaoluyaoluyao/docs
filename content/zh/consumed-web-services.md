---
title: "消耗的网络服务"
parent: "集成"
---

{{% alert type="warning" %}}

本文档描述导入的网络服务。 如果您在消费的 web 服务屏幕上寻找具体信息，您可以检查 [已消耗的 web 服务](consumed-web-service) 文档。

{{% /报警 %}}

## 网络服务

网络服务（另见 [wikipedia](http://en.wikipedia.org/wiki/Web_service)）是系统之间暴露或吸收函数和/或数据实体的一种方式。 它们可以用来使应用程序能够通过网络(或互联网)相互“说话”。

Mendix 支持 SOP 服务器之间的交互。 这可以是Mendix到Mendix，Mendix到ThirdParty或ThirdPart到Mendix。

### 已消耗的网络服务

在Mendix中使用第三方网络服务是容易的。 有一个微流程活动可以在另一个系统上调用一个网络服务，并从 Mendix 数据库中导入XML。

### 已发布的网页服务

为了在Mendix 服务器上显示功能（从而使其他系统能够利用某些功能），微流可以很容易地作为网络服务发布。 查看 [已发布的 Web 服务](published-web-services)。

## XML

为了使各系统能够相互理解，需要有一种标准的“编码”数据方法。 XML (eXtensiable Markup Language) 是一种将数据编码(或包装)的格式，以便双方都能理解电文的含义。 一个简单的示例：

```xml
<person>
    <name>John Smith</name>
    <age>23</age>
    <address>
        <street>Dopeylane 14</street>
        <city>Worchestire</city>
    </address>
</person>
```

对象“人”上方的描述包含属性“name”、“年龄”和所指对象“地址”的对应值。

XML可以在 Mendix 中用于序列化和反序列化，以便导出和导入数据。

请参阅 [XML Schemas](xml-schemas) 关于导入XSDs到您的应用程序的信息。 请参阅  [导入映射](import-mappings) 以获取映射到 XML 文档的信息， [导出映射](export-mappings) 以XML格式导出域实体的信息。

## SOAP

在企业市场中，SOAP（另见 [wikipedia](http://en.wikipedia.org/wiki/SOAP_(protocol))）是网络服务的共同协议。 它确定了各系统如何相互沟通的标准方式。 XML 被用作消息格式。

## XSD

XSD (XML Schema Definition) 文档是一个描述XML 如何结构的文件，这样双方当事人都知道电文的含义。 XSD 本身是在 XML中写入的。

## WSDL

WSDL (Web Service Definition Language) 文档是一个描述客户端如何能够与发布它的服务器交互的文档。 它描述了消息的类型(进出)以及消息必须发送到哪里(端点URL)。

使用导入的 web 服务，您可以从外部应用程序导入一个 web 服务，这样它们就可以用于您自己的应用程序。 您可以从第三方导入网络服务(例如 [w3schools example service](http://www.w3schools.com/xml/tempconvert.asmx?WSDL))，也可以从其他mendix 项目导入。

要在微流程中实际使用这些导入的网络服务，请参阅 [调用网络服务行动](call-web-service-action)。

## 代理

如果你在防火墙后面，你可能需要使用代理来呼叫网络服务。 如何配置 JVM 使用代理的具体信息可以在这里找到 [](using-a-proxy-to-call-a-webservice)

## Protocols

Mendix 支持根据以下协议消费网络服务数据：

*   SOAP 1.1
*   SOAP 1.2
*   MTOM/XOP
*   WS-MetadataExchange v1.1
*   WS-Policy v1.2
*   WS-Policy v1.5
*   WS-Policyattachment 1.5
*   WS-可靠消息1.1

要连接到 Microsoft .NET 网络服务，您必须配置您的网络服务才能使用 BasicHttpBinding (SOAP 1.1) 或 wsHttpBinding (SOAP 1.2)。 为了安全连接，您必须配置 SSL 并将安全模式设置为 '传输' 与 clientCredentialType 'Basic' 在文件 'web.config' 中。 用户凭据可以在 Moderr 中配置为 [在这里描述了](call-web-service-action) (见'使用HTTP 身份验证')。
