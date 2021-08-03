---
title: "ウィジェット"
category: "ページ"
description: "Mendix Studioでウィジェットを説明します。"
tags:
  - "スタジオ"
  - "ページエディタ"
  - "ページ"
  - "ウィジェット"
---

## 1つの紹介

ウィジェットは、設定可能な単一のユーザーインターフェイス要素です。 ウィジェットの例としては、コンテナ、ドロップダウンメニュー、または異なる種類のボタンがあります。

{{% image_container width="300" %}}![](attachments/page-editor-widgets/widgets-examples.png)
{{% /image_container %}}

Studio 内のウィジェットはカテゴリごとにグループ化され、原点ごとに分類できます。

## 2件のウィジェットを表示

Mendix Studio でウィジェットを表示するには、次の手順を実行します。

1. 左のメニューバーの **ページ** アイコンをクリックします。

2. 表示されるアプリの一覧で、開くページを選択してクリックします。

3. **ツールバー** タブでは、 **ウィジェット** がデフォルトで開かれます。

   ![](attachments/page-editor-widgets/toolbox-widgets.png)

## ウィジェットプロパティの3つのクイック設定 {#quick-config}

プロパティのクイック設定は、ほとんどの非カスタム ウィジェットで利用できます。 つまり、これらのウィジェットをページに追加するときに、ポップアップウィンドウでプロパティを設定できます。

ウィジェットをドラッグ&ドロップすると、その隣に小さなポップアップウィンドウが表示されます。 ウィジェットが [一貫性エラー](consistency-errors) をもたらすことなく、必要なプロパティを機能させることができます。また、ウィジェットをすばやく設定できるように、他の頻繁に使用されるプロパティも設定できます。 ただし、 **プロパティ** タブからすべてのプロパティを常に設定できます。

たとえば、データ グリッドのデータ ソースを素早く構成することで、アプリケーションのプレビューやパブリッシュ時の一貫性エラーを回避できます。 あとで残りのプロパティを設定できます

![](attachments/page-editor-widgets/quick-config.png)

The pop-up window disappears once you start interacting with the page or the menu items, for example, if you start clicking elements on the page or if you open **Toolbox**, **Properties**, **Buzz**. クイック設定ポップアップウィンドウに再度アクセスするには、ウィジェットの右上隅にある歯車アイコンをクリックします。

![](attachments/page-editor-widgets/quick-widget-icon.png)

## カテゴリ別の4件のウィジェット {#widget-categories}

Studio のウィジェットは、 **ウィジェット** タブを開いたときに確認できるカテゴリに分かれています。

{{% image_container width="350" %}}![](attachments/page-editor-widgets/widgets-categories.png)
{{% /image_container %}}

ウィジェットのカテゴリは以下の表に記載されています:

