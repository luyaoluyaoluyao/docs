---
title: "SIG-Mendix 性能主题"
category: "Mendix 运行时间"
---

## 1 导言

本文档概述Mendix Runtime 环境对某些典型应用程序使用案例使用的通信模式。

以下是本文件的目标：

*   提供关于通信效率的Mendix Runtime环境质量的信息
*   提供信息以确定其设计决定对通信效率和性能的影响

编写这份文件是为了解决SIG缺少的信息，以评估Mendix 应用程序的性能效率。 该文件最后一节概述了SIG在这个问题上的得分以及本文件如何处理这些要求。

## 2 Mendix Runtime 环境中的通信提纲。

Mendix 平台由以下部分组成：

*   Mendix Platform — — 完全集成的应用程序平台作为服务(aPaaS) 用于设计、建造、部署和管理应用

*   开发者门户——基于网络的应用设计、开发和部署合作环境， 管理用户和环境，只需单击即可即可即可将应用部署到云端，管理和监测其性能。

*   市场 — — 一个门户，拥有数百个公开可用的建筑块来加速应用开发

*   Mendix Modeler - Mendix 平台多用户建模工作室
*   团队服务器 - 管理应用程序模型版本的中央仓库
*   运行环境——使用服务器部件(Mendix Runtime)和客户端部件(Mendix 客户端) 运行应用程序
*   生成 — — 从伪品如模型、样式表和自定义 Java 类创建部署包
*   MxID - 一个适用OpenID 标准的用户管理和供给服务

本文件的重点是Mendix Runtime 环境，更具体地说，是下列部分之间的协作：

*   Mendix 客户端 — JavaScript 客户端在用户浏览器中运行
*   Mendix Runtime — JavaScript /cala运行于服务器上，负责执行微流程逻辑、业务规则和持久对象
*   RDBMS — — 在哪里保存数据
*   可选，州商店在水平缩放运行时间实例之间共享状态

这些组成部分之间的联系如下：

*   Mendix 客户端发出两种类型的请求：
    *   静态资源，如页面、样式表、小部件、图像等。
    *   与应用数据相关的通讯，包括CRUD 关于可能需要数据的数据和逻辑的命令
*   Mendix Runtime 通信使用由 JDBC 库处理的 SQL 语句
    *   应用程序数据存储在一个ER模型中的 RDBMS

## 3 基本CRUD通信模式

大多数Mendix 应用程序的核心涉及在 CRUD 模式上的变异——创建、阅读、更新和删除存储在 Mendix 实体中的数据。

这个基本场景可以用以下两个页面用Mendix模型化：

* 显示特定实体数据表的概览页面，如：

  ![](attachments/19202918/19399028.png)

* 可以编辑实体的特定对象的详细页面，如：

  ![](attachments/19202918/19399029.png)

  * 可以使用新编辑按钮从第一个页面到达此页面


以下各节概述执行这些页面时所涉及的行动。 如前所述，这种模式可以在许多Mendix 应用程序中看到。 但准确的运行结果取决于使用Mendix Modeler构建应用程序时所做的许多细节和设计决定。 更先进的数据模型和网页将导致更多（复杂）查询。

### 3.1 显示对象表所需读取对象

显示天体表由以下步骤组成：

1. 获取页面定义(如果浏览器尚未缓存)。
2. 获取将显示在页面中的数据。
3. 正在更新页面。

基本序列图表看起来像这样：

![](attachments/19202918/19399030.png)

Mendix 客户端使用REST式协议向Mendix Runtime请求数据。 下面的示例显示了当向雇员实体请求对象时它看起来是什么样子：

```json
主席:
   "action":"retrieve_by_xpath",
   "params":□
      "xpath":"//MyFirstModule". mpluse”，
      "schema":□
         "id":"a2916c7c-af2f-4267-a8e9-99604f045861",
         "偏移":0,
         "sort":[
            [
               "sirname",
               "as"
            ]

         "amount":20
      },
      "计数":true"
      "汇总":fals"
   },
   "上下文":[
   ],
   "profiledata":□
      "204ee5ad0c056a0":15
   }
}
```

XPath 表达式表示需要什么数据。 这可能是一个实体——或仅仅是一个实体的某些属性——的申请所要求的。

