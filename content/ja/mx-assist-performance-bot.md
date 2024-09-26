---
title: "MxAssistパフォーマンスボット"
parent: "表示メニュー"
menu_order: 50
description: "Mendix Studio ProのMxAssistパフォーマンスボットについて説明します。"
tags:
  - "studio pro"
  - "パフォーマンスボット"
  - mendix assist", "AI", "assist", "mx assist"
---

## 1つの紹介

MxAssist Performance Botはインテリジェントな仮想共同開発ボットで、Mendix Studio ProのMendix開発のベストプラクティスに対してアプリモデルを検査することで、アプリケーションのパフォーマンスを向上させることができます。 設計と開発中にアンチパターンを検出し、これらのアンチパターンを特定します。 解決方法を提案し、多くの場合、これらの問題を自動的に解決することができます。

MxAssist Performance Bot は、数千の匿名化された Mendix アプリの統計解析を使用して、一般的なアンチパターンを学び、マイクロフローの開発における Mendix Expert Services のベストプラクティスを使用して構築されています。 ドメインモデル、ページ、セキュリティなど

三段階の援助で構成されている。

1. **検出** - ボットはモデルを検査し、問題を特定し、問題を引き起こすドキュメント/要素を特定します。
2. **勧告** - ボットが同定された問題、潜在的な影響、およびそれを修正する方法を説明しています。 問題を解決する方法についての専用のステップバイステップガイドラインを備えた詳細なベストプラクティスガイドもあります。
3. **自動修正** – ボットは自動的にベストプラクティスを実装し、問題を修正できます。

## 2 MxAssistパフォーマンスボットペイン

MxAssistパフォーマンスボットの設定にアクセスする open **Edit** > **Preferences** >the **General** tab > **MxAssist Performance Bot** tab. 詳細については、 [環境設定](preferences-dialog) を参照してください。

MxAssist Performance Bot はデフォルトで有効になっており、ペインとして設計されています。 **MxAssist Performance Bot** ペインにアクセスするには、 **View** > **MxAssistPerformance Botをクリックしてください。**

ペインには、各アンチパターンに関する情報が表示され、MxAssistパフォーマンスボットの設定と構成が含まれています。

![パフォーマンスのボットペイン](attachments/mx-assist-performance-bot/performance-bot-pane.png)

### 2.1 オプションと設定

**MxAssist Performance Bot** ペインの上部には、次のオプションがあります。

* **今すぐ調査** – パフォーマンスの問題についてアプリモデルを検査します。

* **Limit to current tab** – ペインに表示されるメッセージを現在のドキュメントに制限します。

* **構成** - MxAssistパフォーマンスボットが分析するモジュールとドキュメントを定義する。 Click the **Configuration** button to open the **MxAssist Performance Bot Configuration** dialog box that contains the **Project Model** and **Best Practice** tabs.

    * **プロジェクト モデル** タブには、アプリケーション内のすべての関連ドキュメントが一覧表示されます。 特定のモジュールまたはドキュメントを検査または除外するかを選択できます。

        ![プロジェクトモデル](attachments/mx-assist-performance-bot/project-model.jpg)

    * **ベストプラクティス** タブには、利用可能なベストプラクティスがリストされています。 好みのベストプラクティスを選択し、モデルを検査することができます:

        ![ベスト練習](attachments/mx-assist-performance-bot/best-practice.jpg)

アプリモデルとベストプラクティスの両方の設定を一緒に使用できます。

### 2.2 アンチパターンの概要

ペイン内の各アンチパターンラインには、以下の情報が表示されます。

* **アイコン** - アンチパターンが自動的に修正されるかどうかを示します。アイコンに「A」文字がある場合、問題は自動的に修正されます。

* **Code** - アンチパターンタイプに固有のコード

* **ブルーサークル** - 新たに検出されたアンチパターンを示す

* **メッセージ** – 抗パターンの説明/説明

* **要素** - 問題を引き起こす要素

* **ドキュメント** – 要素を含むドキュメント

* **モジュール** - 文書を含むモジュール

    ![アンチパターンの概要](attachments/mx-assist-performance-bot/anti-pattern-overview.jpg)

ペイン内のアンチパターンのメッセージ行を右クリックすると、ドロップダウンメニューが開きます。

![ドロップダウンメニュー](attachments/mx-assist-performance-bot/drop-down-menu.jpg)

