---
title: "エラーイベント"
parent: "イベント"
menu_order: 3
tags:
  - "studio pro"
  - "error event"
  - "イベント"
---

{{% alert type="info" %}}
このイベントは、 **Microflow** でのみ使用できます。
{{% /alert %}}

## 1つの紹介

error イベントは、マイクロフローがどこで停止し、以前に発生したエラーをスローするかを定義します。 マイクロフローを呼び出す場合は、マイクロフロー内でエラーが発生したかどうかを知りたい場合があります。 このイベントは再びエラーをスローし、マイクロフローの呼び出し元がそれらをキャッチすることができます。 現在のトランザクション内のすべてのデータベースアクションがロールバックされるかどうかを制御できます。

エラーハンドラとマイクロフローの設定の詳細については、 [Error Handlers](#errorhandlers) サブセクションを参照してください。 [以下のマイクロフローでエラーを処理する](#errors-in-microflows)。 エラーハンドラとナノフローでの設定の詳細は、 [エラーハンドラ](#errorhandlers-nano) [Nanoflowsでのエラー処理](#errors-in-nanoflows)のサブセクションにあります。 以下です

error イベントと、その上に [シーケンスフロー](sequence-flow)で設定されたエラーハンドラを持つアクティビティをリンクします。

{{% alert type="warning" %}}
エラーがスコープ内にある場合にのみ、error イベントを使用できます。error イベントに通常の実行フローを接続すると、Studio Pro はこれを受け付けません。 呼び出し元に戻すための間違いがないからです
{{% /alert %}}

この例では、データベースにオブジェクトをコミット中にエラーが発生します。 これはキャッチされ、フローは、エラーがマイクロフローの呼び出し元に戻されるエラーイベントを継続します。 したがって、複数のレベルでエラー処理を実装できます。

![](attachments/events/error-event.png)

{{% alert type="info" %}}
When adding an error event, you need to add an [error handler](#errorhandlers) for an activity before the error event, and select **Set as error handler** for the sequence flow.
{{% /alert %}}

## 2マイクロフローのエラー処理{#errors-in-microflows}

マイクロフローでエラーが発生すると、オブジェクトに加えられたすべての変更がロールバックされ、マイクロフローが中断されます。 オプションとして、さまざまなエラー処理設定を構成することで、マイクロフロー自体のエラー [を](/howto/logic-business-rules/set-up-error-handling) 処理できます。 事前定義されたオブジェクト `$latestError` と `$latestSoapFault` を見て、エラーの詳細を調べることもできます。

### 2.1 Error Handlers {#errorhandlers}

エラーハンドラは、マイクロフローのアクティビティ、意思決定、またはループに設定できます。

アクティビティまたは決定では、次の3つの選択肢があります。

*   **Rollback** (default)
*   **ロールバックでカスタム**
*   **ロールバックせずにカスタム**

後者の2つのオプションでは、ブロックから追加のフローを描画し、このフローをエラーハンドラのフローとしてマークすることができます。 'Custom with rollback' を選択すると、エラーが発生し、その後もオブジェクトをロールバックしたときにこのパスがトリガーされます。 'Custom without rollback' オプションは、オブジェクトをロールバックしません。 フローをエラーハンドラとして選択すると、次の画像のように表示されます。

[Rollback object](rollback-object) アクションとは異なり、error イベントの rollback オプションは、オブジェクトがコミットされているかどうかを考慮しません。 つまり、コミットされたオブジェクトであっても、マイクロフロー (または、そこから呼び出されたマイクロフロー) が開始されたときに持っていた値にロールバックされます。 ロールバックは、コミット [の後の](event-handlers) など、 *イベントハンドラ* で行った変更にも適用されます。

**ロールバックのないカスタム** オプションは、アクション自体がエラーイベントを発生させた場合にのみ呼び出されます。 つまり、error handler イベントの原因となるアクションの前に、作成または変更されたデータベースオブジェクトへのアクセス権があります。 持続可能エンティティのオブジェクトに変更を保持したい場合 エラーが発生する前にコミットされていなかった場合でも、 **カスタム** エラーの後に明示的にコミットする必要があります。

![](attachments/events/custom-without-rollback-microflows.png)

ループでは、2 つのオプションがあります。

*   Rollback (default)
*   続ける

continue オプションは、エラーが発生した場合、ループは単に次の反復に続くことを意味します。 ループの終了時に、継続アイコンとして表示されます。

![](attachments/events/error-event-loop.png)

### 2.2 エラーの検査

マイクロフロー内でエラーが発生すると、発生したエラーに関する情報が含まれた Java 例外が発生します。 カスタムエラーハンドラの中（エラー処理フローの後） このJava例外のタイプとその他のいくつかのプロパティを調べることができます。 すべてのマイクロフローには、 `$latestError` と `$latestSoapFault` の 2 つの定義済みエラーオブジェクトが含まれています。 `$latestError` はエンティティSystem.Errorのオブジェクトで、 `$latestSoapFault` はエンティティSystem.SoapFaultのオブジェクトであり、これはSystem.Errorの専門化です。

エラーが発生した後に実行されるカスタムエラーハンドラで。 `$latestError` は発生したエラーに関する情報を含むオブジェクトに設定されています。 エラーが SOAP 障害である場合 (Web サービス コールの結果として発生するエラー) `$latestSoapFault` は SOAP 障害に関するより具体的な情報を含むオブジェクトに設定されます。 それ以外の場合、 `$latestSoapFault` は `空` です。

{{% alert type="info" %}}
`$latestSoapFault` の空 `をチェックすることで、エラーが SOAP 障害であったかどうかを確認できます。`.
{{% /alert %}}

次の表は、System.Error および System.SoapFault の属性を示しています。

| エンティティ           | 属性        | タイプ | 説明                 |
| ---------------- | --------- | --- | ------------------ |
| System.Error     | ErrorType | 文字列 | 発生したエラーのJava例外タイプ。 |
| System.Error     | メッセージ     | 文字列 | Java例外のメッセージ。      |
| System.Error     | スタックトレース  | 文字列 | Java例外のスタックトレース。   |
| System.SoapFault | コード       | 文字列 | SOAP 障害のコード 要素。    |
| System.SoapFault | 理由：       | 文字列 | SOAP 障害の Reason 要素 |
| System.SoapFault | ノード       | 文字列 | SOAP 障害の Node 要素   |
| System.SoapFault | ロール       | 文字列 | SOAP 障害のロール要素      |
| System.SoapFault | 詳細        | 文字列 | SOAP 障害の Detail 要素 |

SOAP 障害の詳細については、 [ここ](http://www.w3.org/TR/soap12-part1/#soapfault) をクリックしてください。

{{% alert type="warning" %}}
エンティティアクセスを適用するマイクロフローでは、セキュリティ上の理由からエラーオブジェクトの属性を検査することはできません。 error オブジェクトをエンティティアクセスを適用せず、そこで属性を検査するサブマイクロフローに渡すことができます。
{{% /alert %}}

## 3 Nanoflows{#errors-in-nanoflows} でエラーを処理する

ナノレベルでエラーが発生した場合、オブジェクトに加えられた変化はロールバックされず、ナノフローは中断されます。 必要に応じて、エラーハンドラを設定することで、nanoflow自体のエラーを処理することができます。 `$latestError` 定義済みの変数を調べることで、エラーの詳細を調べることができます。

### 3.1 Error Handlers {#errorhandlers-nano}

エラーハンドラは、ゲートウェイとループを除くすべてのnanoflow要素でサポートされています。 2つのエラーハンドラのオプションがあります:

*  **中断する** (デフォルト)
*  **ロールバックせずにカスタム**

**カスタム (ロールバックなし) オプションで** ブロックから追加のフローを描画して、このフローをエラーハンドラのフローとしてマークできます。 **ロールバックのないカスタム** オプションは、オブジェクトをロールバックしません。 エラーハンドラとしてフローを選択すると次のように表示されます。

![選択されたエラーハンドラです](attachments/events/custom-without-rollback-nanoflows.png)

### 3.2 エラー検査

エラーが発生した後に実行されるカスタムエラーハンドラでは、エラー情報のメッセージに `$latestError` 変数が設定されます。 `$latestError` 変数の型は `文字列`で、エラーの型が [System.Error](microflows) エンティティである `microflow` とは異なります。

`$latestSoapFault` 変数はナノフラワーでは利用できない。
