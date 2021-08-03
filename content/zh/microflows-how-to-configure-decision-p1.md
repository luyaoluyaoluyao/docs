---
title: "第 1 步：构建域模型 & 配置微流"
parent: "microflow-how to config-decision"
description: "这个操作可以描述在 Mendix Studio 中配置决策的过程。"
menu_order: 10
tags:
  - "工作室"
  - "微流"
  - "决 定"
  - "域模型"
---

## 1 导言

如何在Mendix Studio的微流程编辑器中解释您如何配置决定。

决策是用于模拟应用逻辑条件的活动。 欲了解更多关于决定是什么以及如何配置它的信息，请参阅 [Decision](/studio/microflows-decision)。

**这个教程将教你如何做以下事情：**

* 添加配置决定所需的实体和属性
* 使用参数或属性的布尔类型配置决定
* 配置参数或属性的枚举类型

如何描述下面的用例：

您有一个在线购物应用。 您将创建一个您可以管理您客户的详细信息的页面，即名称、等级和客户的状态(活动或已屏蔽)。

您还将创建一个包含客户列表的页面。 点击此页上的一个特定按钮，将会向不同等级的客户显示不同的页面(订单表单)：Bronze、Silver和黄金。

客户可以在此页面下订单。 但是，如果被阻止的客户试图下订单，应用程序将向他们显示错误消息并关闭当前页面。

## 2 配置枚举类型属性的决定

在这个示例中，您将创建一个微流程并配置一个决定，根据客户等级打开不同的订单表。

此用例将需要具有枚举类型属性的决定 (预定义值列表)。 关于属性类型的更多信息，见 [属性](/studio/domain-models-attributes)。

### 2.1 为域模型添加实体和属性

该应用将根据客户的等级打开相应的页面， 为此您需要先创建一个新的实体和一个新的属性。 要创建新的实体和属性，请执行以下操作：

1. 打开您的 [域模型](/studio/domain-models)。

2. 创建实体 *客户*。 关于如何创建一个新实体的更多信息，请参阅 *域模型概述* 中的 [添加新实体](/studio/domain-models) 部分。