ドロップダウンメニューでは、次の操作を使用できます。

* **原因に移動** – 問題を引き起こす要素に移動します。
* **** - アンチパターンが使用されている対応する場所を開きます。
* **MxAssist Performance recommendation** – (メッセージをダブルクリックするのと同様に) ポップアップウィンドウを開きます。
* **既読にする** – 既読に問題をマークします。 これで青い円が消えます。
* **この勧告を抑制する** – 問題を抑制する。 これにより、問題が灰色で表示され、リストの一番下に送信されます。 エディタに関連するインジケータが消えます。

## 3 アプリ開発におけるMxAssistパフォーマンスボットの使用

### 3.1 アンチパターンの検出 {#detecting}

最初のレベルの支援は、アプリモデルの検査を含む **検出** です。 反パターンを特定し、問題の原因となっているドキュメントを特定します。

To inspect your app model, click **Inspect now** in the **MxAssist Performance Bot** pane.

{{% alert type="info" %}}

**Inspect now** オプションは、アプリに一貫性のあるエラーがある場合は無効になります。 この場合、まず一貫性エラーを解決する必要があります。

{{% /alert %}}

ボットはパフォーマンスのアンチパターンを検出し、関連するアンチパターンタイプの下のペインにリストします。 各アンチパターンタイプの詳細については、アンチパターンコードリンクをクリックしてください。 アンチパターンタイプの横にあるプラスアイコンをクリックすると、このタイプの検出されたケースが表示されます。

![アンチパターンの表示](attachments/mx-assist-performance-bot/viewing-anti-pattern.jpg)

アンチパターンが存在する要素またはドキュメントを表示するには メッセージ ラインをダブルクリックするか、メッセージ ラインを右クリックし、ドロップダウン メニューで **[** ] または **** を選択します。

### 3.2 修正を推奨する {#recommending}

2番目のレベルの支援は **勧告** です。問題の概要を説明し、解決方法を推奨します。

レコメンデーションを表示するには2つの方法があります。

1.  ペインでアンチパターンメッセージを右クリックし、ドロップダウンメニューで **View MxAssist Performance Recommendation** を選択します。

2. ビジュアルエディターのインジケーターをクリックすると、検出された問題が表示されます。

   ![エディタの指標](attachments/mx-assist-performance-bot/indicator-in-editor.jpg)

推奨事項には、特定された問題の説明が含まれており、そこからの潜在的な影響があります 問題を解決するためのより詳細なガイダンスへのリンクです

![パフォーマンス推奨事項](attachments/mx-assist-performance-bot/performance-recommendation.jpg)

### 3.3. アンチパターンの自動修正 {#auto-fixing}

3つ目のレベルの支援は、ボットが自動的にベストプラクティスを実装し、ワンクリックで問題を解決できる **自動修正** です。 望ましくない変更を避けるには 自動修正は、エラーを作成したり、モデルの他の望ましくない変更を行うことなく、ボットがコードを安全にリファクタリングできる場合にのみ利用できます。 パフォーマンスの問題には、自動修正可能かどうかを示すアイコンがペインに表示されます。 アイコンに「A」文字が含まれている場合、問題は自動修正されます。

{{% image_container width="45" %}}![自動修正アイコン](attachments/mx-assist-performance-bot/auto-fixable.png)
{{% /image_container %}}

問題を自動修正するには、以下の手順に従ってください。

1. ペイン内のメッセージ行を右クリックし、ドロップダウンメニューで **View MxAssist Performance Recommendation** を選択するか、エディタ内の対応するインジケータをクリックしておすすめを開きます。

2. **MxAssist Performance Recommendation** ポップアップウィンドウで、使用可能なアクションボタンをクリックします。たとえば、 **コミットを修正**:

    ![パフォーマンスの問題を修正](attachments/mx-assist-performance-bot/fix-performance-issue.jpg)

課題が自動修正されると、変更がポップアップウィンドウに表示されます。 **Show the fix** をクリックすると、変更されたドキュメントと要素が表示されます。

## 4 続きを読む

* [Mendixアシスタント](mx-assist-studio-pro)
* [MxAssist Logic Bot](mx-assist-logic-bot)
* [Mendixの開発のベストプラクティスを実装する方法](/howto/general/dev-best-practices)
