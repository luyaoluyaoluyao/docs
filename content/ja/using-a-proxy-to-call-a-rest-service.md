---
title: "プロキシを使用してREST サービスを呼び出します。"
parent: "rest-services"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/using-a-proxy-to-call-a-rest-service.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

場合によっては、ファイアウォールの背後に立ち往生し、RESTサービスを直接呼び出すことができない場合があります。 このページでは、そのようなサービスを呼び出すためにプロキシを使用するようにアプリを構成する方法を説明します。

## 2 プロキシホスト & プロキシポート

REST コールを実行するときに使用するプロキシサーバを指定する 2 つのパラメータがあります: `http.proxyHost` と `http.proxyPort`。 プロキシによっては認証が必要なものもあります。これは `http.proxyUser` と `http.proxyPassword` として指定できます。

これらをカスタム設定として指定するか、以下のセクションで説明されている JVM パラメータとして指定することができます。

{{% alert type="info" %}}
カスタム設定とJVMパラメータの両方で設定を指定すると、カスタム設定が使用されます。
{{% /alert %}}

### 2.1 カスタム設定

REST プロキシ設定は、 **プロジェクト** > **設定** > **構成** > **カスタム** タブでカスタム設定として構成できます。 詳細については、 [Configurations](configuration#custom) の *Custom* セクションを参照してください。

### 2.2 JVM パラメータ

REST proxy settings can be configured in the **Project** > **Settings** > **Configurations** > **Server** tab > **Extra JVM parameters** field. 詳細については、 [設定](configuration#server) の *サーバー* セクションを参照してください。

また、 *.m2eerc* の JVM パラメータとして指定することもできます。 これらの設定を使って [ウェブサービス](using-a-proxy-to-call-a-webservice) を消費したい場合に便利です。

```java
...
# custom Java options, like -Xmx256m or -Djava.foo=bar
 javaopts: [ ..., "-Dhttp.proxyHost=myproxyserver.com", "-Dhttp.proxyPort=3128", "-Dhttp.proxyUser=myusername" "-Dhttp.proxyPassword=mypassword" ]
...
```

Studio Pro からローカルで実行する場合や、Eclipse から呼び出す場合にも、これらを直接指定することができます。

```java
-Dhttp.proxyHost=myproxyserver.com -Dhttp.proxyPort=3128 -Dhttp.proxyUser=myusername -Dhttp.proxyPassword=mypassword
```
