---
title: "MxAssist Logic Bot"
parent: "マイクロフロー"
description: "Mendix Studio ProのMxAssist Logic Botについて説明します。"
tags:
  - "studio pro"
  - "メンディックスのアシスタント"
  - "AI"
  - "アシスタント"
  - "mxアシストロジックボット"
  - "logic bot"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/mx-assist-studio-pro.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

MxAssist Logic Botは、Mendix Studio Proのアプリケーションロジック(マイクロフロー)のモデリングと構成を支援するAIを搭載した仮想共同開発ボットです。 すでに設計されているアクティビティ、パラメータ、およびその他のコンテキスト関連情報に基づいて、マイクロフローの次の最良のアクティビティについて、コンテキスト化されたおすすめを提供します。

MxAssist Logic Botは、1,200万を超える匿名化されたアプリケーションロジック(マイクロフロー)*—*Mendix*—*で構築された、マイクロフローのベストプラクティスパターンを検出して学習する機械学習分析を使用して構築されています。

MxAssistLogic Botの主な機能は以下のとおりです。

* **次のベストアクション提案** – 精度95%の40種類以上の異なる選択肢の中から、次のベストアクティビティトップ5を推奨しています。
* **自動構成** – 次の最適なアクションを提供するだけでなく、そのようなアクションのパラメータを事前に入力することで、さらに開発を自動化します。
* **文脈依存の提案** - 異なる方法で文脈を導きます 開発者が新しいアクティビティまたは決定を中流で挿入したときに、マイクロフローの左右を「見る」ことを含む; 文脈を推測するためにページが呼び出される場所を使っています
* **高精度** – 継続的な改善とモデルのトレーニングにより、精度レベルが95%から上昇しました。

## 2 MxAssist Logic Botの設定

MxAssist Logic Botの設定にアクセスするには、 **Edit** > **Preferences** >the **MxAssistLogic Bot** section. 詳細については、 [環境設定](preferences-dialog) を参照してください。

**MxAssist Logic Bot** のセクションでは、次のように設定できます:

* **MxAssist Logic Bot を有効にする** – MxAssistLogic Botのオンとオフを切り替えます

* **Show suggestions for system variables** – when enabled, MxAssist Logic Bot will make suggestions for system objects (for example, it can suggest that you change such objects as **currentUser** or **currentSession**):

  ![システム変数の提案](attachments/mx-assist-studio-pro/mx-assist-system-variables.png)

環境設定の詳細については、 [環境設定](preferences-dialog) を参照してください。

## 3 MxAssist Logic Botを使用してマイクロフローを構築

MxAssist Logic Botはデフォルトで有効になっており、 [マイクロフロー](/refguide8/microflows)の中で青色のドットとして表示されます。 点線上にカーソルを合わせると弓のネクタイが現れます。

{{% image_container width="350" %}}![Logic Bot Icon](attachments/mx-assist-studio-pro/mendix-assist-icon.png){{% /image_container %}}

ただし、MxAssist Logic Botを使用せずに、通常の方法で要素をマイクロフローに追加することは可能です。 MxAssist Logic Botは、最も関連性の高いアクティビティの短いリストを提案するため、要素をマイクロフローにすばやく追加できます。

MxAssist Logic Botを使用するには、次の操作を行います。

1. 次の最適なアクションの推奨事項を表示するには、弓のネクタイをクリックします。

    {{% image_container width="350" %}}![Logic Bot Recommendations](attachments/mx-assist-studio-pro/mx-assist-recommendations.png){{% /image_container %}}

2. 推奨されるいずれかのアクティビティをクリックして、マイクロフローに挿入します。

3. **プロパティ** ダイアログボックスで、選択したアクティビティ/イベントを構成します。

アクティビティ/イベントがマイクロフローに追加されます。

トップ5のレコメンデーションリストに目的のアクティビティや要素が表示されない場合 **他の要素を追加** をクリックして、アクティビティ、ループ、意思決定、マージ、またはオブジェクトタイプの決定を選択できます。

## 4 続きを読む

* [マイクロフロー](マイクロフロー)