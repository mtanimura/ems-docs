---
title: WebSocketの概要
keywords: websocket
sidebar: html5players_sidebar
permalink: html5players_wsoverview.html
folder: html5players
toc: false
---

HTML5 Web Socketテクノロジーは、従来のようなHTTP request/responseモデルではなく、webブラウザとサーバー間のソケット接続を提供します。HTTPではデータのやりとりのためにはクライエントがリクエストを送ることで通信を開始し、対してサーバーはレスポンスを返します。HTTPでは低遅延アプリケーションにとって好ましくないオーバーヘッドを招くことになります。

Web Socketを使えばクライエント／サーバー間で持続的な接続を確立でき、双方どちらもいつでもデータ送信を開始することができます。クライエント側からリクエストを送る必要が無いため、ほぼリアルタイムなデータ配信が可能な低遅延な接続が可能となります。

EMSはWeb Socketテクノロジーを活用し次の機能を提供します:

- メタデータアウトバウンドプッシュ – ブラウザにメタデータを送信
- メタデータインジェスト – incomingメタデータの受信
- FMP4プレーヤー – フラグメントMP4(FMP4)を転送するacceptor






