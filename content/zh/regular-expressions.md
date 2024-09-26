---
title: "正则表达式"
parent: "资源"
menu_order: 70
tags:
  - "studio pro"
  - "正则表达式"
  - "正则表达式"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/regular-expressions.pdf)。
{{% /报警 %}}

## 1 导言

正则表达式资源文档用于实体的 [验证规则](validation-rules) 以描述字符串必须匹配的一组标准。

正则表达式有下面描述的属性。

## 2 常用的

### 2.1 名称

名称可以用来指实体的 [验证规则](validation-rules) 的正则表达式。

### 2.2 文件

这只是为了文件的目的；在你正在模拟的最终用户应用程序中是不可见的。

## 3 表达式{#expression}

这个表达式定义了一个标准，即一个字符串应该用一个 [正式的、国际标准化的正则表达式语言](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html) 来对照.

{{% alert type="info" %}}

例如，查看荷兰邮编的表达式可以是： `[1-9][0-9][0-9][0-9] ?[A-Za-z][A-Za-z]`。

这里有两个帖子代码示例： **3072AP** and **7500 AH**。

这些标准是：

* 第一个字符是介于 1 到 9 范围内的数字
* 第二个字符、第三个字符和第四个字符是在0到9个字符之间
* 最后两个字符是字母，最后两个子表达式 [A-Za-z]表示， 表示最后两个字符应该在范围 A-Z 或范围 a-z
* 在数字和字母之间可以有一个由空格和问题标记组成的子表达式所表示的空格； 问题标记表示空间是可选的

{{% /报警 %}}

以下各节概述了可以在 Mendix 中使用的正则表达式。 此描述也适用于正则表达式字符串，如 *isMatch()*。

### 3.1 Subexpressions

正则表达式由子表达式的序列组成。 一个字符串匹配正则表达式，如果字符串的所有部分以相同的顺序匹配这些子表达式。

正则表达式可以包含下列子表达式类型：

* `[ ]` -- 括号中的表达式匹配方括号中显示的单个字符，例如：
    * `[abc]` 匹配"_a_", "_b_", 或 "_c_"
    * `[a-z]` 指定了一个范围匹配来自"_a_到 "_z_ 的小写字母

    ●{% alert type="info" %}}这些表格可以混合： `[abcx-z]` 匹配"_a_", "_b_", "_c_", " "_x_", "_y_", or "_z_", 等于 `[a-cx-z]`。 `-` 字符被当作字面字符处理，如果它是括号内的最后一个或第一个字符， 或者如果它因反斜杠而逃脱(`\`)。
    {{% /报警 %}}

* `[^]` — 匹配一个不包含在括号内的单个字符，例如：
    * `[^ abc]` 匹配除"a"、"b"或"c"以外的任何字符
    * `[^a-z]` 匹配任何一个字符，它们不是一个小写字母从 "a" 到 "z"

    * E/C{% alert type="info" %}}As above, lital 字符和范围可以混合在一起。
    {{% /报警 %}}

* `{m,n}` - 匹配前面的元素至少 _m_ 且不超过 _n_ 次, 例如:

    * `a{3,5}` 只匹配"_aa_",_aaa_", and "_aaaa_"
* `{n}` - 匹配上一个元素的 n 次, 例如:

    * `[1-9][0-9]{3} ?[A-Za-z]{2}` 是写入表达式以检查上面的示例中的荷兰邮政编码
* `.` — 一个点匹配任何单个字符； 如果你想要匹配一个点, 你可以用 `来前缀它` (ackslash)
* 字数字符 — — 这是一个在正则表达式语言中没有特殊意义的字符，它匹配着自己； 这实际上是除了 `\[](){}^-$? +|。`, 例如:
    * 荷兰邮编示例中的 *`空格`* 是一个只匹配自身的字体字符

    {{% alert type="info" %}}If you need to match one of the characters which is not a literal, prefix it with a backslash (`\`).
    {{% /报警 %}}

* `\w` — — 单词：字母、 数字或下划线; `\w` 是 `[A-Za-z0-9_]` 的缩写
* `\d` — — 一个数字" 为 `[0-9]` 的缩写

### 3.2 定量器

子表达式在字符串中可能出现的次表达式的次数由子表达式之后的量化表示. 如果没有量化器，子表达式必须出现一次。

可以使用下列量化器：

| Quantifier | 描述                     |
| ---------- | ---------------------- |
| ?          | 上述子词不应出现，也不应重复出现。      |
| *          | 上面的子表达式发生任何次数。         |
| +          | 上一个子表达式应该出现一次或多次。      |
|            | 没有量化表示上面的子表达式应该准确出现一次。 |

## 4 阅读更多

* [班级模式](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html#matches-java.lang.String-java.lang.CharSequence-) - 从 Oracle Java SE 文档中获取的信息
* [在 Java 中使用正则表达式](http://www.regular-expressions.info/java.html)  - 来自 *Regular-Expressions.info 的 Java 中有关正则表达式的信息* 网站
