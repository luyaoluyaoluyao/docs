---
title: "ネイティブテンプレート"
parent: "native-Mobile"
menu_order: 12
tags:
  - "モバイル"
  - "テンプレート"
  - "ネイティブ"
  - "iOS"
  - "Android"
  - "リファレンスガイド"
---

## 1つの紹介

Mendixネイティブアプリ、具体的にはNative Templateをビルドする場合にテンプレートが必要です。 要するに、Native Templateはアプリケーションが必要とするネイティブの依存関係について説明します。 そして、完成したアプリを作成するために独立して構築することができる2つのネイティブアプリ(iOS用とAndroid用の1つ)が含まれています。 Native Templateは、Native Mobile Builderと連携して動作します。 Native Mobile Builder の機能の詳細については、 [Native Mobile Builder リリースノート](/releasenotes/mobile/mendix-native-mobile-builder) を参照してください。

テンプレートには、すべてをまとめるためのツールも含まれています。 具体的には、Native Template は React Native と Mendix の自動リンク機能を使用して、ネイティブの依存関係をプラットフォーム固有のアプリケーションにリンクします。 およびNative Mobileツールキットを使用して、バージョン番号、アプリ名、スプラッシュスクリーンなどのプラットフォーム固有のアプリケーションを構成します。

さらに、ネイティブテンプレートはカスタム開発者アプリを作成するのに役立ちます。 これらはMake It Nativeアプリのように機能しますが、アプリ固有のニーズに合わせて調整されたアプリです。 カスタム ネイティブ ウィジェットのような特注機能を使用するアプリケーションを構築したい場合は、 [カスタム 開発者アプリケーションを作成する方法](/howto/mobile/how-to-devapps) を参照してください。

## 2つの場所

