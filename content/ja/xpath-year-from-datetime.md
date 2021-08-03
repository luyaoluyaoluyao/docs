---
title: "XPath Year-from-DateTime"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-year-from-datetime.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`year-from-dateTime()` 関数は、 `Date and time` 属性から年数を抽出し、値と比較するために使用することができます。

## 2つの例

このクエリは、 `DateAttribute` の年数が "2011" であるすべてのログを返します(例: "2011-12-30")。

```java
//Logging.Log[year-from-dateTime(DateAttribute) = 2011]
```
