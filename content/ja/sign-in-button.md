---
title: "サインインボタン"
parent: "認証ウィジェット"
tags:
  - "studio pro"
  - "サインインボタン"
  - "サインイン"
  - "認証ウィジェット"
  - "認証"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/sign-in-button.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="warning" %}}The **Sign-in button** is not supported on native mobile pages.{{% /alert %}}

## 1つの紹介

**サインイン ボタン** は、ユーザーのログイン ID とパスワードをサーバーに送信します。

![サインインボタン](attachments/authentication-widgets/sign-in-button.png)

エラーは、 [検証メッセージ ウィジェット](#validation-message-widget) またはポップアップ ウィンドウに表示されます。

**サインイン ボタン** は、 [ログイン ID テキスト ボックス](login-id-text-box) と [パスワード テキスト ボックス](password-text-box) と一緒にページに配置する必要があります。

## 2つのプロパティ

以下の画像にサインインボタンプロパティの例を示します。

{{% image_container width="250" %}}![サインインボタンのプロパティ](attachments/authentication-widgets/sign-in-button-properties.png)
{{% /image_container %}}

サインインボタンのプロパティは以下のセクションで構成されています:

* [一般的な](#common)
* [デザインプロパティ](#design-properties)
* [全般](#general)
* [公開範囲](#visibility)

### 2.1 共通セクション {#common}

{{% snippet file="refguide8/comon-section-link.md" %}}

### 2.2 デザインプロパティセクション {#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 一般セクション {#general}

サインインボタンのほとんどのプロパティは、ボタンウィジェットのプロパティと同じです。 **General** セクションの button プロパティの詳細については、 [Button Properties](button-properties#general) の *General セクション* を参照してください。

#### 2.3.1 検証メッセージウィジェット {#validation-message-widget}

**検証メッセージウィジェット** は、サインインボタンの特定のプロパティです。 認証失敗メッセージをページに表示する [検証メッセージ ウィジェット](validation-message) を定義します。 このプロパティでウィジェットが選択されていない場合、認証失敗メッセージはポップアップウィンドウに表示されます: ![バリデーション失敗](attachments/authentication-widgets/validation-failure.png)

デフォルト: *なし*

### 2.4 表示セクション {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 続きを読む

* [ページ](page)
* [ログインIDテキストボックス](login-id-text-box)
* [パスワードのテキストボックス](password-text-box)
* [検証メッセージ](validation-message)