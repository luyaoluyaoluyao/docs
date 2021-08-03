---
title: "検証メッセージ"
parent: "認証ウィジェット"
tags:
  - "studio pro"
  - "検証メッセージ"
  - "認証ウィジェット"
  - "認証"
---

{{% alert type="warning" %}}バリデーションメッセージウィジェットはネイティブのモバイルページではサポートされていません。{{% /alert %}}

## 1つの紹介

**検証メッセージ** のウィジェットは、ページに認証失敗メッセージを表示します:

![検証メッセージウィジェット](attachments/authentication-widgets/validation-message.png)

 以下の両方の条件が満たされている場合にのみ、エンドユーザーに表示されます。

1.  サインインボタンの **検証メッセージ ウィジェット** プロパティで選択された検証メッセージ。 このプロパティの詳細については、 [サインインボタン](sign-in-button#validation-message-widget) の *メッセージウィジェット* のセクションを参照してください。
2.  無効な資格情報を入力したエンドユーザーである認証に失敗します。

## 2つのプロパティ

検証メッセージプロパティの例は以下の画像で表されています:

{{% image_container width="300" %}}![検証メッセージのプロパティ](attachments/authentication-widgets/validation-message-properties.png)
{{% /image_container %}}

検証メッセージのプロパティは以下のセクションで構成されています:

* [一般的な](#common)
* [デザインプロパティ](#design-properties)

### 2.1 共通セクション {#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 デザインプロパティセクション {#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

## 3 続きを読む

* [ページ](page)
* [ログインIDテキストボックス](login-id-text-box)
* [パスワードのテキストボックス](password-text-box)
* [サインインボタン](sign-in-button)