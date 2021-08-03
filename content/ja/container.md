---
title: "コンテナ"
parent: "container-widgets"
menu_order: 20
tags:
  - "studio pro"
  - "コンテナ"
  - "コンテナウィジェット"
  - "ウィジェット"
---

## 1つの紹介

コンテナは、配置されたウィジェットのグループを同時にスタイル設定、非表示、ドラッグ、または削除することができるレイアウト要素です。

![コンテナの例](attachments/container-widgets/container.png)

ブラウザーでは、デフォルトで単純な `div` 要素としてレンダリングされます。 HTML 5のセマンティック要素の1つとしてコンテナをレンダリングすることもできます(例えば、 `section`, `main`, `article`, `nav`).

## 2つのプロパティ

以下の画像には、コンテナプロパティの例が示されています。

{{% image_container width="300" %}}![コンテナのプロパティ](attachments/container-widgets/container-properties.png)
{{% /image_container %}}

コンテナープロパティは以下のセクションで構成されています:

* [アクセシビリティ](#accessibility)
* [一般的な](#common)
* [デザインプロパティ](#design-properties)
* [全般](#general)
* [イベント](#events)
* [公開範囲](#visibility)

### 2.1 アクセシビリティ {#accessibility}

#### 2.1.1 スクリーンリーダーの非表示

このプロパティは、コンテナをスクリーンリーダーから非表示にするかどうかを指定します。

{{% alert type="info" %}} コンテナには、入力ウィジェット、リンク、ボタンなど、フォーカス可能な要素を含めないでください。 これらの要素により、コンテナはスクリーンリーダーによって発表されます。
{{% /alert %}}

### 2.2 共通セクション {#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.3 デザインプロパティセクション{#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.4 一般セクション {#general}

#### 2.4.1 レンダリングモード

**レンダリングモード** は、Web ブラウザでコンテナを表示するために使用する HTML5 タグを決定します。

| 値               | HTML タグ  |
| --------------- | -------- |
| Div *(default)* | `div`    |
| セクション           | `セクション`  |
| 記事              | `記事`     |
| ヘッダー            | `ヘッダー`   |
| フッター            | `フッター`   |
| メイン             | `メイン`    |
| Nav             | `nav`    |
| アサイド            | `はさておき`  |
| Hgroup          | `hgroup` |
| 住所              | `アドレス`   |

{{% alert type="info" %}}レンダリングモードはネイティブのモバイルページではサポートされていません。{{% /alert %}}

### 2.5 イベントセクション {#events}

#### 2.5.1 On-Click {#on-click}

**Onclick** プロパティは、ユーザーがコンテナをクリックしたときに実行されるアクションを指定します (マウスポインタを使用するか、コンテナがフォーカスされているときに <kbd>Enter</kbd> または <kbd>Space</kbd> キーを押します)。

{{% snippet file="refguide/events-section-link.md" %}}

### 2.6 表示セクション {#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 4 続きを読む

* [ページ](page)
* [コンテナウィジェット](container-widgets)
* [ページエディターで共通のプロパティ](common-widget-properties)
