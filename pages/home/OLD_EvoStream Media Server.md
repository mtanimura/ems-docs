    EvoStream Media Server

クイックスタートガイド on Linux
V1.00


    本文書の内容は予告なく変更となる場合がございます
www.evostream.com © Copyright 2015 All Rights Reserved


目次
I. 本文書の目的 ..............................................................................................2

II. EvoStream Media Serverのダウンロードについて.....................................................3

Linuxアーカイブ ......................................................................................................................... 3
APTとYUMについて.............................................................................................................................. 3

III. ライセンスのインストールについて...........................................................................5
手動で行う場合................................................................................................................................... 5
Web UI経由で行う場合 ............................................................................................................................ 5

IV. Telnetでの接続.........................................................................7

V. EMS APIの基本...................................................................................8
ストリームの追加 .................................................................................................................... 8
ストリームの再生.................................................................................................................... 8
EMSサーバーの停止 ....................................................................................................... 9

図リスト
図1 : 再生 ........................................................................................................................ 8

Page 1 of 9

 I. 本文書の目的
本文書はEvoStream Media Server (EMS)をLinuxにインストールする方法について記述されています。
またEMSを実際に起動する、ソースストリームをpullする、ストリームを再生する、EMSをシャットダウンするといった基本的な操作についても記述されています。



Page 2 of 9

 II. Getting EvoStream Media Serverのダウンロードについて

1.Linux Archive
1. EMS .tarファイルを次のURLからダウンロードしてください
https://evostream.com/software-downloads

2. EMSのインストール
2.1. .tarファイルを伸長・展開してください

2. APT /YUM
A. 管理者権限:
インストールを行うにはシステム管理者権限が必要となります。
sudo utilityが使用可能な場合は：
    $ sudo su –
sudo utilityが使用不可な場合は：
    $ su –

* 管理者権限を得るとプロンプトが‘$’から‘#’に替わります

B. インストール:
1. 下記のaまたはbの要領でEvoStreamソフトウェアリポジトリをインストールするためのスクリプトをダウンロードしてください。

a. DebianベースのLinuxディストリビューションの場合は以下(例Ubuntu, Debian)
    # wget http://apt.evostream.com/installkeys.sh -O /tmp/installkeys.sh

b. RedHatベースのLinuxディストリビューションの場合は以下(CentOS, Fedora, RHEL)
    # curl http://yum.evostream.com/installkeys.sh -o /tmp/installkeys.sh

2. スクリプトを実行しEvoStreamソフトウェアをインストールしてください。
    # sh /tmp/installkeys.sh

正常に終了したら、次のようなメッセージが表示されます。
    "EvoStream keys installed successfully"

Page 3 of 9
EvoStreamソフトウェアリポジトリが正常にインストールされたら、次にパッケージのインストールをおこなってください。

EvoStream Media Serverのインストールの手順（アップデートの際も同じ）

3. EvoStream Media Serverを次のいずれかの方法でインストールします
a. DebianベースのLinuxディストリビューション(UbuntuまたはDebian)
  # apt-get install evostream-mediaserver
b. RedHatベースのLinuxディストリビューション(CentOS, Fedora, RHEL)
  # yum install evostream-mediaserver


Page 4 of 9

 III. ライセンスのインストールについて
1. Copy the license.lic in:
    アーカイブインストールの場合は: ../config
    APT/YUMでインストールの場合は: .. /etc/evostream/ (Web UI経由)

1. Run EMS

-Archive-
[Path to EMS bin folder]$ ./run_console_ems.sh
[Path to EMS bin folder]$ ./run_daemon_ems.sh

-APT/YUM-
# service evostreamms start
# service evostreamms start_console

2. ブラウザで次のWeb UIを開き
    http://localhost:8888/EMS_web_ui/

3. INSTALL EMS LICENSEをクリックしてください
4. ライセンスファイルを選択し、ファイルのインストール先を指定してください

5. Install Licenseボタンをクリックしてください


Page 5 of 9

6. 正常にインストールが完了すると、successfulというメッセージが表示されます

7. EMSを再起動してください

*ヒント: EMSが正常に起動するとコンソールにGO! GO! GO!というメッセージが表示されます


Page 6 of 9

 IV. Telnet接続
EMSとの通信にはtelnetを使用します
telnetを使ってEMS APIコマンドを実行することができます


1. コマンドプロンプトで次のようにしてください

telnet localhost 1112 （ASCII telnetインターフェースの場合）
Enterキーを押すと、localhostへのtelnetセッションが開きます

2. 手始めとしてversionを確認してみてください

Page 7 of 9

 V. EMS APIによるストリームの追加
下記のようにpullStreamコマンドをつかって外部ストリームを取り込むことができます

pullstream uri=rtmp://s2pchzxmtymn2k.cloudfront.net/cfx/st/mp4:sintel.mp4 localstreamname=test

ストリームの再生
EMSに取り込まれたストリームはEMS内部に保持されています。ストリームを再生するにはメディアフォーマットに対応したメディアプレーヤーアプリケーションが必要です。


EMSは自動的に取り込まれたストリームを異なるプロトコルに変換しますので、RTMPやRTSPどちらでもアクセスして再生することができます。

メディアプレーヤーで再生するには
1. Open Network Streamをメニューから選択し
2. 取り込まれたストリームのURLを入力します（下記例）

rtsp://127.0.0.1:5544/test
rtmp://127.0.0.1/live/test

      Figure 1 :ストリームの再生
EMSはlocalStreamNameを参照してストリームを取り込み、ストリーム再生が開始されます。
より詳しい内容については、EMS_User’s GuideおよびEMS_API_Definitions文書を参照してください。


Page 8 of 9

 EMSサーバーの停止
 EMSをシャットダウンするには次のコマンドを送ります
 shutdownServer

すると下図のようにEMSがシャットダウン用のkeyを表示しますので、
下記のように再度シャットダウンコマンドをkeyを付けて送ります
shutdownServer key=bVjvUo8HQ6VzDFJv

コマンドが送られるとEMSはシャットダウンします




Page 9 of 9

