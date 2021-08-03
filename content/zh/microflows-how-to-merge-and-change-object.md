---
title: "配置合并 & 更改对象活动"
category: "微型流动"
menu_order: 70
description: "如何在Mendix Studio中描述配置合并和更改对象活动的过程。"
tags:
  - "工作室"
  - "微流"
  - "合并"
  - "表达式"
  - "更改对象"
---

## 1 导言

如何在Mendix Studio中配置合并和更改对象活动，从而将高级逻辑添加到微流中。

合并用于将流量合并为一个流量。 如果您拆分微流流流量(做出决定)，现在需要执行相同的操作来处理这些分开的流量。 您可以使用合并合并两流(或更多流)。 欲了解更多关于决策的信息，请参阅 [Decision](microflows-decision)。

**这个教程将教你如何做以下事情：**

* 配置包含决策的微流程合并
* 配置合并后的更改对象活动

如何描述下面的用例：

在 [配置决策步骤 1：构建域模型 & 配置微流程 ](microflows-how-to-configure-decision-p1) 你已经配置了根据客户的等级打开特定页面的决定。 如果没有指明客户的评分, 则显示错误消息。 因此你在决定后有四个流量：

* 显示青铜级客户页面
* 显示银级客户页面
* 显示黄金等级客户页面
* 如果客户评分未填写，则显示错误消息

在这种方式下，您将合并铜、银的流量， 当客户打开个人订单表单时，和黄金客户等级设置对象(Customer)为活动状态。

## 2 个前提条件

要启动此教程，请确保您已完成以下前提条件：

* 用决定创建微流程： [配置决策步骤1：构建域模型 & 配置微流程](microflows-how-to-configure-decision-p1)

## 3 正在创建合并

为了在微流程中创建黄金、银和青铜客户等级的合并，遵循以下步骤：

1. 打开名为 *Show_grade_specific_page* 的微流程。

    ![](attachments/microflows-how-to-merge-and-change-object/microflow-without-merge.png)

2. 打开 **Toolbox** 标签 > 的 **常规** 部分 拖放 **合并** 在标明流量的结束事件中的活动 **青铜**

    ![](attachments/microflows-how-to-merge-and-change-object/adding-merge.png)

3. 若要合并标签为 **黄金** 的流量与 **青铜** 流量，请做以下操作：<br/>

    a. 删除标签为 **Gold** 的流程的 **结束** 事件。<br/>

    b. 会议文件。 悬停在 **上显示页面** 活动。<br/>

    ![](attachments/microflows-how-to-merge-and-change-object/hover-over.png)<br/>

    b. 会议文件。 单击会变成箭头的点之一。<br/>

    b. 平均输出功率超过1瓦； 拖动箭头以合并. 现在 **显示页面活动** 已连接到合并中。

    ![](attachments/microflows-how-to-merge-and-change-object/connecting-activity-and-merge.png)<br/>

4. 对标签为 **银的** 的流程重复第 3 步。

因此，你有三个流量合并为一个。

![](attachments/microflows-how-to-merge-and-change-object/flows-into-one.png)

## 4 配置更改对象

现在您将添加逻辑到微流程中。 您已经将三个流合并为一个，将客户状态设置为活跃的分级别。 例如，可以使用设定客户的活动状态 查明客户中的谁在使用他们的帐户，谁没有使用他们的帐户。

 执行以下操作：

1.  首先，， 您需要在域模型中为 **客户** 实体添加一个新属性，以表明客户是否活跃。 点击左侧菜单栏中的域模型图标打开域模型并执行以下操作：<br/>

    a. 点击 **客户** 实体 > **新属性**.<br/>

    b. 会议文件。 在 **创建新属性** 对话框窗口， 将 **名称** 设置为 *激活* 和 **类型** 设置为 *布尔值*.<br/>

    ![](attachments/microflows-how-to-merge-and-change-object/new-attribute-active.png)<br/>

    b. 会议文件。 点击 **创建**。

2. 现在您将在微流程中配置一个新的活动。 打开名为 *Show_grade_specific_page* 的微流程。
3.  在 **工具箱** > **对象活动** 选择 **更改对象** 活动 在微流合并后拖放它。

     ![](attachments/microflows-how-to-merge-and-change-object/change-object-added.png)

4.  在 **属性** 标签中， **更改对象** 的活动，做以下操作：<br/>

    a. 将 **变量** 设置为 **客户** 因为您将要编辑 **客户**。<br/>

    b. 会议文件。 点击 **添加新值**。<br/>

    ![](attachments/microflows-how-to-merge-and-change-object/change-object-add-new-value.png)<br/>

    b. 会议文件。 在 **更改值** 对话框窗口中，选择名为 **Active**的属性 然后点击 **表达式** 标签，输入 *true*。 这意味着在订单为特定客户打开后， 客户的状态被设置为活动状态 (活动=true) ，不管客户有什么等级。<br/>

    ![](attachments/microflows-how-to-merge-and-change-object/change-value-expression-editor.png)<br/>

    b. 平均输出功率超过1瓦； 点击 **添加** 来完成设置 **活动** 属性的值。<br/>

    e. 专门设计或制造的专门设计或制造的设备 在 **属性** 标签 > 中， **行为** 部分做以下操作：将 **提交** 选项设置为 **是**(这意味着对象将不会被进一步更改，您的更改将被保存到数据库)。  <br/>

    ![](attachments/microflows-how-to-merge-and-change-object/change-object-properties.png)

恭喜！ 现在您有以下方式工作的微流程：

1. 分析客户是否有一个等级，并且执行以下内容之一：<br/> a。 如果客户有一个等级，它会为对应的客户等级打开订单表单。<br/> b. 如果客户没有评级，错误消息就会向上传。<br/>
2. 如果客户有这个等级，一旦订单开启，客户的状态将被设置为活跃，不管它的成绩如何。

现在您可以预览或发布您的应用程序。 欲了解更多信息，请参阅 [预览 & 发布您的应用程序](publishing-app)
