---
title: "Synchronize"
parent: "client-activities"
menu_order: 70
tags:
  - "studio pro"
  - "synchronize"
  - "オフライン"
  - "クライアントのアクティビティ"
---

{{% alert type="warning" %}}
このアクティビティは、オフラインファーストアプリ(ネイティブまたはオフラインPWAアプリ)で実行される **Nanoflows** でのみ使用できます。
{{% /alert %}}

## 1つの紹介

**** アクティビティを同期させると、デバイスとサーバー間でデータを同期させることができます。  アクションには以下の3つのモードがあります。

## 2 同期モード

### 2.1 すべてのオブジェクト

{{% image_container width="200" %}}
![Synchronize](attachments/client-activities/synchronize.png)
{{% /image_container %}}

**すべてのオブジェクト** モードは、ローカルデータベース全体を同期します。 サーバーデータベースは、ローカルデータベースからの変更によって更新されます。 ローカルデータベースは、ファイルの内容を含むサーバーからの最新データで更新されます。

このモードの動作は、 [同期構成](offline-first#customizable-synchronization) で設定できます。

### 2.2 同期していないオブジェクト {#unsynchronized-objects}

{{% image_container width="200" %}}
![Synchronize](attachments/client-activities/synchronize-unsynchronized-objects.png)
{{% /image_container %}}

**Unsychronized object** モードでは、コミットされた変更を持つすべてのオブジェクトが同期されます。 同期は双方向です。つまり、サーバーデータベースとローカルデータベースの両方がこれらのオブジェクトに対して更新されます。 詳細については、以下の [同期の動作](#synchronization-behavior) セクションを参照してください。

### 2.3 選択したオブジェクト {#selected-objects}

{{% image_container width="200" %}}
![Synchronize](attachments/client-activities/synchronize-objects.png)
{{% /image_container %}}

**選択されたオブジェクト** モードは、選択に基づいてオブジェクトを部分的に同期します:

{{% image_container width="600" %}}
![Synchronize](attachments/client-activities/synchronize-objects-selection.png)
{{% /image_container %}}

このモードでは、選択したオブジェクトまたはリストのみが同期されます。 同期は双方向です。つまり、サーバーデータベースとローカルデータベースの両方が選択したオブジェクトに対して更新されます。 詳細については、以下の [同期の動作](#synchronization-behavior) セクションを参照してください。

## 3つの同期動作 {#synchronization-behavior}

このセクションでは、 [非同期オブジェクト](#unsynchronized-objects) および [選択オブジェクト](#selected-objects) モードの動作について説明します。

{{% alert type="warning" %}}
[同期構成](offline-first#customizable-synchronization) の設定は、 **Unsychronized object** および **Selected objects(s)** モードには適用されません。
{{% /alert %}}

**選択されたオブジェクト** モードで 同期のために選択されたオブジェクトのセットにまだコミットされていないオブジェクトが含まれている場合 これらの物体はスキップされ同期されません

選択したオブジェクトにローカル変更がある場合、次の手順が実行されます。

1. サーバーデータベースは、ローカルデータベースからの変更によって更新されます。
2. ローカルデータベースがサーバーデータベースから更新されます。 これは、選択したオブジェクトが属性を計算したり、イベントハンドラの前後のマイクロフローで変更された場合に便利です。

選択したオブジェクトがサーバーから生成された場合 (デバイス上で作成されていない) サーバー上に存在しない (またはアクセスルールによりアクセスできません) ローカルの変更は適用されず、オブジェクトはローカルデータベースから削除されます。 この場合、そのオブジェクトの nanoflow 内の変数の値は `空の` になります。 サーバーは、データの損失を防ぐために、 `System.SynchronizationFailure` エンティティに破棄された変更を保存します。

同期のために選択されたオブジェクトのセットがローカル変更なしにオブジェクトを含んでいる場合、同期はサーバーデータベースからローカルコピーを更新します。 サーバーから削除されたオブジェクト、またはアクセスルールによりアクセスできなくなったオブジェクトがある場合。 そのオブジェクトはローカルデータベースからも削除されます

## 4つのプロパティ

**** アクティビティプロパティを同期するには、以下のセクションで構成されています:

* [アクション](#action)
* [一般的な](#common)

{{% image_container width="300" %}}![Synchronize Action Properties](attachments/client-activities/synchronize-properties.png){{% /image_container %}}

## 5アクションセクション {#action}

プロパティ ペインの **アクション** セクションには、このアクティビティに関連付けられたアクションが表示されます。

## 6つの共通セクション {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}

## 7つの制限 {#limitations}

同期モードにかかわらず、複数の同期プロセスを同時に実行することはサポートされていません。

同期中に別の同期プロセスをトリガーしようとすると、 次のエラーメッセージが表示されます。「同時同期の実行はサポートされていません。 現在の同期が完了したら、もう一度お試しください。

このようなエラーは、 [error handlers](/refguide/error-event#errorhandlers) を使用して同期の試みがトリガーされたnanoflowで処理できます。

## 8 続きを読む

* [アクティビティ](アクティビティ)
* [オフライン先](offline-first)
