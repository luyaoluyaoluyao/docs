---
title: "Eclipse を使用する"
category: "Javaプログラミング"
tags:
  - "studio pro"
---

## 1つの紹介

Eclipseを使用して、MendixアプリでJavaアクションを書き込み、デバッグできます。 Mendixモデルがデプロイされると、Eclipseプロジェクトファイル、クラスパスファイル、および起動構成が生成されます。

## 2 Eclipse のセットアップ

Mendix では、すべてのテキストは UTF-8 エンコーディングで保存されます。 ソースコードもUTF-8で保存されていることを確認するには、次の操作を行います。

1.  **ウィンドウ > 設定** を選択します。
2.  新しいメニュー ウィンドウで **ワークスペース** を選択します。
3.  **UTF-8** を選択:

    ![UTF-8 エンコーディング設定](attachments/java-programming/eclipse-utf8-encoding.png)

Java Development Kit (JDK)もインストールして選択する必要があります。

![デフォルトの JDK の選択](attachments/java-programming/eclipse-jdk.png)

JDK を追加し、Eclipse 内でデフォルトとして選択するようにしてください。

## 3 Mendix アプリの追加

Mendix アプリを Eclipse に追加するには、次の手順を実行します。

1.  **ファイル > インポート** を選択します。
2.  **General** フォルダを開き、 **Existing Projects into Workspace** を選択し、 **Next >**:

    ![既存のプロジェクトをインポート](attachments/java-programming/eclipse-select-import.png)

3.  **ルートディレクトリ**を選択し、Mendix アプリフォルダを参照し、 **終了** を選択します。

    ![ルートディレクトリを選択](attachments/java-programming/import-eclipse-project.png)

## 4 Mendix アプリの起動

プロジェクトを起動するには、次の操作を行います。

1.  Select **Run > Run configurations...** or **Run > Debug configurations...**, would you like to start the application
2.  **Java アプリケーション** を選択すると、Mendix Studio Pro によって生成された起動構成が表示されます。
3.  **Run** (or **Debug**)を選択してアプリケーションを起動します。

    ![設定を起動](attachments/java-programming/eclipse-run-configuration.png)

アプリケーションを起動すると、 **M2EE Admin Console** が表示されます。 これは、通常Mendix Studio Proで見られるのと同じコンソールで、そこからアプリケーションを実行する場合に使用します。 コンソールを閉じることでアプリケーションを停止できます。

![M2EE 管理者コンソール](attachments/java-programming/eclipse-debug-log.png)
