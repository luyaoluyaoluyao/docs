---
title: "合作发展"
category: "版本控制"
description: "描述Mendix 桌面Modeler 和 Mendix Web Modeler 之间的协作开发过程"
tags:
  - "桌面模组"
  - "合作发展"
  - "同步"
aliases:
  - /howto/web-model/syncing-webmodel-desktop.html
  - /refguide7/desktop-webmodeler.html
  - /refguide7/sync-webmodeler-desktopmodeler.html
  - /web-model/general-sync-webmodel-desktopmodel-wm.html
---

## 1 导言

{{% alert type="warning" %}}

只有当您的项目有 Mendix 版本 7.23.3 或以上时，协作开发才可用。 如果您的项目有 Mendix 7.23.2 或以下版本，您不能将您的更改同步到 Web Moderr 。

您仍然可以在 Web Moderr 中打开您的项目 (Web Moderr 将自动升级到最新版本的7)。 3. 选举主席团成员。  然而，要同步来自 Web Moderr 的更改，您必须使用Mendix 桌面Moderr 版本7.23.3或以上。

{{% /报警 %}}

协作开发是一个由多人组成的团队在应用上工作时共享应用模式变化的过程。 协作开发使团队成员能够在桌面模式模组和Web Modeler中一起工作一个项目，并使用 [版本控制](version-control) 轻松同步更改。 桌面模型可以用于应用的不同分支， 在这些分支中可以启用Web Modeler。

如果你以前从未使用过Mendix Web Modeler，你需要先启用它来开发一行。 欲了解更多关于管理开发线的信息，请在桌面模式模组</a> 部分中查看
管理开发线。  </p> 



## 2 协作发展概览

桌面模型用户可以通过 [版本控制](version-control) 通过 **提交** 和 **更新** 操作进行合作。 

桌面模型和Web Modeler之间的协作开发过程包括以下步骤：

1. Web Modeler每次修改都会自动保存到 Web Moderr 工作副本。 多个用户可以同时查看 Web Moderr 中的项目：一个用户可以编辑它，其他用户则处于只读模式。 

2.  当桌面建模用户打开一个项目时，如果此开发行启用Web Modeler，他们会收到通知。 
   
   ![协作开发启用通知](attachments/collaborative-development/collaborative-development-enabled-notification.png)

3. 桌面建模创建一个本地工作副本，桌面建模用户可用。 要从团队服务器获取更改，用户需要点击 **更新** (然后从团队服务器检索最新版本) 包含来自其他桌面模式用户的提交以及来自网页模式的最新更改）。

4. 在桌面建模后，用户点击 **更新**Web Modeler的最新更改将在桌面建模收到更新之前自动提交给团队服务器。 来自团队服务器的最新版本已合并到桌面模式的本地工作副本。 

5.  桌面建模用户在项目上工作，一旦用户完成某些功能（例如） 修复错误或创建一个新功能)，他们点击 **提交**。 用户输入提交消息并予以确认。 这会触发一个与更新过程相同的过程(步骤4所述)。 和桌面Modeler的工作副本与团队服务器的最新版本一起更新。
   
   这种合并有两种可能的结果：<br/>
   
   a.   没有冲突，桌面模型用户的更改将被提交给团队服务器。 然后，Web Modeler 会从团队服务器获取最新版本并解锁； Web Modeler用户可以看到桌面建模。 其他桌面建模用户在更新后将得到更改。 <br/>
   
   b. 会议文件。 有冲突，桌面建模提交进程已停止。 Web Modeler已解锁，但没有从桌面建模用户处获取更改。 桌面模型用户需要先解决合并冲突，然后才能再次提交。

{{% alert type="info" %}}

当桌面建模用户想要将应用程序部署到云端时，他们点击 **运行** 按钮。 在这个过程中自动完成提交，步骤五已执行。 

{{% /报警 %}}



## 3 Web Moderr 视图

For information on collaborative development from the Web Modeler perspective, see [Collaborative Development in the Web Modeler](/studio7/general-collaborative-development) in the *Web Modeler Guide*. 



## 4 台式电脑建模视图

当您连接到一个已开启协作开发的项目时， 您看到Web Modeler启用了哪一条开发线 (主行或分支行)。 

点击下拉菜单选择另一行或点击 **确定** 打开当前选中的行。 

![打开应用对话框窗口](attachments/collaborative-development/open-app-dialog.png)



### 4.1 合并最新更改

合并团队服务器中存储的最新更改(来自Web Modeler用户和其他桌面Modeler用户)， 打开 **更改** 并点击 **更新**。

![更新选项](attachments/collaborative-development/update-button.png)



