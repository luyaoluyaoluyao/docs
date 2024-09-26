---
title: "MxAssist Logic Bot"
parent: "マイクロフロー"
description: "Mendix Studio ProのMxAssist Logic Botについて説明します。"
tags:
  - "studio pro"
  - "logic bot"
  - mendix assist", "AI", "assist", "mx assist"
---

## 1つの紹介

MxAssist Logic Botは、Mendix Studio Proのアプリケーションロジック(マイクロフロー)のモデリングと構成を支援するAIを搭載した仮想共同開発ボットです。 すでに設計されているアクティビティ、パラメータ、およびその他のコンテキスト関連情報に基づいて、マイクロフローの次の最良のアクティビティについて、コンテキスト化されたおすすめを提供します。

MxAssist Logic Botは、1,200万を超える匿名化されたアプリケーションロジック(マイクロフロー)*—*Mendix*—*で構築された、マイクロフローのベストプラクティスパターンを検出して学習する機械学習分析を使用して構築されています。

MxAssistLogic Botの主な機能は以下のとおりです。

* **次のベストアクション提案** – 精度95%の40種類以上の異なる選択肢の中から、次のベストアクティビティトップ5を推奨しています。
* **自動構成** – 次の最適なアクションを提供するだけでなく、そのようなアクションのパラメータを事前に入力することで、さらに開発を自動化します。
* **文脈依存の提案** - 異なる方法で文脈を導きます 開発者が新しいアクティビティまたは決定を中流で挿入したときに、マイクロフローの左右を「見る」ことを含む; 文脈を推測するためにページが呼び出される場所を使っています
* **高精度** – 継続的な改善とモデルのトレーニングにより、精度レベルが95%から上昇しました。

## 2 MxAssist Logic Botの設定

マイクロフローエディタの右上隅で、MxAssist Logic Botのオンとオフを切り替えることができます。

MxAssist Logic Botの設定にアクセスする open **Edit** > **Preferences >**the **General** tab > **MxAssist Logic Bot** tab. 詳細については、 [環境設定](preferences-dialog) を参照してください。

**MxAssist Logic Bot** タブでは、次のように設定できます:

* **MxAssist Logic Bot を有効にする** – MxAssistLogic Botのオンとオフを切り替えます

* **Show suggestions for system variables** – when enabled, MxAssist Logic Bot will make suggestions for system objects (for example, it can suggest that you change such objects as **currentUser** or **currentSession**):

    ![Mxはシステム変数のためのロジックボットの提案](attachments/mx-assist-logic-bot/mx-assist-system-variables.png)

環境設定の詳細については、 [環境設定](preferences-dialog) を参照してください。

## 3 MxAssist Logic Botを使用してマイクロフローを構築

MxAssist Logic Bot はデフォルトで有効になっており、 [マイクロフロー](microflows) の中で青色のドットとして表示されます :

![ロジックボットアイコン](attachments/mx-assist-logic-bot/mendix-assist-icon.png)

ただし、MxAssist Logic Botを使用せずに、通常の方法で要素をマイクロフローに追加することは可能です。 MxAssist Logic Botは、最も関連性の高いアクティビティの短いリストを提案するため、要素をマイクロフローにすばやく追加できます。

MxAssist Logic Botを使用するには、次の操作を行います。

1. アイコンをクリックすると、次の最適なアクションの推奨事項が表示されます。

    ![ロジックボットの推奨事項](attachments/mx-assist-logic-bot/mx-assist-recommendations.png)

2. 推奨されるいずれかのアクティビティをクリックして、マイクロフローに挿入します。

3. **プロパティ** ダイアログボックスで、選択したアクティビティ/イベントを構成します。

アクティビティ/イベントがマイクロフローに追加されます。

トップ5のレコメンデーションリストに目的のアクティビティや要素が表示されない場合 **他の要素を追加** をクリックして、アクティビティ、ループ、意思決定、マージ、またはオブジェクトタイプの決定を選択できます。

## 4 続きを読む

* [マイクロフロー](マイクロフロー)
