---
title: "公開された REST クエリパラメータ"
parent: "published-rest-service"
menu_order: 40
description: "公開された REST クエリのパラメータ"
tags:
  - "公開された REST"
  - "クエリ"
  - "パラメータ"
  - "日付と時刻の形式"
---

{{% alert type="info" %}}

**公開されたRESTサービス** 機能は、バージョン7.10.0で導入されました。

{{% /alert %}}

[公開された REST 操作](published-rest-operation) の仕様には、操作を実装するマイクロフローが含まれています。 このマイクロフローは、リクエストのクエリ文字列から来るパラメータを取ることができます。

クエリパラメータはプリミティブ型(コール、日付と時刻、小数、列挙、整数/longer、文字列)のみを持つことができます。

クエリパラメータは、 `?name=John&age=42` のクエリマークに続くパスの最後に追加されます。 これは操作 [の](published-rest-operation#example-location) の場所例に示されています。

クエリパラメータに関する追加のメモは次のとおりです。

* クエリパラメータは大文字と小文字を区別します
* Date and time parameters should be entered in the [ISO-8601](https://www.w3schools.com/xml/schema_dtypes_date.asp) format (for example, `2018-12-31T09:00:00`)
* When a client calls the operation without specifying the query paramater, it will have the value `empty` in the microflow (except when it has the Boolean type, which is `false` by default)
