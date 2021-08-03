---
title: "已发布的 Web 服务"
parent: "已发布的网络服务"
---

## 1 导言

本文档描述已发布网络服务的属性。 如果你想要Mendix 如何将microflow作为网页服务发布的概括，请参阅 [已发布的 Web Services](published-web-services)。

## 2 业务

![](attachments/16713702/16843888.png)

提供网页服务组成的实际操作。 每项行动都是微流。

查看 [操作](operations)。

## 3 个设置

![](attachments/16713702/16843887.png)

### 3.1 针对WSDL进行验证

如果设置为“是”，收到的请求将与WSDL进行验证。

请注意，在Mendix 5.8.0中引进这个属性时，这方面的行为略有改变。 原始值已经用于验证所有情况，但现在我们正在验证整个传入的 XML 消息。 不要打破旧的网络服务请求，这些请求可能无法对照WSDL进行验证，但不会引起实际问题。 在转换旧版本的项目时，我们不会默认打开此功能。 然而，这意味着如果你想再次验证原始，你必须打开此功能。

_默认值：_ 是

### 3.2 身份验证

用于与 web 服务通信的身份验证设置。

### 3.3 Target Namespace

这是已发布的 WSDL 文件中的目标命名空间属性为此服务的值。 在 Mendix 中，目标命名空间必须是一个有效的统一资源标识符(URI)。 关于XML 命名空间的更多信息，见 [Wikipedia](http://en.wikipedia.org/wiki/XML_namespace)。

在将您的 WSDL 发布给第三方之前，必须正确配置目标命名空间。 稍后更改可能会破坏第三方应用程序来呼叫您已发布的网络服务。

### 3.4 生成 XML

{{% alert type="info" %}}

**生成的 XML** 功能是在版本 7.13.0 中引入的。

{{% /报警 %}}

如果您需要在 XML 中包含关联标签，请选择 **包含关联标签**。 这通常是不必要的，对此的支持将在未来的版本中删除。

要查看此复选框的效果，请考虑带有两个狗和一个猫的人。 当您没有选择 **关联标签**，XML 看起来就像这样：

```xml
<Person name="John">
  <Dog name="Max" />
  <Dog name="Rex" />
  <Cat name="Chester" />
</Person>
```

当您选中 **关联**标签时，XML 看起来就像这样：

```xml
<Person name="John">
  <Person_Dog>
    <Dog name="Max" />
    <Dog name="Rex" />
  </Person_Dog>
  <Person_Cat>
    <Cat name="Chester" />
  </Person_Cat> 
</Person>
```

### 3.5 导出 WSDL 文件 & 导出 XML 方案定义

通过使用此按钮，您可以在本地硬盘上保存生成的 WSDL 文件及其XML 架构定义。 您可以在运行您的项目之前就这样做，不像您从 `http://localhost:8080/ws-doc/` 下载它。

### 3.6 文件

文件可以用来描述网络服务的用途。
