---
title: "オブジェクトを削除"
parent: "object-activity"
menu_order: 50
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/deleting-objects.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="warning" %}}
このアクティビティは、 **Microflow** でのみ使用できます。
{{% /alert %}}

## 1つの紹介

オブジェクトの削除は、1つまたは複数のオブジェクトを削除するために使用できます。

## 2つのプロパティ

以下の画像では、deleteオブジェクトプロパティの例を示します。

![オブジェクトのプロパティを削除](attachments/object-activities/delete-properties.png)

このアクティビティには2つのプロパティがあります。 左側のダイアログボックスと右側のプロパティ ペインに表示されています

削除オブジェクトプロパティペインは以下のセクションで構成されています:

* [アクション](#action)
* [一般的な](#common)

## 3つのアクションセクション{#action}

プロパティ ペインの **アクション** セクションには、このアクティビティに関連付けられたアクションが表示されます。

アクションの横にある省略記号 (**…**) をクリックすることで、このアクションを構成するためのダイアログボックスを開くことができます。

また、マイクロフロー内のアクティビティをダブルクリックするか、アクティビティを右クリックして **プロパティ** を選択することで、ダイアログボックスを開くこともできます。

### 3.1 オブジェクトまたはリスト

削除されるオブジェクトまたはオブジェクトのリストの名前。 リストを選択すると、そのリスト内のすべてのオブジェクトが削除されます。

### 3.2 クライアントで更新

この設定では、オブジェクトがデータベースから削除された後にデータソースを再実行するかどうかを定義します。

デフォルト: *いいえ*

{{% alert type="info" %}}
Mendix アプリのページを効率的にするために、多くのウィジェットはページにキャッシュされたオブジェクトの属性から値を表示します。 Attributes in widgets which use cached data are *always* reflected in the client even if they are not committed and irrespective of the value of **Refresh in client**. オブジェクトが削除されると、属性は null として表示されますが、オブジェクトは表示されます (例えば、 リストビューで削除されたオブジェクトの空白のエントリがあります)

If **Refresh in client** is set to *Yes* then all widgets will be updated, including those which are only updated when a [data source](data-sources) is loaded.

アプリをテストする際は、選択したウィジェットで希望するデータが表示されていることを確認してください。
{{% /alert %}}

#### 3.2.1 マイクロフローは、オンラインアプリでクライアントから呼び出されます

クライアントで **更新** が *いいえ*に設定されている場合 データソースは再実行されず、データを再読み込みする必要があるウィジェットはオブジェクトを表示します。

*はい*に設定した場合、削除はクライアント全体に反映され、関連する [データ ソース](data-sources) の再ロードを含みます。

#### 3.2.2 マイクロフローはオフライン、ネイティブ、またはハイブリッドアプリで呼び出されます

オフライン、ネイティブ、またはハイブリッドアプリから呼び出されるマイクロフロー内の場合 **クライアントの** オプションは無視され、 **いいえ** に設定されているかのように機能します。

詳細については、 [オフライン-First Reference Guide](offline-first#microflows) の *Microflow* セクションを参照してください。

## 4つの共通セクション{#common}

{{% snippet file="refguide8/microflow-common-section-link.md" %}}

## 5 削除中に何が起こるか?

Deleteボタンをクリックするか、削除アクティビティをトリガーすると、deleteイベントが開始されます。 さらに、構成された削除動作によってオブジェクトが削除されると、イベントの前後にすべて実行されます。

* イベント: すべてのイベントが実行され、before-delete イベントが false を返した場合、例外をスローできます。
    * イベント中に例外が発生した場合、デフォルトのエラー処理動作で適用されたすべての変更が元に戻されます。
    * ロールバック前に行われた変更は保持されます
* データベース: オブジェクトが状態を持つ場合 **インスタンス化**, データベース通信は必要ありません
    * 他のステータスでは、削除クエリがデータベースで実行されます。
* 結果: オブジェクトがメモリから削除され、該当する場合はデータベースから削除されます
    * 関連付けのすべての削除動作が検証され、関連するオブジェクトも削除されます。

![](attachments/object-activities/18582171.png)
