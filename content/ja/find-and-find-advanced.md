---
title: "検索、詳細検索、および使用方法を検索"
parent: "edit-menu"
description: "Mendix Studio Proで検索、高度な検索、および使用方法を確認する方法について説明します。"
menu_order: 10
tags:
  - "studio pro"
  - "高度な検索"
  - "使い道を見つける"
  - "検索"
  - "メニューを編集"
---

## 1つの紹介

アプリでは、さまざまな要素、ドキュメント、Xpath、さまざまな要素への変更や使用を検索できます。  **Find**, **Find Advanced**, and **Find Usages** オプションで **Edit** メニューを選択します。

![検索オプション](attachments/find-and-find-advanced/find-options.jpg)

## 2検索オプション

**Find** オプションを使用して、アプリ内のさまざまな要素を見つけることができます。 たとえば、ドメインモデル、ページエディタで要素を検索したいとします。 と、"Employee" という単語が使用されるマイクロフローエディタ: ページ、図形、関連付け、式など。 次の操作を行います:

1. **編集** > **トップバーの** をクリックするか、 <kbd>Ctrl</kbd>+<kbd>F</kbd> を押します。

2. **Find** ダイアログボックスで、 **Match case** and **Match the whole word** selected. この方法で、"Employee"、"Employee"、または "Department_Employee" などのインスタンスを含む単語「Employee」のすべてのインスタンスを検索します。

3. **Look in** セクションで、検索したくないアプリの項目を選択解除します:

   ![セクションを見る](attachments/find-and-find-advanced/look-in.jpg)

検索結果は **検索結果** ペインで確認できます。

![検索結果](attachments/find-and-find-advanced/search-results.jpg)

## 3つの高度な検索オプション

With the **Find Advanced** option you can set advanced criteria and find specific elements in your app, such as all [object activities](#find-object-activities), or [unused elements](#find-unused-elements).

### 3.1 オブジェクトアクティビティの検索 {#find-object-activities}

オブジェクトのアクティビティを含むマイクロフローを検索できます。 次の操作を行います:

1.  Click **Edit** > **Find** **Advanced** in the top-bar or press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>F</kbd>. **詳細を検索** ダイアログボックスが開きます: ![](attachments/find-and-find-advanced/find-advanced-dialog-box.png)
3.  **Search for** オプションで、 **Microflow actions** を選択します。 ![](attachments/find-and-find-advanced/search-for-microflow-actions.png)
3.  オブジェクトアクティビティを検索するエンティティを選択し、 **検索** をクリックします。

検索結果は **検索結果** ペインで確認できます。

### 3.2 未使用の要素を見つける {#find-unused-elements}

アプリを開発しているときに、特定の機能が発生する可能性があります（例えば、 ページやマイクロフロー)はアプリケーションの最終バージョンでは適用できなくなりました。 アプリを明確かつ簡単にメンテナンスできるようにするには、未使用のアイテムをクリーンアップすることをお勧めします。

未使用のアイテムを見つけるには、次の手順を実行します。

1. Studio Proのトップバーに **Edit** > **Find Advanced** or press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>F</kbd>.

2. **詳細を検索** ダイアログボックスで、 **** **検索** オプションで</strong> を選択します:

   ![](attachments/find-and-find-advanced/search-for-unused-items.png)

3. **検索** をクリックします。

結果は **検索結果** ペインに表示されます。 結果をフィルタリングするには、ペインの右上隅にある **** ボタンをクリックします。

未使用の項目を削除すると、より多くの未使用の項目が発生する可能性があることに注意してください。 たとえば、未使用のページを削除すると、そのページでのみ使用されるmicroflow が未使用の項目になります。 アプリを定期的にクリーンアップする場合は、未使用のアイテムリストを更新してください。

{{% alert type="info" %}}

マーケットプレイスからダウンロードされたモジュールには、多くの未使用のアイテムが含まれている場合があります。 これらの項目を削除し、モジュールが後で更新された場合、それらの項目はあなたのモデルに戻ります。 ですから、Marketplace モジュールから未使用のアイテムを削除しないことをお勧めします。

{{% /alert %}}

{{% alert type="info" %}}

アプリから除外されたオブジェクトは、未使用のアイテムリストには表示されません。

{{% /alert %}}

### 3.3 未使用のオブジェクトを使用済みとしてマークする

一部のページとマイクロフローは、Java コードからのみ使用され、Studio Pro が Java ソースコードを調べることができないため、未使用の項目としてリストされます。 これらのオブジェクトを削除しないようにするには、ページまたはマイクロフローを使用してマークします。 次の操作を行います:

1. 使用中にマークする必要があるページまたはマイクロフローを開きます。

2. プロパティに移動し、 **** プロパティとして **いいえ** から **はい** に変更します。

## 4つの使い方を見つけるオプション {#find-usages}

**使用法検索** オプションを使用すると、特定の要素が使用される場所を見つけることができます。 例えば、特定のページを開くすべてのボタンを検索します。

{{% alert type="info" %}}
このオプションは、選択したエンティティ/属性が選択されている場所のみを検索します。 これは、エンティティ/属性が暗黙的に派生するインスタンスを見つけられないことを意味します (例えば、関連付けに従うこと)。
{{% /alert %}}

特定の要素が使用される場所を見つけるには、次の手順を実行します。

1. 要素を含むドキュメントを開きます。 たとえば、ドメインモデルを開きます。
2. 要素を選択します (例えば、 エンティティ) をクリックして **編集** > **使用状況を検索** 上部バーで要素を右クリックし、 **使用状況を検索**:
    {{% image_container width="350" %}}![Find Usages](attachments/find-and-find-advanced/find-usages.png){{% /image_container %}}

Studio Pro は、このエンティティのすべての使用状況を **検索結果** ペインに表示します。 ![検索結果ペイン](attachments/find-and-find-advanced/found-usages.png)

**検索結果** ペイン内の項目をダブルクリックして、対応するドキュメントを開きます。

**結果を見つける** ペインの **結果をロック** をクリックします。 **使い方を検索**をクリックすると、2番目の **結果を検索** ペインに結果が表示されます。 これにより、複数の検索結果を保持できます。

## 5 続きを読む

* [オプションに移動](go-to-option)
