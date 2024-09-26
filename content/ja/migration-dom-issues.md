---
title: "DOM の変更のトラブルシューティング"
parent: "moving-from-7-to-8"
menu_order: 10
description: "このドキュメントでは、Mendix 8 用の更新された DOM 構造と、アプリの CSS に何を意味するのかについて説明します。"
tags:
  - "DOM"
  - "ウィジェット"
  - "テーマ"
  - "クラス"
---

## 1つの紹介

Mendix 8 のクライアントのその他の改良の中で、Mendix アプリケーションの HTML も更新されました。 これらの変更により、ウィジェットにアクセスしやすく、一貫性があり、よりクリーンなマークアップを行うことができます。

ただし、これらのアップデートはスタイリングに影響する可能性があります。 ウィジェットの Document Object Model 構造が更新されたため、アプリケーションの外観が影響を受ける可能性があります。 このリファレンスガイドでは、DOM と CSS に関連する、Mendix 7 と 8 の違いについて概説します。 このドキュメントは、カスタム CSS を使用したり、既存の Atlas UI CSS を変更したりするアプリにのみ関連します。

## 2 アトラスの更新

Mendix 8 にアップグレードすると、DOM 構造の変更により Sass のスタイルファイルも変更されます。 これにより、あなたのスタイルの一部が期待どおりに動作しなくなる可能性があります。 Mendix 8とスタイリングを互換性があるようにするには、 [Mendix 8への移行時のアトラスUIの変更のトラブルシューティング](migration-atlas) を参照してください。

## 合理化されたカスタムテーマ3個

Mendix 8より前に、アプリにテーマがない場合、クライアントは大量のデフォルトスタイルを提供しました。 これにより、デフォルトのスタイルを上書きする必要があるため、独自のテーマを構築することが困難になりました。 Mendix 8の時点で、すべてのスタイリングはアトラスUIに移動しました。 今、自分のテーマをゼロから構築するには、大幅に少ない作業が必要です。

