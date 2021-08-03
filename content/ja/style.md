---
title: "スタイル"
parent: "ドキュメントテンプレート"
---


ほとんどのドキュメントテンプレートのウィジェットやコンポーネント、トップレベルのドキュメントでは、スタイルを定義することができます。 このスタイルはカスケーディングスタイルシート (CSS) で設計されています。 ただし、スタイルエディタを使用して、より一般的なスタイル属性の多くを調整することができます。 スタイリングしているウィジェットの種類に応じて、スタイルエディターに異なるオプションが表示されます。 「カスタムスタイル」タブでスタイルを完全にカスタマイズすることもできます。

## Tab pages

### Font

フォントタブページが表示されるウィジェット/コンポーネント

*   ドキュメントテンプレート
*   データグリッド
*   データグリッドセル
*   動的ラベル
*   タイトル
*   スタティックラベル
*   表

{{% alert type="info" %}}

![](attachments/modeler-core/2018-03-01_14-27-27.png) スタイルエディタのフォントタブページ。

{{% /alert %}}

アラビア語やタイ語などの一般的でない文字を含む言語でテキストを表示したい場合。 これらの文字をサポートするスタイルエディタでフォントを選択してください。 「タホマ」はそのようなフォントです。

### セルスタイル

セルスタイルタブページが表示されるウィジェット/コンポーネント:

*   データグリッド
*   データグリッドセル
*   タイトル
*   表
*   テーブルセル

{{% alert type="info" %}}

![](attachments/modeler-core/2018-03-01_14-29-13.png) スタイルエディタのセルスタイルタブページ。

{{% /alert %}}

### Custom styles

カスタムスタイルタブページは、スタイリングを可能にするウィジェット/コンポーネントに常に表示されます。

{{% alert type="info" %}}

![](attachments/modeler-core/2018-03-01_14-33-46.png) スタイルエディタのカスタムスタイルタブページ。

{{% /alert %}}

## PDF ドキュメント用のカスタムフォント

You can include custom fonts in your generated documents by simply using a custom style, for example you'd include _font-family: Verdana;_ in your style to make the text appear in Verdana font. ただし、PDFドキュメントを生成するには、追加の作業が必要です。 次のセクションでは、これを行う方法を説明します。

PDFジェネレータは、PDFファイルの生成を担当するライブラリの設定ファイルを編集することで、カスタムフォントを含めるように設定することができます。 このファイルは、/runtime/libサブフォルダのMendixインストールフォルダにあります。 ファイルは fop.xconf と呼ばれます。 Mendixのバージョンを簡単に更新したり、アプリケーションをデプロイしたりするには、このファイルを直接編集しないで、代わりにプロジェクトのリソースフォルダにコピーすることを強くお勧めします。 このファイルがresourcesフォルダに存在する場合、ランタイムはデフォルトファイルの代わりに自動的にアクセスします。

{{% alert type="warning" %}}

PDFライブラリで使用したいフォントのうち2つはMendixにデフォルトで含まれています。 これらはArialとTahomaのフォントです。 これらのフォントはリソースフォルダにもコピーする必要があります。 /runtime/libフォルダ内のすべてのTTFファイルを見つけます。6(arial.ttf, arialbd.ttf, arialbi.ttf, ariali.ttf, tahoma.ttf, tahoma.ttf, tahomabd.ttf)

{{% /alert %}}

あなたがfopを持っているとき。 confファイルとresourcesフォルダ内のすべてのフォントは、使用したいフォントをフォルダに追加できます。 次に、fop.xconf ファイルをテキストエディタで開きます。 設定ファイルは xml 形式です。 上を見る <fonts> タグとあなたはTahomaとArialを簡単にシングルアウトすることができます。

独自の設定を追加するには、以下の設定を使用してください。

```java

<font kerning="yes" embed-url="mycustomfont.ttf">
    <font-triplet name="myfont" style="normal" weight="normal"/>
</font>

```

埋め込みURLは、ライブラリがフォントファイルを見つけることができる場所です。 font-triple-name は、カスタム CSS スタイルで使用する名前です。 この名前は、独自のカスタムフォントの小文字にする必要があります。

斜体または太字のフォントを使用する場合は、これも指定する必要があります。 例:

```java
<font kerning="yes" embed-url="mycustomfontinbold.ttf">
   <font-triplet name="myfont" style="normal" weight="bold"/>
</font>

<font kerning="yes" embed-url="mycustomfontinitalic.ttf">
   <font-triplet name="myfont" style="italic" weight="normal"/>
</font>

<font kerning="yes" embed-url="mycustomfontinboldanditalic.ttf">
   <font-triplet name="myfont" style="italic" weight="bold"/>
</font>

```

最後に、セットアップは次のようになります:

*   fop.xconf カスタムフォントと 6 つのデフォルトフォントがプロジェクトのリソースフォルダに含まれているはずです。
*   fop.xconf ファイルにカスタムフォントへの参照を含める必要があります。
