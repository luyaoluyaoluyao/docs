---
title: "Mendix 运行时的通信模式"
category: "Mendix 运行时间"
tags:
  - "studio pro"
  - "Mendix 运行时间"
  - "通信"
  - "运行时服务器"
  - "Mendix 客户端"
---

## 1 导言

本文档概述Mendix Runtime 环境对某些典型应用程序使用案例使用的通信模式。

本文件的目的是提供以下方面的资料：

*   评估Mendix Runtime在通信效率方面的质量
*   确定其设计决定对通信效率和性能的影响

## 2 Mendix Runtime 内的通讯大纲

Mendix 平台由以下部分组成：

*   Mendix Platform — — 一个用于设计、建造、部署和管理应用程序的完全集成的应用程序平台(aPaaS)
*   开发者门户——用于设计、开发和部署应用的基于网络的协作环境 管理用户和环境，只需单击即可即可即可将应用部署到云端，管理和监测其性能。
*   市场 — — 一个门户，拥有数百个公开可用的建筑块来加速应用开发
*   Mendix Studio and Studio Pro — Mendix 平台多用户建模工作室
*   团队服务器 - 管理应用程序模型版本的中央仓库
*   Mendix Runtime - 使用服务器部件( [Runtime Server](runtime-server))和客户端部件([Mendix 客户端](mendix-client))
*   编译——一个从伪装品如模型、样式表单和自定义 Java 类创建部署包
*   MxID - 一个适用OpenID 标准的用户管理和供给服务

本文件的重点是Mendix Runtime，更具体地说是以下部分之间的协作：

*   [Mendix 客户端](mendix-client) -- 一个React, React Native, 或 JavaScript 客户端运行在用户的设备上
*   [运行时服务器](runtime-server) — 一个运行在服务器上的 JavaScript 运行时, 负责执行微流程逻辑, 业务规则和持续的对象
*   RDBMS — — 在哪里保存数据

这些组成部分之间的联系如下：

*   Mendix 客户端发出两种类型的请求：
    *   静态资源，如页面、样式表、小部件、图像等。
    *   与应用数据相关的通讯，包括CRUD 关于可能需要数据的数据和逻辑的命令
*   运行时服务器使用由 JDBC 库处理的 SQL 语句与不同的 RDBMS 通信。
    *   应用程序数据存储在一个ER模型中的 RDBMS

## 3 基本CRUD通信模式

大多数Mendix 应用程序的核心涉及在 Mendix 实体中存储的数据上的 CRUD (创建、读取、更新和删除) 模式的变化。

使用 *员工* 实体的基本场景可以用以下两个页面在Mendix 中建模：

* 显示特定实体数据表的概览页面，如： ![](attachments/communication-patterns/19399028.png)
* 可以编辑实体的特定对象的详细页面，如： ![](attachments/communication-patterns/19399029.png)
   * 此详细信息页面可以使用新编辑按钮从第一个页面连接

以下各节概述处理这些页数时所涉及的行动。 如前所述，这种模式可以在许多Mendix 应用程序中看到。 但准确的运行时间结果取决于在构建应用程序时所做的许多细节和设计决定。 更先进的数据模型和网页将导致更多(和更复杂)的查询。

### 3.1 读取需要显示对象表的对象

显示天体表由以下步骤组成：

1. 获取页面的定义(可能已经缓存)。
2. 获取将显示在页面中的数据。
3. 正在更新页面。

基本序列图表看起来像这样：

![](attachments/communication-patterns/19399030.png)

