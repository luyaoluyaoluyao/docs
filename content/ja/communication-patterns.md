---
title: "Mendix Runtime の通信パターン"
category: "Mendix Runtime"
tags:
  - "studio pro"
  - "Mendix Runtime"
  - "コミュニケーション"
  - "ランタイムサーバー"
  - "Mendix クライアント"
---

## 1つの紹介

このドキュメントでは、Mendix Runtime環境で使用される通信パターンを、いくつかの典型的なアプリケーションユースケースで概説しています。

このドキュメントの目的は以下の情報を提示することです:

*   通信効率に関するMendix Runtimeの品質の評価
*   意思決定が通信効率とパフォーマンスに及ぼす影響を判断し

## 2 Mendixランタイムにおけるコミュニケーションの概要

Mendix プラットフォームは以下のコンポーネントで構成されています。

*   Mendix Platform – アプリケーションの設計、構築、展開、管理のためのサービスとして完全に統合されたアプリケーション プラットフォーム (aPaaS)
*   Developer Portal – アプリの設計、開発、デプロイのためのウェブベースのコラボレーション環境。 ユーザーと環境の管理、ワンクリックでクラウドへのアプリのデプロイ、パフォーマンスの管理と監視
*   Marketplace – アプリ開発を加速するための数百の公開ブロックを持つポータル
*   Mendix StudioとStudio Pro – Mendix Platformのマルチユーザーモデリングスタジオ
*   Team Server - アプリケーションモデルのバージョンを管理するための中央リポジトリ
*   Mendix Runtime – サーバー・パーツ ( [Runtime Server](runtime-server)) とクライアント・パーツ ([Mendix Client](mendix-client) ) を使用してアプリケーションを実行します
*   ビルド - モデル、スタイルシート、カスタムJavaクラスなどのアーティファクトからデプロイパッケージを作成するプロセス
*   MxID – OpenID 標準を適用するユーザー管理およびプロビジョニングサービス

このドキュメントの焦点は、Mendix Runtime、より具体的には以下の部分間のコラボレーションです。

*   [Mendix Client](mendix-client) – ユーザのデバイス上で動作する React, React Native, JavaScript クライアント
*   [Runtime Server](runtime-server) – サーバー上で実行されるJava/Scalaランタイム。マイクロフローロジック、ビジネスルール、および永続オブジェクトの実行を担当する
*   RDBMS – データが永続する場所

これらのコンポーネント間の通信は以下のように動作します。

*   Mendix クライアントは 2 種類のリクエストを発行します。
    *   ページ、スタイルシート、ウィジェット、画像などの静的リソース。
    *   データとデータを必要とするかもしれないロジック上のCRUDコマンドを含むアプリケーションデータ関連通信
*   Runtime Serverは、JDBC ライブラリが処理する SQL ステートメントを使用して、異なる RDBMS と通信します。
    *   アプリケーションデータは、RDBMSのERモデルに格納されています

## 3つの基本CRUD 通信パターン

ほとんどのMendixアプリケーションのコアは、Mendixエンティティに格納されているデータのCRUD(create、read、update、delete)パターンのバリエーションを含みます。

*Employee* エンティティを使用した基本的なシナリオは、次の 2 つのページを使用してMendix でモデル化できます。

* 以下のような特定のエンティティのデータテーブルを表示する概要ページです: ![](attachments/communication-patterns/19399028.png)
* エンティティの特定のオブジェクトを以下のように編集できる詳細ページ: ![](attachments/communication-patterns/19399029.png)
   * この詳細ページは、新規および編集ボタンを使用して最初のページからアクセスできます。

次のセクションでは、これらのページを処理する際のアクションの概要を示します。 前述のように、このパターンは多くのMendixアプリケーションで見ることができます。 しかし、正確な実行結果は、アプリケーションの構築中に行われる多くの詳細と設計上の決定に依存します。 より高度なデータモデルとページは、より多くの(そしてより複雑な)クエリをもたらします。

### 3.1 オブジェクトテーブルを表示するために必要なオブジェクトを読み込みます。

オブジェクトの表を表示するには、次のステップで構成されています。

1. ページの定義を取得します (すでにキャッシュされている可能性があります)。
2. ページに表示するデータを取得します。
3. ページを更新中です。

基本的なシーケンス図は次のようになります。

![](attachments/communication-patterns/19399030.png)

Mendix Clientは、Runtime Serverからデータを要求するためにRESTライクなプロトコルを使用します。 以下の例は、Employee エンティティからオブジェクトを要求した場合のこれがどのように見えるかを示しています。

