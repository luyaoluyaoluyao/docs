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

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/synchronize.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="warning" %}}
このアクティビティは **Nanoflows** でのみ使用できます。
{{% /alert %}}

## 1つの紹介

**** アクティビティを同期させると、デバイスとサーバー間でデータを同期させることができます。  **** アクションを同期する 2 つのモードがあります:

### 1.1 すべてのオブジェクトを同期

{{% image_container width="200" %}}
![Synchronize](attachments/client-activities/synchronize.png)
{{% /image_container %}}

このモードでは、ローカルデータベース全体が同期されます。 サーバーデータベースは、ローカルデータベースからの変更によって更新されます。 ローカルデータベースは、ファイルの内容を含むサーバーからの最新データで更新されます。

このモードの動作は、 [****](offline-first#customizable-synchronization) で設定できます。

### 1.2 選択したオブジェクトを同期する

{{% image_container width="200" %}}
![Synchronize](attachments/client-activities/synchronize-objects.png)
{{% /image_container %}}

このモードは、選択に基づいてオブジェクトを一部同期します。

{{% image_container width="600" %}}
![Synchronize](attachments/client-activities/synchronize-objects-selection.png)
{{% /image_container %}}

このモードでは、選択したオブジェクトまたはリストのみが同期されます。 同期は双方向の で、選択したオブジェクトに対してサーバーデータベースとローカルデータベースの両方が更新されます。

同期のために選択されたオブジェクトのセットにまだコミットされていないオブジェクトが含まれている場合 これらの物体はスキップされ同期されません

選択したオブジェクトにローカル変更がある場合、次の手順が実行されます。

1. サーバーデータベースは、ローカルデータベースからの変更によって更新されます。
1. ローカルデータベースがサーバーデータベースから更新されます。 これは、選択したオブジェクトが属性を計算したり、イベントハンドラの前後のマイクロフローで変更された場合に便利です。

選択したオブジェクトがサーバーから生成された場合 (デバイス上で作成されていない) サーバー上に存在しない (またはアクセスルールによりアクセスできません) ローカルの変更は適用されず、オブジェクトはローカルデータベースから削除されます。 この場合、そのオブジェクトの nanoflow 内の変数の値は `空の` になります。 サーバーは、データの損失を防ぐために、 `System.SynchronizationFailure` エンティティに破棄された変更を保存します。

同期のために選択されたオブジェクトのセットがローカル変更なしにオブジェクトを含んでいる場合、同期はサーバーデータベースからローカルコピーを更新します。 サーバーから削除されたオブジェクト、またはアクセスルールによりアクセスできなくなったオブジェクトがある場合。 そのオブジェクトはローカルデータベースからも削除されます

## 2つのプロパティ

**** アクティビティプロパティを同期するには、以下のセクションで構成されています:

* [アクション](#action)

* [一般的な](#common)

    {{% image_container width="300" %}}![Synchronize Action Properties](attachments/client-activities/synchronize-properties.png){{% /image_container %}}

## 3 アクションセクション {#action}

プロパティ ペインの **アクション** セクションには、このアクティビティに関連付けられたアクションが表示されます。

## 4つの共通セクション {#common}

{{% snippet file="refguide8/microflow-common-section-link.md" %}}

## 5つの制限事項 {#limitations}

型にかかわらず、複数の同期プロセスを同時に実行することはサポートされていません (**full** または **selective**)。

同期中に別の同期プロセスをトリガーしようとすると、次のエラーメッセージが表示されます:

**同時同期の実行はサポートされていません。 現在の同期が完了したら、もう一度お試しください。**

このようなエラーは、 [error handlers](/refguide8/error-event#errorhandlers) を使用して同期の試みがトリガーされたnanoflowで処理できます。

## 6もっと読む

* [アクティビティ](アクティビティ)
* [オフライン先](offline-first)
