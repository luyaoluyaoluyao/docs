---
title: "一般情報"
description: "Mendix Studioのさまざまな機能について説明します。"
menu_order: 10
tags:
  - "スタジオ"
  - "studio pro"
---

## 1つの紹介 {#studio-overview}

Mendix Studioは、技術的な詳細を参照せずにMendixアプリケーションを作成、表示、編集できる場所です。 この目的のために、 [Studio Pro](/refguide/modeling) を使用し、 [Studio Pro ユーザーと](general-collaborative-development) をいつでも一緒に開発できます。

Studio を使用すると、PC にソフトウェアをインストールすることなく、ブラウザでアプリケーションを作成および編集できます。

以下の画像は、Studio インターフェイスのコンポーネントを示しています。

![](attachments/general/home-page.png)

## 2つのスタジオを開く

Mendix Studio [は、Developer Portal](#opening-studio-via-dev-portal) または [Studio Pro](#opening-via-studio-pro) で開くことができます。

### 2.1 開発者ポータル経由でStudioを開く {#opening-studio-via-dev-portal}

Mendix Studio でアプリを編集するには、 [Developer Portal](https://home.mendix.com) でアプリを開き、 **Studio で編集** をクリックします。

![](attachments/general/edit-app.jpg)

If you do not see **Edit in Studio**, go to [General Settings](/developerportal/collaborate/general-settings) in the Developer Portal and [enable Studio](/developerportal/collaborate/general-settings#web).

### 2.2 Studio Pro 経由で Studio を開く {#opening-via-studio-pro}

Studio Pro 経由でアプリを開くこともできます。 次の操作を行います:

1. Studio Pro で、Studio で表示したいアプリを開きます。

2.  右上隅の地球儀アイコンをクリックします(Studio が有効な場合のみ使用できます)。

    ![](attachments/general/globe-icon.png)

アプリはStudioで開きます。

## 3 Studio Upgrade

Studio で **編集** をクリックすると、アプリを最新バージョンにアップグレードする必要がある場合があります。

{{% image_container width="350" %}}![](attachments/general/upgrade.png)
{{% /image_container %}}

{{% alert type="info" %}}
Studio で最新の Mendix バージョンにアプリをアップグレードする場合 Studio Pro のアプリを同じバージョンにアップグレードする必要があります。

あなたが他の人とチームで働いている場合。 全員がアプリを最新のMendixバージョンにアップグレードできるかどうかをチームメンバーに確認するのが賢明です。 この理由は、Studio をアップデートすると、Studio Pro もアップデートする必要があるためです。

{{% /alert %}}

## 4 アプリモードの切り替え

Studio を開くと、アプリのホームページが開きます。

対応するアイコンをクリックすると、ページのビューを異なるビューに変更できます。

*  モバイル
*  タブレット
*  レスポンシブ（デスクトップ）

    {{% image_container width="350" %}}![](attachments/general/view.png)
    {{% /image_container %}}

## 5つの左メニューバー

左のメニューバーには、次のオプションがあります。

{{% image_container width="350" %}}![](attachments/general/left-menu-bar.png)
{{% /image_container %}}

| メニュー項目                         | ショートカット      | 説明                                                                                                                                                                                                                                                                                 |
| ------------------------------ | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mxロゴ                           | なし           | Mx ロゴは、アプリの [Developer Portal](https://home.mendix.com) に戻るリターンボタンです。                                                                                                                                                                                                              |
| [ページ](page-editor)             | 1            | アプリ内のすべてのページの一覧を表示します。 ページを選択すると、Studio でページが開きます。                                                                                                                                                                                                                                 |
| [ドメインモデル](domain-models)       | 2            | アプリのドメインモデルを表示します。                                                                                                                                                                                                                                                                 |
| [マイクロフロー](マイクロフロー)             | 3            | アプリ内のすべてのマイクロフローのリストを表示します。  マイクロフローをクリックすると、Studio で開きます。                                                                                                                                                                                                                         |
| [ナビゲーションドキュメント](navigation)    | 4            | ナビゲーション ツリーの形式で構成されたメニューを表示します。 ナビゲーションツリーのメニュー構造を、無制限のページ数で最大2つのレベルまで展開できます。                                                                                                                                                                                                      |
| 検索(拡大ガラス) アイコン                 | <kbd>/</kbd> | マイクロフロー、図形、ページを検索するのに役立ちます。 探しているアイテムの名前を入力し始めると、検索機能は一致するものを返します。 入力された文字に基づいた曖昧な一致を使っています <br />"/" ショートカットを使ってアプリを検索することもできます。                                                                                                                                            |
| [設定](設定)                       | なし           | **設定** は **ロールと権限** と **ウィジェットの概要** で構成されます。 <br /> **[ロールと権限](settings-security)** を使用すると、異なるタイプのユーザーに対してアプリへのアクセスを管理できます。  <br /> [**ウィジェットの概要**](settings-widget-overview) は、すべてのウィジェットとそのステータスの概要を示します。 ウィジェットは、ページを構築するために使用されるユーザーインターフェイス要素(アラート、ボタン、チャートなど)です。 |
| [テーマのカスタマイズ](theme-customizer) | なし           | ここでは、カスタムブランディング、色、タイポグラフィでアプリのスタイルを設定できます。                                                                                                                                                                                                                                        |

## 6 Toolbox, Properties, Buzz

Studio の右上のメニューは、 **Toolbox**、 **Properties** 、および **Buzz** タブで構成されています。

![](attachments/general/toolbox-properties-buzz.png)

| Tab    | 説明                                                                         |
| ------ | -------------------------------------------------------------------------- |
| ツールバー  | 現在のエディタで使用可能なツールを表示します。                                                    |
| プロパティー | 選択したアイテムのプロパティが表示されます。                                                     |
| Buzz   | アプリ開発チームがStudioの異なるページ、マイクロフロー、ドメインモデル、ナビゲーションレイアウトへのコメントや相互作用を行うことを許可します。 |

## 7つのトップバー

上部のバーには、次のオプションがあります。

![](attachments/general/top-bar.png)

| トップバーのアイテム              | 説明                                                                                                                                                                                    |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ステータスアイコン               | Studio のインターネット接続状況を表示します。 ステータスが緑色の場合は、Studio が接続されます。 灰色の場合、Studio はオフラインです。                                                                                                        |
| 元に戻す/やり直しのアクション         | 最後の操作を元に戻すまたはやり直しします。 Ctrl+Z および Ctrl+Y ショートカットを適宜使用することもできます。                                                                                                                        |
| 最近使ったドキュメントのドロップダウンメニュー | 現在表示しているドキュメントがこのオプションに表示されます。 ドロップダウンメニューをクリックすると、最近表示したドキュメントがリストに表示されます。 ドキュメントをクリックして開きます。                                                                                        |
| [公開ボタン](publishing-app) | アプリをデプロイして実行します。 App を更新して、Studio で行った最新の変更をデプロイします。 デプロイ後、 **View** をクリックしてアプリを表示します。 詳細については、 [アプリの公開](publishing-app) を参照してください。                                                   |
| [チェックボタン](チェック)         | 現在アプリにエラーと警告が表示されます。 アプリにエラーが発生した場合は、問題を解決するまでアプリを公開することはできません。 エラーの詳細については、 [Consistency Errors](consistency-errors)を参照してください。<br />C ショートカットを使用して **Checks** パネルを表示することもできます。 |
| 情報アイコン                  | ここでは以下の情報を見つけることができます:<ul><li>**About** – format@@0(general-versions) の情報を表示します。 </li><li>**キーボードショートカット** – Studio でショートカットの一覧を開きます</li><li>**製品ツアーに参加** – ガイド付き製品紹介ツアーを開始し、スタジオを案内します</li><li>**コミュニティに問い合わせ** – format@@0(https://forum.mendixcloud.com/index4.html)へのリンク。Mendixコミュニティ全体から提供される知識を探ることができます。<li>**ドキュメントを確認** – format@@0(index) へのリンク</li><li>**Mendix Supportに連絡** – format@@0(https://support.mendix.com/hc/en-us) へのリンク<li>**Mendix Academy** – format@@0(https://academy.mendix.com) へのリンク</li><li>**Mendix Assistがオン** – [Mendix Assist](mx-assist) を有効/無効にする設定</li><li>**Studio Proで編集** – Studio Proでアプリを開く</li></ul>                                                                                                                                       |

## 8 カット/コピー/貼り付け 機能

切り取り/コピー/ペースト機能は、ページ、マイクロフロー、ドメインモデル、ナビゲーションなど、Studio のすべてのエディタで使用できます。 To cut/copy/paste you can use <kbd>Ctrl</kbd> + <kbd>Z</kbd> /  <kbd>Ctrl</kbd> + <kbd>C</kbd> / <kbd>Ctrl</kbd> + <kbd>V</kbd> or  <kbd>Cmn</kbd> + <kbd>Z</kbd> /  <kbd>Cmd</kbd> + <kbd>C</kbd> / <kbd>Cmd</kbd> + <kbd>V</kbd>.

カット/コピー/ペーストを使用する場合、以下の特性に留意してください:

* 1 つのエディタ内の要素を切り取り/コピー/貼り付けることができます。 つまり、1 ページ内またはStudio 内の他のページに要素をカット/コピー/貼り付けることができます。 1つのマイクロフローまたは他のマイクロフローにマイクロフローの活動をコピーします
* 同じMendixバージョンを使用している場合は、Studio内の異なるアプリに要素をカット/コピー/貼り付けることができます。
* ページやマイクロフロー、ページの要素またはマイクロフローのみをコピー/ペーストすることはできません
* Studio から Studio Pro への切り取り/コピー/貼り付けはできません

## 9 続きを読む

* [ドメインモデル](domain-models)
* [マイクロフロー](マイクロフロー)
* [ページ](page-editor)