schema部分可以用于指定对需要什么数据的额外限制(哪些属性和多少记录)。 这种方法确保最大限度地减少Mendix Runtime 和 Mendix 客户端之间传输的数据量。

这个检索两个SQL查询结果。一个是检索数据，另一个是检索对象总数。

```sql
 SELECT "myfirst module$employee"."id",
 "myfirstmodule$employee"."日期出生",
 "myfirfirst module$employee". 部门”，
 "myfirstmodule$employee"."firstname",
 "myfirstmodule$employee"."jobtitle",
 "myfirfirstmodule$employee". 姓氏”
 FROM "myfirst module$employee"
 ORDER BY "myfirst module$employee". firstname” ASC,
 "myfirst module$employee"."id" ASC LIMIT 20
 SELECT COUNT(*)
 FROM "myfirst module$employee"
```

取决于显示的数据和域模型(继承和行或属性安全的使用) a 检索可能会导致更多的查询或在条款中产生更多的问题。

Mendix Runtime 对 Mendix 客户端的响应如下：

```json
{"count":2,"mxobjects":[{"objectType":"MyFirstModule.Employee","guid":"281474976710757","attributes":{"Firstname":{"value":"peter1"},"DateOfBirth":{"value":-315622800000},"Jobtitle":{"value":"sales"},"Department":{"value":"sales"},"Lastname":{"value":"jones"&#125;&#125;},{"objectType":"MyFirstModule.Employee","guid":"281474976710657","attributes":{"Firstname":{"value":"piet"},"DateOfBirth":{"value":476406000000},"Jobtitle":{"value":"consultant"},"Department":{"value":"expert services"},"Lastname":{"value":"jansen"&#125;&#125;}]}
```

### 3.2 创建新对象

创建新对象流的典型步骤包括：

1. 实例化一个新对象 (主键由数据库生成，Mendix Runtime 保存一个PKS缓存)。
2. 获取编辑表单(如果尚未被浏览器缓存)。
3. 在 Mendix Runtime 中保存更新的对象。
4. 将更新对象提交到数据库。

![](attachments/19202918/19399031.png)

创建一个新对象：

```json
主席:
   "action":"instantiate",
   "params":}
      "objectype":"MyFirstModule.Employee",
      "preventCache":14550322466146
   },
   "context":[
   ],
   "profiledata":
      "204ee68c92aea60":27
   }

```

保存对象到数据库：

```json
主席:
   "行动":"改变",
   "params":□
      "281474976710757":□
         "Firstname":"peter",
         "Lastname":"jones",
         "Jobtitle":"sales",
         "部门":"销售",
         "DateOfBirth":-315622800000
      }
   },
   "上下文":[
   ],
   "profiledata":□
      "204ee6970d53960":18
   }
}
```

将更新提交数据库：

```java
{"action":"commit","params":{"guid":"281474976710757"},"context":[],"profiledata":{"204ee6e9b5eddc0":25&#125;&#125;
```

提交将导致Mendix Runtime保存对象到RDBMS。 在提交之前，数据仅保存在Mendix Runtime中，以优化性能和尽量减少对数据库的影响。

```sql
 INSERT INTO "myfirst module$employee" ("id",
 "firstname",
 "dateof出生",
 "jobtitle",
 "departy",
 "lastname")
 VALUES (?
 ?,
 ?,
 ?,
 ?,
?)
```

### 3.3 编辑现有对象

典型的编辑现有对象流程由以下步骤组成：

1. 选择对象页面表中的对象(概览页面)。
2. 获取编辑表单(如果尚未被浏览器缓存)。
3. 在浏览器中显示已经可用的对象值。
4. 将对象已更改的属性保存到 Mendix Runtime。
5. 从数据库中获取对象。
6. 验证对象更改。
7. 提交数据库中的更改。

![](attachments/19202918/19399032.png)

保存对数据库的更改：

```java
{"action":"change","params":{"281474976710757":{"Firstname":"peter1"&#125;&#125;,"context":[],"profiledata":{"204ee8b633f9a0":25&#125;&#125;
```

这将在数据库中触发以下行动：

