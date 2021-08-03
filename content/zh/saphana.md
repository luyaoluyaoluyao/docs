---
title: "SAP HANA"
parent: "数据存储"
menu_order: 70
---

## 1 导言

Mendix 使用 SAP HANA 数据库的行为与使用 PostgreSQL 数据库相比有一些小的差异。 下文记录了这些差异。

## 2 按关联属性排序

获取一个按一个相关实体的属性分类的实体，在SAPHANA中不支持。

例如， 您有两个相关实体 — **人员** 和 **地址** — 他们有 **名称** 和 **街道** 属性, 分别为之。 您无法获取 `个人` 个物件排序到 `Person_Address/stread`。

## 3 个案例灵敏度

SAP HANA在进行字符串比较和检查时是区分大小写的。 当使用诸如 `contains()`, `starts-with()`, 这一点很重要。 和 `尾声不含()`, 或使用等价(`=`) 或不等价(`!`XPath 约束的运营商。

例如， `包含('OneTwo', 'one')` 将返回 `fals`。

## 无限的 & 非常长的字符串行为

### 4.1 比较职能

SAPHANA不支持不限字符串或字符串，指定长度超过5000个字符，当使用等效的 (`=`)或不等于 (`！`XPath 约束的运营商。 然而，它确实支持函数包括 `contains()`, `starts-with()`, 和 `ends-with()`。

### 4.2 排序，分组 & 聚合

无法排序、群组。 或在不限字符串或字符串上使用总合函数，如 `count()`。 这是因为这么长或无限的字符串是用数据类型 CLOB 实现的。 考虑缩短字符串属性的长度或从数据网格中移除。

### 4.3 选择DISTINCT 属性

选择大小大于5000个字符的字符串类型的DISTINCT 属性不被Mendix 支持，因为已知的 SAPHANA 限制选择带有CLOB 数据类型的DISTINCT 列。

## 5 已知问题

### 5.1 Unicode 支持

目前只支持 [个多语言基本板块](https://en.wikipedia.org/wiki/Plane_(Unicode)#Basic_Multilingual_Plane) Unicode 字符。
