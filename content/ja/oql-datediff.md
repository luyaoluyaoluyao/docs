---
title: "OQL DATEDIFF"
parent: "oql-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-datedeiff.pdf) をクリックしてください。
{{% /alert %}}

DATEDIFF関数は、指定された2つの日付/時刻の値の差を返します。 指定された単位で差分が与えられます。

構文は以下の通りです:

```
DATEDIFF ( 単位 , startdate_expression , enddate_expression )
```

**単位**

取得する日付/時刻の値の単位を指定します。 これは次のいずれかになります。

`YEAR`, `QUARTER`, `MONTH`, `DAY`, `WEEK`, `HOUR`, `MINUTE` or `SECOND`.

**startdate_expression** 計算されている期間の開始日を指定します。 これは、日付/時刻の値を解決する式でフォーマットされる必要があります。

**enddate_expression** 計算されている期間の終了日を指定します。 これは、日付/時刻の値を解決する式でフォーマットされる必要があります。
