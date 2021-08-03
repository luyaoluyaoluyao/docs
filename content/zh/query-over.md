---
title: "查询超限"
parent: "关联"
menu_order: 20
tags:
  - "查询"
  - "自参考"
  - "关联"
  - "域模型"
---

## 1 导言

有时，您想要创建一个更通用的域模型，以便在数据的类型和结构上有更大的灵活性。 在这种情况下，您常常转而使用继承或自我引用来允许使用简单但有效的设计模型。 这使构建您的微流程和应用程序逻辑变得更容易， 但查询正确的对象可能变得很有挑战性，特别是当您使用自引用。

## 2 示例

此示例用于实现计算机上的文件夹，一个文件夹可以包含几个子文件夹。

![](attachments/associations/query-over-example-structure.png)

要实现这一点，请使用 **文件夹** 的自引用。 自引用是一个名为 **文件夹子文件夹** 的关联。 这允许您建立一个无限数量和级别的文件夹结构。

{{% alert type="info" %}}
在这种情况下，协会是一个一对多的协会，但对多个或一对一个协会也采用同样的方法。
{{% /报警 %}}

![](attachments/associations/self-reference-domain-model.png)

如果我们在一个名为 **QueryOver**的模块中创建我们的文件夹功能， 关联 **文件夹子文件夹** 在域模型中用两种方式描述：

| 名称      | 类型 | 所有者  | 父级            | 儿童            |
| ------- | -- | ---- | ------------- | ------------- |
| 文件夹子文件夹 | 参考 | 默认设置 | QueryOver.文件夹 | QueryOver.文件夹 |

* 多重性：一个'文件夹'对象与多个'文件夹'对象关联

**儿童** 是该社团 **所有者** - 换句话说，该社团总是通过该儿童更新的。

![](attachments/associations/query-over-association.png)

上面的示例中有六个文件夹，数据库的结构和属性填充如下所示。 在 **文件夹子文件夹** 表中， **ChildfolderID** 在左侧显示，因为它是关联的所有者。

![](attachments/associations/query-over-example-database.png)

For more information on how domain models are implemented in databases, see the [Implementation](domain-model#implementation) section of *Domain Model*.

### 2.1 从文件夹(父母)检索子文件夹(子文件夹)

如果您在您的微流程中有 $ChosenFolder 个对象，您可以轻松地检索子文件夹。 每个协会都有权利方（协会的家长）和左方（儿童或协会的所有者）。  平台读取每个关联并决定父是否等于 $ChosenFolder。

这是使用以下的 XPath 约束实现的： `[QueryOver.Folder_subFolder=$ChosenFolder]` XPath 约束从右边读取，结果为文件夹。 这是您如何解释您关注的关联方向的关键。

{{% image_container width="400" %}}
![](attachments/associations/query-over-retrieve-normal.png)
{{% /image_container %}}

如果 $ChosenFolder 对象有 **代码** `202002141322015` 和 **名称** `子文件夹 2` 我们选择的文件夹有 **ID** `3`。 左手表中用橙色突出显示的两个文件夹将被还原。 平台默认对社团的权利/父母一方施加约束，并返回相关的 ChildFolder(s)。

![](attachments/associations/query-over-retrieve-normal-tables.png)

### 2.2 从文件夹中获取父文件夹

当你有 $ChosenFolder 个对象可用并且你想要检索它的父文件夹(下一级的文件夹) 例如，给出了 **子文件夹2** 你想要从数据库中获取 **Mainfolder**的数据，因此变得更加复杂。

使用表达式 `[逆向(]` 来指示Mendix 读取它通常使用的约束.

{{% alert type="info" %}}
`[逆变量]` 只适用于一个关联。 如果您有多个关联，它们将继续被正常解读。 查看 [创建更复杂的查询](#more-complex)。

`[reversed()]` 表达式只能应用于自引用上。 当一个关联在两个不同的对象类型之间时，平台将能够自动确定加入的方向。
{{% /报警 %}}

 在我们的例子中，我们想要找到一个 $ChosenFolder 的父文件夹。 现在，查询将变为 `[QueryOver.Folder_sub文件夹[revers()]=$ChosenFolder]` 该协会不是从左边（父母到孩子）阅读，而是从左边读到右边。

{{% image_container width="400" %}}
![](attachments/associations/query-over-retrieve-reversed.png)
{{% /image_container %}}

如果 $ChosenFolder 对象有 **代码** `202002141322015` 和 **名称** `子文件夹 2` 我们选择的文件夹有 **ID** `3`。 右手表中用橙色突出显示的文件夹将被还原。 平台在社团左/儿童一侧反向应用约束并返回相关的父文件夹。

![](attachments/associations/query-over-retrieve-reversed-tables.png)

### 2.3 创建更复杂的查询 {#more-complex}

前面的例子很简单。 然而， `[reversed()]` 表达式可以用于更复杂的查询。

例如，说每个文件夹都可以包含多个文件，关联到关联关联的 **File_folder**。

![](attachments/associations/query-over-extended-domain-model.png)

您想要获取文件夹对象 $ChosenFolder 上级文件夹中的所有文件。

使用约束 `[QueryOver.File_Folder/QueryOver.Folder/QueryOver。 older_subfolder[revers()]=$ChosenFolder]` 返回所有 **文件** 对象与 **文件夹相关联，** 对象（作为父文件夹）与 **文件夹** 相同 **$ChosenFolder**

![](attachments/associations/query-over-retrieve-complex.png)

如果 $ChosenFolder 对象是 `子文件夹2`, 您将在关联上检索所有 **文件** 与 `Main文件夹相关联的对象` **File_文件夹**

## 3个专业协会

当一个一对一的社团具有自己的专业化时，您不能通过社团检索 [](retrieve#source)。

这是一个示例继承：

![](attachments/associations/limitation.png)

In this example, a list of **Specializations** cannot be retrieved when using a standard by-association retrieve in a microflow if the input is the specialization.

然而，这个限制有一个解决方法：可以使用 Java API通过一个 Java 动作检索专业化列表。 此 Java 动作需要两个参数： **Specialization** 和布尔 **通过此代码片段** 反转：

```
公共类RetrieveAsAssociatedWEB 扩展 CustomJavaScript<java.util.List<IMendixObject>>
*
    private IMendixObject __B;
    私人主机。 roxies.Specialization B;
    private java.lang.Boolian Reverse;

    public RetrieveAsAssociatedwithout (IContext context, IMendixObject B, java.lang. oolian Reverse)
    夺取股份权者
        super(context);
        _B = B；
        everse = reverse；
    }

    @java。 override
    public java.util. ist<IMendixObject> executeAction() passes Exception
    por
        there = __B == nul？ nul: main.proxies.Specialization.initialize(getContext(), __B);

        // BEGIN USER CODE
        return Core.re.recheveByPath(getContext(), __B, "Main.Generalization_Specialization", Reverse);
        // END USER CODE
    }
 
 format@@}
```

{{% alert type="info" %}}
请务必导入 `com.mendix.core` 以便您能够在这个代码片段中执行 `Core.re.recheveByPath(...)`
{{% /报警 %}}

当设置 `反向` 布尔为真并使用 `专业化` 对象作为输入时， 返回的列表将包含所有与专业化相关的概括。
