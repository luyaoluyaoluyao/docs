---
title: "公開されたウェブサービス"
parent: "published-web-services"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/published-web-service.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

このドキュメントでは、公開された Web サービスのプロパティについて説明します。 MendixがどのようにマイクロフローをWebサービスとして公開するかについての一般的な概要を知りたい場合は、 [公開されたWebサービス](published-web-services) を参照してください。

## 2つの操作

![](attachments/16713702/16843888.png)

Webサービスが構成されている実際の操作を提供します。 これらの操作はそれぞれマイクロフローです。

[操作](operations) を参照してください。

## 3つの設定

![](attachments/16713702/16843887.png)

### 3.1 WSDL に対する検証

「はい」に設定されている場合、WSDLに対するリクエストの受信が検証されます。

デフォルト: *はい*

### 3.2 認証

Web サービスとの通信を定義する認証設定。

### 3.3 Target Namespace

これは、このサービスの公開済みの WSDL ファイル内の targetNamespace 属性の値です。 Mendix では、ターゲットの名前空間は有効な Uniform Resource Identifier (URI) でなければなりません。 XML 名前空間の詳細については、 [Wikipedia](http://en.wikipedia.org/wiki/XML_namespace) を参照してください。

WSDL をサードパーティに公開する前に、ターゲット名前空間を正しく設定することが重要です。 後で変更すると、公開された Web サービスを呼び出すサードパーティのアプリケーションが壊れる可能性があります。

### 3.4 生成された XML

XML に関連付け用のタグを含める必要がある場合は、 **タグを含める** を選択します。 これは通常必要ありません。将来のバージョンではサポートが削除されます。

このチェックボックスの効果を確認するには、2匹の犬と1匹の猫を持つ人を考えてみましょう。 **関連付けにタグを含む**を選択しないと、XML は以下のようになります:

```xml
<Person name="John">
  <Dog name="Max" />
  <Dog name="Rex" />
  <Cat name="Chester" />
</Person>
```

**関連するタグを含む**にチェックを入れると、XML は以下のようになります:

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

### 3.5 WSDL ファイルのエクスポート & XML スキーマ定義のエクスポート

このボタンを使用することで、生成された WSDL ファイルと XML スキーマ定義をローカルハードドライブに保存することができます。 `http://localhost:8080/ws-doc/` からダウンロードするのとは異なり、プロジェクトを実行する前にすでにこれを行うことができます。

### 3.6 ドキュメント

ドキュメントは、Web サービスが何に使用されるかを記述するために使用できます。
