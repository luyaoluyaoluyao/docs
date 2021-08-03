---
title: "Mendixアシスタント"
category: "マイクロフロー"
menu_order: 10
description: "Descriptions Mendix AssistはMendix Studioにあります。"
tags:
  - "スタジオ"
  - "メンディックスのアシスタント"
  - "AI"
  - "アシスタント"
---

## 1つの紹介

Mendix Assistは、Mendix Studioでマイクロフローを構成するのに役立つ人工知能を搭載したエージェントです。 経験の浅いユーザーには、マイクロフローにすでに存在するアクティビティ、パラメータ、およびイベントに基づいて、マイクロフローの次のステップを設定することをお勧めします。

Mendix AssistはMendixで構築された1,200万以上の匿名化されたアプリケーションフローの機械学習分析を使用して構築されました。 Mendixは、Deep Learningを使用して、マイクロフローのベストプラクティスパターンを検出します。 これらのパターンに基づいてMendix Assistは、マイクロフロー内の次のアクティビティに最適なオプションを予測します。 さらに、Mendix Assistは、構築される新しいマイクロフローを分析することによって学習を続けています。

## 2 Mendix Assistの概要

Mendix Assistはデフォルトで有効になっており、 [マイクロフロー](microflows)の中で青色のドットとして表示されます。 点線の上にカーソルを合わせると、蝶ネクタイが現れます。

![](attachments/mx-assist/mendix-assist-icon.png)

{{% alert type="info" %}}

Mendix Assistを使用せずに定期的にアクティビティを追加することができます。

{{% /alert %}}

メンディックスアシストの推奨を表示するには、ボウタイをクリックします。

{{% image_container width="350" %}}![](attachments/mx-assist/mx-assist-recommendations.png)
{{% /image_container %}}

Mendixアシストは、特定のマイクロフローの可能性が最も低い推奨事項から上位5つの推奨事項をリストしています。 提案をクリックして、マイクロフローに挿入します。 詳細については、 [Mendix Assistでアクティビティと要素を追加する](#add-activities) セクションを参照してください。

{{% alert type="info" %}}

いくつかのアクティビティは、 **プロパティ** で正しく機能するように設定する必要があります。 これは、手動でエンティティと属性値を設定する必要がある場合、 **Create Object**のようなアクティビティに関係します。

{{% /alert %}}

Mendix Assistを使用して、マイクロフローに挿入するアクティビティまたはイベントを選択したら。 フローの上には、このアクティビティ/イベントの簡単な説明のある 情報ダイアログが表示されます。

![](attachments/mx-assist/info-dialog.png)

情報ダイアログボックスでは、次のオプションを使用できます。

* **今後表示しない** - 情報ダイアログボックスを無効にします (他のアクティビティを挿入すると再び表示されません)
* **詳細を見る** - マイクロフローの活動に関するドキュメントを開く
* **ありがとうございます** – 現在の情報ダイアログボックスを閉じます

## 3つの設定

Mendix Assistの設定を開くには、情報ダイアログの右上隅にある歯車アイコンをクリックします。

![](attachments/mx-assist/settings-mx-assist.png)

Mendix Assistで利用可能な設定については、以下の表を参照してください。

| 設定                    | 説明                                                                        |
| --------------------- | ------------------------------------------------------------------------- |
| Mendixアシストはオン/オフ      | ツールを有効/無効にする設定を切り替えます。                                                    |
| format@@0 ダイアログ オン/オフ | 情報ダイアログボックスの有効/無効を切り替えます。 **メモ** Mendix Assistがオフの場合、情報ダイアログボックスは無効になります。 |

Mendix Studioのトップメニューバーにある **その他のオプション** アイコンをクリックすることでMendixアシストを有効/無効にすることもできます:

![](attachments/mx-assist/mx-assist-is-on.png)

{{% alert type="info" %}}
Mendix Assistを無効にすると、情報ダイアログも無効になります。 Mendix Assistを再び有効にすると、情報ダイアログも再度有効になります。
{{% /alert %}}

## 4 メンディックスアシストでアクティビティと要素を追加する {#add-activities}

Mendix Assistを使用してさまざまなアクティビティを追加できます。 マイクロフローの複雑さと要素/アクティビティに応じて異なります。 すぐに挿入するか、Mendix Assistに追加情報を提供する必要があります。 たとえば、チェックを追加する場合は、チェックするオブジェクトまたは変数を指定する必要があります。 そして、どのような条件が正確にチェックされます:オブジェクトが存在する場合、またはオブジェクトが真の場合。 詳細については、 [チェックの追加](#add-check) セクションを参照してください。

### 4.1 アクティビティの追加

アクティビティ（ **オブジェクトの変更**、 **ページの表示**、 **オブジェクトの作成**など）を追加するには、次の操作を行います:

1. マイクロフローの青色のMendixアシストドットをクリックします。

2. 提案を参照し、必要なアクティビティを選択します。

3.  選択したアクティビティをクリックしてフローに追加します。

    {{% image_container width="350" %}}![](attachments/mx-assist/mx-assist-list.png)
    {{% /image_container %}}

アクティビティがフローに追加されます。

### 4.2 チェックを追加する {#add-check}

チェックを追加すると、 **Decision** with Boolean attribute type: あなたのフローは、 *true* と *false* とラベル付けされた別のフローに分割されます。 詳細については、 [Decision](microflows-decision) を参照してください。

![](attachments/mx-assist/check-added.png)

{{% alert type="info" %}}

変数、または、ブール型の属性を持たない場合、このオプションは提案にリストされていません 。

{{% /alert %}}

チェックを追加するには、次の操作を行います。

1. マイクロフローの青色のMendixアシストドットをクリックします。

2.  Find **小切手** を提案に追加します。

    {{% image_container width="350" %}}![](attachments/mx-assist/adding-check.png)
    {{% /image_container %}}

3. チェックのためのオプションの数が開かれ、追加するチェックを選択してクリックします。

この決定は、マイクロフローに追加されます。

{{% alert type="info" %}}

チェックのオプションの数は、マイクロフローのブール型の変数の数と、ドメインモデルのブール型の属性の数によって異なります。 詳細については、 [Domain Model](domain-models) および [属性](domain-models-attributes) を参照してください。 オブジェクトがマイクロフローが存在するかどうかを確認することもできます。

{{% /alert %}}

### 4.3 決定の追加

Mendix Assistを介して決定を追加する場合、それは列挙型の属性を持つ決定をマイクロフローに追加することを意味します。 詳細については、 [Decision](microflows-decision) and [Attributes](domain-models-attributes) を参照してください。 つまり、列挙型データ型のパラメータがない場合、 **Add decision** は提案には表示されません。

決定を追加するには、次の手順を実行します。

1. マイクロフローの青色のMendixアシストドットをクリックします。

2. 検索 **候補に意思決定** を追加し、選択します。

    {{% image_container width="350" %}}![](attachments/mx-assist/adding-decision.png)
    {{% /image_container %}}

この決定は、マイクロフローに追加されます。

{{% alert type="info" %}}

**Add a decision** のオプションの数は、マイクロフロー内の列挙型データ型を持つパラメータの数によって異なります。 詳細については、Studio [の](domain-models) Domain Model と [属性](domain-models-attributes) を参照してください。

{{% /alert %}}

## 5 続きを読む

* [一般情報](general)
* [マイクロフロー](マイクロフロー)
* [決定](microflows-decision)
