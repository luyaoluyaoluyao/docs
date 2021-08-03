---
title: "已消耗的应用服务"
parent: "集成"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/consumed-app-services.pdf)。
{{% /报警 %}}

{{% alert type="info" %}}
应用程序服务已被弃用，并已在Studio Pro 9中删除。 使用 [消费的 web 服务](consumed-web-services) 来消费现有的应用服务。
{{% /报警 %}}

应用服务是连接Mendix 应用程序之间的一种方式。 可以导入应用服务并使用其内容。 到目前为止，应用服务提供了以下内容：

* 微流程操作
* 域模型实体

在项目探险家中，可以在模块上的“添加”上下文菜单中选择应用服务。 查看 [选择应用程序服务](select-app-service) 获取更多信息。

关于文档选项的更多信息，请参阅 [设置](settings) 页面。

应用服务操作可直接在 Microflow中获得。 如果添加了新的活动，新的应用服务操作会显示在标准的微流操作之下。

![](attachments/16713703/16843891.png)

应用服务操作可能需要参数，通常提供返回值。 返回值可以用于微流的其余部分。 参数和返回值可以是对象或列表类型； 被应用服务接受的实体包含在应用服务的域模型中。
