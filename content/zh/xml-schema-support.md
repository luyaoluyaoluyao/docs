---
title: "XML Schema 支持"
parent: "xml-schemas"
tags:
  - "studio pro"
---

## 1 导言

Mendix 通过解释 XML Schema 定义(XSD) 文件获取用于导入/导出的 XML 输入/输出以及调用 SOAP/XML 网络服务的输入/输出格式。 当您导入一个 XML schema (.xsd 文件) 或 web 服务定义(. ) 使用 Mendix Studio Pro（sdl 文件），您可能会得到一个包含不支持的构造警告信息的对话框。 这是因为当前Mendix 不支持整个XSD 标准。 Mendix 中的映射基于实体和属性，而某些XSD 构造并不容易使用此格式。 下表显示在 Mendix 中支持哪些XSD 构造。

| XSD 构造设备 | 支持的                  |
| -------- | -------------------- |
| 群組       | 否                    |
| 序列       | 仅当它发生一次              |
| 选择       | 仅当个别选项不是序列元素时        |
| 唯一的      | 否                    |
| 属性组      | 否                    |
| 所有的      | 仅当 **的每个子元素** 最多发生一次 |
| 联盟       | 否                    |
| 任意一个     | 否                    |
| 任何属性     | 否                    |
| 邮件列表     | 否                    |

Mendix中有两种XML映射：导入映射，将XML数据转换为 Mendix 对象，导出映射则相反操作。 导入映射使用微流中的“导入 XML 活动”导入XML 文件时，以及用于处理网络服务呼叫的响应。 导出映射用于导出微流中的 XML 文件和生成网络服务呼叫请求的 XML 文件。

在映射编辑器中导入映射： 您可以通过 XSD 检查可以在 XML 中发生的元素，然后定义Mendix 对象的映射。 这并不是什么时候发生或是在什么样的顺序上发生；一旦发生某一元素，则适用该元素的相应制图。

如果XSD 包含任何不支持的构造，那么它们将会被高亮显示在映射编辑器中，带有此警告图标： ![](attachments/16713707/16843903.png)

这是每个不支持的元素或属性的旁边。 检查任何此种元素或属性将导致一致性错误。

使用导出映射生成的 XML 必须严格遵守XSD 规格。 这意味着由映射生成的 XML 标签必须是 XSD 指定的确切顺序。

## 2 个元素和类型

XSD 定义了与 XML标签相对应的元素。 元素有定义其内容的类型，例如原始值或子元素列表。 元素可以是简单的类型，也可以是复杂的类型，而复杂的类型可以是简单或复杂的内容。 对于简单内容简单的简单类型和复杂类型， 元素的内容是原始值，例如整数或字符串值。 对于复杂内容的复杂类型，元素的内容可以由几个子元素组成。 复杂类型也可以定义可以在 XML 标签中发生的属性。

下面的示例显示一个 XML schema 和 一个 XML 实例，这两个实例都与该schema 保持一致。 schema定义了一个“客户”元素，其类型复杂且内容复杂，即“name”和“shoesize”元素的顺序。 “名称”元素有一个简单的类型，即“字符串”。 'shoesize' 元素有一个简单内容的复杂类型；它通过添加一个“国家”属性来扩展简单类型的“整数”。

**示例 XML schema**

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema targetNamespace="http://www.example.com/" elementFormDefault="qualified" xmlns:tns="http://www.example.com/" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="name" type="xs:string"/>
        <xs:element name="shoesize" type="tns:shoesizeType"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:complexType name="shoesizeType">
    <xs:simpleContent>
      <xs:extension base="xs:integer">
        <xs:attribute name="country" type="xs:string"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
</xs:schema>

```

**示例 XML 实例**

```xml
<?xml version="1.0" encoding="utf-8"?>
<customer xmlns="http://www.example.com/">
  <name>John Doe</name>
  <shoesize country="GB"></shoesize>
</customer>

```

Mendix 中的 XML 映射基于由实体、属性和协会组成的域模型， 当您创建映射时，XSD 元素会被翻译成某种对象模型。 具有复杂类型或多次发生的元素被翻译成被映射给实体的所谓“对象元素”。 具有简单类型并且最多一次出现的元素被翻译成“值元素”，并映射到包含对象元素实体的属性。 复杂类型的 XML 属性也被翻译成值元素。

下面的图像显示了如何将上一个示例的 XML schema 转换为 Mendix 映射。 这是示例“客户”元素的 XML-域映射。 “客户”元素被翻译为对象元素(灰色矩形)， 当“name”和“shoesize”元素和“shoesize”元素的国家属性被翻译成映射中的元素。

## 3 个属性

复杂类型可以指定可以在 XML 标签中发生的属性。 这些属性总是有一种简单的类型，最多可以出现一次。 这两种映射类型都完全支持属性。 属性被转换为值映射中的元素，因此可以映射到实体的属性。

## 4 种简单类型 & 有简单内容的复杂类型

Mendix 完全支持原始内容的元素，例如简单类型或简单内容的复杂类型。 然而，Mendix 目前没有考虑到简单类型的限制。 例如将字符串限制为一组有限的可能性或限制一个整数的范围。 在这种情况下，允许基本类型（例如字符串）的所有可能值。

通常，原始内容的元素被翻译成在映射中值元素。 如果由于某种原因，原始内容的元素被翻译成映射中的对象元素， 例如，因为它不止一次发生， 或者因为它有一个复杂的类型，它也定义了属性，元素的内容被翻译成一个额外的值元素，叫做“(内容)”。

{{% alert type="info" %}}
十六进制二进制类型被识别为字符串，所以二进制类型操作不适用于十六进制二进制(如MTOM 附件)。
{{% /报警 %}}

## 5种带复杂内容的复杂类型

对于具有复杂内容的复杂类型的元素，元素的内容可以由几个子元素组成。 由一个或多个分组构造，如选择和序列来定义顺序和多重性。

## 6 个混合内容

复杂类型可以将其内容定义为混合。 这意味着一个元素包含文本和子元素作为内容。 混合的内容通常见于文件数据，如(X)HTML，而在结构化数据中则不太常见。 目前，Mendix不支持混合内容。