ネイティブテンプレートは [GitHub](https://github.com/mendix/native-template) でホストされており、公開されています。

## 3 Versioning

バージョン管理に関するこの重要な情報に注意してください:

* ネイティブテンプレートは [セマンティックバージョン管理](https://semver.org/)を使用してバージョン管理されています
* ネイティブテンプレートバージョンは、ビルド中のアプリのMendix Studio Proバージョンと密接に関連しています。
* 一致しないバージョンを使用すると、予期しない動作になります

使用すべきネイティブテンプレートのバージョンを特定するには、以下の手順を行ってください。

1. どのバージョンの Studio Pro を使用しているか、例えば *9.0.0* に注意してください。
1. [ネイティブテンプレートmendix_version.json ファイル](https://github.com/mendix/native-template/blob/master/mendix_version.json) に移動します。

キーはMendix Studio Proバージョンを表します。 `min` と `max` の値は、サポートされているネイティブテンプレートの最小および最大のバージョンです。

{{% image_container width="200" %}}![Mendix Versions](attachments/native-template/mendix-version.png){{% /image_container %}}

上記の例のように、Mendix Studio Pro 8.9の場合のように。 4.0.0から最新のバージョンまで、任意のネイティブテンプレートを選択できます。 理想的には、サポートされている最新バージョンを選択する必要があります。

## 依存関係の自動リンク4

React Native モジュールは npm パッケージで、React Native モジュールをアプリケーションでコンパイルできるように、プラットフォーム固有のアプリケーションにリンクする必要があります。

Native Template は [React Nativeの CLI 自動リンク機能](https://github.com/react-native-community/cli/blob/master/docs/autolinking) を完全にサポートしています。 デフォルトで自動リンク可能なライブラリは、プラットフォーム固有のアプリに正しくリンクされます。

完全に自動リンク可能ではないライブラリ(通常は特別な初期化を必要とするライブラリ)については、デフォルトの自動リンク機能を拡張しました。 このプロセスは公に知られている能力に限定されています。 APIが公開されると、ドキュメントを拡張します。

## 5 Native Mobile Toolkit

Native Mobile Toolkit は Mendix で開発された npm モジュールで、プラットフォーム固有のアプリの設定要件を容易にします。 バージョン管理、パッケージ ID、スプラッシュ画面などのアプリ機能をプラットフォームに依存しない方法で定義できます。

構成は JSON で記述されます。 設定ファイルは増分番号を使用してバージョン化されます。 改ざんの変更が導入されると、バージョンはインクリメントされます。

Native Mobile Toolkit には、古い設定バージョンから新しいバージョンへの変換を可能にするコンバージョンロジックが含まれています。 この変換 は、カスタム実装と競合しないようにメモリ内で行われます。 変換された設定は、さらにデバッグするために端末のコンソール に出力されます。

### 5.1 モバイルツールキットの構成構造

アプリ固有の情報はトップレベルの **config** ファイルで定義されています。 設定オプションを導出する最善の方法は、最初にMendix Native Mobile Builderを使用してアプリを構成し、設定キーに注意することです。

**<details><summary>To see the supported properties as of config version 2, click here.</summary>** These are the supported properties as of config version 2:

```
interface NativeTemplateConfig {
    configVersion: 2;
    appName: string;
    appIdentifier: string;
    appVersion: string;
    bundleName: BundleName;
    buildNumber: number;
    deviceTarget: DeviceTarget;
    capabilities: Capabilities;
    orientation: Orientation;
    permissions: Permission[];
    runtimeUrl: string;
}

interface Capabilities {
    appCenterOTA: Capability;
    crashlytics: Capability;
    deepLink: DeepLinkCapability;
    firebaseAndroid: Capability;
    firebaseIos: Capability;
    localNotifications: Capability;
    maps: MapsCapability;
    mapsIos: MapsIosCapability;
    pushNotifications: Capability;
}

interface Capability {
    enabled: boolean;
}

interface IOSPermission extends Permission {
    purpose: string;
}

interface Permission {
    name: string;
    title: string;
    platform: OS;
    required: boolean;
}

interface DeviceTarget {
    phone: boolean;
    tablet: boolean;
}

export interface Orientation {
    portrait: boolean;
    landscape: boolean;
}
```
</details>

**<details><summary>設定されたアプリの例を見るには、ここをクリックしてください。</summary>** これは設定されたアプリの例です。

```
{
    "configVersion": 2,
    "appIdentifier": "com.mendix.mobile",
    "appName": "Mendix App",
    "appVersion": "1.0.0",
    "buildNumber": 1,
    "runtimeUrl": "http://localhost:8080"
    "bundleName": {
        "main": "MendixApp",
        "dev": "MendixAppDev"
    },
    "deviceTarget": {
        "phone": true,
        "tablet": false
    },
    "orientation": {
        "portrait": true,
        "landscape": true
    },
    "permissions": [
        {
            "title": "Internet",
            "name": "android.permission.INTERNET",
            "platform": "android",
            "required": true
        },
        {
            "title": "Location - Always Usage",
            "name": "NSLocationAlwaysUsageDescription",
            "purpose": "To use that feature, the app needs access to your location.",
            "platform": "ios",
            "required": true
        }
    ],
    "capabilities": {
        "deepLink": {
            "value": "",
            "enabled": false
        },
        "maps": {
            "value": "a12dkdadhqow12123123radqwe",
            "enabled": true
        },
        "mapsIos": {
            "enabled": false
        },
        "pushNotifications": {
            "enabled": false
        },
        "crashlytics": {
            "enabled": false
        },
        "firebaseAndroid": {
            "enabled": false
        },
        "firebaseIos": {
            "enabled": false
        },
        "localNotifications": {
            "enabled": false
        },
        "appCenterOTA": {
            "enabled": false
        }
    }
}

```
</details>


### 5.2 アセット

Mobile Toolkit では、スプラッシュ画面とアプリのアイコンの設定がサポートされています。 アセット名が **アセット**というフォルダにあるネイティブテンプレートのルートからの相対的なアセットが保存されることが予想されます。

```
- assets
    - icons
    - splashScreens
```

#### 5.2.1 iOS アイコン

アイコンの設定は、 *assets/icons/ios.json* の **** 形式の **** ファイルで定義する必要があります。

filename で定義された実際のアセットファイルは **config** ファイルの横にあることが期待されます。

このバージョンは必須であり、後方互換性のために使用されます。 以下に、 **バージョン 1** を使用した設定を示します。

```
interface IOSIconsConfig {
    "images": Array<{
            "size": string",
            "idiom": "ipad" | "iphone" | "ios-marketing",
            "scale": "1x" | "2x"| "3x",
            "type": "icon",
            "filename": string
        }>,
    "version": 1
}
```

**<details><summary>アプリの設定に必要なすべてのキーの例を見るには、ここをクリックしてください。</summary>**

これはアプリの設定に必要なすべてのキーの例です。

```
{
    "images": [
        {
            "size": "20x20",
            "idiom": "ipad",
            "scale": "1x",
            "type": "icon",
            "filename": "notification@1x.png"
        },
        {
            "size": "20x20",
            "idiom": "ipad",
            "scale": "2x",
            "type": "icon",
            "filename": "notification@2x.png"
        },
        {
            "size": "20x20",
            "idiom": "iphone",
            "scale": "2x",
            "type": "icon",
            "filename": "notification@2x.png"
        },
        {
            "size": "20x20",
            "idiom": "iphone",
            "scale": "3x",
            "type": "icon",
            "filename": "notification@3x.png"
        },
        {
            "size": "29x29",
            "idiom": "ipad",
            "scale": "1x",
            "type": "icon",
            "filename": "settings@1x.png"
        },
        {
            "size": "29x29",
            "idiom": "ipad",
            "scale": "2x",
            "type": "icon",
            "filename": "settings@2x.png"
        },
        {
            "size": "29x29",
            "idiom": "iphone",
            "scale": "2x",
            "type": "icon",
            "filename": "settings@2x.png"
        },
        {
            "size": "29x29",
            "idiom": "iphone",
            "scale": "3x",
            "type": "icon",
            "filename": "settings@3x.png"
        },
        {
            "size": "40x40",
            "idiom": "ipad",
            "scale": "1x",
            "type": "icon",
            "filename": "spotlight@1x.png"
        },
        {
            "size": "40x40",
            "idiom": "ipad",
            "scale": "2x",
            "type": "icon",
            "filename": "spotlight@2x.png"
        },
        {
            "size": "40x40",
            "idiom": "iphone",
            "scale": "2x",
            "type": "icon",
            "filename": "spotlight@2x.png"
        },
        {
            "size": "40x40",
            "idiom": "iphone",
            "scale": "3x",
            "type": "icon",
            "filename": "spotlight@3x.png"
        },
        {
            "size": "60x60",
            "idiom": "iphone",
            "scale": "2x",
            "type": "icon",
            "filename": "app@2x.png"
        },
        {
            "size": "60x60",
            "idiom": "iphone",
            "scale": "3x",
            "type": "icon",
            "filename": "app@3x.png"
        },
        {
            "size": "76x76",
            "idiom": "ipad",
            "scale": "1x",
            "type": "icon",
            "filename": "ipadapp@1x.png"
        },
        {
            "size": "76x76",
            "idiom": "ipad",
            "scale": "2x",
            "type": "icon",
            "filename": "ipadapp@2x.png"
        },
        {
            "size": "83.5x83.5",
            "idiom": "ipad",
            "scale": "2x",
            "type": "icon",
            "filename": "ipadproapp@2x.png"
        },
        {
            "size": "1024x1024",
            "idiom": "ios-marketing",
            "scale": "1x",
            "type": "icon",
            "filename": "appstore@1x.png"
        }
    ],
    "version": 1
}
```
</details>

#### 5.2.2 Android アイコン

アイコンの設定は、 **assets/icons/android.json** のバージョンの JSON- *config* ファイルで定義する必要があります。

filename で定義された実際のアセットファイルは **config** ファイルの横にあることが期待されます。

このバージョンは必須であり、後方互換性のために使用されます。 今のところ設定はバージョン1にあります:

```
interface AndroidIconsConfig {
    "images": Array<{
            "directory": "mipmap-mdpi" | "mipmap-hdpi" | "mipmap-xhdpi" | "mipmap-xxhdpi"
            "filename": "ic_launcher.png" | "ic_launcher_round.png"
            "title": string
        }>,
    "version": 1
}
```

**<details><summary>アプリの設定に必要なすべてのキーの例を見るには、ここをクリックしてください。</summary>**

これはアプリの設定に必要なすべてのキーの例です。

```
{
    "images": [
        {
            "filename": "ic_launcher.png",
            "directory": "mipmap-mdpi",
            "title": "mipmap-mdpi-ic_launcher.png"
        },
        {
            "filename": "ic_launcher.png",
            "directory": "mipmap-hdpi",
            "title": "mipmap-hdpi-ic_launcher.png"
        },
        {
            "filename": "ic_launcher.png",
            "directory": "mipmap-xhdpi",
            "title": "mipmap-xhdpi-ic_launcher.png"
        },
        {
            "filename": "ic_launcher.png",
            "directory": "mipmap-xxhdpi",
            "title": "mipmap-xxhdpi-ic_launcher.png"
        },
        {
            "filename": "ic_launcher.png",
            "directory": "mipmap-xxxhdpi",
            "title": "mipmap-xxxhdpi-ic_launcher.png"
        },
        {
            "filename": "ic_launcher_round.png",
            "directory": "mipmap-mdpi",
            "title": "mipmap-mdpi-ic_launcher_round.png"
        },
        {
            "filename": "ic_launcher_round.png",
            "directory": "mipmap-hdpi",
            "title": "mipmap-hdpi-ic_launcher_round.png"
        },
        {
            "filename": "ic_launcher_round.png",
            "directory": "mipmap-xhdpi",
            "title": "mipmap-xhdpi-ic_launcher_round.png"
        },
        {
            "filename": "ic_launcher_round.png",
            "directory": "mipmap-xxhdpi",
            "title": "mipmap-xxhdpi-ic_launcher_round.png"
        },
        {
            "filename": "ic_launcher_round.png",
            "directory": "mipmap-xxxhdpi",
            "title": "mipmap-xxxhdpi-ic_launcher_round.png"
        }
    ],
    "version": 1
}
```
</details>

#### 5.2.3 iOS スプラッシュ画面

The splash screen configuration needs to be defined in a versioned JSON-formatted **config** file under *assets/splashScreens/ios.json*.

filename で定義された実際のアセットファイルは **config** ファイルの横にあることが期待されます。

このバージョンは必須であり、後方互換性のために使用されます。 今のところ設定はバージョン1にあります:

```
interface AndroidSplashScreensConfig {
      "images": Array<{
              "size": "640x960" | "375x667" | "414x736",
              "idiom": "universal",
              "scale": "1x" | "2x" | "3x",
              "type": "splashScreen",
              "filename": string
          }>,
      "version": 1
}
```

必要なスプラッシュ画面がすべて定義されたファイルの例を次に示します:

```
{
    "images": [
        {
            "size": "640x960",
            "idiom": "universal",
            "scale": "1x",
            "type": "splashScreen",
            "filename": "splash@1x.png"
        },
        {
            "size": "375x667",
            "idiom": "universal",
            "scale": "2x",
            "type": "splashScreen",
            "filename": "splash@2x.png"
        },
        {
            "size": "414x736",
            "idiom": "universal",
            "scale": "3x",
            "type": "splashScreen",
            "filename": "splash@3x.png"
        }
    ],
    "version": 1
}
```

#### 5.2.4 Android Splash Screen

スプラッシュ画面の設定は、バージョン管理された JSON- **config** ファイル *assets/splashScreens/android.json* で定義する必要があります。

filename で定義された実際のアセットファイルは **config** ファイルの横にあることが期待されます。

このバージョンは必須であり、後方互換性のために使用されます。 今のところ設定はバージョン1にあります:

```
interface AndroidSplashScreensConfig{
  "images": Array<{
          "filename": "splash.png";
          "directory": "drawable-hdpi" | "drawable-xhdpi" | "drawable-xxhdpi",
          "title": string;
      }>,
  "version": 1
}
```

必要なスプラッシュ画面がすべて定義されたファイルの例を次に示します:

```
{
    "images": [
        {
            "filename": "splash.png",
            "directory": "drawable-hdpi",
            "title": "drawable-hdpi-splash.png"
        },
        {
            "filename": "splash.png",
            "directory": "drawable-xhdpi",
            "title": "drawable-xhdpi-splash.png"
        },
        {
            "filename": "splash.png",
            "directory": "drawable-xxhdpi",
            "title": "drawable-xxhdpi-splash.png"
        }
    ],
    "version": 1
}
```

### 5.3 Firebase の設定

Firebase の使用には特別な考慮が必要です。 When enabling the Firebase capabilities via the Native Mobile Toolkit **config** file, the toolkit will look in the **assets/firebase** folder for the appropriate configuration files.

ファイルは名前で検索されます。 プラットフォームごとの期待される名前は次のとおりです。

| プラットフォーム | 期待される名前                  |
| -------- | ------------------------ |
| Android  | google-services.json     |
| iOS      | GoogleService-Info.plist |

Native Mobile Toolkit は提供された設定ファイルの妥当性を検証しません。 アプリを設定するときにのみ、正しい 場所に移動します。

### 5.4 ネイティブモバイルツールキットの実行

Native Mobile Toolkit は、Native Templateに含まれるNodeモジュールです。 そのため、ネイティブテンプレートのルートディレクトリに `install` を実行することで、最初にインストールする必要があります。 ローカルで建造する場合 Native Mobile Toolkitの新しいバージョンがリリースされた場合、常に最新バージョンで動作していることを確認するには、 `npm install` を実行する必要があります。

{{% alert type="info" %}}
npm スクリプトは、Native Mobile Toolkit 設定ファイルがアプリケーションのルートにあり、 **config.json** と命名されることを期待します。 これは、Mendix Native Mobile Builderを使用してローカルまたはリモートアプリケーションを構成する場合に常に当てはまります。
{{% /alert %}}

**package.json**で定義されている run script を使用してツールキットを実行するには、 `npm run configure` を実行します。

#### 5.4.1 カスタム設定パスの指定

root ディレクトリからの相対的な設定ファイルは、toolkit では必要ありませんが、便宜上行われます。 異なる設定ファイルパスを指定するには、次のコマンドを使用してツールキットを実行できます。

```
native-mobile-toolkit configure --config-path='./<name of the configuration>.json' --verbose
```

## 6バンドル情報

Mendix ネイティブアプリは React Native に基づいています。 Mendix Native Mobile Builderを使用してMendixアプリを構築する場合、アプリは最初にJavascriptコードと静的資産にコンパイルされます。 React NativeのMetro Bundlerを使用すると、クライアントコードとアセットがプラットフォーム固有のReact Native Bundlesにコンパイルされます。 最終的にアプリをコンパイルする前に、最終的にNative Templateの正しい場所に移動されます。

このプロセス全体は、Mendix Studio Proのすべてのインストールに含まれるMXBuildというツールを使用して統一されています。 詳細については、 [MxBuild リファレンスガイド](mxbuild) を参照してください。

### 6.1 MxBuild でネイティブアプリをビルドする

何らかの理由でMendix Native Mobile Builderを使用してアプリを構成およびビルドできない場合。 例えば、ディスプレイがないCI環境で動作する場合など。 正しいMendix Studio Proバージョンをビルドしてから、MXBuildを手動で実行する必要があります。

そうするには:

1. 必要なStudio Proインストールを探します。
1. 実行可能ファイル **mxbuild.exe** へのパスを探し、それをメモします。
1.  コマンドラインを開き、次のコマンドを実行します。

    ```
    <path-to-mxbuild.exe> --java-home=DIRECTORY -java-exe-path=FILENAME --target=deploy --native-packager <path-to-the-app-mpr>
    ```

このコマンドは以下の操作を行います:

* 通常どおり、Webおよびネイティブアプリをデプロイメントフォルダにエクスポートします。
* React Native metro bundler (Note フラグ `--native-packager`) を実行して、 `/deployment/native/bundle` で各プラットフォームの RN バンドルとアセットを作成します。

バンドルフォルダ構造は以下のようになります:

```
- android
    - res
        - drawable-mdpi
        - drawable-hdpi
        - drawable-xhdpi
        - drawable-xxhdpi
        - drawable-xxxhdpi
        - raw
    - assets
        - index.android.bundle
- iOS 
    - assets
        - List of all images namespaced
        - index.ios.bundle
```

### 6.2 バンドルを正しい場所にコピーする

作成されたバンドルをビルドするには、ネイティブテンプレートの適切な場所にコピーする必要があります。

* Androidの場合、 `バンドル/アンドロイド` の内容は、アセットとバンドルをコピーする必要がある正確なフォルダを反映しています。
* iOSの場合、 `バンドル/iOS` フォルダの内容を `<native-template>/ios/Bundle` ディレクトリにコピーする必要があります。

## 7 アプリのネイティブ依存関係の提供

Mendix Studio Pro 9 では、プラグイン可能なウィジェットと Javascript アクション用のネイティブ依存解像度が導入されました。 詳細については、 [ネイティブ依存性の宣言 ](/apidocs-mxsdk/apidocs/pluggable-widgets-native-dependencies) を参照してください。 Studio Pro 9 Mendix Studio Pro以前は、コアの依存関係が一連削除されるようになりました。

開発に伴い、Mendix Studio Pro 9 互換モジュール、ウィジェット、アクションをアプリに追加できます。 これは、ネイティブアプリを構築する前にアプリのネイティブテンプレートにも宣言する必要がある依存関係 が追加されます。

アプリの初期設定には、この依存関係管理が必要ですので、Mendix Native Mobile Builderを使用してアプリを構成することをお勧めします。 Mendix Native Mobileビルダーは、必要な依存関係を引き出し、アプリのNative Templateとリンクすることができます。

## 8 継続的インテグレーションテストガイドライン

いくつかの高度なケースでは、継続的インテグレーション(CI)テストのセットアップを検討することができます。 これは、複数の環境があり、プロダクションにプッシュする前に受け入れの毎夜の変更をテストする ことを好む場合に便利です。

ネイティブの依存関係が安定するまで、Mendix Native Mobile Builderを使用してアプリケーションを開発することをお勧めします。 CIを初期段階に置くことは不満につながり、フラックスの依存関係は予期せぬクラッシュにつながります。

ビルド用のネイティブテンプレートを正常に設定するには、CI 環境で以下を行う必要があります。

* SVN から最新の Mendix アプリをご覧ください
* アプリのネイティブテンプレート（アプリの設定時に使用されるテンプレート）
* `mxbuild` を実行する
* 構成を設定し、必要に応じてアセットを移動します(これは単純なシェルスクリプトまたは他のソリューションで行うことができます。 そして実務者の選択です)
* `npm i` と `npm run configure` を実行して、ビルドの前に Mendix Mobile Toolkit を使用してアプリを構成します。

アプリを構築する方法は、実装者の選択肢です。 Mendixネイティブアプリビルダーは便宜上App Centerを使用しています。 この目的のために使用できる前提またはサービスとして、他にも複数の ソリューションがあります。 私たちは互いに支持しません。

## 9 続きを読む

* [オフラインの最初の参照ガイド](offline-first)