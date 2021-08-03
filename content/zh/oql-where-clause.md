---
title: "OQL 条款位置"
parent: "oql"
---


WHERE条款具体规定了如何限制检索数据。

语法如下：

```
温度 <constraint>
```

`<constraint>` 值总是等于真值的表达式。 表达式包括简单的与操作员、函数、关键字或系统变量的可比性。

{{% alert type="info" %}}

```
选择来自销售的名字。客户
WHERE LastName = 'Jansen'
```

此查询检索名称等于“Jansen”的所有客户。

{{% /警示%}}!{% alert type="info" %}}

```
SELECT 姓来自 Sales.Customer
INNER JOIN Sales.Customer_Address/Sales.Address
WHERE Sales.Address/City = '鹿特丹'
```

此查询可以检索所有居住在鹿特丹的客户。

{{% /报警 %}}
