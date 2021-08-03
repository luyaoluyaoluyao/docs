---
title: "配置域模型"
description: "这个如何描述在 Mendix Studio 中配置域模型的过程。"
menu_order: 30
tags:
  - "工作室"
  - "域模型"
  - "决 定"
  - "域模型"
---

## 1 导言

如何在Mendix Studio中解释您如何配置域模型。

**这个教程将教你如何做以下事情：**

* 定义要包含到您的域模型的数据
* 创建不同类型的实体
* 创建属性
* 创建关联

如何描述下面的用例：

您正在为在线购物应用配置域模型。

## 2 个前提条件

在启动此操作之前，请确保您已完成以下前提条件：

* 熟悉域模型条款并学习如何执行基本功能。 欲了解更多信息，请参阅 [域模型](/studio/domain-models)。

## 3 定义要包含的数据

理解典型的进程将有助于您定义哪些数据包含到您的域模型。 在线购物应用程序的新客户的工作流程看起来如下：

1. 客户注册在线购物应用程序并输入以下详细信息：
   1. 全名
   2. 地址
   3. 电子邮件地址
   4. 出生日期
2. 注册完成后， *唯一ID* 被分配给客户。
3. 客户浏览 *产品* 并显示以下产品详细信息：
   1. 产品图片
   2. 名称
   3. 描述
   4. 可用性
   5. 价格
   6. 供应商
   7.  唯一的产品 ID
4. 客户将产品添加到购物车。
5. 在购物车中，每个项目作为单独的行呈现，显示 *数量* 和 *每行价格*。 客户检查订单，支付它。 并通过 *订单详情* 和 *日期* 获得 *确认* 确认, 订单已购买。

基于上面的描述，您可以将您的数据分成以下元素：

