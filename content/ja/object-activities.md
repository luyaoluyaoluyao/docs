---
title: "オブジェクトのアクティビティ"
parent: "アクティビティ"
menu_order: 10
tags:
  - "studio pro"
  - "マイクロフロー"
  - "オブジェクト"
---

## 1つの紹介

Mendix プラットフォームで作業する場合、エンティティのオブジェクトは常に操作されます。 これは、ページの [データ ウィジェット](data-widgets) 内で暗黙的に発生するか、マイクロフローやナノフローのアクティビティを明示的に使用します。

The activities in this section of the microflow and nanoflow toolbox generally work on single objects, however **commit object(s)**, **delete object(s)**, and **retrieve** also work on lists of objects. リストで動作する他のアクティビティについては、 [リストアクティビティ](list-activities) を参照してください。

このドキュメントで説明されているアクティビティは、 **ツールボックス** の **Object Activities** セクションにあります:

{{% image_container width="40%" %}}
![オブジェクトアクティビティツールボックス](attachments/object-activities/object-activities-toolbox.png)
{{% /image_container %}}

以下は、マイクロフローまたはナノフローで使用できるオブジェクトアクティビティです。

* [キャストオブジェクト](cast-object) *(マイクロフローのみ)* – 一般化されたオブジェクト型から特殊なオブジェクト型に変更します。
* [Change object](change-object) – changes the members of an object
* [Commit objects(s)](committing-objects) - 永続性のあるエンティティのオブジェクトをデータベースに格納するか、または永続性のないエンティティのオブジェクトをメモリに格納してロールバックできるようにします。
* [オブジェクトの作成](create-object) – オブジェクトを作成
* [オブジェクトの削除](deleting-objects) *(microflowのみ)* – アクティビティは1つ以上のオブジェクトを削除します
* [取得](retrieve) – エンティティの 1 つまたは複数のオブジェクトを取得
* [Rollback object](rollback-object) - オブジェクトに加えられた変更を元に戻す

## 2 続きを読む

* [アクティビティ](アクティビティ)