---
title: "XPath 约束"
parent: "xpath"
tags:
  - "studio pro"
---

## 1 导言

一个约束可以添加到任意Xpath 查询中，以筛选检索到的数据。 它应该始终采取有效的 [表达式](xpath-expressions) 的形式。 这应该包含一个或多个变量与 [运算符](xpath-operators), [函数](xpath-constraint-functions), [关键字或系统变量](xpath-keywords-and-system-variables)

例如，此查询会检索名称等于Jansen的所有客户：

```java
//Sales.Customer[name = 'Jansen']
```

The first half of the query is responsible for defining the entity to retrieve and the second half (between the brackets ) *constrains* the data to a certain attribute. 请注意，制约因素是(而且应当始终是)括号内的内容。

多个约束可以添加到单个查询中，除了 `id` 查询以外，所有查询都是如此。 最常见的做法是在第一个方括号关闭后开辟一组新的括号。

{{% alert type="warning" %}}
在 Studio Pro，您不会写完整的查询，仅限限制。 实体是由上下文隐含地确定的。 因此，取代 `//Sales.Customer[Name='Jansen'`, 你只需要在客户上写 `[Name='Jansen' ]`。 在 Java 中，您确实需要写整个查询，包括双斜线 (`//`) 和实体名称。
{{% /报警 %}}

## 2 示例

此查询检索所有名称等于Jansen和居住在鹿特丹的客户：

```java
//Sales.Customer[name = 'Jansen'] [Sales.Customer_Address/Sales.Address/City = '鹿特丹]
```

还可以将约束与 `和` 或 `或` [操作员](xpath-operators) 结合起来。 此查询可以检索所有其名字等于Jansen *和* 的鹿特丹的客户：

```java
//Sales.Customer[name = 'Jansen' and Sales.Customer_Address/Sales.Address/City = '鹿特丹']
```

此查询可检索所有名为Jansen或居住在鹿特丹的客户。

```java
//Sales.Customer[name = 'Jansen' or Sales.Customer_Address/Sales.Address/City = '鹿特丹']
```

用括号来划分制约因素，以确定优先次序。 此查询可以检索所有不仅被命名为“Jansen”或“Smit”而且还生活在鹿特丹的客户：

```java
//Sales.Customer[( name = 'Jansen' or name = 'Smit' ) and Sales.Customer_Address/ Sales.Address/City = '鹿特丹'
```

在某些情况下，可能还需要界定限制受制约的数据的次级制约因素。 通过在原制约因素的方括号内添加一个子约束，很容易做到这一点。 不要将此与两个单独的制约混为一谈，因为子制约只适用于元制约，而不是实际查询。 因此，方括号不是放在另一方括号内或放在另一方括号内；子制约应完全在元制约范围内。 在问答十分复杂时，这可能造成一种制约因素在哪里结束而另一种制约因素在哪里开始的混淆。 请确保您保持对括号集的仔细跟踪，以防止出现这种情况。

此查询检索所有具有管理员角色的用户：

```java
//Sales.User[id = '[%UserRole_Administrator%]']]
```

此查询检索居住在鹿特丹或洛斯敦的所有客户：

```java
//Sales.Customer[Sales.Customer_Address/Sales.Address[City = '鹿特丹'或City = 'Losdun']]
```

这一查询检索了居住在圭亚那新阿姆斯特丹的所有客户（与居住在印度新阿姆斯特丹的客户不同）：

```java
//Sales.Customer[Sales.Customer_Address/Sales.Address[City = 'New Amsterdam']/Sales.Adress_Country/Sales.Country/Name = '圭亚那']
```

避免在单一约束下使用同一条路径不止一次。 例如，关于鹿特丹和洛斯敦的例子也可以像这样：

```java
//Sales.Customer[Sales.Customer_Address/Sales.Address/City = '鹿特丹'或Sales.Customer_Address/Sales.Address/City = 'Losdun']
```

然而，这个查询执行效率低下，因此将大大减慢查询进程。

