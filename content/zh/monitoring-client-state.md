---
title: "监视客户状态"
category: "Mendix 运行时间"
tags:
  - "studio pro"
---

## 1 导言

状态在客户端 (网络浏览器) 中。 这允许将服务器缩放到多个实例。 由于国家现在居住在客户中，监测国家的情况以及为什么在某个时间进行监测可能是有益的。

要做到这一点， 使用 <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>G</kbd> 键组合将状态转储到浏览器控制台。 状态显示在 JSON 对象中，并按实体类型分组. 如果实体不可持续，则标注后缀 `[NPE]`

{{% alert type="info" %}}
The <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>G</kbd> key combination works in all browsers except Mozilla Firefox in [Parallels](/howto8/mobile/using-mendix-studio-pro-on-a-mac).
{{% /报警 %}}

## 2 个详细信息

对于每个实体类型，列出处于状态的对象实例的 ID。 每个对象实例显示以下信息：

* 对象ID之后的后缀 `(新)` - 对象是否是新的对象(对象尚未发生)
* 对象ID后的后缀 `(已更改)` - 对象是否有未承诺的更改(对象已经在之前承诺)
* 属性 `改变` - 对象中存在的更改
* 属性 `订阅小部件` - 正在使用对象的小部件
    * 小部件名称的形式为 `Module.PageName.widgetName` (例如， `MyFirstModule)。 ntity_NewEdit.dataView1`), 它允许您在Studio Pro 中快速找到引用的小部件
* `引用的` 属性 - 引用此对象的对象

`个订阅小部件` and `引用的` 属性解释了为什么对象仍然处于状态状态。 如果两者都是空的，则显示“去收集垃圾”的文字。
