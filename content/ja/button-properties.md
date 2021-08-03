---
title: "ボタンのプロパティ"
parent: "ボタン-ウィジェット"
tags:
  - "studio pro"
  - "ボタン"
  - "アクションボタン"
  - "ドロップダウンボタン"
  - "ボタンウィジェット"
  - "image プロパティ"
---

## 1つの紹介

ボタンは、マイクロフローやナノフローの呼び出しやページを開くなど、さまざまなアクションを実行できます。

## 2つのプロパティ

ボタンプロパティの例を以下の画像に示します。

{{% image_container width="250" %}}![ボタンのプロパティ](attachments/button-widgets/button-properties.png)
{{% /image_container %}}

ボタンのプロパティは以下のセクションで構成されています:

* [アクセシビリティ](#accessibility) ( [レンダリングモード](#RenderMode) がリンクされている場合のみ)
* [一般的な](#common)
* [デザインプロパティ](#design)
* [イベント](#events)
* [全般](#general)
* [アイテム](#items) (ドロップダウンボタンのみ)
* [公開範囲](#visibility)

### 2.1 アクセシビリティセクション {#accessibility}

{{% alert type="info" %}}

**アクセシビリティ** セクションは、 [レンダリングモード](#RenderMode) がリンクの場合にのみ表示されます。

{{% /alert %}}

#### 2.1.1 ロールタイプ {#RoleType}

**Role type** プロパティは、ボタンの HTML でレンダリングされる `aria-role` 属性値を決定します。 `Aria-role` 属性は、アクセシビリティを向上させるために使用できます。 スクリーンリーダーなどのデバイスはそれらを解釈し、エンドユーザーに役割の意味を提示するからです。 利用可能なオプションは次のとおりです:

* ボタン (既定)
* Checkbox
* リンク
* メニュー項目
* メニューアイテムのチェック
* メニュー項目ラジオ
* Option
* ラジオ
* 切り替え
* Tab

### 2.2 共通セクション {#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.3 デザインプロパティセクション {#design}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.4 イベントセクション {#events}

{{% snippet file="refguide/events-section-link.md" %}}

### 2.5 一般セクション {#general}

#### 2.5.1 図表番号 {#caption}

**図表番号** プロパティは、ボタンに表示されるテキストを定義します。 図表番号には、たとえば、 {1} のように、括弧間で書かれたパラメータを含めることができます。

パラメータの使用に関する詳細は、以下の [パラメータ](#parameters) セクションを参照してください。

#### 2.5.2 パラメータ {#parameters}

パラメータは、その値が表示される属性です。 **パラメータ**を表示するには、次のいずれかを実行します。

* プロパティの **図表番号** 設定をダブルクリックします。

* Double-click the button on the page and click **Edit** in the **General** section > **Caption**:

    ![パラメータを開く](attachments/button-widgets/opening-parameters.png)

パラメータには以下の設定があります:

* **Index** - パラメータの識別番号

* **属性 (path)** - 値が表示される属性

* **書式** - 属性値を表示するフォーマット

    ![パラメーターの設定](attachments/button-widgets/button-parameter-settings.png)

##### 2.5.2.1 新しいパラメータの追加

パラメータを追加するには、次の操作を行います。

1. **ボタン** ウィジェットを、 [データ ウィジェット](data-widgets) 内側のように、エンティティのコンテキストに配置します。

2. ボタンウィジェットのプロパティで **図表番号** 設定をダブルクリックします。

3.  **図表番号の編集** ダイアログ ボックス > **パラメータ** セクションで **新規作成**:

    ![新しいパラメータの追加](attachments/button-widgets/new-parameter.png)

4. **テンプレートパラメータの編集** ダイアログボックスで、 **を選択**をクリックし、属性を選択して選択を確定します。

5. In the **Caption** setting, write the text you would like to display and type **Index** of the parameter you would like to include. In the example below, to include a name of your customer , you need to use indexes {1} for the *Name* attribute:

    ![パラメータの例](attachments/button-widgets/button-parameter-example.png)

##### 2.5.2.2 パラメータに対するその他のアクションの実行

新しいパラメータの追加に加えて、パラメータに対して以下のアクションを実行できます。

* **削除** – パラメータを削除するには、削除をクリックするか、キーボードの <kbd>削除</kbd> を押します

* **編集** – パラメータをダブルクリックして編集するか、編集をクリックします

* **Move up** – to move a parameter up in the list of parameters and also to change its index, click **Move up**

* **Move down** – to move a parameter down in the list of parameters and also to change its index, click **Move down**

    ![パラメーターアクション](attachments/button-widgets/button-parameter-actions.png)

#### 2.5.3 ツールチップ

**Tooltip** プロパティは、ボタンの上にカーソルを合わせたときに表示されるテキストの末端ユーザに表示されるテキストを決定します。 ツールチップテキストは翻訳可能です。 翻訳可能なテキストの詳細については、 [言語メニュー](translatable-texts) を参照してください。 ツールチップが指定されていない場合、ボタンの上にカーソルを合わせるとツールチップは表示されません。

#### 2.5.4 アイコン {#icon}

**アイコン** プロパティは、ボタンのキャプションの前に表示されるアイコンを決定します。 利用可能なオプションは次のとおりです。

* アイコンなし
* グリヒコン
* a (ビットマップ) image

グリフはBootstrapのHalfingsコレクションから来ています。 ビットマップ画像を超えるグリヒコンの利点は、それらがスケーラブルであることです。 高解像度の画面でシャープに見えるしフォントの色を変えることで色を変えることができます 画像アイコンの利点は、複数の色を持つことができることです。

#### 2.5.5 レンダリングモード {#RenderMode}

このボタンをエンドユーザーに表示する方法を定義します。 利用可能なオプションは次のとおりです:

* **ボタン** - ウィジェットはボタンとしてレンダリングされます
* **リンク** - ウィジェットはハイパーリンクとしてレンダリングされます

*デフォルトレンダリングモード:* ボタン

#### 2.5.6 ボタンスタイル

**ボタン スタイル** プロパティは、ボタンに定義済みのスタイルを適用します。 利用可能なオプションは次のとおりです:

* デフォルト
* 反転
* プライマリ（プライマリ）
* 情報
* 成功
* 警告
* 危険

#### 2.5.7 アクション中は無効

このプロパティは、 **マイクロフロー** を呼び出すか、 **ナノフローを呼び出す** が [オンクリックイベント](on-click-event) として選択されている場合にのみ表示されます。 **** を選択すると、アクションが完了または失敗するまでボタンが無効になります。

デフォルト: *true*

### 2.6 項目セクション {#items}

{{% alert type="info" %}}

**Items** セクションはドロップダウンボタンでのみ表示されます。

{{% /alert %}}

エンドユーザーがドロップダウンボタンをクリックすると、項目のリストが表示されるポップアップウィンドウが開きます。 各項目はエンドユーザーがこの項目をクリックしたときにイベントを実行します。 さまざまなアイテムが異なるイベントを実行できます。 割り当てることができるイベントの詳細については、 [[イベント & イベントセクション]を参照してください。](on-click-event).

{{% alert type="info" %}}

* **オブジェクトの作成** イベントのアイテムは、十分な権限がある場合にのみ表示されます。 詳細については、 [セキュリティ](security) を参照してください。

* **サインアウト** イベントのアイテムは匿名ユーザーには表示されません。 異なるセキュリティレベルと匿名ユーザに関する詳細については、 [App Security](project-security) と [匿名ユーザ](anonymous-users) を参照してください。


{{% /alert %}}

各項目には以下のプロパティがあります:

* **図表番号** - アイテムのキャプションを定義する

*  **Action** – defines an on-click event performed when the item is clicked (for more information on-click events, see [On Click Event & Events Section](on-click-event))

    ![アイテムのプロパティ](attachments/button-widgets/items-properties.png)


#### 2.6.1 新しいアイテムの追加

ドロップダウンボタンに項目を追加するには、次の操作を行います。

1. ボタンウィジェットのプロパティで **アイテム** 設定をダブルクリックします。

2.  **アイテムの編集** ダイアログボックスで、 **新規** をクリックします。

    ![新しいアイテムの追加](attachments/button-widgets/adding-new-item.png)

3. **ドロップダウンボタン** 項目ダイアログボックスで、以下の操作を行います:
   1. 項目のキャプションを指定します。
   2. このアイテムに表示する画像 (アイコン) を選択します。
   3. エンドユーザーがこのアイテムをクリックしたときに実行されるオンクリックイベントを選択します。
   4. Click **OK**.
4. **アイテムの編集** ダイアログボックスで、 **OK** をクリックして変更を保存し、新しいアイテムを追加します。



### 2.7 表示セクション {#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 続きを読む

* [ページ](page)
* [ボタンウィジェット](ボタン-ウィジェット)
* [ページエディターで共通のプロパティ](common-widget-properties)
* [「イベント & イベント セクション」をクリックしてください](on-click-event)


