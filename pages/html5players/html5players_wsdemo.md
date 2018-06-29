---
title: WebSocketsを使ったストリーミング
keywords: websocket
sidebar: html5players_sidebar
permalink: html5players_wsdemo.html
folder: html5players
toc: true
---

リリース2.0以降ではEMSのHTML5 web player（evoplayer）は下記のストリームを再生できるようになりました:

- プルされたRTMP/RTSPストリーム
- Lazy pullされたストリーム
- プレイリストファイル

WebSocketの使用方法について下記に記述します:


## WebSocketストリーミング

1.  `demo/evoplayers.html`テストページにアクセスしてください

   ```
   http://<ウェブサーバーのip>/demo/evoplayers.html
   ```

2. 再生したい(ストリーム・Lazypullストリーム・プレイリストファイル)のEMS IPアドレスおよびストリーム名

   **Note:** Lazypullおよびプレイリストファイルはmediaフォルダ以下にあるはずです

   ​

3. 再生したストリームのEMS IPアドレスおよびストリーム名を入力してください

4. **Play**ボタンをクリックしストリーム再生を開始してください

   **RTMP/RTSPでプルされたストリームの再生:**

   ![](images/html5/websocket.JPG)

   ​

   **Lazypullされたファイルの再生:**

   ![](images/html5/play_ws_lazypull.jpg)

   ​

   **プレイリストファイルの再生:**

   ![](images/html5/play_ws_playlist.jpg)

   ​

   **Note:**

   WebSocketでは２つのプレーヤーがあります。同じソースストリームでも２つの異なるストリームでも同時に再生させることができます。



## WebSocket Over SSL

このWebSoketプレーヤーは、websocket接続をセキュアにするSSL暗号化トランスポートを使います。有効化する方法は以下です:

1. config.luaファイルのWebSockets over FMP4 Fetchの部分のコメントを外してください

   ```
   -- WebSockets over SSL FMP4 Fetch
   				--[[                                           ---- コメントを外し有効化
   				{
   					ip="0.0.0.0",
   					port=8420,
   					protocol="inboundWSSFMP4",
   					sslKey="C:\\EvoStream\\config\\server.key",
   					sslCert="C:\\EvoStream\\config\\server.cert",
   				},
   				]]--                                           ----コメントを外し有効化
   ```

2. 必要ならパラメータを編集してください

3. EMSを再起動してください

4. `demo/evoplayers.html`テストページにアクセスしWebSocket over SSLプレーヤーでのストリーム再生を確認してください

   ![](/images/html5/play_wsssl.jpg)

   ​

**Notes:**

- 署名済み証明書の使用を推奨します

- 自己署名証明書を使う場合は、プレーヤーを使用する前にブラウザのexception/trusted publishersに証明書を追加してください。

  ​