* [客户](#customer)
* [产品](#product)
* [订单](#order)

## 4 定义产品 {#product}

作为一种产品，它是在线购物应用的主要元素之一， 应该创建一个实体来代表你的域模型中的商品。 定义产品的信息，如产品名称和价格，应该是 **产品** 实体的属性。

要将产品添加到您的域模型，请按照下面的步骤：

1. 创建 **产品** 实体。 执行以下操作：

    1. 打开您的 [域模型](/studio/domain-models)。

    2. 打开 **工具箱**, 拖放 **实体** 在您的域模型中：

       {{% image_container width="350" %}}![Adding a New Entity](attachments/domain-model-how-to-configure/adding-entity.png){{% /image_container %}}

    3. 在 **创建新实体**中，对话框，将名称设置为 **产品** 并点击 **创建**。

2. 为 **产品** 实体创建属性。 执行以下操作：<br />
    1. 选择实体并点击 **新属性**：

        {{% image_container width="250" %}}![Adding New Attribute](attachments/domain-model-how-to-configure/adding-new-attribute.png){{% /image_container %}}

    2. 在 **创建新属性** 对话框中，将名称设置为 *Product_ID*将类型设置为 *自动调用* (以便产品的 ID 自动分配)， 然后点击 **创建**:

        {{% image_container width="450" %}}![Create New Attribute Dialog Window](attachments/domain-model-how-to-configure/create-new-attribute-dialog.png){{% /image_container %}}

    3. 重复步骤 2a 以添加 *名称* 属性。

    4. 在 **创建新属性** 对话框中，将名称设置为 *名称*将类型设置为 *字符串*, 然后点击 **创建**。

   5. 重复步骤 2a 添加 *描述* 属性。

   6. 在 **创建新属性** 对话框中，将名称设置为 *描述*将类型设置为 *字符串*, 然后点击 **创建**。

   7. 重复步骤2a以创建属性以表明产品是否可用。

   8. 在 **创建新属性** 对话框中，将名称设置为 *可用*将类型设置为 *布尔值*, 然后点击 **创建**。

   9. 重复步骤 2a 以创建 *价格* 属性。

   10. 在 **创建新属性** 对话框中，将名称设置为 *价格*将类型设置为 *小数点*并点击 **创建**。

   11. 重复步骤 2a 以创建 *供货商* 属性。

   12. 在 **创建新属性** 对话框中，将名称设置为 *卖家*, 将类型设置为 *字符串*, 然后点击 **创建**。

3. 每个产品都有一个 *镜像*，但是你没有创建它作为属性。 您需要创建一个允许您存储图像的特殊类型的实体——一个图像实体， 并将其名称设置为 *Product_Image*。 遵循下面的步骤：

    1.  打开 **工具箱**, 拖放 **图像实体** 在您的域模型中：

        {{% image_container width="300" %}}![Image Entity](attachments/domain-model-how-to-configure/adding-image-entity.png){{% /image_container %}}

    2. 在 **创建新图像属性** 对话框中，将名称设置为 *Product_Image* 然后点击 **创建**。
 {{% alert type="info" %}} *Name* and *Size* attributes are created automatically and are read-only.
        {{% /报警 %}}

干得好！ 您创建了 **产品** 实体、其属性和 **Product_Image** 图像实体：

{{% image_container width="500" %}}![Product and Product Image Entities](attachments/domain-model-how-to-configure/product-and-product-image.png){{% /image_container %}}

## 5 定义顺序 {#order}

订单信息可分为以下几类：

* **订单** - 有关订单的一般信息，例如它的状态、订单号、客户名称和地址等。
* **订单行** - 订购物品，物品数量和价格
* **订单确认** — 确认发送给客户的订单已经放置了

因此，您需要创建三个实体： *订单*, *Order_Line*, 和 *Order_确认*。

执行以下操作：

1. 创建 **订单** 实体。 使用与创建 **产品** 实体相同的方法。 欲了解更多信息，请参阅 [定义产品](#product) 部分。

2. 为 **订单** 实体创建属性： *订单号* 和 *状态* 执行以下操作：<br />
    1. 选择实体并点击 **新属性**。

    2. 在 **创建新属性** 对话框中，将名称设置为 *订单号*将类型设置为 *Autonumber*, 然后点击 **创建**。

    3. 重复步骤 2a 以创建 *状态* 属性。

    4. 将属性 **名称** 设置为 *状态* 和 **类型** 设置为 *枚举*。 枚举将包含不同的状态值，例如： *已放置* 或 *已发货*。

    5. 点击 **选择枚举** 创建一个新的 [枚举](/studio/domain-models-enumeration)

        {{% image_container width="450" %}}![Select Enumeration](attachments/domain-model-how-to-configure/select-enumeration.png){{% /image_container %}}

    6. 在 **选择枚举** 对话框中，点击右上角的加号图标添加新枚举。

    7. 在 **中创建新枚举** 对话框， 点击 **添加项目** (*状态* 被自动填写为 **名称**)。

        {{% image_container width="450" %}}![Create New Enumeration](attachments/domain-model-how-to-configure/create-new-enumeration.png){{% /image_container %}}

    8. 输入 *订购* **标题** (**名称** 被自动填写为 *订购*)

    9. 点击 **添加** 并重复上面的步骤来创建 **已支付**, **已发货**, **已交付**, 和 **已取消** 状态

        {{% image_container width="450" %}}![Create Enumeration Items](attachments/domain-model-how-to-configure/create-enumeration-items.png){{% /image_container %}}

    10. 点击 **创建** 来关闭对话框并创建属性。

3. 创建 **订单行** 实体来保存订单产品和数量。 使用与创建 **产品** 实体相同的方法。 欲了解更多信息，请参阅 [定义产品](#product) 部分。

4. 为 **order_line** 实体创建属性。 执行以下操作：<br />

    1. 重复步骤 2a 以创建 *数量* 属性。
    2. 在 **创建新属性** 对话框，设置 **名称** 为 *数量*设置 **类型** 到 *整数*, 然后点击 **创建**。
    3. 重复步骤 2a 以创建 *订单价格* 属性。
    4. 在 **创建新属性** 对话框，设置 **名称** 为 *订单价格*设置 **类型** 到 *小数*, 然后点击 **创建**。

5. 创建 **订单确认** 实体。 由于订单确认是向客户发送的文件， 您需要创建一个特殊类型的实体，允许您存储文件 - **文件** 实体。 执行以下操作：

    1. 打开 **工具箱**, 拖放 **文件实体** 在您的域模型中：

        {{% image_container width="350" %}}![Image Entity](attachments/domain-model-how-to-configure/adding-file-entity.png){{% /image_container %}}

    2. 在 **创建新文件属性** 对话框中，将名称设置为 *订单确认* 并点击 **创建**。

6. 为 **订单确认** 实体创建属性。 执行以下操作：<br />

    1. 重复步骤 2a 以创建 *日期发送* 属性。

    2. 在 **创建新属性** 对话框，设置 **名称** 为 *日期发送*将 **类型** 设置为 *日期和时间*并点击 **创建**。

        {{% alert type="info" %}} *Name* and *Size* attributes are created automatically and are read-only.
        {{% /报警 %}}

您配置了三个实体，在您的在线购物应用程序中定义顺序。

## 6 定义客户 {#customer}

客户是需要一个单独实体的在线购物应用程序的另一个关键部分。 定义客户的详细信息，例如名称和地址，应该是此实体的属性。

遵循下面的步骤：

1. 创建 **客户** 实体。 使用与创建 **产品** 实体相同的方法。 欲了解更多信息，请参阅 [定义产品](#product) 部分。
2. 为 **客户** 实体创建属性 (关于如何创建属性的更多信息, 见 [添加新属性](/studio/domain-models#adding-new-attributes) 部分在 *域模型*。 执行以下操作：<br />
1. 选择实体并点击 **新属性**。
    2. 在 **创建新属性** 对话框，设置 **名称** 为 *Customer_ID*将 **类型** 设置为 *Autonumber*, 然后点击 **创建**。
3. 重复步骤 2a 以创建 *名称* 属性。
    4. 在 **创建新属性** 对话框，设置 **名称** 为 *名称*将 **类型** 设置为 *字符串*, 然后点击 **创建**。
5. 重复步骤 2a 以创建 *地址* 属性。
    6. 在 **创建新属性** 对话框，设置 **名称** 为 *地址*将 **类型** 设置为 *字符串*, 然后点击 **创建**。
7. 重复步骤 2a 以创建 *电子邮件* 属性。
    8. 在 **创建新属性** 对话框，设置 **名称** 为 *电子邮件*将 **类型** 设置为 *字符串*, 然后点击 **创建**。
9. 重复步骤 2a 以创建 *日期_Of_Birth* 属性。
    10. In the **Create New Attribute** dialog box, set **Name** to *Date_Of_Birth*, set **Type** to *Date and Time*, and click **Create**.


您创建了 **客户** 实体及其属性：

{{% image_container width="200" %}}
![客户实体](attachments/domain-model-how-to-configure/customer_entity.png)
{{% /image_container %}}

## 7 个正在创建关联

您已创建所有实体及其属性：

<img src="attachments/domain-model-how-to-configure/entities.png" alt="实体" />

现在您需要定义这些实体如何相互连接并创建关联。 欲了解更多关联信息，请参阅 [关联](/studio/domain-models-association-properties)。

首先，定义实体之间如何相互连接：

1. 一个产品图片只连接到一个产品：这意味着它们有一对一的关联。
2. 一个订单可以包含多个项目 (订单行)，这意味着 **订单** and **订单行** 具有一对多的关联。
3. **订单行** 使用了关于产品的信息。 一个产品可以与几个订单行关联，所以 **产品** and **Order_Line** 需要一个一对一的关联。
4. 每个订单发出一次订单确认。 这意味着一个 **订单** 对象与一个 **订单确认** 对象相关，并且有一对一的关联。
5.  订单由客户下达。 多个订单可以连接到一个客户，所以 **订单** and **客户** 有一对一的关联。

现在您已经定义了实体之间的连接，您可以开始创建这些连接。 遵循下面的步骤：

1. 从 **Product_Image** 到 **Product** 创建一个关联。 执行以下操作：

    1. 悬停在 **Product_Image** entity 上，然后点击点图标：

       {{% image_container width="500" %}}![Product Image and Product Association](attachments/domain-model-how-to-configure/product-image-product-association.png){{% /image_container %}}

    2. 拖动点到 **产品** 实体。

        ●{% alert type="info" %}}另一种在实体之间创建关联的方式是选择一个实体并点击箭头图标。
        {{% /报警 %}}

    3. 打开 **属性** 并将多重性 (默认情况下创建一对一) 更改为一对一。

        {{% image_container width="300" %}}![Product_Image and Product Association](attachments/domain-model-how-to-configure/product-image-and-product-association.png){{% /image_container %}}

2. Create an association from **Order_Line** to **Order** following the steps 1a and 1b above. (默认情况下创建了一对一的多重性)。
3. 按照以上步骤1a和1b创建关联从 **订单** 到 **客户**。 (默认情况下创建了一对一的多重性)。

4. 从 **订单** 到 **订单行** 创建一个关联。 执行以下操作：
    1. 按照上面步骤1a和1b。
    2. 打开 **属性** 并将多重性 (默认情况下创建一对一) 更改为一对一。

所有关联都已创建。

{{% alert type="info" %}}

或者，， 您可以创建一个图片或文件实体，点击 **新属性** > **添加文件或图片**在这种情况下，默认情况下创建一个关联。 For more information, see the [Adding New Image or File Entities](/studio/domain-models#adding-image-or-file-entities) section in *Domain Model*.

{{% /报警 %}}

恭喜！ 您现在配置了在线购物应用的域模型！

![域名模型在线购物应用](attachments/domain-model-how-to-configure/domain-model-online-shop.png)

现在您可以为它构建 [页面](/studio/page-editor) 或使用 [Buzz](/studio/collaboration-buzz) 与您团队的开发者和设计者合作，并建立应用程序体验。

## 8 阅读更多

* [域模型](/studio/domain-models)
* [页 次](/studio/page-editor)
* [微型流动](/studio/microflows)
* [布兹斯](/studio/collaboration-buzz)