---
title: EMSへの接続
keywords: amazon
sidebar: emscloud_sidebar
permalink: emscloud_amazon_connectEMS.html
folder: emscloud
toc: true
---

EMSインスタンスを作成したら、下記に示すように**SSH Terminal**, **Windows PuTTy**, **EMS Web UI** and **EMS HTTP Based API**等を駆使し、EMSに接続してください。

## Linux上でEMSに接続

### A.	ターミナルでSSH

SSH経由でインスタンスに接続するのはLinux EC2コンピュータへの接続と同じ要領です。"ubuntu"ユーザーでインスタンス設定時に選択した.pemキーをつかってアクセスできます。


1. ターミナルで.pem (キーファイル)のパスを確認しておきます

2. 次のコマンドを実行: `ssh –i ./<evostream-keys.pem> ubuntu@<public_IP>`

   **Note:** Public IPはアマゾンインスタンスで確認できます

   ```
   test@ubuntu:~/Desktop$ ssh -i ./evostream-keys.pem ubuntu@52.91.237.115
   The authenticity of host '52.91.237.115 (52.91.237.115)' can't be established.
   ECDSA key fingerprint is ae:02:ee:41:ff:38:96:ab:78:7b:3a:e6:09:ed:1f:4c.
   Are you sure you want to continue connecting (yes/no)?
   ```

3. "**yes**"と入力し、 **Enter**を押してください

   ```
   Welcome to Ubuntu 14.04.2 LTS (GNU/Linux 3.13.0-46-generic x86_64)

   	Documentation:  https://help.ubuntu.com/
    System information as of Wed Jan 20 09:11:53 UTC 2016
    System load:  0.0               Processes:           106
    Usage of /:   13.9% of 7.74GB   Users logged in:     1
    Memory usage: 2%                IP address for eth0: 11.22.33.44.55
    Swap usage:   0%
    Graph this data and manage this system at:
      https://landscape.canonical.com/
    Get cloud support with Ubuntu Advantage Cloud Guest:
      http://www.ubuntu.com/business/services/cloud
   ```

### B.	Windows PuTTy

#### B.1.	 事前準備

- PuTTY Generator

- PuTTY Secure Shell Client

- Key file


#### B.2.	Key File変換

EvoStream Media Server設定はSSHやクライエントソフトを使用して行うことができます。Public AMIインスタンスはパスワードではなくpublic/private key pairを使用してログインします。パブリックキーはインスタンス内にエンベッドされており、プライベートキーをつかってログインします。

Windows® OSではPUTTY Secure Shellクライエントを使ってAmazon EC2インスタンスにセキュアなセッションを開くことができます。PUTTYは[ここ](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)からダウンロードできます。

PUTTYをつかってアクセスする前にプライベートキーを<u>変換</u>する必要があります。PUTTYはAmazon EC2が生成するプライベートキーフォーマットをネイティブでサポートしませんので、**PuTTYgen**ツールを使ってプライベートキーをPUTTY Private Key Fiel (\*.ppk)フォーマットに変換してください。\[key-pairname\].pemファイルを\[key-pair-name\].ppkファイルに変換するには次の手順です:

1. **PuTTY Key Generator**を起動してください

2. **Load** ボタンをクリックしてください

   ![](images/emscloud/image14.jpg)

   ​

3. 変換したい**.pem file**を選択してください

   **Note:** ファイルリストでPEMファイルを表示させるにあｈファイルフィルタですべてのファイルを選択しておく必要があります

4. PuTTYgen Noticeウインドウで**OK**ボタンをクリックしてください

   ![](images/emscloud/image15.png)

5. **Save private key**をクリックし**\[key-pair-name\].ppk**というファイル名で保存してください

#### B.3.	SSH経由での接続

1. **PuTTY**を起動してください

2. Categoryから **Session** を選択してください
   ![](images/emscloud/image16.png)

3. Specify the destination欄に接続先を入力してください
   ![](images/emscloud/image17.png)

   **Host Name** – Amazon EC2インスタンスのパブリックIPアドレス
   **Port** – 22 (デフォルト)
   **Connection type** – SSH

