---
title: "特别检查"
parent: "表达式"
---

## 正在检查空对象

### Input

对象。

类型：任何类型的对象。

### 产出

返回对象是否为空。

Type: Boolean.

```java
$object1 = 为空
```

假定 $object1 是一个域实体并且目前存在，这个语句将返回 False。 相反，如果对象目前不存在(如果你试图检索一个不存在的对象可能)，它将返回 True。

当 $object1 是变量时(例如Integer, 字符串等)，也是相同的。

## 检查空对象成员

### Input

对象的会员 (属性或关联)

类型：任何类型的成员。

### 产出

属性是否为空。

Type: Boolean.

```java
$object1/member1 = 为空
```

假定 $object1 是一个域实体，并且它有一个叫做“member1”的会员，下表说明该报表将返回什么：

|               | 成员1 有一个值 | Member1 没有值 |
| ------------- | -------- | ----------- |
| $object1 有一个值 | false    | true        |
| $object1 没有值  | 无        | true        |

## 正在检查对象是否是新对象<a name="new"></a>


### Input

对象。

类型：任何类型的对象。

### 产出

返回对象是否是新对象(已创建但尚未被执行)。 注意，这仅当此函数被调用到代表创建对象的变量时才会保持。 当对象从数据库中检索时，新会总是产生假的。

Type: Boolean.

```java
isNew($object1)
```

## 检查对象是否同步<a name="synced"></a>

{{% alert type="info" %}}

此函数仅在 [条件可见性或可编辑性](conditions)的表达式中可用，因为它们只是经过评估的客户端。

这是在 Mendix 7.1 中添加的。

{{% /报警 %}}

### Input

对象。

类型：任何类型的对象。

### 产出

Returns whether the changes done to the object [offline](offline) have been synchronized to the runtime database. 在 web 配置文件和 [混合配置文件](hybrid-phone-profile) 中，没有离线支持，这总是返回 `true`。

Type: Boolean.

```java
Synced($currentObject)
```
