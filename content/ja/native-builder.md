---
title: "Native Builder (CLI)"
parent: "native-Mobile"
menu_order: 70
tags:
  - "ネイティブ"
  - "モバイル"
  - "デプロイする"
  - "native-builer"
  - "ビルダー:"
  - "appcenter"
  - "非推奨です"
---

{{% alert type="warning" %}}
Native Builder CLI は、Studio Pro と統合された UI ツールである Mendix Native Mobile Builder に代わって廃止されました。 アプリのデプロイ方法については、こちら [](/howto/mobile/deploying-native-app) をご覧ください。
{{% /alert %}}

{{% alert type="warning" %}}
Native Builder v3.2.1 以上にアップデートしてください。 Native Builder v3.2. **マスター** を使用して **メイン** をデフォルトのリポジトリブランチ名として使用するように、GitHub の移行に対して必要な修正が含まれています。
{{% /alert %}}

## 1つの紹介

Native Builderは、ネイティブプロファイルを含むMendixプロジェクトを受け取り、iOSとAndroid用のネイティブモバイルアプリをパッケージ化します。 Native Builderの使用方法の詳細については、 [First Mendix Native Mobile Appをデプロイする方法](/howto8/mobile/deploying-native-app) を参照してください。

Native Builderでは、MxBuild、GitHub、App Centerを使用してアプリケーションを構築します。 このツールは、これらのプロセスの構成を自動化し、アプリの構築体験を合理化します。 The Native builder allows you to create as many apps on GitHub as possible, as long as they are given unique app names using the `--project-name` parameter (for more information, see the [Commands](#commands) section below). `prepare` と `build` コマンドの組み合わせを使用すると、Native Builderは以下のようにアプリケーションをパッケージ化します。

1. Mendixプロジェクトをローカルにデプロイします。
2. 提供されたMendixバージョンに適合するMendixネイティブテンプレートリポジトリの最新バージョンを使用して(指定されたプロジェクト名引数を使用して名前を付けられる)新しいリポジトリを作成します。
3. **build/{build number provided to the tool}** と呼ばれる新しいリポジトリに新しいブランチを作成します。
4. 新しいリポジトリのビルドブランチに必要なファイルとアセットをコミットします。
5. App Center でアプリを設定します。
6. iOS と Android 用のビルドを開始します。
7. ビルドの進行状況情報を提供します。
8. ビルドが成功した場合はzipされたアプリを、ビルドに失敗した場合はビルドログファイルをダウンロードします。

## 2つのコマンド {#commands}

コマンドライン引数は、Mendixプロジェクトがどこにあるかなど、ネイティブビルダーに情報を提供します。 コマンドは以下に示すパラメータを使用して構成されます。 これらのパラメータのいくつかは必須または強く推奨されます。 それらの残りの部分はオプションであり、それらがあなたのアプリに関連するときに使用する必要があります。 パラメータを使用してコマンドを作成するには、以下の操作を行います:

1. アイコンまたは *.exe* ファイルを右クリックし、 **管理者として実行** を選択して、コマンドラインプログラムを管理者として開きます。
2.  `cd "{your Native Builder .exe location}"` と入力し、 <kbd>Enter</kbd> を押して、ネイティブビルダーのディレクトリをターゲットにします :

    ![ディレクトリの変更](attachments/native-builder/change-directory.png)

### 2.1 Prepare {#prepare}

`準備` コマンドは、GitHub と App Center の両方でアプリの作成を処理します。 アイコンアセットとスプラッシュ画像を設定し、Java、Mendix、およびプロジェクトパスを検証します。 設定ファイルは、後で使用するためにその情報を保持するためにユーザーフォルダに対して相対的に生成されます。 `prepare` コマンドを使用して、更新したい引数を渡すことで、この設定を更新できます。

`prepare` コマンドの例:

```bash
native-builder.exe prepare --github-access-token <token> --appcenter-api-token <token> --java-home <absolute-path> --mxbuild-path <absolute-path> --project-path <absolute-path-to-mpr-file> --projectName CoolApp --app-identifier "com.company.myapp" --app-name "My Cool App" -mendix-version 8.5.0
```

| パラメータ                            | 説明                                                      | 例                                                        |
| -------------------------------- | ------------------------------------------------------- | -------------------------------------------------------- |
| `--github-access-token`          | GitHub access token.                                    | `c0e1dasf1e102c55ded223dbdebdbe59asf95224`               |
| `--appcenter-api-token`          | App Center API トークン                                     | `3e18asdfb43f4fe6c85afsd0bf60dde72f134`                  |
| `--appcenter-organization`       | App Center の組織名。                                        | `私の会社`                                                   |
| `--project-name`                 | プロジェクトの一意の名前。 **(必須)**                                  | `CoolApp`                                                |
| `--app-name`                     | アプリの名前を表示します。                                           | `私のクールなアプリ`                                              |
| `--app-identifier`               | Unique app identifier.                                  | `com.mendix.MyAwesomeApp`                                |
| `--app-icon-path`                | アプリアイコンへの絶対パス。                                          | `C:\MyAppIcon.png`                                      |
| `--app-round-icon-path`          | Android専用の丸いアイコンへの絶対パス。                                 | `C:\MyAppRoundIcon.png`                                 |
| `--app-splash-screen-path`       | アプリのスプラッシュ画面画像への絶対パスです。                                 | `C:\MyAppSplash.png`                                    |
| `--java-home`                    | Java実行可能ファイルがあるディレクトリへの絶対パス。                            | `C:\Program Files\Java\jdk-10.0.1`                    |
| `--project-path`                 | Mendixプロジェクトファイルへの絶対パス。                                 | `C:\MyApp\MyApp.mpr`                                   |
| `--mxbuild-path`                 | MxBuild 実行ファイルへの絶対パス。                                   | `C:\Program Files\Mendix\8.0.0\modeler\mxbuild.exe` |
| `--runtime-url`                  | Mendix ランタイムの URL です。                                   | `https://myapp.mendixcloud.com`                          |
| `--mendix-version`               | Mendix Studio Proバージョンでは、Mendixプロジェクトが使用しています。 **(必須)** | `8.5.0`                                                  |
| `--firebase-android-config-path` | *google-services.json* ファイルへの絶対パス。                      | `C:\MyApp\google-services.json`                        |
| `--firebase-ios-config-path`     | *GoogleService-Info.plist* ファイルへの絶対パス。                  | `C:\MyApp\GoogleService-Info.plist`                    |


### 2.2 ビルド {#build}

#### 2.2.1 配布用のアプリの生成

`ビルド` コマンドは、JavaScript バンドルとアセットをビルドし、GitHub 上でビルドを作成し、App Center でビルドを初期化します。

すでに `prepare`を実行している場合、以下は `build` コマンドの例です。

```bash
native-builder.exe build --project-name "CoolApp" --app-version "1.0.0" --build-number 1
```

| パラメータ                      | 説明                                                      | 例                                                        |
| -------------------------- | ------------------------------------------------------- | -------------------------------------------------------- |
| `--project-name`           | `で使用されるプロジェクトのユニークな名前`。                                 | `CoolApp`                                                |
| `--app-version`            | アプリのバージョンはセマンティックバージョンのみです。  **(ストロング推奨)**              | `1.2.3`                                                  |
| `--build-number`           | ビルド番号、任意の一意の整数値。 **(必須)**                               | `1`                                                      |
| `--github-access-token`    | GitHub access token.                                    | `c0e1dasf1e102c55ded223dbdebdbe59asf95224`               |
| `--appcenter-api-token`    | App Center API トークン                                     | `3e18asdfb43f4fe6c85afsd0bf60dde72f134`                  |
| `--appcenter-organization` | App Center の組織名。                                        | `私の会社`                                                   |
| `--app-name`               | アプリの名前を表示します。                                           | `私のクールなアプリ`                                              |
| `--app-identifier`         | Unique app identifier.                                  | `com.mendix.MyAwesomeApp`                                |
| `--app-icon-path`          | アプリアイコンへの絶対パス。                                          | `C:\MyAppIcon.png`                                      |
| `--app-round-icon-path`    | Android専用の丸いアイコンへの絶対パス。                                 | `C:\MyAppRoundIcon.png`                                 |
| `--app-splash-screen-path` | アプリのスプラッシュ画面画像への絶対パスです。                                 | `C:\MyAppSplash.png`                                    |
| `--java-home`              | Java実行可能ファイルがあるディレクトリへの絶対パス。                            | `C:\Program Files\Java\jdk-10.0.1`                    |
| `--project-path`           | Mendixプロジェクトファイルへの絶対パス。                                 | `C:\MyApp\MyApp.mpr`                                   |
| `--mxbuild-path`           | MxBuild 実行ファイルへの絶対パス。                                   | `C:\Program Files\Mendix\8.0.0\modeler\mxbuild.exe` |
| `--runtime-url`            | Mendix ランタイムの URL です。                                   | `https://myapp.mendixcloud.com`                          |
| `--output-path`            | アーティファクトが行くべき場所への絶対パス。                                  | `C:\ダウンロード`                                             |
| `--platform`               | コマンドを実行するプラットフォーム。 デフォルトはiOSとAndroidの両方です。              | `ios` または `android`                                      |
| `--skip-mxbuild`           | JavaScript バンドルとアセットをバンドルする場合に使用します。 デフォルトは `false` です。 | `true` または `false`                                       |

#### 2.2.2 カスタム開発者アプリの生成 {#generate}

`build dev-app` コマンドを使用すると、Make It Native アプリとよく似たプレビューアプリが作成されます。 ただし、それが作成するプレビューアプリは、プロジェクトとStudio Proバージョンの両方に固有のカスタム開発者アプリになります。 このコマンドは GitHub で **** ブランチを作成し、App Center でビルドを初期化します。 また、 `prepare` コマンドを少なくとも一度実行することを期待しています。

以下に、 `build dev-app` を備えたコマンドの例を示します。

```bash
native-builder.exe build dev-app --project-name "CoolApp" --output-path "C:\bundles\developer"
```

| パラメータ            | 説明                                         | 例                        |
| ---------------- | ------------------------------------------ | ------------------------ |
| `--project-name` | `で使用されるプロジェクトのユニークな名前`。 **(必須)**           | `CoolApp`                |
| `--output-path`  | *ZIP* アーカイブの絶対出力パス。                        | `C:\bundles\developer` |
| `--platform`     | コマンドを実行するプラットフォーム。 デフォルトはiOSとAndroidの両方です。 | `ios` または `android`      |

### 2.3 再生 {#regenerate}

`regenerate` コマンドは、 `Native Template`の最新バージョンを使用して GitHub 上のプロジェクトを再作成します。 変更がある場合は新しい名前で前のアプリに名前を変更し、App Center アプリのビルド設定を更新します。 `regenerate` を実行すると、 `prepare` が `--project-name` で少なくとも1回は実行されていることを期待します。

{{% alert type="info" %}}
以前のテンプレートに加えた変更を自動保存する方法はありません。 いくつかある場合は、新しい GitHub リポジトリで手動で適用する必要があります。 さらに、アプリケーションの Mendix バージョンを変更する場合は、 `mxbuild-path` を `prepare` コマンドを使用して更新してください。
{{% /alert %}}


| パラメータ              | 説明                                            | 例                 |
| ------------------ | --------------------------------------------- | ----------------- |
| `--project-name`   | Java実行可能ファイルがあるディレクトリへの絶対パス。                  | `私のクールなアプリ`       |
| `--mendix-version` | プロジェクトが使用しているMendix Studio Proバージョン。 **(必須)** | `8.5.0` または `8.5` |

`regenerate` コマンドの例:

```bash
native-builder.exe regenerate --project-name "CoolApp" --mendix-version 8.5.0
```

| パラメータ            | 説明                      | 例         |
| ---------------- | ----------------------- | --------- |
| `--project-name` | `で使用されるプロジェクトのユニークな名前`。 | `CoolApp` |

### 2.4 空気配備上のリリースの作成 {#ota}

`push-update` コマンドは、新しいJavaScriptバンドルとアセットの生成と、それをOTA(Air (OTA)アップデート)上でデプロイを処理します。

以下は、 `push-update` を備えたコマンドの例です。

```bash
native-builder.exe release push-update --project-name "CoolApp" --target-version "1.0.0" --build-number 1 ---rolout-percentage 100
```

| パラメータ                  | 説明                                                        | 例                                                                        |
| ---------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------ |
| `--project-name`       | `で使用されるプロジェクトのユニークな名前`。 **(必須)**                          | `CoolApp`                                                                |
| `--target-version`     | このアップデートが影響を与えるはずの既に公開されているアプリのバージョンまたはバージョンの範囲。 **(必須)** | セマンティックバージョン セマンティックバージョン [セマンティックバージョン](https://semver.org/) を参照してください。 |
| `--rollout-percentage` | この更新を受けるべきユーザーの割合。 一度設定すると、値を減らすことはできません。 **(必須)**        | `1` から `100` の間の数。                                                       |
| `--build-number`       | このアップデートがターゲットとするApp Centerビルド番号。 **(必須)**                | `ビルド` で定義された任意の数                                                         |
| `--description`        | ユーザーがダウンロードする前に表示されるこのアップデートに関連付けられている詳細情報。               | 任意のテキストメッセージ。                                                            |
| `--mandatory`          | この更新を重要視し、ユーザーに強制的に適用するかどうかを決定します。 デフォルトは true です。        | `true` または `false`                                                       |
| `--platform`           | コマンドを実行するプラットフォーム。 デフォルトはiOSとAndroidの両方です。                | `ios` または `android`                                                      |
| `--deployment-target`  | OTAターゲットグループ デフォルトは `生産`です。                               | `ステージング中`                                                                |
| `--skip-mxbuild`       | JavaScript バンドルとアセットをバンドルする場合に使用します。 デフォルトは `false` です。   | `true` または `false`                                                       |

### 2.5 OTA 導入リリースのメタデータの更新 {#update-ota}

The `patch-update` command allows you to update the metadata of a published update that has not been rolled out to all users (in technical terms, an update which does not have a `rollout-percentage` value of `100`).

以下は、 `パッチアップデート`を備えたコマンドの例です。

```bash
native-builder.exe リリース パッチ-update --project-name "CoolApp" --label "v4" --target-version "1.0.1"
```

| パラメータ                  | 説明                                               | 例                                                               |
| ---------------------- | ------------------------------------------------ | --------------------------------------------------------------- |
| `--project-name`       | `で使用されるプロジェクトのユニークな名前`。 **(必須)**                 | `CoolApp`                                                       |
| `--label`              | パッチへのアップデートの一意のラベル。 **(必須)**                     | これは、 `release list` コマンドを使用して得ることができます。                         |
| `--target-version`     | すでに公開されているアプリのバージョンまたはバージョンの範囲で、更新が影響を与えるはずです。   | セマンティックバージョン管理 [セマンティックバージョン管理](https://semver.org/) を参照してください。 |
| `--rollout-percentage` | 更新を受けるべきユーザーの割合。 一度設定すると、値を減らすことはできません。          | `1` から `100` の間の数。                                              |
| `--description`        | ユーザーがダウンロードする前に表示されるアップデートに関連付けられている詳細情報。        | 任意のテキストメッセージ。                                                   |
| `--mandatory`          | 更新を必須にするかどうかを指定します。                              | `true` または `false`                                              |
| `--platform`           | コマンドを実行するプラットフォームを指定します。 デフォルトはiOSとAndroidの両方です。 | `ios` または `android`                                             |
| `--deployment-target`  | OTAターゲットグループ デフォルトは `生産`です。                      | `ステージング中`                                                       |

### 2.6 以前のリリースに戻る {#rollback}

`rollback-update` コマンドを使用すると、同じターゲットバージョンのアプリケーションで、以前のリリースに戻すことができます。 このコマンドは、 `--label` 引数で指定された以前のリリースを使用して新しいリリースを作成します。

以下は、 `rollback-update` を特徴とするコマンドの例です。

```bash
native-builder.exe リリース rollback-update --project-name "CoolApp" --label "v4"
```

以下の点に注意してください。

* `--label` パラメータは以前のリリースのみを指すことができます
* 壊れたリリースにロールバックすると、ユーザーにデプロイされます。 この状況を修正するには、新しいリリースを実行するか、ワーキングリリースにロールバックする必要があります。

| パラメータ                 | 説明                                         | 例                                       |
| --------------------- | ------------------------------------------ | --------------------------------------- |
| `--project-name`      | `で使用されるプロジェクトのユニークな名前`。 **(必須)**           | `CoolApp`                               |
| `--label`             | ロールバックする安定版のユニークなラベル。 **(必須)**             | これは、 `release list` コマンドを使用して得ることができます。 |
| `--platform`          | コマンドを実行するプラットフォーム。 デフォルトはiOSとAndroidの両方です。 | `ios` または `android`                     |
| `--deployment-target` | OTAターゲットグループ デフォルトは `生産`です。                | `ステージング中`                               |

### 2.7 商品展開リリース

`list` コマンドは、デプロイされたすべてのリリースの整形印刷リストを表示します。

`list` をフィーチャーしたコマンドの例を以下に示します。

```bash
native-builder.exe リリースリスト --project-name "CoolApp"
```

| パラメータ                 | 説明                                         | 例                   |
| --------------------- | ------------------------------------------ | ------------------- |
| `--project-name`      | `で使用されるプロジェクトのユニークな名前`。 **(必須)**           | `CoolApp`           |
| `--platform`          | コマンドを実行するプラットフォーム。 デフォルトはiOSとAndroidの両方です。 | `ios` または `android` |
| `--deployment-target` | OTAターゲットグループ デフォルトは `生産`です。                | `ステージング中`           |

### 2.8 アプリバンドルのみ生成する

`bundle` コマンド **は、MXBuild ステップ** のみを実行します(GitHub の設定と App Center のビルドステップをスキップします)。 このコマンドは *ZIP* アーカイブを対応する JavaScript バンドルと各プラットフォームのリソースで出力します。

`bundle` をフィーチャーしたコマンドの例を以下に示します:

```bash
native-builder.exe bundle --project-name "CoolApp" --output-path "C:\bundles"
```

| パラメータ            | 説明                                         | 例                   |
| ---------------- | ------------------------------------------ | ------------------- |
| `--project-name` | `で使用されるプロジェクトのユニークな名前`。 **(必須)**           | `CoolApp`           |
| `--output-path`  | *ZIP* アーカイブの絶対出力パス。 **(必須)**               | `C:\bundles`       |
| `--platform`     | コマンドを実行するプラットフォーム。 デフォルトはiOSとAndroidの両方です。 | `ios` または `android` |

### 2.9 iOS 固有の構成

iOS の設定を変更するコマンドは、 `config ios` コマンドの下にグループ化されています。

#### 2.9.1 エンタイトルメントの追加と削除

エンタイトルメントを追加または削除するには、 `アドエンタイトルメント` または `削除エンタイトルメント` コマンドを使用します。

```bash
native-builder.exe config ios add-enitlements --project-name "CoolApp" --enitlements notification nfc
```

| パラメータ            | 説明                                                  | 例         |
| ---------------- | --------------------------------------------------- | --------- |
| `--project-name` | `で使用されるプロジェクトのユニークな名前`。 **(必須)**                    | `CoolApp` |
| `--enitlements`  | プロジェクトに追加する権利の一覧です。 サポートされているオプションは `通知` と `nfc` です | `通知 nfc`  |

#### 2.9.2 バックグラウンドモードの追加と削除

バックグラウンドモードを追加または削除するには、 `add-background-mode` または `remove-background-mode` コマンドを使用します。

```bash
native-builder.exe config ios add-background-mode --project-name "CoolApp" --modes notification
```

| パラメータ            | 説明                                                 | 例         |
| ---------------- | -------------------------------------------------- | --------- |
| `--project-name` | `で使用されるプロジェクトのユニークな名前`。 **(必須)**                   | `CoolApp` |
| `--mode`         | プロジェクトに追加するバックグラウンドモードのリスト。 `通知` オプションがサポートされています。 | `通知`      |

## 3 拡張パラメータの説明 {#parameters}

### 3.1 --project-name

このパラメータはアプリケーションのユニークな名前で、任意の文字を含めることができます。 この名前は、マシンに `--github-access-token` のような一般的なパラメータ設定を保持するために使用されます。 これにより、必要な他のコマンドとの再利用性が向上します。 GitHubやApp Centerでもアプリ名として使用されています。

### 3.2 --runtime-url

このパラメータは、アプリケーションを実行するランタイムを指す必要があります。 ローカルにデプロイされたアプリに対してテストする場合は、マシンのIPアドレスを使用してください（例： `http://192.168.1.12:8080`）。 Mendix Cloud-deployされたアプリケーションに対してテストする場合は、デプロイメントサーバーの完全修飾ランタイムURLを使用してください(例えば、 `https://myapp.mendixcloud.com`)。 正しいプロトコルを追加する必要があります。それ以外の場合、URLはデフォルトで `http://`で始まります。

### 3.3 --appcenter-organization

App Center では、1 つ以上の組織のメンバーになることができます。 アプリを組織の一部として構築する必要がある場合 次に、 `--appcenter-organization` を使用して、その組織名をNative Builderに提供します。 コマンドライン引数を外した場合、アプリは個人用App Centerアカウントの一部となります。

### 3.4 --app-name

このパラメータはアプリの表示名で、選択した任意の文字を含めることができます。 ユーザーがデバイスにアプリをインストールすると、この名前が表示されます。 iOSアプリの場合、これは [CFBundleDisplayName](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CoreFoundationKeys.html#//apple_ref/doc/uid/20001431-110725) として機能します。 Android アプリの場合、これは `AndroidManifest.xml` ファイル内の `アプリケーション` タグの *android:label* プロパティとして機能します。

### 3.5 --app-version

このパラメータは、ビルドするアプリのバージョンを指定します。 適切なバージョン番号を選択する方法については [セマンティック バージョニング](https://semver.org/) を参照してください。

### 3.6 --app-identifier

このパラメータはアプリの一意の識別子として機能します これは、Android の [アプリケーション ID](https://developer.android.com/studio8/build/application-id) 要件と Apple の [CFBundleIdentifier](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CoreFoundationKeys.html) 要件に準拠する必要があります。 App を Apple App Store や Play Store にアップロードすると、アプリの識別子は変更できなくなります。 アプリが公開された後に識別子を変更した場合は、両方のストアで異なるアプリとして扱われます。 アプリの識別子は、例えば {com.mendix.MyAwesomeApp} などの逆DNS表記として指定されます。

### 3.7 --platform

このパラメータを使用すると、特定のプラットフォームまたは両方のビルドを選択できます。 デフォルトでは、Native Builderは両方のプラットフォームでビルドを試行しますが、このパラメータはビルドをiOSまたはAndroidのみに制限することができます。

### 3.8 --skip-mxbuild

まれに、バンドル処理が完了した後にエラーが発生することがあります。 このパラメータを使用すると、テスト中に MxBuild をスキップして時間を節約できます。

### 3.9 --app-icon-path

アプリアイコンファイルを指定します。 画像は *.png* ファイルで、解像度は 1024x1024 である必要があります。 Mendixはあなたのためにサイズを変更します。 ファイルパスが指定されていない場合、デフォルトのアプリアイコンはブランチ **マスター** によって提供されます。

### 3.10 --app-round-icon-path

このパラメーターは、Android 固有のアプリの丸いアイコンファイルを指定します。 画像は *.png* ファイルで、解像度は 1024x1024 である必要があります。 Mendixはあなたのためにサイズを変更します。 ファイルパスが指定されていない場合、デフォルトのアプリアイコンはブランチ **マスター** によって提供されます。

### 3.11 --app-splash-screen-path

このパラメータはアプリのスプラッシュファイルを指定します。 画像は *.png* ファイルで、解像度は 1440x2560 である必要があります。 Mendixはあなたのためにサイズを変更します。 ファイルパスが指定されていない場合、デフォルトのアプリのスプラッシュ画像はブランチ **マスター** によって提供されます。

### 3.12 --build-number

このユニークな構成は、Android と iOS の両方のリリースビルドのバージョンビルド番号を表します。 リリース予定のビルドはすべて、一意の増分番号を持つ必要があります。 この番号は、App Center と GitHub のブランチ名として使用されます。

オーバーザエアアップデートでは、各ビルドは特定のリリース・グループ (`--deployment-target`) に関連付けられており、アップデートを取得します。 デフォルトでは、この値は **Production** に設定されており、通常はこのようにしておく必要があります。 変更された場合、新しい値は、その環境で動作しているデバイスのみが更新されることに注意する必要があります。

Android の最大の整数は 2,147,483,647 です。 1から始め、リリースごとに1ずつ増分することを検討してください。 あるいは、2020年7月31日、09:50のビルドに {2007310950} などの「YYmmmddHm」形式で日付を使用することもできます。

### 3.13 --mendix-version

このパラメータにより、Native BuilderはMendixプロジェクトのStudio Proバージョンに基づいてNative Templateの互換バージョンを選択します。 このパラメータは、Studio Pro の有効な意味バージョンである必要があります。例えば、8.5.1 です。 提供されたバージョンは可能な限り具体的である必要があります パッチのバージョンでも、利用可能なすべてのネイティブテンプレートと互換性のない修正が含まれている可能性があります。 どのMendixバージョンを使用しているかを確認するには、MendixプロジェクトのStudio Proバージョンの **About** ページまたはスプラッシュ画面を確認してください。

### 3.14 --verbose {#verbose}

このパラメータは、Native Builderでエラーが発生した場合の詳細を提供します。 `--verbose` が使用され、Native Builder エラーが発生すると、Native Builder はエラーの完全なスタックトレースを出力します。 これは、Native Builderが不明なエラーを伴う場合に便利です。


## 4つの高度な使い方 {#advanced-usage}

### 4.1 カスタムネイティブコード

カスタムネイティブの依存関係またはコードがある場合。 Native Builderが作成しているGitHubリポジトリの **マスター** ブランチに変更をマージすることで、アプリに追加することができます。 **マスター** からすべてのビルドが分岐し、変更内容が含まれます。 Mendixネイティブテンプレートから最新の変更を取得するには、リポジトリを時折同期することを忘れないでください。

リポジトリの同期の詳細については、 [ネイティブテンプレートを再生成するタイミング](#sync-your-repository) を参照してください。

### 4.2 カスタム App センターの設定

App Center では、ブランチレベルでビルドを設定できます。 ブランチ **マスター**で使用可能な設定がない場合、Native Builderはデフォルト設定を作成します。 構成がすでに存在する場合、ツールによって変更されません。 ビルドのブランチが初期化されると、 **master** の設定がコピーされます。 連続したビルドは、このブランチの設定を変更しません。 これは、 `regenerate` コマンドが使用されない限り、カスタム設定を上書きしないようにするためです。

### 4.3 カスタム開発者アプリ

Mendixアプリが成熟するにつれて、 (新しいネイティブ依存関係を必要とするカスタムウィジェットやロジックを導入するなど)機能を拡張したい場合があります。 カスタム開発者アプリは、Make It Native アプリの代替としてこの役割を果たします。 そして、Make It Native アプリでサポートされていないカスタム ウィジェットとロジックがある場合に使用する必要があります。 カスタム開発者アプリは、現在のプロジェクト構造を使用して自分で生成できるアプリです。 カスタムモジュールなど、進化するアプリをテストするためのあらゆる要件。 詳細については、 [カスタム開発者アプリの作成方法](/howto8/mobile/how-to-devapps) を参照してください。

## 5 ネイティブテンプレートを再生成する時 {#sync-your-repository}

ネイティブテンプレートは継続的に開発されています。 これは、Mendixプラットフォームの新機能に対応したり、問題を解決するために新しいバージョンが定期的にリリースされることを意味します。 新しいバージョンが利用可能になった場合、Native Builderはベース・テンプレートを更新するために `再生成` を実行することをお勧めします。

以下のシナリオでプロジェクトのテンプレートを更新する必要があります。

* すべてのStudio ProモジュールとリソースがMendixマーケットプレイスを使用して完全に更新されているにもかかわらず、アプリが予期せずクラッシュします
* Studio Pro のバージョンを更新しました

Native Templateは、実行中のStudio Proのバージョンと密接に結びついています。 そのため、プロジェクトが更新されるたびに、Native Builderを使用して `再生成` を実行してテンプレートを更新することを検討してください。

## 6エラーの解決

### 6.1 GitHub Errors

**不正なアクセストークン** — アクセストークンが無効です。 [GitHub トークン](/howto8/mobile/deploying-native-app#github-token) セクションを参照してください。 *最初のMendix Native Mobile App をデプロイする方法* そしてNative Builder にアクセストークンを提供します。

**リポジトリを作成できません: アクセストークンにはリポジトリスコープへのアクセスが必要** — アクセストークンが有効です。 しかし、Native Builderが動作するための権限が不足しています。 Native BuilderはテンプレートGitHubリポジトリをクローンし、ブランチを作成し、コミットファイルを作成します。 [GitHub トークン](/howto8/mobile/deploying-native-app#github-token) セクションを参照してください。 *最初のMendix Native Mobile App をデプロイする方法* そして、Native Builder に新しいアクセストークンを提供します。

**Unable to Delete Branch Build/{build number}** — GitHub との通信中に問題が発生しました。 接続を確認し、GitHubが利用可能であることを確認し、Native Builderを再度実行してみてください。

**Unable to Create Branch Build/{build number}** — GitHub との通信中に問題が発生しました。 接続を確認し、GitHubが利用可能であることを確認し、Native Builderを再度実行してみてください。

** {build number}をコミットできません** — GitHub との通信中に問題が発生しました。 接続を確認し、GitHubが利用可能であることを確認し、Native Builderを再度実行してみてください。

### 6.2 App Center エラー

**無効な API トークン** — 無効な API トークンです。 [App Center Token](/howto8/mobile/deploying-native-app#appcenter-token) のセクションに従ってください。 *最初のMendix Native Mobile App をデプロイする方法* そして、Native Builder にAPI トークンを提供します。

**Unable to Configure Build:{explanation}** — App Center との通信中に問題が発生しました。 接続を確認し、App Center が利用可能であることを確認し、Native Builder を再度実行してみてください。

**ビルド {build number} for App {app number} が失敗しました** — App Center 上のネイティブビルドが失敗しました。 Native Builderがダウンロードしたログファイルをお読みください。 ログファイルの名前は *{AppName}-{BuildNumber}.log* で、Native Builder の実行ファイルと同じフォルダにあります。

**ビルド設定がデフォルトで上書きされます** — Native Builderがビルド中のブランチが手動で設定されているかどうかを確認します。 偽陽性を感知するかもしれません これにより、カスタム設定が上書きされる可能性があります。 その場合は、App Center を使用してビルドを直接実行し、Native Builder を使用してこのブランチを使用することを検討してください。

**Unknown Error** — If you do not understand an error, you can sign in to App Center and delete the build configuration for the **master** branch. その後、Native Builderを再度実行します。 このツールは、 **master** とブランチのデフォルトのビルド設定を再作成します。

### 6.3 不明なエラー

Native Builderが実行に失敗し、エラーが発生しない場合。 エラーの完全なスタックトレースを得るために [--verbose](#verbose) パラメータを使用することを検討してください。 サポートを利用して問題を伝える場合、これらの追加ログとビルドログを提供することで、タイムリーなソリューションを実現することが常に便利です。

## 7 続きを読む

* [最初のMendixネイティブモバイルアプリをデプロイする方法](/howto8/mobile/deploying-native-app)
* [Native Mobileを使い始める方法](/howto8/mobile/getting-started-with-native-mobile)
* [Mendixネイティブモバイルアプリのスタイル設定](/howto8/mobile/how-to-use-native-styling)
