---
title: "规则"
parent: "资源"
menu_order: 30
tags:
  - "微流"
  - "纳诺夫low"
  - "决 定"
  - "逻辑值"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/rules.pdf)。
{{% /报警 %}}

## 1 导言

规则是一种特殊类型的微流。 其结果应该是枚举或布尔值，它可以用于 [决定](decision) 根据该结果做出决定。 这样做的想法是，复杂的决定可以合并到规则中，并在各地重新使用。

## 2 与微流量的差异

规则非常类似于微流；请参阅关于 [微流](microflows) 的文档以了解如何构建一条规则。 规则和微流之间只有少数差异：

*   规则只能用于决定
*   返回类型必须是布尔值或枚举值
*   规则不能更改数据库中的数据；规则中不可用创建、删除、更改和回滚对象的操作
*   规则不能与客户端交互； 显示或关闭表单、显示消息、发送验证反馈和下载文件的操作在规则中不可用
*   规则不能调用 web 服务、生成文档或导入 XML

## 3 阅读更多

* [微型流动](微流)
* [决 定](决 定)
