---
title: "SIG–Mendix パフォーマンスの件名"
category: "Mendix Runtime"
---

## 1つの紹介

このドキュメントでは、Mendix Runtime環境で使用される通信パターンを、いくつかの典型的なアプリケーションユースケースで概説しています。

このドキュメントの目標は次のとおりです。

*   通信効率に関するMendix Runtime環境の品質を評価するための現在の情報
*   設計上の意思決定が通信効率とパフォーマンスに及ぼす影響を決定するための情報

この文書は、Mendixアプリケーションの通信性能効率を評価するためにSIGが必要とする欠落した情報に対処するために書かれました。 このドキュメントの最後のセクションでは、この主題に関するSIGのスコアリングと、このドキュメントがこれらの要件に対応する方法について概説しています。

## 2 Mendixランタイム環境におけるコミュニケーションの概要

Mendix プラットフォームは以下のコンポーネントで構成されています。

*   Mendix Platform – アプリケーションの設計、構築、展開、管理のためのサービスとして完全に統合されたアプリケーション プラットフォーム (aPaaS)

*   Developer Portal – アプリの設計、開発、デプロイのためのウェブベースのコラボレーション環境 ユーザーと環境の管理、ワンクリックでクラウドへのアプリのデプロイ、パフォーマンスの管理と監視

*   Marketplace – アプリ開発を加速するための数百の公開されたビルディングブロックを備えたポータル

*   Mendix Modeler – Mendix Platformのマルチユーザーモデリングスタジオ
*   Team Server - アプリケーションモデルのバージョンを管理するための中央リポジトリ
*   ランタイム環境 – サーバ部品 (Mendix Runtime) とクライアント部品 (Mendix Client) を使用してアプリケーションを実行します。
*   ビルド - モデル、スタイルシート、カスタムJavaクラスなどのアーティファクトからデプロイパッケージを作成します
*   MxID – OpenID 標準を適用するユーザー管理およびプロビジョニングサービス

このドキュメントの焦点は、Mendix Runtime環境、より具体的には以下の部分間のコラボレーションです。

*   Mendix Client – ユーザーのブラウザで動作する JavaScript クライアント
*   Mendix Runtime – Java/Scalaランタイムはサーバー上で実行され、マイクロフローロジック、ビジネスルール、および永続オブジェクトの実行を担当します
*   RDBMS – データが永続する場所
*   オプションで、水平方向にスケーリングされたランタイムインスタンス間で状態を共有するための状態ストア

これらのコンポーネント間の通信は以下のように動作します。

*   Mendix クライアントは 2 種類のリクエストを発行します。
    *   ページ、スタイルシート、ウィジェット、画像などの静的リソース。
    *   データとデータを必要とするかもしれないロジック上のCRUDコマンドを含むアプリケーションデータ関連通信
*   Mendix Runtime は、JDBC ライブラリによって処理される SQL ステートメントを使用して異なる RDBMS と通信します。
    *   アプリケーションデータは、RDBMSのERモデルに格納されています

## 3つの基本CRUD 通信パターン

ほとんどのMendixアプリケーションのコアにはCRUDパターンのバリエーションが含まれています。Mendixエンティティに保存されたデータの作成、読み取り、更新、および削除です。

この基本的なシナリオは、以下の2つのページを使用してMendixでモデル化できます。

* 以下のような特定のエンティティのデータテーブルを表示する概要ページです。

  ![](attachments/19202918/19399028.png)

* エンティティの特定のオブジェクトを以下のように編集できる詳細ページ:

  ![](attachments/19202918/19399029.png)

  * このページは、新規および編集ボタンを使用して最初のページからアクセスできます。


次のセクションでは、これらのページを実行する際のアクションの概要を示します。 前述のように、このパターンは多くのMendixアプリケーションで見ることができます。 しかし、正確なランタイム結果は、Mendix Modelerを使用してアプリケーションを構築する際に取られる多くの詳細と設計の決定に依存します。 より高度なデータモデルとページは、より多くの(複雑な)クエリをもたらします。

