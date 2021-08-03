---
title: "Desktop Modelerバージョン7からStudio Pro8に移動"
category: "一般情報"
menu_order: 20
description: "Desktop Modelerバージョン7からStudio Proバージョン8へのプロジェクトの更新に関する詳細を提供します プロジェクトと非推奨機能の変換に関するセクションを含む。"
tags:
  - "studio pro"
---

## 1つの紹介

Desktop Modelerバージョン7からStudio Proバージョン8にMendixアプリを変換する場合 お勧めの一連のステップがある これらは以下の [アプリの変換](#converting)に記載されています。

Mendix 8 の新機能については、 [Studio Pro 8 リリース ノート](/releasenotes/studio-pro/) を参照してください。

## 2 Mendix 7から8へのアップグレード

{{% alert type="warning" %}}
Mendixバージョン8の変更により、通常のStudioアップグレードメカニズムを使用して自動的にアップグレードすることはできません。
{{% /alert %}}

これは以下のことを意味する。

* Studioで構築された既存のアプリは現在のMendixバージョンに残り、StudioでMendixバージョン7.23の最新バージョンにアップグレードできます。

    {{% alert type="info" %}}アプリケーションが Mendix 8 Beta バージョンを使用してStudio Pro で作成された場合。 Mendix 8のリリースバージョンに自動的にアップグレードされます。
    {{% /alert %}}

*  これからStudioで作成したアプリは、最初からMendixバージョン8を使用することになります

既存のMendixバージョン7のStudioアプリをMendixバージョン8にアップグレードしたい開発者は、 [アプリのConverting Your App](#converting)の手順に従って、Studio Proでのみアップグレードできます。 以下です

### 2.1 Studio との共同開発

元のプロジェクトがMendixバージョン7.23だった場合。 または以下で、Mendix Studioを使用して開発者と協力して作業したい場合は、プロジェクトをMendixバージョン7にアップグレードする必要があります。 3.3 以上。 このアップグレードなしでは、変更を Studio と同期することはできません。

## 3 Mendix にアップグレードする前にアプリを変更する 8, Studio Pro

*Mendix 8にアップグレードする前に、* アプリに変更を加える必要があるかもしれません。

### 3.1 Java バージョン、非推奨 & 削除された API {#deprecated-apis}

Mendix 8 は Java 11 で動作し、Mendix 7 は Java 8 で動作します。 Java アクションが Java 11 と互換性があることを確認します。 公式の Java 8 から 11 の移行ガイドは、 [Oracle JDK 移行ガイド](https://docs.oracle.com/en/java/javase/11/migrate/index.html#JSMIG-GUID-7744EF96-5899-4FB2-B34E-86D49B2E89B6) の *JDK 移行ガイド* の format@@4 から後の JDK リリースへの移行 にあります。

非推奨のJavaアクションはMendix 7で修正する必要があります。

プロジェクトをJava IDEにインポートし(たとえば、クリップなど)、すべての廃止予定をレビューして解決することで、Javaアクションの廃止を修正します。

削除された API と非推奨の API の詳細は、 *Studio Pro 8 リリース ノート* の [Breaking Changes](/releasenotes/studio-pro/) セクションに追加されます。

### 3.2 アトラスの互換性

Mendix 8に移行する前に、最新のMendix 7互換のAtlasバージョン1.2.4を使用していることを確認してください。 最初にAtlasをこのバージョンにアップデートすることで、Mendix 8の移行後に設計プロパティに関連するいくつかのエラーを防ぐことができます。

Atlas 1.2.4にアップデートする方法

1. Studio Pro Atlas UI Resource モジュールでカスタマイズしたものがあるかどうかを確認します。Atlasを更新すると、そのモジュールのすべてのコンテンツが上書きされます。 アップデートする前に、カスタマイズしたコンテンツをAtlas UIモジュールから移動してください。
2. Mendixプロジェクト内の **テーマ** フォルダでカスタマイズしたものがあるかどうかを確認します。 **theme** フォルダの名前を *theme_oldest* のように別のフォルダに変更します。
3. Update Atlas by opening the Marketplace inside Studio Pro, search for *Atlas UI Resources*, click the **All Versions** pane, and download **Atlas UI Resources v1.2.4**.
4. プロンプトが表示されたら、既存のAtlasモジュールを置き換えることを選択してください。

{{% alert type="info" %}} You do not have to move any customized files from **theme_oldest** to **theme** yet, as after migrating to Mx8, you will update Atlas again which will create a new **theme folder**.{{% /alert %}}

## アプリを変換する {#converting}

次のサブセクションでは、Mendix 7からMendix 8へのアプリケーションの変換手順について説明します。

### 4.1 プロジェクトのバックアップ

チームサーバーに最新の変更をコミットしていることを確認してください。 または、変換を開始する前にローカルプロジェクトのバックアップを取った。

### 4.2 バージョン 7 の最新リリースにアップグレード {#upgrade}

{{% alert type="warning" %}}
アプリケーションをMendix 7の最新バージョン( [7.23](/releasenotes/studio-pro/7.23))にアップグレードすることが技術的に必要です。 アプリをMendix 8に変換できるのは7.23.xからのみです。
{{% /alert %}}

Mendix 7にアップグレードするには、以下の手順に従ってください:

1. Desktop Modelerの最新パッチリリースをダウンロード [7.23](/releasenotes/studio-pro/7.23).
2. Desktop Modelerでアプリを開きます。
3. 必要に応じてアプリのアップグレードを許可します。

### 4.3 Mendix 7プロジェクトのレビュー

以下のセクションと組み合わせてアプリを確認し、Mendix 8にアップグレードする前にさらにアクションを取る必要があるかどうかを評価します。

In particular, it is easier to fix deprecations in Java actions (see [Java Version, Deprecated and Removed APIs](#deprecated-apis)) in Mendix 7 before upgrading to Mendix 8. ただし、 Float と Currency 非推奨エラーは、Mendix 8 の代わりに修正しやすくなります (手順については [Type Float & Currency](#float-currency) のセクションを参照してください)。

### 4.4 バージョン7のプロジェクトを保存

これで、アプリをMendixバージョン8にアップグレードする準備が整いました。

必要に応じてプロジェクトに戻ることができるように、この時点でプロジェクトをバックアップ/コミットすることをお勧めします。

これで、Desktop Modelerバージョン7でプロジェクトを閉じることができます。

### 4.5 アプリをバージョン8にアップグレード

Mendixはあなたのためにあなたのアプリをアップグレードします。

Mendix Studio Proバージョン8でプロジェクトを開き、Studio Proがアプリケーションをバージョン8に更新できるようにします。

### 4.6 Studio Pro でエラー、警告 & 廃止予定 を確認する

廃止された項目についてのすべてのエラーメッセージとメッセージを確認し、必要に応じて変更を行います。

非推奨のデータ型のいずれかまたは両方を使用している場合、Currency と Float にエラーが表示されます。 詳細については、 [Type Float & Currency](#float-currency) のセクションを参照してください。

### 4.7 すべてのウィジェットをアップグレード

問題の可能性を最小限に抑えるには、プロジェクトで使用されているすべてのウィジェットやその他のMarketplaceモデルを最新バージョンに更新する必要があります。

マーケットプレイスで利用可能な新しいバージョンの Marketplace モジュールがあるか確認してください。 アップグレード時に特定のアクションを実行する必要があるかどうかを確認するには、Marketplace のバージョンリリースノートを参照してください。

一般的には、リリースノートで推奨されていない限り、モジュールを削除したり再インポートしたりしないでください。 削除して再インポートすると、モジュールに関連するデータや構成が失われる可能性があります。

### 4.8 レビュー & アプリのテスト

最後に、以下のセクションを確認し、必要なすべての変更を行ったことを確認してください。

予期しない結果をアプリでテストします。

{{% alert type="success" %}}
おめでとうございます アプリは正常にMendix 8にアップグレードされ、通常通り作業を続けることができます。
{{% /alert %}}

## 5種類のフロートの要素 & 通貨 {#float-currency}

Float 型と Currency 型は Mendix バージョン 7 で廃止され、Mendix バージョン 8 から削除されました。

以下のバージョンのFloatまたはCurrencyの要素は、バージョン8のエラーを報告します。

* 属性
* 定数
* 変数アクションを作成
* データセットの列とパラメータ
* マイクロフロー/ナノフローパラメータと戻り値の型
* Java/JavaScriptアクションパラメータと戻り値の型
* 関数 'formatFloat', 'parseFloat' と 'toFloat'

単一のアクションで非推奨エラーのほとんどを修正することができます。 これを達成するには、次の手順を実行します。

1. Studio Pro 8 では、通貨と浮動小数点のデータタイプのサポートに関するエラーメッセージが表示されます。

    ![エラー メッセージ: 通貨とフロートはサポートされなくなりました](attachments/moving-from-7-to-8/currency-float-error.png)

2. エラーメッセージを右クリックします。

    ![手動または自動的に変更しますか？](attachments/moving-from-7-to-8/currency-float-change-options.png)

3. **** をクリックして、すべての属性を自動的に変換します。

    ![すべての浮動小数点数と通貨を小数点以下に変換する際の警告](attachments/moving-from-7-to-8/convert-to-decimal-warning.png)

4. **** をクリックして変換を実行します。

{{% alert type="warning" %}}
このプロセス中に任意の属性が変換されている場合。 次回アプリをローカルまたはデプロイする際に、データベースは新しい属性タイプをサポートするように変換されます。

**This database conversion could take a long time!** We suggest that you first test the data conversion on a representative dataset, so that you can estimate how long it will take to convert your production database.
{{% /alert %}}

## 6 64 ビット Studio Pro

Mendix Desktop Modelerバージョン7は64ビットのアプリケーションでしたが、32ビットでも動作することができました。

Mendix Studio Proは、64ビットバージョンのWindows上で **のみ** 実行される64ビットアプリケーションです。 これは、Windows 7、Service Pack 1以降の64ビット版である必要があります。

## 7 Mendix Cloud Version 3

Mendix Studio Proで作成したアプリは、Mendix Cloudの *Version 3* に展開できません。 Mendix Cloud v3 ノードを使用している場合は、Mendix Cloud v4 にアップグレードすることをお勧めします。 これができない場合は、Mendix 7を引き続き使用してアプリの作成と保守を行う必要があります。

## 8 Java コード生成 {#java-code-generation}

Mendix Studio Pro バージョン 8 では、Java アクションと Java データセットの Java コードの生成方法を変更しています。

Mendix Desktop Modelerバージョン7では、Javaアクションとデータセットのパラメータの名前にポストフィックス( `Parameter1`など)が追加されることがあります。 この動作は、生成されたコードの名前の競合を防ぐために必要でした。 Mendix Desktop Modeler7のマイナーリリースでは、これらの競合が発生するのを防ぐための修正をいくつか導入し、この動作を冗長化しました。

私たちはまた、これらの名前の競合を防ぐために試みることに気づいた Javaコンパイルの失敗を引き起こすことがありました。それは、あなたが取り組んでいるものとはまったく関係がないように思えました。 postfixの追加は完全に不要になり、大きなアプリでかなりの問題が発生したことを見て、完全に削除することにしました。

実際には、それは何を意味するのですか? ほとんどのアプリでは何も変わらず、以前と同じように動作します。 しかし、限られた数のケースでは、Mendix Desktop Modelerバージョン7では、パラメータ名のpostfixが導入されます。 例えば、 `Customer` というパラメータは、生成された Java コード内で `CustomerParameter1` になる可能性があります。 アプリケーションを Mendix Studio Pro 8 に移行すると、このポストフィックスは削除されます。

これらの場合、コードが再びコンパイルされる前に簡単な修正を行う必要があります。

* エラーの原因となっているMarketplace からダウンロードされたモジュール内の Java アクションである場合。 もう一度ダウンロードするか最新版にアップデートしてください
* あなた自身のJavaアクションである場合。 その後、修正が簡単になります - Javaコードからこれらのポストフィックスを削除してください(前の例では、 `CustomerParameter1` は再び `Customer` になります。

### 8.1 違いの例

この例では、 `メッセージ`と呼ばれるパラメータを持つ `メッセージ` というJavaアクションがあります。 Mendix Modelerバージョン7では、 `Message`とも呼ばれるドメインモデルエンティティを導入した場合。 次のJavaコードを生成します（読みやすさのためにいくつかのコードが省略されていることに注意してください）：

```java
        public LogMessage(IContext context, java.lang.String MessageParameter1)
        {
            super(context);
            this.MessageParameter1 = MessageParameter1;
        }
        @java.lang.Override
        public java.lang.Boolean executeAction() throws Exception
        {
            // BEGIN USER CODE
            Core.getLogger("MyLogger").info(this.MessageParameter1);
            // END USER CODE
        }
```

ご覧のとおり、パラメータ `メッセージ` に名前を付ける代わりに、Mendix Modelerのバージョン7で名前を付けます。 `MessageParameter1`. `executeAction()` メソッドのユーザコードでは、 `this.Message` はメッセージをログに記録するために使用されます。 これはコードがコンパイルされないことを意味します。

Studio Pro 8 は以下のコードを生成します。

```java
        public LogMessage(IContext context, java.lang.String Message)
        {
            super(context);
            this.Message = Message;
        }
        @java.lang.Override
        public java.lang.Boolean executeAction() throws Exception
        {
            // BEGIN USER CODE
            Core.getLogger("MyLogger").info(this.Message);
            // END USER CODE
        }
```

このコードは期待どおりに動作し、すぐに動作します。 ただし、Mendix Modelerバージョン7がこのコードを生成していた方法に準拠するようにユーザーコードを以前に変更した場合。 パラメータの新しい名前を使用するには、ユーザーコードを更新するだけです。

## 9 トラブルシューティング

### 9.1 プロジェクトを開くことができません: `レイアウト … に無効な値があります …`

非常にまれに、 以前のバージョンのMendixからアップグレードする必要があるMendix Studio Pro 8でプロジェクトを開くと、以下のようなメッセージが表示される場合があります。

![レイアウト エラー メッセージ](attachments/moving-from-7-to-8/layout-import-message.png)

これは、レイアウトが **レイアウト タイプ** に対して無効な値を持っている場合に発生します。 これは、 *無効なレイアウトがプロジェクトから除外されていても* エラーを引き起こします。

プロジェクトでエラーが発生する可能性がある場合は、以下の画像を参照してください。

![レイアウトエラーの場所](attachments/moving-from-7-to-8/layout-error-location.png)

To resolve this issue, use the previous version of Mendix to change the invalid **Layout type** (in the example above, `Legacy`) to a valid value.

### 9.2 DOM と Atlas UI の問題

Mendix 8 では、DOM 構造がいくつか改善されています。 これらの DOM の変更は Sass のスタイルに影響します。 これらのアップデートにより、Mendix 8アプリは [Atlas UI Resources](/appstore/modules/atlas-ui-resources) (v2.0.0 以降)を使用して完了するように設計されています。 Atlas UIをアップグレードすると、アプリのテーマに問題が発生する可能性があります。 DOM または Atlas UI の移行に関する問題のトラブルシューティングについては、以下のドキュメントを参照してください。

* [DOM の変更のトラブルシューティング](migration-dom-issues)
* [アトラスUI変更のトラブルシューティング](migration-atlas)
