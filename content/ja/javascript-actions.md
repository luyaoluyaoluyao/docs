---
title: "JavaScript アクション"
parent: "リソース"
menu_order: 20
description: "このリファレンスガイドでは、JavaScript のアクションが Mendix アプリの機能を拡張する方法について詳しく説明します。"
tags:
  - "javascript"
  - "javascript アクション"
  - "パラメータ"
  - "studio pro"
---

{{% alert type="warning" %}}
このアクティビティは **Nanoflows** でのみ使用できます。
{{% /alert %}}

## 1つの紹介

JavaScriptアクションを使用すると、アプリケーションの機能をナノフローだけではできない方法で拡張することができます。 JavaScript アクションを使用するには、 [JavaScript アクション コール](javascript-action-call) を使用して nanoflow から呼び出します。

{{% alert type="info" %}}

Each JavaScript action defined in Mendix Studio Pro corresponds to a file *{JavaScript action name}.js* in the subdirectory **javascriptsource{module name}/actions/** in your app directory.

The skeletons of these *.js* files are generated automatically when you save an action, and those JavaScript actions can immediately be edited in the embedded code editor.

{{% /alert %}}

JavaScript アクションの作成、構成、使用方法については、 [JavaScript アクション](/howto/extensibility/build-javascript-actions) の作成方法を参照してください。

## 2つの一般設定

**App Explorer** で JavaScript アクションをダブルクリックすると、JavaScript アクションの設定が表示されます。

{{% image_container width="400" %}}![javascript settings](attachments/javascript-actions/javascript-action-settings-no-para.png){{% /image_container %}}

JavaScript アクションとその影響に関する設定は以下の通りです。

### 2.1 名前

この設定は JavaScript アクションの名前を処理します。nanoflow は呼び出しを実行するときに参照します。 この名前は、生成された *.js* ファイルの名前でもあります。

### 2.2 パラメータ

パラメータは JavaScript のアクションにデータを渡します。 たとえば、JavaScriptに数値を乗算するアクションがある場合、パラメータは乗算する数値を定義します。 JavaScriptアクションには0以上のパラメータがあります。 各パラメータには一意の名前が必要です。 **パラメータ** > **Add**をクリックしてパラメータを追加できます。 そして、そのパラメータをカスタマイズして、データを JavaScript アクションに渡します。

![パラメータ](attachments/javascript-actions/parameter-naming.png)

JavaScript アクションの **コード** タブでは、パラメーターの値を確認し、実装を処理できます。 各パラメータには名前(1)、タイプ(2)、カテゴリ、説明(3)、戻り値(4)があります。

![パラメータコード](attachments/javascript-actions/parameter-code.png)

パラメータのカテゴリ(1)、パラメータ名 (2) が表示されます。 そして、 **JavaScriptアクション** ダイアログボックスの説明 (3) を開きます。

{{% image_container width="400" %}}![call javascript action dialog](attachments/javascript-actions/call-js-action-dialog.png){{% /image_container %}}

JavaScript アクションでサポートされているパラメータ型については、以下で説明します。

#### 2.2.1 名前

この設定はパラメータの名前を処理します。 名前が必要です。 名前は文字で始まり、文字だけを含まなければなりません。 名前にスペースは使用できません。

#### 2.2.2 タイプ

| 名前       | 説明                                                                                                                                                                                                                                                                                                                                                             |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| オブジェクト   | object パラメーターの型は Mendix オブジェクトを JavaScript アクションに渡すことができます。 また、特定のエンティティまたはtypeパラメータのエンティティタイプを選択する必要があります。 生成された JavaScript アクションテンプレートコードでは、この型は MxObject として表現されます。                                                                                                                                                                                         |
| リスト      | list パラメータの型は Mendix オブジェクトのリストを JavaScript アクションに渡すことができます。 また、特定のエンティティまたはtypeパラメータのエンティティタイプを選択する必要があります。 生成された JavaScript アクションテンプレートコードでは、この型は MxObject の配列として表現されます。                                                                                                                                                                                     |
| エンティティ   | 図形パラメータの型はプレースホルダです。 これは、nanoflow 内で呼び出されたときに、新しいエンティティの名前に置き換えられるエンティティを表します。 さらに、エンティティタイプを使用して型パラメータを入力することもできます。 生成された JavaScript アクションテンプレートコードでは、この型は文字列として表現されます。                                                                                                                                                                                       |
| Nanoflow | nanoflowパラメータタイプでは、JavaScriptアクションから呼び出せるナノフローを渡すことができます。 パラメータの値は非同期関数で、呼び出しによって設定されたnanoflowをトリガーします。 パラメータを JavaScript オブジェクトとして指定し、実行が終了すると、nanoflow の戻り値を取得できます。 For example, you can call a nanoflow that has a string `Name` parameter and returns a `User` object with this given name: `const user = await nanoflowParameter({ Name: "John Doe" });`. |
| Boolean  | ブールパラメータ型は、ブール値をJavaScriptアクションに渡すことができます。                                                                                                                                                                                                                                                                                                                     |
| 日付と時刻    | 日付と時刻のパラメータタイプを使用すると、日付と時刻の値を JavaScript アクションに渡すことができます。 生成された JavaScript アクションコードでは、この型は JavaScript `Date` として表現されます。                                                                                                                                                                                                                                        |
| 小数点以下桁数  | 10 進数のパラメータタイプでは、JavaScript のアクションに 10 進数を渡すことができます。 生成された JavaScript アクションコードでは、この型は [Big](https://www.npmjs.com/package/big-js) オブジェクトとして表現されます。                                                                                                                                                                                                             |
| 列挙型      | enumeration パラメータ型は JavaScript アクションに列挙値を渡すことができます。 生成された JavaScript アクションコードでは、この型は文字列として表現されます。                                                                                                                                                                                                                                                              |
| 整数       | integer/long パラメータ型は JavaScript アクションに小数値を渡すことができます。 生成された JavaScript アクションコードでは、この型は [Big](https://www.npmjs.com/package/big-js) オブジェクトとして表現されます。                                                                                                                                                                                                             |
| 文字列      | stringパラメータ型は、文字列の値をJavaScriptアクションに渡すことができます。                                                                                                                                                                                                                                                                                                                 |

#### 2.2.3 カテゴリ

カテゴリを使用して、 [JavaScript Action Call](javascript-action-call) でパラメータを区別します。 カテゴリは、アプリケーションにいくつかのパラメータがある場合にパラメータの論理グループを作成するのに便利です。 カテゴリを指定しない場合、パラメータは **Input** グループに表示されます。

#### 2.2.4 説明

いくつかのパラメータを持つアプリの場合、説明はパラメータの正確な目的を思い出させる役に立ちます。 説明では、アプリのコラボレーターにパラメータを記述することもできます。 説明には、大文字と小文字、数字、および記号の両方を含めることができます。

### 2.3 返品タイプ

returnパラメータ型は、JavaScriptアクションが返すデータの型を決定します。 多くの API は非同期であるため、この型を解決する `Promise` オブジェクトを返すこともできます。 JavaScript アクションの戻り値は、名前を与えて保存することができます。これは nanoflow で呼び出される場所で使用することができます。 パラメータに使用できるすべての型では、戻り値の型を使用することもできます。 さらに、アクションからデータが返されない場合は、戻り値の型「Nothing」を使用できます。

## 3 タイプパラメータ

type パラメータは、nanoflow で呼び出されたときに特定のエンティティで満たされるエンティティタイプのプレースホルダです。 型パラメータは、パラメータのデータ型を構成するときに使用できます。 ユーザーは任意のエンティティタイプのオブジェクトまたはリストを渡すことができます。 それらは簡単に追加、編集、または削除できます:

{{% image_container width="450" %}}![type parameter](attachments/javascript-actions/type-parameter.png){{% /image_container %}}

JavaScriptアクションは0以上の型パラメータを持つことができます。 各typeパラメータは一意の名前を持つ必要があります。

## 4 Nanoflow Actionとして露出する

**公開を nanoflow アクション** タブでは、JavaScript アクションをナノレベルのアクションとして公開することができます。 このサンプルアクションは、 *サンプルアクション* キャプションテキストが与えられており、 *ワークショップ* をカテゴリとして割り当てられており、アイコンが指定されていません:

{{% image_container width="450" %}}![expose action](attachments/javascript-actions/expose-jsaction.png){{% /image_container %}}

JavaScriptアクションを公開すると、選択したカテゴリ内のナノレベルの編集時に **ツールボックス** ウィンドウに表示されます。 このアクションがナノレベルで使用されると、提供されたキャプションとアイコンが表示されます。 ここではカテゴリとキャプションが明らかで、デフォルトのアイコンはカスタムアイコンが割り当てられていないように表示されています:

![ワークショップを公開しました](attachments/javascript-actions/workshop-exposed.png)

### 4.1 図表番号

JavaScript アクションを公開するにはキャプションが必要です。 このキャプションは、nanoflow **Toolbox** ウィンドウ内の JavaScript アクションに伴うもので、JavaScriptアクションに関する有用な情報を提供します。

### 4.2 カテゴリ

JavaScript アクションを公開するには、カテゴリが必要です。 カテゴリを使用して、nanoflow **Toolbox** ウィンドウで同様の目的を持った JavaScript アクションを一緒に整理します。

### 4.3 アイコン

アイコンは、JavaScript アクションを公開するときに任意です。 アイコンが選択されていない場合、デフォルトの JavaScript アクションアイコンが使用されます。 アイコンの推奨サイズは16x16ピクセルです。

## 5 ドキュメント

**ドキュメント** タブで、 **編集** を押してJavaScriptアクションをドキュメント化します:

{{% image_container width="450" %}}![documentation](attachments/javascript-actions/documentation-pro.png){{% /image_container %}}

ドキュメントは **コード** タブで表示されます。 ドキュメントは、対応する *.js* ファイルの関数へのコメントとして、JavaScript アクションにコピーされます。

{{% image_container width="450" %}}![documentation js file](attachments/javascript-actions/documentation-js-file.png){{% /image_container %}}

## 6 コード

**コード** タブでは、Studio Pro から離れずに JavaScript アクションコードを編集できます。 エディタは [モナコエディタ](https://microsoft.github.io/monaco-editor/index.html)をベースにしています。 構文強調やコード補完などの機能を提供します。 このコードはモダンな JavaScript (ES8 / ES2017) で記述でき、 `async` のような関数を `await` や `Promise` で使用できます。

コードには、インポート リスト、追加のコード ブロック、ユーザー コード ブロックの 3 つのセクションがあります。 追加されたすべてのコードは、これらのブロックのいずれかに移動する必要があります。 JavaScriptアクション設定のデプロイまたは更新時にテンプレートコードを再生成すると、ブロック外のコードが失われます。

追加のインポートは `import` で開始し、上に配置する必要があります。 `// BEGIN EXTRA CODE`. Extra code should be placed between `// BEGIN USER CODE` and `// END USER CODE`. User implementation code should be placed between `// BEGIN EXTRA CODE` and `// END EXTRA CODE`.

``` js
// このファイルは Mendix Studio Pro によって生成されました。
//
// 警告: Only the following code will be continued when actions are regenerated:
// - the import list
// - the code between BEGIN USER CODE and END USER CODE
// - the code between BEGIN EXTRA CODE and END EXTRA CODE
// Other code you will be lost the next time you deploy the project.
import { Big } from "big.js";

// BEGIN EXTRA CODE
 function sayHello(message) {
     window.alert("Hello: " + message);
 }
// END EXTRA CODE

/**
 * Show an alert message to an user.
 * @param {string} message - ユーザーに表示されるメッセージ。
 * @returns {Promise.<void>}
 */
export async function Hello(message) {
    // BEGIN USER CODE
    sayHello(message);
    return Promise.resolve();
    // END USER CODE
}
```

## 7 続きを読む

* [JavaScript アクションコール](javascript-action-call)
* [Nanoflows](ナノフロー)
* [JavaScriptアクションをビルド](/howto/extensibility/build-javascript-actions)
* [Java アクションコール](java-action-call)
* [マイクロフロー通話](microflow-call)
