---
title: "下拉搜索字段"
parent: "搜索栏"
---

## 公共属性

{{% snippet file="refguid7/Search+Field+Caption+Property.md" %}}

{{% snippet file="refguid7/Search+Field+Type+Property.md" %}}

{{% snippet file="refguid7/Search+Field+Default+Value+Property.md" %}}

## 常规属性

{{% snippet file="refguid7/Search+Field+Attribute+Path+Property.md" %}}

{{% snippet file="refguide7/Search+Field+Comparison+Property.md" %}}

下拉选择选项的数目上限为1 000个。 因此，所选属性的唯一值不能超过 1 000个。 设置此限制是为了在旧浏览器上保存页面加载性能，因为需要从服务器检索这些选项。 在 Mendix 8 中，此限制已被删除。

### 允许多选

如果这个属性设置为“是”，由此产生的下拉下拉允许您选择多个值，而不只是一个。 当搜索所有匹配的记录时，相应的属性等于所选值之一。 例如，您可以搜索所有订单的状态为“提交”或“正在进行中”。

### XPath 约束

如果“下拉”搜索字段连接到关联实体的属性(相对于网格实体本身)，则可以使用 XPath 约束来限制下拉中显示的对象。

{{% alert type="info" %}}

让我们说你有一个网格显示自行车。 在网域模型中，自行车与商店有一个关联，您可以购买这些自行车。 您可以将搜索字段添加到网格，使终端用户可以选择一个商店的名称。 然后可以使用 XPath 将商店限制在指定国家的商店。 `[MyWebshop.Bicycle_Shop/MyWebshop.Shop/Country='Netherlands']`

{{% /报警 %}}

### 排序顺序

排序顺序指定了下拉搜索字段中各项的显示顺序。 您可以在两个方向排序多个属性 (升序和降序)。 如果没有指定排序顺序，显示属性上的下拉搜索字段排序。

_默认值：_ 无排序顺序