*   从数据库获取原始对象
*   更新用户在 Runtime 中更改的属性

第一个步骤是确定实体上定义的所有数据业务逻辑和验证。

```sql
 SELECT "myfirfirst module$employee"."id",
 "myfirfirst module$employee"."firfiredname",
 "myfirfirst module$employee"."dateofbir",
 "myfirst module$employee". jobtitle”，
 "myfirstmodule$employee"."."department",
 "myfirfirstmodule$employee"."lastname"
 FROM "myfiredmodule$employee"
 WHERE "myfirst module$employee"."id" = (281474976710857)
```

如果所有验证运行正确，客户端可以将更改提交数据库：

```java
{"action":"commit","params":{"guid":"281474976710757"},"context":[],"profiledata":{"204ee8ca8f775a0":20&#125;&#125;
```

这将触发数据库的实际更新和提交。

```sql
 更新"myfirst module$employee"
 SET "dateofbiry" = ?
 “id” = ？
```

### 3.4 删除现有对象

典型的删除流程由以下步骤组成：

1. 选择对象表中的对象(概览页面)。
2. 向Mendix Runtime发送删除请求。
3. Mendix 运行时验证删除请求。
4. Mendix Runtime 从数据库中删除对象。
5. 提交数据库中的更改。
6. 通知客户端删除成功。
7. 刷新数据并更新页面。

以下序列图概述典型的删除场景：

![](attachments/19202918/19399033.png)

删除对象：

```java
{"action":"delete","params":{"guids":["281474976710757"]},"context":[],"profiledata":{"204eeae128284c0":323&#125;&#125;
```

在实际删除数据之前获取对象以启用运行业务逻辑、规则和事件：

```sql
 SELECT "myfirfirst module$employee"."id",
 "myfirfirst module$employee"."firfiredname",
 "myfirfirst module$employee"."dateofbir",
 "myfirst module$employee". jobtitle”，
 "myfirstmodule$employee"."."department",
 "myfirfirstmodule$employee"."lastname"
 FROM "myfiredmodule$employee"
 WHERE "myfirst module$employee"."id" = (281474976710857)
```

从数据库中删除对象：

```sql
从"myfirst module$employee"
“id” = ?
```

刷新数据网格：

```json
{"action":"recheve_by_xpath","params":{"xpath":"//MyFirstModule.Employe","schema":{"id":"a2916c7c-af2f-4267-a8e9-99604f045861","offset":0,"sort":["Firstname","ask"],"amount":20},"count":true,"合计":"false},"context":[],"releaseids"::["281474976710757"],"profiledata":{"204eeb2972550c0":28&#125;&#
```

## 4 执行业务日志

在Mendix中使用微流模拟业务逻辑。 以下各节介绍了涉及微型流动的一些典型流量。

### 4.1 显示微流获取的数据网格

页面上的数据网格往往与域模型中的实体直接相连。 另一种办法是使用微流创建一个要在数据网格中显示的对象列表。

一个从一个实体中检索所有对象的微流模式如下：

![](attachments/19202918/19399034.png)

在这种情况下，所有对象都在一个请求中被传送到浏览器。 用户可以在不触发到 Mendix Runtime的情况下通过所有对象进行页面访问。

这个情景的高级序列图表看起来就像这样：

![](attachments/19202918/19399035.png)

JSON 操作从 Mendix 客户端到 Mendix 运行时间：

```java
{"action":"executeaction","params":{"actionname":"MyFirstModule.GetAllemployees","applyto":"none"},"context":[],"profiledata":{"204f418ba05e7c0":55&#125;&#125;
```

数据库中执行的 SQL 语句：

```sql
SELECT "myfirfirst module$employee"."id",
"myfirfirst module$employee"."firfiredname",
"myfirfirst module$employee"."dateofbir",
"myfirst module$employee". jobtitle",
"myfirst module$employee"."."department",
"myfirst module$employee"."lastname"
FROM "myfirst module$employee"
```

Mendix Runtime 对 Mendix 客户端的响应：

