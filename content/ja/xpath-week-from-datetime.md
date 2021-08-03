---
title: "XPath Week-from-DateTime"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

## 1つの概要

`week-from-dateTime()` 関数は、 **Date and time** 属性から週番号を抽出し、値と比較するために使用することができます。 値は 1 から 53 の範囲です。

{{% alert type="warning" %}}
返される値は、Mendixアプリをサポートするためにどの *データベース* が使用されているかによって異なります。 *は* アプリのランタイム設定 **週の最初の日** を考慮しません。

多くのデータベースは [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)を実装していますが、正確な詳細を見つけるために使用しているデータベースのドキュメントを参照してください。
{{% /alert %}}

## 2つの例

このクエリは、日付 `DateAttribute` が年の 2 週目になるすべてのログを返します(例: "2011-01-13" )。

```java
//Logging.Log[week-from-dateTime(DateAttribute) = 2]
```

## 3 続きを読む

Mendixで使用されている多くのデータベースの特定の日付について週番号が計算される方法に関する関連ドキュメントには、次のリンクがあります。

ローカルでテストするために使用されるHSQLDBデータベースは、JVMの [カレンダー.WEEK_OF_YEAR](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/Calendar.html)を使用します。

PostgreSQL, Oracle, MySQL follow [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601):

* [PostgreSQL](https://www.postgresql.org/docs/11/functions-datetime.html)
* [Oracle](https://docs.oracle.com/cd/B28359_01/olap.111/b28126/dml_commands_1029.htm#OLADM780)
* [MySQL](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html#function_week)

他のデータベースには、より具体的な動作があります。

* [SQL Server](https://docs.microsoft.com/en-us/sql/t-sql/functions/datepart-transact-sql?view=sql-server-ver15)
* [DB2](https://www.ibm.com/support/knowledgecenter/en/SSEPEK_10.0.0/sqlref/src/tpc/db2z_bif_week.html)
