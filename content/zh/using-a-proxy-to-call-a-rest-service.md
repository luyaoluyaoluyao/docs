---
title: "使用代理服务器来调用 REST 服务"
parent: "消耗性服务"
tags:
  - "studio pro"
---

## 1 导言

在某些情况下，您将被困在防火墙后，因此无法直接调用 REST 服务。 此页面向您展示如何配置您的应用来使用代理服务器来呼叫此类服务。

## 2 代理服务器 & 代理端口

有两个参数指定在进行REST 调用时使用哪个代理服务器： `http.proxyhost` and `http.proxyPort`。 一些代理需要身份验证，您可以指定为 `http.proxyUser` 和 `http.proxyPassword`。

您可以指定这些作为自定义设置或JVM参数，这些参数在下面的章节中描述。

{{% alert type="info" %}}
如果您指定了一个既作为自定义设置又为 JVM 参数的设置，则将使用自定义设置。
{{% /报警 %}}

### 2.1 自定义设置

REST 代理设置可以配置为 **App** > **设置** > **配置** > **自定义** 选项卡。 For more information, see the [Custom](configuration#custom) section of *Configurations*.

### 2.2 JVM参数

REST 代理设置可以在 **App** > **设置** > **配置** > **服务器** 标签 > **额外的 JVM 参数** 字段中配置。 For more information, see the [Server](configuration#server) section of *Configurations*.

它们也可以在您的 *.m2eerc* 中指定为 JVM 参数。 如果您想要使用这些设置来同时使用 [消耗网页服务](using-a-proxy-to-call-a-webservice) ，这是有用的。

```java
...
# 自定义的 java 选项，如-Xmx256m 或 -Djava.foo=bar
 javaops: [ ..., "-Dhttp.proxyHost=myproxyserver.com", "-Dhttp.proxyPort=3128", "-Dhttp.proxyUser=myusername" "-Dhttp.proxyPassword=mypassword"

```

当从Studio Pro 本地运行或从 Eclips 来电时，也可以直接指定他们：

```java
-Dhttp.proxyHost=myproxyserver.com -Dhttp.proxyPort=3128 -Dhttp.proxyUser=myuser-httpD.proxyPassword=mypassword
```
