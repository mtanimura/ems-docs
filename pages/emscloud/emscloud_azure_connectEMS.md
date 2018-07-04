---
title: EMSへの接続
keywords: azure
sidebar: emscloud_sidebar
permalink: emscloud_azure_connectEMS.html
folder: emscloud
toc: true
---

## EMSマシンの起動
左側のメニューバーのVirtual machines欄にアカウントの全仮想マシンが表示されます
仮想マシン名を選択しクリックし、**Start**ボタンをクリックしてください
![](images/emscloud/startVM.JPG)

## EMSへの接続
EMSインスタンスを起動したら、EMSに接続してみましょう。それぞれ**SSH Terminal**, **Windows PuTTy**, **Remote Desktop**, **EMS Web UI**, **EMS HTTP Based API**などでの接続について下記を参照してください

### SSH via Terminal

1. コマンドを実行: `ssh <username>@<IP_address>`

   ```
   user@ubuntu:~/Desktop$ ssh user@11.221.105.202

   The authenticity of host '111.221.105.202 (111.221.105.202)' can't be established.
   RSA key fingerprint is ae:02:ee:41:ff:38:96:ab:78:7b:3a:e6:09:ed:1f:4c.
   Are you sure you want to continue connecting (yes/no)?
   ```

2. "**yes**"と入力し、**Enter**を押してください

   ```
   Warning: Permanently added '111.221.105.202' (RSA) to the list of known hosts.
   user@111.221.105.202's password:
   ```

3. パスワードを入力し**Enter**をおしてください。welcomeと表示されます。次に**<u>ライセンスのインストール</u>** を行ってください

**Note:** ライセンスファイルはLinuxでは `/etc/evostreamms`、Windowsでは `./config`に配置する必要があります

### Windows (PuTTy)によるSSH接続

**事前準備:**

- PuTTY Secure Shell Clientをインストールしてください

1. **PuTTY**を起動してください

2. category から**Session** を選択

   ![](images/emscloud/image16.png)

3. 接続先を指定してください:

   ![](images/emscloud/putty.JPG)

   **Host Name** – EvoStream Media Server実行するインスタンスのパブリックIPアドレス

   **Port** – 22 (デフォルト)

   **Connection type** – SSH

4. **Open**をクリックしてください

5. PuTTy Security Alert Windowが表示されますので**Yes** をクリックしてください

6. ユーザーのパスワードを入力し、**Enter**を押してください

   ```
   Using username "EvoStream".
   EvoStream@111.221.105.202's password:
   ```

7. 仮想マシンに接続されます。**<u>ライセンスのインストール</u>** に進んでください。

**Note:** ライセンスファイルはLinuxでは `/etc/evostreamms`、Windowsでは `./config`に配置する必要があります

### Remote Desktop経由での接続

1. **Remote Desktop Application**を起動してください

   **Note:** remote desktopアプリケーションはOSに依存します

2. 仮想マシンの情報を入力し、**Connect**ボタンをくりっくしてください

   **Computer** -  イメージのIPアドレス

   **Username** -  イメージに設定されたユーザー名

   ![](images/emscloud/remotedesktop.jpg)


3. **パスワード** を入力し **OK**ボタンをクリックしてください

4. 接続が確立されたら、**ライセンスのインストール** に進んでください

   **Note:** The EMSは``C:\EvoStream``にインストールされています

### EMS Web UI

EMSでの作業はコマンドラインまたはHTTPベースAPIコールで行えますが、Web UIを使うこともできます。Web UIへアクセスするにはブラウザで下記のURLを開いてください:
`http://<DomainまたはPublicIP>:8888/EMS_Web_UI/index.php`

**< DomainまたはPublicIP >** 部分はEC2インスタンスのパブリックドメインまたはパブリックIPに置き換えてください
**Note:** UIにアクセスするにはEMSが起動している必要があります。

#### Public IPの確認

1. *http://portal.azure.com/* にサインインしてください


2. Virtual Machinesを選択しクリックしてください

3. 仮想マシンを起動してください

4. EssentialsペインにPublic IP/DNS値が表示されます

   **Note:** 仮想マシンが再起動される度にIPアドレスは変わります

   ![](images/emscloud/IPinAzure.jpg)


#### 認証

認証機能はEMS v1.7.1以降で有効となります。 EMS Web UIおよび HTTP Based APIでは認証はデフォルトで有効となっています

#### Web UIへのログイン

EMS on AzureではWeb UIはデフォルトで認証が必要です。ユーザー名・パスワードの入力を促されます。

![](images/emscloud/authentication.JPG)

- ユーザー名: evostream
- パスワード: "UID" - 仮想マシンのユニークID、webconfig.luaで見られます

### HTTPベースAPI

EMS on AzureにおけるHTTPベースAPIは認証が必要です。ベーシック認証が使用されますのでユーザー名・パスワードの入力が必要です:


- ユーザー名: evostream
- パスワード: "UID" - 仮想マシンのユニークID、webconfig.luaで見られます

**下記のようなフォーマットでコマンドは受け付けられます:**

```
http://Username:Password@IPAddress:Port/apiproxy/CommandName?params=<base64EncodedString>
```

ブラウザからのコマンド実行

**サンプルコマンド:**

```
http://evostream:i-D817E76F-B6F2-CC4F-ACAC-EAE9D84CEE3F@52.91.237.115:8888/apiproxy/version
```

**Note:** ユーザー名は “**evostream**”、 パスワードは “**instance ID**”です

くわしくはEMS [HTTP JSON CLI](userguide_telnet.html#http-json-cli)をご参照ください



#### Unique IDの取得

Proxy認証およびWeb UI認証ではUIDがパスワードとして使用されます。仮想マシンが作成されるとUIDを取得することができます。EMS webconfig.luaでのみ確認することができます

**webconfig.luaファイル内の下記を参照:**

```
apiProxy=
{
   authentication="basic",
   pseudoDomain="apiproxy",
   address="127.0.0.1",
   port=7777,
   userName="evostream",
   password="D817E76F-B6F2-CC4F-ACAC-EAE9D84CEE3F",   --> sample UID
}
```