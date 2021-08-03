---
title: "运行时自定义"
category: "Mendix 运行时间"
description: "描述服务器自定义设置，日志文件，数据库，Amazon S3存储服务，IBM 云对象存储， Mendix 中的 Microsoft Azure, IBM Bluemix 对象存储, web 客户端和代理服务器。"
tags:
  - "运行时间"
  - "自定义"
  - "设置"
  - "配置"
  - "IBM 云"
  - "Amazon S3"
  - "IBM 云对象存储"
  - "Microsoft Azure"
  - "自定义设置"
  - "代理服务器"
  - "studio pro"
---

## 1 导言

您可以使用自定义服务器设置来配置 Mendix Runtime 超出Studio Pro提供的标准可能性。

{{% alert type="warning" %}}
只有当您确切知道正在做什么时，才使用此功能。 不正确的值可以阻止Mendix 运行时间。
{{% /报警 %}}

每个自定义设置包含一个名称和一个值。 例如，为了启用持续会话，您添加了一个名为 `持久会话` 和值 `true` 的自定义设置。 欲了解更详细的设置和示例值，请参阅 [完整文档-m2ee.yaml](https://github.com/mendix/m2ee-tools/blob/master/examples/full-documented-m2ee.yaml)。

如果您正在Mendix Cloud上运行您的应用， 您可以通过 **环境** > **环境详细信息** > **运行时间** > **自定义运行时间设置** 访问这些设置。 欲了解更多信息，请参阅 *环境详细信息的 [运行时间标签](/developerportal/deploy/environments-details#runtime-tab) 部分。*。

如果您正在SAP 云上运行，您可以添加自定义设置为 `MXRUNTIME_` 的用户提供变量。 如果设置包含一个点 `。` 您可以在变量中使用下划线 `_` [引用](https://github.com/mendix/cf-mendix-buildpack#configuring-custom-runtime-settings)

## 2 个常规设置

以下自定义设置可以配置：

| 名称                                                | 描述                                                                                                                                                                                                                                                                                                                                                                                                                             | 默认值                                                                           |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------- |
| **TempPath**                                      | 临时文件的位置。                                                                                                                                                                                                                                                                                                                                                                                                                       | [部署文件夹]\data\tmp                                                            |
| **上传文件路径**                                        | 上传文件的位置。 有效的路径可以是： `\\FileServer\CustomerPortalFiles`。                                                                                                                                                                                                                                                                                                                                                                      | [部署文件夹]\dat\files                                                           |
| **应用程序RootUrl**                                   | 可以在 Java 操作中使用来获取应用程序的公共位置。 当HOST 标头不可用时，例如当从预定事件发送电子邮件时包含应用程序的 URL时，非常有用。                                                                                                                                                                                                                                                                                                                                                     | 在 Mendix Cloud, https://\[domain\].mendixcloud.com                          |
| **调度事件执行**                                        | 指定应该执行哪些预定事件。 选项是 `所有`, `NOE`, 或 `SPECIFIED`。 在 `SPECIFIED`的情况下，使用 `MyScheduledEvents` 下面描述的配置选项列出计划的事件。                                                                                                                                                                                                                                                                                                                       | 无                                                                             |
| **MyScheduled事件**                                 | 具有事件名称的逗号分隔的字符串。 请不要忘记模块名称 (例如，名称可以是 `CRM.UpdateCustomerStatistics`)。                                                                                                                                                                                                                                                                                                                                                          |                                                                               |
| **PersistentSessions**                            | 定义会话是否在数据库中持续存在。 会话持续时，将对登录用户进行统计。 当运行时服务器重启时，会话仍然存在，用户不必重新登录。 在集群环境中，您必须有持续的会话。 唯一的例外是在房舍内安装了固定会话。 值可能是真或假的。                                                                                                                                                                                                                                                                                                                  | true                                                                          |
| **TrackWebServiceUserLastLogin**                  | 定义是否更新网页服务用户在每次登录上的 `最后登录` 个字段。 发生这种情况时，数据库更新查询必须发送，这可能会对重负载系统产生性能。 当设置为 false时，无需进行数据库交互。                                                                                                                                                                                                                                                                                                                                     | true                                                                          |
| **JavaScript StorePassword**                      | 默认 Java 密钥店的密码。                                                                                                                                                                                                                                                                                                                                                                                                                | 更改                                                                            |
| <a name="ca-certificates"></a>**证书**                   | CA证书路径的逗号分隔列表。                                                                                                                                                                                                                                                                                                                                                                                                                 |                                                                               |
| **客户端证书**                                         | 以逗号分隔的客户端证书路径列表。 示例： `D:\App\Mx1.pfx, D:\App\Mx2.pfx, D:\App\Mx3.pfx, D:\App\Mx4.pfx`                                                                                                                                                                                                                                                                                                                                  |                                                                               |
| **ClientCertificatePasswords**                    | 客户端证书用逗号分隔的密码列表 (应该匹配 **客户端证书** 订单)。 例如： `pwd1, pwd2, pwd3, pwd4`                                                                                                                                                                                                                                                                                                                                                              |                                                                               |
| **ClientCertificateUsages**                       | 仅当您有多个客户端证书并且您想要为特定服务器配置特定证书时才使用它。<br/> 此设置定义了哪些服务必须使用哪些客户端证书。 此设置的值必须是逗号分隔的键/值项列表。 必须指定一个密钥/值项为 `"identier": "paths to certification"`。<br/>对于网页服务，使用导入的网页服务名称作为标识符。<br/>对于REST 服务，使用远程服务器的主机名作为标识符。<br/>请注意路径中的任何反斜线必须加倍. 整个值必须由括号加以封装(`{ }`)。 例如： ![](attachments/Custom+Settings/code_snippet.png)                                                                                                 |                                                                               |
| **NoClientCertificateUsages**                     | 以逗号分隔的主机名或导入的网络服务名称列表，这些名称不应使用客户端证书进行联系。                                                                                                                                                                                                                                                                                                                                                                                       |                                                                               |
| **com.mendix.core.SameSiteCookies**               | [SameSite](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie/SameSite) 属性可以包含在嵌入的 HTTP 服务器返回的所有 cookie 中。 可能的值是 `"Stric"`, `"Lax"`, 和 `"无"`。 目前， `"无"` 是默认值，但在下一个主要的 Mendix 版本中，这将更改为 `"Strict"`。 设置为 `"无"` 通常只有当应用程序嵌入另一个应用程序的 iframe 中具有不同域名时才需要。 当设置为 `"无"` 时，较新的浏览器可能需要连接安全(HTTPS)。 如果连接是纯HTTP，则此设置必须更改为 `"严格"` (推荐) 或 `"Lax"`。 此设置可在 Studio Pro [8.11.0](/releasenotes/studio-pro/8.11#8110) 和以上版本中使用。 |                                                                               |
| **会话超时**                                          | 定义会话在多长时间后无效(毫秒)。 超时后，会话可适用于除名。 直到分组管理员下次评估活动的会话时，会话才会被销毁。                                                                                                                                                                                                                                                                                                                                                                     | 600000                                                                        |
| **http.client.MaxConnectionsPerRoute**            | The [maximum number of connections for a route](https://hc.apache.org/httpcomponents-client-ga/httpclient/apidocs/org/apache/http/impl/client/HttpClientBuilder.html#setMaxConnPerRoute(int)) for call REST service and call web service activities.                                                                                                                                                                           | 2                                                                             |
| **http.client.MaxConnectionsTotal**               | The [maximum number of connections allowed across all routes](https://hc.apache.org/httpcomponents-client-ga/httpclient/apidocs/org/apache/http/impl/client/HttpClientBuilder.html#setMaxConnTotal(int)) for the call REST service and call web service activities.                                                                                                                                                            | 20                                                                            |
| **http.client.CleupAfterSeconds**                 | 呼叫REST 服务和呼叫网络服务活动 新主机的第一个请求将创建一个 HTTP 客户端来处理随后的请求。 当主机在指定时间内没有新请求时，HTTP客户端将被清除。 值 `0` 意味着不需要清理。                                                                                                                                                                                                                                                                                                                               | `12 * 60 * 60` (12小时) (Studio Pro 8.18.0 及以下) 或 `355` (Studio Pro 8.18.1 及以上) |
| **集群管理动作间隔**                                      | 用于执行所有集群管理器操作的间隔(毫秒)。 这些动作包括解除对用户的屏蔽和移除无效会话。 如果没有指定任何内容，间隔为 `会期超时`。                                                                                                                                                                                                                                                                                                                                                            | 300000                                                                        |
| **com.mendix.core.storageService**                | 定义将使用哪个存储服务模块。 存储服务模块负责存储与 `System.FileDocument` 对象相关的实际文件，例如上传的文件。 可能的值是 `com.mendix.storage.localfilesystym`, `com.mendix.storage.s3`, `com.mendix.storage.azure`, 和 `com.mendix.storage.power`。                                                                                                                                                                                                                             | com.mendix.storage.localfilesystem                                            |
| **com.mendix.storage.PerformerDeleteFromStorage** | 定义是否删除Mendix 文件会导致存储服务中的实际删除。 在存储服务中不执行实际删除的原因可能是当它也被用作备份服务时。                                                                                                                                                                                                                                                                                                                                                                  | true                                                                          |
| **com.mendix.core.SessionIdCookie名称**             | 定义表示会话ID的 cookie 值名称。 当在会议cookie具有特定名称的容器中运行时，可以进行更改。                                                                                                                                                                                                                                                                                                                                                                          | XASSESSIONID                                                                  |
| **启用 ApacheCommonsLogging**                       | Mendix 运行时使用的一些库使用 [Apache Commons](http://commons.apache.org/) 来记录。 默认情况下，这些日志消息被抑制。 设定此值为 `true` 以接收来自Mendix 日志中这些库的日志消息。 此设置在 Mendix 8.18.6 及以后可用。                                                                                                                                                                                                                                                                          | false                                                                         |

## 3 个日志文件设置

下面的设置影响日志文件的行为。 这些设置只能用于房地。 在云端，这些设置不改变任何行为。

| 名称                  | 描述                                                   | 默认值          |
| ------------------- | ---------------------------------------------------- | ------------ |
| **日志文件名称**          | 日志文件的名称。 日志文件 (实际日志文件加上备份文件) 将被放到设置日志路径指定的文件夹中。      | 日志           |
| **MaxLogFile大小**    | 每个日志文件的最大尺寸。 当日志文件达到这个最大大小时，日志文件将被备份，并且将使用一个新的空日志文件。 | 2097152(2MB) |
| **MaxLogFileCount** | 保存日志文件的最大数量(实际文件加备份文件)。 当达到最大计数时，最旧的备份文件将被删除。        | 10           |

## 4个数据库设置

### 4.1 共同设置

| 名称                     | 描述                                                                                                                                                                                                      | 默认值   |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- |
| **ClientQueryTimeout** | 定义为将数据加载到客户端小部件所执行的大多数数据库查询的超时秒数，如数据网格。 在此处指定的持续时间后，查询将被取消，并且会抛出异常。                                                                                                                                     |       |
| **数据库类型**              | 定义使用 Mendix 数据库的数据库引擎。 有效值为： `DB2`, `HSQLDB`, `MYSQL`, `ORACLE,` `POSTGRESQL`, `SAPHANA`, 和 `SQLSERVER`.                                                                                                |       |
| **数据库用户名**             | 验证数据库所需的名称。                                                                                                                                                                                             |       |
| **数据库密码**              | 上面提供 `数据库用户名` 的密码。                                                                                                                                                                                      |       |
| **数据库主机**              | 主机名和数据库的 TCP 端口号。 使用冒号 (`:`) 作为主机名和端口号之间的分隔符。 可能的值是： `db.url.org`, `db.url.org：第1521`, `10.0.0.0.5`和`10.0.0.5：1433`\。 可以使用一个纯IPv6地址，将其放在括号内(例如， `[:1]:5432`)。<br/>如果您提供 `DatabaseJdbcUrl` 这将被覆盖。 |       |
| **数据库名称**              | Mendix 应用程序使用的数据库或架构名称 <br/>如果您提供 **DatabaseJdbcUrl** 这将被覆盖。                                                                                                                                      |       |
| **DatabaseJdbcUrl**    | 定义数据库连接所使用的 JDBC URL (它覆盖其他数据库连接设置)。                                                                                                                                                                    |       |
| **DatabaseUseSl**      | 关于 PostgreSQL 数据库，定义连接是否将使用 SSL 进行，而无需证书验证。 如果您需要证书验证，请使用 **DatabaseJdbcUrl** 代替。                                                                                                                       | false |
| **LogMinDuration查询**   | 定义数据库查询是否通过 `ConnectionBus_Queries` 日志节点登录，如果它们在这里指定的毫秒数后完成。 默认情况下，只有相关的 SQL 查询将被记录。 将 `ConnectionBus_Queries` log节点的日志级别设置为 `TRACE` 以显示更多有关该页面或微流的信息，从而导致此查询。                                          |       |
| **OracleService名称**    | 定义当您与 Oracle DBMS 有连接时的 `SERVICE_NAME`。                                                                                                                                                                 |       |
| **DataStorage.启用诊断程序** | 此设置可以用来生成一个独特约束违反报告。                                                                                                                                                                                    | false |
| **网络超时**               | 此设置用于 PostgreSQL 和 DB2。 它影响在 Mendix 对象保留新的 id 时使用的超时机制。 如果设置为 true，则使用套接字级别请求超时。 在这种情况下，请求超时是在操作系统内处理的。 如果设置为 false，超时由Mendix 运行时间处理。 对于其他数据库，超时总是由 Mendix 运行时间处理。                                      | true  |
| **JdbcLogin超时**        | 此设置定义了数据库连接建立时间，以毫秒计。                                                                                                                                                                                   | 5000  |

### 4.2 连接库

下面的设置用于定义数据库连接池行为。 Mendix Runtime 使用一个可重复使用的数据库连接。 例如，您可以定义可以使用多少连接。 正在使用 [Apache Commons Object-hont API 实现连接池](http://commons.apache.org/pool/)。

这些设置已配置为每个运行时实例的 **。 如果您有 [缩放了您的应用程序](/developerportal/deploy/scale-environment)， 数据库侧的连接数将乘以运行场数。 例如，如果您将 `ConnectionPoolingMaxIdle` 设置为 `50` 并将您的应用程序缩放到 2 个运行时间。 每个运行时实例最多将创建50个连接，但在数据库侧，这将导致最多100个连接。

| 名称                                                 | 值                                                                                                                                                               | 默认值          |
| -------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| **连接 PoolingMaxWait**                              | 当达到“活动”对象的最大数目时，池就会被“耗尽”。 连接总线使用的“当用尽时”操作是 `WHEN_EXHAUSTED_BLOCK`。 设置 `借款对象()` 方法应该阻止的最大时间(毫秒)，然后在池耗尽时丢弃异常。 当小于或等于 `0`时， `借款对象()` 方法可能会无限期阻挡。 (!)               | 10000        |
| **ConnectionPoolingMaxActive**                     | 设置池中活动实例总数的上限。                                                                                                                                                  | 50           |
| **连接 PoolingMaxIdle**                              | 设置池中的“空闲”实例数量上限。                                                                                                                                                | 50           |
| **连接PoolingMinIdle**                               | 设置拆解器线程(如果活动的话)生成新对象之前允许在池中使用的对象的最小数量。 请注意， `numActive` + `numIdle` >= `maxActive` 时没有创建对象。  如果闲置对象驱逐器被禁用，此设置不会产生任何效果(如： `timeBetweenEvictionRunsMillis` <= 0). | 0            |
| **ConnectionPoolingTimeBetweenEvictionRunsMillis** | 设置空闲对象拆解线程运行之间睡眠的毫秒数。 当非正面时，将不会运行闲置对象拆除线程。                                                                                                                      | 300 000(5分钟) |
| **ConnectionPoolingSoftMinEvicableIdleTimeMillis** | 设定一个物体在池内闲置的最低时间，然后才有资格被空闲物体搬迁者(如果有的话)， 额外条件是至少 `minIdle` 对象仍然留在池中。 如果非正数，不会仅仅因为空闲时间而将任何物品从池中逐出。                                                                | 300 000(5分钟) |
| **连接池NumTestsPerEvictionRun**                      | 设置每次运行空闲对象驱逐线程时要检查的对象的最大数目(如果有)。 当提供负值时， `上限(getNumIdle())/abs(getNumTestsPerEvictionRun())` 测试将会运行。 这意味着当值为 -n时，空闲天体的大约n分之一将在运行时进行测试。                          | -3           |

### 4.3 迁移设置

下面的设置用于定义源数据库，所有数据都应复制到主数据库。 您只需在下方指定一次设置。 主数据库应该存在并且应该是空的。 在应用程序启动期间，如果指定了下面的设置，数据将会被复制。 此后移除设置，因为它们不再需要。

在数据复制过程开始之前，源数据库也将与模型一致，如主数据库。 这是必要的，以便能够在没有问题的情况下复制所有数据。

| 名称                                       | 值                                                                                                                                                       | 默认值            |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| **SourceBuiltInDatabasePath**            | 定义内置源数据库的文件位置。 只有当内置数据库的非默认位置必须用于复制数据时，此设置才是必需的。                                                                                                        | [部署文件夹]/数据/数据库 |
| **来源数据库主机**                              | 主机名和源数据库的 TCP 端口号。 使用冒号作为主机名和端口号之间的分隔符。 可能的值为： `db.url.org`, `db.url.org：第1521`, `10.0.0.0.5`, 或 `10.0.0.5：1433`。 可以使用纯IPv6地址，将其放在括号内(例如， `[:1]:5432`)。 |                |
| **SourceDabaseJdbcUrl**                  | 定义源数据库连接所使用的 JDBC URL (它覆盖其他源数据库连接设置)。 PostgreSQL 数据库不支持此功能。                                                                                            |                |
| **源数据库名称**                               | 源数据库的名称。                                                                                                                                                |                |
| **源数据库密码**                               | 连接到源数据库的密码。                                                                                                                                             |                |
| **SourceDatabaseType**                   | 源数据库的类型。 可能的值： `HSQLDB`, `MYSQL`, `ORACLE`, `POSTGRESQL`, 或 `SQLSERVER`.                                                                                |                |
| **SourceDatabaseUseIntegrated Security** | 这个设置定义了是否应该用于 SQL Server 的集成安全性。 如果选中，用户名和密码将不会被使用。                                                                                                     | false          |
| **SourceDatabaseUseSsl**                 | 关于 PostgreSQL 数据库，定义连接到源数据库是否使用 SSL。                                                                                                                    | false          |
| **SourceDatabaseUserName**               | 连接到源数据库的用户名。                                                                                                                                            |                |
| **SourceOracleServiceName**              | 定义当您与 Oracle DBMS 连接时的 `SERVICE_NAME` 作为源。                                                                                                              |                |

## 5 S3 存储服务设置 {#5-amazon-s3-storage-service-settings}

下面描述的设置影响Amazon S3存储服务模块的行为。 此模块可以同时用于Amazon S3存储和 IBM 云对象存储。 强烈阻止手动在 Mendix 云中使用这些设置，因为存储在外部系统中的文件将不会包含在备份创建和恢复中。

| 名称                                                    | 描述                                                                                                                                                                                                                                                                                                                   | 默认值                                                                                                                                                                                                                |
| ----------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **com.mendix.storage.s3.AccessKeyId**                 | 使用 S3 服务进行身份验证。                                                                                                                                                                                                                                                                                                      |                                                                                                                                                                                                                    |
| **com.mendix.storage.s3.SecretAccessKey**             | 使用 S3 服务进行身份验证。                                                                                                                                                                                                                                                                                                      |                                                                                                                                                                                                                    |
| **com.mendix.storage.s3.Bucket名称**                    | 存储在 S3 上的文件的 bucket 名称。                                                                                                                                                                                                                                                                                              |                                                                                                                                                                                                                    |
| **com.mendix.storage.s3.ResourceNameSuffix**          | 存储对象的密钥后缀。 当S3 buckets被分成不同的部分给不同的用户，且不同的凭据（例如，S3 buckets）时，可以使用此功能。 将对象存储为 `"[key]。 客户1"` for customer1 and as `"[key].customer2"` for customer2)。                                                                                                                                                                  |                                                                                                                                                                                                                    |
| **com.mendix.storage.s3.PerformerDeleteFromStorage**  | 废弃。 使用 **com.mendix.storage.PerformeDeleteFromStorage**。<br/>定义是否删除Mendix 文件会导致存储服务中的实际删除。 在存储服务中不执行实际删除的原因可能是当它也被用作备份服务时。                                                                                                                                                                                     | true                                                                                                                                                                                                               |
| <a name="s3-region"></a>**com.mendix.storage.s3.区域** | 设置S3桶所在的区域。 这将用于确定服务端点，除非在 **com.mendix.storage.s3.EndPoint** 中覆盖。 此设置也将被用于签署区域的请求。                                                                                                                                                                                                                                  |                                                                                                                                                                                                                    |
| **com.mendix.storage.s3.EndPoint**                    | 覆盖默认端点。 当存储在非AWS位置时需要此设置 (例如，IBM 云对象存储)。 端点(例如， `s3.example.com`) 或完整的 URL (包括协议) 都被支持(例如， `https://s3.example.com`)。 请注意，当设置自定义端点时，路径样式访问将被启用。 欲了解更多信息，见 [Class S3ClientOptions](http://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/services/s3/S3ClientOptions.html#withPathStyleAccess(boolean))。 |                                                                                                                                                                                                                    |
| **com.mendix.storage.s3.UseV2Auth**                   | 让认证策略使用 `签名版本 2` 而不是默认 `签名版本 4`。 当端点不支持 `签名版本 4` 时，将此设置为 `true`。                                                                                                                                                                                                                                                     | false                                                                                                                                                                                                              |
| **com.mendix.storage.s3.加密密钥**                        | 可用来在S3中加密和解密数据的密钥列表。 解密数据的正确密钥将根据加密的密钥自动选择。 每个加密密钥由密钥ID、加密算法和实际密钥(Base64编码)组成。 示例： ![](attachments/Custom+Settings/code_snippet_2.png)                                                                                                                                                                               |                                                                                                                                                                                                                    |
| **com.mendix.storage.s3.ForceGlobalBucketAccess已启用**  | 值 `true` 允许服务器将请求路由到不同于这些设置中指定的区域(`false` 不允许它)。 此设置可在 Studio Pro [8.12.0](/releasenotes/studio-pro/8.12#8120) 和以上版本中使用。                                                                                                                                                                                             | true                                                                                                                                                                                                               |
| **com.mendix.storage.s3.MaxConnections**              | 覆盖 S3 服务中的默认最大连接限制。 对于大多数应用程序来说，默认值已足够。 所以我们不建议将此设置为自定义值，除非绝对需要更大的最大连接限制。                                                                                                                                                                                                                                            | [DEFAULT_MAX_CONNECTIs](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/ClientConfiguration.html#DEFAULT_MAX_CONNECTIONS) field of the ClientConfiguration interface in the AWS SDK for Java |
| **com.mendix.storage.s3.clientExecutionTimeout**      | 设置允许调用到存储服务完成的时间(毫秒)。 值 `0` 意味着没有超时。 欲了解更多信息，请见 [AWS Java SDK](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/ClientConfiguration.html#setClientExecutionTimeout-int-)。                                                                                                                         | 0 (无超时)                                                                                                                                                                                                            |
| **com.mendix.storage.s3.连接超时**                        | 设置在放弃和超时之前等待连接的时间 (毫秒)。 值 `0` 意味着无限，不推荐。 欲了解更多信息，请见 [AWS Java SDK](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/ClientConfiguration.html#setConnectionTimeout-int-)。                                                                                                                          | 10 000 (10秒)                                                                                                                                                                                                       |
| **com.mendix.storage.s3.SocketTimeout**               | 设置等待数据传输的时间 (毫秒) 连接结束前打开连接。  值 `0` 意味着无限，不推荐。 欲了解更多信息，请见 [AWS Java SDK](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/ClientConfiguration.html#setSocketTimeout-int-)。                                                                                                                         | 50.000 (50秒)                                                                                                                                                                                                       |
| **com.mendix.storage.s3.RequestTimeout**              | 设置等待完成请求的时间长度(毫秒) 才能放弃和超时。 值 `0` 意味着没有超时。 欲了解更多信息，请见 [AWS Java SDK](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/ClientConfiguration.html#setRequestTimeout-int-)。                                                                                                                            | 0 (无超时)                                                                                                                                                                                                            |
| **com.mendix.storage.s3.UseCAC证书**                    | 将此值设置为 `true` 来使用已配置的 [证书](#ca-certificates) 连接到 S3 服务。                                                                                                                                                                                                                                                              | false                                                                                                                                                                                                              |

## 6 Microsoft Azure SQL

这些设置可以修改为Mendix 应用程序使用Microsoft Azure SQL数据库。

首先，您需要创建 Azure SQL 数据库(关于如何做到这一点的信息，请参阅 [SQL 数据库教程](https://azure.microsoft.com/en-us/documentation/articles/sql-database-get-started/))。 请确保您的 Azure 防火墙设置允许您的 Mendix 应用程序访问 Azure SQL 数据库(默认情况下) Azure防火墙不允许外部连接)。

| 名称         | 描述                                               | 默认值 |
| ---------- | ------------------------------------------------ | --- |
| **数据库类型**  | `SQLSERVER`                                      |     |
| **数据库主机**  | `"your-database-host.database.windows.net:1433"` |     |
| **数据库名称**  | `您的数据库名称`                                        |     |
| **数据库用户名** | `您的用户名`                                          |     |
| **数据库密码**  | `您的密码`                                           |     |

## 7 微软Azure Blob 存储设置

这些设置可以使用Microsoft Azure blob 存储服务存储文件。 服务器端加密可以通过 Azure Portal 进行配置(详情请查看 [Azure 存储加密，其余数据](https://azure.microsoft.com/en-us/documentation/articles/storage-service-encryption/))。

| 名称                                                      | 描述                                                                                                                                                            | 默认值    |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ |
| **com.mendix.core.storageService**                      | 必须设置为 `com.mendix.storage.azure` 来选择 Azure 作为存储服务。                                                                                                            |        |
| **com.mendix.storage.azure.Account名称**                  | 通过 Azure 博客存储服务进行身份验证的帐户名。                                                                                                                                    |        |
| **com.mendix.storage.azure.AccountKey**                 | 通过 Azure 博客存储服务进行身份验证的账户密钥。                                                                                                                                   |        |
| **com.mendix.storage.azure.共享访问签名**                     | 提供对存储帐户中资源的授权访问。 欲了解更多信息，见 [共享访问签名在 docs.microsoft.com](https://docs.microsoft.com/en-us/azure/storage/common/storage-dotnet-shared-access-signature-part-1)。 |        |
| **com.mendix.storage.azure.Blob端点**                     | 设置博客端点。 使用 `共享访问签名` 进行身份验证时需要此设置。                                                                                                                             |        |
| **com.mendix.storage.azure.Container**                  | 包含蓝色的容器名称。                                                                                                                                                    |        |
| **com.mendix.storage.azure.CreateContainerIfNotExists** | 指示是否检查容器是否存在，如果它不存在，则创建它。 此设置被引入Studio Pro [8.7.0](/releasenotes/studio-pro/8.7#870) 中。                                                                       | `true` |
| **com.mendix.storage.azure.ParallelismFactor**          | 并联多部分文件上传/下载的最大数量。 我们建议不要更改此设置，除非您在大型文件中经历缓慢的文件传输。 选择更大的值会导致更高的内存使用率。                                                                                         | 5      |
| **com.mendix.storage.azure.UseHttps**                   | 启用或禁用使用 HTTPS 的安全连接。 可以是 `true` 或 `false`。                                                                                                                    | `true` |
| **com.mendix.storage.azure.TimeoutIntervalInMs**        | 设置允许调用到存储服务完成的时间(毫秒)。 欲了解更多信息，请参阅 [Azure 库](https://azure.github.io/azure-sdk-for-java/storage.html)。                                                         | 没有超时   |
| **com.mendix.storage.azure.MaximumExecutionTimeInM**    | 设置在提出此请求时使用的最大执行时间(毫秒)。 欲了解更多信息，请参阅 [Azure 库](https://azure.github.io/azure-sdk-for-java/storage.html)。                                                       | 没有最大时间 |

{{% alert type="warning" %}}
Azure blob 存储的默认连接协议是 HTTPS ，以鼓励默认安全连接。 这是一个高度推荐的最佳做法(详细信息，请参阅 [配置 Azure 存储连接字符串](https://docs.microsoft.com/en-us/azure/storage/common/storage-configure-connection-string))。 这应该是透明的，除非您使用自定义域名(详情参见 [需要安全传输](https://docs.microsoft.com/en-us/azure/storage/common/storage-require-secure-transfer))。 在这种情况下，您应该使用上面的 `UseHttps` 设置来恢复到之前的默认行为并禁用 HTTPS。
{{% /报警 %}}

## 8 IBM Cloud (Bluemix) 对象存储设置

这些设置可以用于使用 IBM 云对象存储服务存储文件。

Mendix 支持未扩展的 OpenStack 身份验证(键盘) v3。 与凭据相关的设置必须填写相应的值，这些值可以在您的对象存储服务的服务凭据部分找到。

{{% alert type="info" %}}
与其他存储服务不同，IBM Cloud不提供服务器端加密。
{{% /报警 %}}

| 名称                                                  | 描述                                               | 默认值   |
| --------------------------------------------------- | ------------------------------------------------ | ----- |
| **com.mendix.core.storageService**                  | 必须设置为 `com.mendix.storage.rester` 来选择IBM 云作为存储服务 |       |
| **com.mendix.storage.promot.Container**             | 对象存储服务的容器名称                                      |       |
| **com.mendix.storage.propect.Container.AutoCreate** | 如果启用(值 `true`)，如果容器不存在，它将自动创建。                   | false |
| **com.mendix.storage.promot.certificals.DomainId**  | 域名唯一标识符                                          |       |
| **com.mendix.storage.propect.validals.Authurl**     | 身份验证URL                                          |       |
| **com.mendix.storage.propect.validals.用户名**         | 用户名                                              |       |
| **com.mendix.storage.propest.validals.Password**    | 密码                                               |       |
| **com.mendix.storage.propect.compensations.region** | 地区                                               |       |

## 9 Web 客户端设置

下面的设置影响Mendix 网页客户端的行为。

| 名称                                                 | 描述                                                                                                                          | 默认值                                        |
| -------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| **启用 KeepAlive**                                   | 定义网络客户端是否发送每一个 SessionTimeout/2 毫秒的存活请求，以防止会话超时。 浏览器中的每个单击都是KeepAlive。 禁用此属性将导致用户在10分钟闲置后自动退出，即使浏览器仍然开启。                    | true                                       |
| **PhoneUserAgentRegEx**                            | 定义用于确定用户是否从手机访问Mendix 应用程序的正则表达式。 正则表达式与客户端的 web 浏览器发送的用户代理头匹配。                                                             | Android, Mobile (iPhone, iPod, BlackBerry) |
| **TabletUserAgentRegEx**                           | 定义用于确定用户是否从平板电脑访问Mendix 应用程序的正则表达式。 正则表达式与客户端的 web 浏览器发送的用户代理头匹配。                                                           | Android, iPad                              |
| **com.mendix.webui.HybridAppLoginTimeOut**         | 确定您的令牌在使用完整凭据重新认证之前仍然有效的分钟数。 此设置默认为 `-1`, 等于没有超时。                                                                           | -1                                         |
| **com.mendix.webui.反馈Size警告阈值**                    | 当反馈大小超过阈值时，将记录警告。 反馈将从服务器发送到客户端来指示(例如，刷新对象或打开页面)。 它们被序列化为服务器响应中的“指示”。 如果有太多的指示，这可能会影响到业绩，因为它们都必须按顺序排列给客户。 为此原因，当超过阈值时会记录警告。 | 5000                                       |
| **com.mendix.webui.StateSize警告阈值**                 | 当状态大小超过阈值时会记录警告。 状态包括更改对象和未输入数据库的对象(尚未输入)。 如果情况太多，这将会产生业绩影响，因为整个状态必须序列化给客户。 为此原因，当超过阈值时会记录警告。                               | 100                                        |
| **com.mendix.webui.Commonwealth ObjectsThreshold** | 阈值控制执行微流程后有多少数据被送回客户端。 默认情况下，当全部对象被更改或提交时，我们会将其退出。 当达到此阈值时 只有对象 GUID 会被送回，所以客户端会知道更改情况，而通过网络发送的数据数量会减少。 然后客户端将在必要时稍后检索对象。   | 100                                        |

## 10 代理设置

下面的设置允许您使用代理服务器

| 名称                 | 描述           | 默认值 |
| ------------------ | ------------ | --- |
| **http.proxyHost** | 定义代理服务器的主机名。 |     |
| **http.proxyPort** | 定义代理服务器的端口号。 |     |
