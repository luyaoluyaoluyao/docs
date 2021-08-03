---
title: "ハイブリッドモバイルアプリの開発"
category: "モバイル開発"
aliases:
  - /ja/refguide7/Developing+Hybrid+Mobile+Apps.html
---

## 1つの紹介

MendixアプリはモバイルWebブラウザで簡単に表示できます。 しかし、モバイルデバイスの一部の機能はHTMLやJavaScriptではアクセスできません。 また、Apple App Store、Google Playでアプリを公開したい場合もあります。 またはMicrosoft Phone Storeでは、アプリをネイティブシェルでラップする必要があります。 これを行うには [PhoneGap](http://phonegap.com/) を使用します。 PhoneGap は、Web アプリケーションの周りにネイティブラッパーを作成し、JavaScript API を介してネイティブ関数へのアクセスを提供します。

これらのアプリは、ウェブとネイティブアプリのハイブリッドであるため、「ハイブリッド」アプリとも呼ばれます。 Mendixは、さまざまな方法でハイブリッドモバイルアプリの作成を容易にします。

## 2 Mendix モバイルアプリ

ハイブリッドモバイルアプリの開発 ツールバーまたは **** **ハイブリッドタブレットアプリオンラインを表示** または **** メニューを使用して、ブラウザで素早くプレビューできます。

ただし、ハイブリッドページでネイティブウィジェットを使用する場合、これらのウィジェットの一部がブラウザで動作しない場合があります。 これらのウィジェットの中には、通常のブラウザで動作している場合に代替の実装を提供するものがあります。他のウィジェットはまったく動作しません。 PhoneGap ラッパー内でアプリがどのように見えるかを確認するには、Mendix Mobile アプリを使用できます。 デスクトップ モデラーで ツールバーの **メニュー App の** ビューまたは **** メニューから、ハイブリッド・モバイル・アプリのダイアログ・ボックスにアクセスできます。 それはそのアプリでスキャンすることができるQRコードを表示します。 これは、PhoneGap 互換環境でアプリケーションを読み込むための迅速な方法です。

![](attachments/Developing+Hybrid+Mobile+Apps/View_Hybrid_Mobile_App_Popup.png)

Mendix Mobile アプリのダウンロード方法については、 [Mendix Mobile App の取得](getting-the-mendix-app) を参照してください。

{{% alert type="warning" %}}

Mendix Mobileアプリを動作させるには、モバイルデバイスが開発マシンと同じネットワーク上にある必要があります。 この場合でも接続に失敗する場合は、Wi-Fiアクセスポイントでデバイス間の通信が許可されていることを確認してください。

{{% /alert %}}

## 3 続きを読む

* [モバイル](モバイル)
* [Mendix モバイルアプリの取得](getting-the-mendix-app)
* [ハイブリッドアプリのカスタマイズ](customizing-hybrid-mobile-apps)
* [ハイブリッドアプリのパッケージ](packaging-hybrid-mobile-apps)