| ウィジェットのカテゴリ                                       | 説明                                                                                                                                                                                                                                                                                                                         |
| ------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| データコンテナ                                           | Contains a [data view](page-editor-data-view-list-view) (the starting point for showing the contents of one object),  [list view](page-editor-data-view-list-view) (the starting point for showing the contents of list of objects), and a [data grid](page-editor-data-grid) (shows a list of objects in a table format). |
| [構成](page-editor-widgets-structure)               | 配置ウィジェットを制御するための特定の列数とウィジェットを持つ事前設定のレイアウト グリッドが含まれています。                                                                                                                                                                                                                                                                    |
| [入力要素](page-editor-widgets-input-elements)        | データの入力に使用できる要素が含まれています。                                                                                                                                                                                                                                                                                                    |
| [テキスト](page-editor-widgets-text)                  | テキスト表示ウィジェットが含まれます。                                                                                                                                                                                                                                                                                                        |
| [画像 & ファイル](page-editor-widgets-images-and-files) | 画像の表示、ファイルのアップロード、および画像のダウンロードに役立つウィジェットが含まれています。                                                                                                                                                                                                                                                                          |
| [ボタン](page-editor-widgets-buttons)                | ページを開いたり閉じたり、microflowを呼び出したり、ユーザーにサインアウトしたり、リンクを開いたりといった一般的なアクションを持つボタンが含まれています。                                                                                                                                                                                                                                          |
| [データボタン](page-editor-widgets-buttons)             | データを操作し、オブジェクトの作成や削除、変更の保存やキャンセルに使用するボタンが含まれています。                                                                                                                                                                                                                                                                          |
| [ワークフローボタン](page-editor-widgets-buttons)          | Contains buttons that are related to [workflows](workflows) and are used to call  a workflow, complete or show a [user task](workflows-user-task), show a workflow page.                                                                                                                                                   |
| [Menus](/refguide/menu-widgets)                   | メニュー作成ウィジェットが含まれています。 現在、これらのウィジェットはStudio Proでのみ設定できます。                                                                                                                                                                                                                                                                   |
| アドオン                                              | アプリにインストールされているすべてのカスタム ウィジェットが含まれています。 ウィジェットが Marketplace プロファイルと一致しない場合、ウィジェットはアドオンに表示されます。                                                                                                                                                                                                                             |
| グラフ                                               | 異なるチャートが含まれています。 このカテゴリは [マーケットプレイスウィジェット](#app-store-widgets) で構成されています。                                                                                                                                                                                                                                                  |
| 表示                                                | マップやプログレスバーなど、ページに変更要素を表示するウィジェットが含まれています。 このカテゴリは [マーケットプレイスウィジェット](#app-store-widgets) で構成されています。                                                                                                                                                                                                                        |
| リストビューコントロール                                      | リストビューのコントロールが含まれています。 このカテゴリは [マーケットプレイスウィジェット](#app-store-widgets) で構成されています。                                                                                                                                                                                                                                            |

## 原産地別の5つのウィジェット {#widgets-by-origin}

Studio のウィジェットは、以下の表のように原点で分割できます。

| タイプ                                       | 説明                                                                                                                                                                                                                                                                              | 原点：                                                                             |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| 既定のウィジェット                                 | デフォルトでアプリに含まれているウィジェットで、右上隅に情報アイコンがありません。                                                                                                                                                                                                                                       | 開発者ポータルで作成されたアプリ (開発者ポータルの詳細については、 [開発者ポータル](/developerportal/index) を参照してください) |
| マーケットプレイスのウィジェット<a name="app-store-widgets"></a> | Studio からアプリに直接ダウンロードできるウィジェット。 一部の Marketplace ウィジェットは、アプリの一部としてすでにお使いのアプリにあります。 このようなウィジェットには、 **ツールバー** 内のウィジェットの右上隅に情報アイコンがあります。 <br />マーケットプレイスの詳細については、 [マーケットプレイスの概要](/appstore/general/app-store-overview) を参照してください。                                             | [市場](/appstore/index)                                                           |
| ローカルウィジェット                                | アプリテンプレートの一部であるウィジェット、またはStudio Proを介してローカルまたはチームによって作成されたウィジェットのいずれか。 ウィジェットの開発についての詳細は、 [プラグイン可能なウェブウィジェット](/howto/extensibility/pluggable-widgets) how-toを参照してください。 原則として、ローカルウィジェットは **アドオン** カテゴリにリストされます。 カテゴリの詳細については、 [カテゴリ別ウィジェット](#widget-categories) セクションを参照してください。 | Developer Portal/Studio Proで作成されたアプリ                                            |

## 6 マーケットプレースのウィジェットの追加

Studio の **ウィジェット** タブから直接ダウンロードして、Marketplace ウィジェットをアプリに追加できます。 これらのウィジェットは Marketplace で利用可能なすべてのウィジェットのサブセットです。Studio で使用を承認されたウィジェットのみをダウンロードできます。 アップデートが利用可能であればアップデートすることもできます。

Marketplace ウィジェットを追加するには、次の手順を実行します。

1. **ウィジェット** タブを開きます。

2.  次のいずれかを実行します。 <br />

    a **マーケットプレイスウィジェット** オプションでカテゴリを見つけてクリックします。  <br />

    {{% image_container width="300" %}}![](attachments/page-editor-widgets/view-app-store-widgets.png)
 {{% /image_container %}}<br />

    B  **検索** フィールドに、カテゴリまたは特定のウィジェットの名前を入力します。 <br />

    ![](attachments/page-editor-widgets/slider.png)

3.  クラウドアイコンをクリックしてウィジェットをダウンロードし、アプリに追加します。

    ![](attachments/page-editor-widgets/app-store-download.png)

ウィジェットがアプリに追加されました。それを使用するには、単純にページにドラッグ&ドロップできます。 **アプリ設定** でこのウィジェットの設定を表示することもできます。  アプリ内のウィジェット管理の詳細については、 [設定](settings) を参照してください。

{{% alert type="info" %}}

いくつかの似たようなウィジェットが一緒にパッケージ化されています:これらのウィジェットの1つをダウンロードすると、他の多くのウィジェットもダウンロードされます。 たとえば、折れ線グラフをダウンロードすると、すべてのグラフのウィジェットが表示されます。

{{% /alert %}}

## 7 続きを読む

* [ページ](page-editor)
* [設定](設定)
* [マーケットプレースの概要](/appstore/general/app-store-overview)
