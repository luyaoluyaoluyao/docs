---
title: "MySQL/MariaDB"
parent: "データストレージ"
menu_order: 50
---

## 1つの紹介

MySQLまたはMariaDBデータベースを使用してMendixアプリケーションを実装する場合は、いくつかの追加の考慮事項があります。 また、MySQLまたはMariaDBデータベースを使用したMendixの動作には、PostgreSQLデータベースの使用と比較していくつかの微妙な違いがあります。

これらの考慮事項と相違点は以下のとおりです。

## 2つのストレージエンジン

MendixはInnoDBストレージエンジンのみをサポートし、行ベースのログを有効にします。

## 3 トランザクションの分離数

Mendixは、Mendix7.2のリリースから始まる `Read Committed` トランザクション分離レベルをデフォルトで使用します。 行ベースのログは、このトランザクション分離レベルの場合にのみ使用できます。 `binlog_format` データベース設定値を `ROW` または `MIXED` に設定する必要があります。 詳細については、MariaDB [の``](https://dev.mysql.com/doc/refman/5.7/en/replication-options-binary-log.html#sysvar_binlog_format) または [`binlog_format`](https://mariadb.com/kb/en/mariadb/replication-and-binary-log-server-system-variables/#binlog_format) を参照してください。

## 保存例外が4つ存在しません

`SAVEPOINT という名前のない` を受け取った場合、例外は存在しません。デッドロックが発生しました。 MySQL/MariaDBは自動的にトランザクションをロールバックし、そのトランザクションのすべてのセーブポイントを削除するため、Mendixはこの状況を正しく処理できません。 Mendixは特定のセーブポイントにロールバックしようとしますが、MySQLとMariaDBではそれはもう許可されていません。 可能な限りトランザクションを短縮してデッドロックを回避することをお勧めします。

## 5つのタイムゾーンサポート

Mendixは、クエリで日付と時刻の一部を抽出する機能をサポートしています。 XPathでは、 [`hours-from-dateTime`](xpath-hours-from-datetime) や [`week-from-dateTime`](xpath-week-from-datetime) のような関数を使用できます。 OQL では、 [`DATEPART(..)`](oql-datepart) や [`DATEDIFF(..)`](oql-datediff) のような関数を使用できます。

Mendix, DateTimesはUTCタイムゾーンに保存されます。 これらの関数が正しく動作するためには、データベースがUTCから別のタイムゾーンに日付と時刻を変換することが重要です。 これが不可能であれば、関数はUTCタイムゾーンの日付と時刻で動作します。 これは、ユーザーが日付が自分のタイムゾーンで動作することを期待する場合、誤った結果をもたらす可能性があります。

MySQLは、すぐに使えるタイムゾーン変換を完全にサポートしていません。 タイムゾーン表を入力する必要があります(詳細については、 [10.6 MySQL Server Time Zone Support](http://dev.mysql.com/doc/refman/5.5/en/time-zone-support.html) を参照してください)。 クエリでこの種の関数を使用しない場合は、これを行う必要はありません。 または常にUTCの日付と時刻を使用したい場合。

MariaDBは、タイムゾーン変換のための同一の構成をサポートしています。

## 6データベース作成

Mendix 7.18以降では、MySQLデータベースの新規作成がサポートされています。 ユーザーがデータベースを作成できるようにするための十分なアクセス権限が必要です。
