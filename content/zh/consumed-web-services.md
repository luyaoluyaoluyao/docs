---
title: "消耗的网络服务"
parent: "集成"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/consumed-web-services.pdf)。
{{% /报警 %}}

## 1 导言

本文档描述导入的网络服务。 欲了解消费的网页服务屏幕上的更多信息，请参阅 [消费的网页服务](consumed-web-service)。


## 2 个网络服务

网络服务（另见 [Wikipedia](http://en.wikipedia.org/wiki/Web_service)）是系统之间暴露或吸收功能和数据实体的一种方式。 它们可以用来使应用程序能够通过网络(或互联网)相互“说话”。

Mendix 支持 SOP 服务器之间的交互。 这可以是Mendix到Mendix，Mendix到ThirdParty或ThirdPart到Mendix。

### 2.1 消费网络服务

在Mendix中使用第三方网络服务是容易的。 有一个微流活动可以在另一个系统上调用一个网络服务，并从 Mendix 数据库中导入XML。

### 2.2 已发布的网页服务

为了在Mendix Server中显示功能（从而使其他系统能够利用某些功能），微流可以很容易地作为网络服务发布。 欲了解更多信息，请参阅 [已发布的网页服务](published-web-services)。

## 3 XML

为了使各系统能够相互理解，需要有一种标准的“编码”数据方法。 XML (eXtensiable Markup Language) 是一种将数据编码(或包装)的格式，以便双方都能理解电文的含义。 下面是一个简单的 XML 代码示例：

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

在这种情况下，对象'人'被描述为属性'name'、'年龄'和所指对象'地址'的对应值。

XML可以在 Mendix 中用于序列化和反序列化，以便导出和导入数据。

请参阅 [XML Schemas](xml-schemas) 以了解导入XSDs到您的应用程序的更多信息。 请参阅  [导入映射](import-mappings) 关于映射XML 文档到域模型实体的进一步信息，以及 [导出映射](export-mappings) 以XML形式导出域实体的进一步信息。

## 4 SOAP

在企业市场，SOAP(另见 [Wikipedia](http://en.wikipedia.org/wiki/SOAP_(protocol)))是网络服务的共同协议。 它确定了各系统相互沟通的标准方式。 XML 被用作消息格式。

## 5 XSD

XSD (XML Schema Definition) 文档是一个描述XML 如何结构的文件，双方当事人都知道电文的含义。 XSD 本身是在 XML中写入的。

## 6 WSDL

WSDL (Web Service Definition Language) 文档是一个描述客户端如何能够与发布它的服务器交互的文档。 它描述了消息的类型(进出)以及消息必须发送到哪里(端点URL)。

使用导入的 web 服务，您可以从外部应用程序导入一个 web 服务用于您自己的应用程序。 您可以从第三方(例如 [w3schools example service](http://www.w3schools.com/xml/tempconvert.asmx?WSDL))或从其他 Mendix 项目导入网络服务。

要在微流程中使用这些导入的网络服务，请参阅 [调用 Web Service](call-web-service-action)。

## 7 个代理

如果你在防火墙后面，你可能需要使用代理来呼叫网络服务。 如何配置 JVM 使用代理服务器的具体信息可以在 [使用代理服务器来调用 Web Service](using-a-proxy-to-call-a-webservice)。

## 8 Protocols

Mendix 支持根据以下协议消费网络服务数据：

*   SOAP 1.1
*   SOAP 1.2
*   MTOM/XOP
*   WS-MetadataExchange v1.1
*   WS-Policy v1.2
*   WS-Policy v1.5
*   WS-Policyattachment 1.5
*   WS-可靠消息1.1
*   WS-Addressing 1.0 (来自 Mendix 版本 8.16)

要连接到 Microsoft .NET 网络服务，您必须配置您的网络服务才能使用 BasicHttpBinding (SOAP 1.1) 或 wsHttpBinding (SOAP 1.2)。 为了安全连接， 您必须配置 SSL 并将安全模式设置为 `传输` 与客户端CredentialType `Basic` 在 **web。 onfig** 文件。 用户凭据可以在 Studio Pro 中配置为 **调用 Web Service** 活动，如 [使用HTTP 身份验证](call-web-service-action#http-headers)。