```json
{
   "action":"retrieve_by_xpath",
   "params":{
      "xpath":"//MyFirstModule.Employee",
      "schema":{
         "id":"a2916c7c-af2f-4267-a8e9-99604f045861",
         "offset":0,
         "sort":[
            [
               "Firstname",
               "asc"
            ]
         ],
         "amount":20
      },
      "count":true,
      "aggregates":false
   },
   "context":[],
   "profiledata":{
      "204ee5ad0c056a0":15
   }
}
```

XPath 条件式は、必要なデータを示します。 これはエンティティのデータを含むオブジェクト、またはアプリケーションで必要に応じてオブジェクトの一部の属性にすぎません。

スキーマセクションを使用して、必要なデータ(どの属性とオブジェクトの数)に関する追加の制限を指定することができます。 このアプローチにより、Runtime ServerとMendixクライアント間で転送されるデータ量が最小限に抑えられます。

アクションを取得すると、2つのSQLクエリになります。1つはデータを取得するクエリ、もう1つはオブジェクトの合計数を取得するクエリです。

```sql
 SELECT "myfirstmodule$employee"."id",
 "myfirstmodule$employee"."dateofbirth",
 "myfirstmodule$employee"."department",
 "myfirstmodule$employee"."firstname",
 "myfirstmodule$employee"."jobtitle",
 "myfirstmodule$employee"."lastname"
 FROM "myfirstmodule$employee"
 ORDER BY "myfirstmodule$employee"."firstname" ASC,
 "myfirstmodule$employee"."id" ASC LIMIT 20
 SELECT COUNT(*)
 FROM "myfirstmodule$employee"
```

表示されるデータとドメインモデルに応じて、(例えば、オブジェクトや属性に適用されるセキュリティ) または、一般化および専門化をサポートするために継承を使用すると、取得により多くのクエリまたは追加のWHERE条項が発生する可能性があります。

Mendix クライアントに対するRuntime Serverの応答は以下のとおりです。

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

### 3.2 新しいオブジェクトを作成

一般的な create-new-object フローは以下の手順で構成されます。

1. 新しいオブジェクトをインスタンス化する (プライマリキーはデータベースによって生成され、ランタイムサーバーはPKSのキャッシュを保持します)。
2. 編集/新規ページを表示します (既にキャッシュされている可能性があります)。
3. 更新されたオブジェクトをRuntime Serverに保存します。
4. 更新されたオブジェクトをデータベースにコミットします。

![](attachments/communication-patterns/19399031.png)

新しいオブジェクトを作成:

```json
{
   "action":"instantiate",
   "params":{
      "objecttype":"MyFirstModule.Employee",
      "preventCache":1455032246146
   },
   "context":[],
   "profiledata":{
      "204ee68c92aea60":27
   }
}
```

オブジェクトをデータベースに保存:

```json
{
   "action":"change",
   "params":{
      "281474976710757":{
         "Firstname":"peter",
         "Lastname":"jones",
         "Jobtitle":"sales",
         "Department":"sales",
         "DateOfBirth":-315622800000
      }
   },
   "context":[],
   "profiledata":{
      "204ee6970d53960":18
   }
}
```

データベースへの更新をコミット:

```json
{
   "action":"commit",
   "params":{
      "guid":"281474976710757"
   },
   "context":[],
   "profiledata":{
      "204ee6e9b5eddc0":25
   }
}
```

コミットにより、Runtime ServerはオブジェクトをRDBMSに保存します。 コミットの前に、データはRuntime Serverにのみ保存され、パフォーマンスを最適化し、データベースへの影響を最小限に抑えます。

```sql
 INSERT INTO "myfirstmodule$employee" ("id",
 "firstname",
 "dateofbirth",
 "jobtitle",
 "department",
 "lastname")
 VALUES (?,
 ?,
 ?,
 ?,
 ?,
 ?)
```

### 3.3 既存のオブジェクトを編集

一般的な編集-既存オブジェクトフローは以下の手順で構成されます。

1. オブジェクトページ(概要ページ)のテーブルでオブジェクトを選択します。
2. 編集/新規ページを表示します (既にキャッシュされている可能性があります)。
3. ブラウザで表示されているページに既に利用可能なオブジェクトの値を表示します。
4. オブジェクトの変更された属性を Runtime Server に保存します。
5. データベースからオブジェクトを取得します。
6. オブジェクトの変更を検証します。
7. データベースの変更をコミットします。

![](attachments/communication-patterns/19399032.png)

変更をデータベースに保存します:

```json
{
   "action":"change",
   "params":{
      "281474976710757":{
         "Firstname":"peter1"
      }
   },
   "context":[],
   "profiledata":{
      "204ee8bb633f9a0":25
   }
}
```

