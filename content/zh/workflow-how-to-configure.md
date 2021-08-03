---
title: "配置工作室中员工上岗流程的工作流"
description: "描述如何在 Mendix Studio 中配置一个工作流。"
menu_order: 5
tags:
  - "工作室"
  - "工作流"
  - "如何处理"
  - 任务", "登机"
---

## 1 导言

Workflow 是 Mendix Studio 和 Mendix Studio Pro 中的一种新的视觉语言，它允许您构建可扩展的流程。 它与其他视觉语言如微流编辑器和页面编辑器完全集成。

如何使用工作流编辑器来构建员工上岗流程。 关于如何在Studio Pro中建立类似进程的更多信息 查看 [如何配置Studio Pro 中的员工待寄流程工作流程](/howto/logic-business-rules/workflow-how-to-configure)。

**这个教程将教你如何做以下事情：**

* 启用并创建工作流
* 配置工作流实体
* 从页面触发工作流
* 为不同的用户角色创建用户任务
* 为用户任务配置页面
* 限制页面访问相关用户角色
* 创建一个决定
* Configuring navigation
* 从不同用户的角度测试您的工作流

如何描述下面的用例：

你想要建立一个员工在职过程。 起初，一名人力资源专家需要为一名新雇员启动上岗程序。 然后该雇员的经理就会走进去。 选择供雇员使用的设备，并指定新雇员是在办公室还是在家工作。 设施部门将需要准备一个工作空间。 视新的雇用地点(办公室或家里)的情况而定， 设施部门要么准备一个台，要么将设备运到雇员的住处。

## 2 个前提条件

在启动此操作之前，请确保您已完成以下前提条件：

* 熟悉工作流程条款。 欲了解更多信息，请参阅 [Workflow](/refguide/workflows)。
* 请确保您的应用有 Mendix 版本 9
* 请确保您的应用基于空白应用模板

## 3 有利于工作流 {#enable-workflows}

首先，您需要为您的应用启用 Workflow。 执行以下操作：

1. 点击左侧菜单栏中的工作流图标。

2. 在启用工作流之前，您需要先启用安全性。 点击 **启用安全**：

    {{% image_container width="250" %}}![启用安全](attachments/workflow-how-to-configure/enable-security.png)
    {{% /image_container %}}

3. 启用安全性后，点击 **启用 Workflow**。

4. 在 **工作流启用** 弹出菜单中，点击 **创建工作流**：

    {{% image_container width="300" %}}![创建工作流](attachments/workflow-how-to-configure/create-workflow.png)
    {{% /image_container %}}

5. 在 **创建新的 Workflow** 对话框中，将 **标题** 设置为 **Employeee_Onboard**然后点击 **工作流实体** 字段创建一个新的工作流实体。

6. 在 **选择工作流程实体** 对话框中，点击 **创建工作流程实体**。

7. 在 **创建新的工作流实体** 对话框中，将 **名称** 设置为 **员工在** 并点击 **创建**

8. 点击 **创建** 再次确认您的选择。

