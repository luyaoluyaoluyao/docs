---
title: "データストレージ"
category: "Mendix Runtime"
tags:
  - "studio pro"
---

## 1つの紹介

データストレージは Mendix Runtime のデータ基盤です。 データストレージは以下の操作を行います:

* サポートされているリレーショナルデータベースへの接続
* ドメインモデルからエンティティと関連付けを保存して取得します
* XPath と OQL クエリを SQL クエリに変換します
* セキュリティを透明かつ効果的に処理する

## 2つのデータベース

Mendix Cloudにデプロイされたアプリの場合、MendixはPostgreSQLデータベースを使用してアプリケーションドメインモデルに定義されたデータを保存します。

異なるインフラストラクチャにデプロイする場合、Mendixは次のデータベースをサポートします。

* IBM DB2
* HSQLDB
* MySQL
* Oracle RDBMS
* PostgreSQL
* SAP HANA
* Microsoft SQL Server
