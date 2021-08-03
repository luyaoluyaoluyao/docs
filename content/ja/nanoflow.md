---
title: "Nanoflow Properties"
parent: "ナノフロー"
tags:
  - "studio pro"
---

## 1つの紹介

このページでは、ナノフローの特性について説明します。 nanoflows と nanoflow 要素の使用の詳細については、 [Nanoflows](nanoflows) を参照してください。

## 2つのプロパティ

以下の画像では、ナノフロー特性の例を示しています。

{{% image_container width="250" %}}![Nanoflow Properties](attachments/microflows-and-nanoflows/nanoflow-properties.png)
{{% /image_container %}}

Nanoflowプロパティは以下のセクションで構成されています:

* [一般的な](#common)
* [出力](#output)
* [セキュリティ](#security)
* [使用法](#usage)

### 2.1 共通セクション{#common}

#### 2.1.1 名前

**名前** はナノフローの内部名である。 アプリでnanoflowを参照するときは、この名前を使用します。 モジュール内では一意でなければなりませんが、異なるモジュール内で同じ名前を持つ2つのナノフローを持つことができます。 ナノフを参照するとき 通常はモジュールの名前を付けて一意性を確保し、他のモジュールでナノフローを使用することができます。

#### 2.1.2 ドキュメント

**ドキュメント** を使用すると、ナノフローを簡単に説明することができます。

### 2.2 出力セクション{#output}

#### 2.2.1 戻り値の種類

戻り値の型は、nanoflow が返す情報を定義します。 nanoflowの呼び出し元はこのタイプの結果を得るでしょう。 戻り値の型については、 [Data Types](data-types) を参照してください。

### 2.3 セキュリティセクション{#security}

#### 2.3.1 許可されたロール

これらは、ユーザーがナノフローを実行できる必要がある [モジュールロール](module-security#module-role) です。

詳細については、 [モジュールセキュリティ](module-security) を参照してください。

### 2.4 使用セクション {#usage}

#### 2.4.1 使用済みマーク

You can search for unused items (<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>F</kbd>, then select **Unused items** in the **Search for** drop-down menu) in Studio Pro. Studio Proはソースコード内を見ることができないため、JavaScriptコードからのみ呼び出されるNanoflowは使用されていないものとしてリストされます。

プロパティ **使用済みとして** を **はい**に設定する あなたは明示的に nanoflow が使用され、使用されていない項目を検索するときに Studio Pro がリストに追加されなくなります。

デフォルト: *いいえ*
