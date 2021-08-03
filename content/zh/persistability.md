---
title: "持久性"
parent: "实体"
menu_order: 20
tags:
  - "域模型"
  - "实体"
  - "可持久性"
  - "可保持的"
  - "不可用"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/persistability.pdf)。
{{% /报警 %}}

## 1 导言

域模型中的实体的 **可持久** 属性定义了一个对象是否可以承诺到数据库中。

可持久实体在域模型中彩色蓝色。 不可持续的实体是彩色的。 下面图像中的 **客户** 实体是可持久的，而 **ProductQueryResult** 是不可持续的。

![可持久实体和不可持久实体的图片](attachments/domain-model/persistable-vs-non-persistable.png)

## 2 可持久实体 {#persistable}

当一个实体被宣布为可持久实体时，将为该实体创建一个数据库表。

提交此实体类型的对象将被插入表中。 对象的属性和关联值也保存在数据库中。

### 2.1 自动承付对象

通常情况下，回滚会恢复自上次提交以来内存的变化。

然而，仍然存在着这种情况。 在可持久自动提交的对象或状态为“NEW”的对象上执行回滚，从相关实体的数据库表中删除与此对象对应的行。 关于自动提交对象的更多信息，请参阅 [对象活动](object-activities)。

## 3 非持久实体 {#non-persistable}

不可持续的实体被存储在运行时的内存中，永远不会被投入数据库。 因此，他们在数据库中没有表格。

承诺不可持续的实体在内存中记录当前的属性值和关联值，允许回滚回到这些值。
