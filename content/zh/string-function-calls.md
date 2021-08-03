---
title: "字符串函数调用"
parent: "表达式"
description: "描述转换和检查Mendix字符串的函数。"
---

## 1 导言

这些是转换和检查 [字符串](data-types) 的函数。 请注意，这些函数永远不会改变字符串本身，它们只会返回一个新的值。

字符串被引号包围。 如果字符串包含引用，它应该用另一个引用逃脱。 例如： `'这不是很有趣'`。

## 2 toLowerCase

将字符串中的所有字符转换为小写。

### 2.1 输入参数

* 要转换的字符串
* 类型：字符串

### 2.2 产出

相同字符串，只有所有小写。

```java
toLowerCase('thisISmyString')
```

返回：

```java
'thisismystring'
```

## 3 toUpperCase

将字符串中的所有字符转换为大写。

### 3.1 输入参数

* 要转换的字符串
* 类型：字符串

### 3.2 产出

相同字符串，只有所有大写。

```java
toUpperCase('thisISmyString')
```

返回：

```java
'THISISMYSTRING'
```

## 4 长度

确定字符串的长度。

### 4.1 输入参数

* 一个字符串
* 类型：字符串

### 4.2 产出

* 字符串长度
* 类型：整数

```java
长度('thisismystring')
```

返回：

```java
14
```

## 5 个子字符串

检索字符串的子字符串。 注意字符串的第一个字符位于位置 `'0'`, 最后一个字符位于位置 `长度(string)-1`

### 5.1 输入参数

* 议 题
   * 类型：字符串
* 子字符串的起始位置
   * 类型：整数
* 结果的预期长度 (可选)
   * 类型：整数

### 5.2 产出

原始字符串的一部分，从起始位置开始，长度等于理想长度。 它将返回一个从开始位置到结束字符串结尾的子字符串。

* 类型：字符串

```java
substring('thisismystring', 6)
```

返回：

```java
'mystring'
```

如果给出第三个参数，它将把返回的字符数限制为该数量：

```java
substring('thisismystring', 6, 2)
```

返回：

```java
'我'
```

如果此第三个参数太大，函数会导致一个错误，说它超出范围，所以请确保加以限制。 这是一个使用长度函数的示例：

```java
'substring' ('thisismystring', 0, min(length('thisismystring') - 1, 20)'
```

## 6 个找到

在字符串中查找第一次出现子字符串的位置。

### 6.1 输入参数

* 原始字符串，您想要搜索的字符串
    * 类型：字符串
* 您想要搜索的子字符串
    * 类型：字符串
* 开始位置从(可选) 开始搜索
    * 类型：整数

### 6.2 产出

原字符串中子字符串的第一个位置。 如果子字符串在原始字符串中根本没有发生，将返回 `'-1'`。

* 类型：整数

```java
find('thisismystring', 'my')
```

返回：

```java
6
```

在原始字符串中不发生的子字符串：

```java
find('thisismystring', '你的字符串')
```

返回：

```java
-1
```

第三个参数：

```java
find('thisismystring', 'i', 5)
```

返回：

```java
11
```

## 7 个查找最后一个

在原始字符串中查找最后一次出现子字符串的位置。

### 7.1 输入参数

* 原始字符串，您想要搜索的字符串
    * 类型：字符串
* 您想要搜索的子字符串
    * 类型：字符串
* 要搜索的最后位置(可选)
    * 类型：整数

### 7.2 产出

原字符串中子字符串的第一个位置。 如果子字符串在原始字符串中根本没有发生，将返回 `'-1'`。

* 类型：整数

```java
FindLast('thisismystring', 't')
```

返回：

```java
9
```

在原始字符串中不发生的子字符串：

```java
findLast('thisismystring', '你的字符串')
```

返回：

```java
-1
```

第三个参数：

```java
findLast('thisismystring', 'i', 5)
```

返回：

```java
4
```

## 8个包含

确定原字符串(第一个参数)是否包含子字符串(第二个参数)。

此表达式：

```java
包含('stringtosearchin', 'stringtosearchfor')
```

等于以下表达式：

```java
find('stringtosearchin', 'stringtosearchfor') != -1
```

搜索空变量或空字符串，就像 `$param = ''` 的表达式：

```java
包含('stringtosearchin', $param)
```

将返回真值。

{{% alert type="warning" %}}
这个功能是大小写的。
{{% /报警 %}}

### 8.1 输入参数

* 原始字符串，您想要搜索的字符串
    * 类型：字符串
* 您想要搜索的子字符串
    * 类型：字符串

### 8.2 产出

原字符串是否包含子字符串。

* Type: Boolean

```java
包含('thisismystring', 'my')
```

返回：

```java
true
```

## 9 个启动

确定字符串是否以指定的子字符串开始。

### 9.1 输入参数

* 原始字符串，您想要搜索的字符串
    * 类型：字符串
* 您想要搜索的子字符串
    * 类型：字符串

### 9.2 产出

原始字符串是否从子字符串开始。

* Type: Boolean

```java
startsWid('thisismystring', 'this')
```

返回：

```java
true
```

## 10 个终点

确定字符串是否以指定的子字符串结尾。

### 10.1 输入参数

* 原始字符串，您想要搜索的字符串
    * 类型：字符串
* 您想要搜索的子字符串
    * 类型：字符串

