---
title: "モデラーバージョン6から7へ移動"
category: "全般"
menu_order: 20
description: "Mendix 6からMendix 7へのプロジェクトの更新に関する詳細を提供します。プロジェクトの変換と非推奨機能に関するセクションを含みます。"
aliases:
  - /refguide/moving-from-6-to-7.html
  - /releasenotes/studio-pro/6.10.html
---

## 1つの紹介

Mendix 7に追加された新たな主要な改善点の最新情報については、 [Desktop Modeler7 リリース ノート](/releasenotes/studio-pro/7) を参照してください。

このドキュメントは、Mendix 6からMendix 7にプロジェクトを更新するのに役立ちます。 以下のトピックが含まれています:

* プロジェクトの変換 - 変換の準備と実際にプロジェクトをMendix 7に変換する
* Java 8要件 - Mendix 6からアプリケーションを実行するには、Java 8が必要です
* 非推奨の機能 – Mendix 7で廃止されたプラットフォームの機能を参照してください。
* 非推奨機能を削除しました – 非推奨になった機能を参照してください。

## 2プロジェクトの変換

プロジェクトを変換する前に、以下のセクションを読むことをお勧めします。

### 2.1 プロジェクトのバックアップ

Team Serverを使用していない場合は、プロジェクトのバックアップを作成してください。 プロジェクトを開いてバックアップが成功したことを確認します。

{{% alert type="success" %}}
真剣に、バックアップを作成します!
{{% /alert %}}

### 2.2 最新のMendix 6バージョンへの変換

Mendix 7への変換は、バージョン6.0.0以降で作成されたプロジェクトで機能します。 ただし、最新のMendix 7バージョンに変換する前に、最新のMendix 6バージョンに変換することをお勧めします。

### 2.3 エラー、警告 & 廃止の修正

エラー、警告、および非推奨を可能な限り修正します。 **エラー** ペインの **非推奨** について特に注意してください。 Mendix 6で非推奨となっているほとんどの機能はMendix 7で完全になくなり、これらはプロジェクトでエラーになります。

### 2.4 Java アクションでの非推奨の修正

Eclipse にプロジェクトをインポートし、 **問題** タブのすべての非推奨を解決することで、Java アクションの非推奨を修正します。

