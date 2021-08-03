---
title: "D. 排除合作发展问题"
parent: "协作发展"
description: "描述Mendix Studio Pro 和 Mendix Studio 之间合作开发故障排除问题"
tags:
  - "studio pro"
  - "工作室"
  - "合作发展"
  - "故障排除"
  - "疑难解答"
---

## 1 导言

合作发展使用户能够相互交流模式变化。 此文档将帮助您解决在与 Mendix Studio 共享更改过程中可能出现的问题。

## 2 概念

关于概念和定义，请参阅 *版本控制* 中的 [概念](version-control#concepts) 部分。

## 3 工作室不同步 {#out-of-sync}

通常情况下，工作室的工作副本在Studio Pro 用户更新或提交时与Studio Pro 同步。 然而，如果在Studio Pro 之外发生了提交或更新(使用 Tortoise SVN 或任何其他版本控制工具)， 工作室暂时脱离同步。 在这种情况下，您将收到一个警告：

![](attachments/collaborative-development-troubleshooting/changes-are-out-of-sync.png)

您可以做以下事情之一：

1.  **合并** (推荐)-- Studio Pro 将尝试自动合并工作室中未同步的更改。 您的本地更改(如果有的话)将与工作室的更改合并。 工作室的更改存储在一个自动创建的分支中，以确保过程中没有丢失的更改。 分支在分支线管理器中可见。 这个过程可以产生以下结果之一： <br/>

    a.  如果合并过程成功完成(没有冲突)，创建的分支将合并到您的工作副本，并且您将得到工作室的更改。 您需要查看合并的更改并提交它们以使Studio 和 Studio Pro 再次同步。 然后您可以删除自动创建的分支。<br/>

    b. 会议文件。 如果在这个过程中发现任何合并冲突，你需要解决它们，然后进行更改。 一旦您解决冲突并提交更改，您可以删除此自动创建的分支。<br/>

    ![](attachments/collaborative-development-troubleshooting/automatically-created-branch.png)

2. **稍后解决** — — 更改可以稍后合并. 同时，工作室和团队服务器开发线的更改将不会同步进行。 在这种情况下，当提交/更新/合并更改时，对话框将再次出现。

## 4 合并工作室专业版和工作室更改失败

当在Studio Pro 之外提交的工作室启用分支与另一行合并时，您将看到以下消息：

![](attachments/collaborative-development-troubleshooting/cannot-merge-automatically.png)

您可以选择以下一种：

1.  **取消合并** (推荐) - 您可以取消进程并先尝试与 Studio 同步。 做以下操作：<br/> a。  打开工作室启用的开发行。<br/> b.  [Studio Pro & Studio 不再同步](#out-of-sync) 部分中描述的警告将被显示。<br/>

    ![](attachments/collaborative-development-troubleshooting/changes-are-out-of-sync.png)<br/>

    b. 会议文件。 点击 **合并** 与工作室同步更改。<br/>

    b. 平均输出功率超过1瓦； 打开上一个分支并重新合并.

2. **无论如何合并** — — 合并将在不改变工作室的情况下继续。 在这种情况下，将只包含Studio Pro 中的更改。 Studio Pro and Studio 将无法同步，您将需要稍后解决这个问题。 查看 [Studio Pro & Studio 退出了同步](#out-of-sync) 部分。

## 5 仓库服务不可用

在 **更新** 操作过程中，需要从Studio进行更改并整合到当前应用中。  更新过程中有一个额外步骤 **获取分支状态**。 在此步骤中，将检索工作室的更改。

![](attachments/collaborative-development-troubleshooting/retrieving-branch-status.png)

如果存在网络或服务问题，Studio Pro 将无法联系资源库服务并显示警告信息：

![](attachments/collaborative-development-troubleshooting/changes-are-not-retrieved.png)

您可以做以下事情之一：

1. **取消** (推荐) - 操作将被取消，您可以稍后在网络问题解决后再试。

2. **继续** - 更新进程将继续，但工作室的更改将无法检索。 Studio Pro and Studio 将无法同步，您将需要稍后解决这个问题。 查看 [Studio Pro & Studio 退出了同步](#out-of-sync) 部分。

## 6 另一项行动正在进行中

当您的团队成员启动阻止操作 (提交/更新/合并启用工作室分支或切换启用工作室分支) 同时，您也启动了一个屏蔽操作，您将看到下面的对话框：

![](attachments/collaborative-development-troubleshooting/another-operation-in-progress.png)

您可以做以下事情之一：

1. **取消** (推荐) - 操作将被取消。 我们建议您在几分钟后进行更新，以便您能够获得最新的更改，您的工作副本和工作室将保持同步。
2. **继续** - 更新进程将继续，但工作室的更改将无法检索。 Studio Pro and Studio 将无法同步，您将需要稍后解决这个问题。 查看 [Studio Pro & Studio 退出了同步](#out-of-sync) 部分。

## 7 阅读更多

* [版本控制](version-control)
* [合作开发工作室](/studio/collaborative-development)
