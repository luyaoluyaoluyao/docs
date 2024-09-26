---
title: "認証ウィジェット"
parent: "ページ"
menu_order: 55
tags:
  - "認証"
  - "ウィジェット"
  - "studio pro"
  - "ログイン"
  - "パスワード"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/authentication-widgets.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

認証ウィジェットは、ユーザーにサインインしてログアウトするために使用されます。

[ナビゲーション プロファイル](navigation#authentication) 設定を使用して、ユーザーを正しい認証ページに誘導します。

**認証ウィジェット** カテゴリには、次のウィジェットが含まれています:

* [ログインIDテキストボックス](login-id-text-box) - ユーザーが認証のためのログインIDを提供することができます

    ![ログインIDテキストボックスの例](attachments/authentication-widgets/logid-id-example.png)

* [パスワードテキスト ボックス](password-text-box) - ユーザーが認証のためのパスワードを提供することができます

    ![パスワードテキストボックスの例](attachments/authentication-widgets/password-text-box-example.png)

* [サインインボタン](sign-in-button) – ユーザーのログインIDとパスワードをサーバーに送信します。 ![サインインボタンの例](attachments/authentication-widgets/sign-in-button-example.png)

* **サインアウトボタン** – 現在サインイン中のユーザーにサインアウトします。 サインアウトボタンは、オンクリックイベントが **サインアウト**に設定されたボタンです。 オンクリックイベントの詳細については、 [[イベント & イベント]セクション](on-click-event)を参照してください。 ボタンのプロパティの詳細。 [ボタンプロパティ](button-properties) を参照してください。

* [バリデーションメッセージ](validation-message) – 認証に失敗した場合、ユーザーに通知します

    ![検証メッセージの例](attachments/authentication-widgets/validation-message-example.png)

## 2 基本機能の実行

{{% snippet file="refguide8/performing-basic-functions-widgets.md" %}}

## 3 続きを読む

* [ページ](page)
* [ページ](ページ)