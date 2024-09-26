---
title: "ドメインモデルの整合性エラー"
category: "整合性エラー"
description: "Mendix Studioでドメインモデルの一貫性エラーと修正方法について説明します。"
tags:
  - "スタジオ"
  - "整合性エラー"
  - "エラー"
  - "ドメインモデル"
---

## 1つの紹介

このドキュメントでは、Mendix Studio でドメインモデルを構成する際に発生する最も一般的な一貫性エラーを解決する方法を説明します。 ドメインモデルの詳細については、 [Domain Model](domain-models) を参照してください。

一貫性エラーの例は、2つのエンティティに対して同じ名前を持つことです。

## 2 ドメインモデルの整合性エラー

ドメインモデルの設定時に発生する最も一般的なエラーについては、以下の表を参照してください。

| エラーコード | チェックパネルのテキスト                                                                                        | エラーの原因                                                                                                                                                                                                                                                                                                | 修理方法                                                                         |
| ------ | --------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| CE0001 | 持続可能エンティティと持続不可能なエンティティとの関連付けは、持続不可能なエンティティで開始し、所有者が「デフォルト」である必要があります。                              | 持続可能エンティティと非持続可能エンティティの間の関連を作成しました そして、その関連は持続可能エンティティから非持続可能エンティティに引き出されます(したがって、関連の所有者は持続可能エンティティです)。 永続的なエンティティはデータベースに保存され、非永続的なエンティティはメモリに保存されます。 メモリからデータベースまでを指すことはできますが、他の方法はありません。 For more technical information, see [Persistability](/refguide/persistability) in the *Studio Pro Guide*. | 関連付けプロパティを開き、関連の方向を交換して、関連の所有者を変更します。 または、エンティティプロパティのいずれかのエンティティの永続性を変更します。 |
| CE0017 | 無効 [削除ビヘイビア](domain-models-association-properties#delete-behavior)。                                 | このエラーは、関連付け内のエンティティの削除動作が矛盾している場合に発生します。 このエラーが発生した場合の詳細については、 [2.1 動作一貫性エラーの削除と修正方法](#delete-behavior) を参照してください。                                                                                                                                                                                    | このエラーを修正する方法については、 [2.1 動作一貫性エラーの削除と修正方法](#delete-behavior) を参照してください。       |
| CE0021 | {attribute type} 型の属性は持続可能エンティティでのみサポートされています。                                                      | 永続性のないエンティティは、AutonumberまたはBinary型の属性を持っています。 これらのタイプの属性はデータベースに保存する必要があります。                                                                                                                                                                                                                          | プロパティ内の対応するオプションを有効にするか、属性タイプを変更することで、エンティティを持続可能にします。                       |
| CE0065 | モジュール {name of the entity} の名前 {name of the module}が重複しています。 エンティティ、関連付け、列挙は名前を共有できません。             | ドメインモデルに同じ名前を持つ複数のエンティティがあります。                                                                                                                                                                                                                                                                        | いずれかのエンティティの名前を変更します。すべてのエンティティ名は一意でなければなりません。                               |
|        | 選択した属性 {name of attribute} は曖昧です。 複数のエンティティ {name of attribute} を持つことは許可されていません。                    | ドメインモデルに同じ名前を持つ複数のエンティティがあります。 これらの複製されたエンティティの属性にはエラーがあります                                                                                                                                                                                                                                           | いずれかのエンティティの名前を変更します。すべてのエンティティ名は一意でなければなりません。                               |
|        | 選択されたアソシエーション {name of the association} は曖昧です。 複数のアソシエーションを持つことは許可されていません {name of the association} | 複数のドメインモデルに1つと同じ名前に関連付けられています。                                                                                                                                                                                                                                                                        | 関連のいずれかの名前を変更します。すべての関連名は一意である必要があります。                                       |

### 2.1 動作一貫性エラーとそれらを修正する方法を削除{#delete-behavior}

 削除動作に接続された一貫性エラーは、次の場合に発生する可能性があります:

*  Delete behavior of an entity the association starts from is set to *Delete {name of entity} object(s) as well* and the delete behavior of an entity the association points to is set to *Delete {name of entity} object only if it is not associated with {name of other entity} object(s)*

    ![行動例を削除する](attachments/consistency-errors-domain-model/delete-behavior-error-example1.png)

*  関連付けが開始するエンティティの動作を削除するには、 * {name of entity} オブジェクトを {name of other entity} オブジェクトに関連付けられていない場合にのみ削除します。* エンティティの削除動作と関連付けポイントが * {name of entity} オブジェクトも削除します*

    ![挙動エラー例2 を削除](attachments/consistency-errors-domain-model/delete-behavior-error-example2.png)

*  関連付け中の両方のエンティティの削除動作は *削除 {name of entity} オブジェクトが {name of other entity} オブジェクトに関連付けられていない場合にのみ設定されています*

    ![行動例3 を削除](attachments/consistency-errors-domain-model/delete-behavior-error-example3.png)

次のいずれかの方法で、削除ビヘイビアエラーを修正できます。

* If  you set delete behavior of one entity to *Delete {name of entity} object only if it is not associated with {name of other entity} object(s)*, set delete behavior of another entity to *Keep {name of entity} object(s)*.
* 両方のエンティティの削除動作を * {name of entity} オブジェクトを保持* に設定する
* 両方のエンティティの削除動作を * {name of entity} オブジェクトも削除* に設定します。

削除動作の詳細については、 [関連プロパティ](domain-models-association-properties#delete-behavior) の *Delete Behavior* セクションを参照してください。

## 3 続きを読む

* [ページ整合性エラー](consistency-errors-pages)
* [ナビゲーション一貫性エラー](consistency-errors-navigation)
* [マイクロフローの整合性エラー](consistency-errors-microflows)
* [チェック](チェック)