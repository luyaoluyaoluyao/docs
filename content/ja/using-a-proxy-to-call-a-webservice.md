---
title: "Webサービスを呼び出すためのプロキシの使用"
parent: "consed-web-services"
---


場合によっては、ファイアウォールの後ろに貼り付けられているため、ウェブサービスを直接呼び出すことができません。 このドキュメントでは、そのようなサービスを呼び出すためにプロキシを使用するように JVM を構成する方法を説明します。

## プロキシホストとプロキシ ポート

使用するプロキシサーバーを指定する2つのJVMパラメータ(システムプロパティ)があります。 これらは http.proxyHost と http.proxyPort です。 JVM パラメータの下で .m2eerc で指定できます。

```java
...
# custom Java options, like -Xmx256m or -Djava.foo=bar
 javaopts: [ ..., "-Dhttp.proxyHost=myproxyserver.com", "-Dhttp.proxyPort=3128"]
...

```

または直接(例えば、日食からの呼び出し時):

```java
-Dhttp.proxyHost=myproxyserver.com -Dhttp.proxyPort=3128

```

## プロキシユーザーとパスワード

一部のプロキシでは認証が必要です。 ユーザーとパスワードを指定するには、2つのJVMパラメータを渡します。

```java
-Dhttp.proxyUser=myusername -Dhttp.proxyPassword=mypassword
```

## SSL

セキュアソケットレイヤー(すなわちhttps)を使用して接続することもできます。 プロキシを設定するには、接続するための **異なる** プロキシ設定を指定する必要があります。 これらの設定は https.proxyHost と https.proxyPort と呼ばれます。 さらに、プロキシサーバーの ssl 証明書を Java キーストアにインポートする必要があります。 詳細については、 [Oracle Web サイト](http://download.oracle.com/javaee/1.4/tutorial/doc/Security6.html) を参照してください。

## 参照

[プロキシに関するOracle ドキュメント](http://download.oracle.com/javase/6/docs/technotes/guides/net/proxies.html)
