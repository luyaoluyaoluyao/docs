---
title: "プログレッシブウェブアプリ"
category: "モバイル"
menu_order: 2
tags:
  - "モバイル"
  - "プログレッシブウェブアプリ"
  - "PWA"
  - "studio pro"
---

## 1つの紹介

プログレッシブウェブアプリ(PWA)は、従来のウェブアプリの進化です。 全体として、PWA はネイティブのモバイルアプリのように振る舞う傾向があり、その人気は高まっています。 ハイブリッドおよびネイティブモバイルアプリと比較してPWAの違いと考えられる利点の1つは、PWAはアプリストアを介して配布する必要はなく、ブラウザ経由で直接アクセスできることです。

プログレッシブウェブアプリには主に3つの特徴があります:

* **インストール可能 —** PWAでは、ユーザーのホーム画面にアプリを追加し、フルスクリーンアプリを起動できます。 これにより、PWA はより完全なネイティブアプリを感じさせることができます。
* **信頼性の高い —** サービスワーカーを使用すると、PWA はオフラインまたは部分的にオフラインで作業できます。 Mendix PWA は部分的にオフラインで動作します (スタイリング、ページ、画像などのリソースはキャッシュされます)、または完全にオフラインで動作します (ハイブリッドオフラインやネイティブモバイルアプリなど)。
* **機能 —** PWA はカメラやロケーションなどの複数のデバイス機能を活用でき、Web プッシュ通知のサポートを提供できます。 機能のサポートは、使用されるブラウザによって異なります。

## 2 PWA機能の有効化

PWAは基本的に追加機能を備えたWebアプリなので、Mendixはこれらの機能をWebナビゲーションプロファイルの一部として提供します。 必要なものに基づいて、完全にオフライン対応した PWA を作成できます。 またはインターネット接続を必要としながらもPWA機能を使用するWebアプリケーション。

完全なオフラインファーストPWAを作成するには、次のプロファイルのいずれかを選択して追加します(必要なフォームファクタに応じて): レスポンシブWebオフライン。 電話ウェブオフライン、またはタブレットウェブオフライン。 オフラインファーストアプリの詳細については、 [オフラインファーストリファレンスガイド](/refguide/offline-first) を参照してください。

