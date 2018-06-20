EvoStream Media Server
クイックスタートガイド on Windows
V1.00
    本文書の内容は予告なく変更となる場合がございます
www.evostream.com © Copyright 2015 All Rights Reserved


 Table Of Contents
I. 本文書の目的 ..............................................................................................2
II. EvoStream Media Serverのダウンロードについて.....................................................3
III. ライセンスのインストールについて ...........................................................................8
手動で行う場合................................................................................................................................... 8
Web UI経由で行う場合 ............................................................................................................................ 8
IV. Telnet接続.......................................................................10
V. EMS APIの基本.................................................................................11
APIによるストリームの追加 ........................................................................................................................... 11
ストリームの再生 .............................................................................................................................. 11
EMSサーバーの停止 ..................................................................................................... 12
図リスト
図１ : 再生 ...................................................................................................................... 11
        EvoStream Media Server
+1 858-454-9393 sales@evostream.com
Page 1 of 12


 I. 本文書の目的
本文書はEvoStream Media Server (EMS)をWindowsにインストールする方法について記述されています。
またEMSを実際に起動する、ソースストリームをpullする、ストリームを再生する、EMSをシャットダウンするといった基本的な操作についても記述されています。

  EvoStream Media Server
+1 858-454-9393 sales@evostream.com
Page 2 of 12




 II.
1. 2.
Getting EvoStream Media Serverのダウンロードについて
EMSパッケージインストーラーを次のURLからダウンロードしてください
https://evostream.com/software-downloads Install EMS

2.1. zipファイルを伸長・展開してください
2.2. Setup.exeを右クリックし管理者権限で実行をクリックしてください
2.3. 言語を選択肢OKをクリックしてください

     EvoStream Media Server
+1 858-454-9393 sales@evostream.com
Page 3 of 12



 2.4. 次へをクリックしインストールを続行してください
 2.5. 使用許諾書類が表示されますので、許諾を選択し次へをクリックしてください

   EvoStream Media Server
+1 858-454-9393 sales@evostream.com
Page 4 of 12



 2.6. インストールされるパスを確認し、次へをクリックしてください

 2.7. EMSデスクトップアイコンの追加をし、次へをクリックしてください
   EvoStream Media Server
+1 858-454-9393 sales@evostream.com
Page 5 of 12



 2.8. インストールの確認をおこない、次へをクリックしてください
 2.9. 情報が表示されます、次へをクリックしてください
   EvoStream Media Server
+1 858-454-9393 sales@evostream.com
Page 6 of 12



 2.10. インストールを終了するため終了をクリックしてください
 Note:
EMSライセンスが未インストールの場合は“Launch EMS”のチェックをはずしてください
  EvoStream Media Server
+1 858-454-9393 sales@evostream.com
Page 7 of 12



 III. ライセンスのインストールについて
ライセンスのインストールは手動とWeb UIによる場合の２つの方法がとれます
手動で行う場合
1. Copy the license.licファイルを ..\EvoStream\config以下にコピーします

Web UI経由で行う場合
1. EMSを起動します
2. ブラウザでEMS Web UI（下記のURL）を開きます
http://localhost:8888/EMS_web_ui/

3. INSTALL EMS LICENSEをクリックしてください
4. ライセンスファイルを選択しライセンスファイルインストール先を指定してください。
5. Install Licenseをクリックしてください
  EvoStream Media Server
+1 858-454-9393 sales@evostream.com
Page 8 of 12


6. インストールが正常に行われるとその旨メッセージが表示されます

7. EMSの再起動
*ヒント: EMSが正常に起動するとコンソールにGO! GO! GO!というメッセージが表示されます

  EvoStream Media Server
+1 858-454-9393 sales@evostream.com
Page 9 of 12



 IV. Telnet接続
EMSとの通信にはtelnetを使用します
telnetを使ってEMS APIコマンドを実行することができます

1. コマンドプロンプトで次のようにタイプしてください
telnet localhost 1112 （ASCII telnetインターフェースの場合）
Enterキーを押すと、localhostへのtelnetセッションが開きます

2. 手始めとしてversionを確認してみてください

   EvoStream Media Server
+1 858-454-9393 sales@evostream.com
Page 10 of 12



 V. EMS APIによるストリームの追加
下記のようにpullStreamコマンドをつかって外部ストリームを取り込むことができます

ストリームの再生
EMSに取り込まれたストリームはEMS内部に保持されています。ストリームを再生するにはメディアフォーマットに対応したメディアプレーヤーアプリケーションが必要です。

EMSは自動的に取り込まれたストリームを異なるプロトコルに変換しますので、RTMPやRTSPどちらでもアクセスして再生することができます。

メディアプレーヤーで再生するには
1. Open Network Streamをメニューから選択し
2. 取り込まれたストリームのURLを入力します（下記例）

rtsp://127.0.0.1:5544/test
rtmp://127.0.0.1/live/test

Figure 1 : Playback

EMSはlocalStreamNameを参照してストリームを取り込み、ストリーム再生が開始されます。
より詳しい内容については、EMS_User’s GuideおよびEMS_API_Definitions文書を参照してください。

  EvoStream Media Server
+1 858-454-9393 sales@evostream.com
Page 11 of 12



EMSサーバーの停止
 EMSをシャットダウンするには次のコマンドを送ります
 shutdownServer

すると下図のようにEMSがシャットダウン用のkeyを表示しますので、
下記のように再度シャットダウンコマンドをkeyを付けて送ります
shutdownServer key=bVjvUo8HQ6VzDFJv


        EvoStream Media Server
+1 858-454-9393 sales@evostream.com
Page 12 of 12



