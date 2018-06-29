---
title: WebRTCを使ったビデオ再生
keywords: webrtc
sidebar: html5players_sidebar
permalink: html5players_wrtcdemo.html
folder: html5players
toc: true
---

**ピアツーピアストリーミングはEvoStream HTML5ストリーム技術を使用します。HTML5 Streamingセクションもご参照いただくことをお薦めします。**

## デモプレーヤー

リリース2.0以降、evoplayer(HTML5 web player)は下記のストリームを再生可能です

- プルした RTMP/RTSP ストリーム
- Lazy pullしたストリーム
- プレイリストファイル


## WebRTCストリーミング

1. webRTCを使用しEMSからストリーム再生するにはまず`startWebrtc`コマンドを実行する必要があります。 [startWebRTCAPI](/api/api_startWebRTC.html)を参照する


   ```
   startwebrtc ersip=54.174.188.145 ersport=4545 roomid=MyRoom
   ```

   **Note:** 特にパブリックERSを使用する場合はroom名コンフリクトを避けるため、roomu名は可能な限りユニークな値である必要があります。room名がすでに使用されている場合はERSはエラーをコンソールログに返します
   ​

2. 次に`demo/evoplayers.html`テストページにアクセスしてください

   ```
   http://<WEBSERVER_IP_ADDRESS>/demo/evoplayers.html
   ```

3. **EMS IP**, **Room名**, **Stream 名**を入力し、

   **Note:** ストリーム名はプルしたストリーム、lazypullファイル、プレイリストファイルなどが使用できます。lazypullやプレイリストはmediaフォルダにある必要があります。   ​

4. **Play**ボタンをクリックしストリーミングを開始してください


   **RTMP/RTSPでプルされたストリームの再生:**

   ![](images/html5/webrtc-1.jpg)


   **lazypullファイルの再生:**

   ![](images/html5/play_wrtc_lazypull.jpg)


   **プレイリストファイルの再生:**

   ![](images/html5/play_wrtc_playlist.jpg)

**Note:**

WebRTCプレーヤーは２つありますが、同じソースや別々のソースを再生することができます。

## SRTPをつかったWebRTC

このプレーヤーはフラグメントMP4ではなくSRTPをトランスポートに使用します。使い方は上記と同様の手順です

![](images/html5/play_wrtcsrtp.jpg)

**Note:**

- ストリームオーディオがうまくいかない場合は、ブラウザがWebRTC AACをサポートしていない可能性があります。


## SSLを使用したWebRTC ERS接続

クライエント(ブラウザ)やサーバー(EMS)などからのERSへの接続にSSLを使うことで通信スニッファーを防ぐことができます。SSL接続を有効にするには:

1. ERSの設定として、default.json設定ファイルを編集

   ```
   "secure": true,
   "key": "/path/to/server.key",
   "cert": "/path/to/server.cert"
   ```

2. EMSの設定としては、config.luaファイル無いwebrtcセクションに`ersOverSsl`パラメータを追加

   ```
   webrtc={
   		ersOverSsl=true,                              --> 追加するパラメーター
   		sslKey="/path/to/server.key",
   		sslCert="/path/to/server.cert",
   	   },
   ```

3. JSプレーヤーの設定として、"opts"オブジェクトの下記の設定値を変更

   ```
   ersOverSsl: true
   ```

4. EMSの設定有効化のため再起動

------

## 関連リンク

- [Starting WebRTC](api/startWebRTC.html)
- [Stopping WebRTC](stopWebRTC.html)

