---
title: "プロジェクトパッケージのエクスポート"
parent: "ファイルメニュー"
menu_order: 30
tags:
  - "studio pro"
  - "エクスポートアプリ"
  - "プロジェクトパッケージのエクスポート"
aliases:
  - /developerportal/support/export-a-project-package.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/export-project-package-dialog.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介
You can export a project package (*.mpk*) from Mendix Studio Pro for backup purposes or to share it with other Mendix developers. これは、誰かにアプリ全体を渡したい場合や、チケットを送信する際にテストアプリを提供する必要がある場合に便利です。

[プロジェクトパッケージのインポート](import-project-package-dialog) を使用して、プロジェクトパッケージを新しいアプリに再びインポートすることができます。

パッケージをエクスポートする **ファイル** メニュー > **プロジェクトパッケージのエクスポート** を開き、 **プロジェクトパッケージのエクスポート** ダイアログボックスで関連するオプションを選択します:

![「プロジェクトパッケージのエクスポート」ダイアログ ウィンドウ](attachments/file-menu/export-project-package.png)

 選択できるオプションの詳細については、以下のセクションを参照してください。

## 2宛先

パッケージをエクスポートするフォルダを指定できます。 デフォルトの場所は、プロジェクト ディレクトリ内の *packages* という名前のフォルダです。

## 3つのデータをエクスポート

Mendix プロジェクトパッケージは Mendix パッケージファイル (*.mpk* ) にエクスポートできます。  組み込みのデプロイメントデータベースとアップロードされたファイルをエクスポートするか、データなしでエクスポートするかを選択できます。 次のいずれかのオプションを選択できます:

* **データなし** – データなしでパッケージがエクスポートされます。

* **既存のスナップショット** - このオプションは、エクスポートプロジェクトパッケージに既存のデータベーススナップショットを含みます

    {{% alert type="info" %}}このオプションはスナップショットがすでに作成されている場合にのみ使用できます。 必要に応じて、 **バージョンコントロール** > **データのスナップショットを追加** を介してスナップショットを作成できます。
    {{% /alert %}}

* **現在のデータベースからの新しいスナップショット** - データベースから新しいスナップショットを作成し、エクスポートに含めます

    {{% alert type="info" %}}このオプションは、アプリをローカルで実行した後、少なくとも一度は使用できます。 アプリを初めて実行するときにローカルデータベースが作成されるからです。
    {{% /alert %}}

## 4 続きを読む

* [プロジェクトパッケージのインポート](import-project-package-dialog)
* [バージョン管理メニュー](version-control-menu)
