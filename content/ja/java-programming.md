---
title: "Javaプログラミング"
description: "Mendix Javaライブラリを使用し、Mendix Javaアクションを作成するための環境としてEclipseを使用する方法を説明します。"
---

## 1つの紹介

Javaアクションを使用すると、マイクロフローにこの機能を実装するのが難しい状況でアプリケーションの機能を拡張できます。

ModelerでのJavaアクションについては、 [Java Actions](java-actions) を参照してください。

## 2 Javaアクションの.javaファイルにコードを書く

Javaアクションの *Java* ファイルでは、マーカー間でJavaコードを記述できます。

*   `// BEGIN USER CODE` and `// END USER CODE`
*   `// BEGIN EXTRA CODE` and `// END EXTRA CODE`

これについては以下で詳しく説明します。

これらのファイルの他のコードは、モデルをデプロイするたびに再生成されます。 このように変更したものは上書きされます ただし、インポートは保持されます。

{{% alert type="info" %}}

![](attachments/819203/917584.png) Mendix Desktop Modelerによって生成されたJavaアクション。 この Java アクションには入力パラメータがなく、ブール値を `true` で返します。

{{% /alert %}}

メソッド _executeAction_ は Java アクションの実行時に Runtime によって呼び出されます。 Between the line `// BEGIN USER CODE` and `// END USER CODE`, アクションの実行時に常に呼び出されるカスタムコードを書くことができます。 この方法で you can call other methods in the section between `// BEGIN EXTRA CODE` and`// END EXTRA CODE`.

executeAction メソッドは発生するすべての例外をスローします。 つまり、このJavaアクションを呼び出してマイクロフローでエラー処理を行うことができます。 アクション内で独自のエラー処理を行いたい場合は、try/catch 文を使用します。

## 3 Mendix Java ライブラリの使用

Javaアクション用に記述するJavaコードでは、Mendix Javaライブラリを使用できます。

{{% alert type="info" %}}
Javadoc は
apidocs.rnd.mendix にあります。 om [](http://apidocs.rnd.mendix.com/7/runtime/index.html) または Mendix をインストールしたディレクトリに (例えば、 *C:\Program Files\Mendix\7.0.0\runtime\javado*). </p> 

{{% /alert %}}

プロジェクトを Eclipse にインポートすると、このライブラリは自動的にライブラリに追加され、 *mxruntime.jar* と呼ばれます。

使用方法や例については、 [Java API の使い方](/howto7/logic-business-rules/java-api-tutorial) を参照してください。



## 4 Mendix Javaアクションを記述するための環境としてEclipseを使う

このトピックの詳細については、 [Eclipse の使用](using-eclipse) を参照してください。



## このカテゴリ内の5つのメインドキュメント

* [トラブルシューティング](トラブルシューティング)
* [Eclipse を使用する](using-eclipse)
