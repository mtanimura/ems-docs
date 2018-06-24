---
title: クイックスタートガイド on Linux
keywords: quick start guide
sidebar: home_sidebar
permalink: /home_quickstartguidelinux.html
folder: home
toc: true
---


# 本文書の目的
本文書はEvoStream Media Server (EMS)をLinuxにインストールする方法について記述されています。
またEMSを実際に起動する、ソースストリームをpullする、ストリームを再生する、EMSをシャットダウンするといった基本的な操作についても触れられています。

# EvoStream Media Serverの取得
## Linux Archive
1. EMS .tarファイルを次のURLからダウンロードしてください
2. https://evostream.com/software-downloads

.tarファイルを伸長・展開し、ご希望のディレクトリにインストールしてください


## APT/YUM
事前準備: インストールを行うにはシステム管理者権限が必要となります。

sudo utilityが使用可能な場合は：
    `$ sudo su –`
sudo utilityが使用不可な場合は：
    `$ su –`

**Note:**
管理者権限を得るとプロンプトが‘$’から‘#’に替わります

# インストール:

1. 下記の要領でEvoStreamソフトウェアリポジトリをインストールするためのスクリプトをダウンロードしてください。

    DebianベースのLinuxディストリビューションの場合は以下(例Ubuntu, Debian)
        `# wget http://apt.evostream.com/installkeys.sh -O /tmp/installkeys.sh`

    RedHatベースのLinuxディストリビューションの場合は以下(CentOS, Fedora, RHEL)
        `# curl http://yum.evostream.com/installkeys.sh -o /tmp/installkeys.sh`

​
2. スクリプトを実行しEvoStreamソフトウェアリポジトリおよびキーをインストールしてください。

    `# sh /tmp/installkeys.sh`

    正常に終了したら、次のようなメッセージがコンソールに表示されます。

    `"EvoStream keys installed successfully"`
​
    EvoStreamソフトウェアリポジトリおよびキーが正常にインストールされたら、次にパッケージのインストールをおこなってください。

**Note:** 上記の手順１，２の実行は１回のみです

EvoStream Media Serverのインストールの手順（最新版にアップデートの際も同じ）

3. EvoStream Media Serverを次のいずれかの方法でインストールします

    DebianベースのLinuxディストリビューション(UbuntuまたはDebian)
        # apt-get install evostream-mediaserver

    RedHatベースのLinuxディストリビューション(CentOS, Fedora, RHEL)
        # yum install evostream-mediaserver


​
#ライセンスのインストールについて
Note: ライセンスファイルをお手元にご用意ください。ライセンスファイルをまだお持ちでなく30日間の試用版を試したい方は、[試用版リクエスト](https://evostream.com/free-trial/) をクリックして表示されるページに必要事項を記入し試用版ライセンスを申請してください。その他のライセンスの購入に関するお問い合わせは[salesupport@evostream](mailto:salessupport@evostream.com) にお問い合わせください。


ライセンスをインストールするには `License.lic` ファイルを下記のディレクトリにコピーするだけです:

Linuxアーカイブ
`../config`

APT/YUM
`/etc/evostreamms/`

**Note:** EMSは起動時に通常/etc/evostreammsにライセンスファイルがあるかどうかを確認します。apt/yumでインストールしていて、アーカイブ版を試したい場合に注意してください。

#EvoStream Media Serverの起動

##Linuxアーカイブ

1. ターミナルを開き
2. EvoStream/binフォルダに移動
3. 下記コマンドを実行
    `./run_console_ems.sh`

![](http://docs.evostream.com/2.0/images/userguide/start1.png)

4. 下記コマンドでEvoStreamが実行中かどうかを確認してください。
    `ps –e|grep evo`

正常に起動すると下記のような表示になります。

  user@ubuntu:~$ ps –e|grep evo
  10727 pts/4 00:00:22 evostreamms
  10728 pts/4 00:00:05 evo-node (for webserver)
  10729 pts/4 00:00:00 evo-node (for webui)
  10730 pts/4 00:00:00 evo-node (for webservices)
​
##APT/YUM
1. ターミナルを開き
2. 下記コマンドを実行
    `service evostreamms start_console`
    ![](http://docs.evostream.com/2.0/images/userguide/start1.png)

下記コマンドでEvoStreamが実行中かどうかを確認してください。
`ps –e|grep evo`


  user@ubuntu:~$ ps –e|grep evo
  10727 pts/4 00:00:22 evostreamms
  10728 pts/4 00:00:05 evo-node (for webserver)
  10729 pts/4 00:00:00 evo-node (for webui)
  10730 pts/4 00:00:00 evo-node (for webservices)
​
#Connecting to Web UI
起動がうまくいったら、EMS Web UIを開くことができます。
1. ブラウザで**<EMS_IP>:4100** を開いてください

2. 必要ならユーザを新規作成するかまたはログインしてください
![](http://docs.evostream.com/2.0/images/home/UI_home.png)

EMS Web UIについて詳しくは[詳細](http://docs.evostream.com/2.0/userguide_webuioverview.html)をご参照ください。


#基本 EMS API
##UIをつかったpullStream
1. UIの**Add**ページを開きます
2. pullコマンドを選択してください
3. ストリームソースとして`rtmp://s2pchzxmtymn2k.cloudfront.net/cfx/st/mp4:sintel.mp4` を指定してください
4. Local Stream Nameにはtestと入力
5. Add Streamボタンをクリック

##UIをつかったストリームの再生
プルされたストリーム情報は自動的にEMS内に保存されます。プルされたストリームを再生するには、メディアフォーマットに対応するメディアプレーヤーを使用するか、またはUI内で再生することもできます

UIのActiveページを開き
再生したいストリームのPlayボタンをクリックしてください
![](http://docs.evostream.com/2.0/images/home/playback.JPG)
​
EMSは自動的にプルしたストリームを他のプロトコルで扱えるよう変換します。メディアプレーヤーで再生するには:

1. Open Network Streamを選択し
2. プルされたストリームのURLを入力してください
    RTSPの場合: `rtsp://127.0.0.1:5544/test`
    RTMPの場合: `rtmp://127.0.0.1/live/test`


![](images/home/rtspplayback.jpg)


ファイルがあればlocalStreamNameを参照し、ストリームを取得・再生します。

##EMSサーバーの停止
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
