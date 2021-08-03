---
title: "Synchronize"
parent: "客户活动"
menu_order: 70
tags:
  - "studio pro"
  - "synchronize"
  - "离线的"
  - "客户活动"
---

{{% alert type="warning" %}}
此活动只能用于在离线第一个应用程序中运行的 **Nanoflow** (本地或离线PWA应用程序)。
{{% /报警 %}}

## 1 导言

**同步** 活动可以用于在您的设备和服务器之间同步您的数据。  该行动有三种方式，下文将予以说明。

## 2 种同步模式

### 2.1 所有对象

{{% image_container width="200" %}}
![Synchronize](attachments/client-activities/synchronize.png)
{{% /image_container %}}

**所有对象** 模式同步整个本地数据库。 使用本地数据库的更改更新服务器数据库。 本地数据库使用来自服务器的最新数据，包括文件内容。

此模式的行为可以通过 [同步配置](offline-first#customizable-synchronization) 进行配置。

### 2.2 非同步对象 {#unsynchronized-objects}

{{% image_container width="200" %}}
![Synchronize](attachments/client-activities/synchronize-unsynchronized-objects.png)
{{% /image_container %}}

使用 **未同步对象** 模式，所有已承诺更改的对象都被同步。 同步是双向的，意味着服务器数据库和本地数据库都被更新。 欲了解更多信息，请参阅下面的 [同步行为](#synchronization-behavior) 部分。

### 2.3 选定对象 {#selected-objects}

{{% image_container width="200" %}}
![Synchronize](attachments/client-activities/synchronize-objects.png)
{{% /image_container %}}

**所选对象(s)** 模式部分同步对象，基于一个选择：

{{% image_container width="600" %}}
![Synchronize](attachments/client-activities/synchronize-objects-selection.png)
{{% /image_container %}}

使用此模式，只有选定的对象或列表被同步。 同步是双向的，意味着服务器数据库和本地数据库都更新了所选对象。 欲了解更多信息，请参阅下面的 [同步行为](#synchronization-behavior) 部分。

## 3 次同步行为 {#synchronization-behavior}

本节描述 [未同步对象](#unsynchronized-objects) 和 [选定对象](#selected-objects) 模式的行为。

{{% alert type="warning" %}}
[同步配置](offline-first#customizable-synchronization) 中的设置不适用于 **未同步对象** 和 **选定对象** 模式。
{{% /报警 %}}

在 **个选定对象** 模式中， 如果选择要同步的对象包含尚未提交的对象集， 这些对象将被跳过，因此不会同步。

如果选中的对象有本地更改，则执行以下步骤：

1. 使用本地数据库的更改更新服务器数据库。
2. 本地数据库已从服务器数据库更新。 如果选中的对象具有计算属性或在事件之前/之后的事件处理器微流中被修改，这是有用的。

如果选中的对象来自服务器 (未在设备上创建), 并且不再存在于服务器上(或由于访问规则无法访问)， 本地更改未应用，对象已从本地数据库中删除。 在这种情况下，该对象的 nanoflow 变量值为 `空`。 服务器在 `System.SynchronizationFaily` 实体中存储被丢弃的更改，以防止数据丢失。

如果选择要同步的对象包含没有本地更改的对象，同步更新服务器数据库中的本地副本。 如果有一个对象已经从服务器上删除，或者由于访问规则无法访问， 该对象也将从本地数据库中删除。

## 4 属性

**同步** 活动属性由以下部分组成：

* [行 动](#action)
* [常用的](#common)

{{% image_container width="300" %}}![Synchronize Action Properties](attachments/client-activities/synchronize-properties.png){{% /image_container %}}

## 5 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

## 共同部分 {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}

## 7 限制 {#limitations}

不支持同时运行多个同步进程，不管同步模式。

如果您试图在同步过程中触发另一个同步过程， 将显示以下错误消息：“不支持同步同步操作。 请在当前同步完成后重试。"

这种错误可以在 nanoflow 中处理，从而触发了同步尝试使用 [错误处理程序](/refguide/error-event#errorhandlers)。

## 8 阅读更多

* [活动](活动)
* [离线前](离线前)
