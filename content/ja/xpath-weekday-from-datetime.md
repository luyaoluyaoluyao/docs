---
title: "XPath 平日から日付時間"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-weekday-from-datetime.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`weekday-from-dateTime()` 関数は、 **Date and time** 属性から、曜日の日を数値として抽出し、値と比較するために使用することができます。 値は 1 から 7 の範囲です。 (1 = 日曜日、7 = 土曜日)。

## 2つの例

このクエリは、 `DateAttribute` の週の曜日が 6 (金曜日) のすべてのログを返します。

```java
//Logging.Log[weekday-from-dateTime(DateAttribute) = 6]
```
