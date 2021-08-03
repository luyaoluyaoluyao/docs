---
title: "运行时自定义"
category: "Mendix 运行时间"
description: "描述服务器自定义设置、日志文件、数据库、Amazon S3存储服务、Microsoft Azure、IBM Bluemix 对象存储、网页客户端和代理服务器。"
tags:
  - "运行时间"
  - "自定义"
  - "设置"
  - "配置"
  - "IBM 云"
  - "Amazon S3"
  - "Microsoft Azure"
  - "自定义设置"
  - "代理服务器"
---

## 1个自定义运行时设置

您可以使用自定义服务器设置来配置超越Modeler提供的标准可能性的运行时间。

{{% alert type="warning" %}}

只有当您确切知道正在做什么时，才使用此功能。 错误的值可以阻止运行时间。

{{% /报警 %}}

每个自定义设置包含一个名称和一个值。 例如，为了启用持续会话，您添加了一个名为 `持久会话` 和值 `true` 的自定义设置。 更详细的设置和示例值列表请参阅 [完整的m2ee.yaml](https://github.com/mendix/m2ee-tools/blob/master/examples/full-documented-m2ee.yaml)。

If you are running your app on the Mendix Cloud, you can access these settings on the **Runtime Tab** of the *Environment Details*: accessible from the *Environments* page of the Developer Portal. 欲了解更多信息，请查看 [环境详细信息 - 运行时标签](/developerportal/deploy/environments-details#runtime-tab)。

## 2 个常规设置

以下自定义设置可以配置：

| 名称                                            | 描述                                                                                                                                                                                                                                                                                                                                                                        | 默认值                                                  |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| TempPath                                      | 临时文件的位置。                                                                                                                                                                                                                                                                                                                                                                  | [部署文件夹]\data\tmp                                   |
| 上传文件路径                                        | 上传文件的位置。 有效路径可以是：\\FileServer\CustomerPortal文件.                                                                                                                                                                                                                                                                                                                        | [部署文件夹]\dat\files                                  |
| 应用程序RootUrl                                   | 可以在 Java 操作中使用来获取应用程序的公共位置。 当HOST 标头不可用时，例如当从预定事件发送电子邮件时包含应用程序的 URL时，非常有用。                                                                                                                                                                                                                                                                                                | 在 Mendix Cloud, https://\[domain\].mendixcloud.com |
| 调度事件执行                                        | 指定应该执行哪些预定事件。 选择是“完全”、“无”或“选择”。 若要使用 'MyScheduledEvents' 配置选项列举计划中的事件。                                                                                                                                                                                                                                                                                                    | 无                                                    |
| MyScheduled事件                                 | 具有事件名称的逗号分隔的字符串。 请不要忘记模块名称。 名称可以是 CRM更新客户统计。                                                                                                                                                                                                                                                                                                                              |                                                      |
| PersistentSessions                            | 定义会话是否在数据库中持续存在。 会话持续时，将对登录用户进行统计。 当运行时服务器重启时，会话仍然存在，用户不必重新登录。 然而，使会话持续下去可能会对应用程序的速度产生消极影响：值可能是真的或是假的。                                                                                                                                                                                                                                                                    | true                                                 |
| TrackWebServiceUserLastLogin                  | 定义是否更新网络服务用户在每个登录上的“LastLogin”字段。 发生这种情况时，数据库更新查询必须发送，这可能会对重负载系统产生性能。 当设置为 false时，无需进行数据库交互。                                                                                                                                                                                                                                                                              | true                                                 |
| JavaScript StorePassword                      | 默认 Java 密钥店的密码。                                                                                                                                                                                                                                                                                                                                                           | 更改                                                   |
| 证书证书                                          | 授权证书路径的逗号分隔列表。                                                                                                                                                                                                                                                                                                                                                            |                                                      |
| 客户端证书                                         | 用逗号分隔的客户端证书路径列表。 示例： `D:\App\Mx1.pfx, D:\App\Mx2.pfx, D:\App\Mx3.pfx, D:\App\Mx4.pfx`                                                                                                                                                                                                                                                                             |                                                      |
| ClientCertificatePasswords                    | 用逗号分隔的客户端证书密码列表 (应匹配“客户端证书”顺序)。 例如： `pwd1, pwd2, pwd3, pwd4`                                                                                                                                                                                                                                                                                                              |                                                      |
| WebServiceClient证书                            | 自版本7.2. 以来已废弃。<br/>定义哪些网络服务必须使用哪些客户端证书。 此设置的值必须是逗号分隔的键/值项列表。 必须指定一个密钥/值项为[`"导入的网络服务名称": "路径到证书"`] 而不包含括号。 请注意路径中的任何反斜线必须加倍. 整个数值必须用括号围住。                                                                                                                                                                                                                            |                                                      |
| ClientCertificateUsages                       | 引入版本7.2。<br/>只能在<br/>1时使用。 您有多个客户端证书，<br/>2。 您想要为特定服务器配置特定证书。<br/> 此设置定义了哪些服务必须使用客户端证书。 此设置的值必须是逗号分隔的键/值项列表。 必须指定一个密钥/值项为 `"identier": "paths to certification"`。<br/>对于网页服务，使用导入的网页服务名称作为标识符。<br/>对于REST 服务，使用远程服务器的主机名作为标识符。<br/>请注意路径中的任何反斜线必须加倍. 整个值必须由括号加以封装(`{ }`)。 例如： ![](attachments/Custom+Settings/code_snippet.png) |                                                      |
| 会话超时                                          | 定义会话在多长时间后无效(毫秒)。 超时后，会话可适用于除名。 直到下次集群管理员评估活动会话时，会话才会被摧毁。                                                                                                                                                                                                                                                                                                                 | 600000                                               |
| http.client.MaxConnectionsPerRoute            | Introduced in version 7.19.<br/> The [maximum number of connections for a route](https://hc.apache.org/httpcomponents-client-ga/httpclient/apidocs/org/apache/http/impl/client/HttpClientBuilder.html#setMaxConnPerRoute(int)) for Call REST and Call Web Service actions.                                                                                          | 2                                                    |
| http.client.MaxConnectionsTotal               | Introduced in version 7.19.<br/> The [maximum number of connections allowed across all routes](https://hc.apache.org/httpcomponents-client-ga/httpclient/apidocs/org/apache/http/impl/client/HttpClientBuilder.html#setMaxConnTotal(int)) for Call REST and Call Web Service actions.                                                                               | 20                                                   |
| http.client.CleupAfterSeconds                 | 引入第7.22版。<br/> 用于通话REST 和调用网络服务操作 对新主机wil 的第一个请求创建一个 HTTP 客户端来处理随后的请求。 当主机在指定时间内没有新请求时，HTTP客户端将被清除。 默认值： 12 * 60 * 60 (12小时)。 值为0表示不清理。                                                                                                                                                                                                                           |                                                      |
| 集群管理动作间隔                                      | 用于执行所有集群管理器操作的间隔(毫秒)。 这些动作包括解除对用户的屏蔽和移除无效会话。 如果没有指定任何内容，间隔是会话超时的一半。                                                                                                                                                                                                                                                                                                       | 300000                                               |
| com.mendix.core.storageService                | 定义将使用哪个存储服务模块。 存储服务模块负责存储与“System.FileDocument”对象相关的实际文件，例如上传的文件。 可能的值是 'com.mendix.storage.localfilesystem', 'com.mendix.storage.s3', 'com.mendix.storage.azure' 和 'com.mendix.storage.propt'。                                                                                                                                                                           | com.mendix.storage.localfilesystem                   |
| com.mendix.storage.PerformerDeleteFromStorage | 引入版本7.19。<br/>定义是否删除Mendix 文件文件会导致存储服务中的实际删除。 在存储服务中不执行实际删除的原因可能是当它也被用作备份服务时。                                                                                                                                                                                                                                                                                       | true                                                 |
| com.mendix.core.SessionIdCookie名称             | 定义表示会话ID的 cookie 值名称。 当在会议cookie具有特定名称的容器中运行时，可以进行更改。                                                                                                                                                                                                                                                                                                                     | XASSESSIONID                                         |

## 3 个日志文件设置

下面的设置影响日志文件的行为。 这些设置只能在内部使用。 在云端，这些设置不改变任何行为。

| 名称              | 描述                                                   | 默认值          |
| --------------- | ---------------------------------------------------- | ------------ |
| 日志文件名称          | 日志文件的名称。 日志文件 (实际日志文件加上备份文件) 将被放到设置日志路径指定的文件夹中。      | 日志           |
| MaxLogFile大小    | 每个日志文件的最大尺寸。 当日志文件达到这个最大大小时，日志文件将被备份，并且将使用一个新的空日志文件。 | 2097152(2MB) |
| MaxLogFileCount | 保存日志文件的最大数量(实际文件加备份文件)。 当达到最大计数时，最旧的备份文件将被删除。        | 10           |

## 4个数据库设置

### 4.1 共同设置

| 名称                    | 描述                                                                                                                                                                                                                                      | 默认值   |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- |
| ClientQueryTimeout    | 定义为将数据加载到客户端小部件所执行的大多数数据库查询的超时秒数，如数据网格。 在此处指定的持续时间后，查询将被取消，并且会抛出异常。                                                                                                                                                                     |       |
| DatabaseJdbcUrl       | 定义数据库连接所使用的 JDBC URL (它覆盖其他数据库连接设置)。 PostgreSQL 数据库不支持此功能。                                                                                                                                                                              |       |
| DatabaseUseSl         | 关于 PostgreSQL 数据库, 定义连接是否将使用 SSL                                                                                                                                                                                                        | false |
| LogMinDuration查询      | 定义数据库查询是否通过 ConnectionBus_Queries 日志节点登录，如果它们在这里指定的毫秒数后完成。 默认情况下，只有相关的 SQL 查询将被记录。 将 ConnectionBus_Queries 日志节点的日志级别设置为 TRACE 以显示更多有关表格或导致此查询的微流程的信息。                                                                                 |       |
| OracleService名称       | 定义当您与 Oracle DBMS 有联系时SERVICE_NAME。                                                                                                                                                                                                     |       |
| ReadCommittedSnapshot | 定义是否必须启用Microsoft SQL Server 的 READ_COMMEND_SNAPSHOT 选项。 欲了解更多信息，请参阅 [交易锁定和行版本指南](https://docs.microsoft.com/en-us/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide?view=sql-server-ver15)。 值可能是真或假的。 | true  |
| DataStorage.启用诊断程序    | 此设置可以用来生成一个独特约束违反报告。                                                                                                                                                                                                                    | false |
| 网络超时                  | 此设置用于 PostgreSQL 和 DB2。 它影响在 Mendix 对象保留新的 id 时使用的超时机制。 如果设置为 true，则使用套接字级别请求超时。 在这种情况下，请求超时是在操作系统内处理的。 如果设置为 false，超时由Mendix 运行时间处理。 对于其他数据库，超时总是由 Mendix 运行时间处理。                                                                      | true  |
| JdbcLogin超时           | 此设置定义了数据库连接建立时间，以毫秒计。                                                                                                                                                                                                                   | 5000  |

### 4.2 连接库

下面的设置用于定义数据库连接池行为。 运行时使用一个可重复使用的数据库连接库。 例如，您可以定义可以使用多少连接。 正在使用 [Apache Commons Object-hont API 实现连接池](http://commons.apache.org/pool/)。

这些设置已配置为每个运行时实例的 **。 如果您有 [缩放了您的应用程序](/developerportal/deploy/scale-environment)， 数据库侧的连接数将乘以运行场数。 例如，如果您将 `ConnectionPoolingMaxIdle` 设置为 `50` 并将您的应用程序缩放到 2 个运行时间。 每个运行时实例最多将创建50个连接，但在数据库侧，这将导致最多100个连接。

| 名称                                             | 值                                                                                                                                                    | 默认值                            |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| 连接 PoolingMaxWait                              | 当达到“活动”对象的最大数目时，池就会被“耗尽”。 连接总线使用的“当耗尽时”动作是 WHEN_EXHAUSTED_BLOCK 设置借款对象() 方法应该阻止的最长时间(毫秒)，然后在池用尽时抛出异常。 当小于或等于 0时，借款对象() 方法可以无限期阻挡。 (!)              | 10000                          |
| ConnectionPoolingMaxActive                     | 设置池中活动实例总数的上限。                                                                                                                                       | 50                             |
| 连接 PoolingMaxIdle                              | 设置池中的“空闲”实例数量上限。                                                                                                                                     | 50 (自Mendix 3.3后20，Mendix 3.3) |
| 连接PoolingMinIdle                               | 设置拆解器线程(如果活动的话)生成新对象之前允许在池中使用的对象的最小数量。 注意，在numActive + numId >= maxActive时没有创建对象。  如果闲置对象驱逐器被禁用，此设置不会产生任何效果(例如在 timeBetweenEvictionRunsMillis <= 0). | 0                              |
| ConnectionPoolingTimeBetweenEvictionRunsMillis | 设置空闲对象拆解线程运行之间睡眠的毫秒数。 当非正面时，将不会运行闲置对象拆除线程。                                                                                                           | 300 000(5分钟)                   |
| ConnectionPoolingSoftMinEvicableIdleTimeMillis | 设定一个物体在池内闲置的最低时间，然后才有资格被空闲物体搬迁者(如果有的话)， 附加条件是至少“小标识”对象仍然留在池中。 如果非正数，不会仅仅因为空闲时间而将任何物品从池中逐出。                                                           | 300 000(5分钟)                   |
| 连接池NumTestsPerEvictionRun                      | 设置每次运行空闲对象驱逐线程时要检查的对象的最大数目(如果有)。 当提供负值时， `上限(getNumIdle())/abs(getNumTestsPerEvictionRun())` 测试将会运行。 这意味着当值为 -n时，空闲天体的大约n分之一将在运行时进行测试。               | -3                             |

### 4.3 迁移设置

下面的设置用于定义源数据库，所有数据都应复制到主数据库。 您只需在下方指定一次设置。 主数据库应该存在并且应该是空的。 在应用程序启动期间，如果指定了下面的设置，数据将会被复制。 此后移除设置，因为它们不再需要。

在数据复制过程开始之前，源数据库也将与模型一致，如主数据库。 这是必要的，以便能够在没有问题的情况下复制所有数据。

| 名称                        | 值                                                                                                                                  | 默认值            |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| SourceBuiltInDatabasePath | 定义内置源数据库的文件位置。 只有当内置数据库的非默认位置必须用于复制数据时，此设置才是必需的。                                                                                   | [部署文件夹]/数据/数据库 |
| 来源数据库主机                   | 主机名和源数据库的 TCP 端口号。 使用冒号作为主机名和端口号之间的分隔符。 可能的值为：db.url.org，db.url.org：1521，10.0.0.5，10.0.0.5：1433\。 可以使用纯IPv6地址，把它放在括号内，如：[:1]:5432 |                |
| SourceDabaseJdbcUrl       | 定义源数据库连接所使用的 JDBC URL (它覆盖其他源数据库连接设置)。 PostgreSQL 数据库不支持此功能。                                                                       |                |
| 源数据库名称                    | 源数据库的名称。                                                                                                                           |                |
| 源数据库密码                    | 连接到源数据库的密码。                                                                                                                        |                |
| SourceDatabaseType        | 源数据库的类型。                                                                                                                           |                |
 可能的值: HSQLDB, MYSQL, ORACLE, POSTGRESQL, SQLSERVER | | SourceDatabaseUseIntegratedSecurity | 此设置定义是否应该用于 SQL Server。 如果选中，用户名和密码将不会被使用。 | false | | SourceDatabaseUseSl | 关于 PostgreSQL 数据库定义连接到源数据库是否将使用 SSL。 | false | | SourceDatabaseUsername | 与源数据库连接的用户名。 | | | SourceOracleService名称 | 定义当您与 Oracle DBMS 有连接时的SERVICE_NAME 作为源。 |   |

## 5 Amazon S3 存储服务设置 {#aws-s3}

以下设置影响Amazon S3存储服务模块的行为。 在Mendix Cloud中手动使用这些设置被强烈阻止，因为存储在外部系统中的文件将不会被包含在备份创建/恢复中。

| 名称                                               | 描述                                                                                                                                                                                                                                                                                                              | 默认值                                                                                                                                                                                                                |
| ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| com.mendix.storage.s3.AccessKeyId                | 以用户名身份验证Amazon S3服务。                                                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                    |
| com.mendix.storage.s3.SecretAccessKey            | 以密码身份验证Amazon S3服务。                                                                                                                                                                                                                                                                                             |                                                                                                                                                                                                                    |
| com.mendix.storage.s3.Bucket名称                   | 存储在 S3 上的文件的 bucket 名称。                                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                    |
| com.mendix.storage.s3.ResourceNameSuffix         | 存储对象的密钥后缀。 当buckets被分成不同的部分给不同的用户使用不同的凭据时(例如，存储对象为 "[key])。 用户1" for customer1 and as "[key].customer2" for customer2)                                                                                                                                                                                          |                                                                                                                                                                                                                    |
| com.mendix.storage.s3.PerformerDeleteFromStorage | 自7.19版以来已废弃。 使用 `com.mendix.storage.PerformeDeleteFromStorage`。<br/>定义是否删除Mendix 文件会导致存储服务中的实际删除。 在存储服务中不执行实际删除的原因可能是当它也被用作备份服务时。                                                                                                                                                                         | true                                                                                                                                                                                                               |
| com.mendix.storage.s3.EndPoint                   | 覆盖默认的 Amazon 网络服务端点。 当存储服务处于非AWS位置时使用此设置。 支持的端点(例如，'s3.example.com') 或包括协议在内的完整URL(例如， `https://s3.example.com`)。 请注意，当设置自定义端点路径样式访问时将会启用。 欲了解更多信息，见 [Class S3ClientOptions](http://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/services/s3/S3ClientOptions.html#withPathStyleAccess(boolean))。 |                                                                                                                                                                                                                    |
| com.mendix.storage.s3.UseV2Auth                  | 让认证策略使用 'signature 版本 2' 而不是默认的 'signature 版本 4'。 当端点不支持“签名版本 4”时，将此设置为“true”。                                                                                                                                                                                                                                  | false                                                                                                                                                                                                              |
| com.mendix.storage.s3.加密密钥                       | 可用来在S3\中加密和解密数据的密钥列表。 解密数据的正确密钥将根据加密的密钥自动选择。 每个加密密钥由密钥ID、加密算法和实际密钥(Base64编码)组成。 示例： ![](attachments/Custom+Settings/code_snippet_2.png)                                                                                                                                                                        |                                                                                                                                                                                                                    |
| com.mendix.storage.s3.MaxConnections             | 覆盖亚马逊S3服务中的默认最大连接限制。 对于大多数应用程序来说，默认值已足够。 所以我们不建议将此设置为自定义值，除非绝对需要更大的最大连接限制。                                                                                                                                                                                                                                      | [DEFAULT_MAX_CONNECTIs](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/ClientConfiguration.html#DEFAULT_MAX_CONNECTIONS) field of the ClientConfiguration interface in the AWS SDK for Java |
| com.mendix.storage.s3.clientExecutionTimeout     | 设置允许调用到存储服务完成的时间(毫秒)。 值为0表示没有超时。 欲了解更多信息，请见 [AWS Java SDK](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/ClientConfiguration.html#setClientExecutionTimeout-int-)。                                                                                                                        | 0 (无超时)                                                                                                                                                                                                            |
| com.mendix.storage.s3.连接超时                       | 设置在放弃和超时之前等待连接的时间 (毫秒)。 值为0意味着无限，不推荐。 欲了解更多信息，请见 [AWS Java SDK](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/ClientConfiguration.html#setConnectionTimeout-int-)。                                                                                                                        | 10 000 (10秒)                                                                                                                                                                                                       |
| com.mendix.storage.s3.SocketTimeout              | 设定要等待的时间(毫秒) 连接结束前打开连接。  值为0意味着无限，不推荐。 欲了解更多信息，请见 [AWS Java SDK](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/ClientConfiguration.html#setSocketTimeout-int-)。                                                                                                                           | 50.000 (50秒)                                                                                                                                                                                                       |
| com.mendix.storage.s3.RequestTimeout             | 设置等待完成请求的时间长度(毫秒) 才能放弃和超时。 值为0表示没有超时。 欲了解更多信息，请见 [AWS Java SDK](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/ClientConfiguration.html#setRequestTimeout-int-)。                                                                                                                           | 0 (无超时)                                                                                                                                                                                                            |

## 6 Microsoft Azure SQL

这些设置可以修改为Mendix 应用程序使用Microsoft Azure SQL数据库。

首先，您需要创建 Azure SQL 数据库(关于如何做到这一点的信息，请参阅 [SQL 数据库教程](https://azure.microsoft.com/en-us/documentation/articles/sql-database-get-started/))。 请确保您的 Azure 防火墙设置允许您的 Mendix 应用程序访问 Azure SQL 数据库(默认情况下，Azure 防火墙不允许外部连接)。

| 名称     | 描述                                             | 默认值 |
| ------ | ---------------------------------------------- | --- |
| 数据库类型  | SQLSERVER                                      |     |
| 数据库主机  | "your-database-host.database.windows.net:1433" |     |
| 数据库名称  | 您的数据库名称                                        |     |
| 数据库用户名 | 您的用户名                                          |     |
| 数据库密码  | 您的密码                                           |     |

## 7 微软Azure Blob 存储设置

这些设置可以使用Microsoft Azure blob 存储服务存储文件。 服务器端加密可以通过 Azure Portal 进行配置(见 [https://azure.microsoft.com/en-us/documentation/articles/storage-service-cryption/](https://azure.microsoft.com/en-us/documentation/articles/storage-service-encryption/))。

| 名称                                               | 描述                                                                                                              | 默认值    |
| ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------- | ------ |
| com.mendix.core.storageService                   | 必须设置为 'com.mendix.storage.azure' 来选择 Azure 作为存储服务                                                               |        |
| com.mendix.storage.azure.Account名称               | 使用 azure blob 存储服务进行身份验证的帐户名称                                                                                   |        |
| com.mendix.storage.azure.AccountKey              | 使用 azure blob 存储服务进行身份验证的账户密钥                                                                                   |        |
| com.mendix.storage.azure.Container               | 包含蓝色的容器名称。 如果容器还不存在，它将被创建。                                                                                      |        |
| com.mendix.storage.azure.ParallelismFactor       | 并联多部分文件上传/下载的最大数量。 我们建议您不要更改此设置，除非您在大文件中经历缓慢的文件传输。 选择更大的值会导致更高的内存使用率。                                           | 5      |
| com.mendix.storage.azure.UseHttps                | 引入版本7.7。 启用或禁用使用 HTTPS 的安全连接。 可以是 `true` 或 `false`。                                                             | `true` |
| com.mendix.storage.azure.TimeoutIntervalInMs     | 设置允许调用到存储服务完成的时间(毫秒)。 欲了解更多信息，请参阅 [Azure Libraries](https://azure.github.io/azure-sdk-for-java/storage.html)。   | 没有超时   |
| com.mendix.storage.azure.MaximumExecutionTimeInM | 设置在提出此请求时使用的最大执行时间(毫秒)。 欲了解更多信息，请参阅 [Azure Libraries](https://azure.github.io/azure-sdk-for-java/storage.html)。 | 没有最大时间 |

{{% alert type="warning" %}}

在 Mendix 7.7.0，我们将 Azure blob storage 的默认连接协议从 HTTP 改为 HTTPS 以鼓励默认安全连接。 这是一个高度推荐的最佳做法(详细信息，请参阅 [配置 Azure 存储连接字符串](https://docs.microsoft.com/en-us/azure/storage/common/storage-configure-connection-string))。 对于切换到此 Mendix 版本的现有客户，这应该是透明的。 除非您使用自定义域名(详情参见 [需要安全传输](https://docs.microsoft.com/en-us/azure/storage/common/storage-require-secure-transfer))。 在这种情况下，您应该使用上面的 `UseHttps` 设置来恢复到之前的默认行为并禁用 HTTPS。

{{% /报警 %}}

## 8 IBM Cloud (Bluemix) 对象存储设置

这些设置可以用于使用 IBM 云对象存储服务存储文件。

Mendix 支持 OpenStack 身份验证(键盘) v3 \。 与凭据相关的设置必须填写相应的值，这些值可以在您的对象存储服务的服务凭据部分找到。

请注意，IBM云端与其他存储服务不同，不提供服务器端加密。

| 名称                                              | 描述                                              | 默认值   |
| ----------------------------------------------- | ----------------------------------------------- | ----- |
| com.mendix.core.storageService                  | 必须设置为 'com.mendix.storage.propt' 来选择IBM 云作为存储服务 |       |
| com.mendix.storage.promot.Container             | 对象存储服务的容器名称                                     |       |
| com.mendix.storage.propect.Container.AutoCreate | 如果启用(值 `true`)，如果容器不存在，它将自动创建。                  | false |
| com.mendix.storage.promot.certificals.DomainId  | 域名唯一标识符                                         |       |
| com.mendix.storage.propect.validals.Authurl     | 身份验证URL                                         |       |
| com.mendix.storage.propect.validals.用户名         | 用户名                                             |       |
| com.mendix.storage.propest.validals.Password    | 密码                                              |       |
| com.mendix.storage.propect.compensations.region | 地区                                              |       |

## 9 Web 客户端设置

以下设置影响Mendix 网页客户端的行为。

| 名称                                             | 描述                                                                                                                                   | 默认值                                        |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------ |
| 启用 KeepAlive                                   | 定义网络客户端是否发送每一个 SessionTimeout/2 毫秒的存活请求，以防止会话超时。 浏览器中的每个单击都是KeepAlive。 禁用此属性将导致用户在10分钟闲置后自动退出，即使浏览器仍然开启。                             | true                                       |
| PhoneUserAgentRegEx                            | 定义用于确定用户是否从手机访问Mendix 应用程序的正则表达式。 正则表达式与客户端的 web 浏览器发送的用户代理头匹配。                                                                      | Android, Mobile (iPhone, iPod, BlackBerry) |
| TabletUserAgentRegEx                           | 定义用于确定用户是否从平板电脑访问Mendix 应用程序的正则表达式。 正则表达式与客户端的 web 浏览器发送的用户代理头匹配。                                                                    | Android, iPad                              |
| com.mendix.webui.HybridAppLoginTimeOut         | 确定您的令牌在使用完整凭据重新认证之前仍然有效的分钟数。 默认设置为 -1，等于没有超时。                                                                                        | -1                                         |
| com.mendix.webui.反馈Size警告阈值                    | 引入版本7.0。 当反馈大小超过阈值时，将记录警告。 反馈将从服务器发送到客户端来指示(例如，刷新对象或打开页面)。 它们被序列化为服务器响应中的“指示”。 如果有太多的指示，这可能会影响到业绩，因为它们都必须按顺序排列给客户。 为此原因，当超过阈值时会记录警告。 | 5000                                       |
| com.mendix.webui.StateSize警告阈值                 | 引入版本7.0。 当状态大小超过阈值时会记录警告。 状态包括更改对象和未输入数据库的对象(尚未输入)。 如果情况太多，这将会产生业绩影响，因为整个状态必须序列化给客户。 为此原因，当超过阈值时会记录警告。                               | 100                                        |
| com.mendix.webui.Commonwealth ObjectsThreshold | 阈值控制执行微流程后有多少数据被送回客户端。 默认情况下，当全部对象被更改或提交时，我们会将其退出。 当达到此阈值时 只有对象 GUID 会被送回，所以客户端会知道更改情况，而通过网络发送的数据数量会减少。 然后客户端将在必要时稍后检索对象。            | 100                                        |

## 10 代理设置

以下设置允许您使用代理服务器.

| 名称             | 描述                  | 默认值 |
| -------------- | ------------------- | --- |
| http.proxyHost | 定义代理服务器的主机名         |     |
| http.proxyPort | 定义代理服务器的 portnumber |     |
