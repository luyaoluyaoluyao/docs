---
title: "D. 排除合作发展问题"
parent: "协作发展"
description: "描述Mendix 桌面Modeler 和 Mendix Web Modeler 之间协作开发的故障排除问题"
tags:
  - "桌面模组"
  - "合作发展"
  - "故障排除"
  - "疑难解答"
---

## 1 导言

{{% alert type="warning" %}}

只有当您的项目有 Mendix 版本 7.23.3 或以上时，协作开发才可用。 如果您的项目有 Mendix 7.23.2 或以下版本，您不能将您的更改同步到 Web Moderr 。

您仍然可以在 Web Moderr 中打开您的项目 (Web Moderr 将自动升级到最新版本的7)。 3. 选举主席团成员。  然而，要同步来自 Web Moderr 的更改，您必须使用Mendix 桌面Moderr 版本7.23.3或以上。

{{% /报警 %}}

合作发展使用户能够相互交流模式变化。 此文档将帮助您解决在与 Web Modeler 共享更改过程中可能发生的问题。

## 2 概念

关于概念和定义，见 [2 Concepts](version-control#concepts) in *版本控制*。

## 3 Web Moderr 不同步 {#out-of-sync}

通常情况下，当桌面建模用户更新或提交时，Web 建模工作副本会与桌面建模同步. 然而，如果在桌面模型外发生了提交或更新(使用 Tortoise SVN 或任何其他版本控制工具)， Web Modeler是暂时不同步。 在这种情况下，您将收到一个警告：

![](attachments/collaborative-development-troubleshooting/changes-are-out-of-sync.png)

您可以做以下事情之一：

1.  **合并** (推荐)-- 桌面模式将尝试自动合并来自Web Modeler 的未同步更改。 您的本地更改(如果有的话)将会与 Web Moderr 更改合并。 Web Modeler的更改存储在一个自动创建的分支中，以确保过程中没有丢失的更改。 分支在分支线管理器中可见。 这个过程可以产生以下结果之一： <br/>

    a.  如果合并过程成功完成(没有冲突)，创建的分支将合并到您的工作副本，并获得Web Modeler的更改。 您需要审阅已合并的更改并提交它们以使Web Moder和桌面Moder再次同步。 然后您可以删除自动创建的分支。<br/>

    b. 会议文件。 如果在这个过程中发现任何合并冲突，你需要解决它们，然后进行更改。 一旦您解决冲突并提交更改，您可以删除此自动创建的分支。<br/>

    ![](attachments/collaborative-development-troubleshooting/automatically-created-branch.png)

2. **稍后解决** — — 更改可以稍后合并. 与此同时，Web Modeler和团队服务器开发线的更改将不会同步进行。 在这种情况下，当提交/更新/合并更改时，对话框将再次出现。

## 4 未能合并桌面模式和Web Moderr 更改

当网络建模启用分支与桌面建模模式外的提交正在与另一行合并。 您将看到以下消息：

![](attachments/collaborative-development-troubleshooting/cannot-merge-automatically.png)

您可以选择以下一种：

1.  **取消合并** (推荐) - 您可以取消进程并先尝试与 Web Moderr 同步。 做以下操作：<br/> a。  打开 Web Modeler 启用的开发行<br/> b。  [3 节中描述的警告将会显示Web Moderr & 的桌面模型退出](#out-of-sync)<br/>

    ![](attachments/collaborative-development-troubleshooting/changes-are-out-of-sync.png)<br/>

    b. 会议文件。 点击 **合并** 以与 Web Modeler 同步更改。<br/>

    b. 平均输出功率超过1瓦； 打开上一个分支并重新合并.

2. **无论如何合并** - 合并将继续进行，不会从 Web Modeler 做任何更改。 在这种情况下，只会包含桌面模型的更改。 桌面模型和Web Modeler将无法同步，您将需要稍后解决这个问题。 查看 [3 桌面建模器 & Web 建模已失去同步](#out-of-sync)

## 5 仓库服务不可用

在 **更新** 操作期间，要求从 Web Moderr 进行更改并整合到当前项目。  更新过程中有一个额外步骤 **获取分支状态**。 在这个步骤中，获取WebModeler更改.

![](attachments/collaborative-development-troubleshooting/retrieving-branch-status.png)

如果存在网络或服务问题，桌面模型将无法联系资源库服务并显示警告信息：

![](attachments/collaborative-development-troubleshooting/changes-are-not-retrieved.png)

您可以做以下事情之一：

1. **取消** (推荐) - 操作将被取消，您可以稍后在网络问题解决后重试

2. **继续** - 更新进程将继续，但是无法检索WebModeler的更改。 桌面模型和Web Modeler将无法同步，您将需要稍后解决这个问题。 查看 [3 桌面建模器 & Web 建模已失去同步](#out-of-sync)

## 6 另一项行动正在进行中

当您的团队成员启动阻止操作(提交/更新/合并网页Modeler启用分支/切换网页Moder启用分支) 同时，您也启动了一个屏蔽操作，您将看到下面的对话框：

![](attachments/collaborative-development-troubleshooting/another-operation-in-progress.png)

您可以做以下事情之一：

1. **取消** (推荐) - 操作将被取消。 我们建议您在几分钟后进行更新，以便您获得最新的更改，您的工作副本和Web Modeler将会同步
2. **继续** - 更新进程将继续，但是无法检索WebModeler的更改。 桌面模型和Web Modeler将无法同步，您将需要稍后解决这个问题。 查看 [3 桌面建模器 & Web 建模已失去同步](#out-of-sync)

## 7 阅读更多

* [版本控制](version-control)
* [Web Modeler 中的协作开发](/studio7/general-collaborative-development)
