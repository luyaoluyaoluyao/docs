---
title: "使用代理服务器来调用网络服务"
parent: "已消耗的网络服务"
---

## 1 导言

在某些情况下，你被困在防火墙后，因此无法直接拨打网络服务。 此文档向您展示如何配置 JVM 来使用代理服务器来呼叫此类服务。

## 2 代理服务器 & 代理端口

有两个JVM参数 (系统属性) 指定使用哪个代理服务器。 这些是 http.proxyHost 和 http.proxyPort 。您可以在 JVM 参数下在 .m2eerc 中指定这些参数：

```java
...
# 自定义的 java 选项，例如-Xmx256m 或 -Djava.foo=bar
 javaops: [ ..., "-Dhttp.proxyHost=myproxyserver.com", "-Dhttp.proxyPort=3128"]
...

```

或直接(例如从省略调用时)：

```java
-Dhttp.proxyHost=myproxyserver.com -Dhttp.proxyPort=3128

```

## 3 代理用户 & 密码

有些代理需要身份验证。 要指定用户和密码，只需通过两个JVM参数：

```java
-Dhttp.proxyUser=myname -Dhttp.proxyPassword=mypassword
```

## 4 SSL

您也可以在使用安全套接字层 (ie https)时连接。 要配置代理，您需要指定 **不同的** 代理设置才能连接。 这些设置叫做https.proxyHost和https.proxyPort。 此外，您需要将代理服务器的 ssl 证书导入到您的 java 密钥店。 更多信息可以在 [Oracle 网站](http://download.oracle.com/javaee/1.4/tutorial/doc/Security6.html) 上找到

欲了解更多信息，请查看代理服务器上的 [Oracle 文档](http://download.oracle.com/javase/6/docs/technotes/guides/net/proxies.html)。
