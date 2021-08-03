---
title: "XPath 日付開始日"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-day-from-datetime.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`day-from-dateTime()` 関数は、 **Date and time** 属性から月の値の日を抽出し、値と比較するために使用することができます。

## 2つの例

このクエリは、 `DateAttribute` が月の 30 日になるすべてのログを返します(例えば、"2011-12-30")。

```java
//Logging.Log[day-from-dateTime(DateAttribute) = 30]
```
