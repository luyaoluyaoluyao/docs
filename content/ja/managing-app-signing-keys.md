---
title: "アプリ署名キーの管理"
category: "モバイル"
menu_order: 21
tags:
  - "studio pro"
---

## 1つの紹介

モバイルアプリを作成するには、プラットフォーム固有のアプリ署名キーが必要です。 モバイルアプリは、出版前にその開発者によってデジタル署名で署名されています。 これらの署名は、アプリが本物であることを確認するために、アプリストアとデバイスの両方で使用されます。

ターゲットとするプラットフォームに応じて、必要な署名キーを作成する必要があります。 次のセクションでは、これらのキーを作成する方法について説明します。

{{% alert type="warning" %}} クラウドでハイブリッドアプリを構築するには、AdobeのPhoneGap Build サービスを使用します。 Adobeはこのサービスを維持できないため、ハイブリッドアプリをクラウドで構築し、アプリストアに公開することはできなくなりました。

このドキュメントの PhoneGap ビルドに言及している部分は、すぐに手順で更新されます。 {{% /alert %}}

## 2 iOS{#ios}

残念ながら、iOS アプリ展開には常に署名キーが必要です。 個人のデバイスで App をテストするだけで、Apple App Store に公開したくない場合でも。 このセクションでは、必要なファイルを作成する方法を説明します。

Apple Macを利用できるようにするのは便利ですが、必須ではありません。 常にApple Developer Accountが必要です。

### 2.1 Apple Mac の場合

