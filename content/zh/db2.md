---
title: "DB2"
parent: "数据存储"
menu_order: 40
---

## 1 导言

如果您正在使用 DB2 数据库实现Mendix 应用，您需要考虑一些额外的考虑。 此外，Mendix 使用 DB2 数据库的行为与使用 PostgreSQL 数据库相比有一些较小的差异。

下文记录了这些考虑因素和分歧。

## 2 表空间的页面大小

Mendix 在 DB2 上运行 非常重要的是，用户表空间的页面大小至少为8K(但最好是32K)。 这是因为Mendix 使用了国家字符串(NVARCHAR 或 VARCHAR 使用字符串单位 CODEUNT32)。 此数据类型消耗的空间多于八进制VARCHAR。 对于系统管理，Mendix 总是创建一些带索引的表格，这些表格至少需要8K的表空间。

**SQL 代码 `-614 异常`**

如果索引太大，DB2会异常： `com.ibm.db2.jcc.am.SqlException: DB2 SQL 错误：SQLCODE=-614, SQLSTATE=54008, SQLERRMC=some _index_name`

对于用户创建的索引，如果索引中指定列的总长度大于最大键长度， 您还应该增加表格的页面空间大小。

更详细的信息 查看 [SQL0614N - 索引或索引扩展索引名称无法创建或更改，因为指定列的合并长度过长](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.db2.luw.messages.sql.doc/doc/msql00614n.html) 在 *SQL 消息* *IBM 知识中心* 中的部分</em>

## 3 个交易日志大小

**SQL 代码 `-964 异常`**

如果交易日志空间已经枯竭，或者现行交易数量暂时增加， DB2 会抛出此异常： `com。 bm.db2.jcc.am.SqlException: DB2 SQL 错误：SQLCODE=-964, SQLSTATE=57011, SQLERRMC=null`

在这种情况下， *LOGPRIMARY* 的大小必须增加。

欲了解更多详细信息，请参阅 [DB2 SQL 错误：SQLCODE: -964, SQLSTATE: 57011, SQLERRMC: null](http://www-01.ibm.com/support/docview.wss?uid=swg21298630) on the *IBM Support* pages and [SQL0964C - 数据库的交易日志完整](http://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.db2.luw.messages.sql.doc/doc/msql00964c.html) in *SQL message* section of the *IBM 知识中心*

## 4 使DB2案例不敏感。

当对字符串列值进行排序时，DB2也会考虑到字母情况。 然而，如果DB2数据库是在对案件不敏感的情况下建立的，就可以避免这种情况。

欲了解更多详情，请参阅 *IBM Developer Work* 中的文章 [使得DB2 案例不敏感](http://www.ibm.com/developerworks/data/library/techarticle/0203adamache/0203adamache.html)

## 5 已知问题

### 5.1 按非常长的字符串排序

无法对无限字符串或字符串进行排序，其长度超过8192个字符。 这是因为这么长或无限的字符串是通过数据类型NCLOB实现的。 DB2 不允许在此数据类型的列中排序。 从技术上讲，可以在执行查询时将此类型投射到正常的 VARCHAR 类型和排序。 但这会增加执行时间。 问题是，在数据网格中显示这么长的字符串是否真的便于使用。 考虑缩短字符串属性的长度或从数据网格中移除。

### 5.2 由一个相关的Scalar Fullselect 或一个具有外部动作的函数

根据 [逐个排序](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.sql.ref.doc/doc/r0059211.html) 文档 *IBM DB2 SQL 引用*DB2 不支持完全选择相关比例的 ORDER (SQLSTATE 42703) 或具有外部动作(SQLSTATE 42845)。

考虑到这个限制，当Mendix 应用程序由 DB2 支持时，不支持按相关属性排序。 因此， 用于排序的任何相关属性都是从查询中过滤出来的，结果集是返回的，好像在查询中没有显示相关属性的排序一样。

### 5.3 OData无阻挡读取孤立流

根据 [隔离级别](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.db2.luw.admin.perf.doc/doc/c0004121.html) 文档在 *IBM DB2 应用程序设计*中，DB2 不支持非屏蔽的孤立查询。 DB2的默认行为是当一个用户从表中检索行，而另一个用户同时在同一个表上进行修改。 然后这些修改将显示在检索查询中的数据中(这意味着数据库读取不是孤立的)。 配置更严格的交易隔离级别以防止这种行为将锁定在同一行上(这意味着同时的数据库操作正在被阻止)。

考虑到这一限制， 当Mendix 应用程序使用 DB2 作为流媒体OData 数据源时，不支持同时进行行修改。

### 5.4 选择非常长字符串的 DISTINCT 属性

选择 DISTINCT 属性的字符串大小 > 8168 个字符不被Mendix 支持，因为已知的DB2 限制选择带有CLOB 数据类型的DISTINCT 列。 当您进入此限制时， 你可能会遇到日志中的异常，比如这样的消息： `DB2 SQL 错误：SQLCODE=-727, SQLSTATE=56098, SQLERRMC=2; 134;42907`
