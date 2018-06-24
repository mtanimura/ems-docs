---
title: クイックスタートガイド on Windows
keywords: quick start guide
sidebar: home_sidebar
permalink: /home_quickstartguidewindows.html
folder: home
toc: true
---



## 本文書の目的

本文書はEvoStream Media Server (EMS)をウインドウズにインストールする方法について記述されています。
またEMSを実際に起動する、ソースストリームをpullする、ストリームを再生する、EMSをシャットダウンするといった基本的な操作についても触れられています。

## EvoStream Media Serverの取得

1. <https://evostream.com/software-downloads>からEMSパッケージインストーラーをダウンロードしてください。

2. EMSのインストール

   2.1. zipパッケージを展開・伸長してください

   2.2. `setup.exe`を右クリックし、**管理者として実行**をクリックしてください

   ![](images/userguide/qsgfw1.jpg)



   2.3. 言語を選択し**OK**をクリックしてください

   ![](images/userguide/qsgfw2.jpg)



   2.4. **次へ**をクリックしインストールを続行してください

   ![](images/userguide/qsgfw3.jpg)



   2.5 使用許諾書類が表示されますので、**許諾**を選択し**次へ**をクリックしてください

   ![](images/userguide/qsgfw4.jpg)



   2.6. インストールされるパスを確認し、**次へ**をクリックしてください

   ![](images/userguide/qsgfw5.jpg)



   2.7. **EMSデスクトップアイコンの追加**を選択し、**次へ**をクリックしてください

   ![](images/userguide/qsgfw6.jpg)



   2.8. インストールの確認をおこない、**インストール**をクリックしてください

   ![](images/userguide/qsgfw7.jpg)



   2.9. 情報が表示されます、**次へ**をクリックしてください

   ![](images/userguide/qsgfw8.jpg)



   2.10. インストールを終了するため**終了**をクリックしてください

   ![](images/userguide/qsgfw9.jpg)



   **Note:** EMSライセンスが未インストールの場合は**Launch EMS**のチェックをはずしてください



## ライセンスのインストールについて

**Note:** ライセンスファイルをお手元にご用意ください。ライセンスファイルをまだお持ちでなく30日間の試用版を試したい方は、[試用版リクエスト](https://evostream.com/free-trial/) をクリックして表示されるページに必要事項を記入し試用版ライセンスを申請してください。その他のライセンスの購入に関するお問い合わせは[salesupport@evostream](mailto:salessupport@evostream.com) にお問い合わせください。

ライセンスをインストールするには `License.lic` ファイルを`C:\EvoStream\config`にコピーするだけです:




## EvoStream Media Serverの起動

EMSを起動するには、EMSのショートカットアイコンをダブルクリックするかまたはEMSフォルダ下の`run_console_ems.bat`をダブルクリックしてください。

![](images/home/startupicon.JPG)

ショートカットアイコンは`run_console_ems.bat`を実行します。このスクリプトはコマンドプロンプトからMedia Serverを起動し、メインのサーバー設定ファイルとして`config/config.lua`を読み込みます。

EMSがコンソールで開きます

![](images/userguide/start1.png)


実行アプリケーションの確認を行うには、タスクマネージャを開いて下記のプログラムが実行中であることを確認してください。

```
evostreamms.exe
evo-node.exe    (for webserver)
evo-node.exe    (for webui)
evo-node.exe    (for webservices)
```



## Web UIへの接続

EMSが正常に起動したら、EMS Web UIを開くことができます。

1. ブラウザで**`<EMS_IP>:4100`**をひらいてください

2. 必要ならユーザを新規作成するかまたはログインしてください

   ![](images/home/UI_home.png)

EMS Web UIについて詳しくは[詳細](http://docs.evostream.com/2.0/userguide_webuioverview.html)をご参照ください。

## 基本 EMS API

### UIをつかったpullStream
1. UIの**Add**ページを開きます
2. pullコマンドを選択してください
3. ストリームソースとして`rtmp://s2pchzxmtymn2k.cloudfront.net/cfx/st/mp4:sintel.mp4` を指定してください
4. Local Stream Nameには`test`と入力


   ![](images/home/addstream.JPG)

5. **Add Stream**ボタンをクリック

### UIをつかったストリームの再生

プルされたストリーム情報は自動的にEMS内に保存されます。プルされたストリームを再生するには、メディアフォーマットに対応するメディアプレーヤーを使用するか、またはUI内で再生することもできます

1. UIの**Active**ページを開き
2. 再生したいストリームの**Play**ボタンをクリックしてください

   ![](images/home/playback.JPG)


EMSは自動的にプルしたストリームを他のプロトコルで扱えるよう変換します。メディアプレーヤーで再生するには:

1. Open Network Streamを選択し
2. プルされたストリームのURLを入力してください
    RTSPの場合: `rtsp://127.0.0.1:5544/test`
    RTMPの場合: `rtmp://127.0.0.1/live/test`

![](images/home/rtspplayback.jpg)

ファイルがあれば`localStreamName`を参照し、ストリームを取得・再生します。

### EMSサーバーの停止
 EMSをシャットダウンするには次のコマンドを送ります
 ```
 shutdownServer
 ```
すると下記のようにEMSがシャットダウン用のkeyを表示しますので、

```
shutdownServer
Command entered successfully!
Call shutdownserver again with the provided key
key: bvjvUo8HQ6VzDFJv
```

下記のように今度はkeyを付けてシャットダウンコマンドを送ります

```
shutdownServer key=bVjvUo8HQ6VzDFJv
```


コマンドが送られるとEMSはシャットダウンします

詳しくは[EMSユーザガイド](http://docs.evostream.com/2.0/userguide_overview.html) および [EMS API ガイド](http://docs.evostream.com/2.0/api_overview.html)を参照してください
