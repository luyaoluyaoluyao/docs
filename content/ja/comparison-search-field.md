---
title: "比較検索フィールド"
parent: "検索バー"
---


## 共通のプロパティ

{{% snippet file="refguide7/Search+Field+Caption+Property.md" %}}

{{% snippet file="refguide7/Search+Field+Type+Property.md" %}}

{{% snippet file="refguide7/Search+Field+Default+Value+Property.md" %}}

{{% snippet file="refguide7/Search+Field+Custom+Date+Format+Property.md" %}}

{{% snippet file="refguide7/Custom+Date+Format+Tokens.md" %}}

{{% snippet file="refguide7/Search+Field+Placeholder+Property.md" %}}

## 一般プロパティ

{{% snippet file="refguide7/Search+Field+Attribute+Path+Property.md" %}}

{{% snippet file="refguide7/Search+Field+Comparison+Property.md" %}}

### 日付の比較とデフォルト値の影響

日付の属性を等価で検索することができます。 日付に属する時刻コンポーネントは、比較検索フィールドのデフォルト値に依存します。

| 既定値                   | 検索クエリ                                                 |  | 結果例 (input: August 4, 2100)                   |
| --------------------- | ----------------------------------------------------- |  | --------------------------------------------- |
| なし                    | 検索フィールドが空です。 指定された日付の深夜から始まる24時間の日付の範囲を表します。          |  | 8月4日0:00~8月5日0:00の間で検索                        |
| [%CurrentDateTime%]   | 検索フィールドに現在の日付が表示されます。 _現在時刻_から始まる24時間の日付範囲を表します。      |  | 8月4日から検索 <current time> -8月 5日 <current time> |
| [%BeginOfCurrentDay%] | 検索フィールドに現在の日付が表示されます。 指定された日付の深夜から始まる24時間の日付の範囲を表します。 |  | 8月4日0:00~8月5日0:00の間で検索                        |
