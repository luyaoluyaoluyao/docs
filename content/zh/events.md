---
title: "事件"
parent: "应用逻辑："
menu_order: 90
tags:
  - "studio pro"
  - "事件"
  - "事件"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/events.pdf)。
{{% /报警 %}}

## 1 导言

事件是指在您的微流流中作为圈子显示的元素，通常放在流流的末尾或开始时：

{{% image_container width="200" %}}
![](attachments/events/events.png)
{{% /image_container %}}

例如，它们被用来开始或结束您的微流，打破循环中的迭代， 或继续此迭代，视活动类型而定。 除错误事件外，所有事件都可以用于微流或nanoflow。

您可以将以下事件添加到您的流程：

* [启动事件](start-event) - 表示您的微流程或nanoflow 的开始

* [结束事件](end-event) - 定义流量停止的位置

* [错误事件](error-event) — 定义微流将停止哪里并抛出一个错误

* [继续事件](continue-event) - 用于循环以停止当前的迭代并开始对下一个对象进行迭代。

* [打破事件](break-event) - 用于循环退出循环并继续保持剩余的流程