### 3.1 オブジェクトテーブルを表示するために必要な読み取りオブジェクト

オブジェクトの表を表示するには、次のステップで構成されています。

1. ページの定義を取得します (ブラウザーによってまだキャッシュされていない場合)。
2. ページに表示するデータを取得します。
3. ページを更新中です。

基本的なシーケンス図は次のようになります。

![](attachments/19202918/19399030.png)

Mendix Client は、REST ライクなプロトコルを使用して、Mendix Runtime からデータを要求します。 以下の例は、Employees エンティティからオブジェクトを要求した場合のこれがどのように見えるかを示しています。

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
   "context":[
   ],
   "profiledata":{
      "204ee5ad0c056a0":15
   }
}
```

XPath 条件式は、必要なデータを示します。 アプリケーションが要求するエンティティ、またはエンティティの属性に過ぎません。

スキーマセクションを使用して、必要なデータ(属性とレコード数)に関する追加の制限を指定することができます。 このアプローチにより、Mendix Runtime と Mendix Client 間で転送されるデータ量が最小限に抑えられます。

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

表示されるデータとドメインモデル(継承と行または属性セキュリティの使用)によって異なります。 検索ではクエリが増えたりwhere節が増えたりするかもしれません

Mendix Runtime の Mendix クライアントへの応答は次のとおりです。

```json
{"count":2,"mxobjects":[{"objectType":"MyFirstModule.Employee","guid":"281474976710757","attributes":{"Firstname":{"value":"peter1"},"DateOfBirth":{"value":-315622800000},"Jobtitle":{"value":"sales"},"Department":{"value":"sales"},"Lastname":{"value":"jones"&#125;&#125;},{"objectType":"MyFirstModule.Employee","guid":"281474976710657","attributes":{"Firstname":{"value":"piet"},"DateOfBirth":{"value":476406000000},"Jobtitle":{"value":"consultant"},"Department":{"value":"expert services"},"Lastname":{"value":"jansen"&#125;&#125;}]}
```

### 3.2 新しいオブジェクトを作成

一般的な create-new-object フローは以下の手順で構成されます。

1. 新しいオブジェクトをインスタンス化する (プライマリキーはデータベースによって生成され、Mendix Runtime は PKS のキャッシュを保持します)。
2. 編集フォームを取得します(ブラウザーがまだキャッシュしていない場合)。
3. 更新されたオブジェクトをMendix Runtimeに保存します。
4. 更新されたオブジェクトをデータベースにコミットします。

![](attachments/19202918/19399031.png)

新しいオブジェクトを作成:

```json
{
   "action":"instantiate",
   "params":{
      "objecttype":"MyFirstModule.Employee",
      "preventCache":1455032246146
   },
   "context":[
   ],
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
   "context":[
   ],
   "profiledata":{
      "204ee6970d53960":18
   }
}
```

データベースへの更新をコミット:

```java
{"action":"commit","params":{"guid":"281474976710757"},"context":[],"profiledata":{"204ee6e9b5eddc0":25&#125;&#125;
```

commitによりMendix RuntimeがオブジェクトをRDBMSに保存されます。 コミット前に、データはMendix Runtimeにのみ保存され、パフォーマンスを最適化し、データベースへの影響を最小限に抑えます。

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
2. 編集フォームを取得します(ブラウザーがまだキャッシュしていない場合)。
3. ブラウザで既に利用可能なオブジェクトの値をフォームに表示します。
4. オブジェクトの変更された属性を Mendix Runtime に保存します。
5. データベースからオブジェクトを取得します。
6. オブジェクトの変更を検証します。
7. データベースの変更をコミットします。

![](attachments/19202918/19399032.png)

変更をデータベースに保存します:

```java
{"action":"change","params":{"281474976710757":{"Firstname":"peter1"&#125;&#125;,"context":[],"profiledata":{"204ee8bb633f9a0":25&#125;&#125;
```

これはデータベース上で次のアクションをトリガーします:

*   データベースから元のオブジェクトを取得する
*   実行時にユーザーによって変更された属性を更新する

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

```java
{"action":"commit","params":{"guid":"281474976710757"},"context":[],"profiledata":{"204ee8ca8f775a0":20&#125;&#125;
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
2. Mendix Runtimeに削除リクエストを送信します。
3. Mendix Runtime は削除リクエストを検証します。
4. Mendix Runtime はデータベースからオブジェクトを削除します。
5. データベースの変更をコミットします。
6. 削除が成功したことをクライアントに通知します。
7. データを更新し、ページを更新します。

次のシーケンス図は、一般的な削除シナリオの概要を示しています。

![](attachments/19202918/19399033.png)

オブジェクトを削除:

```java
{"action":"delete","params":{"guids":["281474976710757"]},"context":[],"profiledata":{"204eeae128284c0":323&#125;&#125;
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
{"action":"retrieve_by_xpath","params":{"xpath":"//MyFirstModule.Employee","schema":{"id":"a2916c7c-af2f-4267-a8e9-99604f045861","offset":0,"sort":[["Firstname","asc"]],"amount":20},"count":true,"aggregates":false},"context":[],"releaseids":["281474976710757"],"profiledata":{"204eeb2972550c0":28&#125;&#125;
```

## 4 ビジネスロジックの実行

ビジネスロジックはMendixのマイクロフローを使用してモデル化されます。 次のセクションでは、マイクロフローを含む一般的な流れを示します。

### 4.1 マイクロフローによって取得されたデータのグリッドの表示

ページ上のデータ グリッドは、多くの場合、ドメイン モデル内のエンティティに直接リンクされます。 別の方法として、microflow を使用して、データ グリッドに表示されるオブジェクトのリストを作成する方法があります。

エンティティからすべてのオブジェクトを取得するマイクロフローは、次のようにモデル化できます。

![](attachments/19202918/19399034.png)

この場合、すべてのオブジェクトは1つのリクエストでブラウザに転送されます。 ユーザーは、Mendix Runtime との通信をトリガーすることなく、すべてのオブジェクトをページに移動できます。

このシナリオの高レベルシーケンス図は次のようになります。

![](attachments/19202918/19399035.png)

Mendix Client から Mendix Runtime へ実行される JSON アクション:

```java
{"action":"executeaction","params":{"actionname":"MyFirstModule.GetAllEmployees","applyto":"none"},"context":[],"profiledata":{"204f418ba05e7c0":55&#125;&#125;
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

Mendix Runtime から Mendix クライアントへの応答:

```json
{"actionResult":[{"objectType":"MyFirstModule.Employee","guid":"281474976710657","attributes":{"Firstname":{"value":"piet"},"DateOfBirth":{"value":476406000000},"Jobtitle":{"value":"consultant"},"Department":{"value":"expert services"},"Lastname":{"value":"jansen"&#125;&#125;},{"objectType":"MyFirstModule.Employee","guid":"281474976710957","attributes":{"Firstname":{"value":"wee"},"DateOfBirth":{"value":1454886000000},"Jobtitle":{"value":"ewji"},"Department":{"value":"wew"},"Lastname":{"value":"ewfeew"&#125;&#125;},{"objectType":"MyFirstModule.Employee","guid":"281474976710958
…
}]}
```

## Mendix Runtime Internals 5名

CRUD シナリオの説明に見られるように、Mendix Platform は、アプリケーションをさまざまな方法で実行する際の効率を保証します。

*   通信と処理に関与するのはユーザーアクションに必要なデータのみです
*   効率的なトランスポートプロトコルは、異なるプロセス間の通信に使用されます。
    * Mendix Client と Mendix Runtime の間の JSON フォーマット
    * RDBMS通信用のネイティブSQLプロトコル
*   可能であれば、Mendix クライアントで既に利用可能なデータが再利用されます(編集フォームでデータグリッドにフェッチされたデータが再利用される編集シナリオを参照してください)。

### 5.1 データ変換

必要に応じてMendixクライアントとデータベース間でデータが転送されます。 Mendix Client からデータベースへのフルサークルを行う場合、次の変換が適用されます。

*   フォームにユーザーが入力したデータは JavaScript オブジェクトに保存されます
*   Mendix Runtime との通信のため、JavaScript オブジェクトは JSON にシリアライズされます。
*   Mendix Runtime は JSON オブジェクトを Java MxObjects に変換します
*   MxObject プロパティは、SQL クエリで必要に応じて SQL ステートメントのパラメーターにバインドされます。
*   JDBC 結果セットデータはMxObjectsに変換されます
*   Mendix クライアントに送信すると、MxObjects は JSON にシリアライズされます。

### 5.2 状態

拡張性を(水平に)高めるために、Mendix PlatformはMendix Runtimeメモリに保存されている状態を最小限に抑えます。 全体的な戦略は、メモリ内の汚れたオブジェクトのみを持ち、リクエストの最後に他のオブジェクトがクリーンアップされることです。 オブジェクトが変更されている場合、オブジェクトは汚れているとみなされますが、変更は RDBMS にまだ継続されていません。 状態はセッションごとに維持されます。

![](attachments/19202918/19399036.png)

### 5.3 永続性

Mendixは、アプリケーション固有のエンティティモデル(ドメインモデル)の翻訳を自動的にRDBMS特定のERモデルに処理します。 CRUD シナリオの読み取り部分に示されているように、データの取得は、わかりやすいように XPath 構文により表現されます。 例えば、すべての従業員オブジェクトを取得するには、以下の XPath を使用することができます:

`//MyFirstModule.Employee`

この XPath 条件式は、データベースクエリへの多数のステップで処理されます:

1. XPath は内部の OQL 構文に変換されます。 OQL は SQL に似ていますが、テクニカルテーブルではなく、アプリケーション ドメイン モデル エンティティの観点からアプリケーションデータを表現します。
2. ドメインモデルで指定されている OQL ステートメントに追加され、必要な式が追加されます (たとえば、スーパークラスのエンティティからの情報を追加するなど)。
3. ドメインモデルのセキュリティ制約は、OQL ステートメントに適用されます。
4. OQLはSQLに変換され、設定されたRDBMSでJDBCを介して実行されます。

### 5.4 スケーラビリティー

Mendix Runtime は単一のプロセスとして実行することも、水平方向にスケーリングすることで、より多くの同時実行ユーザーを容易にし、可用性を向上させることもできます。 このシナリオでは、複数の Mendix Modelerインスタンスが実行されています。 これらのインスタンスは独立して実行され、プロセス間の通信は行われません。

#### 5.4.1 シングルインスタンス

単一のインスタンス内で、Scala Akka アクターモデルは、Mendix Runtime のすべての処理を効率的に処理するために使用される。 同時実行にアクターモデルを使用すると、次のような利点があります。処理できる同時実行ユーザーの数は、利用可能なスレッドの量によって制限されません。 スレッドはリクエストごとに割り当てられるのではなく、責任処理によって割り当てられます。

Mendix Runtime によって受信された Mendix Client リクエストを処理するには、必要なアクションが Akka アクターに送信されます。 このアクターには専用のスレッドプールがあります。 すべての(マイクロフロー)アクションは、アクションディスパッチャアクタに別のメッセージによって処理されます。 これにより、ブロックアクションのスレッドの使用が最適化されます。 例えば、マイクロフローのアクションの一部が外部のWebサービスを呼び出し、応答を待つのをブロックされている場合。 これは、HTTP リクエストハンドラではなく、アクションディスパッチャのスレッドプールにのみ影響します。

#### 5.4.1 マルチインスタンス

水平方向にスケーリングされたシナリオで実行する場合、Mendix Runtime状態はRedis状態を介して調整されます。 すべてのリクエストが終わると、セッションの汚れたオブジェクトはすべてRedisステートストアに書き込まれます。 新しいリクエストが開始されると、この状態は Redis 状態から読み込まれます。

![](attachments/19202918/19399037.png)