4. **Connection > SSH**の下の**Auth**を選択してください

5. **Browse**ボタンをクリックし、**\[key-pair-name\].ppk**を選択してください
   ![](images/emscloud/image18.jpg)

   **Note:** 次回以降同じセッションを開く際のためにセッション情報を保存しておくことができます

   ***セッション情報を保存する:***

   PuTTY SessionページのBasic optionsでSaved Sessions欄に名前を入力し**Save**ボタンをクリックしてください
   ![](images/emscloud/image19.jpg)

   1. **Open**ボタンをクリックしSSHセッションを開いてください。インスタンスへ初回接続時は**\[key-pair-name\].pem**ファイルを初回使用した旨のPuTTY Security Alertが表示されます
   2. セキュリティキーを**Yes**をクリックしてください
      ![](images/emscloud/image20.png)
   3. "**ubuntu**"でログインしてください
      ![](images/emscloud/loggedin.JPG)

Amazon EC2インスタンス用のSSHセッション情報を既に以前保存している場合は下記の要領ですすめてください

1. **PuTTY**を起動してください
2. **Session**を選択してください
3. Saved Sessionを選択し、**Load**ボタンをクリックしてください
   ![](images/emscloud/image21.jpg)
4. **Open**ボタンをクリックして、SSHセッションを開いてください
**Note:** SSHクライエントウインドウでプロンプトが表示されたら、ユーザー名に"**ubuntu**"を入力してください
![](images/emscloud/image22.png)
![](images/emscloud/loggedin.JPG)

### B.	EMS Web UI

EMSでの作業はコマンドラインまたはHTTPベースAPIコールで行えますが、Web UIを使うこともできます。Web UIへアクセスするにはブラウザで下記のURLを開いてください:
`http://<DomainまたはPublicIP>:8888/EMS_Web_UI/index.php`

**< DomainまたはPublicIP >** 部分はEC2インスタンスのパブリックドメインまたはパブリックIPに置き換えてください

**Note:** UIにアクセスするにはEMSが起動している必要があります。

#### B.1.	Public IPの確認

1. *https://console.aws.amazon.com*にサインインしてください
2. Computeで**EC2** をクリックしてください
   ![](images/emscloud/image23.jpeg)

3. EC2 Management ConsoleのNavigationペインのInstancesで**Instances**をクリックしてください

4. 実行中のインスタンスを選択してください

5. **Description tab**をクリックしてください。Public IP/DNS値は実行中のインスタンスのパブリックドメイン名です。
   ![](images/emscloud/image13.jpeg)

#### B.2. Web UIにログイン

AWSでEMSを使用する際Web UIはデフォルトで保護されています。Web UIにアクセスする際ユーザ名・パスワードの入力が求められます
![](images/emscloud/authentication.JPG)

- Username: evostream
- Password: "Amazon Instance ID" - Amazonアカウントで確認できます

  **Amazon Instance IDの確認**

  **Amazon Consoleで**

  1. *https://console.aws.amazon.com*にサインインし
  2. Computeで**EC2**をクリックしてください
     ![](images/emscloud/image23.jpeg)
  3. Resourcesの**Running Instances**をクリックしてください
     ![](images/emscloud/image24.jpeg)
  4. EMSに用意された**Instance Name**をクリックし、**Instance ID**を確認してください
     ![](images/emscloud/image25.jpeg)

### C.	HTTP ベース API

HTTPベースAPIはとても便利に活用できます。APIに関しては: [API 概要](api_overview.html)を参照してください。

AWS上のEMSではHTTPベースAPIは**Proxy Authentication**認証を必要とします。ベーシック認証が使用されユーザ名とパスワード入力が必要です。

- Username: evostream
- Password: "Amazon Instance ID"
**コマンドは次のようなフォーマットとなります:**

```
http://Username:Password@IPAddress:Port/apiproxy/CommandName?params=<base64EncodedString>
```

ブラウザでコマンドを実行します。ブラウザのURL欄にコマンドをペーストし**Enter**を押してください

**サンプルコマンド:**

