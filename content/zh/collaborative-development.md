---
title: "合作开发工作室"
category: "合作"
description: 本文件从Mendix Studio的角度介绍Mendix Studio与Mendix Studio之间的合作开发过程。
tags:
  - "工作室"
  - "合作发展"
  - "同步"
menu_order: 10
---

## 1 导言

{{% alert type="warning" %}}

只有当您的应用有 Mendix 版本 7.23.3 或以上时，协作开发才可用。 如果您的应用有 Mendix 版本的 7.23.2 ，您不能与 Studio Pro 同步您的更改。

您仍然可以在 Studio 中打开您的应用程序。 然而，要同步Studio 和 Studio Pro之间的更改，Studio Pro 必须升级到7.23.3 或以上版本。

{{% /报警 %}}

Collaborative development is the process that allows team members work together on one app in Mendix Studio Pro and Mendix Studio and easily synchronize changes made by others using [version control](/refguide8/version-control).

如果您正在一个团队(或从工作室切换到工作室专业版)，分享应用模型更改是容易的。 工作室中的所有更改都是自动保存的。 Studio Pro 用户点击 **更新** 或 **提交** 时获得这些更改。 如果他们提交，他们同时推送自己的更改，所以Studio 和 Studio Pro 都是同步的。 欲了解更多技术性和详细的进程概述，请在 *Studio Pro Guide* 中查看 [Collaborative Development](/refguide8/collaborative-development)

多个用户可以同时在工作室查看应用程序：一个用户可以编辑它，其他用户则处于只读模式。

## 2 概念

关于概念和定义，见 [2 Concepts](/refguide8/version-control) in *版本控制*。

## 3 从工作室角度看合作发展

因为所有工作室更改已自动保存， 合作开发通过弹出窗口表示。当应用程序的内容被更改或同步时。 在下列情况下可以做到这一点：

1. **正在提交您的更改** - 如果您的团队成员正在工作Studio Pro 中的同一条开发线，他们点击 **更新**您的屏幕会被锁定几分钟，您的更改会自动提交团队服务器，然后应用到Studio Pro。 欲了解更多关于Studio Pro合作发展进程的信息 查看 [4 Studio Pro Perspective](/refguide8/collaborative-development) in *Collaborative Development* in *版本控制*。

    {{% image_container width="350" %}}![正在提交更改对话框](attachments/collaborative-development/committing-changes.png)
   {{% /image_container %}}

2.  **同步更改** - 每次Studio Pro 用户提交时，您的屏幕会被锁定几分钟。 <br/>

    {{% image_container width="350" %}}![正在同步更改对话框](attachments/collaborative-development/synching-changes.png)<br/>

    {{% /image_container %}}

    这一进程有两种可能的结果：<br/>

    a.  在 Studio Pro，应用程序中没有冲突，Studio Pro 的更改将适用于Studio 。 (冲突是相互矛盾的变化，不能自动合并。) 例如，一个用户更改了按钮的标题，而另一个用户删除了此按钮)。

    b. 会议文件。  在Studio Pro 中，在Studio Pro 用户能够再次提交之前，有一些应用冲突需要解决。 您的屏幕已解锁，但您的应用没有任何更改。

3.  **切换内容** - 在 Studio Pro中，用户可以更改分支线工作室已启用。 关于管理分支的更多信息 在 *协作发展* 在 *Studio Pro 指南* 中查看 [管理开发线](/refguide8/collaborative-development#managing-branches) 部分。 在此进程工作室被锁定几分钟，所有更改都会自动保存到当前的开发线。 并且显示一个弹出式对话框，Studio Pro 用户正在更改Studio的分支线。 这意味着您的应用程序的内容将会改变。

    {{% image_container width="350" %}}![切换内容对话框](attachments/collaborative-development/switching-branches.png)
    {{% /image_container %}}

## 4 阅读更多

* [版本控制](/refguide8/version-control)
* [合作发展](/refguide8/collaborative-development)

