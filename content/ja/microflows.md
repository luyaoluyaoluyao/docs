---
title: "マイクロフロー"
parent: "application-logic"
menu_order: 10
description: "マイクロフローで使用できるすべての要素の概要を表示します。"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/microflows.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

マイクロフローを使用すると、アプリケーションのロジックを表示できます。 マイクロフローは、オブジェクトの作成や更新、ページの表示、選択肢の作成などのアクションを実行できます。 それは、伝統的にテキストプログラムコードで終わるものを視覚的に表現する方法です。

マイクロフローはランタイムサーバーで実行されるため、オフラインアプリでは使用できません。 オフラインアプリ内のアプリケーションロジックについては、 [Nanoflows](nanoflows) を参照してください。

このページは、マイクロフローを構成する要素と、マイクロフロー内での視覚表現の概要です。 また、マイクロフローを編集する際に [キーボードサポート](#keyboard) をカバーしています。

{{% alert type="info" %}}
マイクロフロー自体のプロパティについては、 [Microflow Properties](microflow) を参照してください。
{{% /alert %}}

## 2 マイクロフロー表記法

マイクロフローのグラフィカル表記は、 [Business Process Model and Notation](https://en.wikipedia.org/wiki/Business_Process_Model_and_Notation) (BPMN) に基づいています。 BPMN は、ビジネスプロセスをワークフローで描画するための標準化されたグラフィカル表記です。

マイクロフローは要素で構成されています。 以下は、すべての要素のカテゴリ概要です。 以下のカテゴリが使用されます：

*   [イベント](#events) は、ループにおけるマイクロフローと特別な操作の開始点と終了点を表します。
*   [フロー](#flows) が要素間の接続を形成します。
*   [決定](#decisions) は、選択を行い、異なるパスを再度マージすることを取り扱う。
*   [アクティビティ](#activities) は、マイクロフローで実行されるアクションです。
*   [ループ](loop) はオブジェクトのリストを反復するために使用されます。
*   [パラメータ](#parameter) は、マイクロフローの入力となるデータである。
*   [アノテーション](#annotation) は、コメントをマイクロフローに置くために使用できる要素である。

### 2.1 イベント{#events}

イベントは、ループ内のマイクロフローと特殊な操作の開始点と終了点を表します。

| グラフィック                                                                         | 名前                         | 説明                                                                                                      |
| ------------------------------------------------------------------------------ | -------------------------- | ------------------------------------------------------------------------------------------------------- |
| [![](attachments/microflows-and-nanoflows/start-event.png)](start-event)       | [イベントを開始](start-event)     | 開始イベントは、マイクロフローの開始点です。 マイクロフローは、1 つの開始イベントしか持つことができません。                                                 |
| [![](attachments/microflows-and-nanoflows/end-event.png)](end-event)           | [イベントを終了](end-event)       | endイベントは、マイクロフローが停止する場所を定義します。 場合によっては、マイクロフローの戻り値を指定する必要があります。 複数のエンドイベントが存在する可能性があります。                |
| [![](attachments/microflows-and-nanoflows/error-event.png)](error-event)       | [エラーイベント](error-event)     | error イベントは、microflow が停止し、以前に発生したエラーをスローする場所を定義します。 マイクロフローを呼び出す場合は、マイクロフロー内でエラーが発生したかどうかを知りたい場合があります。 |
| [![](attachments/microflows-and-nanoflows/continue-event.png)](continue-event) | [イベントを続ける](continue-event) | continue イベントは、ループの現在の反復を停止し、次の反復を続行するために使用されます。 Continue イベントは、 [Loop](loop) 内でのみ使用できます。               |
| [![](attachments/microflows-and-nanoflows/break-event.png)](break-event)       | [休憩イベント](break-event)      | break イベントは、オブジェクトのリストの反復を停止し、ループの後に残りのフローを継続するために使用されます。 ブレークイベントは [ループ](loop)内でのみ使用できます。              |

### 2.2 フロー{#flows}

フローは要素間の接続を形成します。

| グラフィック                                                                                      | 名前                                  | 説明                                                                     |
| ------------------------------------------------------------------------------------------- | ----------------------------------- | ---------------------------------------------------------------------- |
| [![](attachments/microflows-and-nanoflows/sequence-flow.png)](sequence-flow)                | [シーケンスフロー](sequence-flow)           | シーケンス フローは、イベント、アクティビティ、決定、および互いに結合する矢印です。 彼らは一緒にマイクロフロー内の実行の順序を定義します。 |
| [![](attachments/microflows-and-nanoflows/annotation-flow.png)](annotation#annotation-flow) | [注釈フロー](annotation#annotation-flow) | 関連付けは、注釈を別の要素に接続するために使用できる接続です。                                        |

### 2.3 決定 {#decisions}

決定は、選択を行い、異なるパスを再びマージすることに対処します。

| グラフィック                                                                                     | 名前                                 | 説明                                                                                                                    |
| ------------------------------------------------------------------------------------------ | ---------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| [![](attachments/microflows-and-nanoflows/decision.png)](決定)                               | [決定](決定)                           | 決断は条件に基づいて決定を行い、唯一の発信流れに従います。 マイクロフローでは並列実行はありません。                                                                    |
| [![](attachments/microflows-and-nanoflows/object-type-decision.png)](object-type-decision) | [オブジェクト型の決定](object-type-decision) | オブジェクト型の決定は、選択したオブジェクトの [特殊化](entities) に基づいて選択を行う要素です。 特殊なオブジェクトに [キャストオブジェクト](cast-object) アクションを使用して名前を付けることができます。 |
| [![](attachments/microflows-and-nanoflows/merge.png)](マージ)                                 | [結合](マージ)                          | マージを使用して、複数のシーケンスフローを1つに結合することができます。 マイクロフローで選択が行われ、その後、いくつかの一般的な作業が行われる必要があります。 マージを使用して、2 つのパス(またはそれ以上)を結合できます。     |

### 2.4 アクティビティ{#activities}

[アクティビティ](activities) は、マイクロフローで実行されるアクションです:

![アクティビティ](attachments/microflows-and-nanoflows/activity.png)

### 2.5 ループ {#loop}

[ループ](loop) はオブジェクトのリストを繰り返すために使用されます。

![ループ](attachments/microflows-and-nanoflows/loop.png)

オブジェクトごとに、ループ内のフローが実行されます。 ループアクティビティには、開始イベントと終了イベントを除き、マイクロフローで使用されるすべての要素を含めることができます。

### 2.6 パラメータ {#parameter}

[パラメータ](parameter) は、マイクロフローの入力として機能するデータである。

![パラメータ](attachments/microflows-and-nanoflows/parameter.png)

パラメータは、マイクロフローがトリガーされる場所に入力されます。

### 2.7 注釈 {#annotation}

[アノテーション](annotation) は、コメントをマイクロフローに置くために使用できる要素です。

![注釈](attachments/microflows-and-nanoflows/annotation.png)

### 2.6 アイテムの使用

Studio Pro は、選択した要素によって使用される項目を視覚化します。 これは、使用されているアイテムを青色の背景に白いテキストで表示することによって行います。 逆に、選択された要素によって返されたアイテムを使用する要素は、緑色の背景に白いテキストの単語「Usage」でマークされます。

以下の例では、パラメータ **AccountPasswordData** は、選択したアクティビティ (**アカウントの取得** ) で使用されているためハイライトされています。 **Save password** には **Usage** ラベルがあります。 なぜなら、 **Retrive Account** が返すオブジェクトを使用するからです。

![](attachments/microflows-and-nanoflows/microflow-nanoflow-example.png)

## 3 つのキーボードサポート{#keyboard}

マイクロフローエディタは、マイクロフローのナビゲートと操作のためのキーボードサポートを提供します。 次の表は、使用可能なキーを示しています。

| キー                                                | 効果                                              |
| ------------------------------------------------- | ----------------------------------------------- |
| 矢印キー                                              | 矢印方向の近くの要素 (アクティビティ、イベント、ループ、またはパラメーター) を選択します。 |
| <kbd>Enter</kbd>                                  | 選択した要素のプロパティを編集します。                             |
| <kbd>F2</kbd>                                     | 選択した要素によって返されるアイテムの名前を変更します。                    |
| <kbd>Shift</kbd> + <kbd>F2</kbd> または入力を開始する       | 選択した要素のキャプションを編集します。                            |
| <kbd>Ctrl</kbd> + 矢印キー                            | 選択した要素を矢印の方向に移動します。                             |
| <kbd>Tab</kbd>                                    | ループが選択されている場合、ループ内の最初の要素が選択されます。                |
| <kbd>Shift</kbd> + <kbd>Tab</kbd>                 | ループ内の要素が選択されている場合、ループ自体が選択されます。                 |
| <kbd>ホーム</kbd>                                    | 開始イベントを選択します。                                   |
| <kbd>終了</kbd>                                     | 終了イベントをサイクルします。                                 |
| コンテキストメニューキーまたは <kbd>Shift</kbd> + <kbd>F10</kbd> | 現在選択されている要素のコンテキストメニューを開きます。                    |

## 4 マイクロフローのデバッグ

マイクロフローの実行中に何が起こるかを見たい場合は、microflow デバッガを使用できます。 次の方法を参照してください。

*   [マイクロフローのデバッグ](/howto8/monitoring-troubleshooting/debug-microflows)
*   [マイクロフローのデバッグ](/howto8/monitoring-troubleshooting/debug-microflows-remotely)