これはデータベース上で次のアクションをトリガーします:

*   データベースから元のオブジェクトを取得する
*   実行時にユーザーが変更した属性を更新します

最初のステップは、エンティティに定義されたすべてのデータビジネスロジックと検証を決定するために必要です。

```sql
 SELECT "myfirstmodule$employee"."id",
 "myfirstmodule$employee"."firstname",
 "myfirstmodule$employee"."dateofbirth",
 "myfirstmodule$employee"."jobtitle",
 "myfirstmodule$employee"."department",
 "myfirstmodule$employee"."lastname"
 FROM "myfirstmodule$employee"
 WHERE "myfirstmodule$employee"."id" = (281474976710857)
```

すべてのバリデーションが正しく実行された場合、クライアントは変更をデータベースに反映できます:

```json
{
   "action":"commit",
   "params":{
      "guid":"281474976710757"
   },
   "context":[],
   "profiledata":{
      "204ee8ca8f775a0":20
   }
}
```

これにより実際のデータベースの更新とコミットがトリガーされます。

```sql
 UPDATE "myfirstmodule$employee"
 SET "dateofbirth" = ?
 WRE "id" = ?
```

### 3.4 既存のオブジェクトを削除

通常の削除フローは以下の手順で構成されています。

1. オブジェクトのテーブル(概要ページ)でオブジェクトを選択します。
2. ランタイムサーバーに削除リクエストを送信します。
3. ランタイムサーバーは削除リクエストを検証します。
4. ランタイムサーバーはデータベースからオブジェクトを削除します。
5. データベースの変更をコミットします。
6. 削除が成功したことをクライアントに通知します。
7. データを更新し、ページを更新します。

次のシーケンス図は、一般的な削除シナリオの概要を示しています。

![](attachments/communication-patterns/19399033.png)

オブジェクトを削除:

```json
{
   "action":"delete",
   "params":{
      "guids":["281474976710757"]
   },
   "context":[],
   "profiledata":{
      "204eeae128284c0":323
   }
}
```

データを実際に削除する前に、ビジネス ロジック、ルール、およびイベントの実行を有効にするオブジェクトを取得します。

```sql
 SELECT "myfirstmodule$employee"."id",
 "myfirstmodule$employee"."firstname",
 "myfirstmodule$employee"."dateofbirth",
 "myfirstmodule$employee"."jobtitle",
 "myfirstmodule$employee"."department",
 "myfirstmodule$employee"."lastname"
 FROM "myfirstmodule$employee"
 WHERE "myfirstmodule$employee"."id" = (281474976710857)
```

データベースからオブジェクトを削除:

```sql
"myfirstmodule$employee" から削除
WHERE "id" = ?
```

データグリッドを更新:

```json
{
   "action":"retrieve_by_xpath",
   "params":{
      "xpath":"//MyFirstModule.Employee",
      "schema":{
         "id":"a2916c7c-af2f-4267-a8e9-99604f045861",
         "offset":0,
         "sort":[["Firstname","asc"]],
         "amount":20
      },
      "count":true,
      "aggregates":false
   },
   "context":[],
   "releaseids":["281474976710757"],
   "profiledata":{
      "204eeb2972550c0":28
   }
}
```

## 4 ビジネスロジックの実行

ビジネスロジックはMendixのマイクロフローを使用してモデル化されます。 次のセクションでは、マイクロフローを含む一般的な流れを示します。

### 4.1 マイクロフローによって取得されたデータのグリッドの表示

ページ上のデータ グリッドは、多くの場合、ドメイン モデル内のエンティティに直接リンクされます。 別の方法として、microflow を使用して、データ グリッドに表示されるオブジェクトのリストを作成する方法があります。

エンティティからすべてのオブジェクトを取得するマイクロフローは、次のようにモデル化できます。

![](attachments/communication-patterns/19399034.png)

この場合、すべてのオブジェクトは1つのリクエストでブラウザに転送されます。 ユーザーは、Runtime Server への通信をトリガーすることなく、すべてのオブジェクトをページに移動できます。

このシナリオの高レベルシーケンス図は次のようになります。

![](attachments/communication-patterns/19399035.png)

MendixクライアントからRuntime ServerへのJSONアクション:

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

データベース上で実行された SQL ステートメント:

```sql
SELECT "myfirstmodule$employee"."id",
"myfirstmodule$employee"."firstname",
"myfirstmodule$employee"."dateofbirth",
"myfirstmodule$employee"."jobtitle",
"myfirstmodule$employee"."department",
"myfirstmodule$employee"."lastname"
FROM "myfirstmodule$employee"
```

