---
title: "オブジェクトをロールバックする"
parent: "object-activity"
menu_order: 70
tags:
  - "studio pro"
---

{{% alert type="warning" %}}
このアクティビティは、 **Microflow** と **Nanoflows** の両方で使用できます。
{{% /alert %}}

## 1つの紹介

ロールバック・オブジェクト・アクションを使用すると、アクティビティより前のフローの部分でオブジェクトに加えられた変更(コミットされていない)を取り消すことができます。 さらに、作成されたがコミットされていないオブジェクトを削除します。

{{% alert type="info" %}}
ロールバック・オブジェクト・アクションがサブ・マイクロフローで実行されると、その親マイクロフローとサブ・マイクロフローの変更がロールバックされます。
{{% /alert %}}

## 2つのプロパティ

ロールバックオブジェクトのプロパティの例を以下の画像に示します。

![ロールバックオブジェクト プロパティ](attachments/object-activities/rollback-properties.png)

このアクティビティには2つのプロパティがあります。 左側のダイアログボックスと右側のプロパティ ペインに表示されています

rollback オブジェクトのプロパティペインは、次のセクションで構成されます。

* [アクション](#action)
* [一般的な](#common)

## 3つのアクション{#action}

プロパティ ペインの **アクション** セクションには、このアクティビティに関連付けられたアクションが表示されます。

アクションの横にある省略記号 (**…**) をクリックすることで、このアクションを構成するためのダイアログボックスを開くことができます。

また、マイクロフロー内のアクティビティをダブルクリックするか、アクティビティを右クリックして **プロパティ** を選択することで、ダイアログボックスを開くこともできます。

### 3.1 オブジェクト

**オブジェクト** はロールバックが必要なオブジェクトを定義します。

### 3.2 クライアントで更新

この設定では、エンドユーザーに表示されるページに変更が反映される方法を定義します。

デフォルト: *いいえ*

{{% alert type="info" %}}
Mendix アプリのページを効率的にするために、多くのウィジェットはページにキャッシュされたオブジェクトの属性から値を表示します。 Attributes in widgets which use cached data are *always* reflected in the client even if they are not committed and irrespective of the value of **Refresh in client**.

If a widget is only updated when a [data source](data-sources) is loaded, then rollbacks will only be seen if they are committed and **Refresh in client** is set to *Yes*.

アプリをテストする際は、選択したウィジェットで希望するデータが表示されていることを確認してください。
{{% /alert %}}

#### 3.2.1 マイクロフローは、オンラインアプリでクライアントから呼び出されます

**Refresh in client** が *No*に設定されている場合、ロールバックはクライアントに反映されません。

*はい*に設定すると、関連する [データ ソース](data-sources) の再ロードを含む、オブジェクトはクライアント全体でリフレッシュされます。

#### 3.2.2 マイクロフローはオフライン、ネイティブ、またはハイブリッドアプリで呼び出されます

オフライン、ネイティブ、またはハイブリッドアプリから呼び出されるマイクロフロー内の場合 **クライアントの** オプションは無視され、 **いいえ** に設定されているかのように機能します。

詳細については、 [オフライン-First Reference Guide](offline-first#microflows) の *Microflow* セクションを参照してください。

#### 3.2.3 アクションはNanoflow にあります

When inside a [nanoflow](nanoflows), the rollback object action reloads [data sources](data-sources) as if **Refresh in client** was set to *Yes*.

## 4つの共通セクション{#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}

## 5ロールバックは何をしますか?

{{% alert type="info" %}}
マイクロフローまたはナノフローのロールバックアクションは、マイクロフローの [Error Event](error-event#errors-in-microflows) のロールバックオプションと同じではありません。

error イベントからのロールバックはロールバックイベントをトリガーせず、オブジェクトへの変更がコミットされているかどうかは反映されません。
{{% /alert %}}

**キャンセル** ボタンを押すか、ロールバックアクティビティをトリガーすると、ロールバックイベントが開始されます。

* **イベント**: すべてのイベントが実行される前後のイベント
    * before-rollback イベントが false を返した場合、例外を投げることができます。
    * イベント中に例外が発生した場合、デフォルトのエラー処理動作で適用されたすべての変更が元に戻されます。
    * ロールバック前に行われた変更は保持されます
* **データベース**: beforeまたはafter-create イベントで指定されていない限り、このイベントではデータベース通信が行われません。
* **結果**: 状態のオブジェクト **インスタンス化** が削除されます。 そして、他の状態を持つオブジェクトは、最後のコミット時に与えられた値に戻されます。

![](attachments/object-activities/18582170.png)
