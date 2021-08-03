---
title: "OQL DATEPART"
parent: "oql-functions"
tags:
  - "studio pro"
---

## 1つの説明

`DATEPART` 関数は、日付/時刻の値から指定された要素を取得します。 この要素は整数型です。

## 2つの構文

構文は以下の通りです:

```sql
DATEPART(datepart , date_expression )
```

### 2.1 datepart

`datepart` は、取得する日付/時刻の値の一部を指定します。 値については、以下の [例](#oql-datepart-example) を参照してください。

### 2.2 日付表現

`date_expression` は要素を取得する日付を指定します。 これは、日付/時刻の値を解決する式でフォーマットされる必要があります。

## 3 例{#oql-datepart-example}

| datepart    | 定義                | 例（2005年7月1日(金)16:34:20） |
| ----------- | ----------------- | ----------------------- |
| `YEAR`      |                   | 2005                    |
| `QUARTER`   | 1、2、3、4           | 3                       |
| `月`         | 1 ~ 12            | 7                       |
| `DAYOFYEAR` | 1～366             |                         |
| `日`         | 1～31              | 5                       |
| `WEEK`      | 1～53（データベースの実装次第） |                         |
| `WEEKDay`   | 1～7（1=日曜、7=土曜）    | 6                       |
| `HOUR`      | 0から23             | 16                      |
| `分`         | 0 から 59           | 34                      |
| `秒`         | 0 から 59           | 20                      |
