---
title: "作成日"
parent: "表現"
---

特定の日付の日付型変数は [parseDateTime](parse-and-format-date-function-calls) を使用して作成できます。 日付文字列と書式文字列をパラメータとして取り、日付型変数を返します。 詳細については、 [parseDateTime](parse-and-format-date-function-calls) を参照してください。

日付を表す文字列変数は `dateTime` および `dateTimeUTC` 関数で作成できます。 The difference between these two functions is that `dateTime` uses the calendar of the session used in the function call, and `dateTimeUTC` uses the UTC calendar. システムセッションはデフォルトでUTCとして実行されますが、これは [プロジェクト設定](project-settings)で設定できます。

これらの関数は1~6個の入力パラメータをとり、文字列を返します。 以下は順番に表しています:

1. 年
    * 型: 整数、4桁、1799 より大きい
2. ヶ月
    * タイプ: 整数、1 から 12 の間の値
3. 日数
    * タイプ: 1 から 31 の間の整数。
4. 時間
    * タイプ: 0 から 23 の間の整数。
5. 分
    * 型: 0 から 59 の間の整数。
6. 秒
     * 型: 0 から 59 の間の整数。

1つのパラメータ:

```java
dateTime(2007)
```

戻り値:

```java
"Mon Jan 01 00:00:00 CET 2007"
```

2つのパラメータ:

```java
dateTime(2007年, 1)
```

return:

```java
"Mon Jan 01 00:00:00 CET 2007"
```

3つのパラメータ:

```java
dateTime(2007年, 1, 1)
```

return:

```java
"Mon Jan 01 00:00:00 CET 2007"
```

4つのパラメータ:

```java
dateTime(2007年, 1, 1, 1)
```

return:

```java
"Mon Jan 01 01:00:00 CET 2007"
```

5つのパラメータ:

```java
dateTime(2007年, 1, 1, 1, 1)
```

return:

```java
"Mon Jan 01 01:01:00 CET 2007"
```

6つのパラメータ:

```java
dateTime(2007年, 1, 1, 1, 1, 1, 1)
```

return:

```java
"Mon Jan 01 01:01:01 CET 2007"
```