```
http://evostream:i-013c03dc9bab9d69f@52.91.237.115:8888/apiproxy/version
```

**Note:** ユーザ名は“**evostream**” パスワードは “**instance ID**”です

詳細は[HTTP JSON CLI](userguide_telnet.html#http-json-cli) を参照してください

## WindowsでEMSに接続する
### A.	Remote Desktop Connection

1. **Remote Desktop Application**を起動してください
2. 仮想マシンに関する次の情報を入力し**Connect**をクリックしてください

   **Computer** - イメージのIPアドレス
   **Username** -Administrator
   **Password**- *下記を参照*

   2.1.	パスワードの取得

   パスワードを取得するにはInstances listでインスタンスを右クリックし、**Connect**をクリックしてください
   ![](images/emscloud/password.jpg)

   2.2. **Get Password**ボタンをクリックしてください。**[key-pair-name].pem**を選択し、 **Decrypt Password**をクリックしてください
   **password** が表示されます
   ![](images/emscloud/decrypt.JPG)

3. **password**を入力し**OK**をクリックしてください

4. 接続が確立されます。EMSデスクトップショートカットアイコンをダブルクリックするか、または`run_console_ems.bat`を実行しEMSを起動してください。

**Note:** `C:\EvoStream`にEMSはインストールされます

### B.	EMS Web UI

EMSでの作業はコマンドラインまたはHTTPベースAPIコールで行えますが、Web UIを使うこともできます。Web UIへアクセスするにはブラウザで下記のURLを開いてください:
`http://<DomainまたはPublicIP>:8888/EMS_Web_UI/index.php`

**< DomainまたはPublicIP >** 部分はEC2インスタンスのパブリックドメインまたはパブリックIPに置き換えてください

**Note:** UIにアクセスするにはEMSが起動している必要があります。

#### B.1.	Determining Public IP

1. *https://console.aws.amazon.com*にサインインしてください
2. Computeで**EC2** をクリックしてください
   ![](images/emscloud/image23.jpeg)

3. EC2 Management ConsoleのNavigationペインのInstancesで**Instances**をクリックしてください

4. 実行中のインスタンスを選択してください

5. **Description tab**をクリックしてください。Public DNS値は実行中のインスタンスのパブリックドメイン名です。
   ![](images/emscloud/image13.jpeg)

#### B.2. Login for Web UI

AWSでEMSを使用する際Web UIはデフォルトで保護されています。Web UIにアクセスする際ユーザ名・パスワードの入力が求められます
![](images/emscloud/authentication.JPG)

- Username: evostream
- Password: "Amazon Instance ID" - Amazonアカウントで確認できます

  **Amazon Instance IDの確認**
  **Amazon Consoleで**

  1. *https://console.aws.amazon.com*にサインインし
  2. Computeで**EC2**をクリックしてください
     ![](images/emscloud/image23.jpeg)
  3. Resourcesの**Running Instances**をクリックしてください
     ![](images/emscloud/image24.jpeg)
  4. EMSに用意された**Instance Name**をクリックし、**Instance ID**を確認してください
     ![](images/emscloud/image25.jpeg)

### C.	HTTP Based API
HTTPベースAPIはとても便利に活用できます。APIに関しては: [API 概要](api_overview.html)を参照してください。

AWS上のEMSではHTTPベースAPIは**Proxy Authentication**認証を必要とします。ベーシック認証が使用されユーザ名とパスワード入力が必要です。

- Username: evostream
- Password: "Amazon Instance ID"
**コマンドは次のようなフォーマットとなります:**

```
http://Username:Password@IPAddress:Port/apiproxy/CommandName?params=<base64EncodedString>
```

ブラウザでコマンドを実行します。ブラウザのURL欄にコマンドをペーストし**Enter**を押してください

**サンプルコマンド:**

```
http://evostream:i-013c03dc9bab9d69f@52.91.237.115:8888/apiproxy/version
```

**Note:** ユーザ名は“**evostream**” パスワードは “**instance ID**”です

詳細は[HTTP JSON CLI](userguide_telnet.html#http-json-cli) を参照してください

