---
title: "画像 & ファイル"
parent: "page-editor-widgets"
description: "Mendix Studioで画像とファイルのウィジェットを説明します。"
menu_order: 30
tags:
  - "スタジオ"
  - "ページエディタ"
  - "画像"
  - "画像ウィジェット"
  - "ウィジェット"
  - "ファイル"
  - "ファイルマネージャー"
  - "ファイルアップローダー"
  - "ファイルダウンローダー"
---

## 1つの紹介

**イメージ & ファイル** は、エンドユーザーが画像やファイルを表示、ダウンロード、アップロードできるウィジェットです。 たとえば、アップローダーのエンドユーザーがプロフィール画像をアップロードできるようになります。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-images-and-files/image-uploader-example.png)
{{% /image_container %}}

Mendix Studio には以下の画像とファイルのウィジェットがあります:

* **イメージ** – アプリに静的(変更なし)イメージを表示することができます

*  **ダイナミックイメージ** – 動的イメージを表示することができます(例えば、 アプリ内の関連するプロフィール写真

*  **Image Uploader** – エンドユーザーが画像をアップロードできるようにする

*   **File Manager** – allows end-users to upload or/and download a file (in the **Toolbox**, you see  preconfigured file managers: **File Uploader** and **File Downloader**)

    {{% image_container width="350" %}}![](attachments/page-editor-widgets-images-and-files/images-and-files.png)
    {{% /image_container %}}

## 2画像と動的画像

イメージと動的イメージウィジェットを使用すると、ファイル(静的)またはデータベース(動的)からイメージを表示することができます。

プロパティで、あるウィジェットから別のウィジェットに切り替えることができます。

![](attachments/page-editor-widgets-images-and-files/static-and-dynamic-image.png)

### 2.1 プロパティ

#### 2.1.1 一般セクション {#image-general}

**General** セクションでは、静的イメージと動的イメージの切り替え、画像の選択、幅と高さの設定などができます。

**動的画像** の **一般**セクションで設定を行う前に。 データコンテナ(リストビューまたはデータビュー)内でのみ機能することができます。 既存のデータコンテナにウィジェットを配置することができます。 または **プロパティ** の **新しいデータ ビュー** をクリックして自動的にデータ ビューを作成し、その中に入力要素を配置します。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-images-and-files/dynamic-image-data-view.png)
{{% /image_container %}}

**Static Image** と **Dynamic Image** の設定は以下の表に示されています:

