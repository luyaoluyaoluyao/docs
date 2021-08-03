---
title: "访问规则"
parent: "实体"
menu_order: 70
tags:
  - "域模型"
  - "实体"
  - "访问规则"
  - "x路径约束"
  - "模块角色"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/access-rules.pdf)。
{{% /报警 %}}

## 1 导言

实体的 **访问规则** 定义用户允许对实体对象做些什么。 用户可以创建和/或删除对象，查看和/或编辑会员值。 成员是实体的属性或协会。 此外，可以通过 [XPath 约束](xpath-constraints) 来限制用于查看、编辑和移除的对象。

每个访问规则都适用于一个或多个 [模块角色](module-security#module-role)。 准入规则赋予这些角色某些准入权。 规则是附加的，这意味着如果多个访问规则适用于同一个模块角色 该模块角色的所有访问权限都被合并。

{{% alert type="warning" %}}
访问规则不是从一个实体的 [概括](entities#generalization)继承下来的，每个实体的安全都是明确指定的。 这意味着，在将访问规则添加到实体时，总是确保所有必需的 XPath 约束都得到应用。

如果该实体具有定义了 XPath 约束的访问规则的概括化， 它们不适用于它的专业，因此不会限制它的知名度。
{{% /报警 %}}


## 2 属性

访问规则是通过实体的 **属性** > **访问规则**, 或者在 **访问规则** 实体对话框选项卡。

![实体访问规则](attachments/domain-model/access-rules-section.png)

![实体访问规则](attachments/domain-model/access-rules-tab.png)

{{% alert type="info" %}}
**访问规则** 部分只有在 [项目安全](project-security) 设置为 **生产** 时才可见。
{{% /报警 %}}

下面的图像是访问规则属性的示例：

![实体访问规则](attachments/domain-model/access-rules-properties.png)

访问规则属性由以下部分组成：

* [文件](#documentation)
* [模块角色](#module-roles)
* [访问权](#access-rights)
* [XPath 约束](#xpath-constraint)

### 2.1 文件科 {#documentation}

在 **文档**中，你可以描述访问规则的意图。 这有助于使访问规则易于理解，在非细致的 XPath 限制的情况下尤其如此。

### 2.2 规则适用于以下模块角色部分 {#module-roles}

#### 2.2.1 作用

列出了所有模块角色，并检查了此访问规则所适用的模块角色。 所有拥有至少一个选中模块角色的用户都能获得规则定义的访问权限。

#### 2.2.2 选择/取消选择所有

您可以轻松选择或取消选择使用此复选框的所有模块角色。

### 2.3 访问权选项卡{#access-rights}

**访问权限** 标签允许您将权限分配给具有选定模块角色的用户。

#### 2.3.1 设立和删除权利科

##### 2.3.1.1 允许创建新对象

如果 **允许创建新对象** 被选中，用户可以创建此实体的新对象。

##### 2.3.1.2 允许删除现有对象

如果选中 **允许删除现有对象** ，用户将被允许删除此实体的现有对象。

可以删除的对象组可以通过使用 [XPath 约束](#xpath-constraint) 来加以限制。

#### 2.3.2 成员阅读 & 写权部分

**会员读写权限** 定义了该实体每个成员的访问权限 ([属性](attributes) 或 [关联](associations))。 这些访问权表示是否允许用户查看和/或编辑会员的值。 这些权利所适用的对象组可以通过使用 [XPath 约束](#xpath-constraint) 来加以限制。

| 值     | 描述                 |
| ----- | ------------------ |
| -     | 用户不允许查看或编辑会员的值。    |
| 已读    | 用户可以查看此会员的值，但不能编辑。 |
| 读取，写入 | 用户可以查看和编辑此成员的值。    |

{{% alert type="info" %}}
您不能设置 *写入* 访问已计算的属性。 这包括类型 *Autonumber* 和属性值设置为 **计算的** 的属性。
{{% /报警 %}}

**新成员** 的默认权限指定了适用于此实体新属性或关联的权限。

**将所有设置为** 允许您快速设置成员的所有访问权限为 **无**， **读取**, 或 **读取, 写入**.

例如，客户可以查看折扣，但不允许编辑折扣。 折扣属性的访问权限是 **读取**。

![](attachments/domain-model/access-rule-discount-read.png)

### 2.4 XPath 选项卡 {#xpath-constraint}

[XPath 约束](xpath-constraints) 可以用于限制访问规则所适用的对象集合。 如果XPath 约束为空，规则适用于实体的所有对象。

![](attachments/domain-model/access-rule-xpath-tab.png)

例如， **客户** 实体是 **用户** 实体的专业化。 **订单** 实体与 **客户** 实体相关联。

登录客户可以查看个人订单，但不允许查看其他客户的订单。 这是通过在 **命令** 实体的访问规则中使用以下的 XPath 约束来完成的：

```java
[Module.Order_custer = '[%CurrentUser%]']
```

![](attachments/domain-model/access-rule-order-xpath.png)

由于此 XPath 限制，访问规则仅适用于客户是当前登录用户的订单。

{{% alert type="warning" %}}
XPath 约束只能应用于可持久的实体，因为它们是由数据库应用的。 定义不可持续实体的 XPath 约束会造成一致性错误。
{{% /报警 %}}
