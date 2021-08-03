---
title: "プロキシを使用してREST サービスを呼び出します。"
parent: "rest-services"
---

場合によってはファイアウォールの背後に立ち往生し、RESTサービスを直接呼び出すことができないこともあります。 このドキュメントでは、そのようなサービスを呼び出すためにプロキシを使用するようにアプリを構成する方法を説明します。

## プロキシホストとプロキシポート

REST コールを実行するときに使用するプロキシサーバを指定する 2 つのパラメータがあります: `http.proxyHost` と `http.proxyPort`。 プロキシによっては認証が必要なものもあります。これは `http.proxyUser` と `http.proxyPassword` として指定できます。

これらをカスタム設定として指定するか、JVM パラメーター (システムプロパティ) として指定することができます。

## カスタム設定

REST プロキシ設定をカスタムサーバー設定として指定する方法については、 [Configuration](configuration#custom) を参照してください。

## JVM パラメータ

または、JVM パラメータの下に `.m2eerc` でJVMパラメータを指定することもできます。 これらの設定を使用して [ウェブサービス](using-a-proxy-to-call-a-webservice) を利用したい場合にも便利です。

```java
...
# custom Java options, like -Xmx256m or -Djava.foo=bar
 javaopts: [ ..., "-Dhttp.proxyHost=myproxyserver.com", "-Dhttp.proxyPort=3128", "-Dhttp.proxyUser=myusername" "-Dhttp.proxyPassword=mypassword" ]
...
```

または直接(モデラーからローカルで実行する場合、または Eclipse から呼び出す場合):

```java
-Dhttp.proxyHost=myproxyserver.com -Dhttp.proxyPort=3128 -Dhttp.proxyUser=myusername -Dhttp.proxyPassword=mypassword
```

カスタム設定とJVMパラメータの両方で設定を指定すると、カスタム設定が使用されます。
