---
title: "アクティビティ"
parent: "application-logic"
menu_order: 40
tags:
  - "studio pro"
  - "マイクロフロー"
  - "ナノフロー"
  - "アクティビティ"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/activities.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

アクティビティは、マイクロフローまたはナノレベルで実行されるアクションを定義します。

さまざまな種類のアクティビティがあり、これらはStudio Proツールボックスにまとめられています。 すべてのアクティビティは以下にリストされています。詳細についてはリンクを参照してください。

{{% alert type="info" %}}
ほとんどのアクティビティは、マイクロフローとナノフローの両方で使用できます。 しかしながら、これらの種類のフローのいずれかでのみ使用できる場合や、マイクロフローとナノフローの間で動作が異なる場合があります。 詳細については、リンクに従ってください。
{{% /alert %}}

## 2 Object Activities

オブジェクトのアクティビティはオブジェクトの作成や操作に使用できます。 [ドメイン モデル](domain-model) は、使用可能なオブジェクト タイプ ([エンティティ](entities)) を定義します。

| グラフィック                                                                           | 名前                                          | 説明                                                                                                                            |
| -------------------------------------------------------------------------------- | ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [![オブジェクトをキャスト](attachments/activities/cast-object.png)](cast-object)            | [オブジェクト](cast-object) *をキャスト (マイクロフローのみ)*   | [オブジェクト型の決定](object-type-decision) と組み合わせることで、オブジェクトの特殊なメンバーを使用できます。 オブジェクトの特殊なメンバーに関する詳細については、 [エンティティ](entities) を参照してください。 |
| [![オブジェクトの変更](attachments/activities/change-object.png)](change-object)          | [オブジェクトの変更](change-object)                  | オブジェクトのメンバーを変更できます。 これは、イベントの有無にかかわらず、コミットせずに行うことができます。                                                                       |
| [![commit object](attachments/activities/commit-object.png)](committing-objects) | [コミットオブジェクト](committing-objects)            | 1 つ以上のオブジェクトに変更を反映できます。                                                                                                       |
| [![オブジェクトを作成](attachments/activities/create-object.png)](create-object)          | [オブジェクトを作成](create-object)                  | オブジェクトを作成                                                                                                                     |
| [![オブジェクトの削除](attachments/activities/delete-object.png)](deleting-objects)       | [オブジェクトの削除](deleting-objects) *(マイクロフローのみ)* | オブジェクトを削除する                                                                                                                   |
| [![取得](attachments/activities/retrieve.png)](retrieve)                           | [保留する](retrieve)                            | 別のオブジェクトの 1 つ(または複数) 関連するオブジェクトを取得します。 さらに、このアクティビティは、データベースから直接オブジェクトを取得することもできます。                                           |
| [![ロールバックオブジェクト](attachments/activities/rollback.png)](rollback-object)          | [オブジェクトのロールバック](rollback-object)            | アクティビティに先立つマイクロフローの一部でオブジェクトに加えられた、反映されていない変更をロールバックします。 さらに、作成されているがコミットされていないオブジェクトを削除します。                                  |

## 3つのリストアクティビティ

リストアクティビティは、オブジェクトのリストの作成と操作に使用できます。

| グラフィック                                                                | 名前                      | 説明                                             |
| --------------------------------------------------------------------- | ----------------------- | ---------------------------------------------- |
| [![集約リスト](attachments/activities/aggregate-list.png)](aggregate-list) | [集計リスト](aggregate-list) | オブジェクトのリスト上で、最大値、最小値、合計値、平均値、合計値などの集計値を計算できます。 |
| [![リストの変更](attachments/activities/change-list.png)](change-list)      | [リストの変更](change-list)   | リスト変数の内容を変更できます。                               |
| [![リストを作成](attachments/activities/create-list.png)](create-list)      | [リストを作成](create-list)   | (空) リスト変数を作成します。                               |
| [![リスト操作](attachments/activities/list-operation.png)](list-operation) | [リスト操作](list-operation) | 2 つのリストを同じエンティティのオブジェクトと結合または比較します。            |

## 4つのアクションコールアクティビティ

アクションコールアクティビティは、別のマイクロフローを呼び出したり、Java アクションを呼び出したりするために使用できます。

| グラフィック                                                                                             | 名前                                                     | 説明                                                           |
| -------------------------------------------------------------------------------------------------- | ------------------------------------------------------ | ------------------------------------------------------------ |
| [![javaアクションコール](attachments/activities/call-java-action.png)](java-action-call)                   | [Javaアクション](java-action-call) *(マイクロフローのみ)*            | Javaアクションを呼び出します。 引数はアクションに渡すことができ、結果は変数に格納することができます。        |
| [![javascriptアクションコール](attachments/activities/call-javascript-action.png)](javascript-action-call) | [JavaScript アクション](javascript-action-call) *(ナノフローのみ)* | JavaScript アクションを呼び出します。 引数はアクションに渡すことができ、結果は変数に格納することができます。 |
| [![マイクロフロー・コール](attachments/activities/call-microflow.png)](microflow-call)                        | [マイクロフロー通話](microflow-call)                            | マイクロフローを呼び出します。 引数をマイクロフローに渡すことができ、その結果を変数に格納することができます。      |

## 5種類の可変アクティビティ

変数アクティビティは、マイクロフロー内で変数を作成または変更するために使用できます。

| グラフィック                                                                  | 名前                       | 説明            |
| ----------------------------------------------------------------------- | ------------------------ | ------------- |
| [![変数の変更](attachments/activities/change-variable.png)](change-variable) | [変数の変更](change-variable) | 変数の値を変更できます。  |
| [![変数を作成](attachments/activities/create-variable.png)](create-variable) | [変数を作成](create-variable) | 新しい変数を作成できます。 |

