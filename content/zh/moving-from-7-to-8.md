---
title: "从桌面模型版本7移动到Studio Pro 8"
category: "常规信息"
menu_order: 20
description: "提供关于将您的项目从桌面Moderr 版本7升级到Studio Pro 版本8的详情， 包括关于转换您的项目和废弃功能的章节。"
tags:
  - "studio pro"
---

## 1 导言

将您的 Mendix 应用程序从桌面Moderr 版本7 转换为 Studio Pro 版本8, 建议你们采取一系列步骤。 这些都在下面的 [转换您的应用程序](#converting)中被记录。

关于Mendix 8中新功能的信息，请参阅 [Studio Pro 8 版本说明](/releasenotes/studio-pro/)。

## 针对工作室的 Mendix 7 升级到 8

{{% alert type="warning" %}}
由于Mendix 8版本的更改已经中断，Studio中的应用无法通过常规Studio升级机制自动升级。
{{% /报警 %}}

这意味着：

* 在Studio中构建的现有应用将保持在他们当前的Mendix 版本中，并且可以升级到最新版本的 Mendix 。

    {{% alert type="info" %}}If your app was created in Studio Pro, using a Mendix 8 Beta version, it will be upgraded to the release version of Mendix 8 automatically.
    {{% /报警 %}}

*  从现在起您在Studio中创建的任何应用程序都会从一开始就有 Mendix 版本 8

开发者想要将他们现有的 Mendix 版本 7 Studio 应用程序升级到Mendix 版本 8 只能在Studio Pro 中按照 [转换您的应用程序](#converting)的指示这样做， 以下：

### 2.1 与Studio的合作发展

如果您的原始工程是 Mendix 版本 7.23。 或更低的版本，您想要使用 Mendix Studio 与开发人员合作，您需要将您的项目升级到 Mendix 版本 7。 3.3或以上。 您不能在没有升级的情况下将您的更改同步到Studio。

## 3 在升级到 Mendix 8 Studio Pro 之前对您的应用进行更改

在</em> 升级到 Mendix 8 之前，您可能需要对您的应用程序进行更改 *。</p>

### 3.1 Java 版本，废弃 & 移除API。 {#deprecated-apis}

Mendix 8 运行在 Java 11, Mendix 7 运行在 Java 8。 请确保您的 Java 操作与 Java 11兼容。 官方的 Java 8 到 11 迁移指南可以在 *Oracle JDK 迁移指南* 的 [迁移中找到。从 JDK 8 迁移到 Layer JDK Releases](https://docs.oracle.com/en/java/javase/11/migrate/index.html#JSMIG-GUID-7744EF96-5899-4FB2-B34E-86D49B2E89B6) 部分。

已废弃的 Java 操作应该在 Mendix 7 中修复，然后您将应用程序迁移到 Mendix 8。

通过导入您的 Java IDE （例如Ecliple）并审查和解决所有偏离的问题，修复您的 Java 操作中的废弃之处。

Details of removed and deprecated APIs will be added to the *Breaking Changes* section of the [Studio Pro 8 release notes](/releasenotes/studio-pro/).

### 3.2 Atlas兼容性

移动到Mendix 8之前，请确保您使用最新的 Mendix 7 兼容的 Atlas 版本 1.2.4。 通过首先更新Atlas到这个版本，您将会在Mendix 8迁移后防止与设计属性有关的几个错误。

如何更新到Atlas1.2.4：

1. 如果您在 Studio Pro Atlas UI 资源模块中自定义了任何内容，请检查，因为更新Atlas将覆盖该模块的所有内容。 更新前将您的自定义内容移出Atlas界面模块。
2. 检查您是否在您的 Mendix 项目中自定义了 **主题** 文件夹。 如果是，将 **主题** 文件夹重命名为其它东西，如 *theme_older*。
3. 通过打开Studio Pro中的市场更新Atlas，搜索 *Atlas UI 资源*， 点击 **所有版本** 面板，然后下载 **Atlas UI 资源 v1。 4**
4. 提示时，选择替换您现有的Atlas模块。

{{% alert type="info" %}} You do not have to move any customized files from **theme_oldest** to **theme** yet, as after migrating to Mx8, you will update Atlas again which will create a new **theme folder**.{{% /alert %}}

## 4 转换您的应用程序 {#converting}

以下小节解释了将您的应用程序从 Mendix 7 转换为 Mendix 8 的步骤。

### 4.1 备份您的项目

请确保您已经向团队服务器提交了您的最新更改， 或者在您开始转换之前备份您的本地项目。

### 4.2 升级到最新版本7版本 {#upgrade}

{{% alert type="warning" %}}
技术上您需要升级您的应用到最新版本的 Mendix 7 ，它是 [7.23](/releasenotes/studio-pro/7.23)。 您只能将您的应用程序从 7.23.x 转换为 Mendix 8。
{{% /报警 %}}

要升级到Mendix 7，请遵循以下步骤：

1. 下载桌面模式模组最新版本 [7.23](/releasenotes/studio-pro/7.23)
2. 在 Desktop Model 7.23.x 中打开您的应用程序。
3. 允许它在必要时升级应用程序。

### 4.3 审查您的 Mendix 7 项目

在升级到Mendix 8之前，请结合下面的章节审查您的应用，并评估是否需要采取进一步行动。

In particular, it is easier to fix deprecations in Java actions (see [Java Version, Deprecated and Removed APIs](#deprecated-apis)) in Mendix 7 before upgrading to Mendix 8. 然而，仍然存在着这种情况。 浮点数和货币废弃错误将更容易修复Mendix 8中的错误(说明请参阅下面 [类型浮点 & 货币](#float-currency))。

### 4.4 保存版本7项目

您的应用现已准备好升级到 Mendix 版本 8。

建议您此时备份/提交您的项目，以便您在必要时可以返回。

您现在可以关闭桌面模型第7版中的项目。

### 4.5 将您的应用升级为第8版

Mendix 将为您升级您的应用。

在 Mendix Studio Pro 版本 8 中打开项目，并允许Studio Pro 将您的应用程序更新到版本 8。

### 4.6 审核错误，警告 & Studio Pro 中已废弃的

审查所有错误消息和关于废弃项目的消息，并在必要时做出修改。

如果您正在使用已废弃数据类型货币或浮点型变量，您将会看到错误。 更多信息请参阅下面第 [部分浮动类型 & 货币](#float-currency)

### 4.7 升级所有部件

为了尽量减少出现问题的可能性，您应该更新项目使用的所有小部件和其他应用市场模型到最新版本。

检查市场中是否有更新版本的市场模块。 读取市场版本发布笔记，查看升级时是否需要执行特定操作。

一般而言，您不应删除和重新导入模块，除非在发行说明中推荐这样做。 如果您确实删除并重新导入它们，您可能会丢失与模块相关的数据或配置。

### 4.8 审核 & 测试您的应用

最后，查看下面的章节，并确保您已经做出了所有必要的更改。

测试任何意外的结果。

{{% alert type="success" %}}
恭喜！ 您的应用已成功升级到Mendix 8并且您可以继续正常工作。
{{% /报警 %}}

## 5 类型浮点型 & 货币的元素 {#float-currency}

Mendix 版本 7 中已废弃浮动和货币类型，现已从 Mendix 版本 8 中删除。

下面类型浮动或货币的元素将报告版本8中的错误：

* 属性
* 常数
* 创建变量动作
* 数据集列和参数
* 微流程/nanoflow 参数和返回类型
* Java/JavaScript 动作参数和返回类型
* 函数“格式浮动”、“parseFloat”和“toFloat”

可以在单个操作中修复大多数废弃错误。 为了做到这一点，请采取以下行动：

1. 在 Studio Pro 8 中找到支持货币和 Float 数据类型的错误消息。

    ![错误消息：不再支持货币和浮点数](attachments/moving-from-7-to-8/currency-float-error.png)

2. 右键单击错误消息。

    ![手动或自动更改？](attachments/moving-from-7-to-8/currency-float-change-options.png)

3. 点击 **将全部转换为 Decimal** 自动转换所有属性。

    ![将所有浮点和货币转换为小数点时警告](attachments/moving-from-7-to-8/convert-to-decimal-warning.png)

4. 点击 **将全部转换为 十进制** 来进行转换。

{{% alert type="warning" %}}
如果在此过程中有任何属性已被转换 下次在本地运行您的应用或部署数据库将被转换为支持新的属性类型。

**此数据库转换可能需要很长时间！** 我们建议您首先在一个有代表性的数据集上测试数据转换。 您可以估计转换您的生产数据库需要多长时间。
{{% /报警 %}}

## 6 64-Bit Studio Pro

Mendix 桌面Moderr 版本 7 是 64 位应用程序，但也可以在 32 位上运行。

Mendix Studio Pro is a 64-bit application which will **only** run on 64-bit versions of Windows. 这必须是 Windows 7 的64位版本，服务包1或更多。

## 7 Mendix Cloud 版本 3

Apps made in Mendix Studio Pro cannot be deployed to *Version 3* of the Mendix Cloud. 如果您正在使用一个授权的Mendix Cloud v3节点，我们建议您升级到 Mendix Cloud v4。 如果不可能，您将需要继续使用 Mendix 版本 7 来创建和维护您的应用程序。

## Java 代码生成 8 {#java-code-generation}

在 Mendix Studio Pro 版本8中，我们正在改变我们为 Java 操作和数据集生成Java 代码的方式。

Mendix Desktop Moderr 版本 7 有时在Java 动作和数据集参数名称中添加了一个后缀(例如， `参数1`)。 这种行为是防止生成代码中出现名称冲突所必需的。 在Mendix Desktop Moderr 7的次要版本中，我们引入了一些修复方法来防止这些冲突发生，使这种行为变得多余。

我们还注意到，试图防止发生这些冲突， 我们有时导致Java 编译失败，这似乎与你正在进行的工作完全无关。 由于现在完全没有必要再加上一个后缀，对更大的应用提出了相当多的问题，我们决定完全取消它。

这在实践中意味着什么？ 对于大多数应用，没有任何变化和一切仍然能够正常工作。 但在数量有限的情况下，Mendix Desktop Moderr 版本 7 将为您的参数名称引入一个后缀。 例如，在生成的 Java 代码中，名为 `客户` 的参数可能变成 `CustomerParameter1`。 当您将您的应用程序迁移到 Mendix Studio Pro 8时，这个后缀将被删除。

在这几个情况下，你需要做一个简单的修复，然后你的代码才能重新编译：

* 如果它是从市场下载的模块中的 Java 操作，正在造成错误， 只需重新下载或更新到最新版本
* 如果这是你自己的 Java 动作， 然后修复会变得更加容易——只需从您的 Java 代码中删除这些帖子修复(在前一个例子中)。 `客户参数1` 刚刚变成 `客户`)。

### 8.1 差异的例子

在这个示例中，我们有一个名为 `LogMessage`的Java 动作，它有一个名为 `Message` 的参数。 在 Mendix Moderr 版本7 中，如果您引入了一个域模型实体，也叫做 `消息`， 我们将为您生成以下Java 代码 (请注意，某些代码被省略为可读性)：

```java
        public LogMessage(IContext context, java.lang. tring MessageParameter1)
        让您
            super(context);
            essageParameter1 = MessageParameter1;
        }
        @java. override
        public java ang.Boolian executeAction() plas Exception
        }
            // BEGIN USER CODE
            Core. etLogger("MyLogger").info(这个) essageParameter1;
            // 结束用户代码
}
```

你可以看到，而不是命名参数 `消息` 现在是 Mendix Moderr 版本 7 名称 `MessageParameter1`。 在 `executeAction()` 方法的用户代码中， `这个。消息` 用于记录消息。 这意味着代码不会被编译。

Studio Pro 8将为您生成以下代码：

```java
        public LogMessage(IContext context, java.lang. tring Messagee
        Group
            super(context);
            essage = Message；
        }
        @java。 override
        public java ang.Boolian executeAction() plas Exception
        }
            // BEGIN USER CODE
            Core. etLogger("MyLogger").info(这个) 作品；
            // 结束用户代码
}
```

这个代码按预期行事，可以在盒子中施行。 然而，如果您先前修改了您的用户代码，以符合Mendix Moderr 版本7生成此代码的方式。 您只需要更新您的用户代码才能使用新的参数名称。

## 9 疑难解答

### 9.1 无法打开项目： `布局 … 值无效 …`

极少， 您可以在打开Mendix Studio Pro 8的项目时收到一个类似于下面的消息，这个项目需要从上一个版本的Mendix 升级。

![布局错误消息](attachments/moving-from-7-to-8/layout-import-message.png)

当布局为 **布局类型** 有无效值时发生这种情况。 这仍将导致一个错误， *即使无效的布局已经从项目中删除*。

请参阅下面的图像以了解您在项目中发现错误的位置。

![布局位置错误](attachments/moving-from-7-to-8/layout-error-location.png)

要解决这个问题，请使用前一个版本的Mendix 更改无效的 **布局类型** (在上面的示例中)。 `遗产`为有效值。

### 9.2 DOM和Atlas界面问题

Mendix 8伴随着其DOM结构的一些改进。 这些DOM更改将影响应用的 Sass 样式。 由于这些更新，Mendix 8 应用程序将使用 [Atlas UI 资源](/appstore/modules/atlas-ui-resources) (v2.0.0 或更高版本)完成。 升级您的 Atlas UI 可能会导致您的应用主题出现问题。 要解决DOM或Atlas UI的迁移问题，请查阅以下文件：

* [故障排除DOM更改](migration-dom-issues)
* [Atlas UI更改故障排除问题](migration-atlas)