### 10.2 产出

原字符串是否以子字符串结尾。

* Type: Boolean

```java
endsWith('thisismystring', 'ring')
```

返回：

```java
true
```

## 11 trim

删除字符串开始和结束时的所有空格。

### 11.1 输入参数

* 一个字符串
* 类型：字符串

### 11.2 产出

相同的字符串，但在开始和结束时没有空格。

* 类型：字符串

```java
修剪(' 这是我的字符串 ')
```

返回：

```java
'这是我的字符串'
```

## 12 isMatch

检查字符串是否匹配给定的正则表达式。

### 12.1 输入参数

* 要尝试和匹配的字符串
    * 类型：字符串
* 匹配的正则表达式
    * 类型：字符串

{{% alert type="warning" %}}

请注意此函数调用使用当前平台提供的正则表达式语言：

* 当在 [微流程](microflow) 中使用时——Java 的正则表达式(详情，见 [类图案文档](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html))
* 当在 [条件格式化](conditions) 中使用时——JavaScript 的正则表达式(详情，见 [正则表达式文档](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions))

{{% /报警 %}}

### 12.2 产出

字符串是否匹配。

* Type: Boolean

此示例测试以查看字符串是否只包含数字

```java
isMatch('234hello6432', '^([0-9]+)$')
```

返回：

```java
错误
```

在 `isMatch()`, 正则表达式隐含在 `^` 和 `$` 中。

例如：

* `isMatch('NLG 123.45', '[0-9]')` 返回 false
* `isMatch('NLG 123.45', '.*[0-9].*')` 返回 true

NB 搜索空字符串：

* `isMatch('', '.*[0-9].*')` 返回 false

## 全部替换13个

用另一个字符串替换正则表达式的所有出现。

### 13.1 输入参数

* 要搜索的字符串
    * 类型：字符串
* 匹配的正则表达式
    * 类型：字符串
* 重置值
    * 类型：字符串

{{% alert type="warning" %}}

请注意此函数调用使用当前平台提供的正则表达式语言：

* 当在 [微流](microflows) 中使用时——Java 的正则表达式(详情，见 [类模式](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html))
* 当在 [条件格式化](conditions) 中使用时——JavaScript 的正则表达式(详情请见 [正则表达式](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions))

{{% /报警 %}}

### 13.2 产出

原始字符串，所有正则表达式都被替换字符串所取代。 如果在字符串中没有出现正则表达式，则返回原始表达式。

* 类型：字符串

```java
全部替换('这是一个字符串，75个数字被抛入', '([0-9])', 'NUMBER')
```

返回：

```java
'这是一个带有NUMBERNUMBER的字符串，一些数字已经扔进”
```

没有匹配项：

```java
全部替换('这是一个没有输入数字的字符串', '([0-9])', 'NUMBER')
```

返回：

```java
'这是一个没有出现数字的字符串'
```

## 14个替换在前

用替换字符串替换正则表达式的第一次出现。

### 14.1 输入参数

* 要搜索的字符串
    * 类型：字符串
* 匹配的正则表达式
    * 类型：字符串
* 重置值
    * 类型：字符串

{{% alert type="warning" %}}

请注意此函数调用使用当前平台提供的正则表达式语言：

* 当在 [微流程](microflow) 中使用时——Java 的正则表达式(详情，见 [类图案文档](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html))
* 当在 [条件格式化](conditions) 中使用时——JavaScript 的正则表达式(详情，见 [正则表达式文档](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions))

{{% /报警 %}}

### 14.2 产出

原始字符串，所有正则表达式都被替换字符串所取代。 如果在字符串中没有出现正则表达式，则返回原始表达式。

* 类型：字符串

```java
首次替换('这是一个字符串，75个数字被抛入', '([0-9])', 'NUMBER')
```

返回：

```java
'这是一个带有NUMBER5的字符串，一些数字被扔进了'
```

## 15 字符串连接 ( + )

`+` 操作员可以用来把两个字符串或一个字符串和一个数字。

### 15.1 输入参数

* 第一个参数
    * 类型：字符串、整数/长、 浮点或小数
* 第二个参数
    * 类型：字符串、整数/长、 浮点或小数

至少一个参数必须是类型字符串。

### 15.2 产出

一个新的字符串是两个输入参数的字面汇合。

* 类型：字符串

合并两种严格：

```java
'foo' + 'bar'
```

返回：

```java
'foobar'
```

合并字符串和号码：

```java
4.73+' 千米
```

返回：

```java
“4.73公里”
```

## 16 <a name="urlEncode"></a>urlEncode

将一个字符串转换为URL。 当您想要使用字符串作为URL的一部分时，此函数是有用的。

例如：

```java
'http://google.com/search?q=' + urlEncode($myQuery)
```

### 16.1 输入参数

* 要转换的字符串
* 类型：字符串

### 16.2 产出

字符串，URL编码。

```java
urlEncode('Hello, world!')
```

返回：

```java
'Hello%2C+ world%21'
```

## 17 urlDecode

从URL转换字符串。 [urlEncode](#urlEncode) 相反.

### 17.1 输入参数

* 要转换的 URL 编码字符串
* 类型：字符串

### 17.2 产出

字符串，URL解码。

```java
urlDecode('Hello%2C+ world%21')
```

返回：

```java
'你好，世界！'
```