Apple Mac をお持ちの場合 iOS の署名証明書と配布プロファイルを取得する方法については、 [証明書管理](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) の Apple 開発者向けマニュアルを参照してください。 次に、必要な配布プロファイルを作成する方法は [の Apple ドキュメント](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html) を参照してください。 最後に、署名キーファイルを [Adobe PhoneGap Build](managing-app-signing-keys#uploading-keys) にアップロードする方法については、このセクションの最後を確認してください。

### 2.2 他のプラットフォーム

利用可能な Apple Mac をお持ちでない場合は、証明書署名リクエストを手動で作成できます。 まず、OpenSSL ユーティリティを使用して秘密鍵と証明書署名リクエストを作成します。 次の手順は、Windows マシンがあると仮定しますが、これらは OpenSSL パッケージがプリインストールされている Linux マシンにも同様に適用できます。

証明書署名リクエストを手動で作成するには、次の手順に従ってください:

1.  [OpenSSL for Windows](https://www.openssl.org/community/binaries.html) をダウンロードしてインストールします。 **Win32 OpenSSL Light** パッケージをダウンロードしてインストールするだけです(リストの一番上に最新バージョンを入手してください)。
    *   セットアッププロセスが不足している VC++ 再配布可能ライブラリパッケージに不満がある場合は、インストールをキャンセルします。 そして、同じパッケージ一覧から **Visual C++ 2008 Redistributable** をダウンロードしてインストールします (Microsoft のダウンロードページにリダイレクトされます)。 例えば、 *C:\OpenSSL* をインストールします (ステップ3で必要になるので、このディレクトリに注意してください)。
2.  コマンドプロンプトなどのコマンドラインインターフェイス(CLI)を開きます。 ほとんどのシステムでは、管理者としてこれを行う必要があります(Windowsのスタートメニューのリンクを右クリックし、 **管理者として実行**を選択します)。
3.  インストールしたばかりの OpenSSL プログラムで秘密鍵を生成します。 `C:\OpenSSL` を、手順 1 で OpenSSL をインストールした場所に置き換えます。 秘密キーファイルは、 `-out` パラメータの後に指定された場所に保存されます。 The following example will store the file in the root directory of your C: drive (you can change this to anything you want, just select a convenient place and keep track of where the file is stored): `"C:\OpenSSL\bin\openssl.exe" genrsa -out "C:\private.key" 2048`. このコマンドは、「RSA 秘密鍵の生成、2048 bit の長さのモジュール」と、たくさんのドットとプラス記号を出力します。
4.  証明書署名リクエスト (CSR) を生成します。 ファイルは再び同じフォルダに保存されますが、どこにでも配置できます。 Make sure to point to the private key file that was created in the previous step: `"C:\OpenSSL\bin\openssl.exe" req -new -key "C:\private.key" -out "C:\ios.csr"`. コマンドはいくつかのテキストを印刷し、あなたの身元に関連するいくつかの異なる情報を求めます。 **Common Name** のみが関連します。 Apple Developer Member Centerにアップロードした後、証明書が後で簡単に認識されるように、自分の名前を入力してください。

*ios.csr* ファイルは、署名された証明書を生成するために Apple Developer Member Center にアップロードする必要があります。 以下の手順に従ってください。

1.  [Apple Developer Member Center](https://developer.apple.com/account/overview.action) を開きます。
2.  **iOS, tvOS, watchOS**の下で、 **Certificate, All** をクリックします。
3.  **iOS 証明書** の概要で、右上のプラスボタンをクリックします。 これにより、 **iOS Certificate** を追加するウィザードが開きます。 **Select Type** ステップには、キャプション「どのような種類の証明書が必要ですか?」が表示されます。
    *   プラスボタンが無効(グレーアウト)の場合、十分な権限がありません。 会社のアカウント管理者に追加の権利を与えるよう依頼してください。
4.  **開発**で **iOS 開発証明書** を選択します。
5.  **** をクリックします。 証明書署名リクエスト (CSR) **の作成について**. このページでは、Mac で証明書署名リクエストを作成する方法を説明します。 あなたはそれを無視してもよい。
6.  **** をもう一度クリックします。 ステップ **生成**、キャプション付き **証明書を生成する**。
7.  **CSRファイル**をアップロードするには、 **ファイルを選択...** をクリックします。
8.  作成した *ios.csr* 証明書署名リクエストファイルを選択します。
9.  **** をクリックします。 AppleはあなたのCSRに署名し、署名された証明書をダウンロードできるようにします。
    *   証明書署名要求が承認待ちであるというメッセージが表示された場合、十分な権限がありません。 会社アカウント管理者に証明書署名リクエストの承認を依頼してください。
10.  Click **Download** and store the *.cer* file on your disk at a convenient place (for example, next to the private key and CSR files).
11.  **完了** をクリックします。 **iOS 証明書** の概要ページが再び表示されます。 新しい証明書はリストに含まれているはずです。 ここでは、もう一度ダウンロードするか、または取り消すことができます(対応する秘密鍵を紛失した場合)。

### 2.3 必要な配布プロファイルの作成

証明書ファイルを入手したら、配布プロファイルを取得する必要があります。 Apple Developer Member Center では、アプリケーション識別子、テストデバイス、そして最後に配布プロファイルを定義できます。 詳細については、 [識別子、デバイス、プロファイル](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html) を維持する方法についての Apple ドキュメントを参照してください。

### 2.4 Adobe PhoneGap ビルドにキーをアップロード {#uploading-keys}

Once you have downloaded the signing certificate (a *.cer* file), you need to convert the signing certificate from a *.cer* to a *.p12*. OpenSSL を以下の手順で使用します:

1. 署名証明書から PEM 形式を作成します: `"C:\OpenSSL\bin\openssl.exe" x509 -in "C:\ios.cer" -inform DER -out "C:\ios_pem.pem" -outform PEM`.
2. PEM 証明書からパスワードを確保します。 この操作には、ステップ3で作成された秘密鍵であるPEM証明書が必要です。 そしてパスワードは *iosの作成に与えられました。 sr * :*: `"C:\OpenSSL\bin\openssl.exe" pkcs12 -export -out "C:\ios.p12" -inkey "C:\private.key" -in "C:\ios_pem.pem"`.</li>
3 You can upload the signing certificate (now a `.p12` file) and the distribution profile (a `.mobileprovision` file) to Adobe PhoneGap Build on your [account page](https://build.phonegap.com/people/edit). **署名キー** タブに移動し、 **iOS** の下の **キーを追加** をクリックします。 2つのファイルを選択し、キーに名前を付けます。 鍵の右側にある黄色いロックアイコンをクリックし、証明書のパスフレーズを入力することで、鍵のロックを解除できます。 これでキーはビルドジョブで使用できるようになりました。</ol>

## 3 Android{#android}

Android アプリは、アプリに署名せずに Android デバイスに展開できます。 ただし、アプリストアに公開するには、署名済みのアプリが必要です。 これにはキーストアを生成し、Adobe PhoneGap Buildにアップロードする必要があります。

### 3.1 キーストアの生成 {#generating-a-keystore}

Android 用のキーストアを生成するには、次の手順に従います。

1. MacまたはWindows用のJava JDKをインストールします。 JDK binフォルダが後で使用されるため、JDKをインストールした場所を忘れないでください。
2. **コマンドプロンプト** を開き、JDKのbinフォルダにある新しい *keytool.exe* を実行します。
3.  *keytool.exe* プログラムは Java インストールの bin ディレクトリにあります (例: *C:\Program Files\Java\jre1.8.0_20\bin*):

    ![キーツールの場所](attachments/managing-app-signing-keys/cmdjdkexe.png)

4.  *keystore.exe* を指している間、次のコマンドラインプロンプトを入力します。

    ```
    "{{keytool -genkey -v -keystore file.keystore -alias YOUR_ALIAS_NAME -storepass YOUR_ALIAS_PWD -keypass YOUR_ALIAS_PWD -keyalg RSA -validity 36500}}"
    ```

    `YOUR_ALIAS_NAME` と `YOUR_ALIAS_PWD` をあなたのエイリアス名とパスワードに置き換えてください:

    ![名前とパスワード](attachments/managing-app-signing-keys/ktoolsetup.png)

5.  その後の質問に答えるには、各質問の後に **** を入力し、あなたの情報を確認するように求められたら *はい* と入力します。

    ![情報に関する質問](attachments/managing-app-signing-keys/qanda.png)

6. これらの質問を終了すると、現在の作業ディレクトリの *file.keystore* ファイルに保存されるキーストアが生成されます。

### 3.2 PhoneGap ビルドにキーストアをアップロード中

キーストアファイルを作成したら、Adobe PhoneGap Build で [アカウントページ](https://build.phonegap.com/) にアップロードしてください。 次に、以下の指示を完了します:

1. **署名キー** タブに移動し、 **** の下の **Android** をクリックします。
2. キーストアファイルを選択し、キーのタイトルを入力し、前のステップで説明したエイリアスを入力します。
3. キーストアファイルをアップロードした後、キーのロックを解除します。 キーの右側にある黄色いロックアイコンをクリックし、キーストアとキーパスワードの両方を入力します。 これでキーはビルドジョブで使用できるようになりました。
4. In the [Developer Portal](https://sprintr.home.mendix.com/index.html), navigate to **Deploy > Mobile app**, and click the **Publish for Mobile App Stores** button. 次に、 **PhoneGap Build ジョブ** ボタンをクリックします。