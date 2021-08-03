---
title: "XPath には以下を含みます"
parent: "xpath-constraint-functions"
---

## 1つの概要

`contains()` 関数は、string 属性に特定の文字列 (大文字と小文字を区別しない) が含まれているかどうかをテストします。

## 2つの例

このクエリは、名前が文字列 `an` を含むすべての顧客を返します:

```java
//Sales.Customer[contains(Name, 'an')]
```

"andy" や "Jan" という名前のお客様は、"an" がその名前の一部であるため、例えば返却されます。