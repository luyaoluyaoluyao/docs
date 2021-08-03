---
title: "Javaプログラミング"
description: "Mendix Javaライブラリを使用し、Mendix Javaアクションを作成するための環境としてEclipseを使用する方法を説明します。"
tags:
  - "studio pro"
---

## 1つの紹介

Javaアクションを使用すると、マイクロフローにこの機能を実装するのが難しい状況でアプリケーションの機能を拡張できます。

MendixでJavaプログラミングを深く掘り下げてみるには、このビデオをご覧ください。

<img
  style="width: 100%; margin: auto; display: block;"
  class="vidyard-player-embed"
  src="https://videoshare.mendix.com/watch/aDNqicHTbTMAqYkQvvxAjc?.jpg"
  data-uuid="aDNqicHTbTMAqYkQvvxAjc?"
  data-v="4"
  data-type="inline"
 />

Studio Pro で Java アクションについての詳細は、 [Java アクション](java-actions) を参照してください。


## 2 Javaアクションの.javaファイルにコードを書く

Javaアクションの *Java* ファイルでは、マーカー間でJavaコードを記述できます。

*   `// BEGIN USER CODE` and `// END USER CODE`
*   `// BEGIN EXTRA CODE` and `// END EXTRA CODE`

これについては以下で詳しく説明します。

これらのファイルの他のコードは、モデルをデプロイするたびに再生成されます。 このように変更したものは上書きされます ただし、インポートは保持されます。

{{% alert type="info" %}}

![](attachments/java-programming/917584.png) Mendix Studio Proによって生成されたJavaアクション。 この Java アクションには入力パラメータがなく、ブール値を `true` で返します。

{{% /alert %}}

メソッド _executeAction_ は Java アクションの実行時に Runtime によって呼び出されます。 Between the line `// BEGIN USER CODE` and `// END USER CODE`, アクションの実行時に常に呼び出されるカスタムコードを書くことができます。 この方法で you can call other methods in the section between `// BEGIN EXTRA CODE` and`// END EXTRA CODE`.

executeAction メソッドは発生するすべての例外をスローします。 つまり、このJavaアクションを呼び出してマイクロフローでエラー処理を行うことができます。 アクション内で独自のエラー処理を行いたい場合は、try/catch 文を使用します。

## 3 Mendix Java ライブラリの使用

Javaアクション用に記述するJavaコードでは、Mendix Javaライブラリを使用できます。

{{% alert type="info" %}}
Javadoc は
apidocs.rnd.mendix にあります。 om [](http://apidocs.rnd.mendix.com/8/runtime/index.html) or in the directory which installed Mendix (example, *C:\Program Files\Mendix\8.0.0\runtime\javadoc*). </p> 

{{% /alert %}}

プロジェクトを Eclipse にインポートすると、このライブラリは自動的にライブラリに追加され、 *mxruntime.jar* と呼ばれます。

使用方法や例については、 [Java API の使い方](/howto8/logic-business-rules/java-api-tutorial) を参照してください。



## 4 HTTP接続を開く

(Mendix Cloudで使用されているものを含む)ほとんどのクラウドインフラストラクチャサービスは、数分間トラフィックがない場合、自動的にHTTP接続を閉じます。 活動がまだ反応を待っていてもね これは、アクティビティがWebサービスを呼び出す場合、応答に長い時間がかかることを意味します。 これを認識せずに接続が切断される可能性があります。あなたのアクティビティは応答を受け取れません。 データが届くのを無期限に待つのではなく立ち往生します

そのため、カスタムJavaコードで接続のタイムアウトを常に設定する必要があります。



## 5 Mendix Javaアクションを書くための環境としてEclipseを使う

このトピックの詳細については、 [Eclipse の使用](using-eclipse) を参照してください。



## このカテゴリ内の6つのメインドキュメント

* [トラブルシューティング](troubleshooting) - 問題のあるJARファイルと回避策を提示します
* [Eclipseを使用する](using-eclipse) – MendixアプリでJavaアクションを書き出してデバッグする方法を説明します。