Runtime ServerからMendixクライアントへの応答:

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

## Mendix Runtime Internals 5名

CRUD シナリオの説明に見られるように、Mendix Platform は、アプリケーションをさまざまな方法で実行する際の効率を保証します。

*   通信と処理に関与するのはユーザーアクションに必要なデータのみです
*   効率的なトランスポートプロトコルは、異なるプロセス間の通信に使用されます。
    * Mendix Client と Runtime Server の間の JSON フォーマット
    * RDBMS通信用のネイティブSQLプロトコル
*   可能であれば、Mendix クライアントで既に利用可能なデータが再利用されます(編集/新規ページでデータグリッドにフェッチされたデータが再利用される編集シナリオを参照してください)。

### 5.1 データ変換

必要に応じてMendixクライアントとデータベース間でデータが転送されます。 Mendix Client からデータベースへのフルサークルを行う場合、次の変換が適用されます。

*   ユーザーがページに入力したデータは JavaScript オブジェクトに保存されます
*   Runtime Serverとの通信のため、JavaScriptオブジェクトはJSONにシリアライズされます。
*   Runtime Server は JSON オブジェクトを Java MxObjects に変換します
*   MxObject プロパティは、SQL クエリで必要に応じて SQL ステートメントのパラメーターにバインドされます。
*   JDBC 結果セットデータはMxObjectsに変換されます
*   Mendix クライアントに送信すると、MxObjects は JSON にシリアライズされます。

### 5.2 状態

拡張性を容易にするために、Mendix Runtimeはリクエスト間の状態を保持しません。 全体的な戦略は、リクエスト中にメモリ内の汚れたオブジェクトのみを持つことです。 オブジェクトが変更されている場合、オブジェクトは汚れているとみなされますが、変更は RDBMS にまだ継続されていません。

![](attachments/communication-patterns/19399036.png)

### 5.3 永続性

Mendixは、アプリケーション固有のエンティティモデル(ドメインモデル)の翻訳を自動的にRDBMS特定のERモデルに処理します。 CRUD シナリオの読み取り部分に示されているように、データの取得は、わかりやすいように XPath 構文により表現されます。 例えば、すべての従業員オブジェクトを取得するには、以下の XPath を使用することができます:

`//MyFirstModule.Employee`

この XPath 条件式は、データベースクエリへの多くのステップで変換されます:

1. XPath は内部の OQL 構文に変換されます。 OQLはSQLに似ていますが、実際のRDBMSテーブルではなく、アプリケーション領域モデルエンティティの観点からアプリケーションデータを表現します。
2. ドメインモデルで指定されている OQL ステートメントに追加され、必要な式が追加されます (たとえば、スーパークラスのエンティティからの情報を追加するなど)。
3. OQL 文にはドメインモデルのセキュリティ制約が適用されます。
4. OQLはSQLに変換され、設定されたRDBMSでJDBCを介して実行されます。

### 5.4 スケーラビリティー

Runtime Serverは、単一のプロセスとして実行することができます。また、水平方向にスケーリングすることで、より多くの同時実行ユーザーを容易にし、可用性を向上させることができます。 このシナリオでは、複数の Mendix Studio Pro インスタンスが実行されています。 これらのインスタンスは独立して実行され、プロセス間の通信は行われません。

#### 5.4.1 シングルインスタンス

単一のインスタンス内では、Scala Akka アクターモデルを使用して、Runtime Server 内のすべての処理を効率的に処理します。 並行性にアクターモデルを使用すると、次のような利点があります。並行性のあるユーザーの数は、利用可能なスレッド数に制限されません。 スレッドはリクエストごとに割り当てられるのではなく、責任処理によって割り当てられます。

Runtime Serverが受け取ったMendix Clientリクエストを処理するには、必要なアクションはAkkaアクターに送信されます。 このアクターには専用のスレッドプールがあります。 すべての(マイクロフロー)アクションは、アクションディスパッチャアクタに別のメッセージによって処理されます。 これにより、ブロックアクションのスレッドの使用が最適化されます。 例えば、マイクロフローのアクションの一部が外部のWebサービスを呼び出し、応答を待つのをブロックされている場合。 これは、HTTP リクエストハンドラではなく、アクションディスパッチャのスレッドプールにのみ影響します。

#### 5.4.2 マルチインスタンス

Mendix Runtime 状態は Mendix Client に保存されます。 これは、水平方向にスケールされたシナリオで実行する場合に意味します。 すべてのインスタンスはロードバランサの後ろで実行され、リクエストは最も適切などのインスタンスに送信されます。
