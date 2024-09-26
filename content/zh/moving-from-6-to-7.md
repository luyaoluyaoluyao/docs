---
title: "从 Moderr 版本 6 移动到7"
category: "A. 概况"
menu_order: 20
description: "提供关于将您的项目从 Mendix 6 升级到 Mendix 7 的详细信息，包括转换您的项目和废弃功能的章节。"
aliases:
  - /refguide/moving-from-6-7.html
  - /releasenotes/studio-pro/6.10.html
---

## 1 导言

关于正在Mendix 7中添加的所有新的主要改进的最新详情，请参阅 [桌面Moderr 7 版本说明](/releasenotes/studio-pro/7)。

此文档将帮助您将您的项目从 Mendix 6 升级到 Mendix 7。 它包含以下主题：

* 转换你的项目 — — 准备转换并实际转换你的项目 Mendix 7
* Java 8 要求 -- 从 Mendix 6 开启，Java 8 需要运行您的应用程序
* 已废弃的功能 — — 查看在Mendix 7 中哪些平台功能已被弃用
* 已删除过时的功能——查看哪些功能已被弃用

## 2 转换你的项目

在转换您的项目之前，建议阅读以下章节。

### 2.1 备份您的项目

如果您没有使用团队服务器，请备份您的项目。 通过打开项目检查备份是否成功。

{{% alert type="success" %}}
真的要备份！
{{% /报警 %}}

### 2.2 转换为最新的 Mendix 6 版本

转换为 Mendix 7 将适用于使用 6.0.0 或更高版本创建的项目。 然而，我们建议转换到最新的 Mendix 6 版本，然后转换到最新的 Mendix 7 版本。

### 2.3 纠正错误，警告 & 废弃的

尽可能修复错误、警告和弃置等问题。 特别注意 **错误** 窗格中的 **废弃**。 Mendix 6中已废弃的大多数功能将完全在 Mendix 7中使用，这些功能将导致您项目中的错误。

### 2.4 在 Java 操作中修复过时问题

通过在 Eclipse 中导入您的 Java 操作并解决 **问题** 标签页中所有废弃的问题来修复您的 Java 操作中的弃置状态。

关于已删除和已废弃API的详细信息， 查看 **打破对 [桌面模式版本7版本版本的</strong> 部分的更改](/releasenotes/studio-pro/7.0#BreakingChanges)。</p>

## 3 个转换中！

现在您已准备好转换，所以只需在新的桌面模式中打开您的项目。 在 Mendix 7 中打开您的 Mendix 6 项目后不需要明确的操作。 当您将您的应用程序从Modeler脱离时， 双选同步对话框中所有域模型的更改，以避免意外的修改。

### 3.1 升级市场模块

转换后，验证市场模块是否有更新版本。 某些模块需要升级才能让 Mendix 7 兼容。 读取版本发布说明以查看是否需要特定操作。

在 Mendix 7 中，您项目中使用的应用市场模块被组合在模型中。 它们可以在 **项目资源管理器** 中找到。 **项目** > **应用商店模块**。

### 3.2 双重检查项目变化

验证在上面列出的迁移步骤中，没有模块被重新删除和导入替换。 通过设计，此操作指示桌面模型删除整个模块并再次创建它。 这将导致在移徙结束后出现空实体和协会。

## 4 打破更改

### 4.1 无国籍运行时间 {#stateless}

早期版本的 Mendix 启用了将会话移动到数据库和文件到外部文件存储设施的程序 (例如，) S3 或 Azure Blob 存储)。 在 Mendix 7 中，服务器对象状态已被移动到客户端， 这意味着服务器现在完全无国籍，可以随意水平缩放。

此功能默认启用，所以不需要额外配置。

因为这种无国籍状态，所以是客户端跟踪尚未承诺的物件， 不可持续的对象，甚至对尚未提交的对象的更改。 保持低资源使用率。 Mendix 定期打印存储的状态 - 删除未显示在界面中且未被引用连接的对象。 了解状态在您的应用中有多大(甚至是它存在的原因)， 在您的浏览器中使用 <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>G</kbd> 并且信息将被丢弃到您的浏览器的控制台中(注意此功能可能会在未来版本中被删除)。 欲了解更多详情，请参阅 [Monitoring Client State](monitoring-client-state)。

请注意，重新加载浏览器窗口(按下 F5) 将会丢弃整个状态。

