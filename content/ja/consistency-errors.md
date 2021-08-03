---
title: "整合性エラー"
menu_order: 70
description: "Mendix Studioの一貫性エラーとそれらを修正する方法について説明します。"
tags:
  - "スタジオ"
  - "整合性エラー"
  - "チェック"
  - "エラー"
---

## 1つの紹介

アプリケーションが常に正しくビルドされていることを確認するために、Mendix Studioはいくつかの一貫性を持っています [アプリを公開する際に](checks) をチェックします。 一貫性チェックが満たされない場合、Studio は **チェック** パネルの一貫性エラーを通知します。 一貫性エラーの表示方法の詳細については、 [チェック](checks#viewing-checks) の *チェックパネル*のformat@@4セクションを参照してください。

アプリを公開する前にエラーを解決する必要があります。 整合性エラーの例として、ページ上のデータビューのentityプロパティを指定しない場合があります。

![](attachments/consistency-errors/data-view-no-entity.png)

Mendix Studioの次のエディタで一貫性エラーが発生する可能性があります:

* ページ (ページエディタの一貫性エラーに関する情報については、 [ページ一貫性エラー](consistency-errors-pages) を参照してください)
* ナビゲーションドキュメント (ナビゲーションの一貫性エラーに関する情報については、 [ナビゲーション一貫性エラー](consistency-errors-navigation) を参照してください)
* マイクロフロー (マイクロフローエディタの一貫性エラーに関する情報については、 [マイクロフロー一貫性エラー](consistency-errors-microflows) を参照してください)

## 2 続きを読む

* [ページ整合性エラー](consistency-errors-pages)
* [ナビゲーション一貫性エラー](consistency-errors-navigation)
* [マイクロフローの整合性エラー](consistency-errors-microflows)
* [チェック](チェック)
* [ページ](page-editor)
* [ナビゲーションドキュメント](navigation)
* [マイクロフロー](マイクロフロー)