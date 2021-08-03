---
title: "活动"
parent: "微流和微流法"
menu_order: 40
tags:
  - "studio pro"
  - "微流"
  - "nanoflows"
  - "活动"
---

## 1 导言

活动定义了在微流或纳米流中执行的行动。

有不同类型的活动，它们被归类于Studio Pro工具箱。 所有活动列于下面，请参阅链接以获取更多信息。

{{% alert type="info" %}}
大多数活动都可以用于微流和纳米。 然而，有些只能用于其中一种流量，或者微流和纳米流之间的行为可能不同。 关注链接以获取更多信息。
{{% /报警 %}}

## 2个对象活动

对象活动可以用来创建和操纵对象。 [域模型](domain-model) 定义了可以使用的对象类型 ([实体](entities))。

| 图形                                                                      | 名称                               | 描述                                                                                    |
| ----------------------------------------------------------------------- | -------------------------------- | ------------------------------------------------------------------------------------- |
| [![投射对象](attachments/activities/cast-object.png)](cast-object)          | [投射对象](cast-object) *(仅微流)*      | 结合 [对象类型决定](object-type-decision) 允许您使用对象的专业化成员。 欲了解更多关于对象专业成员的信息，请参阅 [实体](entities)。 |
| [![更改对象](attachments/activities/change-object.png)](change-object)      | [更改对象](change-object)            | 允许您更改对象的成员。 无论有无承诺，也无论有无事可做。                                                          |
| [![提交对象](attachments/activities/commit-object.png)](committing-objects) | [提交对象(s)](committing-objects)    | 允许您提交对一个或多个对象的更改。                                                                     |
| [![创建对象](attachments/activities/create-object.png)](create-object)      | [创建对象](create-object)            | 创建一个对象。                                                                               |
| [![删除对象](attachments/activities/delete-object.png)](deleting-objects)   | [删除对象](deleting-objects) *(仅微流)* | 删除对象。                                                                                 |
| [![获取](attachments/activities/retrieve.png)](retrieve)                  | [获取](retrieve)                   | 获取另一个对象的一个(或多个)关联对象。 此外，这项活动还可以直接从数据库中获取一个或多个对象。                                      |
| [![回滚对象](attachments/activities/rollback.png)](rollback-object)         | [回滚对象](rollback-object)          | 记录活动前微流中某一对象的未承诺的更改。 此外，它删除已创建但从未承诺的对象。                                               |

## 3 列出活动

列表活动可以用来创建和操纵对象列表。

| 图形                                                                   | 名称                     | 描述                                  |
| -------------------------------------------------------------------- | ---------------------- | ----------------------------------- |
| [![合计列表](attachments/activities/aggregate-list.png)](aggregate-list) | [聚合列表](aggregate-list) | 允许您计算合计值，例如对象列表上的对象的最大值、最小值、平均值和总量。 |
| [![更改列表](attachments/activities/change-list.png)](change-list)       | [更改列表](change-list)    | 允许您更改列表变量的内容。                       |
| [![创建列表](attachments/activities/create-list.png)](create-list)       | [创建列表](create-list)    | 创建一个(空)列表变量。                        |
| [![列表操作](attachments/activities/list-operation.png)](list-operation) | [列表操作](list-operation) | 将两个清单与同一实体的对象合并或比较。                 |

## 4 行动呼叫活动

动作调用活动可以调用另一个微流或调用 Java 动作。

| 图形                                                                                              | 名称                                                          | 描述                                       |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------- | ---------------------------------------- |
| [![java 动作调用](attachments/activities/call-java-action.png)](java-action-call)                   | [调用 Java 动作](java-action-call) *(仅在微流程中)*                   | 调用 Java 操作。 参数可以传递到操作中，结果可以存储在变量中。       |
| [![javascript 动作调用](attachments/activities/call-javascript-action.png)](javascript-action-call) | [调用 JavaScript 动作](javascript-action-call) *(仅在 nanoflows)* | 调用 JavaScript 行动。 参数可以传递到操作中，结果可以存储在变量中。 |
| [![微流程呼叫](attachments/activities/call-microflow.png)](microflow-call)                           | [微流程呼叫](microflow-call)                                     | 调用微流。 参数可以传递到微流，结果可以存储在变量中。              |

## 5 可变活动

变量活动可以用于创建或更改微流中的变量。

| 图形                                                                     | 名称                      | 描述          |
| ---------------------------------------------------------------------- | ----------------------- | ----------- |
| [![更改变量](attachments/activities/change-variable.png)](change-variable) | [更改变量](change-variable) | 允许您更改变量的值。  |
| [![创建变量](attachments/activities/create-variable.png)](create-variable) | [创建变量](create-variable) | 允许您创建一个新变量。 |

## 6个客户活动

客户端活动可以用来让您的应用程序的 web 客户端执行操作 例如显示一个不同的页面或下载一个文件。

