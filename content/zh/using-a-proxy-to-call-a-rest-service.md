---
title: "使用代理服务器来调用 REST 服务"
parent: "消耗性服务"
---

在某些情况下，您将被困在防火墙后，因此无法直接调用 REST 服务。 此文档向您展示如何配置您的应用来使用代理服务器来呼叫此类服务。

## 代理主机和代理端口

有两个参数指定在进行REST 调用时使用哪个代理服务器： `http.proxyhost` and `http.proxyPort`。 一些代理需要身份验证，您可以指定为 `http.proxyUser` 和 `http.proxyPassword`。

您可以指定这些作为自定义设置或JVM参数 (系统属性)。

## 自定义设置

指定REST 代理设置作为自定义服务器设置的详细信息，请参阅 [配置](configuration#custom)。

## JVM 参数

或者，您可以在 JVM 参数下在 `.m2eerc` 中指定 JVM 参数。 如果您想要使用这些设置来 [消耗网页服务](using-a-proxy-to-call-a-webservice) ，这是有用的。

```java
...
# 自定义的 java 选项，如-Xmx256m 或 -Djava.foo=bar
 javaops: [ ..., "-Dhttp.proxyHost=myproxyserver.com", "-Dhttp.proxyPort=3128", "-Dhttp.proxyUser=myusername" "-Dhttp.proxyPassword=mypassword"

```

或直接(当从Moderr本地运行或从Eclipse调用时)：

```java
-Dhttp.proxyHost=myproxyserver.com -Dhttp.proxyPort=3128 -Dhttp.proxyUser=myuser-httpD.proxyPassword=mypassword
```

如果指定一个设置，既作为自定义设置，也作为JVM参数，则将使用自定义设置。
