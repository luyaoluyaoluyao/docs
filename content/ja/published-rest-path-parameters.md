---
title: "公開された REST パスのパラメータ"
parent: "published-rest-service"
menu_order: 30
tags:
  - "公開された REST"
  - "パスパラメータ"
  - "データと時間"
  - "studio pro"
---

[公開された REST 操作](published-rest-operation) 内の操作パスは、操作の場所 (URL) の最後の部分を指定します。

1 つまたは複数のパスパラメーターを使用して、ロケーションの一部をマイクロフローパラメーターとしてキャプチャできます。 `{` と `}` の間の操作パスにパスパラメータを指定します。

pathパラメータの場所にあるURL内にあるものは、microflow、import マッピング、または両方に渡されます。

パスパラメータの要件は次のとおりです。

* 同じパスパラメータを2回操作パスで使用することはできません
* Path parameter names cannot contain curry braces (`{` or `}`)
* パスパラメータはプリミティブ型のみを持つことができます (ブール値、日付と時刻、小数値、列挙値、整数/長さ、文字列)
* パスパラメータはパス内のスラッシュ（`/`）間のみ表示できます

[公開された REST 操作](published-rest-operation) エディターウィンドウから新しいマイクロフローを生成する場合 その結果のマイクロフローは、オペレーションパスで指定されたパスパラメータごとに文字列パラメータを持つことになります。 パスパラメータを異なるタイプにしたい場合は、マイクロフロー内のタイプを変更できます。

Date and time parameters should be entered in the [ISO-8601](https://www.w3schools.com/xml/schema_dtypes_date.asp) format (for example, `2018-12-31T09:00:00`).