| 属性       | このプロパティは以下に適用されます。 | 説明                                                                                                                                                       |
| -------- | ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 画像のソース   | 静的および動的画像          | (ファイルから) スタティック画像と (データベースから) ダイナミック画像を切り替えます。                                                                                                           |
| エンティティ   | 動的画像               | 動的イメージに表示するエンティティを指定します。 動的イメージのエンティティは、イメージエンティティの場合にのみ設定できます。 イメージエンティティの詳細については、 [ドメイン モデル](domain-models#entity-types) の *エンティティの種類* セクションを参照してください。 |
| 画像       | 静的画像               | エンドユーザーに表示される画像を設定します。                                                                                                                                   |
| デフォルトの画像 | 動的画像               | データベースに保存されている場合に表示される画像です。                                                                                                                              |
| 幅の単位     | 静的および動的画像          | 画像の幅は以下の方法で指定できます:  <br /><ul><li>**自動** – 与えられた画像の幅が使用されます。</li><li>**ピクセル** – 幅は数ピクセルで指定されます。 幅と高さの両方を指定すると、画像は自動的にスケーリングされます。プロポーションは保持され、画像はストレッチされません。</li><li>**パーセント** – 幅は元の幅のパーセントで指定されます。 画像が伸びている場合は、元の幅よりも大きくすることができます。</li></ul><br />Default value for **Width Unit**: Auto                                              |
| Width    | 静的および動的画像          | **Width** オプションは、 **Pixel** または **Percentage** が **Width Unit** に選択されている場合にのみ表示されます。 画像の幅をピクセルまたはパーセンテージで指定します。                                          |
| 高さの単位    | 静的および動的画像          | 画像の高さは以下の方法で指定できます:  <br /><ul><li>**自動** – 指定した画像の高さが使用されます。</li><li>**ピクセル** – 高さはピクセル数で指定されます。 幅と高さの両方を指定すると、画像は自動的にスケーリングされます。プロポーションは保持され、画像はストレッチされません。</li><li>**パーセント** – 高さは元の高さのパーセントで指定されます。 画像が伸びている場合は、元の高さよりも大きくすることができます。</li></ul><br />**高さ単位**: 自動                                                                       |
| 高さ       | 静的および動的画像          | **高さ** オプションは、 **ピクセル** または **パーセント** が **高さユニット**に選択されている場合にのみ表示されます。 画像の高さをピクセルまたはパーセンテージで指定します。                                                       |

#### 2.1.2 イベントセクション

**イベント** セクションで **クリックアクション** を選択できます。 **on Click Action** は、ユーザーが画像をクリックしたときに実行されるアクションを定義します。

##### 2.1.2.1 一般的なプロパティ

The static image and the dynamic image share the properties in the **Events** section, except for one property that is [specific for the dynamic image](#events-dynamic-image).

静的および動的イメージの **イベント** セクションの詳細については、 [ウィジェットのイベント セクション](page-editor-widgets-events-section) を参照してください。

##### 2.1.2.2 動的イメージ固有のプロパティ {#events-dynamic-image}

ダイナミックイメージには、特定のオンクリックアクション **クリックで拡大**があります。 フルサイズの画像は、ユーザーがそれをクリックすると表示されます。 このプロパティは、他のオンクリック操作を上書きします。

#### 2.1.3 条件付き表示セクション

{{% snippet file="studio/visibility-section-link.md" %}}

#### 2.1.4 デザインセクション

**デザイン** セクションとそのプロパティについては、ウィジェットの [デザインセクション](page-editor-widgets-design-section) を参照してください。

## 3 画像アップローダーとファイルマネージャー

**画像アップローダー** はエンドユーザーがあなたのアプリに画像をアップロードし、アップロードされた画像のサムネイルを生成します。 たとえば、ユーザーは自分のプロフィールの写真をアップロードできます。

画像アップローダーは、データビューまたはデータソースとして画像エンティティを持つリストビュー内に配置する必要があります。  イメージエンティティの詳細については、 [ドメイン モデル](domain-models#entity-types) の *エンティティの種類* セクションを参照してください。

**ファイルマネージャー** により、エンドユーザーはファイルをアップロードおよび/またはダウンロードできます。 たとえば、ユーザーは必要なデータを含むスプレッドシートをダウンロードできます。

ファイルマネージャは、データビューまたはファイルエンティティをデータソースとして持つリストビュー内に配置する必要があります。  ファイルエンティティの詳細については、 [ドメイン モデル](domain-models#entity-types) の *エンティティの種類* セクションを参照してください。

アップロード/ダウンロードできるファイルと画像のデフォルトの最大サイズは5MBです。 Studio Pro で最大サイズを変更できます。 Studio Pro のプロパティの詳細については、 [File Manager](/refguide8/file-manager) および [Image Uploader](/refguide8/image-uploader) を参照してください。

Studio Pro で特に指定しない限り、すべてのファイル拡張子はイメージアップローダーとファイルマネージャに使用できます。 Studio Pro のプロパティの詳細については、 [File Manager](/refguide8/file-manager) および [Image Uploader](/refguide8/image-uploader) を参照してください。

### 3.1 プロパティ

#### 3.1.1 データソースセクション

**Data Source** セクションは、 **Context Entity** オプションで構成されています。 **Context Entity** は(ファイルマネージャを使用している場合)ファイルエンティティまたは(イメージアップローダーを使用している場合)周辺のデータビューまたはリストビューのイメージエンティティを使用します。 **コンテキストエンティティ** が自動的に設定され、読み取り専用です。

#### 3.1.2 一般セクション

**一般的な** セクションプロパティについては以下に説明します。

##### 3.1.2.1 ラベルの表示

エンドユーザーにウィジェットのラベル (名前) を表示する場合は、このプロパティを有効にします。 *このプロパティはデフォルトで有効になっています。*

##### 3.1.2.2 ラベル

このプロパティは、 **Show Label** が有効な場合にのみ表示されます。 エンドユーザーに表示される名前を指定します。 属性を選択すると、属性の名前がブレース内のラベルに表示されます。 これは、静的なテキストの代わりに、属性の値がエンドユーザーに表示されることを意味します。

##### 3.1.2.3 編集可能 {#editability}

編集可能性は、エンドユーザーがウィジェットによって表示される値を変更できるかどうかを示します。 可能な値は次のとおりです。

* **編集可能** - ウィジェットに表示される値は編集可能

* **読み取り専用** – 値は読み取り専用モードです

* **Conditional** – the widget is editable only if specified conditions are met based on an attribute value (for more information, see  [Attribute-Based](#attribute-based) and [Attribute Values](#attribute-values) sections below) or based on an expression. Studio Pro でのみ、式に基づいて条件を作成できます(詳細については)。 [ページエディターで共通のプロパティ](/refguide8/common-widget-properties#editability) の *編集可能セクション* を参照 )

  {{%alert type="info" %}}If an attribute set for the widget's data source is of the AutoNumber type, the widget is set into read-only mode by default and the **Editability** setting itself is disabled, because attributes of this type are generated automatically.

  {{%/alert %}}

##### 3.1.2.4 属性ベース {#attribute-based}

**Attribute-Based** プロパティは [Conditional Editability](#editability) が選択されている場合にのみ表示されます。

**Attribute-Based** の条件付き編集では、選択した属性の特定の値に一致するウィジェットを表示することができます。

{{%alert type="info" %}}

属性は、ブール型または列挙型でなければなりません。

{{%/alert %}}

{{%alert type="info" %}}

データコンテナ内にウィジェットが配置されている場合(データビューまたはリストビュー)にのみ、属性ベースの条件付き編集機能を設定できます。 ウィジェットをページに配置する方法についての詳細は、 [ページ](page-editor#adding-elements) の *ページ* のセクションで要素を追加するを参照してください。

{{%/alert %}}

##### 3.1.2.5 属性値 {#attribute-values}

このプロパティは、 [Attribute-Based](#attribute-based) プロパティの属性が選択されている場合にのみ表示されます。 **属性値** プロパティでは、特定の属性値を選択できます。

例えば、ユーザーの *メールが認証されている場合にのみ、画像をアップロードすることを許可します*。 So, you need to select *EmailVerified* in the **Attribute-Based** property and *true* in the **Attribute Value** property:

{{% image_container width="250" %}}
![](attachments/page-editor-widgets-input-elements/conditional-editability.png)
{{% /image_container %}}

#### 3.1.3 コントロールセクション

{{% alert type="info" %}}

**コントロール** セクションは、 **ファイル マネージャー** のみで使用できます。

{{% /alert %}}

**ボタンの表示** オプションは、エンドユーザーがファイルをアップロードおよび/またはダウンロードできるかどうかを指定し、以下のオプションがあります。

* **アップロード** – エンドユーザーはファイルをアップロードできます
* **ダウンロード** – エンドユーザーはファイルをダウンロードできます
* **両方とも** - エンドユーザーはファイルをアップロードおよびダウンロードすることができます

#### 3.1.4 条件付き表示セクション

{{% snippet file="studio/visibility-section-link.md" %}}

#### 3.1.5 デザインセクション

**デザイン** セクションとそのプロパティについては、ウィジェットの [デザインセクション](page-editor-widgets-design-section) を参照してください。

## 4 続きを読む

* [ページ](page-editor)
* [ウィジェット](page-editor-widgets)
