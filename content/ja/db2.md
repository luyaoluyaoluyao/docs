---
title: "DB2"
parent: "データストレージ"
menu_order: 40
tags:
  - "studio pro"
---

## 1つの紹介

DB2 データベースを使用して Mendix アプリを実装する場合は、いくつかの追加的な考慮事項があります。 さらに、DB2 データベースを使用した Mendix の動作には、PostgreSQL データベースと比較して若干の違いがあります。

これらの考慮事項と相違点は以下のとおりです。

## 2 表領域のページサイズ

Mendix が DB2 上で実行されるようにするには ユーザーテーブルスペースが少なくとも8Kのページサイズを持つことが非常に重要です (しかし、好ましくは32K)。 これはMendixが国の文字列(NVARCHARまたはVARCHARと文字列ユニットCODEUNIT32)を使用するためです。 このデータ型は、オクテットベースの VARCHAR よりも多くのスペースを消費します。 システム管理では、Mendixはインデックス付きのテーブルを常に作成し、少なくとも8Kのテーブル空間ページサイズを必要とします。

**SQLコードの例外 `-614`**

ページサイズに対してインデックスが大きすぎる場合、DB2 は例外を投げます: `com.ibm.db2.jcc.am.SQLException: DB2 SQL Error: SQLCODE=-614, SQLSTATE=54008, SQLERRMC=some_index_name`

ユーザーが作成したインデックスの場合、インデックス内の指定された列の長さが最大キーの長さよりも大きい場合。 表領域のページサイズも増やしてください。

詳細についてはこちら see [SQL0614N – 指定された列の組み合わせ長さが](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.db2.luw.messages.sql.doc/doc/msql00614n.html) *SQL messages* セクションの *IBM Knowledge Center* で長すぎるため、インデックスまたはインデックス拡張インデックス名は作成または変更できません。

## 3トランザクションログサイズ

**SQLコードの例外 `-964`**

If the transaction log space is depleted or there is a temporary increase in the number of active transactions, DB2 will throw this exception: `com.ibm.db2.jcc.am.SqlException: DB2 SQL Error: SQLCODE=-964, SQLSTATE=57011, SQLERRMC=null`.

この場合、 *LOGPRIMARY* のサイズを増やす必要があります。

For more detailed information, see [DB2 SQL error: SQLCODE: -964, SQLSTATE: 57011, SQLERRMC: null](http://www-01.ibm.com/support/docview.wss?uid=swg21298630) on the *IBM Support* pages and [SQL0964C – The transaction log for the database is full](http://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.db2.luw.messages.sql.doc/doc/msql00964c.html) in the *SQL messages* section of the *IBM Knowledge Center*.

## 5つの制限事項

### 5.1 文字列の比較は大文字と小文字を区別する {#making}

DB2 では、文字列列の値を並べ替えることは大文字と小文字を区別します。 これを軽減するために、IBMはロケール対応のUnicode照合をDB2 9.5 fixpack 1に導入しました。 これらの照合順序は、ケースやアクセントを無視するように調整することができます。

詳細については、 [IBM Developer Works](https://developer.ibm.com/technologies/databases/articles/making-db2-case-insensitive#refname) の *DB2 大文字小文字を区別しない* を参照してください。

### 5.2 非常に長い文字列でソート

8192文字を超える長さの無制限の文字列や文字列をソートすることはできません。 これは、このような長い文字列または無制限の文字列が NCLOB データ型で実装されているためです。 DB2 はこのデータ型の列のソートを許可しません。 技術的には、クエリの実行中にこの型を通常の VARCHAR タイプにキャストし、これを並べ替えることができます。 これにより実行時間が延長されます 問題は、データグリッドにこんな長い文字列を表示するのは本当にユーザーフレンドリーであるかどうかです。 文字列属性の長さを減らすか、データグリッドから削除することを検討してください。

### 5.3 相関スカラーフルセレクトまたは外部アクションを伴う関数

[IBM DB2 SQL リファレンス](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.sql.ref.doc/doc/r0059211.html) 内の *order-by-節*ドキュメントによると、 DB2 は、相関するスカラーフルセレクト(SQLSTATE42703)または外部アクション(SQLSTATE42845)を伴う関数によるORDER BYをサポートしていません。

この制限を考慮すると、Mendix アプリケーションが DB2 でサポートされている場合、関連付けられた属性による順序付けはサポートされません。 そのため、 順序付けに使用される関連する属性は、クエリから除外され、関連付けられた属性による順序付けがクエリに表示されていなかったかのように結果セットが返されます。

### 5.4 読み取り/分離されたODataによるストリーミングをブロックしない

[IBM DB2 アプリケーション設計](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.db2.luw.admin.perf.doc/doc/c0004121.html) の *Isolation level*のformat@@4 によると、ノンブロッキングの読み取り分離されたクエリは DB2 によってサポートされていません。 DB2 のデフォルトの動作は、あるユーザーがテーブルから行を取得し、別のユーザーが同じテーブルに対して同時に変更を加えている場合です。 これらの変更は、取得クエリ内のデータに表示されます(つまり、データベースの読み込みは分離されません)。 この動作を防ぐために厳格なトランザクション分離レベルを設定すると、同じ行がロックされます (同時データベースアクションがブロックされていることを意味します)。

この制限を考慮する Mendix アプリケーションが DB2 をストリーミングの OData データソースとして使用している場合、データ取得アクションの結果セットに同時行の変更が含まれないようにすることはサポートされていません。

### 5.5 非常に長い文字列の DISTINCT 属性を選択してください

サイズの文字列の DISTINCT 属性を選択する > 8168 文字は、CLOB データ型の DISTINCT 列を選択するという既知の DB2 制限のため、Mendix ではサポートされていません。 When you run into this limitation, you may encounter an exception in the logs with a message like this: `DB2 SQL Error: SQLCODE=-727, SQLSTATE=56098, SQLERRMC=2;-134;42907`