Mendix 客户端使用 REST 式的协议向运行时服务器请求数据。 下面的示例显示当向员工实体请求对象时它看起来是什么样子：

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
   "context":[],
   "profiledata":□
      "204ee5ad0c056a0":15
   }
}
```

XPath 表达式表示需要什么数据。 这可以是一个包含某个实体的数据的对象，或者只是某个对象的某些属性，这是应用程序所要求的。

schema部分可以用来具体规定对需要什么数据(属性和多少对象)的额外限制。 这种方法确保最大限度地减少运行时服务器和 Mendix 客户端之间传输的数据量。

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

取决于显示的数据和域模型(例如适用于对象或属性的安全性) 检索可能导致更多查询或增加WHERE条款。

Runtime 服务器对Mendix 客户端的响应如下：

```json
{
   "count":2,
   "mxobjects":[
      {
         "objectType":"MyFirstModule.Employee",
         "guid":"281474976710757",
         "attributes":{
            "Firstname":{"value":"peter1"},
            "DateOfBirth":{"value":-315622800000},
            "Jobtitle":{"value":"sales"},
            "Department":{"value":"sales"},
            "Lastname":{"value":"jones"}
         }
      },
      {
         "objectType":"MyFirstModule.Employee",
         "guid":"281474976710657",
         "attributes":{
            "Firstname":{"value":"piet"},
            "DateOfBirth":{"value":476406000000},
            "Jobtitle":{"value":"consultant"},
            "Department":{"value":"expert services"},
            "Lastname":{"value":"jansen"}
         }
      }
   ]
}
```

### 3.2 创建新对象

创建新对象流的典型步骤包括：

1. 实例化一个新对象(主键由数据库生成，运行服务器保存一个PKS缓存)。
2. 显示编辑/新页面 (可能已被缓存)。
3. 将更新对象保存到 Runtime 服务器。
4. 将更新对象提交到数据库。

![](attachments/communication-patterns/19399031.png)

创建一个新对象：

```json
主席:
   "action":"instantiate",
   "params":□
      "objectype":"MyFirstModule.Employee",
      "preventCache":14550322466146
   },
   "context"::[],
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
   "context":[],
   "profiledata":□
      "204ee6970d53960":18
   }
}
```

将更新提交数据库：

```json
很抱歉，
   "action":"commit",
   "params":format@@
      "guid":"281474976710757"
   },
   "context":[],
   "profiledata":
      "204ee6e9b5eddc0":25
   }
}
```

提交将导致运行时服务器将对象保存到 RDBMS。 在提交之前，数据仅保存在运行服务器中，以优化性能并最大限度地减少对数据库的影响。

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
2. 显示编辑/新页面 (可能已被缓存)。
3. 在浏览器显示的页面中显示对象值。
4. 将对象的属性保存到 Runtime 服务器。
5. 从数据库中获取对象。
6. 验证对象更改。
7. 提交数据库中的更改。

![](attachments/communication-patterns/19399032.png)

保存对数据库的更改：

```json
很抱歉，
   "action":"change",
   "params":
      "2814749767107757":
         "Firstname":"peter1"
      }
   },
   "context":[],
   "profiledata":
      "204ee8b633f9a0":25
   }

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

```json
很抱歉，
   "action":"commit",
   "params":
      "guid":"281474976710757"
   },
   "context":[],
   "profiledata":□
      "204ee8ca8f775a0":20
   }
}
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
2. 向 Runtime 服务器发送删除请求。
3. 运行时服务器验证删除请求。
4. 运行时服务器从数据库中删除对象。
5. 提交数据库中的更改。
6. 通知客户端删除成功。
7. 刷新数据并更新页面。

以下序列图概述典型的删除场景：

![](attachments/communication-patterns/19399033.png)

删除对象：

```json
主席:
   "action":"delete",
   "params":
      "guids":["281474976710757"]
   },
   "context":[],
   "profiledata":□
      "204eae128284c0":323
   }
}
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
主席:
   "action":"retrieve_by_xpath",
   "params":□
      "xpath":"//MyFirstModule". mpluse”，
      "schema":□
         "id":"a2916c7c-af2f-4267-a8e9-99604f045861",
         "偏移":0,
         "sort":[["名字","asc"]],
         "amount":20
      },
      "计数":true,
      "合计":fals"
   },
   "上下文":[…],
   "releaseids":["281474976710757"],
   "profiledata":w
      "204eeb2972550c0":28
   }
}
```

## 4 执行业务日志

在Mendix中使用微流模拟业务逻辑。 以下各节介绍了涉及微型流动的一些典型流量。

### 4.1 显示微流获取的数据网格

页面上的数据网格往往与域模型中的实体直接相连。 另一种办法是使用微流创建一个要在数据网格中显示的对象列表。

一个从一个实体中检索所有对象的微流模式如下：

![](attachments/communication-patterns/19399034.png)

在这种情况下，所有对象都在一个请求中被传送到浏览器。 用户可以在不触发到 Runtime 服务器的通信的情况下通过所有对象。

这个情景的高级序列图表看起来就像这样：

![](attachments/communication-patterns/19399035.png)

JSON 操作从 Mendix 客户端到 Runtime 服务器：

```json
{
   "action":"executeaction",
   "params":{
      "actionname":"MyFirstModule.GetAllEmployees",
      "applyto":"none"
   },
   "context":[],
   "profiledata":{
      "204f418ba05e7c0":55
   }
}
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

