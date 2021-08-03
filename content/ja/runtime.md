---
title: "Mendix Runtime"
---

## 1つの紹介

Mendix Runtimeはモデラーで作成されたアプリケーションモデルを実行します。 Mendix Clientにページを提供し、マイクロフローを実行し、Webサービスを呼び出し、文書を生成し、データベースと通信し、その他多くを提供します。

## 2 ライセンス

本番モードでアプリケーションを実行するにはライセンスが必要です。 ライセンスがなければ、Mendix Runtimeは数時間後に動作を停止します。 ライセンスは、Mendixのアカウントマネージャーから取得できます。 その後、 [Microsoft WindowsでMendixライセンスを有効にする方法](/developerportal/deploy/activate-a-mendix-license-on-microsoft-windows)の手順に従ってライセンスを有効にすることができます。

## 3 API

Javaアクションを書くことで、ランタイムの機能を拡張できます。 詳細については、 [API ドキュメント](/apidocs-mxsdk/apidocs/#runtime) の *Runtime API* セクションを参照してください。

{{% alert type="info" %}}
公開された Web サービスの WSDL のような API ドキュメントへのリンクは、URL パス `/api-doc` で利用できます (例: `http://localhost:8080/api-doc/`)。
{{% /alert %}}

## このカテゴリ内の4つのメインドキュメント

* [Clustered Mendix Runtime](clustered-mendix-runtime)
* [カスタマイズ](カスタム設定)
* [データストレージ](データストレージ)
* [日付 & 時間の処理](datetime-handling-faq)
* [ログ](logging)
* [Mendix ランタイムの監視](monitoring-mendix-runtime)
* [オブジェクト & キャッシュ](objects-and-caching)
* [一時オブジェクト & ごみ収集中](transient-objects-garbage-collecting)
