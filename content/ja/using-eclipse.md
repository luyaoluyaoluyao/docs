---
title: "Eclipse を使用する"
category: "Javaプログラミング"
tags:
  - "studio pro"
---

MendixプロジェクトでEclipseを使用してJavaアクションを書き、デバッグするのは本当に簡単です。 Mendixモデルがデプロイされると、Eclipseプロジェクト・ファイル、クラスパス・ファイルおよび起動構成が生成されます。

Mendix では、すべてのテキストは UTF-8 エンコーディングで保存されます。 まず、ソースコードもUTF-8\に保存されていることを確認してください。 これは、ウィンドウメニューに移動して設定を選択し、下のスクリーンショットに示されるようにUTF-8を選択することで行うことができます。

{{% alert type="info" %}}

![](attachments/java-programming/918120.png) UTF-8エンコーディングの設定

{{% /alert %}}

Java Development Kit (JDK)もインストールして選択する必要があります。

{{% alert type="info" %}}

![](attachments/java-programming/918186.png) デフォルトの JDK を選択する。

{{% /alert %}}

JDKを追加し、Eclipseでデフォルトとして選択してください。

Mendix プロジェクトを Eclipse に追加するには、次の手順を実行できます。

*   ファイルメニューを開き、インポートをクリックします。
*   「一般」フォルダを開き、「ワークスペースに既存のプロジェクト」を選択し、「次へ」をクリックします
*   「ルートディレクトリを選択」オプションを使用し、Mendixプロジェクトフォルダを参照して終了をクリックします

{{% alert type="info" %}}

![](attachments/java-programming/917580.png) 既存のプロジェクトをインポート

{{% /alert %}}{{% alert type="info" %}}

![](attachments/java-programming/917527.png) 既存のプロジェクトをインポートする手順 2.

{{% /alert %}}

これで、通常どおりにJavaアクションの編集を楽しく開始できます。

プロジェクトを実際に起動するには、プロジェクトの実行方法に応じて「デバッグ設定」または「実行構成」に移動します。 左側のメニューで「Javaアプリケーション」メニューを選択すると、Mendix Studio Proによって生成された起動構成が表示されます。 右側の「debug」または「run」をクリックするだけでアプリケーションを起動できます。

{{% alert type="info" %}}

![](attachments/java-programming/917586.png) 起動設定を検索します。

{{% /alert %}}

アプリケーションを起動すると、M2EE管理コンソールポップアップが表示されます。 このコンソールは、そこからプロジェクトを実行する場合は、Mendix Studio Proで通常表示されるのと同じです。 コンソールを閉じることでアプリケーションを停止できます。

{{% alert type="info" %}}

![](attachments/java-programming/917582.png) M2EE管理コンソール。

{{% /alert %}}
