---
title: "OQL 条款位置"
parent: "oql"
tags:
  - "studio pro"
  - "查询"
  - "位置"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-where-clause.pdf)。
{{% /报警 %}}

WHERE条款具体规定了如何限制检索数据。

语法如下：

```
温度 <constraint>
```

`<constraint>` 值总是等于真值的表达式。 表达式包括使用操作员、函数、关键字或系统变量进行简单比较。

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
