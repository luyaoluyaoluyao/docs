---
title: "アプリを利用したサービス"
parent: "統合"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/consumed-app-services.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="info" %}}
App サービスは非推奨となり、Studio Pro 9 で削除されました。 既存のアプリサービスを利用するには、 [ウェブサービス](consumed-web-services) を使用してください。
{{% /alert %}}

アプリサービスは、Mendixアプリケーションを互いに接続する方法です。 アプリサービスをインポートし、コンテンツを使用することができます。 現在のところ、アプリサービスは以下の内容を提供しています。

* マイクロフローアクション
* ドメインモデルエンティティ

プロジェクトエクスプローラでは、モジュールの「追加」コンテキストメニューからアプリサービスを選択できます。 詳細は [Select app service](select-app-service) を参照してください。

ドキュメントオプションの詳細については、 [設定](settings) ページを参照してください。

アプリサービスのアクションは、Microflowsで直接利用できます。 新しいアクティビティが追加された場合、標準のマイクロフローアクションの下に新しいアプリサービスアクションが表示されます。

![](attachments/16713703/16843891.png)

appサービスアクションはパラメータを必要とし、通常は戻り値を提供します。 戻り値は、残りのマイクロフローで使用できます。 パラメータと戻り値は、オブジェクトまたはリストの型にすることができます。 アプリサービスで受け入れられるエンティティは、アプリサービスのドメインモデルに含まれます。
