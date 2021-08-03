---
title: "XPath 時間 - 日付時間"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-hours-from-datetime.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`hours-from-dateTime()` 関数は、 **Date and time** 属性から hours の値を抽出し、値と比較するために使用します。

## 2つの例

このクエリは、 `DateAttribute` の時間部分が 8 のすべてのログを返します(例: "2011-12-30 08:00:00")。

```java
//Logging.Log[hours-from-dateTime(DateAttribute) = 8]
```
