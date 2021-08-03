---
title: "作成日"
parent: "表現"
menu_order: 90
tags:
  - "studio pro"
  - "表現"
  - "日付の作成"
  - "表現"
---

## 1つの紹介

日付は `dateTime` および `dateTimeUTC` 関数で作成できます。 The difference between them is that  `dateTime` uses the calendar of the session used in the function call, and `dateTimeUTC` uses the UTC calendar. システムセッションは、スケジュールされたイベントを除き、デフォルトでUTCとして実行されます。 これは、 [アプリ設定](project-settings#scheduled) の **スケジュールされたイベント タイム ゾーン** セクションで設定できます。

この関数は、変数または属性パラメータを受け付けず、固定値のみを受け付けます。 パラメータを使用して日付を作成するには、 [parseDateTime](parse-and-format-date-function-calls#parsedatetime-utc) 関数を使用します。

## 2値

これらの関数は、次の順序で入力値を 1 つから 6 つの間で取ります。

1. 年 (型: 整数、4桁、1799年より大きい)
2. months (type: integer, between 1 and 12)
3. days (type: integer, between 1 and 31)
4. hours (type: integer, between 0 and 23)
5. 分 (0から59の間の整数)
6. seconds (type: integer, between 0 and 59)

## 3つの例

以下の例は、式が返す値を示しています。

* 入力として1つの値を指定した場合:

    ```java
    dateTime(2007)
    ```

    式は次の出力を返します:

    ```java
    "Mon Jan 01 00:00:00 CET 2007"
    ```

* 入力として2つの値を指定した場合:

    ```java
    dateTime(2007年, 1)
    ```

    式は次の出力を返します:

    ```java
    "Mon Jan 01 00:00:00 CET 2007"
    ```

* 3つの値を入力として指定した場合:

    ```java
    dateTime(2007年, 1, 1)
    ```

    式は次の出力を返します:

    ```java
    "Mon Jan 01 00:00:00 CET 2007"
    ```

* 入力として4つの値を指定した場合:

    ```java
    dateTime(2007年, 1, 1, 1)
    ```

    式は次の出力を返します:

    ```java
    "Mon Jan 01 01:00:00 CET 2007"
    ```

* 入力として5つの値を指定した場合:

    ```java
    dateTime(2007年, 1, 1, 1, 1)
    ```

    式は次の出力を返します:

    ```java
    "Mon Jan 01 01:01:00 CET 2007"
    ```

* 6つの値を入力として指定した場合:

    ```java
    dateTime(2007年, 1, 1, 1, 1, 1, 1)
    ```

    式は次の出力を返します:

    ```java
    "Mon Jan 01 01:01:01 CET 2007"
    ```
