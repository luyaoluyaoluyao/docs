---
title: "XPath の日付開始日"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-day-of-year-from-datetime.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`year-of-dateTime()` 関数は、 **Date and time** 属性から年の日を抽出し、値と比較するために使用することができます。 値は 1 (1 月 1日) から 366 (うるう年のため) の範囲です。

## 2つの例

このクエリは、 `DateAttribute` の年の日付が 30 であるすべてのログを返します(例: "2011-01-30" と "2012-01-30" )。

```java
//Logging.Log[year-of-dateTime(DateAttribute) = 30]
```