```json
{"actionResult":[{"objectType":"MyFirstModule.Employee","guid":"281474976710657","attributes":{"Firstname":{"value":"piet"},"DateOfBirth":{"value":476406000000},"Jobtitle":{"value":"consultant"},"Department":{"value":"expert services"},"Lastname":{"value":"jansen"&#125;&#125;},{"objectType":"MyFirstModule.Employee","guid":"281474976710957","attributes":{"Firstname":{"value":"wee"},"DateOfBirth":{"value":1454886000000},"Jobtitle":{"value":"ewji"},"Department":{"value":"wew"},"Lastname":{"value":"ewfeew"&#125;&#125;},{"objectType":"MyFirstModule.Employee","guid":"281474976710958
…
}]}
```

## 5 Mendix Runtime Internals

从CRUD 场景描述可以看出，Mendix Platform 确保了效率，同时以多种方式运行应用程序：

*   只有用户操作所需的数据才能参与通信和处理
*   在不同流程之间通信时使用高效的运输协议
    * 在 Mendix 客户端和 Mendix 运行时间之间使用 JSON 格式
    * RDBMS通信的原生SQL协议
*   Mendix 客户端中已经可用的数据可能被重新使用(见编辑表中为数据网格获取的数据重新使用的编辑场景)

### 5.1 数据转换

数据将根据需要在 Mendix 客户端和数据库之间传输。 从Mendix 客户端到数据库并返回全圈时应用以下转换：

*   用户在表单中输入的数据存储在 JavaScript 对象中
*   要与 Mendix Runtime通信, JavaScript 对象将序列化为 JSON
*   Mendix 运行时间将 JSON 对象转换为 java MxObjects
*   MxObject 属性绑定到 SQL 查询所需的 SQL 语句参数
*   JDBC 结果集数据转换为 MxObjects
*   MxObjects 发送到Mendix 客户端时序列化为 JSON

### 5.2 状态

为了方便(水平) 可缩放，Mendix 平台将状态保存在Mendix Runtime 内存中。 总的策略是在内存中仅有肮脏的物体，其他物体则在请求结束时清理。 对象如果被更改则被视为肮脏，但这些更改尚未持续到RDBMS。 每次会话都保持状态。

![](attachments/19202918/19399036.png)

### 5.3 持久性

Mendix 自动注意将应用程序特定实体模型(域模型)翻译成技术的 RDBMS 特定ER模型。 如CRUD 场景中读取的部分所示，数据检索用易于理解的 XPath 构造表示。 例如，要检索所有员工对象，可以使用下列XPath

`//MyFirstModule.employee`

此 XPath 表达式以若干步骤处理到数据库查询：

1. XPath 被翻译为内部的 OQL 语法。 OQL类似于SQL，但仍以应用程序域模型实体而不是技术表格表示应用程序数据。
2. 在域模型中指定的 OQL 语句中添加了额外的必要表达式（例如添加超类实体的信息）。
3. 域名模型安全限制适用于OQL报表。
4. OQL被翻译成SQL并在已配置的 RDBMS 上通过 JDBC 执行。

### 5.4 范围

Mendix Runtime 可以作为单一进程运行，或者可以水平缩放，以方便更多的并行用户并提高可用性。 在这个场景中，正在运行多个Mendix Moderr 实例。 这些情况是独立发生的，各进程之间不会有任何交流。

#### 5.4.1 单一实例

在一个实例中，Scala Akka 演员模型被用来高效率地处理Mendix Runtime中的所有处理。 使用一个演员模型具有这种好处：可以处理的并行用户数量不受可用线程数量的限制。 因为线程不是按请求分配的，而是通过处理责任

要处理 Mendix Runtime收到的 Mendix 客户端请求，所需的操作将被发送到Akka 演员。 这个演员拥有一个专用的线程池。 每一个 (microflow) 动作由一个单独的消息处理给动作调度员. 这优化了屏蔽操作的线程使用率。 例如，如果微流的一个动作部分呼叫外部网络服务并被阻止等待响应。 这只会影响动作调度器的线程池，而不是HTTP请求处理器。

#### 5.4.1 多实例

当在水平缩放场景中运行时，Mendix Runtime 状态通过Redis州商店进行协调。 在每次请求结束时，会话的所有肮脏对象都被写入Redis statstore。 在新请求开始时，将从Redisstatstore读取此状态。

![](attachments/19202918/19399037.png)
