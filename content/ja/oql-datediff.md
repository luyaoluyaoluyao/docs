---
title: "OQL DATEDIFF"
parent: "oql-functions"
---


DATEDIFF関数は、指定された2つの日付/時刻の値の差を返します。 指定された単位で差分が与えられます。

構文は以下の通りです:

```
DATEDIFF ( 単位 , startdate_expression , enddate_expression )
```

**単位**

取得する日付/時刻の値の単位を指定します。 これは次のいずれかになります。

`YEAR`, `QUARTER`, `MONTH`, `DAY`, `WEEK`, `HOUR`, `MINUTE` or `SECOND`.

**startdate_expression** 計算されている期間の開始日を指定します。 これは、日付/時刻の値を解決する式でフォーマットされる必要があります。

**enddate_expression** 計算されている期間の終了日を指定します。 これは、日付/時刻の値を解決する式でフォーマットされる必要があります。
