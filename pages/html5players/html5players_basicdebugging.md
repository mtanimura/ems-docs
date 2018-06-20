---
title: 基本的なデバッグ
keywords: html5
sidebar: html5players_sidebar
permalink: html5players_basicdebugging.html
folder: html5players
toc: true
---

## WebSockets/WebRTCをつかってストリーム再生ができない

**デバッグ:**

1. **事前チェック** 別のプレーヤーソフトでストリームソースを再生できるかどうかテスト

2. **HTML 5 ブラウザサポート** You may check the support by clicking on this [リンク](https://www.youtube.com/html5?gl=PH)からサポート状況を確認できます。
H264およびMSE & H.264にチェックされていることを確認してください

  Firefoxを使う場合下記設定を確認してください:

   ```
   1. アドレスフィールドに入力してEnter: about:config
   “危険性を承知の上で使用する”をクリックしてください

   2. 次の設定名の値を確認してください:
   media.mediasource.enabled = true
   media.mediasource.whitelist = false
   media.mediasource.mp4.enabled = true
   media.fragmented-mp4.exposed = true
   media.fragmented-mp4.ffmpeg.enabled = true
   media.fragmented-mp4.gmp.enabled = true
   media.fragmented-mp4.use-blank-decoder = false

   3. 設定変更を適用するためFirefoxを再起動してください
   ```

3. 接続が確立するか確認してください。通常ブラウザはEMSとの接続を確立できるはずで、HTML5プレーヤーでEMSロゴが表示されます。ロゴが表示されない場合、接続不良かEMSへの接続がデータチャンネルを確立できていません。webRTCにはEMSがwebRTCを起動できているか、適切なroomを使用しているかを確認してください。


4. **ストリームがあるか**を確認してください。 EvoStreamのロゴが表示された状態のまま何も置きない場合、"Show debug message"にチェックが入っていれば、webRTCページ読み込み直後に下記のようなログが表示される場合があります。

   ```
   1453259850224: Media source is now ready.
   1453259850224: Command: {"payload":{"description":"Requested stream could not be sent!","name":"myStream", "status":"FAIL"},"type":"fmp4Response"}
   1453259850222: channelOpen emsStreamChannel
   1453259850221: Sending request for fmp4...
   1453259850221: channelOpen emsCommandChannel
   1453259850219: Connection established with qKbPr2FJHicfvNx6xRP0

   ```

   上記ログは、接続そのものは確立されたものの、リクエストしたストリームが無いことを意味しています。

------



## HTML5プレーヤーで映像がフリッカーまたはフリーズする場合

**デバッグ:**

1. **GOPサイズ調整** ビデオバッファが小さすぎる場合に起きます。JSページでqueueSize variableを変更してバッファサイズを調整できます。EvoWsPlayer function/constructorに送られるオプションパラメータです。このサンプル[ページ](http://ers.evostream.com:5050/demov2/evoplayers.html)のソースコードは:


   option変数は次のような設定になっています:

   ```
   var opts = {
   		emsIp: emsIp,
   		streamName: streamName,
   		videoTagId: 'video' + number,
   		debugDivId: 'debug' + number,
   		queueSize: 5
   		};

   ```

   queueSizeはGOPによって測られます。GOPサイズが大きい場合、バッファは少なくてすみますが、コンピュータ内のフットプリントは大きくなります。再生レイテンシー増大させます。

