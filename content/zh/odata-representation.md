---
title: "OData 代表"
parent: "已发布的 odata 服务"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/odata-representation.pdf)。
{{% /报警 %}}

本文件介绍了各实体如何在已出版的OData服务中派代表参加的情况。

## 1个属性

| Mendix 数据类型                  | 编辑类型               | 属性值                                  | Atom XML 代表                          |
| ---------------------------- | ------------------ | ------------------------------------ | ------------------------------------ |
| ID <sup>1</sup> <sup>2</sup> | Edm.Int64          | 3940649673954387                     | 3940649673954387                     |
| Autonumber                   | Edm.Int64          | 1                                    | 1                                    |
| 二进制(不支持) <sup>3</sup>        |                    |                                      |                                      |
| Boolean                      | Edm.Boolean        | true                                 | true                                 |
| 日期和时间                        | Edm.DateTimeOffset | Fri, 19 December 2014 10:27:27 GMT   | 2014-12-19T10：27：27.000Z             |
| 枚举数                          | 编辑字符串              | 蓝色                                   | 蓝色                                   |
| 大小数                          | Edm.Decimal        | 0.3333333333333333333333333333333333 | 0.3333333333333333333333333333333333 |
| 哈希字符串                        | 编辑字符串              | HashPassword                         | HashPassword                         |
| 整数                           | Edm.Int64          | 50                                   | 50                                   |
| 长 <sup>2</sup>               | Edm.Int64          | 3940649673954387                     | 3940649673954387                     |
| 字符串 <sup>4</sup>             | 编辑字符串              | 约翰文                                  | 约翰文                                  |

<sup>1</sup>在服务的元数据中。 ID被标记为 `isAttribute="false"` (使用 Mendixspecific XML 属性在 `http://www)。 endix.com/Protocols/MendixData` namespace) 以表明这些不是出现在域模型中的属性。 注意： `isAttribute="false"` 功能已被介绍到 Studio Pro [8.6.0](/releasenotes/studio-pro/8.6#860)中。<br /> <sup>2</sup>使用 Excel 导入OData 源时，长号可能会被切断。 这是因为数据类型微软使用的限制。 欲了解更多信息，请参阅

当您在Excel的单元格中输入长号时，最后一位数字会更改为零。<br /> <sup></sup>即使不支持二进制数据类型。 支持 FileDocument 和图像系统实体，并以Base64 编码字符串表示 `编辑。 文件` 类型。<br /> <sup>4</sup>当字符串属性长度有限时，指定了 `MaxLength` 属性。 注意：此功能已被介绍在 Studio Pro [8.16.0](/releasenotes/studio-pro/8.16#8160) 中。</p> 

此外，一个 `更新了` 字段的 OData 条目来自一个实体的系统更改日期属性。 如果此属性不可用(因为它没有被曝光)，用户没有访问权限 或者它在数据库中是空的。默认日期(1-1-1970)。



## 2 协会 {#associations}

在OData服务的设置中，您可以选择关联的表现方式。 有两种备选办法，下文将加以说明。



### 2.1 作为链接

当您选择作为链接代表关联时，每个对象包含每个关联的链接。 可以通过这些链接检索相关对象。

这意味着您只能在另一方的实体也是此服务的资源时揭露一个协会。 这也意味着您不能在同一服务中多次发布同一个实体 (因为在这种情况下)。 不清楚这种联系应指向何处)。

使用这种方法，你可以揭露社团的两面，你可以揭露多个社团。



### 2.2 作为关联对象ID

当您选择将映射作为关联对象 ID时，关联对象的 ID 表示为 `编辑。Int64` 属性。 如果关联指一个以上的对象，你不能从那边揭露它。