由于服务器不再存储对象状态，客户端必须与一些请求一起发送。 这样服务器端微流就可以访问NPE、未承诺的值等。 Mendix 应用了相当多的优化，以便尽可能少地发送数据，并保持与以前Mendix 版本相同的网络足迹。 **运行时** 选项卡里有一个新设定 **项目设置** 叫做 **优化网络调用**如果你在你的项目中遇到了一些棘手的问题(例如) 一个从客户端调用但看不到数据源微流所做的更改的微流程，您可以尝试禁用这些优化。 (请注意，此设置将在未来版本中删除，所以请尽快报告您遇到的任何问题。)

### 4.2 持续会议

默认启用持久会话。 这对于Mendix 在分组场景中正常工作是必要的。 It's still possible to disable persistent sessions by setting `PersistentSessions` to `false`. 然而，在这种情况下，您将无法以集群模式运行 Mendix 。

我们优化了系统，以降低默认启用的性能影响。 这是通过允许Mendix Runtime 实例假定会话在短时间内有效实现的(默认为30秒)。 Mendix 运行时间实例只会在该时间段内验证会话一次。 然而，这意味着用户注销时， 它可能需要达到这个特定的时间(最坏情况下的场景)才能在群集的所有Mendix Runtime实例(除处理注销的一个实例外)承认用户已经注销了。 此超时可以通过设置 `会期校验超时`的值来配置，它代表以毫秒为单位的时间。

### 4.3 NPE 属性安全

我们禁止对没有至少读取访问权限的属性进行不可持续实体属性级安全。 原因是无法读取属性无法发送到客户端。 这些属性应该使用一个单独的对象 (根本不发送给客户端)。

### 4.4 系统会话自动提交对象

如果你有两个新的对象相互引用并且你试图提交其中一个对象，你也应该提交另一个。 如果您没有和您正在系统会话中运行microflow (例如预定的事件)，您将得到一个例外。 请注意，如果您在不需要的用户会话中运行，我们将为您处理。

### 4.5 从数据库中获取的对象不是国家

从数据库检索到的对象不是状态的一部分(与关联检索到的对象相比)。 这意味着您不能通过来自数据库的对象访问未提交的更改和新对象。 即使从这些对象开始通过关联获取。

例如，假定用户已经与现有的订单对象关联(但没有承诺)。 当从数据库中检索到的订单对象时，不会检索上述订单线。 然而，当订单对象作为微流程参数从页面传递时，相同的检索返回订单行对象。

### 4.6 登录微流

登录微流不再被支持，因为它们不添加任何功能。 在未来的版本中，状态将被客户端自动从匿名用户转移到登录用户。 在 Mendix 7 中，选择登录微流将导致一致性检查错误。 当通过设置微流程到 **无**解决这个问题时，属性将自动从用户界面消失。

### 4.7 系统统计实体

`系统。 tatistics` 实体已经从 **系统** 模块中删除， 随着无国籍运行时间的引入，该实体已经过时。 **运行时间统计** 页面 (与 **运行时间统计** 菜单项) 和 **查看统计** 微流程在您的项目中处于默认位置时自动从它们中移除( **管理** 模块)。

### 4.8 客户端 API 更改