### 4.2 合并最新更改

若要提交您最新的项目更改并将其提供给其他用户，请打开 **更改** 并点击 **提交**。 部署您的应用程序 (当您点击 **运行** 按钮时) 的进程也会触发提交。 

{{% alert type="info" %}}

我们建议您更新您的项目，并经常提交更改，以避免您的项目中的多次冲突。 

{{% /报警 %}}

如果您的项目有冲突，Web Modeler将会被解锁，而不会收到您的更改。 您需要先解决桌面模型中的冲突才能完成合并并再次提交。 

如果没有冲突，您的更改将自动发送到Web Modeler。 For more information on the collaborative development process in the Web Modeler, see [Collaborative Development in the Web Modeler](/studio7/general-collaborative-development) in the *Web Modeler Guide*.



### 4.3 查看承诺历史

您可以通过 **项目** > **更多版本** > **历史记录** 看到所有对当前开发行的更改

![历史对话框](attachments/collaborative-development/history.png)





## 5 管理桌面模式下的开发线 {#managing-branches}

在桌面模型中，您可以为开发线开启Web Moder（主行或分支线）。 您也可以创建和删除分支行。 

为了协作开发，您需要启用 Web Moderr 作为开发线之一。 



### 5.1 使Web Modeler成为开发线 {#active-branch-for-the-wm}

若要在 Web Modeler 和 Desktop 模式之间共享您的模型更改，您需要启用 Web Moderr 作为开发行之一。 

Web Moderr 是否默认为开发线启用，取决于您的项目：

* Web Modeler 默认在以下情况下启用主行： 
    * 通过开发者门户创建的新项目
  * 对于已启用 Web Moderr 的现有项目
* Web Modeler没有为以下情况的任何开发线启用： 
    * 通过桌面建模创建的新项目
  * 对于一个尚未启用 Web Moderr 的现有项目

为了启用 Web Modeler 以开发线或切换到另一个开发线，请做以下工作： 

1.  点击 **项目** > **更多版本** > **管理分支行**. 在 **分支行管理器** 对话框窗口， 您可以看到Web Moderr 已启用的开发行(如果有的话)在第一列中用地球图标标记。<br/> 
   
   ![分支行管理器中的球形图标](attachments/collaborative-development/globe-icon.png)<br/>

2.  选择您想要启用 Web Moderr 的行，并点击 **为Web Moderr** 开启。 <br/>
   
   ![分支行管理器 - 启用另一分支](attachments/collaborative-development/enable-another-branch.png) 

Web Moderr 的开发行已被选中。   

当您切换Web Modeler到另一条开发线时，Web Modeler在此过程中会被锁定几分钟。 一个弹出式对话框向用户显示桌面模式用户正在更改网页模式的行数。 Web Modeler所有的更改都是在当前的开发线上，并且只是在该线被更改之后。 



### 5.2 创建一个新的分支线

要创建一个新的分支，请执行以下操作： 

1. 点击 **项目** > **更多版本** > **管理分支行**. 

2.  在 **分支行管理器** 对话框窗口中，您看到了现有开发行的列表。 点击 **新的** 来创建一个分支线。 <br/>
   
   ![创建新分支](attachments/collaborative-development/creating-new-branch.png)<br/>

3.  在 **创建分支行** 对话框窗口，设置如下： <br/>
   
   a. 您正在创建一条新行：主行、分支行或标签版本。 关于这些概念的更多信息，见 [2 Concepts](version-control#concepts) in *Version Control*。 <br/> 
   
   b. 会议文件。 如果需要请选择修订版。 <br/>
   
   b. 会议文件。 输入新行的名称。 

4.  在您配置了所有设置后，点击 **确定** 
   
   ![创建分支行对话框](attachments/collaborative-development/create-branch-dialog.png) 

您已经创建了一个新的分支线。   



### 5.3 删除分支线

若要删除分支，请执行以下操作：

1. 点击 **项目** > **更多版本** > **管理分支行**. 

2.  在 **分支行管理器** 对话框窗口中，选择您想删除的分支，单击 **删除** 并确认删除。 
   
   ![删除分支](attachments/collaborative-development/deleting-branch.png)

您已删除此分支。

{{% alert type="info" %}}

您不能删除已启用的 Web Moderr 分支。 如果您需要删除此分支，请为另一行启用Web Moder，然后删除分支。 

{{% /报警 %}}



## 6 阅读更多

* [版本控制](version-control)
* [D. 排除合作发展问题](collaborative-development-troubleshooting)
* [Web Modeler 中的协作开发](/studio7/general-collaborative-development)