从 Runtime 服务器到Mendix 客户端的响应：

```json
{
   "actionResult":[
      {
         "objectType":"MyFirstModule.Employee",
         "guid":"281474976710657",
         "attributes":{
            "Firstname":{"value":"piet"},
            "DateOfBirth":{"value":476406000000},
            "Jobtitle":{"value":"consultant"},
            "Department":{"value":"expert services"},
            "Lastname":{"value":"jansen"}
         }
      },
      {
         "objectType":"MyFirstModule.Employee",
         "guid":"281474976710957",
         "attributes":{
            "Firstname":{"value":"wee"},
            "DateOfBirth":{"value":1454886000000},
            "Jobtitle":{"value":"ewji"},
            "Department":{"value":"wew"},
            "Lastname":{"value":"ewfeew"}
         }
      },
      {
         "objectType":"MyFirstModule.Employee",
         "guid":"281474976710958"
         …
      }
      …
   ]
}
```

## 5 Mendix Runtime Internals

从CRUD 场景描述可以看出，Mendix Platform 确保了效率，同时以多种方式运行应用程序：

*   只有用户操作所需的数据才能参与通信和处理
*   在不同流程之间通信时使用高效的运输协议
    * 在 Mendix 客户端和 Runtime 服务器之间使用JSON 格式
    * RDBMS通信的原生SQL协议
*   Mendix 客户端中已经可用的数据可能被重新使用(见编辑情景，在编辑/新页面中为数据网格获取的数据被重新使用)

### 5.1 数据转换

数据将根据需要在 Mendix 客户端和数据库之间传输。 从Mendix 客户端到数据库并返回全圈时应用以下转换：

*   用户在页面中输入的数据存储在 JavaScript 对象中
*   若要连接到 Runtime 服务器，JavaScript 对象将序列化为 JSON
*   运行时服务器将 JSON 对象转换为 java MxObjects
*   MxObject 属性绑定到 SQL 查询所需的 SQL 语句参数
*   JDBC 结果集数据转换为 MxObjects
*   MxObjects 发送到Mendix 客户端时序列化为 JSON

### 5.2 状态

为方便(水平) 可缩放，Mendix Runtime 没有保留请求之间的状态。 总的策略是在请求时仅有脏天体存内存. 对象如果被更改则被视为肮脏，但这些更改尚未持续到RDBMS。

![](attachments/communication-patterns/19399036.png)

### 5.3 持久性

Mendix 自动注意将应用程序特定实体模型(域模型)翻译成技术的 RDBMS 特定ER模型。 如CRUD 场景中读取的部分所示，数据检索用易于理解的 XPath 构造表示。 例如，要检索所有员工对象，可以使用下列XPath

`//MyFirstModule.employee`

此 XPath 表达式被翻译成若干步骤到数据库查询：

1. XPath 被翻译为内部的 OQL 语法。 OQL类似于SQL，但仍以应用程序域模型实体表示应用程序数据，而不是实际的 RDBMS 表。
2. 在域模型中指定的 OQL 语句中添加了额外的必要表达式（例如添加超类实体的信息）。
3. 域名模型安全限制适用于OQL报表。
4. OQL被翻译成SQL并在已配置的 RDBMS 上通过 JDBC 执行。

### 5.4 范围

运行时服务器可以作为单一进程运行，或者可以水平缩放，以方便更多的并行用户并提高可用性。 在此情景下，正在运行多个Mendix Studio Pro 实例。 这些情况是独立发生的，各进程之间不会有任何交流。

#### 5.4.1 单一实例

在一个实例中，Scala Akka 执行者模型用于高效处理运行服务器中的所有处理。 使用一个演员模型具有这种好处：可以处理的并行用户数量不受可用线程数的限制。 因为线程不是按请求分配的，而是通过处理责任

若要处理 Runtime Server 收到的 Mendix 客户端请求，所需行动将被发送到Akka 演员。 这个演员拥有一个专用的线程池。 每一个 (microflow) 动作由一个单独的消息处理给动作调度员. 这优化了屏蔽操作的线程使用率。 例如，如果微流的一个动作部分呼叫外部网络服务并被阻止等待响应。 这只会影响动作调度器的线程池，而不是HTTP请求处理器。

#### 5.4.2 多实例

Mendix 运行状态保存在Mendix 客户端。 这意味着当在水平缩放场景中运行时, 所有实例都会在负载均衡器后运行，请求都会发送到任何最合适的实例。
