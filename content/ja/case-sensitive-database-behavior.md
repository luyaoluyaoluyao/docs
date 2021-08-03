---
title: "大文字小文字を区別するデータベースの動作"
parent: "データストレージ"
tags:
  - "studio pro"
  - "文字列"
  - "並べ替え"
  - "ケース"
  - "クエリ"
  - "制約|制約"
menu_order: 20
---

## 1つの紹介

大文字と小文字を異なる文字と見なす操作です。 クエリ内の文字列に影響を与える操作(例えば、XPath の制約内で)は、大文字と小文字を区別したり、データベースベンダーによっては大文字と小文字を区別したりすることができます。 バージョン、およびMendixアプリケーションで使用される構成。

また、大文字小文字を区別しない操作の各実装は、文字の正規化を別々に扱う可能性があることに注意することも重要です。 原則として、正規化はロケールに基づく。 これは、データベース/テーブルで明示的に指定されるか、オペレーティングシステムから推奨されるデータベースです。 この文字、または大文字の正規化は、 [World Wide Web Consortium](https://www.w3.org/International/wiki/Case_folding) wikiの *ケース折りたたみ* でさらに説明されています。

このドキュメントでは、大文字小文字を区別する操作を3つのカテゴリに分けます。

* 並べ替え: オブジェクトを取得する順序を示します (アルファベット順に昇順または降順)。
* 比較: これらはクエリに直接等価または他の比較を伴う演算子です(例えば、クエリ `\\Entity[Attribute = 'a']`)
* 文字列関数: これらは [に](xpath-contains), [starts-with](xpath-starts-with), および [XPath の](xpath-ends-with) 関数が含まれています。

以下に特に示されていない限り、文字列の並べ替えと比較は大文字と小文字を区別しません。 これは、データベース、テーブル、または列の照合、および他のデータベース固有のオプションによって影響を受けます。 使用可能な照合順序とオプションは、ベンダー(および場合によってはバージョン)固有です。

## 2データベース型によるケース感度の動作

次のセクションでは、Mendix でサポートされているデータベースのデフォルトの動作について説明します。

### 2.1 HSQLDB

**ソート、比較、および文字列関数のための大文字小文字を区別しない**。

### 2.2 POSTGRESQL

並べ替えと比較は、 **大文字と小文字を区別する** です。 設定できません。

String functions are **case insensitive** as they are implemented using the `ILIKE` SQL operator.

### 2.3 DB2

並べ替えと比較は **大文字小文字を区別する** です。 8.14 以下のバージョンでは、すべての操作は **大文字と小文字を区別する** です。 両方のバージョングループでは、照合順序が **大文字小文字を区別しない**に設定されている例外があり、これはすべての操作に影響します。 詳細については、 [DB2](db2#making) の *DB2 大文字と小文字を区別する* セクションを参照してください。

文字列属性の無制限長の並び替えはサポートされていません。

### 2.4 MARIADB & MYSQL

すべての操作は、構成された照合順序に依存します。 The default collation is `utf8_general_ci` when the `utf8` character set is used, or `latin1_swedish_ci` when the `latin1` character set is used. これらのデフォルトの照合順序は **大文字小文字を区別しない** です。

### 2.5 ORACLE

並べ替えと比較は、構成された照合順序によって異なります。 The default collation is `binary`, which is **case sensitive**, but a `binary_ci` is available for case insensitive operations.

異なる値を `NLS_SORT` および `NLS_COMP` 「言語的な並べ替え」に設定することで、ソートと比較操作のために異なる照合順序を設定することができます。

文字列属性の無制限長の比較はサポートされていません。

String functions are implemented by converting all letters to uppercase using the database's `UPPER` function and are, therefore, **case insensitive** and insensitive to the `locale` in which they are executed.

### 2.6 SAP HANA

文字列属性の無制限長のソートや比較はサポートされていません。

### 2.7 SQL サーバー

すべての操作は照合順序に依存します。 デフォルトの照合順序は `SQL_Latin1_General_CP1_CI_AS` です。 詳細はこちら [新しい SQL Server データベースのセットアップ](/developerportal/deploy/setting-up-a-new-sql-server-database) と Microsoft ドキュメント [Windows の照合名](https://docs.microsoft.com/en-us/sql/t-sql/statements/windows-collation-name-transact-sql) を参照してください。

## 既定のケース感度の3つの概要

この表には、異なるデータベースタイプでのデフォルトのケースセンシティビティが表示されます。

|   **データベースの種類** | **比較** | **並び替え** | **文字列関数** |
| ---------------:|:------:|:--------:|:---------:|
|          HSQLDB |   I    |    I     |     I     |
|      POSTGRESQL |   S    |    S     |     I     |
|             DB2 |   S    |    S1    |    I3     |
| MARIADB & MYSQL |   C    |    C     |     C     |
|              配置 |   C1   |    C     |     I     |
|        SAP HANA |   S1   |    S1    |    I2     |
|        SQL サーバー |   C    |    C     |     C     |

文字には以下の意味がある場合:

* **S** – 大文字と小文字を区別する
* **C** - 照合/構成に依存する
* **I** – 大文字小文字を区別しない

1文字列の長さに制限はありません。 2Mendixバージョン8.11.0から 3Mendixバージョン8.14.0から
