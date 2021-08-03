---
title: "コンテナ"
parent: "container-widgets"
---

コンテナウィジェットを使用して、ウィジェットのスタイルを設定したり、ウィジェットのグループを同時に非表示にしたりすることができます。 ブラウザーでは、デフォルトで単純な `div` 要素としてレンダリングされます。 コンテナを HTML5 半分要素のいずれかとしてレンダリングすることもできます (例えば、 `section`, `main`, `article`, `nav`).

{{% alert type="info" %}}

![](attachments/16713858/16843976.png) 空のコンテナ。

{{% /alert %}}

## 共通のプロパティ

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 一般プロパティ

### レンダリングモード

レンダリングモードは、Webブラウザでコンテナを表示するために使用されるHTML5タグを決定します。

| 値      | HTML タグ  |
| ------ | -------- |
| Div    | `div`    |
| セクション  | `セクション`  |
| 記事     | `記事`     |
| ヘッダー   | `ヘッダー`   |
| フッター   | `フッター`   |
| メイン    | `メイン`    |
| Nav    | `nav`    |
| アサイド   | `はさておき`  |
| Hgroup | `hgroup` |
| 住所     | `アドレス`   |

_Default value:_ Div

## 表示プロパティ

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Simple.md" %}}
