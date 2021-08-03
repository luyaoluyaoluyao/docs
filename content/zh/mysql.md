---
title: "MySQL/MariaDB"
parent: "数据存储"
menu_order: 50
tags:
  - "studio pro"
---

## 1 导言

如果您正在使用 MySQL 或 MariaDB 数据库实现Mendix 应用，您需要考虑一些额外的考虑。 此外，Mendix 使用 MySQL 或 MariaDB 数据库的行为与使用 PostgreSQL 数据库相比有一些小的差异。

下文记录了这些考虑因素和分歧。

## 2 个存储引擎

Mendix 只支持 InnoDB 存储引擎，启用了基于行的日志记录。

## 3 个交易隔离。

Mendix 默认使用 `读取提交的` 交易隔离等级。 在这个交易隔离级别的情况下，只能使用基于行的日志记录。 您应该将 `binlog_format` 数据库配置值设置为 `ROW` 或 `MEXED`。 欲了解更多信息，请访问 [`binlog_format` for MySQL](https://dev.mysql.com/doc/refman/5.7/en/replication-options-binary-log.html#sysvar_binlog_format) 或 [`binlog_format` for MariaDB](https://mariadb.com/kb/en/mariadb/replication-and-binary-log-server-system-variables/#binlog_format)。

## 4 SAVEPOINT 异常不存在

如果您收到一个未命名的 `SAVEPOINT 不存在` 例外情况，就会出现僵局。 Mendix 无法正确处理此情况，因为MySQL/MariaDB 会自动回滚交易并删除该交易的所有保存点。 Mendix 试图回退到一个特定的保存点，但MySQL 和 MariaDB 不再允许这一点。 建议尽可能缩短交易时间，以避免僵局。

## 5 时区支持

Mendix 支持在查询中提取部分日期和时间的功能。 在 XPath，您可以使用如下功能： [`小时从日期时间`](xpath-hours-from-datetime) 和 [`周从日期时间起`](xpath-week-from-datetime) 在 OQL 中，您可以使用如下功能： [`DATEPART(...)`](oql-datepart) 和 [`DATEF(...)`](oql-datediff)

在 Mendix 中，日期时间存储在 UTC 时区。 要使这些函数正常工作，数据库必须支持将日期和时间从 UTC 转换到另一个时区。 如果不可能，函数将在UTC 时区的日期和时间运行。 如果用户期望在他们的时区工作日期，这可能导致错误的结果。

MySQL 不完全支持时区从箱外转换。 您必须填写一些时区表 (详情请参阅 [10.6 MySQL 服务器时区支持](http://dev.mysql.com/doc/refman/5.5/en/time-zone-support.html))。 如果您不在查询中使用这种功能，您无需这样做。 或者如果您总是想使用 UTC 日期和时间。

MariaDB 支持时区转换的相同配置。

## 6个数据库创建

要创建一个新的 MySQL 数据库，用户必须有足够的访问权限才能创建数据库。