削除された、非推奨の API の詳細については、 **Desktop Modelerバージョン 7 リリースノート** の [Breaking changes](/releasenotes/studio-pro/7.0#BreakingChanges) セクションを参照してください。

## 3 Converting!

変換の準備ができましたので、新しいDesktop Modelerでプロジェクトを開いてください。 Mendix 7でMendix 6プロジェクトを開いた後、明示的なアクションは必要ありません。 モデラーからアプリをデロイト 予期しない変更を避けるために、同期ダイアログボックス内のすべてのドメインモデルの変更をダブルチェックします。

### 3.1 マーケットプレイスモジュールのアップグレード

変換後、Marketplace モジュールの新しいバージョンがあるかどうかを確認します。 Mendix 7互換にするためにアップグレードする必要があるモジュールもあります。 バージョンリリースノートを読んで、特定のアクションが必要かどうかを確認します。

Mendix 7では、プロジェクトで使用されるMarketplaceモジュールがモデラーにまとめられています。 **Project Explorer** の **Project** > **App store modules** にあります。

### 3.2 プロジェクトの変更を再確認する

上記の移行ステップでは、モジュールを再度削除およびインポートすることによってモジュールが置換されないことを確認します。 この操作は、Desktop Modelerにモジュール全体を削除して再度作成するように指示します。 これは、移行が完了した後に空のエンティティや関連付けにつながります。

## 破壊的な変更（4）

### 4.1 ステートレスランタイム {#stateless}

以前のバージョンのMendixが有効になっているアプリケーションは、セッションをデータベースおよびファイルに外部ファイルストレージ機能に移動します(例えば、 S3 または Azure Blob Storage )。 Mendix 7 では、サーバーオブジェクトの状態がクライアントに移動されました。 つまりサーバーは完全にステートレスで 水平方向に拡大できます

この機能はデフォルトで有効になっているため、追加の設定は必要ありません。

このステートレスのため、まだコミットされていないオブジェクトを追跡するのはクライアントです。 永続性のないオブジェクト、まだコミットされていないオブジェクトへの変更さえあります。 リソース使用量を低く保つために。 Mendixは、保存された状態を定期的に剪定します — UIに表示されず、参照によって接続されていないオブジェクトは削除されます。 アプリ内の状態の大きさ(そして存在する理由)についての洞察を得るために。 ブラウザで <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>G</kbd> を使用すると、情報がブラウザのコンソールにダンプされます（この機能は今後のリリースで削除される可能性があることに注意してください）。 詳細については、 [クライアント状態のモニタリング](monitoring-client-state) を参照してください。

(F5キーを押すと)ブラウザーウィンドウを再読み込みすると状態全体が失われることに注意してください。

サーバーはもうオブジェクトの状態を保存しないため、クライアントはいくつかのリクエストと一緒にそれを送信する必要があります。 サーバー側のマイクロフローは、NPE、コミットされていない値などにアクセスできます。 Mendixは、できるだけ少ないデータを送信し、以前のMendixバージョンと同じネットワークフットプリントを維持するために、かなりの数の最適化を適用します。 **プロジェクト設定** の **ランタイム** タブの **ネットワーク呼び出しの最適化**に新しい設定があります。 プロジェクトで厄介な問題が起きた場合 データソースのマイクロフローによって行われた変更が表示されないクライアントからのマイクロフロー)、これらの最適化を無効にしようとすることができます。 (この設定は今後のリリースで削除されるので、できるだけ早く問題を報告してください。

### 4.2 持続的なセッション

永続的なセッションはデフォルトで有効になっています。 これは、Mendixがクラスタ化されたシナリオで正しく動作するために必要です。 `PersistentSessions` を `false` に設定することで、持続的なセッションを無効にすることは可能です。 ただし、その場合、クラスタモードでMendixを実行することはできません。

デフォルトでこれを有効にする際のパフォーマンスへの影響を減らすためにシステムを最適化しました。 これは、Mendix Runtime インスタンスに短い時間(デフォルトでは30秒)のセッションが有効であると仮定させることによって達成されます。 Mendix Runtime インスタンスは、その期間内に一度だけセッションを検証します。 ただし、これはユーザーのログアウト時にそれを意味します。 クラスタのすべてのMendixランタイムインスタンス(ログアウト処理の1つを除く)が、ユーザーがログアウトしていることを認識する前に、その特定の期間(最悪の場合のシナリオでは)がかかることがあります。 このタイムアウトは、ミリ秒単位の時間を表す `SessionValidationTimeout`の値を設定することで設定できます。

### 4.3 NPE Attribute-Level Security

少なくとも読み取りアクセス権を持たない属性に対して、非持続可能エンティティ(NPE)属性レベルのセキュリティを禁止しています。 この理由は、読み取り不可能な属性をクライアントに送信できないためです。 これらの属性には、(まったくクライアントに送られていない)別のオブジェクトを使用する必要があります。

### 4.4 システムセッションの自動コミットオブジェクト

2つの新しいオブジェクトが互いに参照していて、それらのいずれかをコミットしようとする場合は、もう1つをコミットする必要があります。 システムセッションでマイクロフローを実行していない場合(スケジュールされたイベントなど)、例外が発生します。 必須ではないユーザー・セッションで実行している場合は、そのセッションを処理します。

### 4.5 データベースから取得したオブジェクトはステートではありません

データベースから取得されたオブジェクトは、ステートの一部ではありません (関連付けによって取得されたオブジェクトと比較して)。 つまり、データベースから来るオブジェクトを通じて、コミットされていない変更や新しいオブジェクトにアクセスすることはできません。 これらのオブジェクトから始まる関連付けによって取得する場合でもです

例えば、ユーザーが既存の注文オブジェクトに関連付けられている(しかしコミットされていない)と仮定します。 データベースから取得した注文オブジェクトを介して注文行を取得する場合、前述の注文行は取得されません。 しかし、ページから microflow パラメータとして注文オブジェクトが渡されると、同じ取得が注文行オブジェクトを返します。

### 4.6 サインインマイクロフロー

サインインマイクロフローは機能を追加しないため、サポートされなくなりました。 将来のバージョンでは、状態は自動的にクライアントによって匿名ユーザーからサインインユーザーに転送されます。 Mendix 7では、サインインマイクロフローを選択すると、一貫性チェックエラーが発生します。 microflow を **None**に設定することで解決すると、UIから自動的にプロパティが消えます。

### 4.7 システム統計エンティティ

`システム. t<unk> <code>` エンティティが **システム** モジュールから削除されました 無国籍ランタイムの導入によって実体は時代遅れになってしまった。 **Runtime Statistics** ページ ( **Runtime Statistics** メニュー アイテムとともに) と **ViewStatistics** マイクロフローは、( **管理** モジュール内の) デフォルトの場所にあるプロジェクトから自動的に削除されます。

### 4.8 クライアント API の変更

セマンティクスは `MxObject.get` と `mx.parser.parseValue` のために変更されました。 これにより、常に文字列を返すのではなく、適切な型の値(数字の場合は `Big` など)を返すようになりました。 詳細については、 [Class: mendix/lib/MxObject](https://apidocs.rnd.mendix.com/7/client/mendix_lib_MxObject.html#get) を参照してください。

`dojo.require` のサポートが削除されました。 ハイブリッドアプリでは機能しませんでしたが、今では公式化されています。 [ウィジェット ボイラープレート](https://github.com/mendix/AppStoreWidgetBoilerplate) に記載されているように、カスタム ウィジェットを AMD スタイルで記述します。

グローバルな `道場` オブジェクトを通じて公開されたDojoAPIは、AMDウィジェットで動作することは想定されていなかったため、サポートされなくなりました。 これらの API の一部(例えば `dojo.html`など)はすでに削除されていますが、将来的には予告なしに削除されます。 あなた自身のリスクでこれらを使用するか、それ以上、それらをまったく使用しないでください!

## 非推奨の5つの機能

Mendix 7では、次の機能が廃止されました。 Mendixの今後のリリースで削除されるため、これらの機能を使用することは推奨されません。

### 5.1 クライアントの<unk>

`mx.server.request` クライアント API メソッドは非推奨になりました。 私たちは、あなたがそれが存在することを知らなかったことを賭けます! その場合は、バリデーションは処理されなくなりますのでご注意ください。 この責任は `mx.data` に移動しました。

`MxContext` メソッド `setTrackId` と `setTrackEntity` は非推奨となりました。 代わりに `setContext` メソッドを使用してください。

### 5.2 `com.mendix.core.Core`

| メソッド名                                                                                                                            | 代替                                                                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `getActiveSession(String userName)`                                                                                              | 代わりにセッションテーブルの XPath クエリを使用します。                                                                                                                                      |
| `getActiveSessions()`                                                                                                            | 代わりにセッションテーブルの XPath クエリを使用します。                                                                                                                                      |
| `exportStream(IContext コンテキスト, String exportMappingName, IMendixObject objectToExport, Boolean shouldValidate)`                  | `com.mendix.core.integration().exportStream(IContext context, String exportMappingName, IMendixObject objectToExport,Boolean shouldValidate)`                        |
| `importStream(IContext コンテキスト,InputStream ストリーム,String importMappingName,IMendixObject mappingParameter,Boolean shouldValidate)` | `com.mendix.core.integration().importStream(IContext context, InputStream stream, String importMappingName, IMendixObject mappingParameter, Boolean shouldValidate)` |

## 6 廃止された非推奨機能を削除

以下の機能は Mendix 6 で非推奨となり、Mendix 7 で削除されました。

### 6.1 削除されたクライアント機能

#### 6.1.1 ペインを分割

Mendix 6以降非推奨となっている垂直分割ペインウィジェットと水平分割ペインウィジェットのサポートを廃止しました。 これ以降、これらのウィジェットはモデラーの一貫性エラーになります。 変換パスをスムーズにするために、既存の分割ペイン(1つずつまたはすべてまとめて)をレイアウト グリッドに変換するツールを導入しました。 一貫性エラーメッセージを右クリックするか、 **ツール** メニューからツールにアクセスできます。

ツールは間違いなく素晴らしいですが、完璧ではないことに注意してください。 結果のレイアウトグリッドは(分割ペインのアニメーションリサイズ機能を介して)動的にサイズを変更することはできません。 これはもはやプラットフォームでサポートされていません)、マークアップとスクロールの動作が少し異なる場合があります。 Mendix 7にアップデートした後、アプリケーションをテストしてください! (我々は本当にそれを言及する必要がありますか?)

#### 6.1.2 従来のナビゲーションレイアウト

**Legacy** タイプのナビゲーションレイアウトのサポートが削除されました。 レイアウトタイプでは、Web クライアントでのページの開き方を定義します。(モーダル) ポップアップウィンドウまたはコンテンツです。 Legacyタイプのナビゲーションレイアウトでは、その動作はページを開くボタン (またはマイクロフロー) によって定義され、一貫性のない動作になる可能性があります。 レガシー型のすべてのナビゲーションレイアウトは、モデラーのエラーになります。

詳しい情報については、 [レイアウト](layout#layout-type) およびブログ投稿 [レイアウトに型がある](https://www.mendix.com/blog/layouts-have-types/) を参照してください。

#### 6.1.3 コンテキストを適用 & コンテキストから削除する

参照セレクターのコンテキスト **** と **コンテキストから削除** オプションを適用する データグリッドとテンプレートグリッドのデータソースは Mendix バージョン 5 で非推奨になりました。 9、そして、彼らは削除されました。 これで、それらを使用した場所に一貫性のエラーが表示されます。 代わりに XPath 制約を使用することをお勧めします。

### 6.2 削除されたクライアント API

* `mxui/dom.{p,div,span...}` と `mxui/dom.builder` は `mxui/dom.create`
* `MxMetaObject.isNumber` と `MxObject.isNumber` が `isNumeric` メソッドに置き換えられました
* `mxui/dom.{copyChildren,insertBefore,insertAfter}` はプレーン `dom` API の使用を支持して削除されました
* `mx.ui.hideLogin` が `mx.ui.showLogin` で返されるオブジェクトの `hide` に置き換えられました
* `mx.login` の署名が `mx.login(ユーザー名、パスワード、onLoginSucceed、onLoginFailure) に変更されました`
* `_WidgetBase.resume`, `_WidgetBase.suspend`, および `_FormBase.startup` は効果がなかったため削除されました

### 6.3 ランタイム機能を削除しました

#### 6.3.1 非推奨クラスを削除しました

| クラス名                                                                       | 代替インターフェイス/クラス                                                         |
| -------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `com.mendix.modules.exportmanager.Excel.ExcelCellStyle`                    | `com.mendix.modules.exportmanager`, `.interfaces.excel.IExelCellStyle` |
| `com.mendix.modules.exportmanager.Excel.ExcelCell`                         | `com.mendix.modules.exportmanager`, `.interfaces.excel.IExelCell`      |
| `com.mendix.modules.exportmanager.Excel.ExcelColumn`                       | `com.mendix.modules.exportmanager`, `.interfaces.excel.IExelColumn`    |
| `com.mendix.modules.exportmanager.Excel.ExcelGrid`                         | `com.mendix.modules.exportmanager`, `.interfaces.excel.IExelGrid`      |
| `com.mendix.systemwideinterfaces.core.Feedback`                            | `com.mendix.systemwideinterfaces.core.IFeedback`                       |
| `com.mendix.core.conf.ConfigurationImpl`                                   | `com.mendix.core.conf.Configuration`                                   |
| `com.mendix.core.component.InternalCore`                                   | `com.mendix.Core`                                                      |
| `com.mendix.core.conf.ConfigValueChecker`                                  | -                                                                      |
| `com.mendix.core.conf.UserPermissions`                                     | -                                                                      |
| `com.mendix.core.conf.CertificateProcessor`                                | -                                                                      |
| `com.mendix.core.conf.HashAlgorithmType`                                   | -                                                                      |
| `com.mendix.systemwideinterfaces.connectionbus.ConnectionBusException`     | -                                                                      |
| `com.mendix.systemwideinterfaces.connectionbus.DBMSType`                   | -                                                                      |
| `com.mendix.systemwideinterfaces.connectionbus.JDBCDataStoreConfiguration` | -                                                                      |
| `com.mendix.systemwideinterfaces.core.IMendixEnum`                         | `com.mendix.core.objectmanagement.member.MendixEnum`                   |

#### 6.3.2 削除された定数

| クラス名                                                                         | 代替                                                                                                                                                                                       |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `com.mendix.systemwideinterfaces.HandlerConstans`                            | -                                                                                                                                                                                        |
| `com.mendix.systemwideinterfaces.SystemModuleConstans`                       | -                                                                                                                                                                                        |
| `com.mendix.core.conf.CoreConstant`                                          | -                                                                                                                                                                                        |
| `com.mendix.core.conf.AdminActionConstans`                                   | -                                                                                                                                                                                        |
| `com.mendix.core.conf.Tokens`                                                | -                                                                                                                                                                                        |
| `com.mendix.externalinterface.connector.RequestHandler.XAS\_SESSION\_ID` | RequestHandler で使用: `com.mendix.externalinterface.connector.RequestHandler.getSessionCookieName()`<br> 定数として使用: `com.mendix.core.Core.getConfiguration().getSessionIdCookieName()` |

#### 6.3.3 削除されたメソッド

##### 6.3.3.1 com.mendix.core.Configuration

| メソッド名                                                                       | 代替 |
| --------------------------------------------------------------------------- | -- |
| `registerConfigurationSetting(文字列名、文字列デフォルト値)`                              | -  |
| `getValue(String name)`                                                     | -  |
| `setValue(文字列の名前、文字列の値)`                                                    | -  |
| `updateConfiguration(JSONObject params, boolean overwrite)`                 | -  |
| `getUploadedFilesPath()`                                                    | -  |
| `useLDAPAuthentication()`                                                   | -  |
| `getReadCommittedSnapshot()`                                                | -  |
| `getMaxThreadsPerDataStoreRequest()`                                        | -  |
| `getLogMinDurationQuery()`                                                  | -  |
| `mustReturnOnlyNecessaryDDLCommands()`                                      | -  |
| `setReturnOnlyNecessaryDDLCommands(boolean returnOnlyNecessaryDDLCommands)` | -  |
| `getConstantValue(Object component, String key)`                            | -  |
| `getDefaultHashAlgorithm()`                                                 | -  |

##### 6.3.3.2 com.mendix.modules.exportmanager.excel.Excel.ExcelExporter

| メソッド名                                                                                                                                                                                                                | 代替                                                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `generateWorkbook(LocalComponent コンポーネント, IContext context, List<IExcelGrid> grids)`                                                                                                                           | -                                                                                                                                                                  |
| `generateXLS(com.mendix.core.component.LocalComponent コンポーネント, IContext context, IMendixObject fileObject, String fileName, List<IExcelGrid> grids)`                                                           | `generateXLS(IContext context, IMendixObject fileObject, String fileName, List<IExcelGrid> grids)`                                                           |
| `generateXLS(com.mendix.core.component.LocalComponent コンポーネント, IContext context, IMendixObject fileObject, String fileName, List<String> oqlQueries, boolean autoSizeColumns, List<String> headerNames)` | `generateXLS(IContext context, IMendixObject fileObject, String fileName, List<String> oqlQueries, boolean autoSizeColumns, List<String> headerNames)` |

##### 6.3.3.3 From com.mendix.systemwideinterfaces.core.IContext

| メソッド名                                                             | 代替                  |
| ----------------------------------------------------------------- | ------------------- |
| `setCurrentIdentifier(IMendixIdentifier currentIdentifier)`       | -                   |
| `setContextObjects(List<IMendixIdentifier> contextObjects)` | -                   |
| `setSudo(boolean sudo)`                                           | -                   |
| `getSudoContext()`                                                | `createSudoClone()` |

##### 6.3.3.4 From com.mendix.core.Core

| メソッド名                                                   | 代替                                                             |
| ------------------------------------------------------- | -------------------------------------------------------------- |
| `callWebservice()`                                      | 代わりにマイクロフローで REST コールアクションを使用します。                              |
| `importXmlStream()`                                     | 代わりに `com.mendix.core.integration().importStream()` を使用してください。 |
| `getComponent().runtime().about().get("model_version")` | `getModelVersion()`                                            |

##### 6.3.3.5 com.mendix.systemwideinterfaces.core.ISession

状態は Mendix 7 でクライアントに移動され、そのため以下のメソッドは廃止されました。

| メソッド名                   | 代替 |
| ----------------------- | -- |
| `保持する`                  | -  |
| `リリース`                  | -  |
| `addToClientRoots`      | -  |
| `removeFromClientRoots` | -  |
| `getClientRoots`        | -  |
| `getJavaActionRoot`     | -  |
| `getData`               | -  |

##### 6.3.3.6 その他

| メソッド名                                                                  | 代替                                                                |
| ---------------------------------------------------------------------- | ----------------------------------------------------------------- |
| `com.mendix.m2ee.api.IMxRuntimeRequest.getOriginalRequest()`           | `com.mendix.m2ee.api.IMxRuntimeRequest.getHttpServletRequest()`   |
| `com.mendix.m2ee.api.IMxRuntimeResponse.getOriginalResponse()`         | `com.mendix.m2ee.api.IMxRuntimeResponse.getHttpServletResponse()` |
| `com.mendix.systemwideinterfaces.core.meta.IMetaObject.getComponent()` | -                                                                 |
| `com.mendix.systemwideinterfaces.core.ISession.getComponent()`         | -                                                                 |

#### 6.3.4 Mendix 7にプロジェクトを移行する際のコンパイル問題

Mendix 7の非推奨クラスとメソッドを削除すると、プロジェクトをMendix 7に移行した後にコンパイルエラーが発生する可能性があります。 削除された非推奨コードについては、上記の代替を使用してください。

#### 6.3.5 SystemModuleConstans

これらは主にシステムエンティティの名前またはその属性名を参照するために使用されます。 このような名前は、対応するシステムプロキシ経由でも利用できます。

例えば、 `SystemModuleConstats.FILE_DOCUMENT_NAME` を `FileDocument` プロキシに置き換えることができます:

```
import com.mendix.systemwideinterfaces.SystemModuleConstants;

private final String FILE_DOCUMENT_NAME = SystemModuleConstants.FILE_DOCUMENT_NAME;
```

置き換える必要があります：

```
import system.proxies.FileDocument.MemberNames;

private final String FILE_DOCUMENT_NAME = MemberNames.toString();
```

here `MemberNames` は `FileDocument` プロキシクラスで定義された列挙型です。

#### 6.3.6 移動されたパッケージ

| クラス名            | 代替インターフェイス                            |
| --------------- | ------------------------------------- |
| `org.json.\*` | `com.mendix.thirdparty.org.json.\*` |

これは、 `org.json` ライブラリのMendixバージョンと他のJSONライブラリとの間の潜在的な名前空間の衝突を避けるために必要です。

#### 6.3.7 Mendix 7への移行時のランタイム問題

Mendix 7のJavaライブラリは、インストールパッケージに同梱されていません。 これにより、各プロジェクトの依存関係管理が改善されますが、移行後に実行時にエラーが発生することもあります(例えば、 `NoClassDefFoundError`)。 ですから、移行されたプロジェクトの `userlib` ディレクトリに必要なライブラリがすべて含まれていることを確認することが重要です。 Mendix 7では、実行時に各ライブラリの1つのバージョンしか存在できないことも注目に値します。 つまり、1つのライブラリに複数のバージョンがある場合、最新バージョンが使用され、残りのバージョンが無視されるということです。

### 6.4 データストレージ機能の削除

#### 6.4.1 削除されたメソッド

| パッケージ名                                                        | メソッド名                  | 代替                     |
| ------------------------------------------------------------- | ---------------------- | ---------------------- |
| `com.mendix.systemwideinterfaces.connectionbus.data.IDataRow` | `getPrimaryKeyValue()` | `getValue(context, 0)` |

##### 6.4.1.1 使用例

`IDataRow.getPrimaryKeyValue()`

Mendix 6.xのgetPrimaryKeyValue()メソッドを使用してMendixObjectを取得しましょう。

`リスト<? extends IDataRow> dataRows = retrieveOQLDataTable.getRows();`<br> `IDataRow dataRow = dataRows.get(0);`<br> `IMendixIdentifier mendixIdentifier = dataRow.getPrimaryKeyValue();`<br> `IMendixObject mendixObj = Core.retrieveId(context, mendixIdentifier);`<br>

Mendix 7.x で MendixObject を取得する同様のアプローチは、次のとおりです。

 `リスト<? extends IDataRow> dataRows = retrieveOQLDataTable.getRows();`<br> `IDataRow dataRow = dataRows.get(0);`<br> `IMendixIdentifier mendixIdentifier = dataRow.getValue(context, 0);`<br> `IMendixObject mendixObj = Core.retrieveId(context, mendixIdentifier);`<br>
