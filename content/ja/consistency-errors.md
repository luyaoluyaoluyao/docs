---
title: "整合性エラー"
parent: "errors-pane"
menu_order: 10
description: "Mendix Studio Proの一貫性エラーとそれらを修正する方法について説明します。"
tags:
  - "Studio Pro"
  - "整合性エラー"
  - "チェック"
  - "エラー"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/consistency-errors.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

アプリケーションが常に一貫して正しくビルドされていることを確認するために、Studio Proはアプリケーションのビルド時に一貫性を確認します。

一貫性チェックが満たされない場合、Studio Pro は、 [エラー ペイン](errors-pane) で一貫性エラーを通知します。 ページ、マイクロフロー、ドメインモデル、ドキュメントテンプレートのエラーが強調表示されます。

![Errors Pane](attachments/consistency-errors/errors-pane.png)

**エラー** ペインが表示されない場合は、メニュー オプションから **表示 > エラー リスト** を有効にできます。

エラーをすばやく見つけられるようにするには、各エラーが表示されます:

* ユニークな **エラーコード** のエラー
* エラーを記述する **メッセージ**
* ページの名前 **要素** がエラーを引き起こしています
* この要素がある **ドキュメント**
* ドキュメントがある **モジュール**

エラーをダブルクリックすると、エラーの原因となる要素が表示されます。

アプリをデプロイする前にエラーを解決する必要があります。 Studio Pro の次のエディタや機能で一貫性のエラーが発生する可能性があります。

* [ページ](consistency-errors-pages)
* [Navigation](consistency-errors-navigation)
* [マイクロフロー](マイクロフロー)
* [ドメインモデル](ドメインモデル)
* [統合](integration)
* [セキュリティ](セキュリティ)

## 2 続きを読む

* [ページエディタの整合性エラー](consistency-errors-pages)
* [ナビゲーション一貫性エラー](consistency-errors-navigation)
* [Errors Pane](errors-pane)
* [ページ](ページ)
* [マイクロフロー](マイクロフロー)
* [Mendix のナビゲーション](navigation)
