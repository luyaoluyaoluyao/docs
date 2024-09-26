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

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/synchronize.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动只能用于 **Nanoflows**。
{{% /报警 %}}

## 1 导言

**同步** 活动可以用于在您的设备和服务器之间同步您的数据。  **同步** 动作有两个模式：

### 1.1 同步所有对象

{{% image_container width="200" %}}
![Synchronize](attachments/client-activities/synchronize.png)
{{% /image_container %}}

此模式同步整个本地数据库。 使用本地数据库的更改更新服务器数据库。 本地数据库使用来自服务器的最新数据，包括文件内容。

此模式的行为可以通过 [**同步配置**](offline-first#customizable-synchronization) 进行配置。

### 1.2 同步选定的对象

{{% image_container width="200" %}}
![Synchronize](attachments/client-activities/synchronize-objects.png)
{{% /image_container %}}

此模式基于一个选区部分同步对象：

{{% image_container width="600" %}}
![Synchronize](attachments/client-activities/synchronize-objects-selection.png)
{{% /image_container %}}

使用此模式，只有选定的对象或列表被同步。 同步是双向的， 意味着服务器数据库和所选对象的本地数据库都被更新。

如果选择同步对象包含任何尚未提交的对象集， 这些对象将被跳过，因此不会同步。

如果选中的对象有本地更改，则执行以下步骤：

1. 使用本地数据库的更改更新服务器数据库。
1. 本地数据库已从服务器数据库更新。 如果选中的对象具有计算属性或在事件之前/之后的事件处理器微流中被修改，这是有用的。

如果选中的对象来自服务器 (未在设备上创建), 并且不再存在于服务器上(或由于访问规则无法访问)， 本地更改未应用，对象已从本地数据库中删除。 在这种情况下，该对象的 nanoflow 变量值为 `空`。 服务器在 `System.SynchronizationFaily` 实体中存储被丢弃的更改，以防止数据丢失。

如果选择要同步的对象包含没有本地更改的对象，同步更新服务器数据库中的本地副本。 如果有一个对象已经从服务器上删除，或者由于访问规则无法访问， 该对象也将从本地数据库中删除。

## 2 属性

**同步** 活动属性由以下部分组成：

* [行 动](#action)

* [常用的](#common)

    {{% image_container width="300" %}}![Synchronize Action Properties](attachments/client-activities/synchronize-properties.png){{% /image_container %}}

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

## 4 共同部分 {#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}

## 5 限制 {#limitations}

不支持同时运行多个同步进程，不管类型为何(**完整** 或 **选择**)。

如果您试图在同步过程中触发另一个同步过程，则将显示以下错误信息：

**不支持同步同步进行。 请在当前同步完成后重试。**

这种错误可以在 nanoflow 中处理，从而触发了同步尝试使用 [错误处理程序](/refguide8/error-event#errorhandlers)。

## 6 阅读更多

* [活动](活动)
* [离线前](离线前)