{{% alert type="info" %}}
オフラインで最初のプログレッシブWebアプリには、完全にオフラインで動作できるようにするための制限があります。 詳しい情報については、 [オフライン-ファーストリファレンスガイド ](offline-first#limitations) の *アプリがオフラインであることを確認する* セクションを参照してください。
{{% /alert %}}

ナビゲーション プロファイル内では、次の PWA 機能を設定できます。

{{% image_container width="350" %}}![PWA settings](attachments/progressive-web-app/settings.png){{% /image_container %}}

PWA 機能を完全にテストできるようにするには、アプリケーションをクラウドにデプロイする必要があります。 これは、Service Worker が HTTPS 経由でクラウドでのみ有効になっているためです。

### 2.1 プログレッシブウェブアプリとして公開

チェックしてクラウドにデプロイすると、アプリケーションはPWAの基礎となる [サービスワーカー](https://developers.google.com/web/fundamentals/primers/service-workers) を登録します。 オフラインナビゲーションプロファイルでは、このオプションは常に有効です。 オンラインナビゲーションプロファイルでは、このオプションを有効にすると、デバイスに接続がない場合に、エンドユーザーにカスタムページが表示されます。 必要に応じて、このページは *offline.html* ページをテーマフォルダに追加することでカスタマイズできます(例えば、 *theme/offline.html*)。 このページはネットワーク経由で他のリソースをロードしてはいけないことに注意してください。

### 2.2 「ホーム画面に追加」プロンプトを許可する

**Add to Home Screen** オプションが選択された場合。 エンドユーザーは、デバイスのホーム画面やデスクトップにアプリを追加するように積極的に求められる場合があります。 動作はブラウザごとに、時間の経過とともに異なる場合があります。 選択されていない場合でも、アプリは常にホーム画面に追加することができますが、ユーザーはアクティブに求められません。

### 2.3 静的リソース

このオプションを有効にすると、バックグラウンドでページ、画像、ウィジェットなどの静的リソースが事前にロードされます。 これはパフォーマンスを助けることができる。 このプリロードは、ユーザーが初めてアプリを開くとき、またはモデルが変更されたときに行われます。 これにより、新しいページに移動するときにアプリがより速く感じられます。 しかし、最初はより多くの帯域幅とデバイスストレージを消費するため、コストがかかります。

オフラインプロファイルでは、この機能は自動的に有効になり、アプリが完全にオフラインで機能するようになります。

ナビゲーションプロファイルに到達可能なすべてのページと画像はブラウザによって読み込まれることに注意してください。 この構成は、使用事例と要件に応じて、セキュリティの観点から望ましくない場合があります。

## 3 PWAのプレビューまたはテスト

PWA は、お使いのマシンまたはデバイスのブラウザで直接見ることができます。 **ビュー** メニューから、PWAプロファイルを直接ブラウザで開くことができます。

![メニューを表示](attachments/progressive-web-app/view-menu.png)

お使いのデバイスの **ビュー** オプションを使用して、PWAプロファイルをデバイスで開くこともできます。

{{% image_container width="350" %}}![View menu](attachments/progressive-web-app/view-dialog.png){{% /image_container %}}

Parallels 付きの Mac で実行している場合は、注意してください。 ポート8080(またはアプリに設定されているいずれかのポート)が転送され、仮想マシンのIPの代わりにMacのIPを使用することを確認してください。 Mendix と Parallels の詳細については、 [Parallels の設定方法](/howto/mobile/using-mendix-studio-pro-on-a-mac) を参照してください。

{{% alert type="info" %}}
オフライン最初の PWA をローカルでプレビューまたはテストする場合、アプリをロードするには常にインターネット接続が必要です。 初期読み込み後、アプリは完全にオフラインで動作しますが、接続なしで再読み込みすることはできません。 アプリがクラウドにデプロイされると、エンドユーザーは最初にアクセスした後、接続なしでいつでもアプリをロードできます。
{{% /alert %}}

### 3.1 PWA灯台チェック

PWAの能力を確認するには、 [灯台](https://developers.google.com/web/tools/lighthouse)を使用できます。 Lighthouseは、Webページの品質を向上させるためのオープンソースの自動化ツールです。 アプリがプログレッシブウェブアプリの要件を満たしているかどうかを確認し、ウェブアプリを改善するための提案を提供することができます。

## 4 PWAを配布または共有

PWA はウェブアプリなので、PWA の URL を共有することで簡単に共有できます。

デバイスまたはブラウザでアプリを開くと、Mendixはユーザーエージェントとブラウザの機能に基づいてナビゲーションプロファイルを自動的に決定します。 ブラウザーがオフライン機能をサポートしていない場合は、代わりにオンラインプロフィールが使用されます。

Google ChromeとMicrosoft Edge(Chromiumエディション)は、オフラインファーストアプリの実行を完全にサポートしています。

### 4.1 プロファイル選択の例

たとえば、Phone Web Offline プロファイルが構成されていて、ブラウザーでアプリが開かれている場合、次のシナリオが発生する可能性があります。

| デバイス & ブラウザー          | 結果                                                                                                           |
| --------------------- | ------------------------------------------------------------------------------------------------------------ |
| デスクトップ ブラウザー          | レスポンシブWebプロファイルが読み込まれました                                                                                     |
| Android - Chromeブラウザー | 電話ウェブオフラインプロファイルが読み込まれました                                                                                    |
| iOS - 任意のブラウザ         | Phone Web プロファイルがある場合、これは読み込まれます。そうでなければ、Responsive Web プロファイルが読み込まれます。 これは、オフラインPWAがiOSで(まだ)サポートされていないためです。 |

Next to that, it is possible to force a profile by providing the profile name in the URL as a query parameter: for example `http://localhost:8080/?profile=PhoneOffline`. プロファイルの値は次のとおりです。

| プロファイル名          | URL 内の値     |
| ---------------- | ----------- |
| レスポンシブウェブ        | レスポンシブ      |
| レスポンシブWebオフライン   | レスポンシブオフライン |
| 電話のウェブ           | 電話番号        |
| オフライン電話          | オフライン電話     |
| タブレットウェブ         | タブレット       |
| タブレットの web オフライン | タブレットオフライン  |

クラウド展開に特定のプロファイルを強制する場合は、まずブラウザキャッシュをクリアする必要があります。

## 5つの詳細設定

詳細設定については、以下のセクションを参照してください。

### 5.1 Web App Manifest

PWA は、アプリケーションに関する情報をブラウザに提供する Web アプリマニフェストを使用します。 Mendixはモデルに基づいて自動的に生成されます。 It can be customized for specific needs by changing the `manifest-overrides.webmanifest` *.json* file in the **theme** folder. `background_color` と `theme_color` プロパティは、しばしばカスタマイズに役立ちます。

```json
{
    "background_color": "white",
    "theme_color": "#0CABF9"
}
```

For more information on the available properties in the web app manifest, read this [short introduction](https://web.dev/add-manifest/) or view [the full reference at MDN](https://developer.mozilla.org/en-US/docs/Web/Manifest).

### 5.2 セッション

オフライン最初の PWA は、長寿命のセッションを使用します。これにより、ユーザーは自分のアプリが閉じられた後も長期間ログインできます。 デフォルトでは、ユーザーは7日間操作が行われなかった後にログアウトされます。 これは、 *LongLivedSessionTimeout* ランタイム設定を使用してカスタマイズできます。

セッションの詳細とタイムアウトをカスタマイズする方法 [Mendix Runtime Reference Guide](tricky-custom-runtime-settings#session-duration) の *トリッキーカスタム設定* セクションを参照してください。

## 6 デバイスの機能へのアクセス

ブラウザは、PWA で活用できる API を通じてデバイス機能にアクセスできます。 これらのデバイス機能は、利用可能なウィジェットとナノフローアクションで使用できます。 [JavaScript アクション](/refguide/javascript-actions) または [Pluggable Widgets](/howto/extensibility/pluggable-widgets) を使用してプラットフォームを拡張することで、追加のデバイス機能を活用することもできます。

この表には、最も使用されているデバイスの機能と API のほか、一般的なブラウザとの互換性も記載されています。

| 機能                                                                                        | Chrome/Edge                                                           | Firefox                                                               | Safari                                                                |
| ----------------------------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| [カメラ](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices)                      | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) |
| [支払い](https://developer.mozilla.org/en-US/docs/Web/API/Payment_Request_API)               | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) | ![互換性がありません](attachments/progressive-web-app/icons/cross-mark.svg)    | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) |
| [資格情報 (バイオメトリクス)](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/credentials) | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) | ![互換性がありません](attachments/progressive-web-app/icons/cross-mark.svg)    |
| [プッシュ通知](https://developer.mozilla.org/en-US/docs/Web/API/Push_API)                       | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) | ![互換性がありません](attachments/progressive-web-app/icons/cross-mark.svg)    |
| [アクセス許可](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/permissions)          | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![互換性がありません](attachments/progressive-web-app/icons/cross-mark.svg)    |
| [フォアグラウンド検出](https://developer.mozilla.org/en-US/docs/Web/API/Page_Visibility_API)        | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       |
| [Bluetooth](https://developer.mozilla.org/en-US/docs/Web/API/Bluetooth)                   | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) | ![互換性がありません](attachments/progressive-web-app/icons/cross-mark.svg)    | ![互換性がありません](attachments/progressive-web-app/icons/cross-mark.svg)    |
| [ファイルアクセス](https://developer.mozilla.org/en-US/docs/Web/API/File)                         | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       |
| [ジオロケーション](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/geolocation)        | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) |
| [バッテリー](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/getBattery)            | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![互換性がありません](attachments/progressive-web-app/icons/cross-mark.svg)    | ![互換性がありません](attachments/progressive-web-app/icons/cross-mark.svg)    |
| [共有](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/share)                    | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) | ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg) |
| [振動](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/vibrate)                  | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![互換性がありません](attachments/progressive-web-app/icons/cross-mark.svg)    |
| [メモリ](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/deviceMemory)            | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![互換性がありません](attachments/progressive-web-app/icons/cross-mark.svg)    | ![互換性がありません](attachments/progressive-web-app/icons/cross-mark.svg)    |
| [接続](https://developer.mozilla.org/en-US/docs/Web/API/NetworkInformation)                 | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)       | ![互換性がありません](attachments/progressive-web-app/icons/cross-mark.svg)    |

**凡例** — 上記の記号は以下の定義に対応しています。

*  完全な互換性:

    ![完全な互換性](attachments/progressive-web-app/icons/check-mark.svg)

*  HTTPS プロトコルを使用している場合のみ互換性があります。

    ![HTTPSを使用する際の互換性](attachments/progressive-web-app/icons/warning.svg)

*  互換性がありません:

    ![互換性がありません](attachments/progressive-web-app/icons/cross-mark.svg)

特定のデバイス機能のブラウザーサポートの詳細については、サードパーティのウェブサイト [使用できる](https://caniuse.com/) を参照してください。

{{% alert type="info" %}}
HTTPS プロトコルを必要とする機能をテストするには、 [ngrok](https://ngrok.com/) を使用して、localhost内の機能を有効にします。
{{% /alert %}}

## 7 PWAまたはネイティブモバイルアプリ間で決定する

MendixはネイティブモバイルアプリとPWAの両方を構築するためのオプションを提供します。 アプリの要件や制約に応じて、どちらか一方または他方が適合することがあります。 1つのアプリでネイティブモバイルとPWAの両方のプロファイルを持つこともできます。 お互いに並んで重なり合うことができます

{{% alert type="info" %}}
重要な制限: iOS 上の PWA のプッシュ通知は、Apple ではサポートされていません。

現在、完全にオフラインで初めてiOS用PWAを作成することはできません。サポートは2022年のロードマップの一部です。
{{% /alert %}}

次の図を使用して、PWA、ネイティブ モバイル アプリケーション、または両方を作成するかどうかを決定します。

{{% image_container width="350" %}}![Native app or PWA](attachments/progressive-web-app/native-or-pwa.png){{% /image_container %}}

## 8 続きを読む

* [ネイティブモバイルリファレンスガイド](native-Mobile)
* [オフライン-ファーストリファレンスガイド](offline-first)
* [ナビゲーションリファレンスガイド](navigation)
