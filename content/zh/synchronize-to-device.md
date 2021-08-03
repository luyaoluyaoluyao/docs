---
title: "同步到设备"
parent: "客户活动"
tags:
  - "studio pro"
  - "同步到设备"
  - "客户活动"
menu_order: 60
---

{{% alert type="warning" %}}
此活动只能用于在离线第一个应用程序中运行的 **微流程** (本地或离线PWA应用程序)。
{{% /报警 %}}

## 1 导言

**与设备** 活动同步可以有选择地同步一个或多个对象或列表到设备并将它们存储在离线数据库中。 它意在用于离线应用，当在线应用时不做任何事情。

{{% image_container width="200" %}}
![同步到设备](attachments/client-activities/synchronize-to-device-action.png)
{{% /image_container %}}

## 2 属性

该活动有两组属性。 左侧对话框中的人，以及右侧属性窗格中的人：

![同步到设备属性](attachments/client-activities/synchronize-to-device-action-properties.png)

**与设备** 活动属性同步由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开对话框来配置此动作，点击动作旁边的椭圆(…)。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 目标或清单

指向要同步的对象或列表的变量。

## 4 共同部分 {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}

## 5 限制

将 **同步到设备** 到微流程时考虑以下因素：

* 只有您在离线第一个应用程序中使用的可持久对象或可持久对象列表才能同步。
* 如果当前用户由于访问规则无法访问某些对象， 他们将不会同步到设备。 如果离线数据库已经包含相同对象，它将被删除。
* 如果要同步到设备的对象在相同的微流中被删除， **同步到设备** 活动将从离线数据库中删除，如果找到的话。
* 自动跳过并跳过新的对象。
* 它只会同步来自纳米流而非事件微流的微流中的物体。

## 6 点评论

将 **同步到设备** 到微流程时考虑以下因素：

* 此动作应与 [没有 (保留数据)](offline-first#customizable-synchronization) 选项结合使用，以确保您的数据在同步操作过程中没有被清除。
* **同步到设备** 动作在附加模式下工作，它不能替换数据库中的所有数据。 任何现有数据都被保存，只有发送给客户的对象才会受到影响。
* 同步同一个对象或多次列表将只同步一次。 最新的被命令的状态将被同步。
* 当同步已存在的肮脏对象时，肮脏的值会被覆盖，并且清理脏状态。 但未承诺的更改在应用程序中仍然可用，直到你回滚对象。
* **同步到设备** 总是在数据库中找到相同对象时覆盖现有数据。 这意味着如果 **同步到设备** 被用于离线被更改并在离线中执行的离线对象。 所有这些更改将丢失，受影响对象的属性将被重置为运行时值。
* 用于同步对象的微流中未提交的更改将发送给客户端，但对象回滚到离线版本。
