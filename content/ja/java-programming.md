---
title: "Javaプログラミング"
description: "Mendix Javaライブラリを使用し、Mendix Javaアクションを作成するための環境としてEclipseを使用する方法を説明します。"
tags:
  - "studio pro"
---

## 1つの紹介

Javaアクションを使用すると、マイクロフローにこの機能を実装するのが難しい状況でアプリケーションの機能を拡張できます。

Studio Pro で Java アクションについての詳細は、 [Java アクション](java-actions) を参照してください。

## 2 Javaアクションの.javaファイルにコードを書く

In *.java* files of your Java actions, the method `executeAction` is called by the Mendix Runtime when the Java action is being executed. メソッドは発生するすべての例外をスローします。 つまり、このJavaアクションを呼び出してマイクロフローでエラー処理を行うことができます。 アクション内で独自のエラー処理を行いたい場合は、 `` / `catch` 文を使用してください。

Between the line `// BEGIN USER CODE` and `// END USER CODE`, アクションの実行時に常に呼び出されるカスタムコードを書くことができます。 You can call other methods in the section between `// BEGIN EXTRA CODE` and `// END EXTRA CODE`.

ブロック外のコードは、モデルをデプロイするたびに再生成されるため、そのブロック内で行った変更は上書きされます。 ただし、インポートは保持されます。

```java
// このファイルは Mendix Studio Pro によって生成されました。
//
// 警告: Only the following code will be continued when actions are regenerated:
// - the import list
// - the code between BEGIN USER CODE and END USER CODE
// - the code between BEGIN EXTRA CODE and END EXTRA CODE
// Other code you will be lost the next time you deploy the project.
// Special characters, e', o<unk> , etc. is supported in comments.

package myfirstmodule.actions;

import com.mendix.systemwideinterfaces.core.IContext;
import com.mendix.webui.CustomJavaAction;

public class JavaAction_1 extends CustomJavaAction<java.lang.Void>
{
    public JavaAction_1(IContext context)
    {
        super(context);
    }
    @java.lang.Override
    public java.lang.Void executeAction() throws Exception
    {
        // BEGIN USER CODE
        return true;
        // END USER CODE
    }
    /**
     * Returns a string representation of this action
     */
    @java.lang.Override
    public java.lang.String toString()
    {
        return "JavaAction_1";
    }

    // BEGIN EXTRA CODE
    // END EXTRA CODE
}
```

## 3 Mendix Javaライブラリの使用

Java アクション用に記述する Java コードの Mendix Java ライブラリを使用できます。

{{% alert type="info" %}}
You can find the Javadoc at [Runtime API](/apidocs-mxsdk/apidocs/runtime-api) or in the directory Studio Pro is installed in (for example, *C:\Program Files\Mendix\9.0.0\runtime\javadoc*).
{{% /alert %}}

このライブラリは、アプリを Eclipse にインポートすると自動的にライブラリに追加されます。これは *mxruntime.jar* と呼ばれます。

使用方法や例については、 [Java API の使い方](/howto/logic-business-rules/java-api-tutorial) を参照してください。

## 4 HTTP接続を開く

(Mendix Cloudで使用されているものを含む)ほとんどのクラウドインフラストラクチャサービスは、数分間トラフィックがない場合、自動的にHTTP接続を閉じます。 活動がまだ反応を待っていてもね これは、アクティビティがWebサービスを呼び出す場合、応答に長い時間がかかることを意味します。 これを認識せずに接続が切断される可能性があります。あなたのアクティビティは応答を受け取れません。 データが届くのを無期限に待つのではなく立ち往生します

そのため、カスタムJavaコードで接続のタイムアウトを常に設定する必要があります。

## 5 Mendix Javaアクションを書くための環境としてEclipseを使う

このトピックの詳細については、 [Eclipse の使用](using-eclipse) を参照してください。

## このカテゴリ内の6つのメインドキュメント

* [トラブルシューティング](troubleshooting) - 問題のあるJARファイルと回避策を提示します
* [Eclipseを使用する](using-eclipse) – MendixアプリでJavaアクションを書き出してデバッグする方法を説明します。
