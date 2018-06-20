---
title: ERS Installation
keywords: html5
sidebar: html5players_sidebar
permalink: html5players_ersinstallation.html
folder: html5players
toc: true
---



## 事前準備

### STUNサーバー

STUNは、NATの向こう側にあっても、パブリックIPアドレスをエンドホストに知らしめてくれるメソッドセットおよびネットワーク・プロトコルです。ERSによりこのサーバーは使われており、EMSおよびクライエントエンドポイント(ブラウザ)に互いのIPアドレスを知らせてくれます。RestundはオープンソースのSTUN/TURNサーバーでERSと一緒に使用することが推奨されます。

ERSはデフォルト設定ですでにパブリックEvostream STUNサーバーを使用するよう設定されていますが、個別のSTUN/TURNサーバーを立ててホスティングする方法についても記述します。

Linuxにrestundをインストールしホスティングするには:


1. build-essentialおよび伸長・展開されたパッケージがインストールされていることを確認してください。debianベースのLinuxの場合は以下のようにします:

   ```
   apt-get install build-essential
   apt-get install unzip
   ```

2. 次にrestundで使用するtoolkit libraryをダウンロード・インストールしてください:

   ```
   wget http://www.creytiv.com/pub/re-0.4.12.tar.gz
   tar -xzf re-0.4.12.tar.gz
   cd re-0.4.12/
   make
   sudo make install
   ```

3. restundをダウンロード・インストールしてください:

   ```
   wget https://github.com/otalk/restund/archive/master.zip
   unzip master.zip
   cd restund-master
   make
   sudo make install
   sudo ldconfig
   ```

4. restundを設定してください (下記は基本的なconfig.fileの例です):

   ```
   #
   # restund.conf
   #
   # core
   #
   daemon no
   debug yes
   realm TestRealmThatCanBeChanged
   syncinterval 600
   udp_listen <ip>:<port>
   udp_sockbuf_size 524288
   tcp_listen <ip>:<port>
   #
   # modules (STUN messages are processed in module loading order)
   #
   module_path /usr/local/lib/restund/modules
   module stat.so
   module binding.so
   module syslog.so
   module status.so
   #
   # syslog
   #
   syslog_facility 24
   ```

5. 設定ファイルを下記のように所定のパスにコピーしてください:

   ```
   sudo cp restund.conf /etc/
   ```

6. restundを実行してください:

   ```
   sudo restund /etc/restund.conf # add -d option for daemon
   ```


- **Node.JS**

  Node.jsはERSをで使用されているサーバーサイドJavaScriptランタイムです。


  Linux/Unix派生のOSの場合は、インストールプロセスを自動化するヘルパースクリプトがあります。

  ウインドウズプラットフォームでのインストールについては:

  [nodejsウェブサイト](https://nodejs.org/en/download/)からダウンロード・インストールしてください。

  Node.JSにパスを通しておきます


- **NPM**

  Node Package Manager(NPM)はNode.JSパッケージのインストールおよび依存関係の処理を簡単にしてくれます。NPMはERSのインストールに使用されます。NPMはNode.JSアプリケーションの一部です。


- **PM2**

  事前に必要というわけではありませんが、Node.JSアプリケーション／プロセスマネージャーをインストールしておいても構いません。設定が必要ですが、ERSプロセス管理やリスタートを行うことができます。PM2は推奨されています。

  このパッケージはLinux/Unixヘルパースクリプトにより自動的にインストールされます。


  手動でPM2パッケージをインストールするには:

  ```
  npm install -g pm2
  ```


## インストール手順

### 手動インストール

ERSがインストールされる場所を選択し、そのパスへ移動します。ERSをインストールするコマンドは以下です:

```
npm install http://tarballs.evostream.com/ers/ers-<version>.tgz
```

**例:**

```
npm install http://tarballs.evostream.com/ers/ers-1.0.0.tgz
```


### 自動インストール

Linux/Unixプラットフォームでは簡単にNode.JS, PM2, ERSを自動的にインストールしてくれ、さらにPM2 node.jsアプリケーションマネージャーでERSを起動してくれる簡易スクリプトがあります。


スクリプトは下記URLからダウンロードできます:

```
http://tarballs.evostream.com/ers/ers-<version>-<OS>-<arch>.sh

```

**例:**

```
http://tarballs.evostream.com/ers/ers-1.0.0-linux-x64.sh

```

ダウンロードしたら、インストール先を選択し、そのパスへ移動し下記のようにスクリプトを実行してください:

```
sudo ./ers-<version>-<OS>-<arch>.sh
```


## ERS設定

**デフォルトの**設定ファイルは`default.json`でERSがインストールされているフォルダ下の`config`フォルダにあります。 (例 `インストールディレクトリ/node_modules/ers/config/default.json`)このファイルを編集してERSの設定をカスタマイズすることができます。

`default.json`設定ファイルの内容は以下です:

```
{
  "server": {
    "port": 3535,
    "secure": false,
    "key": null,
    "cert": null,
    "password": null,
    "tokensEnabled": false,
    "webServerEnabled": true,
    "adminAccessEnabled": true,
    "adminIP": "127.0.0.1",
    "adminPort": 3030
  },
  "allowedrooms": [
  ],
  "stunservers": [
    {
    "url": "stun:162.209.96.37:55555"
    }
  ],
  "turnservers": [
  ]
}
```



**フィールドの内容**

|      **名前**      | **デフォルト値** | **内容**                          |
| :----------------: | :---------------: | ---------------------------------------- |
|       server       |                   | すべてのサーバー関連設定のトップレベルフィールド |
|        port        |       3535        | ERSがlistenするポート番号     |
|       secure       |       false       | ERSがHTTPの代わりにHTTPSを使用するかどうか |
|        key         |       null        | HTTPSで使用されるプライベートキー    |
|        cert        |       null        | HTTPSで使用される証明書    |
|      password      |       null        | 証明書のパスワード        |
|   tokensEnabled    |       false       | トークン(セキュリティ機能)が有効か EMSストリームのアクセスを制限します |
|  webServerEnabled  |       true        | ERSがビデオプレーヤーが記述されるhtmlページなど静的ファイルサーをサーブするようにwebサーバーを初期化 |
| adminAccessEnabled |       true        | ERS管理する管理者アクセスの有効化 |
|      adminIP       |     127.0.0.1     | ERSに接続できる管理者IPアドレス。ERSの管理APIを発行するマシンの実際のIPアドレスを指定する必要があります |
|     adminPort      |       3030        | ERS管理アクセス用ポート番号 |
|    allowedrooms    |                   | ERSが生成できるroom名リスト文字列 どのようなroom名も許可したい場合は空白のままにしておきます。またはemsインスタンスごとにひとつのroomを割り当てておくことによりセキュリティを高めることもできます。 |
|    stunservers     |                   | ERSが使用できるSTUNサーバーのリスト   |
|    turnservers     |                   | ERSが使用できるTURNサーバーのリスト    |





## ERSの起動

### Nodeを使用

ERSがインストールされているフォルダ下の`node_modules/ers`フォルダに行き、次のコマンドを実行してください:

```
node ers.js
```

ERSが起動し下記のメッセージが表示されます:

```
info: ERS running on port 3535...
info: Webserver port: 3535
info: Admin access port: 3030
```

ERSを終了するには、**CTRL-C**キーを押してください



### PM2を使用

ERSがインストールされているフォルダ下の`node_modules/ers`フォルダに行き、次のコマンドを実行してください:

```
pm2 start ers.js
```

ERSを終了するには:

```
pm2 stop ers
```