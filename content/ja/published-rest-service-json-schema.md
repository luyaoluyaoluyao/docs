---
title: "公開されたREST操作のためのJSONスキーマ"
parent: "published-rest-technical-details"
menu_order: 20
description: "操作リクエストボディと操作結果のための JSON スキーマの説明"
tags:
  - "公開された REST"
  - "JSON"
  - "スキーマ"
  - "操作"
  - "本文をリクエスト"
  - "result"
  - "メッセージの定義"
---

## 1つの紹介

[残りのサービス](published-rest-services)を公開すると、 [OpenApi (Swagger) ドキュメント ページ](published-rest-services#interactive-documentation) が生成されます。 これは、サービスが受信および返却できるメッセージの構造の説明を含みます。 この構造は JSON スキーマを使用して説明されています。

インポートまたはエクスポートマッピングが定義されている操作は、スキーマを生成します。 しかし、 [メッセージ定義](message-definitions) に基づくマッピングのみ。

JSON スキーマは、ここで説明されているルールに基づいて生成されます。

## 2つの定義

OpenApi スキーマには、ボディパラメータとリターン型の定義が含まれています。 構成されたインポートまたはエクスポートマッピングがメッセージ定義に基づいている場合、その定義が存在します。

### 2.1 メッセージの定義

```json
"#definition_name#": { 
  "type": "object",
  "properties": [
     #attribute_name#: #attribute_schema#
  ]
}
```

デフォルトでは、定義名はマッピングが基づいているメッセージ定義の名前です。 マッピングの _Public name_ を設定することで、独自の定義名を選択できます。

### 2.2 属性

属性のスキーマは属性型によって異なります。

| 属性タイプ      | 属性スキーマ                                             |
| ---------- | -------------------------------------------------- |
| Autonumber | `{ "type": "integer", "format": "int64" }`         |
| バイナリ       | `{ "type": "string", "format": "binary" }`         |
| Boolean    | `{ "type": "boolean" }`                            |
| 日付と時刻      | `{ "type": "string", "format": "date-time" }`      |
| 小数点以下桁数    | `{ "type": "number" }`                             |
| 列挙型        | `{ "type": "string", "enum": ["Male", "Female"] }` |
| ハッシュ文字列    | `{ "type": "string" }`                             |
| 整数         | `{ "type": "integer", "format": "int32" }`         |
| 長い順        | `{ "type": "integer", "format": "int64" }`         |
| 文字列        | `{ "type": "string" }`                             |

## オペレーションリクエストボディ用の3つのJSONスキーマ

操作にbodyパラメータがある場合、スキーマがあります。 このスキーマは、メッセージ定義に基づいてインポートマッピングを選択したときに定義を参照します。

パラメータがオブジェクトの場合:

```json
{ "$ref": "#/definitions/#definition_name#"}
```

パラメータがリストの場合:

```json
{ 
  "type": "array",
  "items": [{ "$ref": "#/definitions/#definition_name#"}]
}
```

インポートマッピングが存在しないか、またはマッピングがメッセージ定義に基づいていない場合:

```json
{ "type": "file" }
```

## 操作結果のための 4 JSON スキーマ

操作の結果にもスキーマがあります。 この形式は結果の種類によって異なります。

エクスポートマッピングが存在しないか、エクスポートマッピングがメッセージ定義に基づいていない場合:

```json
{ "type": "file" }
```

microflow がオブジェクトを返す場合:

```json
{ "$ref": "#/definitions/#definition_name#"}
```

マイクロフローがリストを返した場合:

```json
{ 
  "type": "array",
  "items": [{ "$ref": "#/definitions/#definition_name#"}]
}
```

マイクロフローがプリミティブを返すと、スキーマは型に依存します。

| マイクロフローの結果 | スキーマ                    |
| ---------- | ----------------------- |
| なし         | (なし)                    |
| バイナリ       | `{ "type": "file" }`    |
| Boolean    | `{ "type": "boolean" }` |
| 日付と時刻      | `{ "type": "file" }`    |
| 小数点以下桁数    | `{ "type": "number" }`  |
| 列挙型        | `{ "type": "file" }`    |
| 整数         | `{ "type": "integer" }` |
| 文字列        | `{ "type": "file" }`    |
