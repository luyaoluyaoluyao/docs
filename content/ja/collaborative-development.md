---
title: "Studio での共同開発"
category: "コラボレーション"
description: このドキュメントでは、Mendix StudioとMendix Studioの共同開発プロセスについて説明します。
tags:
  - "スタジオ"
  - "共同開発は"
  - "同期"
menu_order: 10
---

## 1つの紹介

{{% alert type="warning" %}}

共同開発は、Mendix バージョン 7.23.3 以降の場合にのみ利用できます。 Mendix バージョン 7.23.2 以下のアプリでは、Studio Pro で変更内容を同期できません。

Studio でアプリを開くことができます。 ただし、Studio と Studio Pro 間の変更を同期するには、Studio Pro をバージョン 7.23.3 以上にアップグレードする必要があります。

{{% /alert %}}

コラボレーション開発とは、チームメンバーがMendix Studio ProとMendix Studioの1つのアプリで協力し、 [バージョンコントロール](/refguide8/version-control)を使用して他のメンバーが行った変更を簡単に同期できるようにするプロセスです。

チームで作業している場合(または、Studio から Studio Pro に切り替えている場合)、アプリモデルの変更を簡単に共有できます。 Studio で行われたすべての変更は自動保存されます。 Studio Pro のユーザーは、 **Update** または **Commit** をクリックすると、これらの変更を受け取ります。 コミットすると、独自の変更を同時にプッシュするため、Studio と Studio Pro の両方が同期されます。 より技術的で詳細なプロセスの概要については、 [Studio Pro Guide](/refguide8/collaborative-development) の *Collaborative Development* を参照してください。

複数のユーザーが同時にStudioでアプリを表示できます: あるユーザーが編集でき、他のユーザーが読み取り専用モードになっています。

## 2つのコンセプト

概念と定義については、 [バージョンコントロール](/refguide8/version-control) のセクション *2 コンセプト* を参照してください。

## スタジオからの共同開発

Studio の変更はすべて自動保存されます。 共同開発は、アプリの内容が変更されたり同期されたりするときに表示されるポップアップで示されます。 これは以下の場合に発生します。

1. **変更をコミットする** – Studio Pro でチームメンバーが同じ開発ラインで作業している場合、 **Update**をクリックします。 変更がチームサーバーに自動的に反映され、Studio Pro に適用されている間、しばらく画面がロックされます。 Studio Proの共同開発プロセスの詳細についてはこちらをご覧ください。 see [4 Studio Pro Perspective](/refguide8/collaborative-development) in *Collaborative Development* in *Version Control*.

    {{% image_container width="350" %}}![変更をコミットするダイアログ ボックス](attachments/collaborative-development/committing-changes.png)
   {{% /image_container %}}

2.  **変更の同期** – Studio Pro のユーザーがコミットするたびに画面がしばらくロックされます。 <br/>

    {{% image_container width="350" %}}![同期変更ダイアログ ボックス](attachments/collaborative-development/synching-changes.png)<br/>

    {{% /image_container %}}

    このプロセスには2つの可能性のある結果があります:<br/>

    a  Studio Pro では、アプリ内で競合が発生せず、Studio Pro からの変更は Studio に適用されます。 (競合とは矛盾する変更であり、自動的にマージすることはできません。 たとえば、あるユーザーがボタンのキャプションを変更し、別のユーザーがこのボタンを削除しました。

    B  Studio Proユーザーが再度コミットする前に、Studio Proで解決するアプリの競合があります。 画面はアプリに変更を加えることなくロック解除されます。

3.  **コンテンツの切り替え** – Studio Pro では、Studio が有効になっているブランチラインを変更できます。 ブランチの管理に関する詳細情報 [Studio Pro Guide](/refguide8/collaborative-development#managing-branches) の *Collaborative Development* の *開発ラインの管理* セクションを参照してください。 このプロセスでは、Studio がしばらくロックされます。すべての変更は現在の開発ラインに自動保存されます。 そして、Studio ProユーザーがStudioのブランチラインを変更していることをポップアップダイアログが表示されます。 これは、アプリの内容が変わることを意味します。

    {{% image_container width="350" %}}![format@@0 ダイアログ ボックス](attachments/collaborative-development/switching-branches.png)
    {{% /image_container %}}

## 4 続きを読む

* [バージョン管理](/refguide8/version-control)
* [共同開発](/refguide8/collaborative-development)