## 6つのクライアントアクティビティ

クライアントアクティビティは、アプリケーションのWebクライアントにアクションを実行させるために使用できます。 例えば、別のページを表示したり、ファイルをダウンロードしたりしています。

| グラフィック                                                                                | 名前                                             | 説明                                                                                                                      |
| ------------------------------------------------------------------------------------- | ---------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| [![ナノフロー・コール](attachments/activities/call-nanoflow.png)](nanoflow-call)               | [nanoflow を呼ぶ](nanoflow-call) *(nanoflowsのみ)*  | 別のナノフローを呼び出します。 引数はnanoflowに渡すことができ、その結果を変数に格納することができます。                                                                |
| [![ページを閉じる](attachments/activities/close-page.png)](close-page)                       | [ページを閉じる](close-page)                          | このアクティビティが使用されているマイクロフローを呼び出したユーザーが最後に開いたページを閉じます。                                                                      |
| [![ファイルをダウンロード](attachments/activities/download-file.png)](download-file)             | [ファイル](download-file) をダウンロード *(マイクロフローのみ)*    | ブラウザで特定のファイルをダウンロードできるようにすることができます。 このアクティビティが使用されているマイクロフローを呼び出したユーザーは、ダウンロードポップアップウィンドウを取得します。 またはファイルがブラウザに直接表示されます。 |
| [![ホームページを表示](attachments/activities/show-home-page.png)](show-home-page)             | [ホームページ](show-home-page) *(マイクロフローのみ)*         | 現在のユーザーのホームページに移動します。                                                                                                   |
| [![メッセージを表示](attachments/activities/show-message.png)](show-message)                  | [メッセージを表示](show-message)                       | このアクティビティが使用されているマイクロフローを呼び出すユーザーにブロックまたは非ブロックメッセージを表示できます。                                                             |
| [![ページを表示](attachments/activities/show-page.png)](show-page)                          | [ページを表示](show-page)                            | このアクティビティが使用されているマイクロフローを呼び出すユーザーにページを表示できます。                                                                           |
| [![デバイスに同期](attachments/activities/synchronize-to-device.png)](synchronize-to-device) | [デバイスに同期](synchronize-to-device) *(マイクロフローのみ)* | 1つ以上のオブジェクトまたはリストをデバイスに選択的に同期し、それらをオフラインデータベースに格納するために使用できます。                                                           |
| [![synchronize](attachments/activities/synchronize.png)](synchronize)                 | [](synchronize)  *を同期する (ナノフローのみ)*             | データの同期。                                                                                                                 |
| [![検証フィードバック](attachments/activities/validation-feedback.png)](validation-feedback)   | [検証のフィードバック](validation-feedback)              | 属性または関連付けを表示するウィジェットの下に赤色のテキストを表示できます。                                                                                  |

## 7 つの統合アクティビティ

統合アクティビティは、Web サービスを呼び出すなど、他のシステムと統合するために使用できます。

| グラフィック                                                                                       | 名前                                     | 説明                                                                                                                                                                                |
| -------------------------------------------------------------------------------------------- | -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [![REST サービスを呼び出す](attachments/activities/call-rest-service.png)](call-rest-action)          | [REST サービスに発信](call-rest-action)       | REST エンドポイントを呼び出すために使用できます。 マッピングを使用して結果をエンティティやエンティティにリクエストにマップすることができます。 文字列テンプレートを使用して、結果を文字列変数に格納することもできます。                                                                   |
| [![ウェブサービスアクションを呼び出す](attachments/activities/call-web-service.png)](call-web-service-action) | [Web サービスに発信](call-web-service-action) | インポートされた [Webサービス](consumed-web-services) のいずれかを呼び出すために使用できます。 リクエストの内容は編集できます。 さらに、Webサービスの応答は、変数に格納されたエンティティにマップしたり、無視したりすることができます。                                             |
| [![マッピング付きでインポート](attachments/activities/import-with-mapping.png)](import-mapping-action)    | [マッピングでインポート](import-mapping-action)   | ファイルドキュメントに格納されている文字列変数またはデータを解析するために使用できます。 を選択し、データベースの [ドメイン モデル](domain-model) に定義されたエンティティに保存します。 [インポート マッピング](import-mappings) は、受信する XML または JSON をエンティティにマップするために使用されます。 |
| [![マッピングでエクスポート](attachments/activities/export-with-mapping.png)](export-mapping-action)     | [マッピングでエクスポート](export-mapping-action)  | [ドメイン モデル](domain-model) に格納されているデータを XML または JSON 文字列にエクスポートするために使用できます。 ファイルドキュメントに保存することもできます。 [エクスポートマッピング](export-mappings) は、ドメインモデルエンティティを XML または JSON にマップするために使用されます。   |

## 8つのログ記録

| グラフィック                                                            | 名前                     | 説明                                   |
| ----------------------------------------------------------------- | ---------------------- | ------------------------------------ |
| [![ログメッセージ](attachments/activities/log-message.png)](log-message) | [ログメッセージ](log-message) | Mendixアプリケーションのログに表示されるメッセージを作成できます。 |

## 9 ドキュメント生成アクティビティ

| グラフィック                                                                          | 名前                                          | 説明                                                      |
| ------------------------------------------------------------------------------- | ------------------------------------------- | ------------------------------------------------------- |
| [![ドキュメントを生成](attachments/activities/generate-document.png)](generate-document) | [ドキュメント](generate-document) を生成 *(ナノフローのみ)* | [テンプレート](document-templates) に基づいて、特定の種類のドキュメントを作成できます。 |