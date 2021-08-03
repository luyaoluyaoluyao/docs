---
title: "OQL DATEDIFF"
parent: "oql-functions"
tags:
  - "studio pro"
---

## 1つの説明

`DATEDIFF` 関数は、与えられた日付/時刻の値の差を返します。 指定された単位で差分が与えられます。

## 2つの構文

構文は以下の通りです:

```sql
DATEDIFF ( 単位 , startdate_expression , enddate_expression )
```

### 2.1 単位

`単位` では、取得する日付/時刻値の単位を指定します。 This can be one of the following: `YEAR`, `QUARTER`, `MONTH`, `DAY`, `WEEK`, `HOUR`, `MINUTE` or `SECOND`. 日付/時刻の値の詳細については、 [OQL DATEPART](oql-datepart#oql-datepart-example) の *例* セクションを参照してください。

### 2.2 startdate_expression

`startdate_expression` は計算される期間の開始日を指定します。 これは、日付/時刻の値を解決する式でフォーマットされる必要があります。

### 2.3 endate_expression

`enddate_expression` は計算される期間の終了日を指定します。 これは、日付/時刻の値を解決する式でフォーマットされる必要があります。