If you have already built your own theme from scratch in an earlier version of Mendix, you might depend on the default styling (specifically the Bootstrap files and the **mxui.css** file) not included in Mendix 8 applications by default. この場合、Mendixはレガシー **mxui.css** とBootstrapファイルをこの [GitHubリポジトリ](https://github.com/mendix/legacy-mxui-css)で提供します。 カスタムテーマを有効にするには、このリポジトリからファイルをダウンロードしてください。

{{% alert type="info" %}}
エラーメッセージが表示された場合 `CE6103:テーマにAtlas UIを使用していないことを検出しました。 テーマがMendix 8に完全に準拠していることを確認するには、「DOM Changesのトラブルシューティング」を確認してください。 右クリックして`オプションを表示するには、右クリックして **解決済みとしてマーク** を選択することで、メッセージをクリアできます。
{{% /alert %}}

## フォーカス特有の4クラスが削除されました

Mendix 8 より前に、クライアントは `mx-focus` をフォーカスを受け取っている要素に頻繁に適用し、要素がフォーカスを失ったときに `mx-focus` を削除しました。 サポートされているすべてのブラウザーが `:focus` 疑似クラスを適切にサポートしているため、これらの再アプリケーションはもはや必要ありません。  `:four`の詳細については、Mozillaの [:focus documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus) を参照してください。

テーマに `mx-focus` を使用している場合は、 `:focus`に置き換える必要があります。

以下のようなコードを入力してください。

```css
.mx-listview-item.mx-focus {
    /* スタイリング */
}
```

変更する必要があります:

```css
.mx-listview-item:focus {
    /* スタイリング */
}
```

## 5つのデータグリッドマークアップの更新

データグリッドのマークアップをいくつかアップデートしました。 以前は、データ グリッドは、ヘッダーを含むテーブルと データを含むテーブルの 2 つに分割されていました。 これにより、スクリーンリーダーはこれらを2つの別個のテーブルとして表示するため、データグリッドにアクセスできなくなりました。 二つのテーブルが一つのテーブルに統合されました。 さらに、2つのテーブルをラップしている `div` が削除されました。

もう1つのデータ グリッドのマークアップの変更点は、ツール バーを含む `div` と ページ バー (コントロールバーの一部) を含む `div` が論理的な順序であることです。 以前は、適切な順序でそれらを表示するために追加の CSS が必要でした。論理的なタブの動作を指示するには、追加の JavaScript が必要でした。 現在の構造は、

Web Content Accessibility Guidelines 2に沿っています。 の基準 1.3.2 [](https://www.w3.org/TR/WCAG21/#meaningful-sequence) は [DOM 順序をビジュアルの順序](https://www.w3.org/TR/WCAG20-TECHS/C27.html) に従うようにします。</p> 

新しいアクセシビリティ機能が実装され、ページネーションセクション (コントロールバー内) を含む `div` に適切な `ロール` 属性が設定されました。 Buttons inside of this `div`, including the `div` itself, now has translatable `aria-label` attributes which can be set from Modeler's `System Texts` page with category name `Accessibility`. 新しい `スパン` と `キャプション` 要素は、それぞれページネーション用の *`ボタン` と* `thead` の兄弟として追加されました。 彼らはスクリーンリーダーにのみ表示されます。 

これはデータ グリッドの現在のマークアップです(変更されていないコードが省略されています):



```html
<div class="mx-grid mx-datagrid mx-name-grid1">
    <div class="mx-grid-searchbar" style="display: none;">...</div>
    <div class="mx-grid-controlbar">
        ...
        <div ... role="navigation" aria-label="Pagination(translatable text)">
            <button ...  aria-label="Go to first page(translatable text)"> </button>
            <button ... aria-label="Go to previous page(translatable text)"></button>
            <div ... aria-hidden="true">1 to 20 of 132</div> 
                <span class="sr-only">Currently showing(translatable text) 1 to 20 of 132</span>
            <button ... aria-label="Go to next page(translatable text)"></button>
            <button ... aria-label="Go to last page(translatable text)"></button>
        </div>
        ...
    </div>
    <div class="mx-grid-content">
        <table>
            <caption class="sr-only">Caption</caption>
            <colgroup>...</colgroup>
            <thead>
                <tr class="mx-name-head-row"></tr>
            </thead>
            <tbody>
                <tr class="mx-name-index-0" >...</tr>
            </tbody>
            <tfoot></tfoot>
        </table>
    </div>
</div>
```


さらに、要素名を使用して簡単にアクセスできるため、テーブル上の多数の追加クラスが削除されました。 

このようにしてデータグリッドをスタイリングしている場合:



```css
.mx-datagrid .mx-datagrid-head-table {
    // your styling
}
.mx-datagrid .mx-datagrid-body-table .mx-datagrid-body tr {
    // your styling
}
```


これらのガイドラインを使用してデータグリッドのスタイルを書き換える必要があります。



```css
.mx-datagrid thead {
    // your styling
}

.mx-datagrid tbody tr {
    // your styling
}
```




## マークアップ一覧表示の変更

リストビューウィジェットのマークアップも変更されました。 スタイリングを簡素化するために、以下のクラスが削除されました。

* `mx-list`
* `mx-listview-list`
* `mx-listview-striped`
* `mx-listview-item`
* `mx-listview-search-input`
* `mx-listview-clear-button`

参照セットセレクターまたは参照セットセレクターの選択ページにないリストビューの場合。 リストビューの `mx-listview-selectable` が削除されました。 不要な `div` 要素で、クラス `mx-listview-content` が各リストビューアイテムの内容を囲んでも削除されました。

リストビュー検索バーの DOM 要素の順序は、視覚的な順序と一致するように修正されました。 検索入力フィールドを囲む `div` 要素が削除されました。

リスト表示ウィジェットのスタイリングをこちらの方法で行っている場合：



```css
.mx-listview-item {
    // Your styling
}
.mx-listview-search-input input {
    // Your styling
}
.mx-listview-clear-button {
    // Your styling
}
```


次のガイドラインを使用して、リストビューのスタイルを変更する必要があります。



```css
.mx-listview li {
    // Your styling
}
.mx-listview-searchbar input {
    // Your styling
}
.mx-listview-searchbar button {
    // Your styling
}
```




## 7つのスクロールコンテナのマークアップの変更点

`mx-layoutcontainer` で始まるすべてのクラスは、スクロールコンテナから削除されています。これは、 `mx-scrollcontainer` と重複しているためです。



## 8 リンクボタンのマークアップの変更

リンクボタンのマークアップは他のボタンとより一貫性があります:



```html
<a href="#" class="mx-link mx-name-actionButton1">
    <span class="glyphicon glyphicon-euro"></span>
    リンクボタン
</a>
```




## インプットウィジェットマークアップの変更

すべての入力ウィジェットには、それを包み込んだ暗黙のフォームグループ構造があります。 最近の変更前に、入力ウィジェットのDOM構造は設定に応じて無秩序に見える可能性があります。 これでフォーム グループ 構造により、入力ウィジェットがデータ ビュー内で適切に整列され、適切にラベル付けされます。



### DataView上の9.1 垂直方向と水平方向のクラス

Previously, data view was rendering `form-horizontal` class on it when **Form orientation** was set to **Horizontal** and no such class if this option was set to **Vertical**. `フォーム水平` または `フォーム垂直` が **水平** オプションと **垂直** オプションにそれぞれ追加されます。 

これにより、CSS セレクター内のクラスをターゲットにすることで、さまざまな方向でフォーム(および入力)のスタイルを簡単に設定できます。 If you were previously relying on the presence or absence of `form-horizontal,` now you can simplify your CSS selectors by using `form-vertical`.

データビューウィジェットの DOM 構造は以下のように整理されています。



```html
<div class="mx-dataview [form-horizontal or form-vertical]">
    <div class="mx-dataview-content">
        ...
        <div class="form-group"> ... </div>
        <div class="form-group"> ... </div>
        ...
    </div>
    <div class="mx-dataview-controls">
        ...
    </div>
</div>
```




### 9.2 フォームグループ構造

Previously, if widget had the **Show caption** option set to **No**, form group structure was missing `form-group` class on its top level `div`:



```html
<div class="mx-name-textBox4 [...]" [...]>
    <INPUT-WIDGET />
</div>
```


これで、 `フォームグループ` クラスは、余分な `列なし` クラスでそのまま使用できます。



```html
<div class="form-group no-columns mx-name-textBox4 [...]" [...]>
    <INPUT-WIDGET />
</div>
```


If you have made custom styles using `.form-group` before, this might be a breaking change as `.form-group`  matches with more elements now. You can now target form groups and elements inside them on only horizontal or only vertical forms using `.form-horizontal .form-group` or `.form-vertical .form-group` respectively. 



### 9.3 ウィジェットタイプクラス

フォームグループにウィジェットの種類に応じて特別なクラス名が追加されました:

* `.mx-checkbox`
* `.mx-datepicker`
* `.mx-dropdown`
* `.mx-inputreferencesetselector`
* `.mx-radiobuttongroup`
* `.mx-referenceselector`
* `.mx-textarea`
* `.mx-textbox`



### 9.4 フォームグループレイアウトの例

垂直方向のフォーム グループ入力ウィジェットには、同じレベルのラベル、入力コントロール、およびオプションの検証メッセージが表示されるようになりました。



```html
<div class="form-group mx-name-textBox4 [...]" [...]>
    <label class="control-label" for="123_abc">
        Caption
    </label>

    <INPUT-CONTROL/>
    <!-- OR for readonly style text -->
    <div class="form-control-static">value</div>

    <!-- optional: validation message -->
    <div class="alert alert-danger mx-validation-message">checkboom</div>
</div>
```


水平フォームグループ入力ウィジェットに `col-sm-{labelWith}`と `div.col-sm-{12-labelWith}` のラベルが追加されました。 そのラベルには、入力コントロールとオプションの検証メッセージも含まれています。



```html
<div class="form-group mx-name-textBox4 [...]" [...]>
    <label class="control-label col-sm-4" for="123_abc">
        Caption
    </label>
    <div class="col-sm-8">
        <INPUT-CONTROL/>
        <!-- OR for readonly style text -->
        <div class="form-control-static">value</div>

        <!-- optional: validation message -->
        <div class="alert alert-danger mx-validation-message">checkboom</div>
    </div>
</div>
```


これは、水平または垂直のデータビューの入力ウィジェットの構造です。 **ラベル表示** が **いいえ** に設定されています。 入力ウィジェットには、入力コントロールとオプションの検証メッセージがあります。



```html
<div class="form-group mx-name-textBox4 [...]" [...]>
    <!-- A form group without a label is still a form-group -->

    <INPUT-CONTROL/>
    <!-- OR for readonly style text -->
    <div class="form-control-static">value</div>

    <!-- optional: validation message -->
    <div class="alert alert-danger mx-validation-message">checkboom</div>
</div>
```




### 9.5 読み取り専用コントロール

以前は **読み取り専用スタイル** を **テキスト** に設定した入力ウィジェットの編集不可能な入力コントロールは、 `p` または `ラベル` 要素に `フォームコントロール静的な` クラスを使用してレンダリングされていた可能性があります。 

**読み取り専用スタイル** を **テキスト** に設定した読み取り専用コントロールが次のようにレンダリングされるようになりました。



```html
<div class="form-control-static">値</div>
```




### 9.6 入力ウィジェット構造

以前は、入力ウィジェットにはコントロールを囲むラッパー要素がありました。 

これらの冗長なラッパーは削除され、可能な限り裸のコントロールがレンダリングされます(ラジオボタングループ内のラジオボタンを除く)。 は、個々のコントロールを `div` でラップします。



### 9.7 入力コントロールの例

さまざまな入力制御の例を以下に示します。

テキスト ボックス:



```html
<input class="form-control" type="text" id="123_abc" />
```


テキスト領域:



```html
<textarea class="form-control mx-textarea-input mx-textarea mx-textarea-input-noresize"></textarea>
```


チェックボックス:



```html
<input type="checkbox" value="" />
```


**ラベルの位置** が **コントロール後** に設定されている場合チェックボックスをオンにします(この場合、フォームグループのラベルは表示されません):



```html
<input type="checkbox" id="123_abc" value="" />
<label for="123_abc">ラベル</label>
```


ラジオボタン: 



```html
<div role="radiogroup" id="123_abc" aria-labelledby="123_abc-label">
    <div class="radio">
        <input type="radio" id="123_abc_0" value="Funghi">
        <label for="123_abc_0">Funghi</label>
    </div>
    <div class="radio">
        <input type="radio" id="123_abc_1" value="Pepperoni">
        <label for="123_abc_1">Pepperoni</label>
    </div>
    <div class="radio">
        <input type="radio" id="123_abc_2" value="Tre_Formaggi">
        <label for="123_abc_2">Tre Formaggi</label>
    </div>
    <div class="radio">
        <input type="radio" id="123_abc_3" value="Margherita">
        <label for="123_abc_3">Margherita</label>
    </div>
</div>
```


ドロップダウン:



```html
<select class="form-control">
    <option value=""></option>
    <option value="a1">a1</option>
    <option value="a2">a2</option>
    <option value="a3">a3</option>
</select>
```




## 10 日付選択ウィジェットの変更



### 10.1 Input

日付ピッカー入力ウィジェットに以下の変更が加えられました:

* `mx-dateinput` クラスと `mx-dateinput-input` は新しい `mx-compound-control` クラスに代わって削除されました
* 複数の要素で構成された入力ウィジェットに `mx-compound-control` クラスが導入されました。 例えば、入力の隣にボタンがあるウィジェットなど。
* 内部の `<div>` クラス `mx-date-input-wrapper` のある要素が、入力の周りに削除されました。
* `<button>` 要素は、視覚的な順序に合わせてDOMの入力の後に配置されました。



### 10.2 カレンダー

道場フレームワークを使用してカレンダーポップアップウィンドウが実装されていないため、カレンダーポップアップウィンドウの内部構造にいくつかの変更が加えられました。

* `dijit` で始まるすべてのクラスが削除されました
* 一番外側の `<div>` 要素にクラス `mx-calendar` が追加されました
* `<td>` 要素は、カレンダービューで日付を表します。次のクラスを取得します： 
      * `mx-calendar -day-month -current`, `mx-calendar -day-month-next` または `mx-calendar -day-month-next`: 日が現在、前、来月に該当するかどうかによって異なります
    * `mx-calendar-day-selected`: カレンダーを開いた日付ピッカーで現在日が選択されている場合。
    * `mx-calendar-day-active`: その日が現在フォーカスされている場合
* `<span>` 要素の `<td>` と `<th>` 要素が削除されました

月ヘッダーに次の構造が追加されました。



```html
<div class="mx-calendar-month-header">
    <button class="mx-calendar-month-previous">
        <span class="glyphicon glyphicon-minus"/>
    </button>
    <div class="mx-calendar-month-dropdown">
        <div class="mx-calendar-month-current">
            <div class="mx-calendar-month-spacer">
                <div>January</div>
                ...
            </div>
            <div class="mx-calendar-month-label">June</div>
        </div>
        <span class="glyphicon glyphicon-chevron-down"/>

        <!-- only rendered when the month dropdown is clicked -->
        <div class="mx-calendar-month-dropdown-options">
            <div>January</div>
            ...
        </div>
    </div>
    <button class="mx-calendar-month-next">
        <span class="glyphicon glyphicon-plus"/>
    </button>
</div>
```


今年のスイッチャーの構造は次のとおりです。



```html
<div class="mx-calendar-year-switcher">
    <span class="mx-calendar-year-previous">2018</span>
    <span class="mx-calendar-year-selected">2019</span>
    <span class="mx-calendar-year-next">2020</span>
</div>
```




## 11 リファレンスセレクタと入力リファレンスセットセレクタの変更点

参照セレクタのマークアップには、次の変更が加えられました。

* `mx-referenceselector` と `mx-referencesetselector` のクラス `<div>` は新しい `mx-compound-control` クラスを支持している要素から削除されました。 これは、複数の要素で構成される入力ウィジェットに導入されました(複数の要素を持つ共通の入力ウィジェットは、入力要素の隣にあるボタンです)。

次のような変更が入力リファレンスセットセレクターマークアップに加えられました。 

* フォーム グループは、クラス `mx-referenceselector` または `mx-inputreferencesetselector` ( `input` 接頭辞に注意) を代わりに取得します。
* 入力周辺の内部 `<div>` 要素 ( `-input-wrapper`で終わるクラスを共有する) が削除されました
* `<button>` 要素は、視覚的な順序に合わせてDOM内の入力の後に配置されています



## 12 DropDownButton ウィジェットのクリーンアップ

`DropDownButton` ウィジェットに以下の変更が行われました。

* クラス `mx-list` がダイアログボックスの用語リストから削除されました
* クラス `mx-dropdown` は、検索入力のドロップダウンとは何の関係もないので、ダイアログボックスから削除されました



## 13 ファイルマネージャーと画像アップローダーウィジェットの変更

以前は、ファイルマネージャと画像アップローダーのウィジェットはデスクトップとモバイルのブラウザーで異なるレンダリングを行っていました。 デスクトップでは、これらのウィジェットは簡単なスタイルのカスタム HTML スニペットとしてレンダリングされ、モバイルではスタイル間のネイティブファイル入力が困難であることが明らかになりました。

ファイルマネージャと画像アップローダーウィジェットが一貫性を保つように変更されました。 これで、これらは常に同じHTML構造を表示します。 また、これらのウィジェットの DOM 構造は、他の複合ウィジェット(参照セレクタや日付ピッカーなど)とより一致しています。

現在、ファイルマネージャと画像アップローダーのウィジェットは常に `div`  要素として表現され、その上に `mx-compound-control` クラスがあります。 また、 `mx-fileinput` クラスがフォーム グループに移動されました。 `div`の中には、 `form-control` クラスの入力があります。 この入力は現在選択されているファイルのファイル名を表します。 クラス `mx-wrapped-label` は入力から消えます。 入力の横には、現在のファイルをアップロードおよびダウンロードするための2つのボタンの1つがあります。 これらのボタンは以前と同じクラスを持っています。



## 14 もっと読む

* [アトラスのUI変更のトラブルシューティング](migration-atlas)
