---
title: "XPath Quarter-from-DateTime"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-quarter-from-datetime.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`quaret-from-dateTime()` 関数は、 **Date and time** 属性に対応する四半期を抽出し、値と比較するために使用することができます。

## 2つの例

このクエリは、 `DateAttribute` が四半期にあるすべてのログを返します(たとえば、"2011-12-30")。

```java
//Logging.Log[quaret-from-dateTime(DateAttribute) = 4]
```
