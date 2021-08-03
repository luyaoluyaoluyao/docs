---
title: "对象活动"
parent: "活动"
menu_order: 10
tags:
  - "studio pro"
  - "微流"
  - "对象"
---

## 1 导言

使用 Mendix 平台时，实体的对象总是被操纵。 这种情况隐含在页面的 [数据小部件](data-widgets) 中，或者在微流程和 nanoflow 中明确使用活动。

微流和 nanoflow 工具箱中的这一部分的活动一般适用于单个物体，但 **提交对象**， **删除对象**和 **检索** 也适用于对象列表。 关于其他与列表相关的活动，请参阅 [列表活动](list-activities)。

The activities described in this document are in the **Object Activities** section of the **Toolbox**:

{{% image_container width="40%" %}}
![对象活动工具箱](attachments/object-activities/object-activities-toolbox.png)
{{% /image_container %}}

下面是您可以在微流程或 nanoflow 中使用的对象活动：

* [投射对象](cast-object) *(仅在微流程中)* - 将对象类型从一般对象类型改为专门对象类型
* [更改对象](change-object) - 更改对象的成员
* [提交对象](committing-objects) — — 要么在数据库中存储可持久实体的对象，要么在内存中存储不可持续实体的对象以使它们能够回滚。
* [创建对象](create-object) - 创建对象
* [删除对象](deleting-objects) *(仅在微流程中)* - 活动删除一个或多个对象
* [检索](retrieve) - 获取一个实体的一个或多个对象
* [回滚对象](rollback-object) - 撤销未承诺的对对象的更改

## 2 次阅读更多

* [活动](活动)