| 图形                                                                                  | 名称                                            | 描述                                                           |
| ----------------------------------------------------------------------------------- | --------------------------------------------- | ------------------------------------------------------------ |
| [![nanoflow 呼叫](attachments/activities/call-nanoflow.png)](nanoflow-call)           | [调用 nanoflow](nanoflow-call) *(仅在 nanoflows)* | 呼叫另一个 nanoflow。 参数可以传递到 nanoflow 中，结果可以存储在变量中。               |
| [![关闭页面](attachments/activities/close-page.png)](close-page)                        | [关闭页面](close-page)                            | 关闭此活动所使用的microflow 用户最后打开的页面。                                |
| [![下载文件](attachments/activities/download-file.png)](download-file)                  | [下载文件](download-file) *(仅微流程中)*               | 可以用来启用浏览器下载特定文件。 调用该活动所使用的微流程的用户将获得一个下载弹出窗口， 或者该文件直接显示在浏览器中。 |
| [![显示主页](attachments/activities/show-home-page.png)](show-home-page)                | [显示主页](show-home-page) *(仅在微流程中)*             | 导航到当前用户的主页。                                                  |
| [![显示消息](attachments/activities/show-message.png)](show-message)                    | [显示消息](show-message)                          | 允许您向调用此活动所使用的微流的用户显示屏蔽或非屏蔽消息。                                |
| [![显示页面](attachments/activities/show-page.png)](show-page)                          | [显示页面](show-page)                             | 允许您向调用该活动的微流程的用户显示一个页面。                                      |
| [![同步到设备](attachments/activities/synchronize-to-device.png)](synchronize-to-device) | [同步到设备](synchronize-to-device) *(仅微流程中)*      | 可以用于选择性地同步一个或多个对象或列表到设备并将其存储在离线数据库中。                         |
| [![synchronize](attachments/activities/synchronize.png)](synchronize)               | [同步](synchronize)  *(仅在 nanoflows)*           | 同步数据。                                                        |
| [![验证反馈](attachments/activities/validation-feedback.png)](validation-feedback)      | [验证反馈](validation-feedback)                   | 允许您在显示属性或关联性的部件下方显示红色文本。                                     |

## 7 集成活动

集成活动可用于与其他系统集成，例如通过呼叫网络服务。

| 图形                                                                                     | 名称                                | 描述                                                                                                                   |
| -------------------------------------------------------------------------------------- | --------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| [![通话REST 服务](attachments/activities/call-rest-service.png)](call-rest-action)         | [通话REST 服务](call-rest-action)     | 可以用来调用REST 端点。 您可以使用映射将结果映射到实体或实体请求中。 您也可以使用字符串模板并将结果存储在字符串变量中。                                                      |
| [![调用 web 服务操作](attachments/activities/call-web-service.png)](call-web-service-action) | [呼叫网络服务](call-web-service-action) | 可以调用导入的 [网页服务](consumed-web-services)。 请求的内容可以编辑。 此外，网络服务的响应可以映射到实体，并存储在变量中或被忽略。                                     |
| [![导入映射文件](attachments/activities/import-with-mapping.png)](import-mapping-action)     | [通过映射导入](import-mapping-action)   | 可以用来解析一个字符串变量或存储在文件中的数据。 并将它们存储到数据库的 [域模型](domain-model) 中定义的实体。 [导入映射](import-mappings) 用于映射进入的 XML 或 JSON 到实体。     |
| [![导出映射文件](attachments/activities/export-with-mapping.png)](export-mapping-action)     | [用映射导出](export-mapping-action)    | 可以用于将存储在 [域模型](domain-model) 实体中的数据导出到 XML 或 JSON 字符串。 它也可以存储在文件中。 [导出映射](export-mappings) 用于将域模型实体映射到 XML 或 JSON 中。 |

## 8个日志活动

| 图形                                                             | 名称                  | 描述                         |
| -------------------------------------------------------------- | ------------------- | -------------------------- |
| [![日志消息](attachments/activities/log-message.png)](log-message) | [日志消息](log-message) | 允许您创建出现在Mendix 应用程序日志中的消息。 |

## 9 文档生成活动

| 图形                                                                         | 名称                                         | 描述                                        |
| -------------------------------------------------------------------------- | ------------------------------------------ | ----------------------------------------- |
| [![生成文档](attachments/activities/generate-document.png)](generate-document) | [生成文档](generate-document) *(仅在 nanoflows)* | 允许您基于 [模板](document-templates) 创建特定类型的文档。 |

## 10 工作流活动

工作流活动与工作流及其用户任务有关。

| 图形                                                                       | 名称                              | 描述                                                          |
| ------------------------------------------------------------------------ | ------------------------------- | ----------------------------------------------------------- |
| [![](attachments/activities/complete-task.png)](complete-task)           | [完成用户任务](complete-task)         | 设置 [用户任务](user-task) 应该遵循的结果。 例如，此活动可以用来通过自定义验证的微流程来完成用户任务。 |
| [![](attachments/activities/open-task-page.png)](show-task-page)         | [显示用户任务页面](show-task-page)      | 打开 [用户任务属性](user-task) 中指定的用户任务页面。                          |
| [![](attachments/activities/open-workflow-page.png)](show-workflow-page) | [显示工作流管理页面](show-workflow-page) | 打开一个工作流概览页面。                                                |
| [![](attachments/activities/workflow-call.png)](workflow-call)           | [工作流呼叫](workflow-call)          | 触发选定的工作流。                                                   |
