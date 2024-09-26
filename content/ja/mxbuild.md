---
title: "MxBuild"
category: "一般情報"
menu_order: 50
description: "Mendix Appsを構築およびデプロイするためのコマンドラインツールであるMxBuildの説明"
tags:
  - "ビルド"
  - "デプロイする"
  - "デプロイパッケージ"
  - "コマンド"
  - "studio pro"
---

## 1つの紹介

MxBuild は Windows および Linux のコマンドラインツールで、Mendix プロジェクトから Mendix Deployment Package をビルドするのに使用できます。

必要な MxBuild のバージョンは、ビルドする Mendix モデルのバージョンによって異なります。 You can find your correct MxBuild by entering this URL into a browser and replacing `mxversion` with your own, full Mendix version number: `https://cdn.mendix.com/runtime/mxbuild-{mxversion}.tar.gz`.

{{% alert type="info" %}}

A build number is included in the version, and this has to be included in the link path mentioned above — for example`8.12.1.3458` is the 3458 build of the 8.12.1 Studio Pro release.

You can find the build number in path of your Mendix installation (for example if your installation looks like this `C:\Program Files\Mendix\8.12.1.3458`, use this URL to get your files: https://cdn.mendix.com/runtime/mxbuild-8.12.1.3458.tar.gz).

この [Studio Pro リリース一覧の公開バージョン](https://marketplace.mendix.com/link/studiopro/) では、MxBuild ファイルをダウンロードできます。 ファイルのダウンロードに問題が発生した場合は、ビルドがリストされていることを確認してください。

{{% /alert %}}

お気に入りのアーカイブツールを使用して、 [7-Zip](https://www.7-zip.org/)などのファイルを抽出できます。

MxBuildのシステム要件の詳細については、 [システム要件](system-requirements#mxbuild) を参照してください。

{{% alert type="info" %}}
特に言及されている場合を除き、このドキュメントで使用されている例はWindows用です。
{{% /alert %}}

## 2つのコマンドライン

パッケージをビルドするには、コマンドラインにデプロイメント・パッケージ(.mda)をビルドするMendixプロジェクト・ファイル(.mpr)を指定します。 ファイル名の前には、相対パスまたは絶対パスを使用できます。 プロジェクト ファイルは Mendix プロジェクト ディレクトリ内に配置する必要があります。

MxBuild では、Mendix プロジェクトの処理方法を制御する多数のコマンドラインオプションが使用されます。 これらのオプションはプロジェクト ファイルの名前の前にあります。

コマンド ラインには、次の形式を使用します。

`MxBuild --java-home="JDKDirectory" --java-exe-path="javaExecutable" [options] projectFile`

次のコマンドライン形式を使用して、Linux上でMxBuildを実行することもできます。

`mono mxbuild.exe --java-home="JDory" --java-exe-path="javaExecutable" [options] projectFile`

デプロイパッケージを作成すると、MxBuild プロセスは終了します。

### 2.1 一般的なコマンドラインオプション

コマンドラインオプションは以下の表に記載されています。

| Option&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 説明                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-h`, `--help`                                                                                                                                                                                               | MxBuild の簡単な説明と、利用可能なすべてのオプションのリストを印刷します。                                                                                                                                                                                                                                                                                                                                                                  |
| `--java-home=DIRECTORY`                                                                                                                                                                                      | (必須)。 The directory in which the JDK is installed.<br/>For example, `--java-home=/usr/lib/jvm/java-8-oracle`.<br/>For Windows the *DIRECTORY* should be enclosed in double-quotes `"`.                                                                                                                                                                                                         |
| `--java-exe-path=FILENAME`                                                                                                                                                                                   | (必須)。 The **full path** to the Java executable.<br/>For example, `--java-exe-path=/usr/lib/jvm/java-8-oracle/bin/java`.<br/>For Windows the *DIRECTORY* should be enclosed in double-quotes `"`, and must contain the complete file name `...\java.exe`.                                                                                                                                      |
| <code>––target=[package&#124;deploy]</code>                                                                                                                                                                                    | `パッケージ`: オプションが省略された場合はデフォルト。 デプロイパッケージ(.mda file)を作成します。<br/>`deploy`: デプロイパッケージを作成せずにプロジェクトをデプロイします。                                                                                                                                                                                                                                                                                               |
| `--lose-version-check`                                                                                                                                                                                       | Creates a deployment package from a project which was created with a lower Mendix version.<br/>The project will be upgraded to the MxBuild version before the deployment package is created.<br /> Any changes included as a result of this upgrade will **not** be stored in your project.                                                                                                    |
| `--write-errors=FILENAME`                                                                                                                                                                                    | Writes all errors, warnings, and deprecations encountered during deployment of the project to the specified file in JSON format.<br />This file is only written when the project contains errors.<br />If the file already exists, it will be overwritten without a warning.<br />For a description of the format of this file, see the [Project Errors](#project-errors) section below. |

### 2.2 パッケージ作成時のオプション

{{% alert type="info" %}}
以下のオプションは、 `--target=package` オプションでのみ適用できます。
{{% /alert %}}

パッケージの作成時のオプションについては、以下の表を参照してください。

| Option&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 説明                                                                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-o FILENAME` または<br/>`--output=FILENAME`                                                                                                                                                                                                                                                                                            | The name (with optional relative or absolute path) of the .mda file that is created by MxBuild.<br />If this option is omitted, the file will be saved in the *current* directory under a name `out.mda`. |
| `--project-name=NAME`                                                                                                                                                                                                                                                                                                                      | アプリケーションの名前をMendix Runtimeで使用される名前に変更します。<br />このオプションが指定されていない場合、プロジェクトの名前が使用されます。                                                                                                                       |
| `--model-version=VERION`                                                                                                                                                                                                                                                                                                                   | パッケージ内のモデルに特定のバージョン番号を適用します。                                                                                                                                                                                    |
| `--model-description =DESCRIPTION`                                                                                                                                                                                                                                                                                                         | パッケージにモデルの説明を埋め込みます。                                                                                                                                                                                            |

For example, to create a deployment package `out.mda` in the current directory using the app `MyApp` using the *Windows* version of MxBuild, you can use the following command:

```bat
mxbuild --target=package --java-home="C:\Program Files\Java\jdk1.8.0_144" --java-exe-path="C:\Program Files\Java\jdk1.8.0_144\bin\java.exe" "C:\Users\username\Documents\Mendix\MyApp\MyApp.mpr"
```

## 3返品コード

MxBuild 終了時、次のコードのいずれかが返されます：

| 終了コード | 説明                       |
| ----- | ------------------------ |
| 0     | MxBuild は正常に終了しました。      |
| 1     | 内部エラーが発生しました             |
| 2     | コマンドラインオプションに問題があります。    |
| 3     | Mendix プロジェクトの展開に失敗しました。 |


終了コードが 0 より大きい場合、MxBuild はエラーを説明するメッセージを表示します。

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

| 属性      | 説明                                                                |
| ------- | ----------------------------------------------------------------- |
| `名前`    | Mendix Metamotelで整合性チェックがまだ定義されていない場合、問題の一意の識別子または `null`。        |
| `重要度`   | 問題の種類を説明します: `警告`, `エラー`, または `非推奨`.                              |
| `メッセージ` | 問題の説明 これはMendix Studio Pro の [エラー ペイン](errors-pane) 内のメッセージと同じです。 |
| `場所`    | 問題が発生したMendixプロジェクト内の場所を記述する0個以上のオブジェクトが含まれています(次の表を参照)。          |

この問題に関連付けられた場所には、次のプロパティがあります。

| 属性          | 説明                       |
| ----------- | ------------------------ |
| `elementId` | 問題が発生したモデル要素の一意の id です。  |
| `unitId`    | 問題が発生したドキュメントの一意の id です。 |
| `要素`        | 問題が発生したモデル要素の説明。         |
| `ドキュメント`    | 問題が発生するドキュメントの説明。        |
| `モジュール`     | 問題が発生するモジュールの説明。         |