3.  为 **客户** 实体创建属性 (关于如何创建属性的更多信息, 查看 [添加新属性](/studio/domain-models) 部分，并执行以下操作：

    1. 将属性 **名称**设置为*等级*。
    2. 将[类型](/studio/domain-models-attributes)设置为**枚举**。
    3. 点击**选择枚举**。
    4. 在 **选择枚举** 对话框中，点击右上角的加号图标来创建枚举。
    5. 在 **中创建新枚举** 对话框， 点击 **添加项目** (*级*自动填充**名称**)。

        ![](attachments/microflows-how-to-configure-decision/new-enumeration-add-item.png)

    6. 输入 *青铜***标题** (**名称** 自动填充为 *青铜*)

        ![](attachments/microflows-how-to-configure-decision/new-enumeration-add-item-bronze.png)

    7. 点击 **添加项目** 并重复上面的步骤来创建**银级**和**黄金**级别。

    8. 点击**创建**来关闭对话框并创建属性。

        ![](attachments/microflows-how-to-configure-decision/new-enumeration-bronze-silver-gold.png)

属性已创建。

![](attachments/microflows-how-to-configure-decision/grade-attribute.png)

### 2.2 微流程配置

要使用枚举类型的属性或参数配置决策，请按照以下步骤：

1. [创建一个新的微流](/studio/microflows) 并命名它，例如， *显示级别指定页面*。

2. 在 **工具箱** 标签页中，选择 **Decision**, 拖放它到微流程。

3.  您需要传递一个参数才能正确配置决定。  在 **工具箱**, 选择 **参数** 并拖放它到微流程。

    ![](attachments/microflows-how-to-configure-decision/microflow-not-set-parameter.png)

4.  在此示例中，您正在添加的逻辑应该适用于在页面中选择的单个客户。 因此，您需要添加客户作为参数。 更改 **参数** 的以下属性：

    1. 将 **数据类型** 设置为 **对象**。
    2. 将 **实体** 设置为 **客户**。

        ![](attachments/microflows-how-to-configure-decision/parameter-properties.png)

5. 在决策的 **属性** 中，点击 **配置条件** 字段。

6. 在 **配置条件** 弹出窗口中，您需要选择一个条件将基于的属性。 因此，点击 **变量/属性** 标签，选择 **级客户等级** 条件，并点击 **保存**。

    ![](attachments/microflows-how-to-configure-decision/configure-condition-grade.png)

   标题 **评分？** 是根据属性名称自动添加到决定中，以表明该决定是基于哪个条件。

7. 您需要为 **级** 属性的每个值添加不同的逻辑。 要做到这一点，在 **属性** 选项卡中，设置用于决定的案例：

    1. 选择 **在 **(未设置)** 字段中编辑**。

        ![](attachments/microflows-how-to-configure-decision/setting-cases.png)

    2. 在 **选择值** 下拉菜单中设置 **青铜**。
    3. 点击 **返回** 图标返回决策属性。

        ![](attachments/microflows-how-to-configure-decision/go-back-button.png)

    4. 点击 **在 **案例** 部分中添加新案例**。
    5. 重复步骤b-d以添加所有可能的案例： **银**, **Gold**, 和 **空** (客户成绩未设定的案例)。

        ![](attachments/microflows-how-to-configure-decision/possible-cases.png)

8. To open a corresponding order form (page) for customers with the bronze grade, select **Show Page** in the **Toolbox**, drag and drop it to the flow labelled **Bronze** in the microflow.

9. 打开 **显示页面** 活动的属性，并执行以下操作：

    1. 点击 **选择一个页面** 字段。
    2. 在 **选择页面** 对话框中，点击右上角的加号图标， 和 [为客户等级创建页面](/studio/page-editor) **青铜**。 请注意，在您创建一个页面后，它将自动添加到 **选择字段**。

        ![](attachments/microflows-how-to-configure-decision/show-page-select-page.png)

    3. 在 **数据源** > **对象到通过**, 设置 **客户** 获取关于客户及其等级的数据。

10. 对银级和金级客户重复步骤8-9，分别为银级和金级客户创建订单页面。

11. 对于没有成绩的客户，您将显示一个错误消息。 要这样做，请选择 **在 **工具箱**中显示信件** 并将其添加到微流程中的标签为 **(空)** 的流程：

    ![](attachments/microflows-how-to-configure-decision/microflow-empty-flow-show-message.png)

12. In the **Properties** tab for the **Show message** activity, do the following:

    1. 选择 **错误** 作为消息类型。
    2. 填写 **模板** 当这个消息倒计时将会显示给最终用户(这个例子： *请选择客户成绩第一级*)。
    3. 将 **阻止** 个属性设置为启用的消息，它将阻止用户继续工作，直到弹出窗口关闭。

        ![](attachments/microflows-how-to-configure-decision/empty-customer-grade-message.png)

恭喜！ 您现在已经创建了微流程，为不同级别的客户打开不同的订单表单， 或在客户没有成绩时显示错误消息。

如果您想要通过添加到页面来测试您的微流程， 查看 [配置决策步骤 2：将微流程嵌入您的应用程序](microflows-how-to-configure-decision-p2)。

## 以布尔类型的属性配置决定

在这个示例中，您将创建一个微流程并配置一个决定来阻止被屏蔽的客户下订单。 阻止客户的原因可能是客户的信用等级太低或密码已过期。

此用例将需要一个带有布尔类型属性的决定(true或false)。 关于属性类型的更多信息，见 [属性](/studio/domain-models-attributes)。

### 3.1 为域模型添加实体和属性

由于您将根据客户的状态验证客户，您需要先为该实体创建一个相应的属性。 为此，采取以下行动：

1. 打开您的 [域模型](/studio/domain-models)。

2.  对于客户实体，创建属性 (关于如何创建属性的更多信息) 查看 [添加新属性](/studio/domain-models) 部分，并执行以下操作：

    1. 将名称设置为 *被屏蔽了*。
    2. 将 [类型](/studio/domain-models-attributes) 设置为 **布尔值**。
    3. 点击 **创建**。

        ![](attachments/microflows-how-to-configure-decision/new-attribute-create-dialog.png)

**客户** 实体的属性已创建。

![](attachments/microflows-how-to-configure-decision/blocked-attribute.png)

### 3.2 配置微流

要使用布尔类型的属性配置决策，请按照以下步骤：

1. [创建一个新的微流](/studio/microflows) 并命名它，例如 *Customer_status_check*。

2. 在 **工具箱** 标签页中，选择决策，拖动并拖放到微流程。

3.  您需要通过一个参数来配置决定。 在 **工具箱** 标签中，选择 **参数**，然后拖放它到微流。

    ![](attachments/microflows-how-to-configure-decision/microflow-not-set-parameter.png)

4.  在此示例中，您添加的逻辑应该适用于客户的状态。 因此，您需要添加客户作为参数。 在 **属性 **参数**的** 标签中，执行以下操作：

    1. 将 **数据类型** 设置为 **对象**。
    2. 将 **实体** 设置为 **客户**。

        ![](attachments/microflows-how-to-configure-decision/parameter-properties.png)

5. 单击该决定，并且在 **属性** 标签中，点击 **配置条件** 字段。

6. 在 **配置条件** 弹出窗口中，您需要选择条件将基于的属性。 因此，在 **配置条件** 弹出窗口中，点击 **变量/属性** 选项卡， 选择 **被屏蔽的布尔值** 属性的 **客户**，点击 **保存**

    ![](attachments/microflows-how-to-configure-decision/configure-condition-pop-up.png)

7. **true** and **false** 的案例会自动为该决定的属性设置，并且相应的流量会被添加到微流中。 标题 **已阻止？** 是根据属性名称自动添加的。

    ![](attachments/microflows-how-to-configure-decision/true-false-flows-microflow.png)

8. 若要向被阻止的客户显示错误消息，请选择 **在 **工具箱**中显示消息** 并将其添加到 **true** microflow。

9. In the **Properties** tab for the **Show message** activity, do the following:

    1. 选择 **错误** 作为消息类型。
    2. 填写 **模板** 当这个消息倒计时将会显示给最终用户(这个例子： *对不起) 您不能继续订单*。
    3. 为启用消息留下 **阻止** 个属性，从而阻止用户继续工作，直到弹出窗口关闭。

        ![](attachments/microflows-how-to-configure-decision/show-message-properties-true-flow.png)

10. 在 **工具箱** 标签页中，选择 **关闭页面** 活动，拖动并拖放它到微流程。

    ![](attachments/microflows-how-to-configure-decision/microflow-blocked-completed.png)

恭喜！ 您现在已经创建了微流，它将显示错误消息，并且在客户被阻止时关闭当前页面。

如果您想要嵌入您的微流到页面, 请参阅 [步骤 2: 将微流嵌入您的应用程序](microflows-how-to-configure-decision-p2)。
