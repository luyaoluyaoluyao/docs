---
title: "索引"
parent: "实体"
menu_order: 60
tags:
  - "域模型"
  - "实体"
  - "属性"
  - "索引"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/indexes.pdf)。
{{% /报警 %}}

## 1 导言

**索引** 是实体底层数据库表中创建数据库索引的属性列表。 如果索引属性在搜索字段中使用，索引会提高检索对象的速度。 一个数据网格或模板网格的 XPath 约束，或一个 `WHERE` 条款的 OQL 查询。 然而， `比较` 属性有值的搜索字段 `包含` 不会利用改进的性能。

索引可以从实体属性的 **索引** 标签中添加和编辑。

![索引选项卡示例](attachments/domain-model/index-properties.png)

{{% alert type="info" %}}
索引属性是只读的外部实体。 欲了解更多详情，请参阅 [外部实体](external-entities)。
{{% /报警 %}}

## 2 重要考虑因素

### 2.1 属性顺序

索引已订购， 这意味着当您在两个或多个属性上创建索引时，必须考虑属性的顺序。 在搜索或查询多个属性时利用改进的性能， 这些属性应该与索引中的属性相同。 扩展，当检索仅受一个属性约束时， 只有当这是索引中的第一个属性时，才能实现更好的性能。

### 2.2 系统成员索引

如果您选择存储一个实体的 `所有者` and `更改了` 系统成员将创建一个索引。 `创建日期` 和 `更改日期` 系统成员的情况不是这样。 此外，为自动生成的属性 `id` 创建了一个索引。 更多关于实现这些属性的信息，请参阅 [域模型](domain-model)。

### 2.3 非永久性实体的指数

您只能定义可持久实体的索引，因为索引是一个数据库概念。 因此，不可持续实体的索引已被禁用。

### 2.4 性能考虑

更改和删除具有索引的实体的对象需要更长时间，因为除了实际数据外，还需要更新索引。 因此，对于在搜索或查询中很少用作标准的属性， 如果检索性能的提高证明更新性能的降低，只能创建一个指数。

## 3 个示例

客户通常通过邮政编码和住宅编号的组合检索。 因此， *一个* 索引设置于属性的组合：

![](attachments/domain-model/customer-index-example.png)

以下OQL查询获取对象——注意 `WHERE` 条款中属性的顺序与索引属性的顺序相同：

```sql
来自Module.Customer AS c
WHERE c.zipcode = $ParameterZipCode and c.housnumber = $ParameterHouseNumber
SELECT c.name as Customername
```
