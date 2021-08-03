---
title: "一般情報"
description: "Mendix Studioのさまざまな機能について説明します。"
menu_order: 10
tags:
  - "スタジオ"
  - "studio pro"
aliases:
  - /ja/howto/tutorials/index.html
  - /ja/howto/tutorials/mendix-tutorials.html
---

## 1つの紹介 {#studio-overview}

Mendix Studioは、技術的な詳細を参照せずにMendixアプリケーションを作成、表示、編集できる場所です。 この目的のために、いつでも [Studio Pro](/refguide/modeling) を使用し、 [Studio Pro ユーザーと](collaborative-development) を一緒に開発することができます。

Studio を使用すると、PC にソフトウェアをインストールすることなく、ブラウザでアプリケーションを作成および編集できます。

以下の画像は、Studio インターフェイスのコンポーネントを示しています。

![スタジオ図](attachments/general/home-page.png)

## 2つのスタジオを開く

Mendix Studio は、 [Developer Portal](#opening-studio-via-dev-portal) または [Studio Pro](#opening-via-studio-pro) で開くことができます。

### 2.1 開発者ポータル経由でStudioを開く {#opening-studio-via-dev-portal}

Mendix Studio でアプリを編集するには、 [Developer Portal](https://home.mendix.com) でアプリを開き、 **Studio で編集** をクリックします。

{{% image_container width="350" %}}
![スタジオで編集](attachments/general/edit-app.jpg)
{{% /image_container %}}

If you do not see **Edit in Studio**, go to [General Settings](/developerportal/collaborate/general-settings) in the Developer Portal and [enable Studio](/developerportal/collaborate/general-settings#web).

### 2.2 Studio Pro 経由で Studio を開く {#opening-via-studio-pro}

Studio Pro 経由でアプリを開くこともできます。 次の操作を行います:

1. Studio Pro で、Studio で表示したいアプリを開きます。
2.  右上隅の地球儀アイコンをクリックします(Studio が有効な場合のみ使用できます)。

    ![グローブアイコン](attachments/general/globe-icon.png)

アプリはStudioで開きます。

## 3 アップグレードスタジオ

Studio で **編集** をクリックすると、アプリを最新バージョンにアップグレードする必要がある場合があります。

{{% image_container width="350" %}}![アップグレードする](attachments/general/upgrade.png)
{{% /image_container %}}

次のMendixバージョンへのアップグレードを示すトップバーも表示されるかもしれません。 Studio のアップグレードと Mendix バージョンの詳細については、 [Studio Ranges & Mendix Versions](general-versions) を参照してください。

{{% alert type="info" %}}
Studio で最新の Mendix バージョンにアプリをアップグレードする場合 Studio Pro のアプリを同じバージョンにアップグレードする必要があります。

あなたが他の人とチームで働いている場合。 全員がアプリを最新のMendixバージョンにアップグレードできるかどうかをチームメンバーに確認するのが賢明です。

{{% /alert %}}

## 4 アプリモードの切り替え

Studio を開くと、アプリのホームページが開きます。

対応するアイコンをクリックすると、ページのビューを異なるビューに変更できます。

* モバイル
* タブレット
* レスポンシブ（デスクトップ）

    {{% image_container width="300" %}}![デバイスモード](attachments/general/view.png)
    {{% /image_container %}}

## 5つの左メニューバー

左のメニューバーでは、Studio でページ、ドメインモデル、マイクロフロー、ワークフロー、ナビゲーションドキュメントにアクセスできます。 アプリ内のさまざまな要素を検索し、設定を開き、アプリの外観をカスタマイズします。

{{% image_container width="250" %}}
![左メニューバー](attachments/general/left-menu-bar.png)
{{% /image_container %}}

左のメニューバーのすべての項目は以下の表に記載されています:

| メニュー項目                         | ショートカット      | 説明                                                                                                                                                                                                                                                                       |
| ------------------------------ | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [ページ](page-editor)             | 1            | アプリ内のすべてのページの一覧を表示します。 ページを選択して開きます。                                                                                                                                                                                                                                     |
| [ドメインモデル](domain-models)       | 2            | アプリのドメインモデルを表示します。                                                                                                                                                                                                                                                       |
| [マイクロフロー](マイクロフロー)             | 3            | アプリ内のすべてのマイクロフローのリストを表示します。 マイクロフローを選択して開きます。                                                                                                                                                                                                                            |
| [ワークフロー](workflows)            | なし           | アプリ内のすべてのワークフローのリストを表示します。 ワークフローを選択して開きます。                                                                                                                                                                                                                              |
| [ナビゲーションドキュメント](navigation)    | 4            | ナビゲーション ツリーの形式で構成されたメニューを表示します。 ナビゲーションツリーのメニュー構造を、無制限のページ数で最大2つのレベルまで展開できます。                                                                                                                                                                                            |
| 検索(拡大ガラス) アイコン                 | <kbd>/</kbd> | マイクロフロー、図形、ページを検索するのに役立ちます。 探しているアイテムの名前を入力し始めると、検索機能は一致するものを返します。 入力された文字に基づいた曖昧な一致を使っています <br />"/" ショートカットを使ってアプリを検索することもできます。                                                                                                                                  |
| [テーマのカスタマイズ](theme-customizer) | なし           | カスタムブランディング、色、タイポグラフィでアプリのスタイルを設定できます。                                                                                                                                                                                                                                   |
| [設定](設定)                       | なし           | **設定** は **ロールと権限** と **ウィジェットの概要** で構成されます。 <br /> [ロールと権限](settings-security) を介して、さまざまなタイプのユーザーのアプリへのアクセスを管理できます。  <br /> [ウィジェットの概要](settings-widget-overview) は、すべてのウィジェットとそのステータスの概要を表示します。 ウィジェットは、ページを構築するために使用されるユーザーインターフェイス要素(アラート、ボタン、チャートなど)です。 |

## 6 Toolbox, Properties, Buzz

Studio の右上のメニューは、 **Toolbox**、 **Properties** 、および **Buzz** タブで構成されています。

![ツールボックス、プロパティ、バズ](attachments/general/toolbox-properties-buzz.png)

**Toolbox**, **Properties** , および **Buzz** タブは以下の表に記載されています:

| Tab                        | 説明                                                             |
| -------------------------- | -------------------------------------------------------------- |
| ツールバー                      | 現在のエディタで使用可能なツールを表示します。                                        |
| プロパティー                     | 選択したアイテムのプロパティが表示されます。                                         |
| [Buzz](collaboration-buzz) | アプリ開発チームにStudioの異なるページ、マイクロフロー、ドメインモデル、レイアウトへのコメントや相互作用を許可します。 |

## 7つのトップメニューバー

トップメニューバーでは、操作の取り消しやリアクション、最近のドキュメントの表示、アプリのプレビューや公開、アプリでのチェックの表示ができます。 また、ヘルプにアクセスして学習し、トップメニューバーでさまざまな情報を表示することもできます。

![トップメニューバー](attachments/general/top-bar.png)

上のメニューバーの項目は以下の表に記載されています。

| メニュー項目                     | 説明                                                                                                                                                                                                                  |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **スイッチ** メニュー              | **Switch-to** メニューでは、Mendix プラットフォームの他の部分に切り替えることができます。 このメニューには、次のオプションが含まれています。 <ul><li>**Mendix Home** – format@@0(/developerportal/index)</li><li>**Studio** – 開発者ポータルで **My Apps** 画面を開きます</li><li>**Studio Proを入手** – Mendix Studio Proの最新バージョンをダウンロード</li><li>**アカデミー** – format@@0(https://gettinged.mendixcloud.com) へのリンク</li><li>**ドキュメント** – format@@0(https://docs.mendix.com/) へのリンク</li></ul>                                                                                                          |
| 元に戻す/やり直しのアクション            | 最後の操作を元に戻したりやり直したりします。 <kbd>Ctrl</kbd>+<kbd>Z</kbd> と <kbd>Ctrl</kbd>+<kbd>Y</kbd> ショートカットも対応して使用できます。                                                                                                              |
| 最近使ったドキュメントのドロップダウンメニュー    | 現在表示しているドキュメントがこのオプションに表示されます。 ドロップダウンメニューをクリックすると、最近表示したドキュメントがリストに表示されます。 ドキュメントをクリックして開きます。                                                                                                                      |
| [プレビューボタン](publishing-app) | 公開後のアプリの見た目を表示します。                                                                                                                                                                                                  |
| [公開ボタン](publishing-app)    | このボタンでアプリを公開できます。 **公開** > **更新** をクリックして、Studio で行った最新の変更を公開します。 詳細については、 [プレビュー & アプリを公開する](publishing-app) を参照してください。                                                                                            |
| [チェックボタン](チェック)            | アプリのプレビューと公開を妨げる一貫性エラー(ある場合)を表示します。 For more information on errors, see [Consistency Errors](consistency-errors).<br />You can also use <kbd>C</kbd> shortcut to view the **Checks** panel.                   |
| ヘルプアイコン                    | **ヘルプ & 学習** サイドメニューを開きます。 どこでジャストインタイムのヘルプを見つけることができます - ビデオとハウツーは、現在のタスクの文脈で説明と指示を提供します。 例えば、ドメインモデルで作業する場合、ドメインモデルで動画とhow-toが表示されます。 推奨されるトピックとしてエンティティと属性があります。 ただし、Studio のすべての主な機能をカバーするカテゴリやその他のトピックも参照できます。 |
| **その他のオプション** アイコン         | 追加情報を提供します。 次の項目があります。<ul><li>**About** – format@@0(general-versions) の情報を表示します。 </li><li>**キーボードショートカット** – Studio でショートカットの一覧を開きます</li><li>**製品ツアーに参加** – ガイド付き製品紹介ツアーを開始し、スタジオを案内します</li><li>**Mendix Supportに連絡** – format@@0(https://support.mendix.com/hc/en-us) へのリンク</li><li>**Mendix Assistがオン** – [Mendix Assist](mx-assist) を有効/無効にする設定</li><li>**App Buzz** – デベロッパーポータルの format@@0(/developerportal/collection/buzz#app-buzz) に移動します。</li><li>**Studio Proで編集** – Studio Proでアプリを開く</li></ul>                                                                                                                                                                     |

## 8 カット/コピー/貼り付け 機能

ページとマイクロフローをコピー&ペーストできます。 ウィジェットやマイクロフローアクティビティなどの個別の要素を切り取り、コピー、および貼り付けることもできます。

### 8.1 ワークフロー、ページ、マイクロフロー、列挙型のコピー/貼り付け {#copy-paste-documents}

ワークフロー、ページ、マイクロフロー、列挙はクリップボードにコピーし、別のスタジオアプリに貼り付けることができます。 それらをコピーして同じアプリに貼り付けることもできますが、この目的に使用できる **Duplicate** オプションがあります。 For more information on how to copy, paste, or duplicate workflows, pages, microflows, and enumerations, see [Workflows](workflows), [Pages](page-editor), [Microflows](microflows), and [Enumerations](domain-models-enumeration) respectively.

ページ、マイクロフロー、列挙をコピー&ペーストするときは、以下に注意してください。

* ワークフロー、ページ、マイクロフロー、列挙は、同じMendixバージョンを持つStudioアプリのみにコピー/ペーストできます。
* ワークフロー、ページ、マイクロフロー、列挙は、同じブラウザのインスタンス間でのみコピー/ペーストできます。
* You *cannot* copy/paste from Studio Pro or versa

### 8.2 別の要素を切り取り/コピー/貼り付け

切り取り/コピー/貼り付け機能は、ページ、マイクロフロー、ワークフロー、ドメインモデル、ナビゲーションドキュメントのすべてのエディタで使用できます。 To cut/copy/paste you can use <kbd>Ctrl</kbd> + <kbd>X</kbd> /  <kbd>Ctrl</kbd> + <kbd>C</kbd> / <kbd>Ctrl</kbd> + <kbd>V</kbd> or  <kbd>Cmd</kbd> + <kbd>X</kbd> /  <kbd>Cmd</kbd> + <kbd>C</kbd> / <kbd>Cmd</kbd> + <kbd>V</kbd>.

カット/コピー/ペーストを使用する場合、以下の特性に留意してください:

* 1 つのビジュアルエディター内で要素を切り取り/コピー/貼り付けることができます。 つまり、1 ページ内またはStudio 内の他のページに要素をカット/コピー/貼り付けることができます。 1つのマイクロフローまたは他のマイクロフローにマイクロフローの活動をコピーします
* 同じMendixバージョンを使用している場合は、Studio内の異なるアプリに要素をカット/コピー/貼り付けることができます。
* ページ、マイクロフロー、ワークフロー、ページまたはマイクロフローの要素のみをコピー/ペーストすることはできません
* Studio から Studio Pro への切り取り/コピー/貼り付け、またはその逆はできません。

## このカテゴリ内の9つのメインドキュメント

* [Studio Ranges & Mendix Versions](general-versions) – Studio のバージョンが Mendix バージョンと相関する方法を説明します

