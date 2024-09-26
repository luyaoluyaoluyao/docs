---
title: "XPath Minutes-from-DateTime"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-minutes-from-datetime.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`minutes from-dateTime()` 関数は、 **Date and time** 属性から分数の値を抽出し、値と比較するために使用することができます。

## 2つの例

このクエリは、 `DateAttribute` の分部分が 30 になっているすべてのログを返します(例: "2011-12-30 08:30:00" )。

```java
//Logging.Log[minutes-from-dateTime(DateAttribute) = 30]
```
