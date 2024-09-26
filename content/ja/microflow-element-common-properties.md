---
title: "共通のプロパティ"
parent: "application-logic"
menu_order: 110
tags:
  - "studio pro"
  - "共通のプロパティ"
  - "マイクロフロー"
  - "nanoflow"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/microflow-element-common-properties.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

このドキュメントでは、マイクロフローエディタ内の多くの要素によって共有される一般的なプロパティについて説明します。

{{% alert type="warning" %}}
マイクロフローやナノフローのすべての要素がこれらの特性を持っているわけではありません。
{{% /alert %}}

これらはマイクロフローとナノフローの一般的な特性です。

{{% image_container width="30%" %}}
![プロパティペインの共通プロパティ](attachments/microflows-and-nanoflows/microflow-element-common-properties.png)
{{% /image_container %}}


* [図表番号](#caption)
* [キャプションを自動生成する](#auto-generate-caption)
* [背景色](#color)
* [エラー処理タイプ](#error-handling)

## 図表番号2 {#caption}

**図表番号** では、この要素で何が起こるかを説明します。 これは、注釈を追加することなく、マイクロフローを読みやすくし、理解しやすくするために microflow 要素に表示されます。 ここに値を入力すると、 [自動生成図表番号](#auto-generate-caption) は自動的に **いいえ**に設定されます。

## 図表番号を自動生成 {#auto-generate-caption}

**自動生成図表番号** プロパティは、アクティビティの種類に基づいてキャプションが自動的に生成されるかどうかを指定します。

| Option        | 説明                                     |
| ------------- | -------------------------------------- |
| はい  *(デフォルト)* | アクティビティのキャプションは、Studio Pro によって生成されます。 |
| いいえ           | 自分で編集できる **図表番号** プロパティの値が使用されます。      |

## 3 背景色 {#color}

**背景色** プロパティでは、各アクティビティの背景色を個別に選択できます。 色は実行に影響を与えません。要素はフロー内で素早く見つけるためにのみ使用されます。 例えば、 [エラーハンドラ](error-event#errorhandlers) を赤色にすることで、簡単に識別できます。

**プロジェクト設定** > [その他](project-settings#miscellaneous) で、特定のタイプのすべてのアクティビティのデフォルトの色を選択することもできます。 特定のタイプのすべてのアクティビティのデフォルトの色は、マイクロフローのアクティビティを右クリックし、コンテキストメニューから **既定の色** として設定することで変更することもできます。 これにより、現在のアクティビティの色が同じタイプのすべてのアクティビティのデフォルトの色になります。 アクティビティの種類のデフォルトの色を変更し、アプリ内に別の背景色を指定したその種類のアクティビティがある場合。 これらの個々の色を新しいデフォルトの色で上書きするかどうかを尋ねられます。

## 4エラー処理タイプ {#error-handling}

**エラー処理 タイプ**では、アクティビティのエラー処理の種類を選択できます。 利用可能なオプションとその効果の詳細については、 [Microflows](error-event#errorhandlers) の *Error Handlers* セクションを参照してください。

## 5 続きを読む

* [マイクロフロー](マイクロフロー)
* [Nanoflows](ナノフロー)
