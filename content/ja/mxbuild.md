---
title: "MxBuild"
category: "全般"
menu_order: 50
description: "Mendix Appsを構築およびデプロイするためのコマンドラインツールであるMxBuildの説明"
tags:
  - "ビルド"
  - "デプロイ"
  - "デプロイパッケージ"
  - "コマンド"
---

## 1つの紹介

MxBuild は、Mendix プロジェクトから Mendix Deployment Package を構築するのに使用できる Windows および Linux のコマンドラインツールです。

必要な MxBuild のバージョンは、ビルドする Mendix モデルのバージョンによって異なります。 正しいMxBuildのダウンロードは、 `https://cdn.mendix.com/runtime/mxbuild-{mxversion}.tar.gz` のリンクから確認できます。

{{% alert type="info" %}}

Mendix バージョン 7.18.1 以降では、バージョンにビルド番号が含まれており、リンクパスに含める必要があります。 例:

* 7.17.2
* 7.18.1.40272

Mendixインストールのパスにビルド番号が記載されています(例えば `C:\Program Files\Mendix\7.18.1.40272`)。

{{% /alert %}}

MxBuild for Mendix バージョン 7.18.1 は [https://cdn.mendix.com/runtime/mxbuild-7.18.1.40272.tar.gz](https://cdn.mendix.com/runtime/mxbuild-7.18.1.40272.tar.gz) にあります。

お気に入りのアーカイブツールを使用して、 [7-Zip](https://www.7-zip.org/)などのファイルを抽出できます。

MxBuild のシステム要件はこちらに記載されています: [システム要件](system-requirements#mxbuild).

{{% alert type="info" %}}
特に言及されている場合を除き、このドキュメントで使用されている例はWindows用です。
{{% /alert %}}

## 2つのコマンドライン

パッケージをビルドするには、コマンドラインにデプロイメント・パッケージ(.mda)をビルドするMendixプロジェクト・ファイル(.mpr)を指定します。 ファイル名の前には、相対パスまたは絶対パスを使用できます。 プロジェクト ファイルは Mendix プロジェクト ディレクトリ内に配置する必要があります。

MxBuild では、Mendix プロジェクトの処理方法を制御する多数のコマンドラインオプションが使用されます。 これらのオプションはプロジェクト ファイルの名前の前にあります。

Windows では、コマンド ラインに次の形式を使用します。

`MxBuild --java-home="JDKDirectory" --java-exe-path="javaExecutable" [options] projectFile`

次のコマンドライン形式を使用して、Linux上でMxBuildを実行することもできます。

`mono mxbuild.exe --java-home="JDory" --java-exe-path="javaExecutable" [options] projectFile`

デプロイパッケージを作成すると、MxBuild プロセスは終了します。

{{% alert type="info" %}}
このドキュメントで使用されている例は Windows 用です。
{{% /alert %}}

### 2.1 一般的なコマンドラインオプション


<!-- Note to editor: the &nbsp; here makes the column wider so that options are not broken at hyphens
  The alternative of using non-breaking hyphens means that a cut and paste may not work -->

| Option&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 説明                                                                                                                                                                                                                                                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-h`, `--help`                                                                                                                                                                                               | MxBuild の簡単な説明と、利用可能なすべてのオプションのリストを印刷します。                                                                                                                                                                                                                                                                                                                                                      |
| `--java-home=DIRECTORY`                                                                                                                                                                                      | (required) the directory in which the JDK is installed<br/>for example: `--java-home=/usr/lib/jvm/java-8-oracle`<br/>for Windows the *DIRECTORY* should be enclosed in double-quotes, `"`.                                                                                                                                                                                         |
| `--java-exe-path=FILENAME`                                                                                                                                                                                   | (required) the **full path** to the Java executable<br/>for example `--java-exe-path=/usr/lib/jvm/java-8-oracle/bin/java`<br/>for Windows the *DIRECTORY* should be enclosed in double-quotes, `"`, and must contain the complete file name `...\java.exe`.                                                                                                                       |
| <code>––target=[package&#124;deploy]</code>                                                                                                                                                                                    | `パッケージ` (オプションが省略された場合のデフォルト): デプロイパッケージを作成します。 da file) ` ` deploy<br/>`deploy`: デプロイパッケージを作成せずにプロジェクトのデプロイを行う。                                                                                                                                                                                                                                                                         |
| `--lose-version-check`                                                                                                                                                                                       | create a deployment package from a project which was created with a lower Mendix version.<br/>The project will be upgraded to the MxBuild version before the deployment package is created.<br /> Any changes included as a result of this upgrade will **not** be stored in your project.                                                                                         |
| `--write-errors=FILENAME`                                                                                                                                                                                    | Write all errors, warnings and deprecations encountered during deployment of the project to the specified file in JSON format.<br />This file is only written when the project contains errors.<br />If the file already exists, it will be overwritten without warning.<br />See section 4, [Project Errors](#project-errors) for a description of the format of this file. |

### 2.2 パッケージ作成時のオプション

{{% alert type="info" %}}
以下のオプションは、 `--target=package` オプションでのみ適用できます。
{{% /alert %}}

| Option&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 説明                                                                                                                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-o FILENAME` または<br/>`--output=FILENAME`                                                                                                                                                                                                                                                                                            | The name (with optional relative or absolute path) of the .mda file that is created by MxBuild.<br />If this option is omitted, the file will be saved in the *current* directory with the name `out.mda`. |
| `--project-name=NAME`                                                                                                                                                                                                                                                                                                                      | Mendix Runtimeで使用するアプリケーションの名前を変更します。<br />このオプションが指定されていない場合、プロジェクトの名前が使用されます。                                                                                                                            |
| `--model-version=VERION`                                                                                                                                                                                                                                                                                                                   | パッケージ内のモデルに特定のバージョン番号を適用します。                                                                                                                                                                                     |
| `--model-description =DESCRIPTION`                                                                                                                                                                                                                                                                                                         | パッケージにモデルの説明を埋め込みます。                                                                                                                                                                                             |

For example, to create a deployment package `out.mda` in the current directory using the app `MyApp` using the *Windows* version of MxBuild, you could use the command:

```bat
mxbuild --target=package --java-home="C:\Program Files\Java\jdk1.8.0_144" --java-exe-path="C:\Program Files\Java\jdk1.8.0_144\bin\java.exe" "C:\Users\username\Documents\Mendix\MyApp\MyApp.mpr"
```

## 3返品コード

MxBuild 終了時、次のコードのいずれかが返されます：

| 終了コード | 説明                      |
| ----- | ----------------------- |
| 0     | MxBuild が正常に終了しました      |
| 1     | 内部エラーが発生                |
| 2     | コマンドラインオプションに問題があります    |
| 3     | Mendix プロジェクトの展開に失敗しました |


終了コードが 0 より大きい場合、MxBuild もエラーを記述するメッセージを出力します。

## 4 プロジェクトエラー {#project-errors}

Mendixプロジェクトにエラーが含まれている場合、デプロイは失敗し、MxBuildはこれらのエラーを報告します。 `--write-errors=FILENAME` コマンドラインオプションを使用して MxBuild にエラーをファイルに書き込むように指示することができます。

エラーは、1 つのプロパティ `問題` を持つ JSON オブジェクトとして出力されます。 このプロパティの値は、プロジェクト内の1つのエラー、警告、または非推奨を記述するオブジェクトの配列です。 例:

```json
{
  "problems": [
    {
      "name": null,
      "severity": "Error",
      "message": "Start event cannot be the last object of a flow.",
      "locations": [
        {
          "elementId": "252e1008-d795-4e49-b3e3-2ba38eb0a56d",
          "unitId": "1a8a3593-6f01-43a3-bc22-bd22f9244983",
          "element": "Start event",
          "document": "Microflow 'MyMicroflow'",
          "module": "MyModule"
        }
      ]
    }
  ]
}
```

次の表は、 *問題* JSON オブジェクトの様々なプロパティについて説明しています。

| 属性      | 説明                                                          |
| ------- | ----------------------------------------------------------- |
| `名前`    | 整合性チェックがMendix Metamotelでまだ定義されていない場合、問題の一意の識別子、または `null`。 |
| `重要度`   | 問題の種類を説明します: `警告`, `エラー` または `廃止`.                          |
| `メッセージ` | 問題の説明 これはMendix Modelerの「Errors」ドックのメッセージと同じです。             |
| `場所`    | 問題が発生したMendixプロジェクト内の場所を記述する0個以上のオブジェクトが含まれています(次の表を参照)。    |

この問題に関連付けられた場所には、次のプロパティがあります。

| 属性          | 説明                       |
| ----------- | ------------------------ |
| `elementId` | 問題が発生したモデル要素の一意の id です。  |
| `unitId`    | 問題が発生したドキュメントの一意の id です。 |
| `要素`        | 問題が発生したモデル要素の説明。         |
| `ドキュメント`    | 問題が発生するドキュメントの説明。        |
| `モジュール`     | 問題が発生するモジュールの説明。         |
