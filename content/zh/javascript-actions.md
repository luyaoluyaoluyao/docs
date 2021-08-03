---
title: "JavaScript 操作"
parent: "资源"
menu_order: 20
description: "本参考指南详细介绍JavaScript 操作可以扩展Mendix 应用程序功能的方式。"
tags:
  - "javascript"
  - "javascript 操作"
  - "参数"
  - "studio pro"
---

{{% alert type="warning" %}}
此活动只能用于 **Nanoflows**。
{{% /报警 %}}

## 1 导言

用 JavaScript 动作，您可以以非独特的方式扩展您的应用程序的功能。 要使用 JavaScript 动作，使用 [JavaScript 动作调用](javascript-action-call)。

{{% alert type="info" %}}

Mendix Studio Pro 中定义的每个JavaScript 动作对应文件 *{JavaScript action name}。 s* 在子目录 **javascriptsource{module name}/actions/** 在您的应用目录中。

这些 *的骨头. s* 个文件是在您保存一个动作时自动生成的，这些JavaScript操作可以立即被编辑到嵌入代码编辑器中。

{{% /报警 %}}

要学习如何创建、配置和使用 JavaScript 动作，请参阅 [如何构建JavaScript 动作](/howto/extensibility/build-javascript-actions)。

## 2 个常规设置

在您的 **App Explorer** 中双击JavaScript 动作后，您将看到JavaScript 动作的设置：

{{% image_container width="400" %}}![javascript settings](attachments/javascript-actions/javascript-action-settings-no-para.png){{% /image_container %}}

JavaScript 动作及其影响的设置详见下文。

### 2.1 名称

此设置处理一个 JavaScript 动作的名字，当进行通话时，nanoflow 是指它的。 此名称也是生成的 *.js* 文件的名称。

### 2.2 参数

参数传递数据到 JavaScript 操作。 例如，如果你有一个 JavaScript 动作，乘以数字，参数会定义要乘以的数字。 JavaScript 动作可以有零或更多参数。 每个参数应该有一个唯一的名称。 您可以点击 **参数** > **添加**然后自定义该参数以将数据传递到 JavaScript 动作：

![参数](attachments/javascript-actions/parameter-naming.png)

在 JavaScript 动作的 **代码** 标签中，你可以看到它的参数值并处理它的实现。 每个参数有一个名称(1)、类型(2)、类别、描述(3)和返回类型(4)：

![参数代码](attachments/javascript-actions/parameter-code.png)

您将看到一个参数类别(1)，参数名称(2)。 在 **调用 JavaScript 动作** 对话框中，在你的 nanoflow 中双击其活动后的描述（3）:

{{% image_container width="400" %}}![call javascript action dialog](attachments/javascript-actions/call-js-action-dialog.png){{% /image_container %}}

JavaScript 操作支持的参数类型描述如下。

#### 2.2.1 名称

此设置处理参数的名称。 名称是必需的。 名称必须以字母开头，只包含字母。 名称中不允许有空格。

#### 2.2.2 类型

| 名称      | 描述                                                                                                                                                                                                                                                        |
| ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 对象      | 对象参数类型允许您将 Mendix 对象传递到 JavaScript 动作。 您还必须选择其实体类型，它可以是一个特定的实体或类型参数。 在生成的 JavaScript 动作模板代码中，这种类型表示为 MxObject。                                                                                                                                            |
| 列表      | 列表参数类型允许您将 Mendix 对象列表传递到 JavaScript 动作。 您还必须选择其实体类型，它可以是一个特定的实体或类型参数。 在生成的 JavaScript 动作模板代码中，这种类型表示为 MxObjects 的数组。                                                                                                                                     |
| 实体      | 实体参数类型是占位符。 它指的是一个实体，如果一个新的实体被用纳米材料命名，该实体将被替换。 此外，实体类型可以用来填写类型参数。 在生成的 JavaScript 动作模板代码中，这种类型是一个字符串。                                                                                                                                                     |
| 纳诺夫low  | nanoflow 参数类型允许您传递一个 nanoflow ，您可以通过您的 JavaScript 动作呼叫。 参数值是异步函数，调用将触发配置的 nanoflow 您可以指定参数为 JavaScript 对象，并在执行完成后捕获nanoflow 的返回值。 例如， 您可以调用 nanoflow 具有字符串 `name` 参数并返回一个 `用户` 对象使用给定名称： `const user = requising nanoflowParameter(欧共体名称: "John Doe" });` |
| Boolean | 布尔参数类型允许您将布尔值传递到 JavaScript 动作。                                                                                                                                                                                                                           |
| 日期和时间   | 日期和时间参数类型允许您将日期和时间值传递到 JavaScript 动作。 在生成的 JavaScript 动作代码中，这种类型将表示为 JavaScript `日期`。                                                                                                                                                                     |
| 小数      | 十进制参数类型允许您将十进制值传递到 JavaScript 动作。 在生成的 JavaScript 动作代码中，这种类型将表示为 [大](https://www.npmjs.com/package/big-js) 对象。                                                                                                                                            |
| 枚举数     | 枚举参数类型允许您将枚举值传递给一个 JavaScript 操作。 在生成的 JavaScript 动作代码中，这种类型将作为字符串表示.                                                                                                                                                                                     |
| 整数/经度   | 整数/长参数类型允许您将十进制值传递到 JavaScript 动作。 在生成的 JavaScript 动作代码中，这种类型将表示为 [大](https://www.npmjs.com/package/big-js) 对象。                                                                                                                                           |
| 字符串     | 字符串参数类型允许您将字符串值传递到 JavaScript 操作。                                                                                                                                                                                                                         |

#### 2.2.3 类别

在 [JavaScript 行动调用](javascript-action-call) 中使用类别来区分参数。 当您的应用有几个参数时，类别对逻辑参数组是有用的。 如果您没有指定类别，参数将出现在 **输入** 组中。

#### 2.2.4 描述

对于有多个参数的应用，描述可以作为参数确切用途的有用提示。 描述还允许您向应用合作者描述您的参数。 描述可以包含大写和小写字母、数字和符号。

### 2.3 返回类型

返回参数类型决定一个 JavaScript 动作返回的数据类型。 因为许多API是异步的，您也可以返回解析此类型的 `承诺` 对象。 JavaScript 动作的返回值可以给出一个名称并存储，以便它可以用于调用的 nanoflow 中。 对于你可以用作参数的所有类型，你也可以使用返回类型。 此外，如果没有数据从该动作返回，您可以使用返回类型“无”。

## 3 类型参数

类型参数是实体类型的占位符，当调用nanoflow时，该实体类型将填充特定实体。 在配置参数的数据类型时可以使用类型参数， 它允许用户传递任意实体类型的对象或列表。 可以轻松添加、编辑或删除：

{{% image_container width="450" %}}![type parameter](attachments/javascript-actions/type-parameter.png){{% /image_container %}}

JavaScript 动作可以有零或更多类型参数。 每个类型参数应该有一个唯一的名称。

## 4 以Nanoflow Action

在 **以nanoflow 动作** 标签页显示时，可以将JavaScript 动作作为纳米动作暴露。 这个示例动作已经获得 *示例动作* 标题文本，分配 *Workshop* 作为其类别，并且没有给出图标：

{{% image_container width="450" %}}![expose action](attachments/javascript-actions/expose-jsaction.png){{% /image_container %}}

在编辑您选择的类别中的 nanoflow 时，暴露JavaScript 动作会使它出现在 **工具箱** 窗口。 当这个动作被用在 nanoflow 中时，它将显示您提供的标题和图标。 类别和字幕在这里显现，默认图标被显示为没有自定义图标：

![工作室曝光](attachments/javascript-actions/workshop-exposed.png)

### 4.1 标题

曝光JavaScript操作时需要一个标题。 此字幕将伴随你的 JavaScript 动作在 nanoflow **工具箱** 窗口，并且可以在那里提供关于你的 JavaScript 动作的有用的提醒信息。

### 4.2 类别

曝光JavaScript操作时需要一个类别。 在nanoflow **工具箱** 窗口中使用类别组织类似目的的 JavaScript 动作。

### 4.3 图标

当曝光JavaScript操作时，图标是可选的。 当没有选择图标时，使用默认的 JavaScript 动作图标。 建议的图标大小为16x16像素。

## 5 文件

在 **文档** 标签页中，按 **编辑** 来记录一个 JavaScript 动作：

{{% image_container width="450" %}}![documentation](attachments/javascript-actions/documentation-pro.png){{% /image_container %}}

文档在 **代码** 选项卡中可见。 您的文档也被复制到JavaScript操作中，作为相应函数的 *.js* 文件的评论：

{{% image_container width="450" %}}![documentation js file](attachments/javascript-actions/documentation-js-file.png){{% /image_container %}}

## 6 个代码

在 **代码** 标签中，您可以不离开Studio Pro编辑JavaScript操作代码。 编辑器基于 [Monaco 编辑器](https://microsoft.github.io/monaco-editor/index.html)。 它提供了诸如语法高亮和代码完成等功能。 代码可以写入现代JavaScript(ES8/ES2017)，并且可以使用像 `async` 这样的功能， `等待` 和 `承诺`。

代码有三个部分：导入列表、一个额外的代码块和一个用户代码块。 添加的所有代码都应该在其中一个模块中。 当部署或更新JavaScript操作设置时重新生成模板代码时，区块外的代码将丢失。

额外的导入应该从 `导入` 开始，并放置在 `/ BEGIN EXTRA CODE` 上。 额外代码应该放置在 `// BEGIN USER 代码` 和 `// END USER 代码` 之间。 用户执行代码应该放置在 `// BEGIN EXTRA 代码` 和 `/ END EXTRA 代码` 之间。

``` js
// 此文件由 Mendix Studio Pro生成。
//
// 警告: 只有以下代码将在重新生成操作时保留：
// - 导入列表
// - BEGIN UER CodDE 和 END USER CodDE 之间的代码
// - BEGIN EXTRA CodE 和 END EXTRA CDE
// 其他代码下次部署项目时会丢失。
从 "big.js"导入 { Big } ；

// BEGIN EXTRA Code
 function sayHello(message) Windows
     window。 lert("Hello: " + message);
 }
// END EXTRA 代码

/**
 * 向用户显示警告消息。
 * @param {string} 消息-向用户显示消息。
 * @return {Promise.<void>
 */
导出异步函数 Hello(消息) *
    // BEGIN USER CODE
    sayHello(消息);
    退货承诺。 esolve();
    // END USER CODE
}
```

## 7 阅读更多

* [JavaScript 动作调用](javascript-action-call)
* [纳诺夫拉](nanoflows)
* [生成 JavaScript 操作](/howto/extensibility/build-javascript-actions)
* [Java 行动电话](java-action-call)
* [微流程呼叫](microflow-call)