`MxObject.get` and `mx.parser.parseValue` 的语义已更改。 他们现在返回了一个适当类型的值(例如，数字为 `大` , 日期数字)，而不是总是返回一个字符串。 欲了解更多详情，请见 [类：mendix/lib/MxObject](https://apidocs.rnd.mendix.com/7/client/mendix_lib_MxObject.html#get)。

`dojo.requires` 的支持已被放弃。 它从来没有在混合应用中发挥作用，我们现在已经使它成为正式的。 用AMD样式写下您的自定义小部件，如 [小部件Boilerplate](https://github.com/mendix/AppStoreWidgetBoilerplate) 所述。

Dojo APIs exposed through the global `dojo` object are no longer supported, as they were never supposed to work in AMD widgets. 有些API (例如 `dojo.html`) 已经被删除，但其他一些将在将来被移除。 使用这些冒着自己的风险，或者更好的风险，不要使用它们！

## 5 个废弃的功能

Mendix 7中已不推荐使用以下功能。 不鼓励使用这些功能，因为它们将在未来Mendix版本中被移除。

### 5.1 客户端弃用

`mx.server.request` 客户端 API 方法已被弃用。 我们打赌，你甚至根本不知道它存在！ 如果你这样做，请注意它不再处理验证。 此责任已被移动到 `mx.data`。

`MxContext` 方法 `setTrackId` 和 `setTrackEnty` 已被弃用。 使用 `setContext` 方法代替。

### 5.2 在 `com.mendix.core.core上已废弃的`

| 方法名称                                                                                                            | 备选办法                                                                                                                                                                            |
| --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `getActiveSession(用户名)`                                                                                         | 使用会话表上的 XPath 查询。                                                                                                                                                               |
| `getActiveSessions()`                                                                                           | 使用会话表上的 XPath 查询。                                                                                                                                                               |
| `导出Stream(Context context, String Exporting MappingName, IMendixObject objectToExport, Boolian shouldValidate)` | `com.mendix.core.integration().exportStream(IContext context, String exportingName, IMendixObject objectToExport,Boolian shouldValidate)`                                       |
| `导入 Stream(IContext 环境,InputStream 串流,String 导入映射名称,IMendixObject mappingParameter,Boolian shouldValidate)`     | `com.mendix.core.integration().importStream(IContext context, InputStream stream stream, String importing MappingName, IMendixObject mappingParameter, Boolian shouldValidate)` |

## 6 已删除过时的功能

以下功能在 Mendix 6 中被废弃，并已在 Mendix 7 中被删除。

### 6.1 移除客户端功能

#### 6.1.1 分割面板

我们放弃了对自Mendix 6以来被废弃的垂直和水平分割窗格部件的支持。 从现在开始，这些小部件将导致模型中的一致性错误。 为了平滑转换路径，我们引入了一个将现有的拆分窗格(一个或全部)转换为布局网格的工具。 您可以通过右键单击一致性错误消息或从 **工具** 菜单访问工具。

请注意，虽然这个工具肯定很棒，但它并不完美。 生成的布局网格将无法动态调整大小(通过拆分窗格的动画调整大小功能) 这个平台不再支持)，标记和滚动行为可能有些不同。 因此，请在升级到 Mendix 7 后测试您的应用程序！ (我们真的必须提到这一点？)

#### 6.1.2 传统导航布局

**传统的** 类型的导航布局支持已被放弃。 布局类型定义了页面在网页客户端中的打开方式：在一个(模式)弹出窗口中或在内容中。 对于传统类型的导航布局，这种行为是通过打开页面的按键(或微流程)定义的，可能导致行为不一致。 传统类型的所有导航布局现在都会导致建模中的错误。

欲了解更多信息，请参阅 [布局](layout#layout-type) 和博客文章 [布局有类型](https://www.mendix.com/blog/layouts-have-types/)。

#### 6.1.3 应用Context & 从上下文删除

**应用上下文** 和 **从上下文中删除参考选择器的** 选项。 Mendix 版本5中已废弃数据网格和模板网格数据源。 这些建议已经被删除。 您现在将在使用它们的地方获得一致性错误。 我们建议使用明确的 XPath 限制。

### 6.2 已移除客户端 APIs

* `mxui/dom。{p,div,span...}` 和 `mxui/dom.builder` 已被删除，用于使用 `mxui/dom.create`
* `MxMetaObject.isNumber` and `MxObject.isNumber` 已被 `isNumeric` 方法替换
* `mxui/dom。{copyChildren,insertBefore,insertAfter}` 已被移除，方便使用普通 `套` APIs
* `mx.ui.hide登录` 已被替换为 `隐藏` 返回对象的 `mx.ui.show登录`
* `mx.login` 签名已更改为 `mx.login(用户名，密码，onLoginSucceed, onLoginFailure)`
* `_WidgetBase.rest`, `_WidgetBase.sust`和 `_FormBase.startup` 已被删除，因为它们没有效果

### 6.3 移除运行时功能

#### 6.3.1 移除废弃类

| 类名                                                                      | 替代界面/面板                                                                |
| ----------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `com.mendix.modules.exportmanager.excelCellStyle`                       | `com.mendix.modules.exportManager`, `.interfaces.excelIExcelCellStyle` |
| `com.mendix.modules.exportmanager.excel.ExcelCell`                      | `com.mendix.modules.exportManager`, `.interfaces.excelIExcelCell`      |
| `com.mendix.modules.exportmanager.excel.ExcelColumn`                    | `com.mendix.modules.exportManager`, `.interfaces.excelIExcelColumn`    |
| `com.mendix.modules.exportmanager.excelGrid`                            | `com.mendix.modules.exportManager`, `.interfaces.excelIExcelGrid`      |
| `com.mendix.systemwide interfaces.core.core.反馈`                         | `com.mendix.systemwide interfaces.core.IFeedback`                      |
| `com.mendix.core.com.Conf.ConfurationImpl`                              | `com.mendix.core.conf.配置`                                              |
| `com.mendix.core.component.InternalCore`                                | `mendix.Core`                                                          |
| `com.mendix.core.conf.Conf.ConfValueChecker`                            | -                                                                      |
| `com.mendix.core.com.UserPermissions`                                   | -                                                                      |
| `com.mendix.core.conf.certiateProcessor`                                | -                                                                      |
| `com.mendix.core.conf.HashorithmType`                                   | -                                                                      |
| `com.mendix.systemwide interfaces.connectionbus.ConnectionBusException` | -                                                                      |
| `com.mendix.systemwide interfaces.connectionbus.DBMSType`               | -                                                                      |
| `com.mendix.systemwide interfaces.connectionbus.JDBCDatasore配置`         | -                                                                      |
| `com.mendix.systemwide interfaces.core.IMendixEnum`                     | `com.mendix.core.objectmanagement.member.MendixEnum`                   |

#### 6.3.2 移除常量

| 类名                                                                           | 备选办法                                                                                                                                                                        |
| ---------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `com.mendix.systemwide interfaces.HandlerConstants`                          | -                                                                                                                                                                           |
| `com.mendix.systemwide interfaces.SystemModuleConstants`                     | -                                                                                                                                                                           |
| `com.mendix.core.conf.CoreConstants`                                         | -                                                                                                                                                                           |
| `com.mendix.core.conf.AdminActionConstants`                                  | -                                                                                                                                                                           |
| `com.mendix.core.conf.Tokens`                                                | -                                                                                                                                                                           |
| `com.mendix.externalinterface.connector.RequestHandler.XAS\_SESSION\_ID` | 用于请求处理器： `com.mendix.externalinterfacee.connector.RequestHandler.getSessionCookieName()`<br> 用作常量： `com.mendix.core.core.getConfiguration().getSessionIdCookieName()` |

#### 6.3.3 移除的方法

##### 6.3.3.1 从 com.mendix.core.core.configuration

| 方法名称                                                  | 备选办法 |
| ----------------------------------------------------- | ---- |
| `registerConfigurationSetting(字符串默认值)`                | -    |
| `getValue(名字)`                                        | -    |
| `设置值(字符串值)`                                           | -    |
| `updateConfiguration(JSONObject 参数，布尔值覆盖)`            | -    |
| `getUploadedFilesPath()`                              | -    |
| `useLDAPAuthentication()`                             | -    |
| `getReadCommittedSnapshot()`                          | -    |
| `getMaxThreadsPerDataStoreRequest()`                  | -    |
| `getLogMinDurationQuery()`                            | -    |
| `mustReturnOnlyNecessaryDDLCommands()`                | -    |
| `setReturraynecessaryDDLCommands(布尔只有必需的DDLCommands)` | -    |
| `getConstantValue(对象组件，字符串键)`                         | -    |
| `getDefaultHashAlgorithm()`                           | -    |

##### 6.3.3.2 从 com.mendix.modules.exportmanager.excel.ExcelExporter

| 方法名称                                                                                                                                                                                                                          | 备选办法                                                                                                                                            |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| `生成Workbook(本地组件组件，上下文，列表<IExcelGrid> 格子)`                                                                                                                                                                              | -                                                                                                                                               |
| `GenerateXLS(com.mendix.core.component.LocalComponent component, IContext context, IMendixObject fileObject, String fileName, List<IExcelGrid> gids)`                                                                   | `生成XLS(上下文, IMendixObject fileObject, String fileName, List<IExcelGrid> gids)`                                                            |
| `generateXLS(com.mendix.core.core.component.LocalIncomponent component, IContext context, IMendixObject fileObject, String fileName, List<String> oqlQueries, boolian autoSizeColumns, List<String> headerNames)` | `生成XLS(上下文, IMendixObject fileObject, String fileName, List<String> oqlQueries, boolian autoSizeColumns, List<String> headernames)` |

##### 6.3.3.3 从 com.mendix.coreIContext

| 方法名称                                                            | 备选办法                |
| --------------------------------------------------------------- | ------------------- |
| `设置CurrentIdentifier(IMendixIdentifier currentIdentifier)`      | -                   |
| `setContextObjects(列表<IMendixIdentifier> contextObjects)` | -                   |
| `setSudo(boolean sudo)`                                         | -                   |
| `getSudoContext()`                                              | `createSudoClone()` |

##### 6.3.3.4 从 com.mendix.coreCore

| 方法名称                                                    | 备选办法                                                  |
| ------------------------------------------------------- | ----------------------------------------------------- |
| `callWebservice()`                                      | 在微流中使用通话REST 动作。                                      |
| `importXmlStream()`                                     | 使用 `com.mendix.core.integration().importStream()` 代替。 |
| `getComponent().runtime().about().get("model_version")` | `getModelVersion()`                                   |

##### 6.3.3.5 从com.mendix.systemwide interfaces.core.ISession

状态已经移动到Mendix 7的客户端，因此以下方法现在已经过时：

| 方法名称                 | 备选办法 |
| -------------------- | ---- |
| `保留`                 | -    |
| `发布`                 | -    |
| `addToClientRoots`   | -    |
| `移除 FromClientRoots` | -    |
| `getClientRoots`     | -    |
| `getJavaScript`      | -    |
| `getData`            | -    |

##### 6.3.3.6 其他

| 方法名称                                                           | 备选办法                                                              |
| -------------------------------------------------------------- | ----------------------------------------------------------------- |
| `com.mendix.m2ee.api.IMxRuntimeRequest.getoriginalRequest()`   | `com.mendix.m2ee.api.IMxRuntimeRequest.getHttpServletRequest()`   |
| `com.mendix.m2ee.api.IMxRuntimeResponse.getoriginalResponse()` | `com.mendix.m2ee.api.IMxRuntimeResponse.getHttpServletResponse()` |
| `com.mendix.systemwideface.core.metaObject.getComponent()`     | -                                                                 |
| `com.mendix.core.ISession.getComponent()`                      | -                                                                 |

#### 6.3.4 将项目迁移到Mendix 7

在 Mendix 7 中移除已弃用的类和方法可能在将您的项目迁移到 Mendix 7 后导致编译错误。 请使用上面提供的替代方法来替代已删除的代码。

#### 6.3.5 SystemModuleConstants

这些主要用来指系统实体的名称或其属性名称。 这些名字也可以通过相应的系统代理人获得。

例如， `SystemModuleConstants.FILE_DOCUMENT_NAME` 可以替换为 `FileDocument` 代理：

```
导入 com.mendix.systemwides.SystemModuleConstants;

private final String FILE_DOCUMENT_NAME = SystemModuleConstants.FILE_DOCUMENT_NAME;
```

应改为：

```
导入 system.proxies.FileDocument.Members;

private final String FILE_DOCUMENT_NAME = MemberNames.Name.toString();
```

其中 `个成员名` 是在 `FileDocument` 代理类中定义的枚举.

#### 6.3.6 移动的包

| 类名              | 替代接口                                  |
| --------------- | ------------------------------------- |
| `org.json.\*` | `com.mendix.thirdparty.org.json.\*` |

这是为了避免在 `org.json` 库的 Mendix 版本与其他 JSON 库之间可能发生的命名空间冲突。

#### 6.3.7 将项目迁移到Mendix 7时的运行时问题

Mendix 7中带有安装包的Java 库不再适用于项目。 虽然这会导致每个项目更好的依赖管理，但它也可能在迁移后的运行时造成错误(例如， `NoClassDefFound错误`)。 因此，必须确保迁移项目的 `userlib` 目录包含所有必需的库。 还值得注意的是，在Mendix 7中，每个图书馆在运行时只能有一个版本。 这意味着，如果一个库有多个版本，使用最新版本，其他版本被忽略。

### 6.4 移除数据存储功能

#### 6.4.1 移除方法

| 软件包名称                                                         | 方法名称                   | 备选办法                   |
| ------------------------------------------------------------- | ---------------------- | ---------------------- |
| `com.mendix.systemwide interface.connectionbus.data.IDataRow` | `getPrimaryKeyValue()` | `getValue(context, 0)` |

##### 6.4.1.1 实例用法

`IDataRow.getPrimaryKeyValue()`

让我们使用 getPrimaryKeyValue() 方法在Mendix 6.x中检索MendixObject

`列表<? 扩展 IDataRow> dataRows = recheveOQLDataTable.getRows();`<br> `IDataRow dataRw = dataRows. et(0)；`<br> `IMendixidentifier mendixidentifier = dataRow。 etPrimaryKeyValue();`<br> `IMendixObject mendixObj = Core.retrieveId(context, mendixIdentifier);`<br>

在Mendix 7.x中获得MendixObject 的类似方法如下：

 `列表<? 扩展 IDataRow> dataRows = recheveOQLDataTable.getRows();`<br> `IDataRow dataRw = dataRows. et(0)；`<br> `IMendixidentifier mendixidentifier = dataRow。 etValue(context, 0);`<br> `IMendixObject mendixObj = Core.re.revieId(context, mendixIdentifier);`<br>
