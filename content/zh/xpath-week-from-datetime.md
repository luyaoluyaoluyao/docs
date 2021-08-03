---
title: "XPath 周，从日期开始"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-week-from-datetime.pdf)。
{{% /报警 %}}

## 1 概览

`week-fro-dateTime()` 函数从 **日期和时间(年份)中提取每周数字** 属性，以便它可以与一个值进行比较。 值介于 1 到 53 之间。

{{% alert type="warning" %}}
返回的值取决于你的 *数据库* 用于支持你的 Mendix 应用程序。 它不 ** 不会考虑应用程序的运行时间设置 **周的第一天**。

许多数据库实现 [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)，但请参阅您正在使用的数据库的文档以找到准确的细节。
{{% /报警 %}}

## 2 个示例

此查询返回当年第二周的日期 `日期属性` 的所有日志(例如，"2011-01-13")：

```java
//Logging.log[周起-日期时间(DateAttribute) = 2]
```

## 3 阅读更多

以下链接是如何计算Mendix所用许多数据库的特定日期的周号的相关文件。

用于测试本地使用 JVM 的 [日历.WEEEK_OF_YEAR](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/Calendar.html) 的 HSQLDB 数据库。

PostgreSQL、 Oracle和 MySQL 跟随 [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601):

* [PostgreSQL](https://www.postgresql.org/docs/11/functions-datetime.html)
* [Oracle](https://docs.oracle.com/cd/B28359_01/olap.111/b28126/dml_commands_1029.htm#OLADM780)
* [MySQL](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html#function_week)

其他数据库有更具体的行为：

* [SQL 服务器](https://docs.microsoft.com/en-us/sql/t-sql/functions/datepart-transact-sql?view=sql-server-ver15)
* [DB2](https://www.ibm.com/support/knowledgecenter/en/SSEPEK_10.0.0/sqlref/src/tpc/db2z_bif_week.html)
