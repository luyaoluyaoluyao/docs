---
title: "消耗的网络服务"
parent: "已消耗的网络服务"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/consumed-web-service.pdf)。
{{% /报警 %}}

## 1 导言

此文档描述导入网络服务的属性。 关于导入网页服务的一般概况，请参阅 [消费网络服务](consumed-web-services) 概览文档。

## 2 WSDL 源

您可以从 URL 或从您磁盘上保存的 WSDL 文件加载WSDL

{{% alert type="warning" %}}

如果您尝试从需要身份验证的 URL 中加载一个 WSDL 文件，您将被要求获取用户名和密码。

{{% /警示%}}!{% alert type="warning" %}}

WSDL 文件可能包含多个服务，服务可能包含多个端口。 在加载WSDL时，对话框将要求您为包含多个端口的每个服务选择一个端口。

{{% /报警 %}}

## 3 服务

这一部分具体规定了WSDL中要找到的服务。

* **名称** -- 服务名称。
* **端口** - 选定的端口。
* **位置** - 服务所在的地方。
* **位置常量** - 可以用于添加服务的额外位置， 例如，当SOAP服务的URL从开发环境转向生产环境时会发生变化。 也见 [常数](constants)。

如果在 WSDL 中定义了多端口服务，弹出式对话框将使您能够选择使用哪个端口。

## 4 业务

本部分显示WSDL中发现的所有操作。 您可以在右侧面板中扩展列表并查看有关个别操作的额外信息。

## 5 高级设置

检查 **发送二进制数据作为附件 (MTOM)** 以启用 MTOM (_Message Transmission Optimization Mechanism_)：一种将二进制数据有效发送到网络服务的方法。 在 [w3.org](https://www.w3.org/TR/soap12-mtom/) 处阅读更多关于它的信息。

{{% alert type="warning" %}}

只有当您使用一个或多个导出映射在通话网络服务操作中创建请求正文时，消息优化才会被应用。

{{% /报警 %}}

## 6 呼叫消费的网络服务

关于如何调用消费的网络服务的详情，请见 [调用网络服务](call-web-service-action)。