干得好！ 您已创建了一个工作流程和针对工作流程的实体。 欲了解更多关于工作流实体的信息，请在 *域模型* 中查看 [实体及其类型](/studio/domain-models#entity-types) 部分。

## 4 配置域模型

1. 打开 [域模型](/studio/domain-models)。
2.  您已创建的 **员工登临** 实体将保持关于员工登机的信息。 以及捕获在执行工作流程过程中添加的信息，例如新雇员所需的膝上型计算机模型。 Add the following attributes to the **EmployeeOnboarding** entity (for more information on how to create attributes, see [Adding New Attributes](/studio/domain-models#adding-new-attributes) section in the *Domain Model*):
    1. 添加 **全名** 属性并将类型设置为字符串。
    2. 添加 **第一天** 属性，并将其类型设置为日期和时间。
    3. 添加 **FWH** (在家工作) 属性，并将其类型设置为 Boolean。
    4. 添加 **PhoneModel** 枚举与下列枚举项: iPhone、iPhone_Pro、三星。 欲了解更多关于枚举和如何创建这些枚举的信息，请在 *枚举* 中查看 [创建一个新枚举](/studio/domain-models-enumeration#create-new-enumeration) 部分。
    5. 用以下枚举项添加 **笔记模型** 个枚举：Lenovo, Mac, Dell。 欲了解更多关于枚举和如何创建这些枚举的信息，请在 *枚举* 中查看 [创建一个新枚举](/studio/domain-models-enumeration#create-new-enumeration) 部分。

您已经配置 **员工toon** 实体： ![域模型](attachments/workflow-how-to-configure/domain-model.png)

## 5 配置安全

在 [启用工作流](#enable-workflows) 部分中，您已经为您的应用启用了安全性，并且自动添加了几个角色和权限。 然而，您需要为您的应用添加更多的角色：HR、经理和设施角色。 遵循下面的步骤：

1. 打开 **应用设置** > **角色和权限**。
2. 点击 **在右角添加角色**。
3. 将角色的名称设置为 **HR** 并点击 **创建**.
4. 重复步骤2和3以创建 **管理器** 和 **设施** 角色。

现在为您的应用创建了所有必要的角色。 欲了解更多安全信息，请参阅 [安全性，角色 & 权限](/studio/settings-security)

## 6 从页面触发工作流

要启动您的工作流，您需要触发它。 在这种情况下，工作流程是由一名人力资源专家启动的，该专家应填写新租用的姓名： 第一天，然后单击 **启动上岗** 按钮，触发工作流。 执行以下操作：

1. 创建一个 **EmployeesToOnboard** 页面，其中包含一个 **EmployeeOnboard** 实体作为其数据源。 (更多关于如何创建一个页面并添加小部件的信息。) 查看 [履行基本函数](/studio/page-editor#page-editor-basic-functions) 部分在 *页面* 中 .)

    {{% image_container width="500" %}}![在线员工列表](attachments/workflow-how-to-configure/employees-to-onboard-list.png)
     {{% /image_container %}}

2. 在列表视图中添加启动工作流的按钮。 遵循下面的步骤：

    1. 打开 **工具箱** 并搜索 **调用工作流程** 按钮。

    2. 拖放列表视图中的按钮：

        ![启动登机按钮](attachments/workflow-how-to-configure/start-onboarding-button.png)

    3. 打开按钮属性并将 **Workflow** 属性设置为 **Employeee_Onboard**。

    4. 将按钮的 **标题** 设置为 **启动上船**。

3. 人力资源专家还需要一个网页，他们可以填写新的租户细节。 在页面顶部添加 **创建对象** 按钮(在列表视图之外)：

    {{% image_container width="500" %}}![员工到在线页面](attachments/workflow-how-to-configure/employees-to-onboard-page.png)
    {{% /image_container %}}

4. 将 **实体** 设置为 **员工Ontool**：

    ![](attachments/workflow-how-to-configure/create-object-button.png)

5. 点击 **页面** 属性。

6. 在 **选择页面** 对话框中，点击加号图标。

7. 在 **创建新页面** 对话框中，您可以看到窗体的模板。 执行以下操作：

    1. 将 **标题** 设置为 **员工详细信息**。

    2. 将 **布局** 设置为 **弹出布局**。

    3. 选择 **表单列** 模板。

    4. 点击 **创建**。

        ![创建员工详细信息页面](attachments/workflow-how-to-configure/create-employee-details-page.png)

8. 新页面正在打开 默认情况下，所有属性都添加到表单中。 然而，人力资源专家只需具体说明新聘人员的姓名和第一天。 保留相关的小部件并从表单中删除所有其他小部件：

    ![员工详细信息表单](attachments/workflow-how-to-configure/employee-details-form.png)

干得好！ 现在你有一个可以启动工作流程的 HR 专家页面。

## 7 指明新租的详细信息 {#specify-details}

一名新员工的经理将获得一项任务，指定新员工的设备。 管理人员还需要说明新聘用者是否在家工作。 为了此功能，您需要将活动添加到工作流。 遵循下面的步骤：

1. 打开 **Employeee_Ontool** workflow。

2. 在 **工具箱** 标签页中，找到 **用户任务** 活动，并拖放到工作流编辑器。

3. 打开用户任务属性。

4. 将 **标题** 属性设置为 **经理：指定员工详细信息** 以方便地查看该任务应分配给谁：

    ![标题](attachments/workflow-how-to-configure/user-task-caption.png)

5. 要创建管理员指定必要详细信息的页面, 请点击 **页面** 属性。

6. 在 **选择页面** 对话框中，点击加号图标。

7. 在 **创建新页面** 对话框中，您可以看到工作流页面的模板。 执行以下操作：

    1. 将 **标题** 设置为 **详细说明**.

    2. 检查 **布局** 已设置为 **Atlas_默认**。

    3. 选择 **用户任务扩展** 模板。

    4. 点击 **创建**。

        ![创建新页面](attachments/workflow-how-to-configure/create-new-page.png)

8. 现在您需要确保只在 **SpecifyDetail** 页面上显示相关信息。 默认情况下，所有属性都被添加到数据视图中与员工详细信息一起进行编辑。 您只需要保留与任务相关的属性。 您还需要确保管理员只能更改表单中的特定字段。 例如，该雇员的姓名已被人力资源部门输入， 所以管理员不需要更改它，应该将此字段作为只读字段。

    执行以下操作：

    1. 选择标签为 **的文本框，全名** 并转到其属性。

    2. 将 **编辑性** 属性设置为 *只读*。

    3. 删除 **第一天** 日期选择器，因为它与这个任务无关。

    4. 离开 **WFH**, **Phone 模型**, 和 **Laptop 模型** 字段：

        ![指定详细信息表单](attachments/workflow-how-to-configure/specify-details-form.png)

9. 只有管理员角色可以访问 **特殊设备** 页面。 导航到页面属性 > **允许角色** 并取消除 **管理器** 之外的所有角色。

10. 返回工作流并打开用户任务属性来完成用户任务配置。

11. 因为只有经理才应具体说明新雇员的详细情况， 您需要确保用户任务只分配给具有管理员角色的用户。 执行以下操作：

    1. 请确认 **分配任务使用** 属性已设置为 **过滤器**。

    2. 点击 **滤镜** 属性。

    3. 在 **分配任务到** 对话框中， **** 条件设置为 **用户角色** 默认情况。 将条件的其他部分设置为 **管理器** 并单击 **添加**：

        ![分配任务给管理器](attachments/workflow-how-to-configure/assign-task-to-manager.png)

12. 在 **允许的角色** 属性中，除 **Manager** 外，取消所有角色的选择，以限制对此用户任务的访问仅限于相关角色。

干得好！ 您已经为管理器角色创建了用户任务：

![配置用户任务](attachments/workflow-how-to-configure/user-task-configured.png)

## 8 跟随Here位置的不同路径

取决于新雇员是在办公室还是在家工作。 在这次租用上有两个不同的过程：准备办公室的一个服务台或将膝上型计算机和电话发送到家用地址。 上岗过程的这一步骤应由设施部门执行。

执行以下操作：

1. 打开 Workflow editor > **Toolbox** 然后拖放 **Decision** activity after **Manager: 指定位置** 用户任务。

    ![添加决定](attachments/workflow-how-to-configure/decision.png)

2. 决定意味着工作流程路径可以根据决定的条件分割并遵循其中的一个结果。 欲了解更多信息，请参阅 *一般活动* 中的 [Decision](/studio/workflows-general-activities#decision) 部分。 打开决策属性并执行以下操作：

    1. 将 **标题** 设置为 **WH?**.

    2. 点击 **条件** 属性。

    3. 在 **配置条件** 对话框中， 在表达式中键入将根据 **WFH** 属性将一个流程分割成两个： `$workflowData/ WFH`

        {{% image_container width="500" %}}![Decision Properties](attachments/workflow-how-to-configure/decision-properties.png){{% /image_container %}}

    4. 点击 **保存**。

3. 因为WFH 属性是布尔值， 它是真实的(当新的雇用人员从家里工作时)和假的(当他们从办公室工作时)结果。 这些结果自动添加到工作流中：

    ![决策结果](attachments/workflow-how-to-configure/decision-outcomes.png)

4. 现在您需要配置两种场景中发生的情况：新的雇用在家里工作（true）和新的雇用在办公室工作（Alse）。 打开 **Toolbox**, 拖放 **用户任务** 活动到 **false** 路径, 并执行以下操作：

    1. 将其标题设置为 **设施：准备桌面**。

    2. 由于只有设施部门应为新雇员准备一个桌子， 您需要确保用户任务只分配给具有设施角色的用户。 参考新Hire</a> 部分的
指定详细信息的步骤11a-11c，以便将用户任务分配给设施角色。</p></li> 
       
           3 在 **中允许的角色** 属性取消了除 **设施以外的所有角色** 

    4 为 **页面** 创建一个新页面名为 **准备桌面** 的属性，指的是 [指定新节的步骤7a-7d](#specify-details)

    5 您需要确保只在 **准备桌面** 页面上显示相关信息。 默认情况下，所有属性都添加到员工详细表单中。 您需要确保设施部门能够查看字段，但不会更改。 执行以下操作： 

    6 选择雇员详细信息的数据视图并转到其属性。

    7 切换 **只读** 属性，以使所有字段都只读。
      
      ![只读数据视图](attachments/workflow-how-to-configure/data-view-read-only.png)

    8 只有设施角色才能访问 **准备桌面** 页面。 导航到页面属性 > **允许角色** 并取消除 **设施** 之外的所有角色。</ol></li> 

8 现在，当雇员在家里工作时，您需要为设施创建一个用户任务。 打开工作流编辑器。

6 打开 **Toolbox**, 拖放 **用户任务** 活动到 **true** 路径, 并执行以下操作：
  
      1. 将其标题设置为 **个设施：船舶设备**。

    2. 由于只有设施部门应为新雇员准备一个桌子， 您需要确保用户任务只分配给具有设施角色的用户。 请参阅新Hire</a> 部分的 指定细节步骤11a-11c。</p></li> 
       
           3 在 **中允许的角色** 属性取消了除 **设施以外的所有角色** 

    4 为 **页面** 创建一个新页面 **发货设备** 创建一个新页面 </strong> 属性, 指的是步骤7a-7d [指定新Hire 章节的详细信息](#specify-details)

    5  在新创建的 **发货设备** 页面上，默认情况下所有属性都添加到员工详细表单中。 您需要确保设施部门能够查看字段但不能更改它们：选择雇员详细信息的数据视图并前往其属性。

    6 切换 **只读** 属性，使所有字段都只读：
      
      ![只读数据视图](attachments/workflow-how-to-configure/data-view-read-only.png)

    7 只有设施角色才能访问 **发货设备** 页面。 导航到页面属性 > **允许角色** 并取消除 **设施** 之外的所有角色。</ol></li> </ol> 

干得好！ 您已经创建了关于新聘用者是从办公室还是从家里工作的决定和用户任务。 您的 Workflow 已配置！ 

{{% image_container width="250" %}}

![配置的工作流](attachments/workflow-how-to-configure/worfklow-configured.png) 

{{% /image_container %}}



## 10 Configuring Navigation

您需要配置导航，否则用户角色将无法到达任何页面并与他们的任务交互。 遵循下面的步骤：

1. 打开 [导航文档](/studio/navigation), 其中一些菜单项已经为您预先配置。

2. 人力资源角色需要能够访问 **EmployeesToOnboard** 页面。 添加一个新的菜单项并执行如下操作(关于如何添加一个新菜单项的更多信息) 查看 [导航文档](/studio/navigation)：
   
       1. 将 **单击动作** 设置为 **页面**。

    2. 点击 **页面** 属性。

    3. 在 **选择页面** 对话框框中，选择 EmployeesToOnboard 页面。

    4. 在菜单项属性中，将标题设置为 **HR：员工在板上**。

    5. 将 **图标** 设置为 **用户**。
       
       ![HRs导航项](attachments/workflow-how-to-configure/navigation-hr.png)

3. 管理员需要添加菜单项才能打开他们的任务收件箱。 添加一个新的菜单项并执行如下操作(关于如何添加一个新菜单项的更多信息) 查看 [导航文档](/studio/navigation):
   
       1. 将 **单击动作** 设置为 **页面**。

    2. 点击 **页面** 属性。

    3. 在 **选择页面** 对话框中 从当前模块切换到工作流共享，使用右上角的下拉菜单：
       
       {{% image_container width="400" %}}![Select Page](attachments/workflow-how-to-configure/select-page-for-navigation.png){{% /image_container %}}

    4. 在列表中找到 **任务收件箱** 页面并点击 **选择**。

    5. 在菜单项属性中，将 **标题** 设置为 **经理：任务收件箱**。

    6. 将 **图标** 设置为 **信封**。

4. 您还需要为设施部门添加菜单项才能打开他们的任务收件箱。 创建一个新的 **设施：任务收件箱** 菜单项提及上面的步骤2a-2e。

您已为您的应用配置导航，现在您可以预览和测试 

![已配置导航](attachments/workflow-how-to-configure/configured-navigation.png)



## 11 测试 Workflow {#test-workflow}

现在您可以从不同用户的角度测试您的工作流。 

例如，拥有分配给他们的任务的用户 (管理员) 设施作用将看到他们的任务收件箱和仪表板页面，以便能够管理和监测分配给他们的任务：

![任务收件箱](attachments/workflow-how-to-configure/task-inbox.png)

工作流管理员角色可以访问工作流管理中心，并且可以监控所有工作流量。 可以查看工作流的进度，更改工作流设置。

管理员角色能够管理用户。

要测试您的工作流，您需要在不同的用户角色之间切换。 遵循下面的步骤：

1. 点击 **预览** 按钮。 (关于如何预览您的应用的更多信息，见 [预览 & 发布您的应用](/studio/publishing-app))

2. 点击右边的用户图标并选择一个用户角色：
   
   {{% image_container width="300" %}}![Demo User Role](attachments/workflow-how-to-configure/user-roles.png){{% /image_container %}}

3. 您可以在不同的演示用户角色间切换来测试使用情况。 可以这样做：
   
       1. 选择 HR 用户角色，打开 **EmployeesToOnboard** 页面并添加一个新的在线请求。
    2. 切换到管理员角色，在收件箱中看到一个新的任务，打开任务，添加数据并完成任务。
    3. 切换到设施用户角色并完成进程。
4. 打开 Workflow 管理中心。

5. 打开工作流程仪表。

干得好！ 您已经在本地预览了您的应用，并且从不同用户的角度测试了您的工作流。 您现在可以为您的应用添加更多功能，或与其他用户分享您的应用，以便在实际生活中尝试它。 



## 12 阅读更多

* [工作流](/studio/workflows)
* [如何配置导航栏](navigation-how-to-configure)
* [如何将字段设置为只读字段或必填字段](pages-how-to-set-validation-and-editability)