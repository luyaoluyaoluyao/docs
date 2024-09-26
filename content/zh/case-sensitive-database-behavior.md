---
title: "区分大小写的数据库行为"
parent: "数据存储"
tags:
  - "studio pro"
  - "字符串"
  - "排序"
  - "大小写"
  - "查询"
  - "约束"
menu_order: 20
---

## 1 导言

对大小写敏感的字符串操作是将大小写视为不同字母的那些操作。 在查询中影响字符串的操作(例如在 XPath 约束内的操作)可能是区分大小写或不区分大小写的，取决于数据库供应商。 版本，Mendix 应用程序使用的配置。

还必须指出，每次执行对案件不敏感的行动都可能不同地对待案件的正常化。 一般来说，正常化是以地方为基础的。 这要么在数据库/表格中明确指明，要么从操作系统推断出数据库。 This normalization of letters, or case folding, is further described in [Case Folding](https://www.w3.org/International/wiki/Case_folding) on the *World Wide Web Consortium* wiki.

为了本文件的目的，我们可以将案件敏感操作分为三类：

* 排序：指示您想要检索对象的顺序(按字母顺序升序或降序)。
* 比较：这些是直接在查询中包含平等或其他比较的操作(例如，在查询 `\\Entity[attribute = 'a']`)
* 字符串函数：这些函数是 [包含](xpath-contains), [开始使用](xpath-starts-with), 和 [结尾的 XPath](xpath-ends-with) 函数。

除非下面另有说明，字符串的排序和比较是区分大小写的，而字符串函数则不区分大小写。 这受到数据库、表格或栏目整理的影响，有时也受到其他数据库特定选项的影响。 现有的整理和备选办法是卖方（有时是版本）的具体情况。

## 2 按数据库类型区分大小写敏感性的行为

下面的部分描述Mendix支持的数据库的默认行为。

### 2.1 HSQLDB

**用于排序、比较和字符串函数的** 案例不敏感。

### 2.2 POSTGRESQL

排序和比较是 **个大小写敏感的**。 无法配置它们。

字符串函数是 **个案不敏感的** ，因为它们是使用 `ILIKE` SQL 操作员实现的。

### 2.3 DB2

截至版本 [8.14.0](/releasenotes/studio-pro/8.14), 排序和比较 **区分大小写**. 对于低于8.14的版本，所有操作都是 **大小写敏感的**。 两个版本组都有异常，校验被配置为 **大小写不敏感的**，这影响到所有操作。 欲了解更多信息，请参阅 *DB2* 的 [Making DB2 案例不敏感](db2#making) 部分。

不支持按无限长度的字符串属性排序。

### 2.4 MARIADB & MYSQL

所有操作都取决于配置的校验. 当使用 `utf8` 字符集时，默认校验是 `utf8_general_ci` 。 或 `latin1_swedish_ci` 当使用 `latin1` 字符集时。 这些默认的校验都不敏感的 **案例**。

### 2.5 ORACLE

排序和比较取决于配置的校验. 默认校验是 `二进制`, 它是 **大小写敏感的**, 但是一个 `binary_ci` 可用来进行不敏感的操作。

可以通过设置 `NLS_SORT` 和 `NLS_COMP` "语言排序参数"来设置不同的组合来排序和比较操作。

不支持对无限长度的字符串属性进行比较。

字符串函数通过使用数据库的 `UPPER` 函数转换所有字母到大写来实现， 因此， **案例不敏感** 并且对执行他们的 `区域` 无动于衷。

### 2.6 SAP HANA

不支持对无限长度的字符串属性进行排序或比较。

### 2.7 SQL 服务

所有操作都取决于整理。 默认推荐的校验是 `SQL_Latin1_General_CP1_CI_AS`。 更多信息 请参阅我们关于 [设置一个新的 SQL Server 数据库](/developerportal/deploy/setting-up-a-new-sql-server-database) 和 Microsoft 文档 [Windows 整理名称](https://docs.microsoft.com/en-us/sql/t-sql/statements/windows-collation-name-transact-sql) 的指南。

## 3 默认情况敏感性概述

此表以不同数据库类型显示默认大小写敏感度：

|       **数据库类型** | **比较** | **排序中** | **字符串函数** |
| ---------------:|:------:|:-------:|:---------:|
|           HSQDB |   一    |    一    |     一     |
|      POSTGRESQL |   秒    |    秒    |     一     |
|             DB2 |   秒    |  烧结厂1   |    I3     |
| MARIADB & MYSQL |   C    |    C    |     C     |
|              排行 |   C1   |    C    |     一     |
|        SAP HANA |  烧结厂1  |  烧结厂1   |    I2     |
|          SQL 服务 |   C    |    C    |     C     |

如果字母具有以下意义：

* **S** — — 大小写敏感的
* **C** - 依赖于整理/配置
* **我** — — 大小写不敏感的

1操作不支持无限长度字符串。 2From Mendix 版本 8.11.0 3From Mendix 版本 8.14.0
